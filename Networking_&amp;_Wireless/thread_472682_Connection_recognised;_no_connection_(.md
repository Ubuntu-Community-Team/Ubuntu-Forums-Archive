---
title: "Connection recognised; no connection :("
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by Glennjamin on 2007-06-13
I have a intel pro wireless 3945 ABG and i had it all working peacey until i installed 176 updates- and now it's recognising the connection but simply gives the status as disconnected and 0 signal strenght; any ideas?

my iwconfig is:


eth0  no wireless extensions

eth1 unassociated ESSID: off/any

MOde: managed Frequency= nan kHz Acess point : Not- Associated 
Bit rate: 0 Tx-Power: 16dBm
Retry limit: 15 RTS thr:off Fragment thr:off
Power Managment: Off
Link Quality:O Signal Level:0 Noise Level: O
Rx invalid nwid:0 Rx invalid crypt:0 Px invalid frag:0
Tx excessive retries:0 Invalid misc:1 Missed Beacon:0

sit 0 no wirless extension

--------------------------------------

i was using eth1 as my connection before hand. Any ideas?

---

### Post by sammydee on 2007-06-13
Hi all

I've been helping Glenn (glannjamin) and I installed ubuntu for him. He is running edgy eft, it was working fine on his wireless out of the box but now one of the updates has broken it. Any ideas?

I don't think his wired network is working either,

Sam

---

### Post by sammydee on 2007-06-14
Hi All

This is still a major problem! Without any means of accessing the internet Ubuntu is worse than useless, and Glenn is new to linux so it would be great to show him how good the community support is!

Cmon guys you haven't let me down before...

Sam

---

### Post by dardack on 2007-06-14
I am just a beginner myself, but feel i should TRY to give back.

First is your AP useing any security?  Is it broadcasting it's ESSID?  For now might want to try by turning off security and turning on broadcasting, just to see if you can connect at all. 

Also try this commands:

sudo killall dhclient
sudo iwconfig wlan0 essid "your essid without quotes" mode managed enc off
sudo dhclient -d wlan0


Print what it displays, that is if your AP has security turned off and broadcasting it's ID.

---

### Post by Glennjamin on 2007-06-15
is it broadcasting a SSID, and has no security properties (no wep (hex or string) attached to it, i'll try those commands thanks

---

