---
title: "comcast"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by shadowlands on 2009-04-18
I have comcast and I can not connect to the net. The wireless is not working nor is it working when i connect it with a Ecable.  Help please.

---

### Post by matrixblue on 2009-04-18
Which version of Ubuntu are you running?

---

### Post by jbrown96 on 2009-04-18
We really need a lot more info. Please post the output of the following lines. These commands are case sensitive

```
lspci | grep Network
```
```
iwlist scan
```
```
ifconfig && iwconfig
```

What is the name of your wireless network?

---

### Post by JK3mp on 2009-04-18
Yes get us the info from above and it should be a simple fix. i've heard of alot of people having problems with comcast whilst using linux and i have a friend whose one of there POS Tech Support team members... lol. But the fix's are usually simple.

---

### Post by xarquid on 2009-04-18
Yes, the above information will help us. It could be a router issue, or it could be a networking issue on your P.C.

Or it could actually be Comcast. This happens a lot to NEW customers (if you are a NEW install). You have to be in Windows to run the initial setup, which is ridiculous, *BUT* the alternative is to call them and ask them to provision your modem over the phone. So, that's good. 

If you do the latter (provision over the phone), just say you were told by the technician to do so or the "cd won't run." Because there's no need for fifty questions about Linux. And they won't ask. They have enough to worry about in their call queue. ;-)

---

### Post by shadowlands on 2009-04-19
how do I find out what version of ubuntu i am running?  Sometimes i can get internet and other times I can not get internet.
i typed in cat /ect/lab-release 

and it said no such file or directory

---

### Post by matrixblue on 2009-04-19
Run lsb_release -a from the terminal

---

### Post by shadowlands on 2009-04-19
> **matrixblue said:**
> Run lsb_release -a from the terminal

what part do I type in the terminal?

---

### Post by matrixblue on 2009-04-19
lsb_release -a

---

### Post by shadowlands on 2009-04-19
I typed in lsb_release 

and was told that "nO lsb MODULES ARE AVILABLE"

---

### Post by matrixblue on 2009-04-19
lsb_release **-a**

the -a is important

---

### Post by shadowlands on 2009-04-19
> **matrixblue said:**
> lsb_release -a

did it and got 
"lsb_release-a: command not found"

re entered it and got

ubuntu 8.10 
command name intrepid

---

### Post by matrixblue on 2009-04-19
there's a space between lsb_release and -a

---

### Post by shadowlands on 2009-04-19
> **matrixblue said:**
> there's a space between lsb_release and -a

got it 

ubuntu 8.10

codename: intrepid

---

### Post by matrixblue on 2009-04-19
Okay, we still need the info requested in ealier posts. Those guys seem to have experience with that particular ISP so they would be better able to assist you than me (I'm in The Bahamas).

---

### Post by shadowlands on 2009-04-19
> **matrixblue said:**
> Okay, we still need the info requested in ealier posts. Those guys seem to have experience with that particular ISP so they would be better able to assist you than me (I'm in The Bahamas).

Dang, not only are you smart you have great weather and the beach!!  Some folk have all the luck.  Thanks a ton and enjoy your day.

---

### Post by shadowlands on 2009-04-19
lspci | grep Network 

with this code what am i looking for?

---

### Post by shadowlands on 2009-04-19
iwlist scan

response 

lo  Interface doesn't support scanning

eth0 interface doesn't support scanning

wlan0 no scan results
pan0 interface doesn't support scanning

---

### Post by shadowlands on 2009-04-19
:~$ ifconfig && iwconfig 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1044 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1044 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:83360 (83.3 KB)  TX bytes:83360 (83.3 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 00:19:7e:a0:a2:e3   
          inet6 addr: fe80::219:7eff:fea0:a2e3/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:169 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:250 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:20660 (20.6 KB)  TX bytes:46413 (46.4 KB) 
          Interrupt:17 Memory:54100000-54110000  
 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11g  ESSID:off/any   
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated    
          Bit Rate:54 Mb/s    
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 
pan0      no wireless extensions.

---

### Post by shadowlands on 2009-04-19
help please!!!!!!!!!!!!!!!!!!!!!

---

### Post by shadowlands on 2009-04-19
I called comcast sorry bombcast and they reset the modem while I had the router unplugged and now i get internet from my wireless.

Is there anything I can do to keep my service working?

---

### Post by shadowlands on 2009-04-22
how do I show this has been solved.

---

### Post by matrixblue on 2009-04-22
Change the title to put SOLVED in front

---

