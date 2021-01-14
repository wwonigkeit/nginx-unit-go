# Go Hello World

Hello World is a simple webserver to use as an introduction to Vorteil. It hosts a webpage containing a simple hello world message with Vorteil's logo. The background colour of the page can be controlled by setting the `--colour` argument to any valid HTML colour code.

The code has been specifically modified for the [NGINX Unit platform!](https://unit.nginx.org/)

The following changes are needed:
```go
import (
    ...
    "unit.nginx.org/go"
    ...
)
```

and

```go
func main() {
    ...
    http.HandleFunc("/", handler)
    ...
    //http.ListenAndServe(":8080", nil)
    unit.ListenAndServe(":8080", nil)
    ...
}
```

## Compilation

```sh
CGO_ENABLED=0 go build
```

To simplify the process of getting Hello World to run in a Virtual Machine, we set CGO_ENABLED=0 to direct Go to statically compile the binary without needing dynamically linked libraries.

## Running

The helloworld binary requires a `--colour` argument

```sh
./helloworld --colour=0xFFFFFF
```

The argument colour: must be six characters of hexadecimal (like '0xFFFFFF')

Should return something like

```
2017/10/13 11:14:32 Binding port: 80
```

You can connect to the web server by visiting http://localhost/
