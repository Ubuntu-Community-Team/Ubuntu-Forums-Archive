---
title: "essential programs..."
date: 2011-08-26
forum: New to Ubuntu
---

### Post by Florio on 2011-08-26
I've just recently installed Ubuntu 11.04 on my wife's Acer Aspire One which, as you may know, is a netbook with not a lot of HD space and limited memory. Ubuntu _***just ***_fits on there, but as my wife will never use many of the accessories/applications included in the install, I was thinking of removing several programs, for example those for burning CDs and editing videos seeing as there is no CD drive on the AAO.

My wife just wants acess to internet (Firefox), a program with which to manage her email and appointments (Evolution), a multimedia player (Movie Player) and software for her photos. I'd also like to install GIMP.

What can I safely remove without jeopardising the OS?

Florio

---

### Post by HereInOz on 2011-08-26
You could remove LibreOffice, for a start.

---

### Post by raja.genupula on 2011-08-26
[http://stevehanov.ca/blog/index.php?id=107](http://stevehanov.ca/blog/index.php?id=107)

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

i hope these links can solve your problem

---

### Post by Cu Rua on 2011-10-10
I have a similar issue: I don't want Evolution, but when I tried to remove "evolution data server common" in the synaptic package manager, it said it wanted to also remove "ubuntu-desktop". I'm not sure if it's referring to the desktop program or just Evolution's little tentacles wrapped around the desktop program, so I just left that one alone and removed everything else. Now, the Evolution icon shows up as just an application, an odd springy-lookin-thingy. Is it okay to remove that package? I'd prefer to do so without reinstalling the whole OS or crippling bits of my display please!

---

### Post by bodhi.zazen on 2011-10-10
It is far easier to start with a minimal install or lubuntu and build up then with the Ubuntu desktop and start removing.

---

### Post by mörgæs on 2011-10-10
> **bodhi.zazen said:**
> It is far easier to start with a minimal install or lubuntu and build up then with the Ubuntu desktop and start removing.

+1

Yes, for example using
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

Also run **sudo apt-get clean** once in a while to remove old packages.

---

### Post by oldos2er on 2011-10-10
> **Cu Rua said:**
> I have a similar issue: I don't want Evolution, but when I tried to remove "evolution data server common" in the synaptic package manager, it said it wanted to also remove "ubuntu-desktop". I'm not sure if it's referring to the desktop program or just Evolution's little tentacles wrapped around the desktop program, so I just left that one alone and removed everything else. 

It's been awhile since I used Gnome, but all the Evolution packages are safe to remove except evolution-data-server or evolution-data-server-common, can't remember which.

ubuntu-desktop is a metapackage, removing it won't actually remove anything, though you should leave it installed if you intend to do a system upgrade to a newer version of Ubuntu.

---

### Post by Cu Rua on 2011-10-12
> **oldos2er said:**
> It's been awhile since I used Gnome, but all the Evolution packages are safe to remove except evolution-data-server or evolution-data-server-common, can't remember which.

ubuntu-desktop is a metapackage, removing it won't actually remove anything, though you should leave it installed if you intend to do a system upgrade to a newer version of Ubuntu.

D'oh! I'll just leave it then...

---

### Post by LittleDende on 2011-10-12
> **bodhi.zazen said:**
> It is far easier to start with a minimal install or lubuntu and build up then with the Ubuntu desktop and start removing.
Agreed, I think you should just give her lubuntu! It's all you'd need on a little netbook like that.

---

### Post by retchid on 2011-10-12
I have acer one ssd version 8gb ssd and 8gb sd card version

take all docs vids and music out of your home folders and put on sd card 

That way you dont need to uninstall anything and you will have 1gb on ssd easily and 8gb sd card(i think the first install of ubuntu is about 3gb anyway)

Its unwise to have anything in home on this machine you will lose it all one way or another (but that goes for windows as well)

if you don;t have an sd card then they are cheap as chips

the acer does have 2 slots one on left and one on right

With 3 usb ports and 2sd card ports space is not really a problem provided you dont use home on the ssd drive for file storage and downloads

- if downloading in firefox or transmission just change the default in preference within the program to sd card

---

