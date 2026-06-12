---
title: "No internet connection"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by el mariachi on 2007-02-25
Hey all! Just finished making the switch to Xubuntu on my old desktop pc
[LIST]
[*]PIII 933Mhz
[*]256MB ram
[*]3COM 3C905B 100Base TX
[/LIST]

it used to have WinXP and Ubuntu 5.10 in dual boot, both of them had internet and everything was fine.

recently i acquired (because my new ISP forced me to...) a new cable modem, the Motorola SurfBoard SB5101.   In my new desktop pc Xu runs flawlessly and internet is not a problem.

I already tried the dhclient command and nothing happend (except for the "sleepy" error lol)
Xu recognizes the ethernet board and it's assigned to DHCP, dynamic IP but i can't get an IP.

It's a direct connection to the internet, no routers.

---

### Post by gejr on 2007-02-25
Tried stuff like sudo ifup/ifdown <interface> ?

or am I underestimating/misinterpreting now?:)

---

### Post by el mariachi on 2007-02-25
no i didn't use that. I'm relatevily new to to the Linux world so could you teach me what that command is for? Thanks

---

### Post by gejr on 2007-02-25
It's the same as ipconfig /renew in windows. It basically asks the dhcp to give you a new ip.

sudo ifdown wlan0 (or eth1 or whatever your wireless is called)

then

sudo ifup wlan0 

First one releases your current ip, second one tries to acquire another one.

---

### Post by el mariachi on 2007-02-25
it's a no go... tried sudo ifdown eth0 (my ethernet card) and "Send_packet: Network is unreachable"

this is weird because in my new pc Xu has internet but the old one doesn't and the cable modem is the same (the ethernet board is different but with my old cable modem it worked on both pcs)

---

### Post by koenn on 2007-02-25
Those cable modems sometimes act up when you attach a different pc to them. 
Work around :
turn cable modem and pc off (unplug power)
wait 15 minutes
turn modem on, what till it''s fully operational (watch blinking lights)
turn pc on.

with a bit of luck, it will work

---

