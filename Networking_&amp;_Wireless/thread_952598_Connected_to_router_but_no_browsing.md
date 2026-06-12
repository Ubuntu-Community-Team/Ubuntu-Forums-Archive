---
title: "Connected to router but no browsing"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by faisal892 on 2008-10-19
Hi all,

I just upgraded from Ubuntu 8.04 to Ubuntu 8.1. Problem is that my internet was working fine before I upgraded but after upgraded to Ubuntu8.1 I can not browse internet though my laptop is connected through wireless to router. The same is the case when I connected my laptop through wire to router. It shows me as connected but no browsing.

Please if any body could help.

Faisal.

---

### Post by sethvath on 2008-10-19
Same issue described here: [http://ubuntuforums.org/showthread.php?t=952549](http://ubuntuforums.org/showthread.php?t=952549)

Downgrade to a previous kernel version from the grub boot screen and try whether wireless works. Press ESC during boot up and pick another kernel such as 2.6.24.21

---

### Post by superprash2003 on 2008-10-19
please post output of the following commands from the terminal
1)ifconfig
2)ping 192.168.1.1

 presuming 192.168.1.1 is the ip of your router..

---

### Post by faisal892 on 2008-10-19
Dear sethvath & superprash2003,

I Pressed the Esc key at boot up time and it gave the message

Error 15: could not find the file

Press any key to continue ...

Output of ipconfig and ping are 

faisal@faisal-laptop:~$ ipconfig
bash: ipconfig: command not found
faisal@faisal-laptop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted              
ping: sendmsg: Operation not permitted              
ping: sendmsg: Operation not permitted              
ping: sendmsg: Operation not permitted              
ping: sendmsg: Operation not permitted              
ping: sendmsg: Operation not permitted   

Please if you could help.

Regards

Faisal.

---

### Post by sethvath on 2008-10-19
Was there an option to hit ESC to enter setup options when you boot up? 

ipconfig works on windows, for linux its "ifconfig"

---

### Post by faisal892 on 2008-10-19
There was no Esc option.

just kernal name and then on the second line kernal name and in brackets "Recovery mode"

Regards

Faisal

---

### Post by faisal892 on 2008-10-19
Here is output of ifconfig


faisal@faisal-laptop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1b:38:91:87:6a  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:16 Base address:0x1000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:246 errors:0 dropped:0 overruns:0 frame:0

          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:15416 (15.4 KB)  TX bytes:15416 (15.4 KB)



wlan1     Link encap:Ethernet  HWaddr 00:1a:73:c3:c2:da  

          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0

          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1

          RX packets:9 errors:0 dropped:0 overruns:0 frame:0

          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:2088 (2.0 KB)  TX bytes:2018 (2.0 KB)



wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-C3-C2-DA-00-00-00-00-00-00-00-00-00-00  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



faisal@faisal-laptop:~$

---

### Post by faisal892 on 2008-10-22
Please if any body could help because I am in frustration without access to internet in Ubuntu. Life without internet is useless.

In case there is no solution to this problem then plz let me know  so that I may not be waiting in frustration and may switch to other distribution.

Faisal.

---

