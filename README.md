Hostinger module for Caddy
===========================

This package contains a DNS provider module for [Caddy](https://github.com/caddyserver/caddy). It can be used to manage DNS records with [Hostinger](https://www.hostinger.com/) via their [API](https://developers.hostinger.com).

It uses the [`libdns-hostinger`](https://github.com/sbrunk/libdns-hostinger) provider.

## Caddy module name

```
dns.providers.hostinger
```

## Config examples

To use this module for the ACME DNS challenge, [configure the ACME issuer in your Caddy JSON](https://caddyserver.com/docs/json/apps/tls/automation/policies/issuer/acme/) like so:

```json
{
	"module": "acme",
	"challenges": {
		"dns": {
			"provider": {
				"name": "hostinger",
				"api_token": "{env.HOSTINGER_API_TOKEN}"
			}
		}
	}
}
```

or with the Caddyfile:

```
# globally
{
	acme_dns hostinger {env.HOSTINGER_API_TOKEN}
}
```

```
# one site
tls {
	dns hostinger {env.HOSTINGER_API_TOKEN}
}
```

You can also use the block syntax:

```
tls {
	dns hostinger {
		api_token {env.HOSTINGER_API_TOKEN}
	}
}
```

API tokens can be created and managed in the [Hostinger Panel](https://hpanel.hostinger.com/profile/api).
