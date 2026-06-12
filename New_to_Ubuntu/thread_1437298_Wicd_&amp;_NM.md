---
title: "Wicd &amp; NM"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by dunbrokin on 2010-03-23
I had wicd running on my Kubuntu PC until this morning when (after some recent updates) it was no longer able to connect to the wireless router. In desperation, I installed network-manager-gnome as I thought that this was the appropriate alternative. However, I have ended up now with access to the net either by wire or by wireless. What do I have to do to get reconnected?

Have tried the Ubuntu 9.10 iso CD as a software source to install network-manager-gnome...but it will not accept it.

---

### Post by Gadgetech on 2010-03-23
Did you remove wicd when you installed network manager? The two might be fighting with each other. You can **sudo apt-get remove wicd** without losing the package. It will still remain on disk if you want to reinstall it.

---

### Post by dunbrokin on 2010-03-23
Nope, that does not seem to be the problem...I have had some luck with this

auto eth0
iface eth0 inet static
address 192.168.0.35
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

    * Then restart networking: 

sudo /etc/init.d/networking restart

    So, I can now access the web....but it is very slow and does not scroll properly in Konqueror. What is the network manager for Kubuntu?

---

