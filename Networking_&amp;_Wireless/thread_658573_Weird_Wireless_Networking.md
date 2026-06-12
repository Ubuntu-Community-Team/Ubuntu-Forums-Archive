---
title: "Weird Wireless Networking"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by kiisu on 2008-01-04
I've been bouncing back and forth between the regular network manager that came with Ubuntu install and wifi-radar.

Yesterday I tried to get on my own wireless network at home using wifi-radar and it wouldnt work, although I was able to get on an unencrypted neighbour's network no problem.

I then disabled the security on our network using my roommate's computer. Still couldnt get on it. Then a few hours later I tried using the regular network manager and had success!

Today I tried changing onto an encrypted network just to see what happened ... it asked for a password, I was satisfied, and tried to get back onto my own network .... but it wouldnt go, it just got stuck on the connecting icon, and now it just shows an unplugged icon ... the drop down menu shows me all the available networks, including my own, but if I click on one nothing happens.

Meanwhile, wifi-radar still doesnt get me on to my own network, so I'm stuck stealing this weak signal from my neighbour!!

Needless to say ... frustrating .... anyone have any guesses what I can do to get network manager to reconnect?

---

### Post by Digger78 on 2008-01-04
Does your /etc/network/interfaces file have

```
wireless-key **s:** "your key"
```

if so try removing **s:**

then restart networking

```
sudo /etc/init.d/networking restart


```
HTH

---

### Post by kiisu on 2008-01-04
all the file has in it is this:

auto lo
iface lo inet loopback

---

### Post by Digger78 on 2008-01-05
I assume you know your interface name - eth0, wlan0 or similar

If you only intend to connect to your home network the easiest way is to add the following to your /etc/network/interfaces

substitute the [COLOR="Red"]red text[/COLOR] to suite your own setup

if you use DHCP 

```
iface [COLOR="Red"]eth0[/COLOR] inet dhcp
wireless-essid [COLOR="Red"]youressid[/COLOR]
wireless-key [COLOR="Red"]yourkey[/COLOR]

auto[COLOR="Red"] eth0[/COLOR]

```

Or if you use a static IP

```
iface [COLOR="Red"]eth0[/COLOR] inet static
address [COLOR="Red"]xxx.xxx.xxx.xxx[/COLOR]
netmask 255.255.255.0
gateway [COLOR="Red"]xxx.xxx.xxx.xxx[/COLOR]
wireless-essid [COLOR="Red"]youressid[/COLOR]
wireless-key [COLOR="Red"]yourkey[/COLOR]

auto [COLOR="Red"]eth0[/COLOR]

```


restart networking

```
sudo /etc/init.d/networking restart
```

Hopefully you should now be connected to your own network.

HTH

---

### Post by kiisu on 2008-01-05
Thanks for your help Digger78
before seeing your reply I tried the instructions in this thread:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
and it worked flawlessly, according to wifi-radar I am now connected to my home network and its showing in my internet loading speed. 

By the way, I am trusting wifi-radar over the built-in network manager cause that f'in program seems to have a mind of its own .... when it works it works beautifully but that doesnt seem to be all that often.

If I have problems in the future I will try the above suggestion and report back. Thanks again!

---

### Post by familjen on 2008-02-17
Hi 
I am experiencing the same problem as kiisu, and tried to fix it with by editing in /etc/network/interfaces but without result... atleast no good result. The only thing happening was that all wireless networks disappeared from the "Wifi-radar quick view" 
(by clicking the network icon in upper right)

facts: I can log on to a unencrypted network in my area (not my network) and use it. 
I can not log on to my network if I run wep-kryptation (and use korrect key).
Wifi-radar says that I can log on to my network when I removed the kryptation but I can not use internet or see other computers in that network, so I doubt that. Wifi-radar also gives me an ip-number but by using 
ping <that-number>
from other computers I get no answear. 

I do not know if it is related but the wireless network card seems to be refeered to as both wlan0 and wmaster0 (by iwconfig it is named wlan0 but by lshw the logical name is wmaster0)

I understand that the facts point to that my acces point is broken, but before I ran xubuntu on an old laptop where the wireless connection was flawless. 

Any guesses to what to do?

---

