---
title: "Peculiar disconnecting problem"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by InRainbows001 on 2008-02-23
My internet connection has been disconnecting every hour or so recently, and i haven't been able to reconnect until i unplug my wireless adapter (belkin g) and plug it in to a different USB port. anyone have any ideas why this is happening?

---

### Post by Sam Lars on 2008-02-23
I used to have problems with my wireless dropping out, too (though I don't have a USB).  Does
```
sudo ifdown eth0
sudo ifup eth0
```
do the trick (replace eth0 with your interface)?

---

### Post by InRainbows001 on 2008-02-23
hi, thanks for the reply. this is what i got in the terminal:

tony@tony-desktop:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
tony@tony-desktop:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
tony@tony-desktop:~$ 

is that what i should've got?

---

### Post by Sam Lars on 2008-02-23
The first one maybe, but the second one seems to say that you have no wlan0, are you sure that's what you have set up?
What do you get from ifconfig?

---

### Post by InRainbows001 on 2008-02-23
yeah, that's what i've got set up

here's my ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:11:11:C3:D8:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:BC:A4:88  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:febc:a488/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18551746 (17.6 MB)  TX bytes:2257589 (2.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-BC-A4-88-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Sam Lars on 2008-02-23
What do you get from iwconfig?

---

### Post by InRainbows001 on 2008-02-23
tony@tony-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Belkin_G_Plus_MIMO_E20769"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:50:E2:07:69   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Sam Lars on 2008-02-23
It looks fine now, is this during a disconnect?

---

### Post by InRainbows001 on 2008-02-23
no, i got that when it was connected. it's been connected for a few hours now without any problems. do you know of anything i can do to prevent it from happening again?

---

### Post by Sam Lars on 2008-02-23
I don't know how to prevent it... do you get anything in syslog or dmesg?  I had a bunch of TX timeouts when mine was doing that... but it just stopped doing that.  I had a panel button to reset the connection for when that happened.
Are you using ndiswrapper?

---

