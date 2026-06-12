---
title: "dns and dhcp server with updates"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by fredraket on 2007-05-20
Hi,
i'm a beginner in linux, i've tried allready suse oss (because they had that yast  :D )

i just want to replace my win2k box, with a linux box,
i've now chosen ubuntu server, and could setup webmin
and i can get the dns and dhcp working
but all my workstations (osx and winxp) can't ping each other with their hostname

the problem is that my dhcp server doesn't update my dns server...

could anyone give me any sugestions???
if possible with webmin??

or should i do it with the configfiles???

thanks in advance

---

### Post by beazer on 2007-05-23
I found this link really helpful:

[http://doc.gwos.org/index.php/DynamicDNS](http://doc.gwos.org/index.php/DynamicDNS)

Cheers
Rob

---

### Post by fredraket on 2007-05-23
thx for the reply, i'll test it :D
and let you know

---

### Post by fredraket on 2007-05-23
this is more the case when you have two servers...

tried to change a bunch of options (keys, allow update, etc...) but no change
clients get an ipadress, can querry names,  but still the clients don't get into the bind database

i'm also not really sure if i have bind9

any idea how to check this???
i can restart bind with webmin but when i restart it with the comand prompt
#
 * Stopping domain name service... bind 
 rndc: connection to remote host closed
This may indicate that the remote server is using an older version of
the command protocol, this host is not authorized to connect,
or the key is invalid.
                                                                         [fail]
 * Starting domain name service... bind           [fail]

---

