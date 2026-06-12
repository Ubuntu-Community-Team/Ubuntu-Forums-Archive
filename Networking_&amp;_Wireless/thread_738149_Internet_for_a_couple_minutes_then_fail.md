---
title: "Internet for a couple minutes then fail"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by M787M on 2008-03-28
I posted here previously about trying to get my WUSB54gv4 card working, and after getting it to work in feisty, I decided that maybe I would try upgrading to Gutsy.

Now, I can get internet for about 60 seconds before it completely fails and only sometimes sporadically works after that point.  I have ndiswrapper installed, and the driver (rt2500usb) is working through there.

I'm writing this on another computer, since I wouldn't be able to find the forums, post and submit in 60 seconds time.  Sometimes, unplugging and replugging in the wireless card seems to work for a couple of seconds before it fails again.

First of all, is there anything to be done about it? And if more information is needed, what is helpful to know? I'm really new to Ubuntu, but I'm determined to make it work.

---

### Post by Iowan on 2008-03-28
Although unlikely, I thought I read a thread about APIC causing issues.  I'll see if I can find it.

I'm not finding anything on ACPI - but check [here]("http://ubuntuforums.org/showthread.php?t=588045&highlight=WUSB54gv4") for other WUSB54gv4 information.

---

### Post by M787M on 2008-03-28
I've tried that thread... the internet worked really slowly if at all, so I switched back to ndiswrapper.

Maybe something that will help?

> molly@George3:~$ ifconfig
eth0   Link encap:Ethernet  HWaddr 00:13:20:17:21:6E
          UP BROADCAST MULTICAST MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16

lo       Link encap:local loopback
          inet addr:127.0.0.1  Mask:255.0.0
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1669 (1.6 KB)  TX bytes:1669 (1.6 KB)

wlan0 Link encap:Ethernet HWaddr 00:12:17:7C:F8:90
          UP BROADCAST MULTICAST MTU:1500 Metric:1
          RX packets:15236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1747930 (1.6 MB)  TX bytes:34889 (33.9 KB)

wlan0:ava Link encap:Ethernet HWaddr:00:12:17:7C:F8:90
                 inet addr:  Bcast: Mask: (there are numbers for each of these, but I don't know whether I should post them? I'm really paranoid)
                UP BROADCAST MULTICAST MTU:1500 Metric:1

wmaster0-00 Link encap:UNSPEC HWaddr 00-12-17-7C-F8-90-00-00-00-00-00-00-00-00-00-00
                      UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
                     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                     collisions:0 txqueuelen:1000
                     RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

I don't know what either of those last two even mean...

---

### Post by miker999 on 2008-03-29
Don't know if this might help, but I had desktop freeze & router jam up - turned out to be a Firefox/Flash issue, it seems, although early days yet. I'm now using Opera.

Michael

---

