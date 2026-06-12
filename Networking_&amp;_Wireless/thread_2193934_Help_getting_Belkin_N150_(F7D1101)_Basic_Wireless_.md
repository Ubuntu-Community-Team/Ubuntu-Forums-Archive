---
title: "Help getting Belkin N150 (F7D1101) Basic Wireless adapter to work in mode monitor!"
date: 2013-12-15
forum: Networking &amp; Wireless
---

### Post by pakowalski86 on 2013-12-15
Hey all. New Ubuntu user here (Please bear with me :) ) and I'm trying to get my Belkin N150 USB wireless adapter to broadcast SSID's (using aircrack-ng) for a project I'm doing. I have got this to work with my other USB wireless adapter without a hiccup (Some realtek micro wireless adapter), but this one is giving me trouble. When I plugged in the Belkin adapter, everything seemed to work. I could connect to my local wifi no problem, but I couldn't get the adapter to go into monitor mode. Firstly, here's my lsusb (I'm running Ubuntu on a virtual machine for convenience atm):

lsusb:
```
Bus 001 Device 002: ID 050d:945a Belkin Components F7D1101 Basic Wireless USB Adapter v1000 [Realtek RTL8188SU]Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:0c:29:32:c3:2e            inet addr:192.168.139.128  Bcast:192.168.139.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe32:c32e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:477 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:76207 (76.2 KB)  TX bytes:28287 (28.2 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:187 errors:0 dropped:0 overruns:0 frame:0
          TX packets:187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18636 (18.6 KB)  TX bytes:18636 (18.6 KB)


wlan1     Link encap:Ethernet  HWaddr ec:1a:59:bf:c3:7f  
          inet6 addr: fe80::ee1a:59ff:febf:c37f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:499 errors:0 dropped:8 overruns:0 frame:0
          TX packets:173 errors:0 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:85690 (85.6 KB)  TX bytes:33618 (33.6 KB)



```

iwconfig:
```
wlan1     unassociated  Nickname:"rtl_wifi"          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


eth0      no wireless extensions.


lo        no wireless extensions.



```

When I try to go into monitor mode here's what happens:
```

paul@ubuntu:~$ sudo ifconfig wlan1 downpaul@ubuntu:~$ sudo iwconfig wlan1 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan1 ; Invalid argument.



```

Something interesting to note is that nothing shows up when I do airmon-ng on the belkin adapter:
```
paul@ubuntu:~$ sudo airmon-ng



Interface    Chipset        Driver





```

Compared to the properly working Ralink card:
```
Interface	Chipset		Driver

wlan0		Ralink RT2870/3070	rt2800usb - [phy0]

```

Don't have a name of the working card, it's this one: [http://www.newegg.com/Product/Product.aspx?Item=9SIA2BM15K9373](http://www.newegg.com/Product/Product.aspx?Item=9SIA2BM15K9373) (probably besides the point but w/e)

I'm really not sure what to do to get it working. I tried the instructions in this thread as a shot in the dark: [http://ubuntuforums.org/showthread.php?t=1522815&highlight=Belkin+F7D1101](http://ubuntuforums.org/showthread.php?t=1522815&highlight=Belkin+F7D1101) but it didn't make a difference. To reiterate, the network adapter seemed to find my wireless network fine, but airmon and monitor mode never seemed to work before and after I followed that thread.

Thanks for the help, I'll be around to provide any outputs all day.

---

### Post by pakowalski86 on 2013-12-15
Small update, I undid everything in the help thread above, and here's what I get from airmon-ng:
```
Interface	Chipset		Driver

wlan1		Unknown 		r8712u



```

```

paul@ubuntu:~$ sudo ifconfig wlan1 down
paul@ubuntu:~$ sudo iwconfig wlan1 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan1 ; Invalid argument.
```

---

### Post by networkingartist on 2014-01-08
I have the same issue. Does anyone know of a resolution for this?

---

