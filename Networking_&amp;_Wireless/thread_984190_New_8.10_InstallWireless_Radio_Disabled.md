---
title: "New 8.10 Install/Wireless Radio Disabled"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by logistician on 2008-11-16
Hello.

This morning, I decided to install Ubuntu on an old Gateway Laptop I had lying around.  This is my first experience with Ubuntu, so I was wondering if somebody could help me with an issue I'm having regarding my wireless setup?  The ubuntu built-in help is maddeningly frustrating!

Under the System->Preferences->Network Configuration box, my "Wireless" tab is showing empty, so I went to the ubuntu built-in help and it wanted me to check that the wireless device is on.  Now, with the original gateway/xp configuration, Fn+F2 would turn on/off the wireless radio (it was on prior to me installing ubuntu).  However, it looks like it got turned off, and pressing Fn+F2 now doesn't seem to enable/disable anything.

Running the sudo lshw -C network option shows that it is there, but showing DISABLED.  The help of course, loops back to say that some wireless radios must be enabled via windows.

Needless to say, I am kind of in an endless loop here.  Since I installed Ubuntu, I can't go back to Windows to enable the radio.

I tried searching the forums here, but unfortunately, it seems that searching for phrases doesn't seem to work (even when using quotes).

I apologize in advance if this has already been answered somewhere else.  Thanks!

---

### Post by jnorthr on 2008-11-16
could you please open a terminal session: Applications>Accessoris>Terminal and type in this command:
ifconfig
this will give us a picture of your network. Then try the command
iwconfig
as this gives more specific details of your wireless configurations. If you can post any of that output, we may be able to advise further.
:)

---

### Post by logistician on 2008-11-16
> **jnorthr said:**
> could you please open a terminal session: Applications>Accessoris>Terminal and type in this command:
ifconfig
this will give us a picture of your network. Then try the command
iwconfig
as this gives more specific details of your wireless configurations. If you can post any of that output, we may be able to advise further.
:)

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:03:25:21:80:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17088 (17.0 KB)  TX bytes:17088 (17.0 KB)

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by logistician on 2008-11-16
Aha...I poked around the forums more and found my fix at [http://ubuntuforums.org/showthread.php?t=759100](http://ubuntuforums.org/showthread.php?t=759100)

---

