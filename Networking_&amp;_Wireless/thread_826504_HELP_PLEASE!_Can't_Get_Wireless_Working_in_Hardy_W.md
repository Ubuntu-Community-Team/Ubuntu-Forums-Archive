---
title: "HELP PLEASE! Can't Get Wireless Working in Hardy W/Broadcom 4318"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by ibohren on 2008-06-11
I just upgraded my laptop to Hardy from Gutsy and I have been pouring through the forums and how-to's for hours and can't get my wireless card to work. It was working fine in Gutsy. I know I have the dreaded Broadcom 4318 card and have found several walkthroughs, but none of them have worked. Here are links to a few how-to's I have tried that have not worked.

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

[http://ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+belkin](http://ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+belkin)

[http://backports.ubuntuforums.com/showthread.php?t=813363](http://backports.ubuntuforums.com/showthread.php?t=813363)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc)

The last one seemed promising but I started out with my network light at least on but unable to detect any wireless networks, but it is now out. I'm at my wits end.

Thanks for any help.

---

### Post by Ayuthia on 2008-06-12
Which method did you use to get it working in Gutsy (NDISwrapper or bcm43xx)?

---

### Post by Dark_Stang on 2008-06-12
Hardy is a little different... This method assumes you are using ndiswrapper with the bcmwl5 driver.

enter ```
sudo gedit /etc/init.d/wifiFix.sh
```
Now copy and paste this into the file, then save it.
```
#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44 
```
Now enter this into a terminal
```
cd /etc/init.d
sudo chmod 755 wifiFix.sh
sudo update-rc.d wifiFix.sh defaults
```

---

### Post by Ayuthia on 2008-06-12
> **Dark_Stang said:**
> Hardy is a little different... This method assumes you are using ndiswrapper with the bcmwl5 driver.

enter ```
sudo gedit /etc/init.d/wifiFix.sh
```
Now copy and paste this into the file, then save it.
```
#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44 
```
Now enter this into a terminal
```
cd /etc/init.d
sudo chmod 755 wifiFix.sh
sudo update-rc.d wifiFix.sh defaults
```

You don't need the b44 portion if your wired ethernet card is not a Broadcom card that uses the b44 driver.  You can see if it is by checking lshw -C network.

---

### Post by ibohren on 2008-06-12
To answer the first question, to be honest, I don't recall what method I used initially. I have been using Ubuntu since Dapper and remember my wireless card being an issue after each upgrade. After each upgrade, I have been able to get wireless up and working after some looking through the forums and applying what worked for others. This however, is not the case this time around. I have tried everything I can find and nothing has worked. I did a fresh install of Hardy from CD this morning and tried again, but I am still having no luck. Hardy recognizes my card and I am able to enable it in the Restricted Drivers, which prompts it to install b43-fwcutter and asks if I want extract the firmware. I check yes and then my wireless light comes on on the front of my laptop. However, even after reboot, when I click on network manager, there are no wireless networks displayed to connect to (and I'm 3ft away from my router). I tried the "connect to other wireless networks" option and manually entered the name of my network and the WEP key. When I hit the connect button it acts as though it's trying to connect, but never does, and just keeps prompting me for the WEP key over and over again.

Secondly, several of the methods I have tried involved NDISwrapper. None of them worked and all caused my wireless light on the front of my laptop to go out. I have since read several posts in the forums that have folks saying that NDISwrapper won't work with Hardy. If it does, I have not found a how-to that I can follow from start to finish that does.

I was able to get the card working in all the previous distributions, so I have to believe that it will work with Hardy. I just can't find a how-to on here, or anywhere, using either B43-fwcutter or NDISwrapper that will get it working like it was in Gutsy yesterday on my computer.

Thanks you very much, each of you, for your help thus far.

---

### Post by Ayuthia on 2008-06-12
> **ibohren said:**
> To answer the first question, to be honest, I don't recall what method I used initially. I have been using Ubuntu since Dapper and remember my wireless card being an issue after each upgrade. After each upgrade, I have been able to get wireless up and working after some looking through the forums and applying what worked for others. This however, is not the case this time around. I have tried everything I can find and nothing has worked. I did a fresh install of Hardy from CD this morning and tried again, but I am still having no luck. Hardy recognizes my card and I am able to enable it in the Restricted Drivers, which prompts it to install b43-fwcutter and asks if I want extract the firmware. I check yes and then my wireless light comes on on the front of my laptop. However, even after reboot, when I click on network manager, there are no wireless networks displayed to connect to (and I'm 3ft away from my router). I tried the "connect to other wireless networks" option and manually entered the name of my network and the WEP key. When I hit the connect button it acts as though it's trying to connect, but never does, and just keeps prompting me for the WEP key over and over again.

