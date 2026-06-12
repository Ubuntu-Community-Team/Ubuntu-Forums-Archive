---
title: "HowTo: Local Transparent Caching Proxy using Apache"
date: 2007-11-22
forum: Networking &amp; Wireless
---

### Post by IntuitiveNipple on 2007-11-22
If you do a lot of development or installation testing that requires repeated download of the same (large) packages it makes sense to cache the content locally since it saves time and bandwidth.  If you're also already using **apache2** it makes little sense to install squid as well since apache2 with **mod_proxy** and **mod_cache** can do the job too.

I use this to accelerate the creation of User Mode Linux root file-system images, KVM/QEMU Virtual Machine guest images, and pbuilder. If extended to work on a LAN<>Internet gateway/firewall it could be used to cache updates and general apt-get/aptitude/synaptic requests for all clients on the LAN.

This is how to use apache2 as a localhost transparent caching proxy.
[list=1]
[*] Add additional modules to apache2 startup
[indent]Start a terminal and do:
```
$ cd /etc/apache2/mods-enabled
$ sudo ln -s ../mods-available/proxy.load proxy.load
$ sudo ln -s ../mods-available/proxy.conf proxy.conf
$ sudo ln -s ../mods-available/proxy_http.load proxy_http.load
$ sudo ln -s ../mods-available/cache.load cache.load
$ sudo ln -s ../mods-available/disk_cache.load disk_cache.load
$ sudo ln -s ../mods-available/rewrite.load rewrite.load

```
I've deliberately *not* linked disk_cache.conf since we want to set rules specific to the proxy virtual host.
[/indent]
[*] Add an additional port for proxying
[INDENT]Edit **/etc/apache2/ports.conf** and add the line "Listen 127.0.0.1:8080"
```

$ sudo sh -c "grep '127.0.0.1:8080' /etc/apache2/ports.conf >/dev/null || echo 'Listen 127.0.0.1:8080' >> /etc/apache2/ports.conf"

```
[/INDENT]
[*] Create a new Virtual Host for the proxy
[indent]It is easiest to create a new file in gedit and then save it. Press Alt+F2 then type "**gksudo gedit**". This will run the text editor as user root so you can save the file. Copy and paste the following Virtual Host definition, amending it to be specific to your network:
```
# Listen locally. This needs modifying (along with the associated netfilters rule)
# if you want to proxy for a LAN, if this machine is a gateway/firewall
<VirtualHost 127.0.0.1:8080>
	ServerName proxy.lan.mydomain.net
	ServerAdmin webmaster@mydomain.net

	<IfModule mod_rewrite.c>
		RewriteEngine On
		RewriteLog /var/log/apache2/rewrite.log
		RewriteLogLevel 9

		# Only rewrite requests that don't already have a Via: header
		# If there is a possibility of this proxy being in a chain 
		# then you'll have to test the Via hostname value as well using something like this
 		# RewriteCond %{HTTP:Via} !.*proxy.lan.mydomain.net.*
		RewriteCond %{HTTP:Via} ^$

		# Alter the GET /... to GET http://host/... so it is treated as
		# a proxy request, and then forward it to mod_proxy immediately
		RewriteRule (.*) http://%{HTTP_HOST}$1 [P]
	</IfModule>

	<IfModule mod_proxy.c>
		ProxyRequests On
		ProxyVia On
		# don't proxy for LAN addresses
		NoProxy localhost 10.0.0.0/8 127.0.0.0/8 192.168.0.0/16 .lan.mydomain.net
		# default LAN domain for use where FQDNs aren't being used
		ProxyDomain .lan.mydomain.net
		ProxyBadHeader Ignore
		ProxyStatus On
		ProxyPreserveHost On

		# limit connections to LAN clients
		<Proxy *>
			Order Deny,Allow
			Deny from all
			Allow from 10.0.0.0/8
			Allow from 127.0.0.0/8
			Allow from 192.168.0.0/16
		</Proxy>

		<IfModule mod_cache.c>
			# 1 hour (the default) before checking if content has expired
			CacheDefaultExpire 3600

			<IfModule mod_disk_cache.c>
				CacheRoot /var/cache/apache2/mod_disk_cache
				# To cache all requests the path here should be /
				# To cache just Ubuntu packages you'd use
				# CacheEnable disk http://archive.ubuntu.com
			 	CacheEnable disk /
				# make sure BIG packages are cached (up to 20MB)
				CacheMaxFileSize 20000000
				CacheDirLevels 5
				CacheDirLength 3
			</IfModule>
		</IfModule>
	</IfModule>
</VirtualHost>

# allow the proxy information to be reported by /server-status
<IfModule mod_status.c>
	ExtendedStatus On
</IfModule>

```
Now save the file to **/etc/apache2/sites-available/proxy**
[/indent]
[*] Enable the new site
[indent]
```
$ cd /etc/apache2/sites-enabled
$ sudo ln -s ../sites-available/proxy proxy

```
[/indent]
[*] Add a conditional redirection rule to netfilters
[indent]This will redirect HTTP requests transparently to port 8080 **only** if they don't originate from the apache **www-data** group ID.
```
$ grep 'www-data' /etc/group
$ sudo  iptables -t nat -A OUTPUT -m owner ! --gid-owner 33 -p tcp --dport 80 -j REDIRECT --to-port 8080

```
The restriction on the group is so that netfilters doesn't get stuck in an endless loop of transparently redirecting the Proxy's outgoing requests as well as the applications making the requests.

You will need to save this rule using your preferred firewall manger so that it is loaded at system or network start-up. It can be added manually to the **Firestarter** configuration files by adding the following lines to **/etc/firestarter/outbound/setup** - you'll need to make the file writeable by root first
```
$ sudo chmod 660 /etc/firestarter/outbound/setup
```
```
# enable HTTP transparent proxy to apache2 on 127.0.0.1:8080
$IPT -t nat -A OUTPUT -m owner ! --gid-owner 33 -p tcp --dport 80 -j REDIRECT --to-port 8080

```
If you are reworking this method to support operation on a LAN gateway you can't use the **REDIRECT** target since it only works on the localhost in the nat table PREROUTING or OUTPUT chains. Instead, you'll need to use the DNAT target and adjust the parameters.
[/indent]
[*] Restart apache2
[indent]```
$ sudo /etc/init.d/apache2 reload

```
[/indent]
[/list]

---

### Post by X-Stranger on 2008-01-29
Thank you for this guide. It was very useful for me, but I've found one issue I can't resolve: 
Google Reader can't work through this proxy. In apache log I see the next message: 

```
[Tue Jan 29 09:53:33 2008] [error] [client 127.0.0.1] error parsing URL //: Invalid host/port
```

I've tried to edit rewrite rules but still have no luck. Could anybody please help me?

---

### Post by X-Stranger on 2008-01-29
Currently I've found workaround:

```

-A OUTPUT -p tcp -m owner ! --gid-owner www-data -m tcp -d www.google.com --dport 80 -j ACCEPT                                             
-A OUTPUT -p tcp -m owner ! --gid-owner www-data -m tcp --dport 80 -j REDIRECT --to-ports 8080

```

I'm using these two iptables rules instead of one. First rule grants accessing google resources without proxying, the second rule is the same as in original HowTo.

---

