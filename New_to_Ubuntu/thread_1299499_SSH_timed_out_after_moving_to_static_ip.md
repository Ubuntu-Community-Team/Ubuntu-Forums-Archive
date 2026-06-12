---
title: "SSH timed out after moving to static ip"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by zacnotes on 2009-10-23
Thanks in advance for any help!
 
 laptop with 9.1 beta
 desktop with 8.04 lts server
 the server is going to be a media server, but i have run into a wall that didn't exist earlier.
 
 Earlier today, i had all my pc's assigned ip's by dchp. to keep my config files from having to be edited every time i have to restart, i moved my server to a static ip. Before going static, i could ssh into the server easy as pie. Now, i get a "connection timed out" error every time i try. netstat -tn on the laptop shows it trying (SYN_SENT) but $ cat /var/log/auth.log on the server shows no ssh  inbound

is there any info i could post that would help resolving my issue?

---

### Post by mr_steve on 2009-10-23
The output of ```
ifconfig
``` from both machines would probably be useful.

---

### Post by zacnotes on 2009-10-24
ifconfig-
laptop:
eth0      Link encap:Ethernet  HWaddr 00:12:3f:e3:31:42  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:0b:50:00  
          inet addr:10.20.1.107  Bcast:10.20.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fe0b:5000/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7068 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6352095 (6.3 MB)  TX bytes:1018842 (1.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-0B-50-00-30-62-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


server:
eth0       Link endcap:Ethernet   HWaddr 00:11:d8:ed:98:85
             inet addr:10.20.1.105   Bcast:10.20.1.255   Mask:255.255.255.0


(having to type that out by hand, i don't know a good way to get it pasted over here otherwise, any other relevant lines needed?)

---

### Post by mr_steve on 2009-10-24
Hmm, based on that, everything looks good, it occurs to me that I forgot to ask a couple important questions; 
1) are you trying to connect to the server by hostname, or by IP address?
2) can you ping the server from the workstation? can you ping the workstation from the server?

---

### Post by zacnotes on 2009-10-24
by ip. tried hostname early, but it never worked, so i stuck with ip address from then on. ping replies both ways.

---

### Post by mr_steve on 2009-10-24
Okay, a couple more questions then;
a) how are you configuring the static IP on the server? DHCP static assignment, NetworkManager, /etc/network/interfaces?
b) have you restarted the server since making the change?
c) do you have a firewall configured on the server?

The only thing I can think of at the moment is that either the SSH daemon is somehow still bound to the old IP, or that you have some kind of firewall issue. Or perhaps a duplicate IP address on the network?

---

### Post by zacnotes on 2009-10-24
1.ip assigned in /etc/network/interfaces,
2.i have restarted
3.if the server edition ships with a firewall then yes, but i believe i remember trying a "sudo ufw disable" at one point also.

---

### Post by zacnotes on 2009-10-24
took another look at the ufw, looks like that was my problem indeed. disabled and ssh'd in just fine

---

### Post by mr_steve on 2009-10-24
Glad you got it figured out, I was starting to feel like I was grasping at straws there. #-o

---

