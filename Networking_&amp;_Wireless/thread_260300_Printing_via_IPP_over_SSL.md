---
title: "Printing via IPP over SSL"
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by rene86 on 2006-09-18
Hi, I try to use IPP in his direct meaning, via internet.

The situation:
For this, I have installed Apache2 with a nice page to switch off the pc and to access the harddisk via webdav. this runs fine.
because i dont trust the internet as much as my private network this apache-installation uses ssl und http-auth. to use just one port (cause off my router) I use the apache mod_proxy to access the cups printer directly via this apache "connection". this also runs fine, i can access the cups-pages and a friend of mine printed the testpage from 20km away...

The question:
but how can I setup the client-cups to print via this ssl and http-auth secured printer?

---

### Post by rene86 on 2006-09-18
Now I have tried with Windows XP and it runs perfect, so it has to be possible...

---

### Post by tbonius on 2006-09-18
From the cupsd.conf man page:

SSLListen : Listens on the specified address and port for encrypted  connections.

SSLPort : Listens on the specified port for encrypted connections.

From the CUPS Documentation Site:
[http://www.cups.org/documentation.php/ref-cupsd-conf.html](http://www.cups.org/documentation.php/ref-cupsd-conf.html)

ServerCertificate

Examples:
ServerCertificate /etc/cups/ssl/server.crt

Description

The ServerCertificate directive specifies the location of the SSL certificate file used by the server when negotiating encrypted connections. The certificate must not be encrypted (password protected) since the scheduler normally runs in the background and will be unable to ask for a password.

The default certificate file is /etc/cups/ssl/server.crt.

ServerKey

Examples:
ServerKey /etc/cups/ssl/server.key

Description

The ServerKey directive specifies the location of the SSL private key file used by the server when negotiating encrypted connections.

The default key file is /etc/cups/ssl/server.crt.

Hope this is helpful.

T

---

### Post by rene86 on 2006-09-19
My CUPS-Server is already secured with SSL via apache. i want to print to this secured cups.

---

