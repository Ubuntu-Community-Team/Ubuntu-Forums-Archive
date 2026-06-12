---
title: "Apache2 SSL doesn't seem to be working"
date: 2016-05-13
forum: Networking &amp; Wireless
---

### Post by rlongfield on 2016-05-13
I believe I have setup Apache correctly to use SSL but I seem to have missed a step or done something terribly wrong :)

http works ok so I know Apache is running.

ssl.conf and ssl.load are enabled.

When I try to access any https site (default-ssl included) I get a message about the website not being available.

thanks,

---

### Post by SeijiSensei on 2016-05-13
What do you see in the SSL site's error log in /var/log/apache2?

---

### Post by rlongfield on 2016-05-24
Sorry for the long wait in my reply.
I went back to redo everything starting with new certs since I had bumbled things up (or so I had thought)

So I followed the steps on this page ([https://www.maketecheasier.com/apache-server-ssl-support/)to](https://www.maketecheasier.com/apache-server-ssl-support/)to) create new certs and keys. I accepted the defaults when creating the ca.csr.

I then modded the 000-defaults conf file as the site said, restarted Apache 2 and got the same error message (This webpage is not available, Err_Timed_Out)

Here is the contents of the error log from Apache restart.

[INDENT][Tue May 24 13:02:40.014520 2016] [ssl:warn] [pid 12780] AH01909: RSA certificate configured for localhost:443 does NOT include an ID which matches the server name
[Tue May 24 13:02:40.014743 2016] [ssl:warn] [pid 12780] AH02292: Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Tue May 24 13:02:40.395788 2016] [ssl:warn] [pid 12781] AH01909: RSA certificate configured for localhost:443 does NOT include an ID which matches the server name
[Tue May 24 13:02:40.396081 2016] [ssl:warn] [pid 12781] AH02292: Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Tue May 24 13:02:40.418581 2016] [mpm_prefork:notice] [pid 12781] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.16 OpenSSL/1.0.1f configured -- resuming normal operations
[Tue May 24 13:02:40.418702 2016] [core:notice] [pid 12781] AH00094: Command line: '/usr/sbin/apache2'[/INDENT]

---

### Post by SeijiSensei on 2016-05-24
The SSL server settings are in /etc/apache2/sites-available/ssl-default.conf.  That's the file you need to modify.  Revert the 000-defaults.conf back to its original form, or reinstall Apache and start over.

---

### Post by rlongfield on 2016-05-25
Ok so I reverted the file, I never delete just uncomment :)

I updated the default-ssl file in the correct manner (I think) and I am getting this error message when I try to restart Apache2

[INDENT][Wed May 25 14:56:41.523852 2016] [ssl:emerg] [pid 20049] AH02241: Init: Unable to read server certificate from file /etc/apache2/ssl/ca.key
[Wed May 25 14:56:41.524032 2016] [ssl:emerg] [pid 20049] SSL Library Error: error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag
[Wed May 25 14:56:41.524053 2016] [ssl:emerg] [pid 20049] SSL Library Error: error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error (Type=X509)
[Wed May 25 14:56:41.524061 2016] [ssl:emerg] [pid 20049] AH02312: Fatal error initialising mod_ssl, exiting.[/INDENT]

Here is my conf file:

<IfModule mod_ssl.c>
        <VirtualHost _default_:443>
                ServerAdmin webmaster@localhost

                DocumentRoot /var/www/html

                SSLEngine on
                SSLCertificateFile /etc/apache2/ssl/ca.key
                SSLCACertificatePath /etc/apache2/ssl/
                SSLCACertificateFile /etc/apache2/ssl/ca.crt

                <FilesMatch "\.(cgi|shtml|phtml|php)$">
                                SSLOptions +StdEnvVars
                </FilesMatch>

                <Directory /usr/lib/cgi-bin>
                                SSLOptions +StdEnvVars
                </Directory>

                BrowserMatch "MSIE [2-6]" \
                                nokeepalive ssl-unclean-shutdown \
                                downgrade-1.0 force-response-1.0
                BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown

        </VirtualHost>
</IfModule>

---

### Post by SeijiSensei on 2016-05-25
Where did you get those certificate files from?  Does it work if you use the defaults that come with Ubuntu in /etc/ssl?

---

### Post by rlongfield on 2016-05-26
The certs were generated on the computer using the steps on the webpage in my previous post.

