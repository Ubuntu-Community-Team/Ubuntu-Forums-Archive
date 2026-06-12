---
title: "Use squid for proxy"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by randumnumber on 2010-11-20
Hello all.

I have been working for a few hours to get squid set up as a proxy and have had no luck. I have a server at home that I have installed squid on. I would like to use it as a proxy while I am on other networks(over wan). I have opened up the port that I set in the squid.conf file though my router. I have also installed foxyproxy which is an addon for firefox to use proxys, I have tried to test it. But it tells me the connection is refused by the proxy. Is there additional setup required in squid? 

If you have used squid before please inform me on how the setup process should go. 
I have looked at a few resources but they are over 2 years old and are not specific to my application (the guides i have found are on how to use squid on a computer acting as a router to increase cache speeds).

My setup is like this:

server running squid -> router with port open for squid -> internet

Any help or links to resources would be appreciated.

Thank you.

---

### Post by SeijiSensei on 2010-11-20
Squid isn't a generalized proxy; it's designed to cache and accelerate web access.

If you're looking for a general proxy, take a look at [SOCKS]("http://en.wikipedia.org/wiki/SOCKS").

If you're simply looking to proxy Firefox, you don't need any add-ons; proxy support is available by configuring Edit > Preferences > Advanced > Network > Settings.

---

### Post by randumnumber on 2010-11-20
Thank you, I knew something wasn't right, but i could not find any other programs. I will mark this as solved.

---

### Post by randumnumber on 2010-11-21
OP please unmark solved.

I have discovered how to use ssh to make a socks connection. its easy enough.

NEW PROBLEM
I would like to use apache as a forward proxy. I found some basic stuff and added this to my /etc/apache2/sites-enabled/000-default page
```


#PROXY
       <Directory proxy:*>
       Order Deny,Allow
       Deny from none
       Allow from all
      </Directory>

```
of course this is JUST for testing purposes and i will change the allow to the appropriate IP address.

if i just add the above code and then try to use firefox to proxy though my server it takes me to the default IT WORKS page no matter what i do!?! im sure im not getting something right so here is the full 000-default
```


<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
#PROXY	
       <Directory proxy:*>
       Order Deny,Allow
       Deny from none
       Allow from all
      </Directory>
#cache usage of proxy
#CacheRoot "/usr/local/apache/proxy"
#CacheSize 5
#CacheGcInterval 4
#CacheMaxExpire 24
#CacheLastModifiedFactor 0.1
#CacheDefaultExpire 1

       <Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

As you can see it is the basic default page, with some proxy stuff added. Another thing i have to comment out the Cache stuff or the apache server fails to restart with this error.
```


Invalid command 'CacheRoot', perhaps misspelled or defined by a module not included in the server configuration

```


What am i doing wrong here?

---

### Post by SeijiSensei on 2010-11-22
> **randumnumber said:**
> if i just add the above code and then try to use firefox to proxy though my server it takes me to the default IT WORKS page no matter what i do!?! 

Your <VirtualHost> definition doesn't include a ServerName directive.  If you want to access [http://somehost.example.com/](http://somehost.example.com/), you must have a VirtualHost definition with the directive

ServerName somehost.example.com

Otherwise you'll always end up on the default page.

---

### Post by randumnumber on 2010-11-22
Thanks, now it does exactly what i want it to do.

---

