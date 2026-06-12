---
title: "feisty network install ---- Where do I start?"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by andytof47 on 2007-05-21
Hi I am looking at setting up feisty over a network deploy

I'm not really sure where to start

As it stands I have a compaq evo which has a pxe boot agent or something

and another system that is running Fesity

Seems dumb but It would be great if someone could help

;)cheers

---

### Post by daller on 2007-05-21
What exactly is it you are trying to do?

---

### Post by andytof47 on 2007-05-21
ok I am trying to install onto system that has no cd......

It has a floppy can though and the intel boot agent thing....

I'm still green with servers so this is why i'm asking

I'm trying to have the install files on one computer --- my Ubuntu box and have them served up to the other box and install them


thanks all

---

### Post by tomroffe on 2007-05-21
try this...

[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

 i have a IBM x24 Laptop and i have to PXE/Netboot the thing to install any operating systems.
netbooting the fesity installer can be done but doc is a bit dated.

---

### Post by andytof47 on 2007-05-21
Awesome all is going well pxe booting is happening

Now what do I do? 

I have a feisty disc ---- Do I just make an image of the disc and leave the image in the /tftp folder? is there a way top make a "special" image of the disc or is it just drag and drop?


Cheers

---

### Post by tomroffe on 2007-05-21
you have to use the netboot image for example for feisty

[http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/netboot.tar.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/netboot.tar.gz)

will do, follow the instructions, btw .this will boot a text base installer and download the packages for your system so the CD is not required

---

### Post by andytof47 on 2007-05-22
Ok Half way there

I Am stuck at  the part of the install process that asks for a mirror?????? how do I point this install to the cd files I ripped earlier?


cheers

---

### Post by andytof47 on 2007-05-22
bump please ----

I have rpped the files top the hdd and just need a little help in pointing the install process towards that location


cheers

---

### Post by tomroffe on 2007-05-22
your missing the point you dont need a CD for a netboot install, it pulls eveything  (the packages) down from the internet. if you want to install from a local network location then try [https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet)

---

### Post by andytof47 on 2007-05-22
>  	your missing the point you dont need a CD for a netboot install, it pulls eveything (the packages) down from the internet. if you want to install from a local network location then try [https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet)

No I understand you don't need the CD that's exactly what I want --- The files to reside on a server and boom ----choose which system to load and everyone is happy -- no need to scrounge for CD's

The problem is when I manually enter a "mirror" which is actually the files straight off of the cd on the server's hdd I get a bad mirror error

so here is my network

(server)192.168.2.10---------(client)192.168.2.99     (direct connection)

On the Server ---
```
(feisty install files)
/var/lib/tftpboot/feisty/
(so all the CD files are in here)

(apache is running)
symlinked the feisty directory to 
/var/www


```
Does DHCP work ----- YES
DOES PXE boot WORK ----YES

This is not the problem --- I don't have an internet connection on this particular system----- I have read the localnet docs but to no avail

I really don't know what the syntax is for the "mirror"
e.g. do I tell the install that the mirror is just 
192.168.2.10         (do I need to specify a port also? or a path? or [HTTP://192.168.2.10](HTTP://192.168.2.10))
then do I need to point to a path perhaps?

Which directory or file is it looking for?????


Cheers

---

### Post by andytof47 on 2007-05-22
sorry but Bump again

Really --- I'll write a howto for this as soon as I learn this final part

Pleeeeease

---