I have commented out those certs and removed the comments for the default ones

                 SSLCertificateFile     /etc/ssl/certs/ssl-cert-snakeoil.pem
                 SSLCertificateKeyFile /etc/ssl/private/ssl-cert-snakeoil.key


Here is the results of the error log:

[INDENT][Thu May 26 09:36:36.109098 2016] [ssl:warn] [pid 25444] AH02292: Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Thu May 26 09:36:36.335302 2016] [ssl:warn] [pid 25445] AH02292: Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Thu May 26 09:36:36.355128 2016] [mpm_prefork:notice] [pid 25445] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.16 OpenSSL/1.0.1f configured -- resuming normal operations
[Thu May 26 09:36:36.355339 2016] [core:notice] [pid 25445] AH00094: Command line: '/usr/sbin/apache2[/INDENT]

---

### Post by rlongfield on 2016-05-26
So a further update as I've done a bit of digging.

I ran the following commands and got some strange results.

[INDENT]b@zues:/etc/apache2$ source /etc/apache2/envvars
b@zues:/etc/apache2$ apache2 -t -D DUMP_MODULES -f /etc/apache2/apache2.conf
AH00526: Syntax error on line 33 of /etc/apache2/sites-enabled/default-ssl.conf:
SSLCertificateKeyFile: file '/etc/ssl/private/ssl-cert-snakeoil.key' does not exist or is empty
b@zues:/etc/apache2$ sudo ls /etc/ssl/private/
ssl-cert-snakeoil.key
b@zues:/etc/apache2[/INDENT]

I'm a little confused as ssl-cert-snakeoil.key is the default. It clearly exists so the file must be empty?

---

### Post by rlongfield on 2016-06-14
I've done some more testing.

I've started over with this whole process. I created a new cert and setup a conf file based on default-ssl.conf. I followed the steps here ([https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04))

conf file:
```
<IfModule mod_ssl.c>
    <VirtualHost _default_:443>
        ServerAdmin [email]admin@example.com[/email]
        ServerName thel******s.TLD
        ServerAlias thel******s.TLD
        DocumentRoot /var/www/html
        ErrorLog ${APACHE_LOG_DIR}/thel******s.error.log
        CustomLog ${APACHE_LOG_DIR}/thel******s.access.log combined
        SSLEngine on
        SSLCertificateFile /etc/apache2/ssl/apache.crt
        SSLCertificateKeyFile /etc/apache2/ssl/apache.key
        <FilesMatch "\.(cgi|shtml|phtml|php)$">
                        SSLOptions +StdEnvVars
        </FilesMatch>
        <Directory /usr/lib/cgi-bin>
                        SSLOptions +StdEnvVars
        </Directory>
        BrowserMatch "MSIE [2-6]" \
                        nokeepalive ssl-unclean-shutdown \
                        downgrade-1.0 force-response-1.0
        BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown
    </VirtualHost>
</IfModule>
```


When I restarted Apache there were no errors.
I ran the following commands just to be sure which early produced errors, but this time there were no errors:
```
bt@zues:/etc/apache2/sites-available$ source /etc/apache2/envvars
bt@zues:/etc/apache2/sites-available$ apache2 -t -D DUMP_MODULES -f /etc/apache2/apache2.conf
```

And I got this for the output:
```

Loaded Modules:
 core_module (static)
 so_module (static)
 watchdog_module (static)
 http_module (static)
 log_config_module (static)
 logio_module (static)
 version_module (static)
 unixd_module (static)
 access_compat_module (shared)
 alias_module (shared)
 auth_basic_module (shared)
 authn_core_module (shared)
 authn_file_module (shared)
 authz_core_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgi_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 filter_module (shared)
 mime_module (shared)
 mpm_prefork_module (shared)
 negotiation_module (shared)
 php5_module (shared)
 proxy_module (shared)
 proxy_http_module (shared)
 reqtimeout_module (shared)
 rewrite_module (shared)
 setenvif_module (shared)
 socache_shmcb_module (shared)
 ssl_module (shared)
 status_module (shared)
```

When I try to connect to the URL using HTTP everything works and I get the Apache default page (handled by 000-default.conf). When I use HTTPS I get a "ERR_TIMED_OUT message. However when I go to the Apache2 error log the only entry I get is the following:
```
[Tue Jun 14 10:07:11.773608 2016] [ssl:warn] [pid 16527] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
```

I am at a complete loss here.

---

