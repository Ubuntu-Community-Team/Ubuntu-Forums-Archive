---
title: "Network nterfaces are interchanged automatically!!!!"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by tuxy on 2006-09-13
I am using wireless on my Compaq V4000 laptop which has a network card "eth1" and wireless card on "eth0". I have setup "eth0" as the default gateway interface through Gnome's Networking utility.

The wireless connection is perfect until I use it often. But, if I leave the laptop idle the network interfaces are getting interchanged automatically,means network card is assigned as eth0 and wirless card to eth1 and the wireless setup is stuffed up and I have to reconfigure the whole wireless setup whenever this happens!!! 

I even tried disabling the network card through the "Deactivate" option in Networking utility so that there will be only wireless card enabled in my laptop. But when I restart the laptop the network card automatically becomes activated and it changes to "eth0" even when I changed to "eth1".

I feel there is some script some where in the system which is waking up the network card at a certain period of time(even on bootup) and making the network interfaces interchanged.

Is there any way I can disable this thing to happen ?

---

### Post by awaldram on 2006-09-13
check out /etc/iftab

---

### Post by tuxy on 2006-09-16
I couldnt find any /etc/iftab file in Ubunutu DD. But I can see Man pages for iftab. 

Do I have to create the file if it doesn't exist? If so what is the proper syntax for the network interfaces to type in iftab file.
In fact, i did try by using the man pages but it didn't work!

Sorry for a delayed reply.

---

### Post by awaldram on 2006-09-20
Its part of udev I believe 

try 
locate iftab

should see some udev rules and an iftab_helper


/etc/iftab works like this

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:15:65:B2:15:1D arp 1
eth1 mac 00:16:65:49:D5:D7 arp 1


you can find your mac address's from ifconfig

---

### Post by tuxy on 2006-09-20
Thanx for the reply. Infact, I fixed the problem few days ago. I have created the /etc/iftab file and added the mac addreses of my network interfaces.
I have also changed the wirleless card to  "wlan0" from "eth1"
and left the network card "eth0" as it is and it worked brilliantly :)

This is my /etc/iftab file:

wlan0   mac 00:15:A5:8A:58:70
eth0    mac 00:0A:E4:D8:B8:94

I hope this post helps some one who has the same problem.
Happy Linuxing :)

---

