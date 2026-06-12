---
title: "Linux access from Windows"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by NicoV on 2008-04-09
Hello, I am a bit new to Linux and I would like to know how can I do the following using Edubuntu. We have different PC's on a school and instead of using a Thin client loader with different CD-ROMS (one for each network type) I would like to know if there is a way to access Linux server from a terminal window on Windows. So, PC's have their Windows OS to boot, but users have to go to Linux to see the real world.... I gues is a sort of Terminal Server client, but don't know where to find it for edubuntu.

Thank you

Nicolas
:popcorn:

---

### Post by koshari on 2008-04-09
cygwin-ssl?

---

### Post by Kebabman on 2008-04-09
I'm not totally sure if this is what you are looking for but if you just want terminal access to a Linux server you can just add users to the Linux server and then ssh into it using [Putty]("http://www.putty.org/").

---

### Post by Eiríkr on 2008-04-09
I'll ditto Kebabman here and say ssh + PuTTY is your best bet for CLI access.  If, on the other hand, by "see the real world" you mean using a GUI, you'll want something like VNC.  I have no experience setting up VNC, so plug "VNC" into the forum search box at the top right of any forum page to look up related posts.  

Cheers,

Eiríkr

---

### Post by Kebabman on 2008-04-10
If it is GUI connectivity you want I would recommend something along the lines of [Exceed]("http://connectivity.hummingbird.com/products/nc/exceed/"). This will allow you to connect to the X server running on the Linux machine and have a separate X session for each user.

VNC Could also be used for this by having multiple instances running, each with their own X session but this would invoke a much larger overhead on the Linux box I believe.

---

