---
title: "Wireless network ubuntu 8.10 problems"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by Azren0 on 2008-11-16
Hey guys 

I've just recently upgraded to ubuntu 8.10 and i seem to have a wireless network issue. The problem is that i can see other wireless networks apart from my own - I'm not sure if its a problem with my router or not. When i manually type in the SSID of the network my laptop connects but then instantly disconnects;

Just wondered if anyone had any thoughts?

Btw; my laptop is a Sony Vaio VGN-FZ38M.

Cheers.

Edit - I forgot to mention my wireless router is a Belkin N1-Vision

---

### Post by jnorthr on 2008-11-16
do you have any kind of security features like WEP or WPA set on your router that requires a key or password ?
 
If you do a command to scan for networks, we will know more. Try
Aplications>Accessories>Terminal to open a command terminal session then type:
[B]iwlist scan
[/B]you may see something similar to mine:

[I]jim@tiny:~$ iwlist scan
lo        Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:00:W1:FD:FW:A4
                    ESSID:"xxx_yyy"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/100  Signal level:-67 dBm  Noise level=-70 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000002c3b1d31e4
                    Extra: Last beacon: 12ms ago

[/I]

also try the command:
[B]iwconfig
[/B]to view your hardware settings.  Your ESSID will be different or missing.

---

### Post by Azren0 on 2008-11-16
I just ran both commands and the first one **iwlist scan** showed up other wireless networks (like i said before) but not mine :( **iwconfig** returns an empty config because im not connected to any wireless network 

My wireless network uses WPA Personal 2 - Could this be the issue?

---

### Post by jnorthr on 2008-11-16
i would certainly look at that issue first. If you have any way to turn off your security as a temporary measure, and confirm your unbuntu network also has security turned off, it will be easier to get it all working together. Otherwise, there are too many variables to solve your problem. So i'd try that first.

---

### Post by Azren0 on 2008-11-17
Yeah i did try that before still no luck :( I can connect to the router fine via Ethernet but this really isn't a solution :)

---

### Post by kj6ythgfg on 2008-11-17
I have the 64 bit ubuntu 2.10 and can't  get my linksys WMP54GS wireless card to work.help:confused:

---

