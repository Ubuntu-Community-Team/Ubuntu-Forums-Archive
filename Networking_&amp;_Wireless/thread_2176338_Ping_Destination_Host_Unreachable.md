---
title: "Ping: Destination Host Unreachable"
date: 2013-09-23
forum: Networking &amp; Wireless
---

### Post by TheOnlyChosenOne on 2013-09-23
I have a weird kind of situation here.
My laptop and Android device are on the same network.
My Android device has the next configuration:
[IMG]http://s12.postimg.org/hzzu375t5/Wireless_Settings.jpg[/IMG]

My laptop has the next configuration:
inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0

For some reason I cannot ping my Android device. But we are on the same network! How is this possible?

---

### Post by oldos2er on 2013-09-24
Moved to Networking & Wireless.

---

### Post by zero2xiii on 2013-09-24
I assume the router is not pinging through, or it has a separation between LAN and WAN traffic.

Can you ping the computer from the phone?

Cheers

---

### Post by Chip88 on 2013-09-24
Hi TheOnlyChosenOne!

Seems we have exactly the same problem.
Check it out here: [http://ubuntuforums.org/showthread.php?t=2176120](http://ubuntuforums.org/showthread.php?t=2176120) !

I also can't ping from my laptop to my Android device via WiFi, meanwhile two Android devices in the same wireless network, yes, can communicate between each other without any problems.

It seems to me, the issue here is on Ubuntu - especially, if we're already at least two, experiencing this troubles.

---

### Post by zero2xiii on 2013-09-25
Hay,

Ok so then the questions are more android than ubuntu.

Maybe android does not reply to ping requests. So give us more information about your android device:
Device, Android Version, Kernel version, any customizations (Root, roms, Antivirus software, firewalls, is background data restricted etc)

This might be android and not ubuntu,
For the record my device responds (although with an insanely high latency):
```
Galaxy S3 I9300
Android 4.2.2
Kernel 3.0.31
```

Cheers

---

### Post by Chip88 on 2013-09-25
First of all: Seems to be exactly the same problem: [http://ubuntuforums.org/showthread.php?t=2176120](http://ubuntuforums.org/showthread.php?t=2176120) !

My problem is that I don't have any connection between my Android and my notebook **in a protected WiFi network (WPA2 - PSK)**.
In an open network, i. e. **withouth protection** at all, everything just works like a charm.

Apparently, this is caused by a misconfiguration within my router - not the settings I made there!

In the [German Ubuntu Forum]("http://forum.ubuntuusers.de/topic/dateiuebertragung-via-wlan") someone worked with me for two days now to find a solution and finally, some minutes ago, we succeeded to build up a connection.

By generating static ARPs on both devices, I'm able to connect my Android and my notebook.

This is how we did:
1. Open the terminal on your notebook and type in:
```
sudo arp -i eth1 -s **THE.IP.ADDRESS.OF.YOUR.ANDROID THE:MAC:ADDRESS:OF:YOUR:ANDROID**
```

2. Typing in ```
arp -av
``` now finally recognizes the Android device.

3. Open a terminal emulator on your Android device and type in:
```
sudo arp -i wlan0 -s **THE.IP.ADDRESS.OF.YOUR.NOTEBOOK THE:MAC:ADDRESS:OF:YOUR:NOTEBOOK**
```

4. Typing in the terminal emulator ```
arp -av
``` now finally recognizes the notebook.

You're able to connect your Android and your notebook now and access your files with the help of apps like *WiFi File Transfer* or *ES File Manager*.

**&#8594; BUT: **I think, it's impossible that this is the solution of the problem, i. e.,** connecting Kubuntu with Android in a protected WiFi Network**.

First of all, what do you think about that solution?!

Is there maybe a possibility to make a script or something similar, so I don't have to type in every time the codes above?!

Thanks in advance!
Mark

---

### Post by TheOnlyChosenOne on 2013-09-25
Thanks for your replies.

I guess the problem solved itself, because now I can ping my Android device and I didn't change anything in the configuration.

> **zero2xiii said:**
> Hay,

Ok so then the questions are more android than ubuntu.

Maybe android does not reply to ping requests. So give us more information about your android device:
Device, Android Version, Kernel version, any customizations (Root, roms, Antivirus software, firewalls, is background data restricted etc)

This might be android and not ubuntu,
For the record my device responds (although with an insanely high latency):
```
Galaxy S3 I9300
Android 4.2.2
Kernel 3.0.31
```

Cheers
Maybe usefull for future reference:
Android Device: HTC One X
Android Version: 4.2.2
Kernel Version: 3.1.17-cyanogenmod+build03 (Thu Jul 11 18:04:26 PDT 2013)
Rom: Cyanogenmod 10.1.2-endeavoru

The ip on this device is set up statically. The phone has restarted since this problem occured. So I'm pretty sure this was an Android problem.

---

### Post by zero2xiii on 2013-09-27
> **Chip88 said:**
> 

Is there maybe a possibility to make a script or something similar, so I don't have to type in every time the codes above?!


Hay,
Yes. Scripting that should not take 10 minutes. I think normal bash scripts can be run by android, not sure.

On ubuntu you could use grep and awk to get everything you need. However I am unsure if they come with android, you can install them, but then it kind of defeats the purpose of scripting things for automation since you can just install an application.

@OP, Glad it "worked it self out". Would still be nice to know what caused the issue, but glad it is working now.

Cheers

---

