---
title: "wins client"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by shlomiarfa on 2008-05-28
hello all

i need your help on this case :

i have ubuntu 7.10 on a pc machine.
the machine got IP address from dhcp.
i installed NAGIOS 2 on the ubuntu machine and i want to connect to that NAGUIOS application using my windows pc **_not_** via IP but via **name **.
right now i can connect only this way :
[http://10.119.1.156/nagios2/](http://10.119.1.156/nagios2/)

and i want to connect with a name like :

[http://example](http://example)

please specify what are the steps i have to do.

---

### Post by wdaniels on 2008-05-28
I think you will need at least to be running Samba (to set the NETBIOS name), so that is the first thing to check (System->Administration->Services).

---

### Post by shlomiarfa on 2008-05-28
samba service is runing on my ubuntu machine.
how i configure the IP address of the machine and the name ?

---

### Post by wdaniels on 2008-05-28
In the [global] section of /etc/samba/smb.conf. I think the settings is "netbios name" although it should just use the hostname by default. 

Unfortunately I don't know a whole lot about Samba and don't even use it myself, so hopefully someone else can give you better advice...I just answered with my best guess because nobody else had and to bump the thread :D

The part of Samba that handles NetBIOS is called nmbd, so you could try:

```
man nmbd
```

or google for more info. There is also winbind but I think this is for the opposite case (resolving NetBIOS names on the Linux box). Sorry I can't be of more help...

---

### Post by shlomiarfa on 2008-05-28
thanks for your help

---

### Post by Iowan on 2008-05-28
You can set up a Samba server to be a WINS client OR server (not both).  It's also possible the DHCP server might act as a nameserver, but **/etc/dhcp3/dhclient.conf** should have the line```
;send host-name "<hostname>";

``` uncommented and the proper hostname used.

---

