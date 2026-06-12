---
title: "Samba Permission Issues"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by sporez on 2011-03-01
I have been having a mini-nightmare trying to get a samba share set up and running.  I'm hoping someone on here could help me.

I have a flash drive plugged in via USB to a computer running Ubuntu Server.  I have mounted the flash drive to /media/external
I followed [this]("http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/") tutorial to get samba up and running.  I have created an [external] share in the smb.conf file and pointed it to /media/external and am able to connect and view the files on the drive over the network (on a Windows PC) however no matter what I do I cannot gain write access to them.  I get this error:  "You require permission from SMBSERVER\neil to make changes to this file"

I'm not sure if this is samba related or the folder permissions are messed up or what.  At this point I'm pretty confused, so any help is greatly appreciated.  :)

---

### Post by HermanAB on 2011-03-02
Howdy,

Here is a debug guide that may help:
[http://www.aeronetworks.ca/howtos/samba-debug-howto.html](http://www.aeronetworks.ca/howtos/samba-debug-howto.html)

---

