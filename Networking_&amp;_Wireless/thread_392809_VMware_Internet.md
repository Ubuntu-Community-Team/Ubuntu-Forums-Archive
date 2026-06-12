---
title: "VMware Internet"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by cmillican on 2007-03-25
When I'm running Windows XP in VMware Server, I can't get an internet connection on Windows (it doesn't even recognize an ethernet port). When I set up the program, I remember it asked if I wanted networking, and I think I may have put no, but then later, I thought I switched it. I have already gone through much trouble to install Windows, and I was wondering if there was any way to fix this without having to reinstall.

Thanks,
Chris

---

### Post by Floppyjoe on 2007-03-25
> **cmillican said:**
> When I'm running Windows XP in VMware Server, I can't get an internet connection on Windows (it doesn't even recognize an ethernet port). When I set up the program, I remember it asked if I wanted networking, and I think I may have put no, but then later, I thought I switched it. I have already gone through much trouble to install Windows, and I was wondering if there was any way to fix this without having to reinstall.

Thanks,
Chris

Do you see an option to configure an ethernet port when you click on edit virtual machine settings?
If not you can possibly try to add an ethernet port although I am not sure as I have not needed to do this before.

---

### Post by cmillican on 2007-03-25
No matter which setting I select, every time I hit "Connect" for the Ethernet, I get this:

Could not open /dev/vmnet0: No such file or directory
Failed to connect virtual device Ethernet0.

---

### Post by cmillican on 2007-03-25
Ok, I figured it out. To change settings selected during installation, you go to /usr/bin/vmware-config.pl and it guides you through it again. Thanks.

---

### Post by bennyj on 2007-04-22
I am running vmware player with windows xp pro on an ubuntu fiesty box.For the life of me i can not get windows xp (running in the virtual) to get an internet connection.I have tried bridged,nat and host.this is what i get when i run "ifconfig"
```
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:76:1B:F2:38  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:fe1b:f238/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10507 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9551 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6109223 (5.8 MiB)  TX bytes:1346376 (1.2 MiB)
          Interrupt:17 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:201121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:201121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72954389 (69.5 MiB)  TX bytes:72954389 (69.5 MiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.77.1  Bcast:192.168.77.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1615 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.226.1  Bcast:192.168.226.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1613 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

When I go into my virual windows and select devices I can see that my ethernet contoler has that yellow exclamation mark next to it.I try to update driver but it wants to connect to the internet to do it which of course I cant do.

from the terminal in ubuntu I can ping the ip addresses under vnmet1 and vmnet8. I have a router(linksys) between my comp and modem. I went in and add the mac address just to be on the safe side(I have mac enabled) but still nothing.

I have searched high and low but everything I have read so far seems to have been fixed by just swithcing from bridged to nat in the virtual settings,this does not work for me.Any suggestions.
thx

---

