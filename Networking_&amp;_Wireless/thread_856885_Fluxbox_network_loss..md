---
title: "Fluxbox network loss."
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by DocYoung on 2008-07-11
I have my wireless network working while in gnome but when I switch sessions to fluxbox after restart, my wireless no longer works. It see my wireless card with driver fine as eth1 but doesnt seem to resolve an address for it.

I've searched but seen no other threads on the subject thought my search fu is weakish.

Any ideas or suggestions would be appreciated.

Thanks in advance.

-Doc

---

### Post by Hooya on 2008-07-11
when you log into fluxbox run iwconfig in a terminal and post the output.

Oh, and run nm-applet to get the same network manager taskbar icon thingy as in gnome.

I put "nm-applet &" in my ~/.fluxbox/startup

---

### Post by DocYoung on 2008-07-11
> **Hooya said:**
> when you log into fluxbox run iwconfig in a terminal and post the output.

Oh, and run nm-applet to get the same network manager taskbar icon thingy as in gnome.

I put "nm-applet &" in my ~/.fluxbox/startup

odin@odinware:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
odin@odinware:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:05:9b:f8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:ee:7a:56  
          inet6 addr: fe80::21a:73ff:feee:7a56/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3400 (3.3 KB)  TX bytes:3400 (3.3 KB)

odin@odinware:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:ee:7a:56
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:68:05:9b:f8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
odin@odinware:~$

---

### Post by DocYoung on 2008-07-11
Sorry for the extra I thought it might be asked for also.

Ill do the nm-applet &" in my ~/.fluxbox/startup to see what that gets me.

Thank you again.

-Doc

---

### Post by DocYoung on 2008-07-11
> **Hooya said:**
> ...
Oh, and run nm-applet to get the same network manager taskbar icon thingy as in gnome.

I put "nm-applet &" in my ~/.fluxbox/startup

OMG you couldn't have made that any easier ....

you rock ...:guitar:

Fixed. Way to simple and now I feels like an idiot. LOL

Thank you again,
you rock

-Doc

---

### Post by DocYoung on 2008-07-11
> **Hooya said:**
> when you log into fluxbox run iwconfig in a terminal and post the output.

Oh, and run nm-applet to get the same network manager taskbar icon thingy as in gnome.

I put "nm-applet &" in my ~/.fluxbox/startup

BTW I owe you a beer ... or six if ever we should meet.

---

### Post by Hooya on 2008-07-12
No problem, glad I could help.  :-)

---

