---
title: "Error while trying to scp files to my ubuntu 13.10"
date: 2014-07-09
forum: Networking &amp; Wireless
---

### Post by Suchetana on 2014-07-09
Dear all
I have Ubuntu 13.10 installed in my system. I can connect to other systems via ssh. However, when I am trying to copy files from those systems to mine via scp, I am getting the error:
ssh: connect to host 10.21.50.207 port 22: No route to host
lost connection
This is an issue with some computers only. When I am trying to do scp from other systems in my Institution, I am able to do them, albeit, I ahve to use rsync --append option everytime. 


My ifconfig output is as follows (if it helps):
eth0      Link encap:Ethernet  HWaddr 00:1d:09:7a:cc:ee  
          inet addr:10.21.48.83  Bcast:10.21.51.255  Mask:255.255.252.0
          inet6 addr: fe80::21d:9ff:fe7a:ccee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:242549 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104953 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:255829482 (255.8 MB)  TX bytes:15430478 (15.4 MB)
          Interrupt:20 Memory:fdfc0000-fdfe0000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6966 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6966 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1729901 (1.7 MB)  TX bytes:1729901 (1.7 MB)



I had also disabled firewall using the command: 
sudo ufw disable


I would be really grateful if someone can help me with a detailed instruction set. I am a newcomer to Linux, so detailed instructions are welcome.
Thanks a lot for your help and time, in advance.

---

### Post by slooksterpsv on 2014-07-10
Are they on the same Subnet/Network? The No Route seems like it's saying, hey I don't know where this computer is at (which is a literal translation of what it means), but I mean for the network you're on. Are the servers in a different section of campus vs your computer e.g.
Your's is in the dorm, the other is in Comp Lab 1 or what not?

---

### Post by Suchetana on 2014-07-10
Both the computers are in the same network.

---

### Post by slooksterpsv on 2014-07-10
Is one wired and the other wireless?

---

### Post by Suchetana on 2014-07-10
no, both are wired. 
earlier i could do scp from some machines to my system, now i cannot do scp from any machine, even though i can connect to all machines by ssh.

---

### Post by Suchetana on 2014-07-11
Hello all
I have found the error. It seems that my IP had changed and I wasn't aware of it. Hence, I could not connect. Now everything is working fine!
Thanks all for your efforts and time.
Have a good day

---

