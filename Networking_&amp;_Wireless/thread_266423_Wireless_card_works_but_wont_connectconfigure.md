---
title: "Wireless card works but wont connect/configure?"
date: 2006-09-27
forum: Networking &amp; Wireless
---

### Post by jcrnan on 2006-09-27
So, Im trying to set up the wireless on my little sisters pc. It uses a Jensen AirLink network card and a Jensen Airlink Router. My hp pc with built in network card connects just fine. This one however doesnt. It shows good signal rates and it does find the network with iwconfig but not in the gui.

ifconfig doesnt find my eth1, just lo and something called wlan0. It says it gets some sporadic signal and such but I dont know what it is.

iwconfig doesnt say much intersting as far as I can see (hard to copy paste since its on another pc but just say so if you want spesific info from it) It doesnt seem to find the ESSID now but it did while I was setting up the WPA :-k 

etc/network/interfaces doesnt contain anything interesting except for what I added from the wpa guide [here]("http://www.ubuntuforums.org/showthread.php?t=263136").

Otherwise the reuter is working fine with the other wireless pcs in the house (my ubuntu, and two other wirless windows, one with same wireless card as the problematic one here) and the wireless works fine in windows.

btw: I can also mention that the wirless actually worked automaticly when I first used the livecd when installing (altough I had to select eth1 manually as it wasnt in the dropdown list) but if I try the live cd now its no such luck. 


any ideas?

---

### Post by mysmallsecret on 2006-09-27
from my experience you need a number of things inorder to get your wireless card to connect to the internet

in addition to the loop back (lo) entry
you should have an entry for your other network devices in the /etc/network/interfaces file for you probably something like this

auto wlan0
iface wlan0 inet dhcp
wireless-essid any
wireless-key <your key>

also you need to have the correct name server in /etc/resolv.conf
if you know it add this as the first line in that file
nameserver <your nameserver address>

or run 
sudo dhclient wlan0
and that will set it for you

hope this helps.

---

### Post by jcrnan on 2006-09-27
Okey, so I added to the interfaces and it seemed to get some responce at least. Now I was able to get it activated and enabled. But it doesnt let me connect to the net any more. (It doesnt find the server via the browser either).

How do I know my nameserver?

I tried doing the dhclient but I got a input/output error on the SIOCSIFFLAGS and he only tried to send to 255.255.255.255 and just said network was down.

---

### Post by jcrnan on 2006-09-28
anyone?

---

### Post by Ferrat on 2006-09-28
Maybe not the fault but just dubble check that in the networksettings you got wlan0 as Default Gateway device 

just go to system >> Administration >> networking 

ans just below all your network connections you ha a little pulldown box where you select your default device for networking.

---

### Post by jcrnan on 2006-09-28
its eth1 not wlan0 but wlan0 just seems to be something strange. Im pretty sure that eth1 is the card. 

So.. still not working... noone that knows this?

---

### Post by mysmallsecret on 2006-09-29
i missed that your device is eth1 in the message
you should change the wlan0 to eth1
in the /etc/network/interfaces file

---

### Post by jcrnan on 2006-09-29
I already have the eth1 set up in the interfaces file.

---

### Post by joplass on 2006-09-29
if all things don't work with eth1 maybe you want to try ndiswrapper and have wlan0.  i am using it on both ubuntu and elive.

---

### Post by jcrnan on 2006-09-30
Yeah, I'll prolly just set up ndiswrapper again. but what is wlan0? eth1 is the wireless card, that im pretty sure of. wlan0 seems to be nothing or some weird thing :S

---

