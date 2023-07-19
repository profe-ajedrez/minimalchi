# Minimal Chi

Un template mínimo recargado con el router [Chi](https://go-chi.io/#/) para ser usado como base para construir apis REST.

Minimal Chi no intenta decidir por ud. que clase de proyecto realizar ni que dependencias importar. Ofrece simplemente una estructura de directorios base, componible y expandible para ser usada en cualquier proyecto, manteniendo algunos elementos idiomáticos. 


## Prueba rápida

Descargue el repositorio e instale las dependencias:

```bash
$ go get -u
$ go mod tidy
```

Levante la api

```bash
$ go run main.go serve
```

## Api

En el paquete *api/v1*, en el archivo *routes.go puede registrar las rutas de su aplicación, escribiendo los handlers en *api/v1/handlers* según los vaya necesitando.

Puede revisar el endpoint de ejemplo `Ping` que se incluye.

## Visualización de stats

Se incluyen los manejadores para poder revisar stats de la api como el consumo de memoria y otros usando el paquete [statsviz](https://github.com/arl/statsviz). Con su aplicación ejecutandose, solo dirijase en su navegador favorito a http://localhost:puerto/debug/statsviz.

Si desea desactivar esta feature, solo comente las líneas donde se le referencia en el archivo *api/v1/routes.go* y ejecute `$ go mod tidy`.



## Configuración

En el paquete internal/config puede, si gusta, agregar campos al struct `Conf` para cargar las configuraciones de su aplicación, usando la función `NewConf`. 

```Go
// Conf contiene los datos de configuración de la api.
// Implemente los campos que su aplicación necesite y defina un medio para obtener
// esos datos, ya sea cargandolos desde un archivo o desde flags de la línea de comandos.
type Conf struct {
	// AppName contiene el nombre de su aplicación
	APPName string `json:"appName" yaml:"app_name"`

	// Port infica en que puerto poner a escuchar a esta api
	Port int `json:"port" yaml:"port"`
}
```

De esta forma ud. decide si cargarlas desde un archivo, desde la línea de comandos o desde otros medios.
