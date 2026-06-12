---
title: "How should I configure a Linux machine to share internet connection with a W10 machin"
date: 2020-02-23
forum: Networking &amp; Wireless
---

### Post by spupazza on 2020-02-23
Hi, I'm trying to set up my malware lab.
I have 2 laptops: on one I have installed Ubuntu, on the other one I have installed Windows 10.
Both laptops have 1 ethernet port/NIC and one wireless interface.
 
I have also 1 physical network line to dedicate to this setup, with only one ethernet port. The idea I'm trying to implement is that the Linux machines will receive the internet connection through ethernet, and I want to share this connection with the Windows 10 machine 'somehow'. 
Also, I'll use a software -INETSIM, installed on the Linux machine- which will simulate a virtual network.
 
If I set up a hotspot with a DHCP, INETSIM won't work as it needs a static IP.
If I set up the hotspot with a static IP, then the ethernet connection on the Linux machine won't work.
 
Can anybody suggest what route would be best in order to achieve my goal?
Summarizing: I need to make a Windows 10 laptop receive the internet connection from a Linux machine through wireless using a static IP address.

---

### Post by him610 on 2020-02-23
> I'm trying to set up my malware lab.
What is purpose of malware lab?

---

### Post by spupazza on 2020-02-24
to run static and dynamic malware analysis. why?

---

### Post by kurt18947 on 2020-02-26
I'm no expert in this stuff but would a router with DHCP disabled do what you want?

---

### Post by him610 on 2020-02-26
> **spupazza said:**
> to run static and dynamic malware analysis. why?
Have you read this?
[https://ubuntuforums.org/misc.php?do=showrules]("https://ubuntuforums.org/misc.php?do=showrules")

---

### Post by rsteinmetz70112 on 2020-02-27
You don't say what you 1 Ethernet port Internet access is. If it is a a modem of some kind they can usually do dhcp and share connections.

The simplest solution is a cheap router. You can get a router for under $10.00.

You can also do a wired connection to the Linux laptop and set it up as a router. You don't say which version of Ubuntu you installed and the router set up would be different depending on that.

---

