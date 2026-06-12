---
title: "Need to connect to work PC. Remote desktop for Linux?"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by hazypictures on 2009-10-20
My office has a way for me to connect to my work desktop files from home. With Vista, I use Remote Desktop but now I am (happily) running Ubuntu and our 'help desk'  says that they don't support Linux. 

Is there a program that will work like Remote Desktop on Linux for this purpose?

---

### Post by dvlchd3 on 2009-10-20
VNC

[http://www.realvnc.com/products/free/4.1/index.html](http://www.realvnc.com/products/free/4.1/index.html)

---

### Post by ZankerH on 2009-10-20
> **dvlchd3 said:**
> VNC

[http://www.realvnc.com/products/free/4.1/index.html](http://www.realvnc.com/products/free/4.1/index.html)

Correct. Here's a ubuntu-specific guide:

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by wojox on 2009-10-20
rdesktop

[http://www.rdesktop.org/](http://www.rdesktop.org/)

---

### Post by linux-hack on 2009-10-20
the problem you'll have is security ... you need to encrypt the transfers between desktops... you can use OpenSSH with VNC

---

### Post by dvlchd3 on 2009-10-20
> **boogy9 said:**
> the problem you'll have is security ... you need to encrypt the transfers between desktops... you can use OpenSSH with VNC

That is a much better solution.  Below is a guide that should help you out.  It explains, and links to, setting up SSH, securing SSH, and setup VNC servers and clients.

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by dgoosens on 2009-10-20
I am more or less in the same situation
But I do have to connect to my company through a VPN.

After that, I simply use tsclient
This works great

---

### Post by The Cog on 2009-10-20
> **hazypictures said:**
> My office has a way for me to connect to my work desktop files from home. With Vista, I use Remote Desktop but now I am (happily) running Ubuntu and our 'help desk'  says that they don't support Linux. 

Is there a program that will work like Remote Desktop on Linux for this purpose?

There is a remote desktop client for Linux called **rdesktop**. This allows you to connect from a Linux workstation to a Windows server. You can launch it from the command line like:
```
rdesktop 1.2.3.4
```
or you can launch it from the menus:
Internet->Terminal Server Client
Chose RDP as the protocol.
 
I don't think there is an RDP server program to allow windows clients to connect to an Ubuntu server (use VNC or NoMachine instead), but I think that's not what you are trying to do anyway.

---

### Post by ukripper on 2009-10-20
If you want server program which can even work on low bandwidth securely. Nothing beats Freenx (free implementation of Nomachine's NX)

Here is the guide:
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

Here is some quote taken from the FREENX website:
> NX is an exciting new technology for remote display. It provides near local speed application responsiveness over high latency, low bandwidth links. The core libraries for NX are provided by NoMachine under the GPL. FreeNX is a GPL implementation of the NX Server and NX Client Components. 

I use it daily to log on to my home ubuntu machines from work.

---

### Post by hazypictures on 2009-10-22
Thank you! I'm still an absolute beginner here and your reply gave me enough info to get onto my office remote desktop in about 2 minutes. I'm sure that the VNC solution is interesting, but all that I  need to do it get to the work server to get some files, etc.

Thanks!

---

### Post by hazypictures on 2009-10-22
Thank you! I'm still an absolute beginner here and your reply gave me enough info to get onto my office remote desktop in about 2 minutes. I'm sure that the VNC solution is interesting, but all that I need to do it get to the work server to get some files, etc.

I used the menu suggestion:
> **The Cog said:**
> You can launch it from the menus:
Internet->Terminal Server Client
Chose RDP as the protocol.
 


It is magic. Thank you!

---

