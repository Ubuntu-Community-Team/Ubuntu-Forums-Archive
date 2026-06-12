---
title: "Lubuntu Wifi stopped working"
date: 2018-03-23
forum: Networking &amp; Wireless
---

### Post by rob-13 on 2018-03-23
Hello all, i am a noobie here and am having problem with my Wifi.
I have searched the net for hours trying to find a solution and just can't seem to get it back up and running.
I have an old Dell Vostro 1500 that i have set up as a media center with Lubuntu 64bit running on it. 
The Wifi has been working pretty well with occasional drop outs that i couldn't re connect to unless i preformed a reboot (All over a hidden network) and usually after 5 or 10 mins. After a reboot i would have no issue with it.
After the last update and while watching Netflix my cat had somehow pulled the power out of our router and now i can no longer connect over wireless.
I can connect over a hard line, i can see other wireless networks that are not hidden, i can connect to the wireless network with other pc's in the house just can't connect to it with Lubuntu anymore.
I have also run 
```
Iwconfig wlan0
```
and get no such device.

Any help would be greatly appreciated.

---

### Post by jeremy31 on 2018-03-23
Welcome to the forums rob-13
See the wireless script link in my signature and post results

---

### Post by rob-13 on 2018-03-23
Thanks for the reply.
Here is the link to the results.
[http://paste.ubuntu.com/p/6mpRfxP7cZ/](http://paste.ubuntu.com/p/6mpRfxP7cZ/)

---

### Post by jeremy31 on 2018-03-23
In terminal do ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Then check the router settings to see it has B/G/N enabled and not N mode only

---

### Post by rob-13 on 2018-03-23
Ok, so i ran the code and it it asked me for my password then just went straight back to the command prompt.
Is there supposed to be router settings in the /etc/NetworkManager/conf.d?
Only thing i can find in there is a file called default-wifi-powersave-on.conf containing
```
[connection]
wifi.powersave = 2
```
Or do you want me to log into the router its self?

---

### Post by jeremy31 on 2018-03-23
You need to login to the router itself

---

### Post by rob-13 on 2018-03-23
Ok, the closest thing i can find to what you are describing is Wireless Mode and it is set at 802.11b+g
Its an old TP-Link TD-W8901G Router

---

### Post by rob-13 on 2018-03-29
Ok..... So my network was hidden and after making my network visible again i am able to connecting back up to it.

---

### Post by jeremy31 on 2018-03-29
That is strange as I have hidden my wifi before and it would still connect as long as I had the connection set to automatically connect

---

### Post by rob-13 on 2018-04-04
Yeah, was all working fine bar from the drop outs that would fix on a re boot and was set to automatic connection. 
All works no problems with the network visible, no drop out at all.
Will just blame it on the cat, she is a fuzzy little wrecking ball and leave the network visible for now. :)

---

