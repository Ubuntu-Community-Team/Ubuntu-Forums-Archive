---
title: "Setting Up a SoftAP"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by Unanimated on 2008-09-03
EDIT: Okay, it's been three days and there have been no replies. I'm just assuming that this won't work, even though I'm sure it's very possible.

EDIT: I've done this in Windows before and I'm sure there's a way to do it in Ubuntu, as well. So far, there are **no replies.**

Okay, I'm trying to set up my Nintendo Wi-Fi USB Connector to become a SoftAP. I've done it in Windows using VirtualBox, and I'm sure I can do it in Ubuntu as well. Here are the resources I'm using:

[http://forums.afterdawn.com/thread_view.cfm/390312]("http://forums.afterdawn.com/thread_view.cfm/390312") - Using the driver provided in the package, installed under ndiswrapper
[http://ubuntuforums.org/showthread.php?t=132980]("http://ubuntuforums.org/showthread.php?t=132980") - Used to install and configure ndiswrapper and the driver above
[http://ubuntuforums.org/showpost.php?p=1109936&postcount=4]("http://ubuntuforums.org/showpost.php?p=1109936&postcount=4") - Following the instructions here

I used the first forum post to use it like this in Windows. I got the driver successfully installed in ndiswrapper. I'm sure the last post is using an older version of Ubuntu, because there is no /etc/iftab or /etc/network/options in my filesystem. I had to make /etc/network/options myself, and I don't think Ubuntu is even doing anything with it. I'm running Hardy. Here's the output of my iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
Although my computer does not have a wireless card installed internally, Ubuntu is recognizing the USB connector, just not applying it the way I want it to. There are no wireless networks around me, so I can't test to see if it can connect to a network. The drivers in the first forum post listed above are modified Buffalo drivers, supposed to make the USB connector act as a wifi chip and be able to connect to wireless routers. I tried to install the ASUS utility in Wine, and it installed successfully, but when I open it, an error occurs. Any help?

EDIT: Those above drivers also support SoftAP mode.

---

### Post by Unanimated on 2008-09-04
bump...

---

### Post by Unanimated on 2008-09-04
bump

---

### Post by Unanimated on 2008-09-04
bump

---

### Post by Unanimated on 2008-09-04
...

---

### Post by Unanimated on 2008-09-05
Is no one going to be able to help me at all?

---

### Post by Unanimated on 2008-09-05
Okay, this cannot be that difficult.

---

### Post by Unanimated on 2008-09-06
Two days and no replies? Can somebody please help?

---

### Post by Unanimated on 2008-09-07
bump

---

### Post by Unanimated on 2008-09-07
Okay, three days and no replies. I'm just going to assume that it's not possible.

---

