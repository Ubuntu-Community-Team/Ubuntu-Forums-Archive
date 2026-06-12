---
title: "No internet access through ubuntu"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by Langley56 on 2009-12-13
I have Windows 7 and ubuntu 8.10 installed on my new computer.
I was able to access the internet through both OSs.
Now I am only able to access through Windows 7.
 
What do I do to reconfigure (?) ubuntu to get on the net with it?
 
Thank you.
Langley

---

### Post by JDShu on 2009-12-13
What happened in between your internet working and not working on Ubuntu?

---

### Post by Langley56 on 2009-12-13
I was on Windows 7 and it did some internet set up routine.
 
When I restarted and went back to ubuntu I suddenly had no connection
 
I can access the internet on the same computer in windows 7 though.

---

### Post by JDShu on 2009-12-13
Are you connected to the internet through an ethernet cable or wireless? If its through wireless, can you see any networks from ubuntu?

---

### Post by lidex on 2009-12-13
How do you access the internet? Are you using a router? Wireless?

---

### Post by The_Pirate_King on 2009-12-13
Copy the following commands into the terminal and tell me what the output is: 

```
lspci | grep -e Ethernet -e Wireless
```
```
ifconfig
```

---

### Post by Langley56 on 2009-12-13
I use cable and a router to connect to the internet.
 
All of my other computers connect fine.

---

### Post by Langley56 on 2009-12-13
> **The_Pirate_King said:**
> Copy the following commands into the terminal and tell me what the output is: 
 
```
lspci | grep -e Ethernet -e Wireless
```
```
ifconfig
```
 
 
Do you mean the Terminal Service Client?
 
Where would I copy it to??

---

### Post by The_Pirate_King on 2009-12-13
No, I mean Applications > Accessories > Terminal

---

### Post by lidex on 2009-12-13
> **Langley56 said:**
> Do you mean the Terminal Service Client?
 
Where would I copy it to??

No. Copy and paste the commands, one at a time into a terminal. Look in your applications menu "accessories>terminal"

---

### Post by Langley56 on 2009-12-13
> **JDShu said:**
> Are you connected to the internet through an ethernet cable or wireless? If its through wireless, can you see any networks from ubuntu?
 
I do not have wireless.
 
In Windows 7 from the computer I can see other computers.
 
In the Network - File Browser in ubuntu I can see something called Windows Network

---

### Post by Langley56 on 2009-12-13
> **The_Pirate_King said:**
> No, I mean Applications > Accessories > Terminal
 
 
I may have put in the first code wrong.
 
I got a message to try grep -- help
 
With the ifconfig I got lots of 0's packets sent.

---

### Post by The_Pirate_King on 2009-12-13
I meant copy and paste the actual output... it should help me diagnose your problem.

---

### Post by Langley56 on 2009-12-13
> **The_Pirate_King said:**
> I meant copy and paste the actual output... it should help me diagnose your problem.
 
I know but -  in ubuntu I do not have internet connection.
I can not send it.
 
If I copy it in ubuntu and switch to Windows 7 I will lose it.

---

### Post by lidex on 2009-12-13
Copy the data into a text file on a drive that windows can access.

---

### Post by Langley56 on 2009-12-14
> **lidex said:**
> Copy the data into a text file on a drive that windows can access.

Here it is.

Report bugs to <bug-grep@gnu.org>.

langley@langley-desktop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:26:18:9a:32:b5  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:23985514729 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:251 Base address:0x6000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:310 errors:0 dropped:0 overruns:0 frame:0

          TX packets:310 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:20148 (20.1 KB)  TX bytes:20148 (20.1 KB)



langley@langley-desktop:~$

---

### Post by Scunnered on 2009-12-14
**Langley56**

You don't say where you are.  In the UK I have to provide my password that is agreed with my ISP to access the network connection.

I had problems initially when the password was requested but would not take and found that if I re-started the system nothing happened.  Entering the password and shutting down the system and re-starting ensured the connection.

I would also ask is it necessary to use version 8.10 as my experience is that 9.10 offered me an immediate network connection out of the box.  You might find things easier by a fresh install of 9.10

---

