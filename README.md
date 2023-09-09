# Contenedor de Docker para Rust

Este proyecto contiene un ejemplo simple de como contenerizar una aplicacion de Rust en Docker.

Para correr el codigo ejemplo

```bash
cargo run --manifest-path Cargo.toml
```

Para Crear el contenedor de Docker

```bash
docker build -t tu-cuenta/tu-tag .
```

Para correr el contenedor, vamos a mapear el puerto `8080` que la aplicación expone al arrancar por `4000` en nuestro ordenador. 

```bash
docker run -it -p 4000:8080 tu-cuenta/tu-tag
```

Y visita http://localhost:4000 

# Usuarios de Apple Silicon

Si estas trabajando en una Mac con Apple Silicon (M1, M2) vas a tener que crear una imagen exclusiva para `arm64` ya que por el momento Rust no soporta hacer imagenes multi-arquitectura.


```bash
docker buildx build --platform linux/arm64 --push -t tu-cuenta/tu-tag -f Dockerfile.arm64 . 
```
