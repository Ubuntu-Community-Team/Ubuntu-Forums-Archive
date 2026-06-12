---
title: "[HELP] Need guidence for setting up a Wireless Connection."
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by ojdon on 2008-07-30
Hey there, I have Ubuntu Dual Booted with Windows XP on my laptop. At the moment I have Ubuntu connected to a Ethernet cable and I just plug that in and it works. But the cable is actually for the family PC. 

I've tried several methods trying to at least find the Wireless Connection (BT VOYAGER 2091) but no luck. I just need a step by step guidance to get connected (Like the Windows XP) to my Wireless Network. 

Thanks!

---

### Post by Kevbert on 2008-07-30
Please post the output (from terminal) of
```
lshw -C network
```

---

### Post by ojdon on 2008-07-30
```
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
       vendor: Linksys, A Division of Cisco Systems
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=64 maxlatency=32 mingnt=32
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:0a:e4:5f:a1:bd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes

```

---

### Post by superprash2003 on 2008-07-30
hope this helps [http://sicksand.net/post/32208741/inprocomm-ipn-2220-wireless-lan-adapter-problem-in](http://sicksand.net/post/32208741/inprocomm-ipn-2220-wireless-lan-adapter-problem-in)

---

### Post by Kevbert on 2008-07-30
Please take a look at this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=133492").

---

### Post by ojdon on 2008-07-30
> **Kevbert said:**
> Please take a look at this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=133492").

I did follow this post and it seems that my case is the same as the guy who started that post. I downloaded the driver I used for XP from the Acer website, I know it's the correct driver since it works on XP. 

So I followed the instructions in the link and that all went fine, but I don't know where to go from now, the driver is present etc, but I do not know how to connect to my wireless box again. 

Thank you for your help so far.

---

### Post by Kevbert on 2008-07-30
If everything went OK it's probably best to reboot the PC first.  Now on the top right (menu) bar you may have a twin display icon with a cross on it.  If you right-click on it check that both Enable Networking and Enable Wireless are ticked.  If you left-click on the icon you should have a list of available wireless networks (just select your network and a window should appear asking for a password).  You should then get a connection when the icon changes to four bars.  If not, please post the output from terminal of
```
iwconfig
ifconfig 

```

---

### Post by ojdon on 2008-07-30
> **Kevbert said:**
> If everything went OK it's probably best to reboot the PC first.  Now on the top right (menu) bar you may have a twin display icon with a cross on it.  If you right-click on it check that both Enable Networking and Enable Wireless are ticked.  If you left-click on the icon you should have a list of available wireless networks (just select your network and a window should appear asking for a password).  You should then get a connection when the icon changes to four bars.  If not, please post the output from terminal of
```
iwconfig
ifconfig 

```

I've rebooted several time but no help. When I right click over the Two Monitors I only get one box that says "Enable Networking" that is ticked, if I go to "Edit Wireless Networks" there are no wireless networks to choose from. When I left click I only get the option to connect to the wired connecion (I am using the Ethernet Cable from the back of the family PC, into my laptop) 

Anyway, here is the output from:

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.


```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:5f:a1:bd  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fe5f:a1bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1450 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1171326 (1.1 MB)  TX bytes:239634 (234.0 KB)
          Interrupt:20 Base address:0x4800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2928 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2928 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:146400 (142.9 KB)  TX bytes:146400 (142.9 KB)

```

---

### Post by Kevbert on 2008-07-31
Have you had the ethernet cable connected all the time ?  Disconnect the cable, reboot and see if anything changes.  It's strange that it doesn't look as if the wireless drivers have installed :confused:

---

### Post by ojdon on 2008-07-31
> **Kevbert said:**
> Have you had the ethernet cable connected all the time ?  Disconnect the cable, reboot and see if anything changes.  It's strange that it doesn't look as if the wireless drivers have installed :confused:

I've reboot several times without the ethernet cable plugged in. This is how it looks without the ethernet cable in after rebooting/shutting down and turning on again (I've put it in a link so it doesn't stretch the screen) 

[http://img177.imageshack.us/img177/3354/wirelessjq8.png](http://img177.imageshack.us/img177/3354/wirelessjq8.png)

I'm not to sure if this is right but it seems that the "two monitors" are on. I can't connect since I haven't got the cable in. Anyway, I made a few more screenshots to see if this will indicate my problem: 

[http://img177.imageshack.us/img177/1680/wirelessci7.png](http://img177.imageshack.us/img177/1680/wirelessci7.png)
I don't have a choice to choose my wireless connection here (If that is the place to choose)

[http://img210.imageshack.us/img210/7348/nowirelessbh8.png](http://img210.imageshack.us/img210/7348/nowirelessbh8.png)
There isn't a way to try and set it up here is there?

---

### Post by Kevbert on 2008-07-31
That's interesting you have two (two) monitor icons which are for wired connection (you should only have one). I don't know what to suggest...

---

