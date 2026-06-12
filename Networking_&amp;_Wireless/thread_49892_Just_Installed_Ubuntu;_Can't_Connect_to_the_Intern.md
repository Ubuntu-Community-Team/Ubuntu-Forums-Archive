---
title: "Just Installed Ubuntu; Can't Connect to the Internet"
date: 2005-07-18
forum: Networking &amp; Wireless
---

### Post by acphenom on 2005-07-18
Okay, i installed Ubuntu 5.04 on my laptop; no problems. First thing i want to do is go on the internet and see what i can do with it. I thought it'd be like Windows and i could connect to the internet automatically, like that. Unfortunately, it seemed that i had to configure the connection myself. So i copied the information of my connection from my desktop PC, but it still didn't work. It shows up as Eth0, and it is active...only that in Firefox, 'www.google.com cannot be found'. I don't understand it at all. The Ethernet device shows up in Device Manager.
 
I'm using a 1Mbps NTL Cable Broadband Modem, with a 100Mbps Ethernet cable.
 
Can anyone tell me what i'm doing wrong? :?

---

### Post by dataw0lf on 2005-07-18
1) Check dmesg for any suspicious messages about your interface
2) Try pinging your gateway / router
3) Insure that you have no firewall rules in place (iptables -L)
4) Try pinging ips instead of hostnames (tell me if you get a response to : ping 66.219.227.114)


Here's the resolution to each problem 
1) You'll have to google for any problems that show up in dmesg;  they're varied and I can't possibly list all the solutions for each specific problem 
2) If you can't ping your gateway, it's probably firewall rules, and/or you have the ip to your gateway incorrect
3) iptables -F (flush the iptables) you'll have to find which script is running it upon boot, as well.
4) Change your nameservers (resolv.conf)

---

### Post by acphenom on 2005-07-18
[QUOTE=dataw0lf]1) Check dmesg for any suspicious messages about your interface
2) Try pinging your gateway / router
3) Insure that you have no firewall rules in place (iptables -L)
4) Try pinging ips instead of hostnames (tell me if you get a response to : ping 66.219.227.114)


Here's the resolution to each problem 
1) You'll have to google for any problems that show up in dmesg;  they're varied and I can't possibly list all the solutions for each specific problem 
2) If you can't ping your gateway, it's probably firewall rules, and/or you have the ip to your gateway incorrect
3) iptables -F (flush the iptables) you'll have to find which script is running it upon boot, as well.
4) Change your nameservers (resolv.conf)[/QUOTE]
 Well, it turns out that all i had to do was change 'Static IP Address' to 'DHCP' in Network Settings.

Sorry for wasting your time, dataw0lf, and thanks anyway. :D

---

### Post by excelsior on 2005-07-18
maybe your time won't be wasted after all

I have the exact same problem, except when i ping I get "network is unreachable"

My network settings are already set to DHCP

the funny thing is, my internet connection used to work perfectly, it just suddenly stopped

so what am i supposed to do with resolve.conf?

---

### Post by excelsior on 2005-07-19
I tried reinstalling ubuntu, but the installation can't configure the conncection. My modem works fine for windows on my PC

---