Secondly, several of the methods I have tried involved NDISwrapper. None of them worked and all caused my wireless light on the front of my laptop to go out. I have since read several posts in the forums that have folks saying that NDISwrapper won't work with Hardy. If it does, I have not found a how-to that I can follow from start to finish that does.

I was able to get the card working in all the previous distributions, so I have to believe that it will work with Hardy. I just can't find a how-to on here, or anywhere, using either B43-fwcutter or NDISwrapper that will get it working like it was in Gutsy yesterday on my computer.

Thanks you very much, each of you, for your help thus far.

Let's start with checking b43 since you already have the firmware.  Try the following:
```
sudo modprobe -r ndiswrapper b43 ssb bcm43xx
sudo depmod -ae
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```If it is able to see wireless connections:
```
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid <name> key <passkey>
sudo dhclient wlan0
```

However, if it does not see any wireless, then let's try the NDISwrapper route.  Please check ndiswrapper -v and see that it is using a version greater than 1.50 and then make sure that the device is present in ndiswrapper -l.  Then do the following:
```
sudo modprobe -r ndiswrapper b43 ssb bcm43xx
sudo depmod -ae
sudo modprobe ndiswrapper
sudo iwlist scan
```
if no networks are found, check:
```
lshw -C network
```
See if your wireless card is using ndiswrapper or b43.  If it is using the b43 driver, check:
```
dmesg
```There should be some kind of error message at the end of the listing.

Can you also post your lspci -nnm?  I would like to see your wireless card information (vendor and subvendor information).  It will help in determining why your card is not working.

---

### Post by ibohren on 2008-06-12
Ayuthia, the first two sets of code worked perfectly from start to finish and my wireless card is working exactly as before. I can't thank you enough! 

I'm not sure what the difference is between all the other Broadcom how-to'
s posted, but whatever it is, it worked perfectly for me when nothing else seemed to do anything.

Thanks Again!

---

### Post by ibohren on 2008-06-12
OK, so after a successful reboot, my wireless is still working but, I have broadband internet and my wireless connection is running slow like dial up. It wasn't like that with Gutsy. Is there some sort of configuration I need to make now that it's working?

Thanks Again.

---

### Post by Ayuthia on 2008-06-12
> **ibohren said:**
> OK, so after a successful reboot, my wireless is still working but, I have broadband internet and my wireless connection is running slow like dial up. It wasn't like that with Gutsy. Is there some sort of configuration I need to make now that it's working?

Thanks Again.You might try the following:
```
sudo dhclient -r wlan0
sudo iwconfig wlan0 rate 54M essid <name> key <passkey>
sudo dhclient wlan0
```
If it goes slow again, please post your ifconfig results.

---

### Post by ibohren on 2008-06-12
I tried the code you provided but when I get to the second step, it returns an error. Sorry if it's user error, I'm definitely a novice user. Here's what I got:

ibohren@ibohren-laptop:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 6890
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:a4:79:cf:76
Sending on   LPF/wlan0/00:14:a4:79:cf:76
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
ibohren@ibohren-laptop:~$ sudo iwconfig wlan0 rate 54M essid <name> key <passkey>
bash: syntax error near unexpected token `newline'
ibohren@ibohren-laptop:~$ 


Here are the results of ifconfig:


ibohren@ibohren-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:08:7e:37  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:207700 (202.8 KB)  TX bytes:207700 (202.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a4:79:cf:76  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a4ff:fe79:cf76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27945 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49115044 (46.8 MB)  TX bytes:2703769 (2.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A4-79-CF-76-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ibohren@ibohren-laptop:~$ 

Thanks Again!

---

### Post by Ayuthia on 2008-06-12
> **ibohren said:**
> 
ibohren@ibohren-laptop:~$ sudo iwconfig wlan0 rate 54M essid <name> key <passkey>
bash: syntax error near unexpected token `newline'
ibohren@ibohren-laptop:~$ 
Sorry, <name> should be replaced with the essid of your router and <passkey> should be replaced with your WEP key.

---

### Post by ibohren on 2008-06-12
Seems actually a little slower after applying the code, though I can't really tell surfing from sight to sight. It didn't seem to want to reconnect to the router after I applied the code, so I rebooted and it came up fine. Before applying the code I ran a test on Speedtest.net and the max download was about 1.4Mbps, but the test hung on the upload and I had to go unplug my router to get it working again. After the reboot I ran another test at both Speedtest.net and Speakeasy and now the max download I'm hitting is about 768Kbps. So, I put it back the way it was and retested, and I'm still at 768Kbps. So, I guess there was just maybe less network traffic when I the first time. I guess I better not press my luck anymore and just be happy that wireless is at least working. Though, it seemed faster with Gutsy.

Thanks Again!

---

