---
title: "apache2, https"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by oger5 on 2011-03-30
Hi,
I installed some webware. ( It was ajaxterm: [http://antony.lesuisse.org/software/ajaxterm/]("http://antony.lesuisse.org/software/ajaxterm/") but it is not so important what is it. It is working, listening on port 8022, how i want to. And it is accepting connections only from localhost. I believe it behaves how it should behave.)

And now I am trying to use configuration example from their page to configure apache to use mod_proxy, to make secured proxy to localhost:8022 over https.

I added to apache configuretion this:

<VirtualHost *>
        ServerName ajaxterm.nameofmyserver.cz:443
        HostnameLookups Double
        CustomLog /var/log/apache2/access.log combined env=!dontlog
        SetEnvIf Request_URI "^/u" dontlog
        ErrorLog /var/log/apache2/error.log
        Loglevel warn
        SSLEngine On
        SSLCertificateFile /etc/apache2/ssl/apache.pem

        ProxyRequests Off
        <Proxy *>
                AuthUserFile /srv/ajaxterm/.htpasswd
                AuthName EnterPassword
                AuthType Basic
                require valid-user

                Order Deny,allow
                Allow from all
        </Proxy>
        ProxyPass / http://localhost:8022/
        ProxyPassReverse / http://localhost:8022/
</VirtualHost>

and when I run sudo /etc/init.d/apache2 start
I get this error:

 * Starting web server apache2                                                                                                                                              Syntax error on line 9 of /etc/apache2/sites-enabled/ajaxterm2:
Invalid command 'SSLEngine', perhaps misspelled or defined by a module not included in the server configuration
                                                                                                                                                                     [fail]

I was looking on internet for this SSLEngine error and if I understand it correctly I need mod_ssl to get this work. Am I correct?

And if so How can I install it? I looked on [http://modssl.org/]("http://modssl.org/") I wanted to download source and compile it but it seems like i need to compile and install apache with it too. But I allready have apache and I dont want to install it again.

By the way the file /etc/apache2/ssl/apache.pem and the directory /etc/apache2/ssl which I mentioned in that config file doesn't still exit. But I hope it solves somehow with the SSLEngine error.

I am not even sure if I am searching the proble at the right place. :(
Thans for help.

---

