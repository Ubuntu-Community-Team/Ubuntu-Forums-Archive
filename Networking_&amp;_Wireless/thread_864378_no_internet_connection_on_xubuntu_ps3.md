---
title: "no internet connection on xubuntu ps3"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by freest82 on 2008-07-19
I just installed xubuntu on ps3 and I dont have any internet connection. Using the command ifconfig on the terminal I get something like this:
(this is from linux mint on my pc, but the print out from the ps3 is about the same)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

I'm using an ethernet connection, so I should see something about eth0 but I don't. How do I add it.

---

### Post by freest82 on 2008-07-19
no one knows? I thought this was a pretty basic question.

---

### Post by SchindlerShadow on 2008-11-19
idk i have the same problom.... but in ubuntu 8.10 on ps3. :confused:

---

### Post by eckz59 on 2008-12-20
run 'lspci -vvnn' as root and post the output here...

in the mean time, I would try adding the following lines to your /etc/network/interfaces file (this assumes your router gives DHCP):

auto eth0
iface eth0 inet dhcp

---

