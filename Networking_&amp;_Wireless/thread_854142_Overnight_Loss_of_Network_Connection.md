---
title: "Overnight Loss of Network Connection"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by andrewbrown22 on 2008-07-09
Late last night I was able to connect to my "server" on my home network and stream a video file to my Xbox running XBMC.
This morning though, when I tried to VNC in to it, planning on looking for updates, I couldn't connect.  So I decided that I would restart it, hoping that would address whatever issue it was having.
But it didn't and I don't know what I should check to troubleshoot the problem. 
I have conky running on the desktop, and it is showing that I'm getting about 0.25kiB/s Down constantly, but I have no connection to the Local Network or the WAN.

What should I check first?

---

### Post by andrewbrown22 on 2008-07-09
Any ideas? I'm at a loss here, I have no idea what to check.  I didn't even do any updates from the time that I watched the video through this morning.

---

### Post by andrewbrown22 on 2008-07-09
Another bump.
Any networking gurus out there?

---

### Post by superprash2003 on 2008-07-09
is your server getting an ip?? in the server's terminal type ifconfig and post output

---

### Post by andrewbrown22 on 2008-07-09
Yeah, it's a Static IP of 192.168.1.5
I just turned it back on again, and now it is saying that
 "No network devices have been found."

---

### Post by andrewbrown22 on 2008-07-09
So I guess I'm wondering how this device got removed mysteriously overnight and how I can make it realize it is still there..

---

### Post by andrewbrown22 on 2008-07-09
After disabling the port in the BIOS and booting into the OS and then rebooting with the device enabled, Ubuntu actually recognizes that I have a network card. Here is the output of ifconfig:
```

andrew@server:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:11:3e:94:b3  
          inet6 addr: fe80::211:11ff:fe3e:94b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16256 (15.8 KB)  TX bytes:176 (176.0 B)
          Interrupt:16 

eth0:avahi Link encap:Ethernet  HWaddr 00:11:11:3e:94:b3  
          inet addr:169.254.6.189  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1987 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1987 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100072 (97.7 KB)  TX bytes:100072 (97.7 KB)


```

---

### Post by superprash2003 on 2008-07-10
hmm.. ok now set static ip (192.168.1.5)again to eth0

---

### Post by andrewbrown22 on 2008-07-10
> **superprash2003 said:**
> hmm.. ok now set static ip (192.168.1.5)again to eth0

Ok, I went in to the network settings and set it back to a static IP and it shows that I have that IP address now, but I still have no connection to the internet or other computers on the network.

---

### Post by andrewbrown22 on 2008-07-10
[SOLVED]

Well, I'll be damned. Turns out I had a bad switch on my network that caused it to go down. As for Ubuntu saying no device found, I don't know, but it is working now.

---

