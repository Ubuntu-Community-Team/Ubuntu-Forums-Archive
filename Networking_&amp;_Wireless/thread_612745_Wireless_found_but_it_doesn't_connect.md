---
title: "Wireless found but it doesn't connect"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by UnBr34KaBl3 on 2007-11-14
Well, ubuntu finds the network i cklick it and it starts to connect. It tries for a long time but it never manages to connect and then i just goes back to how it was before. I can click it again but the same thing happens. I have Ubuntu 7.10 now. A strange thing is that it worked with no problem at all when i tried it on the Ubuntu 7.04 Live disc.

---

### Post by kasperfish on 2007-11-14
hi what is your wireless card chipset (check hardware on ubuntu)?
what drivers are you using?

---

### Post by UnBr34KaBl3 on 2007-11-14
It's an USB connected card: Compex WLU11A. I haven't installed any drivers. Can I install the drivers from the cd that is for windows??

---

### Post by kasperfish on 2007-11-14
no you can't use the windows drivers. you need to install atmel driver for your card.
use synaptics to download en istall it.

---

### Post by UnBr34KaBl3 on 2007-11-14
Ok, how do i do that, I'l have to download them to windows and open them with ubuntu, i guess. But where do i get the drivers and how do I install it?

---

### Post by Znort_Ubern00b on 2007-11-14
in ubuntu
System - admin - synaptic package manager

search for atmel

right click atmel when it comes up in search result box and mark for installation then click apply button.

---

### Post by UnBr34KaBl3 on 2007-11-14
It's already in the OS? A windows junkie like me is used to download everything:P

---

### Post by Znort_Ubern00b on 2007-11-14
The synaptic looks at repositories where the software is held, you can search for, download and install from there...which it does with minimal user interface.

---

### Post by kasperfish on 2007-11-14
sorry for the incomplete instructions... i tought you knew more about linux.

in fact you have to install at76c503a-source wich you can find via synaptic with the keyword atmel.

MIND:
these drivers will only work when your kernel version is =>2.6.20

hope this helps...
cheers

---

### Post by UnBr34KaBl3 on 2007-11-14
It's offtopic but how do i make MP3 files work? I've tried to download wm32codecs or what its called. But i just can't find where to download them.

---

### Post by kasperfish on 2007-11-14
open them with a player...
you can add software 

*from synaptic
* from : applications/add-remove...

in this case you best use the latter option.
search for mp3 and install a player

trie open your mp3 by clicking it or via an application

---

### Post by UnBr34KaBl3 on 2007-11-14
Are you sure you doesn't have to download anything? It doesn't find anything when I serch for Atmel or that version number. There is another strange thing to it doesn't find the wireless everytime you start ubuntu. It does find it every twice time i restart:confused:

EDIT: Yes I tried to open a file but it didn't install it becouse i didn't have working internet connection.

---

### Post by Znort_Ubern00b on 2007-11-14
to use synaptic you need to have internet connection working. this may be why it didn't find anything.

---

### Post by kasperfish on 2007-11-14
okay,

so you do not have an internet connection at all? then you are in trouble because all the methods to get the appropriate drives need an internet connection. synaptic is a manager which will automate the download (it's not windows style, where you have to go to a site and download an item).

your solution:

* plug your ubuntu system in a wired network and use synaptic for the atmel driver
* download the driver manualy in your windows OS and copy it to Ubuntu and make a manual install (ps this can be tricky if you are not comfortable with linux)

probably when you plug into a wired network (with internet connection) ubuntu will update and will automatically install the newest drivers...

thats the cool think of ubuntu!!

---

### Post by UnBr34KaBl3 on 2007-11-14
Yes, Linus and the Internet is the same:p 

I have a internet connection through a wireless bridge now. But the Synaptic doesn't work :(. I think it's because I'm using a bridge that is configured to work with my xbox 360...
I can browse the web(Pidgin/GAIM works aswell) but i can't download with synaptic.

It just looks like this :(


[http://img114.imageshack.us/img114/5098/screenshotxk9.png](http://img114.imageshack.us/img114/5098/screenshotxk9.png)

Where can i find the driver?

EDIT: I found the driver and downloaded it but when i was going to install the installer refused to install.

---

### Post by UnBr34KaBl3 on 2007-11-15
Is this the right one?

[http://dir.filewatcher.com/d/Debian/all/contrib/net/at76c503a-source_0.12.beta19-4_all.deb.95922.html](http://dir.filewatcher.com/d/Debian/all/contrib/net/at76c503a-source_0.12.beta19-4_all.deb.95922.html)
 
ot this?
[http://packages.debian.org/sarge/at76c503a-source](http://packages.debian.org/sarge/at76c503a-source)

I've tried to install one of them(the 2:nd) but it didn't work...

---

### Post by UnBr34KaBl3 on 2007-11-15
Please help!

---

### Post by UnBr34KaBl3 on 2007-11-15
[http://img155.imageshack.us/img155/9459/screenshot2xm1.png](http://img155.imageshack.us/img155/9459/screenshot2xm1.png)

Strange huh?


Is this the right driver??

[http://packages.ubuntu.com/gutsy/net/at76c503a-source](http://packages.ubuntu.com/gutsy/net/at76c503a-source)

---

