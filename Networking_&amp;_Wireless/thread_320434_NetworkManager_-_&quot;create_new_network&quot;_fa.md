---
title: "NetworkManager - &quot;create new network&quot; fails"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by mommebu on 2006-12-17
Using the 'Create new network" menu from network manager I am trying to establish a new wifi network ( for the moment not encrypted) to connect a palm, but networkmanager fails in establishing the network. After a while of the swirling around logo doing its stuff, the connection drops back to not connected state. Anybody has any idea?
On iwconfig I can see that the frequency is NaN, so this could be the problem, but is it the cause of it or rather a consequence?

grateful for any hint,
Momme

---

### Post by pcastell on 2007-12-27
Try this: sudo iwconfig <card> mode Master where <card> is your wifi card interface name (ie: eth0). If it say something like "Error for failed request" or "Set failed on device" your card do not support becomming an Access Point which is required to created a wifi network. You can try to create an Ad-Hoc network, it's a kind of direct link but instead of using a usb/parallell/serial cable you use your wifi card to do it.

---

### Post by Arlanthir on 2008-03-28
I'm getting the same behavior here.
Doing "iwconfig eth1 mode master" got me an "Invalid Argument" error. 
Does that mean my wireless card doesn't support that type of connection?
Shouldn't NetworkManager say something in that case?

I'd really like some help over here =/

Thank you

---

### Post by CLomax on 2008-03-28
Same problem here:

[PHP]<name>@<name>-desktop:~$ sudo iwconfig wlan0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
[/PHP]

And to be honest, I haven't the slightest clue as to what I'm doing, just trying to create a new wireless network to no avail despite the large number of tutorials on the internet. If anyone can help with this or adding security to my current network then please help.

---

