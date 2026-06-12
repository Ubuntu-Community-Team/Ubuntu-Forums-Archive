---
title: "[SOLVED] Help setting up a server at home"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by steviefordi on 2008-12-01
I have been using ubuntu for a few months now on my ageing desktop PC. In the new year I want to buy a laptop (on which I will install ubuntu) and use the desktop as a server. The laptop will be a client to the server.
 
I want the server to perform a few tasks:
 
[LIST=1]
[*]It will have a big hard drive for home directories and general data storage.
[*]It will have a printer connected to it for printing from the laptop.
[*]Internet access will be gained through the cable modem that's connected to the server via an ethernet card.
[*]Email Mail boxes are to be stored on the server
[*]Connectivity to the server will be through a wireless network cards (both on the server and laptop).
[*]I also need a backup solution (not sure what is best) to keep all the data backed up.
[/LIST]
Also, as the hardware on the server is quite old, I would like to minimise what runs on it (like no X window system if possible). Applications launched on the laptop are to run on the laptop, and the server's purpose will be storage, printing, backup and as a route to the internet.
 
My problem is I have no idea where to start. Any advice or links to guides and information would be greatly appreciated.
 
Thanks
Steve.

---

### Post by zotkop on 2008-12-01
You might try to start 1 toppic with the same text:
[http://ubuntuforums.org/showthread.php?t=998855](http://ubuntuforums.org/showthread.php?t=998855)

---

### Post by ibutho on 2008-12-01
You could start by browsing through the [Ubuntu Server Guide]("https://help.ubuntu.com/8.04/serverguide/C/index.html").

---

### Post by ghostworkz on 2008-12-01
This is pretty easy.  You can run a "headless" server which pretty much means using ssh or webmin to manage all of the various settings.  To begin with, I would visit this link:
[http://www.howtoforge.com/perfect-server-ubuntu-8.10](http://www.howtoforge.com/perfect-server-ubuntu-8.10)

You probably won't need to use all of the packages for your home server unless you plan on doing webpages.

For file sharing/networking, look at this how to:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

For your backup solution, I suggest Backuppc.  Kinda confusing at first to setup but well worth it for backing up desktops:
[http://www.howtoforge.com/linux_backuppc](http://www.howtoforge.com/linux_backuppc)

Most of these how tos require you to do some cli work.  Some of it, you can download webmin and configure from there.  Of course, change these how tos to fit your particular install/network.

---

### Post by superprash2003 on 2008-12-01
two main things which you require are

for internet connection sharing - [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)
file sharing samba or nfs, same easier - [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by steviefordi on 2008-12-02
Thanks to all you guys for your input. I don't think it's going to be an easy task, but it's certainly possible. Now I have some ideas of where to start I can get planning.

---

