---
title: "Help with reverse proxy on single server (Ubuntu 22.04)"
date: 2023-04-12
forum: Networking &amp; Wireless
---

### Post by flagg616 on 2023-04-12
I have a server that hosts lots of things.  I have most of them secured (after years of trial and error) but now I'm stuck.  Everything I see says to set up a reverse proxy to allow all of the various types of sites I run to be routed through my SSL certificate, rather than securing each one individually.  
Here's what I have running.


Apache/2.4.52 website.com  443 with Letsencrypt.
Then I have multiple subdomains, each running on their own ports (except the store and the cloud).
radio.website.com (a modified, secured version of Kodi control interface, port 902 and Icecast2 on port 8443) 
store.website.com (an opencart website)
media.website.com (Jellyfin server, port 8096 not yet secured)
humanity.website.com (Pretend you're Xyzzy server, port 8080 not yet secured, Tomcat)
cloud.website.com (Nextcloud server)
books.website.com (Calibre book server, secured using the current cert, set up in config)




Ideally, I would like to have all the different sites and apps that I have painstakingly forced to limp along and have them all run (http) through reverse proxy, where they will be routed (https), en masse through a single certificate.  The reason being is that every time my certificate is renewed or if it changes, I have to concatenate each individual set of certs for each one separately, since they all require different types of certificate formats.  It's tedious and time consuming and creates too many points of failure.  I don't want to set up a second server as a front end if I can avoid it.  I just want everything it serves to go through the reverse proxy, so I don't have to configure SSL for each one every time.  I have searched and searched, but I can't seem to find what I need.

---

### Post by SeijiSensei on 2023-04-12
> **flagg616 said:**
> The reason being is that every time my certificate is renewed or if it changes, I have to concatenate each individual set of certs for each one separately, since they all require different types of certificate formats.  It's tedious and time consuming and creates too many points of failure.

I run a 20.04 server with Apache that supports multiple domains via virtual hosting. I manage all my certificates with acme.sh using the LetsEncrypt server. I run a cron job each night to update any certificates that need it. 

I'm just wondering if you really need such a complex setup.

---

### Post by flagg616 on 2023-04-12
Yes, the point of what I'm trying to do is to not have things be so complex.  Rather than running a script to handle my certificates, I was hoping to remove the need to even have them at all.  If I understand correctly (and I'm not sure I do) reverse proxy allows you to take http traffic and (for lack of a better term) 'convert' it to https before sending it out.  I would like to do that with every part of my webserver traffic, so I don't have to configure each one independently if it runs on a port other than 443.

---

