---
title: "Still no internet"
date: 2006-09-27
forum: Networking &amp; Wireless
---

### Post by muggins on 2006-09-27
I have an active wlan0. I can ping my router using IP 192.168.1.1
But cannot connect to internet. Have tried with & without wep. Wifi radar picks up my router with an excellent signal. Can not ping [www.google.com](www.google.com). Still haven't given up trying after 4 weeks of effort. Any suggestions?

---

### Post by encompass on 2006-09-27
can your other computers connect?  is the router setup correctly.  Can you ping and communicate with other computers on the network?

---

### Post by bigken on 2006-09-27
ok have you tried adding your dns to /etc/resolv.conf also in firefox 
type about:config then in the filter bar type ipv6 and change it to true from fales just double click it ;)

---

### Post by muggins on 2006-09-27
Thanks for responding encompass and bigken. Yes this computer can connect when I boot into windows and our main computer can connect also. Yes the router is set up correctly but I haven't tried to ping other computer. Where would I find the IP address for it? Also where do I find my dns to enter into etc/resolv.conf? I am assuming that this is a terminal command. Thanks so much for helping.

---

### Post by bigken on 2006-09-27
go to your isp web site and find your dns from there or your router interface will tell you the command is 

gksudo gedit /etc/resolv.conf

then you would add something like 

nameserver 195.92.195.95
nameserver 195.92.195.94

yours will differ from this

---

### Post by muggins on 2006-09-28
> **bigken said:**
> ok have you tried adding your dns to /etc/resolv.conf also in firefox 
type about:config then in the filter bar type ipv6 and change it to true from fales just double click it ;)

Where exactly in firefox do I type about:config?

---

### Post by bigken on 2006-09-28
> **muggins said:**
> Where exactly in firefox do I type about:config?

in the address bar ;)

---

### Post by Iowan on 2006-09-28
> **muggins said:**
>  Also where do I find my dns to enter into etc/resolv.conf? I am assuming that this is a terminal command. Thanks so much for helping.
If the Windows box is XP, you can Start>Run>"CMD" to get a terminal-type window.  From there type: **netsh interface ip show dns** to learn what DNS servers whe Windows box is using.

---

### Post by muggins on 2006-09-29
> **Iowan said:**
> If the Windows box is XP, you can Start>Run>"CMD" to get a terminal-type window.  From there type: **netsh interface ip show dns** to learn what DNS servers whe Windows box is using.
I did the command you recommended and I got my routers address 192.168.1.1

---

### Post by muggins on 2006-10-01
How should I be changing my network settings, with wifi radar or networking under system administration or command line? Does it matter? Still can't connect.

---

### Post by bigken on 2006-10-01
who is your broadband supplyer ?

---

### Post by muggins on 2006-10-01
My broadband supplier is telus.

---

### Post by muggins on 2006-10-02
In my router under the LAN & DHCP Server tab it shows my wireless with an IP address and a MAC address. This must mean something.

---

