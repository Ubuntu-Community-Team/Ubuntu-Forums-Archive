---
title: "Internet Problems"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by J003S3PH on 2011-07-05
I just recently installed Ubuntu onto my laptop. 11.04 32bit
However, I cannot connect to the Internet. I can't connect wirelessly or with the Ethernet cable plugged in.
I have another computer connected so the same router that connects fine, I even tried plugging in the cable into different sockets, and tried using different chords, but none of that worked.

But, when I run my computer off of the USB and run Ubuntu off of the USB, the trial thing, I have Internet only with the Ethernet cable plugged in. I had wireless connections completely fine before I installed Ubuntu. 

And when I officailly install it, same thing happens, with no internet.

Also when I finish installing, I get a message saying that I don't have the right hardware. And its gonna use the traditional version.
But I do, I have 1 gb ram, 160 gb hard drive, nVidia GeForce Go 7300, 1.86 Ghz CPU, so im sure i have the right hardware.

Please Help!
Thanks, and sorry for all this bombardment of help

---

### Post by jtarin on 2011-07-05
Ok let's get wired internet running first. If your comfortable using the terminal and commandline it will make it a lot easier.First by cable then to router.....what internet service are you using DSL or other?

---

### Post by J003S3PH on 2011-07-05
Im using DSL

---

### Post by jtarin on 2011-07-05
In a terminal issue the command ```
ifconfig
``` and post the results.

---

### Post by J003S3PH on 2011-07-05
> **jtarin said:**
> In a terminal issue the command ```
ifconfig
``` and post the results.

Ok, so what happens after that?

---

### Post by jtarin on 2011-07-05
> **J003S3PH said:**
> Ok, so what happens after that?Well normally following instructions you would post it here as requested in my first post, but if we are dealing with an unusual situation where I need to repeat my instructions please let me know.

---

### Post by J003S3PH on 2011-07-05
> **jtarin said:**
> Well normally following instructions you would post it here as requested in my first post, but if we are dealing with an unusual situation where I need to repeat my instructions please let me know.

Sorry bout that

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:6c:d2:3e  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe6c:d23e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6891 (6.8 KB)  TX bytes:9192 (9.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1776 (1.7 KB)  TX bytes:1776 (1.7 KB)


Thats what i get

---

### Post by jtarin on 2011-07-05
Ok it looks as if you have a connection.....let's try the command ```
sudo pppoeconf 
``` once you have executed the command enter any information it ask. When completed the next command will be ```
sudo pon -dsl provider
```Once this command is executed if you have no errors open a browser and navigate to a site. If you have errors or questions post back.

---

### Post by J003S3PH on 2011-07-07
> **jtarin said:**
> Ok it looks as if you have a connection.....let's try the command ```
sudo pppoeconf 
``` once you have executed the command enter any information it ask. When completed the next command will be ```
sudo pon -dsl provider
```Once this command is executed if you have no errors open a browser and navigate to a site. If you have errors or questions post back.

Thank you, Its all fixed now

---

### Post by jtarin on 2011-07-07
Can you connect automatically at boot now?
If this is solved mark the thread as solved, please.:p

---

### Post by OldBoy44 on 2011-07-07
Hi j003S3PH,

Not meaning to butt in, but if solved suggest you may mark as Solved via thread tools, as suggested by jtarin,

Cheers, ;)

---

