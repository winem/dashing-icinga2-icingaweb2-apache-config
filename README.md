# dashing-icinga2-icingaweb2-apache-config
These snippets & the configuration allow you to use the same domain for both, icingaweb2 and dashing-icinga2. 

## Overview 
  - `vhost-dashing-icinga2-locations.conf` & `vhost-dashing-icinga2-locations-with-authentication.conf` are just snippets you can copy paste into your existing vhost configuration
  - `moni.mydomain.com.conf` is a complete vhost configuration file for moni.mydomain.com that
      - redirects all http requests to https
          - be careful with the SSL certificates / CN (I have a wildcard certificate for our domain, so it's for *.mydomain.com and the filename is just mydomain.com.crt
      - adds basic auth to the locations being proxied to the dashing-icinga2 instance
          - /etc/icingaweb2 is synchronized between my two master / icingaweb2 instances, that's why I place the .htpasswd file here (make sure that this file is in a secure location and has the minimum required permissions) 
  - `dashing.mydomain.com.conf` is an example vhost configuration for a reverse proxy for dashing-icinga2 only.

## Required modules
Following modules are required: 
  - mod_ssl
  - mod_authz_core (if you want to use basic authentication)
  - mod_proxy
  - mod_proxy_http
