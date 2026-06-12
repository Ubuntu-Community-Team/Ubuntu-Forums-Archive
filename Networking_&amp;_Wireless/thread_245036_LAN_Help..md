---
title: "LAN Help."
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by wtr_sprts4life on 2006-08-27
Hi. Ive had heaps of problems getting ubuntu to install, and i gave in, bought a new hdd, partitioned it so i have windows, and ubuntu, and my old one to store music etc. I have a wireless router (which is hardwired to my network card on this computer) and ubuntu recognises it, but when i open up modzilla firefox, it wont go to any pages. It recongnises my windows network. Any ideas on how to configure it? i can access the router by typing 192.168.1.1 in the address bar.

thanks. JB

---

### Post by steve.horsley on 2006-08-27
Can you post the output from the command 
**route -n**
and also post the contents of the file /etc/resolv.conf
and also the results of these two commands
[B]ping 82.211.81.186
ping [www.ubuntuforums.org](www.ubuntuforums.org)[/B]

---

### Post by wtr_sprts4life on 2006-08-27
Results for route -n are:

Destination  Gateway      Genmask:       Flags:  Metric:  Ref:
192.168.1.0  0.0.0.0      255.255.255.0  U       0        0
0.0.0.0      192.168.1.1  0.0.0.0        UG      0        0

Use:    Iface:
0       eth0
0       eth0

as for the file/etc/resolv.conf where do i find that? i tried typing it into terminal and all it said was ASC II Text. 

It wont let me ping either..thanks.

---

### Post by funchords on 2006-08-28
Your netstat -n output looks correct.

the command for resolv.conf is

cat /etc/resolv.conf

I have ideas (not in any particular order):

1.  Your wireless router may be filtering the packets.  You may have set up some security option that disallow all but a few MAC addresses from reaching the internet.  Turn off such filters and try again.

2.  Try these commands and try again:
sudo ifdown eth0
sudo ifup eth0

3.  You can bypass the router by connecting the Ethernet cable that is currently going into your router's WAN port directly into your computer's Ethernet port.  This will tell us whether the issue has anything to do with the router or involves something else.  Bypass the router and try again.

---

### Post by steve.horsley on 2006-08-28
The routing looks good. You have a default root pointing to the wireless router. If that's working, I would expect you to be able to ping things by address, even if not by name.

Can I assume that your wireless router is the thing that's connected to the internet? If not, what is?

To see the contents of /etc/resolv.conf, you can either go find it with nautilus and open it with Text editor, or use the command-line command **cat /etc/resolv.conf**

Won't let you ping is pretty vague. What does it say? No such file? Access denied?

---

