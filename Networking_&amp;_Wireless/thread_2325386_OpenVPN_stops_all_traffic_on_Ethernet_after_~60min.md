---
title: "OpenVPN stops all traffic on Ethernet after ~60minutes"
date: 2016-05-21
forum: Networking &amp; Wireless
---

### Post by fujipurple on 2016-05-21
Good morning, I'm hoping someone can help me with solving a very frustrating issue.

After having my internet connection snooped on more than one occasion, I have started using a VPN to encrypt my traffic. However, after approx 60 minutes, all my traffic will stop abruptly. I have spent the last 5 hours trawling the internet to find a solution but nil joy.

My setup is as follows:
Ubuntu 16.04 LTS
ASRock mini-itx motherboard with Ethernet built in
Linksys wrt1900ac
The computer is connected to the router via a 1gigabit cable.

I have installed the OpenVPN packages and are managing my settings via the gnome network manager.

The VPN connects fine and will work as per normal (including an IP check) until approx 60 minutes, then all traffic stops. The only way to get traffic working again is to either disconnect the VPN (not desirable) or restart the machine (where my frustration lies as I am in the middle of working).

Self fix #1 - Initial searches indicated it might have been a DNS issue from my ISP, that it was blocking access because I was using a VPN. I changed my DNS to the DNS.watch no logging servers on both the network connection and VPN, rebooted, but this did not fix the issue.

Self fix #2 - Another search indicated it may have been a firewall issue, so I ran the remove command for both firestarter and ufw, rebooted, but this did not fix the issue either.

Self fix #3 - I tried the option "apply to traffic on this network only" but that results in everything bypassing the VPN.

I can't see how it's the VPN though, as I tested it on my Android phone and it does not drop out or stall at all. I can't see it being the router either as all my other devices are working fine.

The only skerrick of an idea of where to head next is the IP tables, but I would have no idea where to start, and I'm at my wit's end already.

Advice please? Thanks in advance.

---

### Post by Doug S on 2016-05-22
Hi and welcome to ubuntu forums.

> **fujipurple said:**
> The only skerrick of an idea of where to head next is the IP tables, but I would have no idea where to start, and I'm at my wit's end already.please provide the output for "sudo iptables -v -x -n -L"

---

### Post by fujipurple on 2016-05-27
Apologies for the delay in my response.

The output for "sudo iptables -v -x -n -L" as follows:
> Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination

---

### Post by fujipurple on 2016-05-28
After disconnecting the VPN when the traffic stops, the output is:

> Chain INPUT (policy ACCEPT 491 packets, 104236 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 534 packets, 175745 bytes)
    pkts      bytes target     prot opt in     out     source               destination 

---

### Post by fujipurple on 2016-06-08
Hi, I'm still having this problem, can someone please advise?

---

