---
title: "Cannot access wireless network"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by richlatham on 2008-12-14
Hi
Just getting started with Ubuntu. Problem I'm having is accessing wireless network. I have clickeed on the network button at the top of the screen and can "create" a new wireless network or connect to a "hidden" network. But when I enter the password etc. it says "disconnected from network". So actually, I cannot connect.

How do you search for wireless networks? My router broadcasts the SSID, so I can see it in Windows XP.

Just a thought, but the MAC address will be the same whether I'm running XP or Ubuntu, won't it? My router only allows certain MAC addresses to access it.
Thanks.

---

### Post by jay li on 2008-12-14
What is the spec of your laptop?

---

### Post by richlatham on 2008-12-14
It's a 3 year old desktop.
2gb RAM, AMD Athlon 64 2800+, Linksys Wireless-G network card.

---

### Post by jay li on 2008-12-14
You may try that [http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Wireless_Cards](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Wireless_Cards)

---

### Post by richlatham on 2008-12-14
Thanks for that - I'll give it a go.

---

### Post by richlatham on 2008-12-14
Tried it, but still can't access wireless network. Thanks for advide anyway.

---

### Post by Michael.Godawski on 2008-12-14
hi richlatham,

What version of Ubuntu are you using?

Can you please post the output of these terminal commands?

```
sudo lshw -C network
iwconfig
ifconfig
sudo iwlist scan
```

---

### Post by richlatham on 2008-12-14
> **Michael.Godawski said:**
> hi richlatham,

What version of Ubuntu are you using?

Can you please post the output of these terminal commands?

```
sudo lshw -C network
iwconfig
ifconfig
sudo iwlist scan
```

Hi
It's Ubuntu 8.10
Output from above commands:
richard@richard-desktop:~$ sudo lshw -C network
[sudo] password for richard: 
  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:66:6d:f4:05
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 36:79:54:99:a3:0a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
richard@richard-desktop:~$ iwconfig
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

richard@richard-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:2a:93:54:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

richard@richard-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.

richard@richard-desktop:~$

---

### Post by stickman51 on 2008-12-14
rich, my problem is similar to yours and I have not had any replies to my question in the past day-and-a-half so I'll re-post the question, hoping that is allowed.

The folks in this forum have been SUPER helping me get Ubuntu running but I cannot get online yet.

Maybe my thread will give you some ideas that may help.

ken

---

### Post by karlr42 on 2008-12-14
The MAC address will be the same, it's built into the memory of the wifi card itself. 
I'm assuming you left-click on the network icon, click your SSID, enter the password, then get this "disconnected" message? If not, could you try that?

---

### Post by Michael.Godawski on 2008-12-14
Broadcom is a beast (BCM4306), as you will see on these sites:

[LIST]
[*][https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)
[*][http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)
[/LIST]

---

### Post by richlatham on 2008-12-18
Hi
Difficult to remember exactly what I type because it's a dual boot machine and I'm using Windows XP now, but the "wireless networks" is greyed out and I get prompted to "connect to a hidden wireless network". I enter the SSID, followed by password and then it comes up with "disconnected from network". It seems the Linksys wireless card isn't being recognised.

---

