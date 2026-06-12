---
title: "Ubuntu server LAMP"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by shanep-server on 2010-11-04
I have a Lucid Ubuntu server running on DHCP 192.168.2.2 

I installed LAMP on this machine.

From my desktop on the network.. i open Mozilla Firefox and in the browser I type "192.168.2.2" and the following is returned.

Forbidden

You don't have permission to access /index.html on this server.
Apache/2.2.14 (Ubuntu) Server at 192.168.2.2 Port 80

Any Idea's?

---

### Post by Barriehie on 2010-11-04
> **shanep-server said:**
> I have a Lucid Ubuntu server running on DHCP 192.168.2.2 

I installed LAMP on this machine.

From my desktop on the network.. i open Mozilla Firefox and in the browser I type "192.168.2.2" and the following is returned.

Forbidden

You don't have permission to access /index.html on this server.
Apache/2.2.14 (Ubuntu) Server at 192.168.2.2 Port 80

Any Idea's?

So what are the permissions you've got for DocumentRoot and for the files therein?

---

### Post by shanep-server on 2010-11-05
Ok I ssh into server...

cd /var/www/
sudo chmod 777 index.html

from desktop 192.168.2.2 worked an viewed the Index.html file..

My question is what permissions should I give /var/www folder permissions so its not a security risk... Being that is will be used to host an actual website. 

would sudo chmod 777 -R /var/www do what I want an not be a security risk. I don't want to have to chmod every file i put in here.

---

### Post by bioterror on 2010-11-05
> **shanep-server said:**
> Ok I ssh into server...

cd /var/www/
sudo chmod 777 index.html

from desktop 192.168.2.2 worked an viewed the Index.html file..

My question is what permissions should I give /var/www folder permissions so its not a security risk... Being that is will be used to host an actual website. 

would sudo chmod 777 -R /var/www do what I want an not be a security risk. I don't want to have to chmod every file i put in here.
 maybe 755

---

### Post by Barriehie on 2010-11-05
> **bioterror said:**
> maybe 755

755 here too.

You can also use /etc/apache2/httpd.conf to set /path/file permissions and don't advertise i.e.:

In httpd.conf
```

#
# Minimize Advertising / No version info.
#
ServerSignature off
ServerTokens Prod
```

Might think about running fail2ban or denyhosts also.

Edit: I was averaging an attack every 25 or so minutes!  Might find this [link](http://www.petefreitag.com/item/505.cfm) useful.

---

### Post by shanep-server on 2010-11-05
Thank you guys for all your help

---

