---
title: "Networking server question?"
date: 2005-04-23
forum: Networking &amp; Wireless
---

### Post by dfghost on 2005-04-23
How do i set up Ubuntu as a web server, for html and file sharing?  I have a 56k dial-up modem, that's not working on Ubuntu right now, but i'm feed up with it and thinking of getting Comcast cable net.  Any help is appreciated in advance and thanks.

---

### Post by localzuk on 2005-04-23
For a simple web server, run 'sudo apt-get install apache2' in a terminal.

This will install the apache 2 web server, with its base web directory being: /var/www/html

Hope this is of help. Also, have a look at: [http://ubuntuguide.org/#apachehttpserver](http://ubuntuguide.org/#apachehttpserver)

for more information about web servers and Ubuntu

---

### Post by ifrflyer on 2005-04-23
For file serving, install samba and create a workgroup among your linux/windows/mac clients. sudo-apt-get install samba and make sure that any linux machine which intends to mount samba shares across the net has smbfs (you can also sudo apt-get  install smbfs) .

---

