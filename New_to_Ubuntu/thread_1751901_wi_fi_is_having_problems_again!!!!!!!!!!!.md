---
title: "wi fi is having problems again!!!!!!!!!!!"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by blake7 on 2011-05-07
this odd my wi fi is not picking up a clean signle in the rooms next door to the router

what is odd is this is the same problem i has with 10.04 which went away with 10.10 and is now back again with 11.04

also a other old problem has come back when iam viewing vidio and close my laptop lid it freezes my laptop up so i have to re boot

all problems are back again

cheers 
ps i have ibm x60s
ps can any exsplain why old problem could be back ????

---

### Post by Redblade20XX on 2011-05-07
What type of wireless card do you have? In the terminal type either: ifconfig or iwconfg and post the results!

---

### Post by blake7 on 2011-05-07
does that help?
thank you 


dude@dude:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:33:9a:79  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:331 errors:0 dropped:0 overruns:0 frame:0
          TX packets:331 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53444 (53.4 KB)  TX bytes:53444 (53.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:04:47:d9  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe04:47d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:147473 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93563 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:176549023 (176.5 MB)  TX bytes:8872811 (8.8 MB)

---

### Post by Redblade20XX on 2011-05-07
Post the output for this command plz.
[FONT=monospace]
[/FONT]lspci -v | less

---

### Post by blake7 on 2011-05-07
thank you   :)

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at ee100000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at ee200000 (32-bit, non-prefetchable) [size=256K]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML E:

---

### Post by Redblade20XX on 2011-05-07
Did you do a clean install or an upgrade for 11.04? Currently 11.04 is kind of buggy, so if your willing reinstall 10.10 and give 11.04 a month or two to develop?

---

### Post by blake7 on 2011-05-07
ok can i go back with out changing the setting or set up of my laptop ??
why does ubuntu just not do 1 release each year????
it seems crazy doing two they never get it right.(it would also make your jobs much easier)


thank you for all your help

---

### Post by Redblade20XX on 2011-05-07
It's always good to give open source projects a couple of weeks to work out the bugs. From what I know, you can't downgrade so you'll need to fresh install 10.10. Back up all your data before you start thought. Also there are methods to test out any new distribution without changing your current build. Look up virtualbox.

---

### Post by blake7 on 2011-05-07
cool

and thanks once aggaain

---

