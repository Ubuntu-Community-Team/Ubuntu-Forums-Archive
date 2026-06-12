---
title: "Can't connect wirelessly (D-Link DWL-G510)"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by Janzuka on 2007-06-18
Hey,

I'm experiencing the following problem: I installed this wireless card (D-Link DWL-G510), downloaded Ndiswrapped and installed the driver, then tried to connect - but, surprisingly, it wasn't that easy.
Although Ndiswrapper could install the driver it says hardware is not present. Regardless of this my OS (feisty) recognizes the card: the wireless network can be found, but, somehow, it fails to connect. It tries really hard - without any results whatsoever.
Any help is appreciated :)

---

### Post by charleseddy on 2007-06-18
At this point, I'd like you to do three things, then post them back here.

Go to a terminal and type the following commands:
iwconfig
ipconfig

Paste the terminal's entire output, then go to a terminal and type this:

sudo gedit /etc/network/interfaces

Paste what comes up in the text editor as well.  That should help us to troubleshoot a little more.

ce

p.s.  Also, save it to a file in case you need to retrieve it for a later post.

---

### Post by ThenonS on 2007-06-24
I`m having some problems with my D-Link too, I have a DWL-G510 and this is what comes up with those commands.
```
brett@brett-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:"BTVOYAGER2500V-5B"  Nickname:""
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:11:F5:EA:34:5B   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=60/100  Signal level:-64 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

brett@brett-desktop:~$ ipconfig
bash: ipconfig: command not found
brett@brett-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:8F:C6:D5:17  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fec6:d517/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9928 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8718 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12998447 (12.3 MiB)  TX bytes:738415 (721.1 KiB)
          Interrupt:21 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ra0       Link encap:Ethernet  HWaddr 00:19:5B:D0:DF:BC  
          inet6 addr: fe80::219:5bff:fed0:dfbc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3749 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:38 dropped:38 overruns:0 carrier:0
          collisions:14 txqueuelen:1000 
          RX bytes:345286 (337.1 KiB)  TX bytes:8233 (8.0 KiB)
          Interrupt:19 

ra0:avahi Link encap:Ethernet  HWaddr 00:19:5B:D0:DF:BC  
          inet addr:169.254.10.104  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 


```

[I]auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface ra0 inet dhcp
wireless-essid BTVOYAGER2500V-5B
wireless-key s:************* (not letting you see that :S)

auto ra0

auto eth0[/I]

At first I was seeing the router but not getting a strong signal with the signal icon in red, I tried to manually configure it but it didn`t work, now its not giving me the option to connect wirelessly. I`m using the network manager.

---

### Post by Janzuka on 2007-06-24
Hey, and sorry for the late reply.

By typing iwconfig i get

janne@funky-town:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

By typing ipconfig i somehow get nothing at all :O

And in the text editor, the following can be read:

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

Hopefully, with the help of these, you can figure out something. Especially when there are others having the same problem, too.

---

### Post by ThenonS on 2007-06-25
he has misspelled that command its supposed to be *ifconfig* not *ipconfig*

---

### Post by Janzuka on 2007-06-25
Wait a minute! This code was of no use, as the wireless card has mysteriously disappeared from each menu.
I'll get back to you as soon as i get it to appear again.

---

### Post by kevdog on 2007-06-25
I thought ndiswrapper installed by default a driver for the named interface wlan0.  Can you post the following for me:

ndiswrapper -v
ndiswrapper -l

Did you get your driver from the ndiswrapper website?
What kind of chipset do you have for this card anyway??:
lspci

---

