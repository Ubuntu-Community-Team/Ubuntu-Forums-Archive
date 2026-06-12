---
title: "Ubuntu on VMWare 6 - shared network problem"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by ronshani on 2008-02-25
Hi

I installed Ubuntu 7.10 on my Vista machine as a virtual machine using VMWare 6.

I set the network on this VM to be NAT, meaning sharing the network with my Vista host. I did this with other virtual machines and this is working usually.

But with Ubuntu Virtual machine, I can not figure how to configure Ubuntu network settings to get working on my shared network.

What am i doing wrong?

Ron Shani

---

### Post by superprash2003 on 2008-02-25
are you using DHCP??does your modem/router give ip's to your computer or do you type in the ip manually??
 try this.. go to system-administration-network ... type in the password.. select the wired or wireless connection(depending on your setup) and click on properties.. if you use DHCP  then select "Automatic Configuration(DHCP) " else select "static ip address" and type in the ip address manually..

---

### Post by ronshani on 2008-02-25
The host computer (Vista) is connected to the Internet using static IP, DNS and Proxy server. Host connection to Internet is perfect.

The virtual machine (where I installed Ubuntu) is set to used NAT, to my understanding this means that Ubuntu will see the host connection to the internet as if it was its own connection.

I tried everything in Ubuntu, from static ip address and configuration (same as the host computer), tried DHCP. No network...

I can also tell you that when I set proxy server in Firefox (same proxy as my host computer proxy) - I get from firefox a message that proxy server refuses connections.

---

### Post by ronshani on 2008-02-26
PROBLEM SOLVED - not completely, but I know the problem.

I tried the same configuration at home. Host is Vista Ultimate. Running VMware with client Ubuntu. Network is set to NAT. Installed Ubuntu and all is ok, including Internet and Mail. Great system.

The problem I described is at work, it seems that the Host proxy server is blocking Internet connection of Ubuntu.

Ron Shani

---

