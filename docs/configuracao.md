# Tema do Laravel para projetos USPdev

## [Início](../README.md) > Instalação e configuração


0. Se você vai iniciar uma nova aplicação, instale o laravel primeiro.

```bash
composer create-project --prefer-dist laravel/laravel minha_aplicacao
```

1. Se você já tem uma aplicação laravel ou com a nova aplicação
que você criou instale o tema usando o composer.

```bash
composer require uspdev/laravel-usp-theme
```

2. Publique o arquivo de configuração.

```bash
php artisan vendor:publish --provider="Uspdev\UspTheme\ServiceProvider" --tag=config
```

3. Configure o `composer.json` para publicar os assets automaticamente. Para isso acrescente a linha abaixo na seção `scripts`->`post-autoload-dump`.

```json
"scripts": {
    "post-autoload-dump": [
        ...
        "@php artisan vendor:publish --provider=\"Uspdev\\UspTheme\\ServiceProvider\" --tag=assets --force"
        ...
    ],
}
```

4. Execute o comando abaixo para publicar os assets.

```bash
composer dump -o
```

5. Edite o arquivo `.gitignore` e acrescente a linha abaixo.

```txt
public/vendor
```

6. Configure o `.env.example` e o `.env`. Note que todas as configurações são opcionais.

```txt
# LARAVEL-USP-THEME
# https://github.com/uspdev/laravel-usp-theme

# O laravel-usp-theme permite que seja criado links
# para outras aplicações da unidade
#USP_THEME_SISTEMAS_1='{"text":"Pessoas","url":"http://localhost/pessoas"}'
#USP_THEME_SISTEMAS_2='{"text":"LDAP","url":"http://localhost/ldap"}'

# Escolha o skin a ser utilizado
#USP_THEME_SKIN=uspdev
```

7. Edite ou crie o seu arquivo `resources/views/layouts/app.blade.php` para estender o **laravel-usp-theme**. Veja um exemplo.
   
```php
@extends('laravel-usp-theme::master')

@section('title') 
  @parent 
@endsection

@section('styles')
  @parent
  <style>
    /*seus estilos*/
  </style>
@endsection

@section('javascripts_bottom')
  @parent
  <script>
    // Seu código .js
  </script>
@endsection
```

8. Em suas views, estenda o seu layout base.

```php
@extends('layouts.app')

@section('content')
  Seu html que será inserido no meio do layout
@endsection
```

9. Configure o menu da aplicação. Ele está em `config/laravel-usp-theme.php`. Veja a [documentação aqui](config/opcoes-menu.md).
