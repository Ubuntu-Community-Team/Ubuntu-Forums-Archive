---
title: "Cannot Connect To Internet After Install"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by gruurly on 2009-08-17
Installed newest version earlier today but can't get on the net. Using Shaw in Canada with an ASUS modem. System -> Administration -> Hardware Drivers doesn't show the driver, and the synaptic package manager doesn't either.     
iconfig eth1 says: error reading interface information    
Total n00b here (but tech savvy). Help?

---

### Post by gruurly on 2009-08-17
Oops, should also add this is a laptop, and not wireless. ASUS motherboard, every thing else was pieced together/custom made... not sure how to get a list of what the comp is comprised of, but if someone can tell me what terminal command to use, I'll post it. 

Thanks! :)

---

### Post by Riaku on 2009-08-17
Does it show the wireless bars beside the date?
Was it working before the install?

---

### Post by gruurly on 2009-08-17
No wireless, there is no wireless on this computer. 

Yes, it worked before with XP no problem right before install.

---

### Post by gruurly on 2009-08-17
More data.

ifconfig

Linux XXXX-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

00:00.0 "0600" "8086" "2578" -r02 "1043" "80f6"
00:01.0 "0604" "8086" "2579" -r02 "" ""
00:06.0 "0880" "8086" "257e" -r02 "" ""
00:1d.0 "0c03" "8086" "24d2" -r02 "1043" "80a6"
00:1d.1 "0c03" "8086" "24d4" -r02 "1043" "80a6"
00:1d.2 "0c03" "8086" "24d7" -r02 "1043" "80a6"
00:1d.3 "0c03" "8086" "24de" -r02 "1043" "80a6"
00:1d.7 "0c03" "8086" "24dd" -r02 -p20 "1043" "80a6"
00:1e.0 "0604" "8086" "244e" -rc2 "" ""
00:1f.0 "0601" "8086" "24d0" -r02 "" ""
00:1f.1 "0101" "8086" "24db" -r02 -p8a "1043" "80a6"
00:1f.3 "0c05" "8086" "24d3" -r02 "1043" "80a6"
00:1f.5 "0401" "8086" "24d5" -r02 "1043" "80f3"
01:00.0 "0300" "10de" "0342" -ra1 "1462" "9480"
02:0a.0 "0200" "1317" "0985" -r11 "1317" "0574"
02:0d.0 "0401" "1102" "0002" -r08 "1102" "8064"
02:0d.1 "0980" "1102" "7002" -r08 "1102" "0020"

eth0      Link encap:Ethernet  HWaddr 00:0c:41:20:d4:51  
          inet6 addr: fe80::20c:41ff:fe20:d451/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:3 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5952 (5.9 KB)  TX bytes:5952 (5.9 KB)

---

### Post by zerhacke on 2009-08-17
That doesn't look like output from ifconfig.  That's uname -a.

---

### Post by gruurly on 2009-08-17
> **zerhacke said:**
> That doesn't look like output from ifconfig.  That's uname -a.

Ok, well then something seriously wonky is going on. Half the time the Terminal commands are telling me the command doesn't exist, and then when it magically does exist (exact same thing typed in each time), this is what it spit out for ifconfig.

Alrighty, tried again, this is what I got:

eth0      Link encap:Ethernet  HWaddr 00:0c:41:20:d4:51  
          inet6 addr: fe80::20c:41ff:fe20:d451/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:3 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5952 (5.9 KB)  TX bytes:5952 (5.9 KB)

---

### Post by gruurly on 2009-08-17
Data again, this time [SIZE=3]sudo lshw -c network[/SIZE]

*-network               
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth0
       version: 11
       serial: 00:0c:41:20:d4:51
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=64 maxlatency=128 mingnt=64 module=tulip multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: be:78:fa:b7:d6:7d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

