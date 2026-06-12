---
title: "BCM4318 Wireless Problems"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by drfalkor on 2006-11-10
Hi ubuntupeople, it has been a long time since I've posted here on the forums.. Some days ago I got a Dell **Inspiron 1300** Laptop with Windows XP preinstalled.. I formatted, and then installed *Ubuntu Edgy*!

Now, Here is my issue !.. I am trying to get my **Wireless card** to work, but with no succsess.

This is my wireless card when I do a "lspci":

**Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)**

This is my iwconfig
> wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


This is my ifconfig:
> wlan0     Link encap:Ethernet  HWaddr (I HAVE REMOVED THIS PART) 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Memory:dfbfe000-dfc00000 
------
ndiswrapper -v

> utils version: 1.9
driver version:        1.28
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
-----
ndiswrapper -l

> installed drivers:
bcmwl5          driver installed, hardware (14E4:4318) present (alternate driver: bcm43xx)

-----

I have followed this HOWTO: [http://ubuntuforums.org/showthread.php?t=285809]("http://ubuntuforums.org/showthread.php?t=285809")

Only that I have compiled ndiswrapper from source...

---'

I am trying to connect to a *public free internett network* that's named "defualt" but I just cant find it !
And, my Wireless green light is not lighting !

What more can i do ? I have looked in many forums, and yes, I have blacklisted the old driver and installed some new ones from: 
[ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip]("ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip")


Sorry for my long post, but I hope somebody can help me :)

---

### Post by PisstMSTRCHIEF on 2006-11-10
try typing the network name in: Network name (lol thats redundant!)

Just as I have it pictured:

---

### Post by drfalkor on 2006-11-10
I have tryed that already with no succsess :-?

---

### Post by drfalkor on 2006-11-10
Anyone ? I Really need this thing to work :(

---

### Post by gitargr8 on 2006-11-10
What happens when you run

```
iwlist wlan0 scan
```

?

Can you see the network you want to connect to?

---

### Post by drfalkor on 2006-11-10
> falkor@Flybox:~$ iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

falkor@Flybox:~$ iwlist eth1 scan
eth1      No scan results
falkor@Flybox:~$ 

Thats about it : / I WANT SO BADLY TO FIX THIS :S + The wireless is not lightning !

---

### Post by drfalkor on 2006-11-11
Anyone ? please, I don't want to go back to windows after years with Linux ! I am trying so hard to stay sane right now ! :(

---

### Post by steve.dhondt on 2006-11-11
yeah I got the exact same problem. Seems like ubuntu doesn't recognize our wireless receptors, hence the light on the receiver not burning. 

> steve@steve-desktop:~$ iwconfig
lo        no wireless extensions.

eth1      NOT READY!  ESSID:"Steve"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=31 dBm   Sensitivity=0/200  
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

steve@steve-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D3:A7:26:65  
          inet addr:192.168.2.141  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fea7:2665/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35437 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18779 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51593965 (49.2 MiB)  TX bytes:1460356 (1.3 MiB)
          Interrupt:217 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
steve@steve-desktop:~$ Iwlist wlan0 scan
bash: Iwlist: command not found
steve@steve-desktop:~$ iwlist eth1 scan
eth1      No scan results

I'm a noob here so got no idea what to do about this. Let me know if you find a solution I'm desperate to :(

---

### Post by drfalkor on 2006-11-11
OH well, I hate to say it and do it.. but, wintendo, here I come... Maybe next release of ubuntu.. see you all guys on the other side..I'll be back here to read ! :)

---

### Post by prince_niceguy on 2006-11-15
A dumb question though? Is your wireless switch enables? Just check  in after loging into windows if the light glows. 

I have the same card and it is work without issues. I too have compiled from source... ndiswrapper i mean.

---

### Post by tweaker99 on 2006-11-15
Im finding the same problem with my HP. If this helps, I uninstalled the HP Wireless Assistant in XP and found out I could not use my button to turn off or on my Broadcom wireless card. It seems its some what software driven rather than a mechanical off/on switch. If I shut it off with the assistant I can't turn it back on with the button either, I have to use the software. Hope this at least points someone in the right direction.

---

### Post by BlackRoseBud on 2006-11-15
Easy answer: [http://www.walmart.com/catalog/product.do?product_id=2470289](http://www.walmart.com/catalog/product.do?product_id=2470289)

---

