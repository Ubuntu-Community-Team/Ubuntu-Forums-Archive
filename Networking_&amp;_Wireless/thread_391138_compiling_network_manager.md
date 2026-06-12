---
title: "compiling network manager"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by egle853 on 2007-03-22
I am in the process of installing Network Manager.  My firt attempt to compile the program helped me determine that the C compiler was not installed.  This was done and the compile progressed to the point where the following message was printed:

checking for wireless-tools >= 28pre9... no
configure: error: wireless-tools >= 28pre9 not installed or not functional
  
I checked and the wireless-tools have been installed.  Any ideas?  I am in the process of installing a D-Link WDA-2320 wireless network card.:confused: :confused:

---

### Post by andreas64 on 2007-03-23
Hi,

why don't you install network-manager via Synaptic. It's in the repos.

Andreas

---

### Post by egle853 on 2007-03-23
Thanks for the help.  I do not have an internet connection yet with this PC.  Do you know of a version of network-manager manager that I can load from CD etc..... ?

---

### Post by chili555 on 2007-03-23
Put the CD in the tray, do:```
sudo apt-cdrom add
sudo apt-get-update
sudo synaptic
```You will probably have to play around with the exact command apt-cdrom add. The command I got to work was:```
sudo apt-cdrom -m -d /media/Ubuntu\ 7.04\ i386 add
```The 'Ubuntu\ 7.04 etc. will be different for your system and can be determined by popping the CD into the tray and a file browser will come up. At the top, you can see the exact path. Actually, when you type 'Ubuntu' and press the TAB key, it should fill in the rest.

Open synaptic, temporarily uncheck all the online repos and Reload. You will then see the packages on the CD. Pick network-manager and Apply.

Easier than compiling a tar.gz, I bet.

---

### Post by egle853 on 2007-03-23
Thanks in advance for the help.  I will give it a try tonight and get back to you on how it goes.

---

### Post by spd106 on 2007-03-23
Please bear in mind that network manager is only available on Edgy's Alternate cd, if you have the desktop cd then you are out of luck. 

Instead of downloading the whole Alt cd you can grab the files via another PC as suggested here [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager).

---

### Post by egle853 on 2007-03-23
Thanks for the reply.  How do I get a copy of Edgy's Alternate CD?  My experience is that at some point I may have to obtain a copy of the Alternate CD, where do I get it?  I will also try to get the files from the other source.  

Once again thanks.

---

### Post by spd106 on 2007-03-23
Here's the main site's list
[http://releases.ubuntu.com/6.10/](http://releases.ubuntu.com/6.10/)

You may be able to find a local mirror that would be quicker for a direct download or simply grab the torrent from the link above.

[https://wiki.ubuntu.com/Mirrors](https://wiki.ubuntu.com/Mirrors)

---

### Post by egle853 on 2007-03-23
Thanks,  I just started the download.

---

