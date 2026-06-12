---
title: "How do I get my internet working?"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by CCCody on 2008-12-30
My modem is on and all the lights are lighting up.

My internet does not work and I'm currently typing this from a different computer.

I don't know what to do and I'm trying to make this transition as painless as possible.. Please help.

---

### Post by pytheas22 on 2008-12-30
Please open up a terminal on Ubuntu from the Applications>Accessories menu, run the following commands and post the output here:
```

lspci -nn
lsusb
uname -rm
lshw -C Network
```

You can copy and past the output of those commands into a text file (Applications>Accessories>Text Editor), then transfer the file to another computer in order to post it here.

Also, are you trying to connect wirelessly or via ethernet?

---

### Post by CCCody on 2008-12-30
All the modem lights are on. My wireless works fine. I don't know what I'm doing.

This is what I get when I type in ifconfig:

> eth0      Link encap:Ethernet  HWaddr 00:1d:09:54:43:1d  
          inet addr:76.210.36.211  Bcast:76.210.255.255  Mask:255.255.0.0
          inet6 addr: fe80::21d:9ff:fe54:431d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:139785 (139.7 KB)  TX bytes:27556 (27.5 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:16:44:c6:80:4d  
          inet6 addr: fe80::216:44ff:fec6:804d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:1
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:218 errors:0 dropped:0 overruns:0 frame:0
          TX packets:218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13572 (13.5 KB)  TX bytes:13572 (13.5 KB)

---

### Post by overdrank on 2008-12-30
Please do not create duplicate threads on the same issue. Threads merged :)

---

### Post by cdtech on 2008-12-30
What type of modem are you trying to connect?

---

### Post by -=-+ w1r1zu +-=- on 2008-12-30
Is your ISP requiring you to dial before you connect to the internet?

---

### Post by overdrank on 2008-12-31
Thread closed [Duplicate here]("http://ubuntuforums.org/showthread.php?t=1026445&page=2")

---

