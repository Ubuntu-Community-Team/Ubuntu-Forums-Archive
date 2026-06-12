---
title: "Tethering With Sprint Android Cellphones"
date: 2015-01-17
forum: Networking &amp; Wireless
---

### Post by abbatemark on 2015-01-17
I would like to buy a 2 year contract with sprint because they have unlimited data tethering. Since I would like to sign up for a 2 year contract I want to make sure that tethering with Sprint works with Ubuntu Gnome 13.10. That's all the information that I know to give. I don't know what cellphone I will buy yet. If you need more info please let me know.

---

### Post by Bucky Ball on 2015-01-17
Welcome. Can't help with your problem, but please note, 13.10 is no longer supported. Please upgrade to a supported release. See [here]("http://ubuntuforums.org/showthread.php?t=2229730"). Good luck. ;)

---

### Post by PhilGil on 2015-01-17
For what's it's worth, I'm running Ubuntu Gnome 14.04 with a Sprint branded phone. Both wifi and USB tethering work flawlessly.

---

### Post by abbatemark on 2015-01-17
@philgil: What kind of phone do you have? or does it matter?

ok I'll upgrade thanks.

---

### Post by PhilGil on 2015-01-18
> **abbatemark said:**
> @philgil: What kind of phone do you have? or does it matter?
I'm using a Galaxy Note 2. I would think any modern Android phone would work but you should confirm with Sprint.

---

### Post by efflandt on 2015-01-18
While I could not get MTP did not work in Ubuntu 12.04 (for looking at  files on my phone), USB tethering worked flawlessly with my Samsung S3  (although, using T-Mobile). Basically connect USB cable, enable  tethering in Settings of the phone, and Ubuntu recognized the phone as  an ethernet equivalent device (usb0), so Ubuntu disconnected my WiFi. I  needed to do that a couple of times when my DSL was acting up.

And  I am trying it now in 14.04.1 (where MTP does work to copy files to/from phone on USB). When I enabled tethering Ubuntu  automatically switched to that instead of WiFi on my desktop PC. I am  posting this using mobile data.```
usb0      Link encap:Ethernet   HWaddr 02:03:51:01:38:30  
          inet addr:192.168.42.184  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::3:51ff:fe01:3830/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10079 (10.0 KB)  TX bytes:23672 (23.6 KB)
```Another use for tethering is to provide WiFi client for a computer that does not have it. Connect your phone to WiFi and to computer with USB, enable tethering, the computer then has WiFi.

Note: For Windows computers you might need an existing internet connection on the PC when you first enable tethering, so Win7 or newer can find a driver. Or for WinXP or without any other internet connection, you may first need a USB driver from your phone manufacturer before tethering would work.

Apparently the forum no longer considers you logged in when connecting from a different public IP. I had to log in again when switching to mobile data, and again when switching back to my home network. That might be an issue for AOL users if AOL still uses a bank of multiple transparent web proxies, but then how many Linux users would use AOL for their ISP?

---

