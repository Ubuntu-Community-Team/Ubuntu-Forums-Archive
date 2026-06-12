---
title: "help configuring wireless"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by chimanrao on 2007-03-24
hi

I have succesfully managed to install kubuntu 6.10.
Now I am stuck trying to configure my wirelss.

I see two wirless interfaces getting identified:
wlan0
wmaster0

I tried using the wireless lan assistant, but its not finding any network. (The network is up and running, thats how I am posting this post).

The network uses wep encryption, open and has a 64bit key.

Help!
Chimanrao

PS: I am not a techie, so if the solution to this involves some sort of kernel compilation, do let me know, I will have to reconsider using linux.

---

### Post by chimanrao on 2007-03-24
I changed my wireless card from DLink PCI card to a AirLink usb based wireless dongle.

Now I can see the network listed, but its still not connecting.
On the wireless router I have the following key listed in the wepkey 260b3c4937,

is this key ascii or hex?

I tried all options but its not connecting.
Chimanrao

---

### Post by handaxe on 2007-03-24
Hi,

asci key must have a s: before it, not so?

In case that does not work, please post outputs from each of these run in a terminal

```
sudo lshw -C network

sudo ifconfig

sudo iwconfig

```

HA

---

### Post by Albert E. on 2007-03-24
I too am having problems configuring my wireless. I got the following from those commands:

 sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:bf:a9:f0
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=sky2 driverversion=1.6.1 duplex=full firmware=N/A ip=192.168.2.20 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:bc000000-bc003fff ioport:a000-a0ff irq:11
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@06:04.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:4c:0c:72
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.1.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) link=no multicast=yes wireless=unassociated
       resources: iomemory:b000b000-b000bfff irq:11


sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:BF:A9:F0  
          inet addr:192.168.2.20  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:febf:a9f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:818043 (798.8 KiB)  TX bytes:201833 (197.1 KiB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:4C:0C:72  
          inet6 addr: fe80::212:f0ff:fe4c:c72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5798 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3070 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:b000b000-b000bfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1558 (1.5 KiB)  TX bytes:1558 (1.5 KiB)


sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"Wireless"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:1393-8917-4705-7334-0000-0000-00   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


I tried using the System ->Admin-> Networking menu, entered my password for the Wireless connection there and nothing happened :(

Any ideas what is going on?

---

### Post by handaxe on 2007-03-24
Looks to me as a hex/asci issue. The encryption key is meant to be i hex (26 numbers/letters) but you have entered it in the asci form (16), hence the 10 zeros.

Place s: before the key and see if that helps.

HA

---

### Post by chili555 on 2007-03-24
> I have the following key listed in the wepkey 260b3c4937, is this key ascii or hex?Hex, no prefix needed.

---

### Post by chili555 on 2007-03-24
Albert E.-
Your wireless will not connect as long as your ethernet is connected.```
eth0 Link encap:Ethernet HWaddr 00:A01:BF:A9:F0
inet addr:192.168.2.20 Bcast:192.168.2.255 Mask:255.255.255.0
```Please disconnect the ethernet cable, restart networking:```
/etc/init.d/networking restart
```Then double-check that eth0 has dropped it's address```
ifconfig -a
```If not, reboot.

NOW, try to configure your wireless.

To all-
Correctly configuring WEP is a delicate task. Here is a tutorial that may help:[http://www.ubuntuforums.org/showthread.php?t=172810&page=2](http://www.ubuntuforums.org/showthread.php?t=172810&page=2)

---

### Post by handaxe on 2007-03-24
@chili555,

seems like I need to leech some more knowledge from you :)

Under what circumstances will wireless not work with wired? I am confused as mine does, at least with wpa.  Is it a wep & wired matter?

Hope you don't mind the asking...
tx,

HA

---

### Post by chili555 on 2007-03-24
Certainly, NetworkManager won't do it, it's specifically designed to drop wireless if wired is available. I managed to do it once, just to see if I could mess things up. I keep an old Thinkpad T23 around just to wreck once in a while.

When I got it going, I could reach the web, but not ssh or ping in my network, couldn't access the router's administration pages, fping couldn't find anybody on the network but myself wired and myself wireless. In short, all kinds of network stuff went south. I didn't try every network related thing I could, email, instant messaging, FTP, etc.; the sweat pouring off my brow was starting to pool on the keyboard.

I'm not saying it *absolutely, positively will not work,* I'm saying it most likely won't work, will hinder your efforts to sort out wireless connection problems and why would you want to? Why complicate the already daunting job of wireless newbie?

Perhaps our esteemed colleague, Mr.C will chime in here.

---

### Post by handaxe on 2007-03-24
ta chili555,

I use Wicd rather than NetworkManager, so that probably explains it although I admit I did not test thoroughly.

I agree about keep it simple so know I know...

HA

---

