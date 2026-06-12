---
title: "internet problems"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by allsys3 on 2009-08-29
I recently removed my wireless internet router (it was borrowed)and now am plugged straight into my PC. Now however I cant seem to get my internet to connect. What information would be best to supply to the forum so someone could help me? Thanks

---

### Post by earthpigg on 2009-08-29
right click on the network applet, disable wireless?

what other things have you tried?

---

### Post by allsys3 on 2009-08-29
I've tried everything and nothing seems to work

---

### Post by halitech on 2009-08-29
can you post the output of
```
lspci
```
```
lsusb
```
```
lshw -C network
```and 
```
sudo ifconfig
```

---

### Post by Iowan on 2009-08-29
**ifconfig -a** will show all interfaces - including those that are unconfigured.

---

### Post by allsys3 on 2009-08-31
These are the reslts I got:
lspci


00:00.0 Host bridge: nVidia Corporation Unknown device 0071 (rev a3) 
00:00.1 RAM memory: nVidia Corporation Unknown device 007f (rev a1) 
00:00.2 RAM memory: nVidia Corporation Unknown device 0075 (rev a1) 
00:00.3 RAM memory: nVidia Corporation Unknown device 006f (rev a1) 
00:00.4 RAM memory: nVidia Corporation Unknown device 00b4 (rev a1) 
00:01.0 RAM memory: nVidia Corporation Unknown device 0076 (rev a1) 
00:01.1 RAM memory: nVidia Corporation Unknown device 0078 (rev a1) 
00:01.2 RAM memory: nVidia Corporation Unknown device 0079 (rev a1) 
00:01.3 RAM memory: nVidia Corporation Unknown device 007a (rev a1) 
00:01.4 RAM memory: nVidia Corporation Unknown device 007b (rev a1) 
00:01.5 RAM memory: nVidia Corporation Unknown device 007c (rev a1) 
00:01.6 RAM memory: nVidia Corporation Unknown device 007d (rev a1) 
00:02.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2) 
00:04.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2) 
00:05.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2) 
00:06.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2) 
00:07.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2) 
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2) 
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2) 
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2) 
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2) 
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) 
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) 
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) 
00:0e.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1) 
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) 
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) 
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 [Sapphire X550 Silent] 
01:00.1 Display controller: ATI Technologies Inc RV370 secondary [Sapphire X550 Silent] 
06:06.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10) 
06:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13) 

lsusb

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 04f9:01d7 Brother Industries, Ltd 
Bus 001 Device 003: ID 046d:c317 Logitech, Inc. 
Bus 001 Device 002: ID 1210:0009  
Bus 001 Device 001: ID 0000:0000  

lshw -c network 

Hardware Lister (lshw) - B.02.10 
usage: lshw [-format] [-options ...] 
       lshw -version 

        -version        print program version (B.02.10) 

format can be 
        -html           output hardware tree as HTML 
        -xml            output hardware tree as XML 
        -short          output hardware paths 
        -businfo        output bus information 

options can be 
        -class CLASS    only show a certain class of hardware 
        -C CLASS        same as '-class CLASS' 
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. ) 
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. ) 
        -quiet          don't display status 

sudo ifgonfig  

eth0      Link encap:Ethernet  HWaddr 00:18:F3:97:A6:11  
          inet addr:192.168.254.254  Bcast:192.168.254.255  Mask:255.255.255.0 
          inet6 addr: fe80::218:f3ff:fe97:a611/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:4688 (4.5 KB)  TX bytes:7601 (7.4 KB) 
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:1600 (1.5 KB)  TX bytes:1600 (1.5 KB)

---

### Post by halitech on 2009-08-31
lshw -C network is not the same as lshw -c network, linux is case sensative.

It looks like you have an IP address on eth0. Can you ping google.com or 74.125.45.100?

---

### Post by mapes12 on 2009-09-01
That's an odd IP address. What output do you get from ```
ping -c4 192.168.254.254
```Can you access your routers Admin screen (the user manual should have instructions via a web browser for doing this) and have a look at how the router assigns IP addresses. Most have DHCP enabled which automatically assigns addresses. Yours is currently right at the top of the 192.x.x.x range. 

I'm assuming your router also acts as the ADSL modem to access broadband? 

As the other post said you my also want to turn of the wifi AP (Access Point). If you're not using it then turning it off eliminates anyone hijacking it. If you can't turn it off set WPA encryption with a strong password.

---

### Post by allsys3 on 2009-09-01
sorry for the earlier mistake. This is what I get : 

*-network               
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: c
       bus info: pci@0000:06:0c.0
       logical name: eth0
       version: 13
       serial: 00:18:f3:97:a6:11
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=skge driverversion=1.11 firmware=N/A ip=192.168.254.254 latency=32 maxlatency=31 mingnt=23 module=skge multicast=ye

 ping 74.125.45.100
connect: Network is unreachable

---

### Post by alphacrucis2 on 2009-09-01
What do you get from:

```
route -n
```

---

### Post by allsys3 on 2009-09-02
Is there any hope for me?

---

### Post by mapes12 on 2009-09-02
> **allsys3 said:**
> Is there any hope for me?Yep!

Have you looked at my last post #8?

I guess you have removed your wifi card from your PC. It isn't showing in lspci nor lsusb but if it's still there then I would remove it.

---

### Post by allsys3 on 2009-09-02
No wifi card. I just have my internet connection into my modem and then straight into my computers built in Marvell Lan.

---

### Post by allsys3 on 2009-09-02
I'm just about ready to pack it in with Ubuntu and head back to Windows like a dog with its tail between its legs because solving something as simple as an internet hookup is just too time consuming and frustrating for me.

---