### Post by SeijiSensei on 2023-04-12
We need more information. What web server software are you running? Apache? Why are you using different destination ports than the standard virtual hosting features built into Apache? Each of my sites has a separate file in /etc/apache2/sites-available/ like this one for politicsbythenumbers.org:
```

<VirtualHost    *:443>
ServerAdmin     webmaster@cyways.com
DocumentRoot    /home/cyways/sites/politicsbythenumbers/public
ServerName      politicsbythenumbers.org
ServerAlias     www.politicsbythenumbers.org 
ErrorLog        logs/error_log-politicstats
TransferLog     logs/access_log-politicstats
CustomLog       logs/referer_log-politicstats "%h: %{referer}i -> %U"

<Directory      "/home/cyways/sites/politicsbythenumbers/public">
        Require all granted
</Directory>

Alias /images /home/cyways/sites/politicsbythenumbers/images
<Directory      "/home/cyways/sites/politicsbythenumbers/images">
        Require all granted
</Directory>

Include /etc/letsencrypt/options-ssl-apache.conf
SSLCertificateFile /root/.acme.sh/politicsbythenumbers.org/politicsbythenumbers.org.cer
SSLCertificateKeyFile /root/.acme.sh/politicsbythenumbers.org/politicsbythenumbers.org.key
SSLCertificateChainFile /root/.acme.sh/politicsbythenumbers.org/ca.cer

</VirtualHost>

```
The ServerName and ServerAlias fields specify the name to which this virtual server responds, politicsbythenumbers.org, along with some aliases like [www.politicsbythenumbers.org](www.politicsbythenumbers.org). The main directory contains a WordPress site. I have another couple of subdirectories outside of WordPress that you can access directly like [https://politicsbythenumbers.org/images/](https://politicsbythenumbers.org/images/). They are referenced using the "Alias" directive. At the bottom are the directives needed to support HTTPS encryption. 

Notice that the top of the file uses
```
<VirtualHost *:443>
```
That means it's listening on the HTTPS port to all requests that arrive ("*"). The ServerName and ServerAlias definitions for my various sites determine which configuration to use for each requested site.

I played with proxies once many years back. I have no need for them now. All my sites are on a public server at Linode for $5/month that sits directly on the public Internet. I use OpenVPN tunnels to communicate securely with my remotes. 

I'd just redefine all your sites as Apache virtual hosts and have everything come in via 443.

I use [acme.sh]("https://github.com/acmesh-official/acme.sh") + LetsEncrypt for all my certificates. I use LetsEncrypt rather than the default server because it has been much faster in my experience. (Add "-s letsencrypt" to acme.sh command line.)

---

### Post by flagg616 on 2023-04-12
As I mentioned in the first post, Apache 2.4.52
I think maybe I have done it wrong.  This may shed some light.  When I first set up my server, I edited the 000-default.conf with my domain and all of my subdomains.  Then I ran the letsencrypt script.  It asks which domains I want to secure and lists the domain and all subdomains.  I choose all of them.  That creates my certs at /etc/letsencrypt/live/website.com.  It also rewrites my 000-default.conf and adds rewrites to the 000-default-le-ssl.conf and all the website traffic is forced to 443. Everything that lives in folders in my web root work just fine.  It's when I get into other services such as, for instance Icecast.  That runs on port 8443, for that, I have to combine two of the certificates into a single cert that Icecast can use.  Then I have to do the same thing, but in a different way for the Kodi interface which runs on port 902.  Then I have to do the same thing, in a different way for the Jellyfin service, which runs on port 8096.  All I want is to secure every single port with SSL.  So if I open a port in my router, to my server, no matter which port it is, it's secured.  That way I can run things out of the box as http, which at least one of mine break when I add ssl.  I have a clunky workaround for it, but it's kind of crappy.






This is my 000-default.conf.


> 
<VirtualHost *:80>
    DocumentRoot "/var/www/html/website"
    ServerName website.com
RewriteEngine on
RewriteCond %{SERVER_NAME} =website.com
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
</VirtualHost>


<VirtualHost *:80>
    DocumentRoot "/var/www/html/website/radio"
    ServerName radio.website.com
RewriteEngine on
RewriteCond %{SERVER_NAME} =radio.website.com
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
</VirtualHost>


<VirtualHost *:80>
    DocumentRoot "/var/www/html/website/cloud"
    ServerName cloud.website.com
RewriteEngine on
RewriteCond %{SERVER_NAME} =cloud.website.com
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
</VirtualHost>


<VirtualHost *:80>
    DocumentRoot "/var/www/html/website/humanity"
    ServerName humanity.website.com
RewriteEngine on
RewriteCond %{SERVER_NAME} =humanity.website.com
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
</VirtualHost>


<VirtualHost *:80>
    DocumentRoot "/var/www/html/website/store"
    ServerName store.website.com
RewriteEngine on
RewriteCond %{SERVER_NAME} =store.website.com
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
</VirtualHost>


<VirtualHost *:80>
    DocumentRoot "/var/www/html/website/books"
    ServerName books.website.com
RewriteEngine on
RewriteCond %{SERVER_NAME} =books.website.com
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
</VirtualHost>


<VirtualHost *:80>
    DocumentRoot "/var/www/html/website/media"
    ServerName media.website.com
</VirtualHost>


<Directory /var/www/>
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
        Allow from all
 </Directory>



I would just like to not have to set up SSL for each service that runs on a different port than 443.

---

### Post by SeijiSensei on 2023-04-13
I prefer to keep each site's configuration in a separate file in /etc/apache2/sites-available.

Your config file has no
```
<VirtualHost *:443>
```
entries, just entries for unencrypted traffic on port 80 with redirects to port 443. Are there corresponding configuration entries for the same sites on 443?

My configurations all have definitions for both port 80 and port 443 like this:
```

<VirtualHost    *:80>
ServerAdmin     webmaster@cyways.com
ServerName      sportsbythenumbers.org
ServerAlias     www.sportsbythenumbers.org

Redirect permanent / https://sportsbythenumbers.org/

</VirtualHost>

<VirtualHost    *:443>
ServerAdmin     webmaster@cyways.com
DocumentRoot    /home/cyways/sites/sportsbythenumbers/public
ServerName      sportsbythenumbers.org
[...]
</VirtualHost>

```

The definition for port 80 uses the simple Apache redirect mechanism to direct traffic to port 443.

I have no idea about any of those other services you are trying to host.

---

### Post by marcusantoniouslee on 2023-05-25
It took years to get to this level of complexity you said so it might take a while for a casual observer to unravel and suggest fixes.

One suggestion I'd make re LetsEncrypt certs is to confugure autorenewal. Setting a cron job to check and renew at a set interval is one option.

Secondly, there is a way to set the Icecast cert to be renewed, concatenated and moved to its folder automatically, hence, that same method can be used for any app that requires a single pem file.

Searching about Icecast SSL will give you all the answers to what I suggested.

All the best.

---

### Post by TheFu on 2023-05-25
I use nginx as my reverse proxy.  It holds the 20-ish SSL certs from LE.  I renew them using acme.sh every 77 days.  Because my back-end servers are a mix, some can be updated while the sites are live and others require bringing down nginx, disabling lots of firewall blocks, updating each cert (I don't like wildcard certs), then bringing up nginx and restarting my ipset firewall rules.

I keep each virtual website in a separate config file like SeijiSensei. It makes solving issues easier for me.  If one site is broken, all the others keep working.  I've used a few different reverse proxies over the decades.  Most didn't support HTTPS, which is what brought me to nginx. It does and it also handles serving static websites and micro-caching for dynamic content.  This micro-caching can make times when lots of concurrent users hit the system not get bogged down by 500 requests per second.  A 10 second micro-cache can drastically handle dynamic content better.

nginx also supports include files, so for settings that are common to all my websites, I setup include file with those settings.  I want the same log format, TLS ciphers (v1.3+), and the same letsencrypt-webroot. Sometimes I need to allow only LAN systems access, so that's in an include file.  1 change inside 1 file and a reload to see the changes used across 20 webapps.

To my recollection, nginx has excellent documentation with examples for specific needs.  But you'll need to know what is possible and what you'd like.

There are lots of ways to create a reverse proxy with nginx.  I use the 
```
upstream **somename** {
   ...
}
server {
   ...
  proxy_pass [http://**somename**](http://**somename**) ;
}

```
method for each service.  It might be easier to use http-proxy. IDK.  [https://docs.nginx.com/nginx/admin-guide/security-controls/securing-http-traffic-upstream/](https://docs.nginx.com/nginx/admin-guide/security-controls/securing-http-traffic-upstream/) explains.

BTW, rather than putting media servers directly onto the internet, have you considered running a VPN server instead?  Then that single connection would allow your approved clients full access to the services and nobody else would have access to hack the different, complex, webapps you are running.  Setting up a wireguard VPN server is really easy.  There are solutions where you don't even need to open any ports.  [https://ubuntu.com/server/docs/wireguard-vpn-introduction](https://ubuntu.com/server/docs/wireguard-vpn-introduction)  If you put everything behind the VPN, you don't need any HTTPS at all.

---

### Post by marcusantoniouslee on 2023-05-26
SSL is for the domain and not the port, I was told by a Let's Encrypt forum admin.

---

### Post by TheFu on 2023-05-26
> **marcusantoniouslee said:**
> SSL is for the domain and not the port, I was told by a Let's Encrypt forum admin.

The term "domain" has many different meanings.  For a website/webserver, we should probably be clear that it is a virtual host in apache or nginx terms.

Certs are for the virtual host ... that is true.  However, you can get a "wildcard" cert which would match *.domain.com ... so any sub-domain virtual host would use the same cert.  This same cert can be used on multiple systems, if you aren't too concerns about real security.

Nobody should be using SSL ciphers anymore (nor for the last 5 yrs).  Today, TLS v1.3 or later should be used.  All earlier ciphers have been hacked.  And to be clear, these connections are about privacy, not really security.
[https://www.youtube.com/watch?v=eRWbNno4sN4](https://www.youtube.com/watch?v=eRWbNno4sN4) explains.
> TLS Doesn’t Do Any Of These Things

[LIST]
[*]    Add Security
[*]    Block Intruders
[*]    Keep Your Credit Card Secret
[*]    Stop Password Theft
[/LIST]

What TLS Does

[LIST]
[*]    Encrypt traffic between client and server
[*]    Identify server, client, or both
[*]    Nothing more.
[/LIST]

Weak TLS Versions

    In early 2021, NSA strongly discourages use of TLS 1.2


---

### Post by SeijiSensei on 2023-05-27
> **marcusantoniouslee said:**
> SSL is for the domain and not the port, I was told by a Let's Encrypt forum admin.
Yes, certificates are tied to domain names. However, SSL website connections use port 443, so there has to be a declaration for that port in any Apache configuration files as I presented in [https://ubuntuforums.org/showthread.php?t=2485878&p=14138713&viewfull=1#post14138713](https://ubuntuforums.org/showthread.php?t=2485878&p=14138713&viewfull=1#post14138713) above.

---

