---
title: "Wireless Interface Keeps Changing"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by jeelliso on 2007-02-27
Hello,

I've setup my wireless card with ndiswrapper build from source and using the binary Windows driver specified on the ndiswrapper website.  I do not have any problems with actually getting my internet connection to work.

Here's my problem:  I like to use wifi-radar to semi-automatically connect to various wireless networks since I'm constantly going back and forth between work, school, and home.  If you're familiar with wifi-radar, you'll know the /etc/wifi-radar.conf file specified which interface to look at for incoming wireless connections.  The problem is my wireless interface, which is automatically brought up during the boot sequence, keeps changing from wlan0 to eth1 and vice versa.  This means that every time it changes I have to modify my wifi-radar.conf file.  Does anyone know how I can force it to use either of them (I don't care which as long as its consistent)?

Thanks,
Justin

---

### Post by spd106 on 2007-02-27
Add it to the /etc/iftab file. A line such as this will do```
eth0 mac 00:ab:12:cd:34:ef arp 1

```
Just use your own mac address, it can be found through ifconfig.

---

### Post by pixeldotz on 2007-02-28
**spd106** is correct in saying to edit the /etc/iftab file.

however i did the following to mine.

i changed the eth1 to read wlan0.

simply because i only have two eth interfaces on my laptop. eth0 is the wired and eth1 used to be the wireless. after setting up ndiswrapper for broadcom i was encountering problems with iwconfig telling me that the wireless interface was eth1.

do a **iwconfig** to find out what interface your wireless card is actually one (since you've alreayd done ndiswrapper from source i'm pretty sure you know this already) and change whatever interface is registered to your wireless in /etc/iftab.

also, how did you get wifi-radar to function correctly? i can only change my settings from the default network manager. wifi-radar see's the ssid i want to connect to but won't connect at all. do i have to edit etc/wifi-radar.conf ?

---

### Post by jeelliso on 2007-02-28
Okay, I've changed my /etc/iftab file to match the wlan0 setting specified by ndiswrapper.  Lets hope it works out...I'll keep the thread updated.

> **pixeldotz said:**
> also, how did you get wifi-radar to function correctly? i can only change my settings from the default network manager. wifi-radar see's the ssid i want to connect to but won't connect at all. do i have to edit etc/wifi-radar.conf ?

I'm not exactly sure what you mean.  When you click the "Connect" button on wifi-radar does it immediately say "Could not get IP address"?  If it does this without pausing at "Acquiring IP Address" the the /etc/wifi-radar.conf is probably looking at the wrong interface.  I can't imagine why it wouldn't work.  I just installed it was apt-get and it worked.  Sorry I couldn't be of more help.

---

### Post by jeelliso on 2007-03-06
Its been quite a while and the interface hasn't changed so it looks like this works.

Thanks

---

