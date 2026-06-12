---
title: "Configure ADSL MTNL Triband in Ubuntu 9.04"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by Krishnan on 2009-07-19
Hi, I have just installed Ubuntu 9.04 on my system. The problem is i don't know how to configure my internet as there are variety of options available there. I'm using UT300R2U Modem(T-KD-318-EUI). I am using windows os on the other side. I am using my net connection through Bridged Mode. How do i configure the same in ubuntu

---

### Post by Krishnan on 2009-07-20
Seems no one wants to answer my query:(

---

### Post by prshah on 2009-07-20
> **Krishnan said:**
> I am using my net connection through Bridged Mode. How do i configure the same in ubuntu

Open a terminal (Applications-Accessories-Terminal) and use ```
sudo ppoeconf
``` The questions are pretty much straight-forward, post back with outputs if you run into problems for specific answers.

---

### Post by Krishnan on 2009-07-20
I have tried that.Not working. But now i have set it up using the DSL option. But now can't access my modem page at all :( Any one help plz

---

### Post by zerhacke on 2009-07-20
What was in bridged mode, the Modem or the Win setup?

---

### Post by Krishnan on 2009-07-20
Modem is in the bridged mode. I'm using the same connection through windows xp in a bridged mode.

---

### Post by zerhacke on 2009-07-20
The easiest answer I can come up with is that you could unbridge your modem and use pppoe on both Windows and Linux.

---

### Post by Krishnan on 2009-07-20
But i want to use my internet in a bridged mode :( We do have a pppoe dialler in windows. Can that be done in ubuntu?

---

### Post by zerhacke on 2009-07-20
PPPoE is built into Windows.  Call your ISP and they'll walk you through it.

---

### Post by prshah on 2009-07-21
> **Krishnan said:**
> I have tried that.Not working. But now i have set it up using the DSL option. But now can't access my modem page at all :( 

If you can't access your modem page at all, then you have likely changed either your IP or your modem's IP. Open a terminal (Applications-Accessories-Terminal) and post back the result of ```
ifconfig
``` for further troubleshooting. I assume that you are connected through the Ethernet interface and not USB.

What exactly is the difficulty you faced with pppoeconfig?

---

### Post by Ashish Nag on 2010-02-07
Hi,

I have installed Ubuntu installed on my PC with Install from Windows Option. Internet is working fine on my PC through Windows however I am not able to connect to Internet through Ubuntu.

I tried
[COLOR="Red"]*sudo ppoeconf*[/COLOR]
but its not working.

It is giving the following Error message which says it Scanned fot the Interface but the Access Concentrator of my Provider did not respond.


I have used the following Settings:

[I]IP address: 192.168.1.2
Subnetmask : 255.255.255.0
Default Gateway: 192.168.1.1
Primary DNS server: 203.94.227.70
Alternate DNS server : 203.94.243.70[/I]

Please help.

---

