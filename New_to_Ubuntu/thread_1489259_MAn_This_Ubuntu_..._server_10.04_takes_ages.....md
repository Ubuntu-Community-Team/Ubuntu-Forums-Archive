---
title: "MAn This Ubuntu ... server 10.04 takes ages...."
date: 2010-05-20
forum: New to Ubuntu
---

### Post by kiwixboxer on 2010-05-20
Too load the gnome updates.... been waiting for over an hour...

All I did was enter this in the shell

sudo apt-get install ubuntu-desktop

looks like it is sucking about 2Gig of the net in updates....

bummer... all I wanted was a light GUI ... did not want all the apps under the sun.:guitar:

well.... finally finished its set up.... now reload.... all up and straight into the gnome GUI!!!

Cool. now the fun part ... working out how to set up this beast as a print and file server!

---

### Post by Ozymandias_117 on 2010-05-20
Gnome is certainly NOT a "light GUI" if you want light, you should try CrunchBang, LXDE, IceWM... Never KDE or Gnome :P

---

### Post by kiwixboxer on 2010-05-21
cheers for that ... all is up and running now .... trying 'desperately' to navigate through the command line.....

This is kind of like walking on mars.... all strange and gooey...

just doing simple things like dns and IP address changing ... is paaaiiiinnn full...
Am used to doing it VIA the GUI in windows app and using ipconfig to get all the network info I need...

Am trying to set up a simple print/file server..... is it easy to set up with printers on USB ports?

can you some something like assign virtual IP addresses to separate USB ports? not too sure on what to do .... as both printers are not cat 5 connectable to the network.... was hoping to be tricky!

---

### Post by Nythain on 2010-05-21
not sure if its quite what your looking for, but if you're networked with windows machines, samba can share printers hooked up to the linux box... never done it myself because i've never owned a printer, but there's more than a few guides on it

---

### Post by lisati on 2010-05-21
There's a tutorial for setting up samba here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
If you haven't yet set up a GUI on your server, you can safely use something like "nano" where the tutorial refers to "gedit".

---

### Post by kiwixboxer on 2010-05-21
hey people ... thanks for that .... have goth te GUI up and running .... 

However am having heaps of trouble getting the network to route out my gateway...

I am running it in VMWARE and there is a virtual eth0 that windows has been set up with...
I have changed the static address of  that interface to the same base network the rest of my network is running....
192.168.1.0 network.

when I change the /etc/networks/interfaces file from DHCP to Static..... and then try to restart the interfaces... it dies... then times out.

When it is on dhcp and I do an ifconfig.... it is a totally different network 10.0.2.15 ???

Is there a DHCP server on the actual ubuntu that is controlling this?

It seems to work on dhcp with the 10.0.2.15 address as i can get a web page up and running in the vmware loaded ubuntu server.

sorry to pain you all ... but this is getting frustrating.

---

