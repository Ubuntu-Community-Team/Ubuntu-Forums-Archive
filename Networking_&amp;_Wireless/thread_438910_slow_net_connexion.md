---
title: "slow net connexion"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by avikguru on 2007-05-10
I have just installed Ubuntu 7.04. Every thing is running fine except internet. Net speed is very much slow compared to my MS Windows Distro. Where as windows is giving 60 KBps, Linux speed is just funny.(nearly 1000 Bps, Highest speed I got is 11.5 KBps) . Earlier I had Ubuntu 6.04 installed and net speed was fine there. It is still good in Windows.

Please Help me in this context. What is taking up the band width. Any help is very much appreciated..

---

### Post by Kobalt on 2007-05-10
How do you connect to the internet : modem type, what type of connection, how did you set it up under Ubuntu, etc. ?
Can you additionally post the output of the *ifconfig* command line please.

---

### Post by avikguru on 2007-05-10
I use Static IP through wired connexion. I just give my IP, DNS, and made the host to be 'localhost'. This much was fine to get the net connexion. I will give the out put of ifconfig just when i will log on to ubuntu. Annoyed from sloww connexion, I am now using another Comp.
thanx for help.

---

### Post by avikguru on 2007-05-10
Here is my ifconfig output:


avik@localhost:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:19:D1:37:21:1E  

          inet addr:172.16.11.17  Bcast:172.16.255.255  Mask:255.255.0.0

          inet6 addr: fe80::219:d1ff:fe37:211e/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          **RX packets:297 errors:157** dropped:0 overruns:0 frame:157

          TX packets:285 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:245186 (239.4 KiB)  TX bytes:31596 (30.8 KiB)



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Thanx for any help... cheeeeeeeeers

---

