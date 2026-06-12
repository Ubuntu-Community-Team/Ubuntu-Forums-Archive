---
title: "Connect two pcs"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by ninicoco on 2008-01-19
how to connect two PCs using an LAN-LAN cable to transfer files sharing and printer. I'm using windows xp an ubuntu.

I connected with Ethernet cable from one directly to the other. 

That work with XP ---> XP no problem.

but with XP ---> ubuntu there is a problem. please help.

---

### Post by jeffus_il on 2008-01-19
You have to be more specific about the problem. Is the Linux machine visible from the windows one. Have you set up Samba on Linux (the Microsoft Networking protocol).

---

### Post by ninicoco on 2008-01-19
The network from windows xp doesn't work (status: Limited or no connectivity). I did not install anything yet.

---

### Post by zero-9376 on 2008-01-19
you will need to assign static ip addresses to both the windows and ubuntu machine

if you are just wanting to share files static ips are easy and there are gui methods for both ubuntu and windows.

---

### Post by perfecttao on 2008-01-19
Just to add to this...you should assign a static IP address on both machines.  The IP address should be in the same subnet - ie. 

Machine 1

IP 192.168.0.10
Subnet Mask 255.255.255.0

Machine 2

IP 192.168.0.11
subnet Mask 255.255.255.0

You can then test this setup by pinging the other machine:

In ubuntu, open a terminal and type


>ping 192.168.0.x 

(x being the last octet of the ip address)

In windows, go to start->run and type 

cmd

in the black box type 

>ping 192.168.0.x

If you get a response then the link between the 2 machines is ok.  If not (ie get destination host unreachable), then it is possible that you may need a crossover ethernet cable as it's possible that your network card drivers don't support auto-negotiation between MDI and MDI-X in Ubuntu.

P

---

