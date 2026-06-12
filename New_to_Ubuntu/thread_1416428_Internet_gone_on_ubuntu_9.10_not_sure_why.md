---
title: "Internet gone on ubuntu 9.10 not sure why"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by alikebabay on 2010-02-26
What might cause the loss of internet on my ubuntu?
I have forwarded ports for warcraft and garena on my linksys dir-615 (ports 6112, 6113, 1513, 1514) I have also enabled qos-engine. If anyone has this router (comes with virgin cable internet) you know that for qos you only setup uplink speed and type of connection ( i set 2mb (i have 1.5 mbit upload, so it seems like overkill, but friend didn't complain) to prioritize game and http traffic over torrent and get rid of torrent lags). Well so far it worked and games were fine, despite my flatmate ruthlessly downloading stuff from torrents. 
The problem arose when I launched ubuntu 9.10 ( I dual boot with windows on my sony vaio fz21m). Both firefox and google-chrome had almost none of internet (the web-page header will load (you know on the top bar of firefox) but the rest is blank and then it was all gone completely. 
I log on to another modem - internet is there (so it isn't smth on the pc causing it). My friend uses virgin internet fine from his pc. Cell phone wifi also works fine. 
So can anyone tell me what seems to be the problem? Is it ports forwarded? or qos engine?
p.s. I limited range of avalable ips to 5 (192.168.0.1-5) to limit the people who could connect to wifi at home. not sure if that helps.

---

### Post by Kakers on 2010-02-26
Are the 5 ips set as reserved ips? you may find that your windows boot may be getting 1 of the 5 ips leased for 7 days but if it isn't reserved by MAC address then your linux boot may not be able to get a free ip. However I doubt this is the case if you can get the header.

Can you copy and paste what is in the /etc/networks/interfaces

---

### Post by alikebabay on 2010-02-26
Sorry forgot to tell, last time router gave me the same ip on linux as on windows.
auto lo
iface lo inet loopback
 
apparently that's all i have.
Btw, im writing this from main virgin box. I disabled port forwarding and enabled qos
my flatmate is on the torrent, but webpages open fine.
It's still bugging me why would that happen.

---

### Post by Kakers on 2010-02-26
This is what mine looks like:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

```

Try it and see how you get on... as it seems you don't have anything listed for your eth0 connection

---

### Post by alikebabay on 2010-02-26
yeah, but i use wlan mostly. ethernet works fine..

---

### Post by alikebabay on 2010-02-26
think i mark it as solved. i have inet now:)

---

### Post by Kakers on 2010-02-26
Great :D

---

