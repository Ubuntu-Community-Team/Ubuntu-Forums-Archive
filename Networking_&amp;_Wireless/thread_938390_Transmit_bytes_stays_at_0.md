---
title: "Transmit bytes stays at 0"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by RoyalPro on 2008-10-04
I have an Asus P5Q SE with the on board Atheros network.  I installed the drivers from the Asus website and I am able to use it fine but it does not keep track of the TX bytes.  I have looked at both ifconfig and system monitor and they say at zero.

Also is there a way to get jumbo frames working?  I have tried to change the MTU, but all above 1500 fail.

---

### Post by n5pwpMike on 2008-12-21
Did you ever get a reply to this? I have been searching for a solution to this problem also. I'm running eeebuntu on an Asus 701. In Gnome System Monitor the Network History shows no activity on send. I loaded GKrellM thinking it was just something with System Monitor and no transmit activity there either. I do receive and transmit because I'm able to move around on the internet but something is not monitoring the activity. I also noticed that when I do "ifconfig -a" I get 

eth0      Link encap:Ethernet  HWaddr xxxxxxxxxxxx  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: xxxxxxxxxxxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:272733 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179345 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:176132510 (167.9 MB)  TX bytes:0 (0.0 B)
          Memory:fbfc0000-fc000000 

Yet lo shows

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7060 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7060 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:309278 (302.0 KB)  TX bytes:309278 (302.0 KB)

There are 0 bytes transmitted in eth0 which is what I should be running on for a wired net connection. Why would the loopback show the transmit activity and eth0 doesn't? Although they both (t/r) look to be the same value. It's very puzzling to me.

Thanks for any enlightenment you can shed. Though it looks like we're both in the same boat here. 

Mike

---

