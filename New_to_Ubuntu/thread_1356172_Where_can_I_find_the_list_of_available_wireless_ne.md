---
title: "Where can I find the list of available wireless networks"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by joolz1234 on 2009-12-15
Hi I just installed Koala on my laptop. Used ndiswrapper to install the driver for my card, but now I can't find the list of networks (my windows detects several)  in my area... where is it? System-preferences-network connections is showing up empty.  The app I used, ndisgtk says my driver installed perfectly, so how do I connect? I know the answer is probably istaring at me in the face, but please bear with me. Thanks in advance. 

Btw, the icon in the top right of the screen only shows wired connections and vpn, no wireless.

---

### Post by hansdown on 2009-12-15
Hi joolz1234.

Click applications> accessories> terminal.

Enter 

```
iwconfig

```
Hit enter.

See if any come up.

---

### Post by PRC09 on 2009-12-15
Sometimes all thats required is a reboot and then it will detect just fine...

---

### Post by joolz1234 on 2009-12-15
no luck, hansdown ```
lo no wireless extensions 
eth0 no wireless extensions 
```.
PRC09, rebooting was the first thing I tried ;)

---

### Post by hansdown on 2009-12-16
> Btw, the icon in the top right of the screen only shows wired connections and vpn, no wireless.

You may need to disconnect the ethernet cable to get the wireless icon to show.

My laptop hides the icon when it is plugged in.

---

### Post by joolz1234 on 2009-12-16
I'm this close to giving up, don't know what else to do...Quick question: if I pop in the live cd and attempt to reinstall, will it know to install in the same partition tha ubuntu is using right now? Does that hold true for any Linux distro? I'm thinking probably not.

---

### Post by doas777 on 2009-12-16
it looks like your wifi driver is not being recognized by iwconfig
what do you get from 
```

ifconfig
sudo lshw -C network

```

---

### Post by joolz1234 on 2009-12-16
Here goes :
```

joolz@joolz-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:7c:f4:e5  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe7c:f4e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:138203 (138.2 KB)  TX bytes:21459 (21.4 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

joolz@joolz-laptop:~$ sudo lshw -C network
 
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0300000-f0300fff
  *-network
       description: Ethernet interface
       product: 88E8040T PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 12
       serial: 00:1e:68:7c:f4:e5
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.1.100 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:f0200000-f0203fff ioport:2000(size=256)


```

---

### Post by baddog144 on 2009-12-16
Are you sure that the wireless card is switched on? Try just toggling it once, then:
```

sudo ifconfig -a

```

---

### Post by joolz1234 on 2009-12-16
Thanks for replying baddog144, the card is indeed switched on :)
```

sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:68:7c:f4:e5  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe7c:f4e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:977 errors:0 dropped:0 overruns:0 frame:0
          TX packets:949 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1043924 (1.0 MB)  TX bytes:132608 (132.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```So...what does this tell me?

---

### Post by 3rdalbum on 2009-12-16
The list of wireless connections is NOT under System > Preferences > Network Connections. It is in the Network Manager applet on your top panel. Left-click it and see if there are any connections detected there.

If not, then it might be that Ndiswrapper is conflicting with the native Linux driver; As far as I can determine, the 3945ABG wireless device is supported by Ubuntu out-of-the-box. Try removing Ndiswrapper (ndiswrapper-common) and rebooting, then take a look at Network Manager and see what happens.

---

### Post by baddog144 on 2009-12-16
Hmm, that's...very strange :S
I have the exact same card on Jaunty, and it's working fine :(
Sorry, I don't have any idea, except for trying
```

sudo modprobe iwl3945

```
and then doing 
```

sudo ifconfig -a

``` 
again, and seeing if it turns up then. If it doesn't I truly have no idea :(

---

### Post by doas777 on 2009-12-16
> **joolz1234 said:**
> Thanks for replying baddog144, the card is indeed switched on :)
```

sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:68:7c:f4:e5  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe7c:f4e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:977 errors:0 dropped:0 overruns:0 frame:0
          TX packets:949 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1043924 (1.0 MB)  TX bytes:132608 (132.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```So...what does this tell me?

well, it tells me that your system does not believe that there is a wifi card attached. lshw should show the device even if you don't have a driver for it installed, so that is worrisome.

---

### Post by doas777 on 2009-12-16
> **3rdalbum said:**
> The list of wireless connections is NOT under System > Preferences > Network Connections. It is in the Network Manager applet on your top panel. Left-click it and see if there are any connections detected there.

If not, then it might be that Ndiswrapper is conflicting with the native Linux driver; As far as I can determine, the 3945ABG wireless device is supported by Ubuntu out-of-the-box. Try removing Ndiswrapper (ndiswrapper-common) and rebooting, then take a look at Network Manager and see what happens.
love the python part of your sig. were you on that trainwreck of a thread about that a couple weeks ago?

---

### Post by joolz1234 on 2009-12-17
So I burned a new ubuntu image, booted live...and my card worked. I'm going to try reinstalling, but ran into this : The ubuntu partitioner recognizes my windows AND  this ubuntu, then tries to install a 2nd ubuntu OS. I'm not sure I want to fly solo when dealing with disk partitioning, which ones should I delete? there's swap and ext and whatnot...

---

### Post by natravis on 2009-12-17
> **joolz1234 said:**
> So I burned a new ubuntu image, booted live...and my card worked. I'm going to try reinstalling, but ran into this : The ubuntu partitioner recognizes my windows AND  this ubuntu, then tries to install a 2nd ubuntu OS. I'm not sure I want to fly solo when dealing with disk partitioning, which ones should I delete? there's swap and ext and whatnot...

You should try just removing ndiswrapper first and rebooting.

If that does not work and you want to wipe it and reinstall, proceed.

If you do not care about anything on the current Ubuntu install, when the Partitioning Wizard comes up, select manual. If you want to auto mount windows (for whatever reason) you can setup a mount point like /windows but DO NOT select format. From what you said, it seems to have 3 partitions total (windows, ubuntu, swap). You can mark the ubuntu partition for mounting as "/" (root) and format it. You can mark the swap as swap for use as swap.

---

### Post by joolz1234 on 2009-12-17
Ended up deleting the ubuntu partitions with windows, then reinstalling  from the cd. Works like a charm. Thanks for all the help guys.

---

### Post by chillyomi on 2009-12-17
shouldn't there be a tab for wireless connections can you see it

---

### Post by baddog144 on 2009-12-17
> **joolz1234 said:**
> Ended up deleting the ubuntu partitions with windows, then reinstalling  from the cd. Works like a charm. Thanks for all the help guys.

Heh, well as long as you got it working in the end :P

---

