---
title: "[SOLVED] DNS??IPV6?? No Internet on one xubuntu box"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by jerome1232 on 2008-01-20
Okay i have two Ubuntu boxes, one 7.10 with gnome, the other 7.10 xfce, (installed the base system off of xubuntu alt cd then aptitude install xubuntu-desktop) while installing during the config the network area it got dhcp fine and complained about DNS and asked me to manually enter DNS settings. I checked my gnome machine and it's DNS is set to 192.168.0.1 (my NAT router) and DNS works on this one, so i went with that, it allowed up to three so i browsed to my router and looked up what the router shows as my DNS servers and entered those as secondary.

when i aptitude xubuntu-desktop it used the cd as my source install went fine

log in no internet with mozilla

ping google.com
connect: Network is unreachable

ping 192.168.0.1 (my router)
sent 10 recieved 10 loss 0

ping 192.168.0.2 (the gnome box)
sent 10 recieved 10 loss 0

dig google.com
gives me a whole slew of results so DNS seems to work just fine

then i tried
ping 64.233.167.99  (one of the ip's dig gave me for google)
connect: Network is unreachable

so i have no access out of my LAN even by ip... I checked the logs in my router it has nothing about allowing or blocking access for 192.168.0.3 (the xfce box) it does show it as a connected device, i have no restriction set for internet access

I tried putting the xfce box out of the firewall (DMZ+ mode) and still nothing

if I use xdmcp (xfce connecting to gnome) and login i do get internet just fine

i'm at a loss here

---

### Post by jimrz on 2008-01-20
sounds as though it needs you to set valid DNS servers in your Network settings or, and this would probably work out better, set them in your router's settings if you can.

---

### Post by rosegarden78 on 2008-01-20
If wireless works in Ubuntu you probably need the nm-applet package from the repositories.  You may also need to add Item - System Tray to your launcher by right clicking the edge of your Xfce Menu.

UPDATE: If you have a wireless antenna bars on your desktop prior to Xubuntu, Xfce, Fluxbox or Blackbox - you may consider running nm-applet from a konsole.  If you're a blackbox user you'll need to run nautilus first.  This will activate your default wireless connection.  You may also try running kicker but I cannot get the system tray working yet.

---

### Post by jerome1232 on 2008-01-20
ps i'm using a 10baseT nic (10mbs) on the xfce machine
                      100baseT nic on the gnome machine

is nm-applet a wireless only thing?, i believe i have a sys tray (tells me 97 update are availble and shows my network manager up there is that what ur talking about?)

from /etc/resolv.conf on box that works
nameserver 192.168.0.1

from /etc/resolve.conf on the stubborn box
nameserver 192.168.0.1

both are set to the router
the router is set for DHCP on the wan side
shows a public ip and 2 dns servers 
one machine works so i think that rules out my router this is machine related

when i dig google.com the results are coming from my router on both
machine's

... this is interesting i did
sudo /etc/init.d/networking restart on the stubborn one

gives me

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
**DHCPOFFER from 192.168.0.2 (my gnome box, not my router)**
DHCPREQUEST on eth0 to 255.255.255.255 port 67
**DHCPACK from 192.168.0.2**
bound to 192.168.0.3 -- renewal in 19707 seconds

will try a network restart on gnome box see what's diff

I will try some manually assigned ip's, must be a dhcp server on my gnome box i did try to setup up network booting a month ago and installed web server/dhcp server so that may be interfering here will do some research and update, thanks for the reply

---

### Post by jerome1232 on 2008-01-20
thanks for the suggestions guys i don't know why i didn't try this earlier, it is a dhcp server on my ubuntu machine getting in the way

manually setting 
ip 192.168.0.3
netmask 255.255.255.0
defualt gateway 192.168.0.1

gives me INTERNET!!! so i just gotta get rid of the server on my gnome box thanks for the suggestions every1

---

### Post by rosegarden78 on 2008-01-21
> **jerome1232 said:**
> thanks for the suggestions guys i don't know why i didn't try this earlier, it is a dhcp server on my ubuntu machine getting in the way

manually setting 
ip 192.168.0.3
netmask 255.255.255.0
defualt gateway 192.168.0.1

gives me INTERNET!!! so i just gotta get rid of the server on my gnome box thanks for the suggestions every1

For me the modem and router ended up having the same address: 192.168.1.1.  LinkSys tech support was most helpful to diagnose this for me.  Now I always set my router to 192.168.2.1

---

