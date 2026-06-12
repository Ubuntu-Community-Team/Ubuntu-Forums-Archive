---
title: "Yawni - Yet another wireless network issue"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by martmort on 2007-04-26
I have an wireless adapter on my computer. It's an SMC SMC2602W. Feel like I've searched the whole web for the right drivers but without any luck. Anyone got some support?

Thanks for any help!

---

### Post by chili555 on 2007-04-26
And what does:```
lspci -v | grep Network
```say it's chipset is? If that command is unproductive, how about:```
sudo lshw -C network
```Thanks.

---

### Post by martmort on 2007-04-26
Then I got this.
```
martin@martin-desktop:~$ lspci -v | grep Network
03:09.0 Network controller: Standard Microsystems Corp [SMC] SMC2602W EZConnect / Addtron AWA-100 / Eumitcom PCI WL11000 (rev 02)
martin@martin-desktop:~$ sudo lshw -C network
Password:
  *-network:0             
       description: Ethernet interface
       product: 82801EB/ER (ICH5/ICH5R) integrated LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@03:08.0
       logical name: eth0
       version: 02
       serial: 00:30:05:69:b3:2d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: iomemory:c0205000-c0205fff ioport:4000-403f irq:21
  *-network:1 DISABLED
       description: Ethernet interface
       product: SMC2602W EZConnect / Addtron AWA-100 / Eumitcom PCI WL11000
       vendor: Standard Microsystems Corp [SMC]
       physical id: 9
       bus info: pci@03:09.0
       logical name: wlan0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_plx driverversion=0.2.5 latency=0 link=no multicast=yes
       resources: ioport:4800-487f iomemory:c0206000-c0206fff ioport:4400-443f irq:18


```

---

### Post by chili555 on 2007-04-26
Hmm! Wonder what we think of this?> driver=p80211_prism2_plx driverversion=0.2.5It appears, also, that an interface, wlan0, has been assigned. Please do:```
iwconfig
ifconfig
```and post the results. Thanks.

---

### Post by martmort on 2007-04-27
Then I got this:
```
martin@martin-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.

martin@martin-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:05:69:B3:2D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0:avah Link encap:Ethernet  HWaddr 00:30:05:69:B3:2D  
          inet addr:169.254.5.35  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2564 (2.5 KiB)  TX bytes:2564 (2.5 KiB)

martin@martin-desktop:~$ 

```

---

### Post by chili555 on 2007-04-27
Hey! You told me this was going to be a yawn! It is anything but.

So far, my research has suggested three different drivers that may, or may not, work with this card. Let's try this. Open a terminal and do:```
sudo tail -f /var/log/messages
```That will allow you to watch kernel messages or complaints. Open another terminal and do:```
sudo modprobe prism2_plx
iwconfig
```Did a wireless interface appear? If so, can you do:```
sudo iwlist <new_wireless_interface> scan
```Do you see any complaints or other messages in the first terminal?

If this module fails, repeat the process with these modules: orinoco_cs and adm8211. One of these should kick your card to life. Post back and let us know.

---

### Post by martmort on 2007-04-29
I did what you said and nothing happened.. So I tried with the different drivers and the only one I got a reaction on in the other terminal was the last one, the adm8211.. I got this..

```
Apr 29 17:14:02 martin-desktop kernel: [  181.870129] adm8211: Copyright 2003, Jouni Malinen <jkmaline@cc.hut.fi>; Copyright 2004-2006, Michael Wu <flamingice@sourmilk.net>

```

And if you wanna check if I did it right, here's what I typed in.

```
martin@martin-desktop:~$ sudo modprobe prism2_plx
martin@martin-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.

martin@martin-desktop:~$ sudo modprobe orinoco_cs
martin@martin-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.

martin@martin-desktop:~$ sudo modprobe adm8211
martin@martin-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.

martin@martin-desktop:~$ 
```

I really appreciate your time helping me :)

---

### Post by martmort on 2007-05-02
*bump*

---

