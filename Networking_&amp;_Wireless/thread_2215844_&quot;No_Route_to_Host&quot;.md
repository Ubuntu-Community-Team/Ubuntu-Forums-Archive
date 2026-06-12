---
title: "&quot;No Route to Host&quot;"
date: 2014-04-08
forum: Networking &amp; Wireless
---

### Post by Benjamin_Smith on 2014-04-08
Hello all, I'm new to Linux and to the forums, but not new to computers and networking.  I switched when I had to reformat my Windows computer and couldn't afford to purchase another license.  Anyhow onto my problem, but first and overview of my intention

I've got Ubuntu 13.10 on my desktop with a wireless card (no ethernet access...wife won't let me run cables in the house) and I'm trying to connect to it via SSH from my phone (Android Jellybean using JuiceSSH) and my laptop (Windows 7 using PuTTy) for access to the CLI on my desktop.  I also have Pure-FTPd installed on my desktop for file sharing between my systems. My connections are hit and miss, and the only thing that usually temporairily fixes it is walking over and doing a manual restart on my machine.  I cannot do this EVERY time I want to connect, it impractical. 

I get period of time where I can sucessfully connect via both FTP and SSH to my desktop from all machine on my LAN, but more often than that I cannot connect to them over the LAN and get a "No route to host" error.  I cannot ping my Ubuntu machine from ANY node in my network, it says "Destination Host unreachable." However, if I attempt to connect to either service via WAN on my phone (either using work's network or my cell carrier's network) I can do so without limit or problem.  I've tried disabling UFW, tried adding rules to allow SSH and FTP connections (port 22 and 21 respectively) for WAN, tried adding the entire scope my home network ID of 192.168.10.0 to allow incoming connections and most recently even tried flushing iptables but none of this does any good.  To me this seems odd, I can connect to the system over the internet but not from my nodes within the LAN which rules out the possiblity of my router's firewall being the problem. Any help?

---

### Post by apohal9 on 2014-04-08
Hi,

could you provide more information about the network setup of you LAN where all those hosts resist on? This may help to understand your environment.

---

### Post by Benjamin_Smith on 2014-04-08
They are all connected wirelessly to my network.  My phone is a Galaxy S4 running 802.11n, my laptop is a Toshiba running 802.11g, my Ubuntu Desktop is connected via the Gigabyte WPGS01 802.11g adapter and the wireless AP is my comcast residential gateway.  No nodes (to include my Ubuntu machine, my laptop and phone...as well as my wife's laptop and phone which are not included in the need for access) have any problems pinging any others or accessing the LAN or Internet.  I can also ping OUT from my Unbuntu but cannot accept pings as they are unreachable.

As I mentioned, I get intermittent access to my Ubuntu desktop. some times it works just fine, other times it says no route to host but it never loses network connectivity or internet access.

I feel I've bounced around your question but I was quite confused myself haha

---

### Post by steeldriver on 2014-04-08
Given that it's intermittent and it's wireless, I would be grepping the desktop machine's dmesg log for disassociate / deauthenticate messages

```
dmesg | grep 'disassoc\|deauth'
```

What wireless card / chipset is it running?

```
lspci -nnv | grep '\[02.0\]'
```

---

### Post by Benjamin_Smith on 2014-04-08
when i copy/paste the dmesg code, nothing appears. 

Here is the code result:

```
bsmith@Desktop-PC:~$ dmesg | grep 'disassoc\|deauth'
bsmith@Desktop-PC:~$ lspci -nnv | grep '\[02.0\]'
00:12.0 Ethernet controller [0200]: ULi Electronics Inc. ULi 1689,1573 integrated ethernet. [10b9:5263] (rev 60)
05:0c.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
```


The driver for the wireless card was autodetected when I first installed Ubuntu

---

### Post by SeijiSensei on 2014-04-09
Can you connect the machine with an Ethernet cable for testing and see if the problem persists?

---

### Post by apohal9 on 2014-04-09
@Benjamin: I meant if you could provide some kind of IP addressing used in your network. The IPs and routes of the configured on the laptop and on the Desktop system.
Did you try to connect your Desktop via wired connection to the router and see if the behavior does change?

---

### Post by Benjamin_Smith on 2014-04-09
All nodes on the network are DHCP assigned on a 192.168.10.0/24 scheme...router is 192.168.10.1.  My desktop (....10.5) is a RESERVED ip within my router. I don't have a cable long enough to run from one room to the next.  I'd have to physically move my router, and i cannot leave it that way for any length of time for testing. Since this is an intermittent issue, it could temporarily fix it, but then it could revert back. If I did leave it to test it over a day my whole network would be without internet and house without phone. The only LIVE  cable jacks in my home are in my living room where it currently sits,  and my master bedroom.   For example, when i say it's intermittent...it was working JUST FINE last night, then this morning I cannot get it to connect.  A new problem persists though which was my first sign...when I connect to the internet it's FINE. Can load webpages etc, but soon as I tried to connect my desktop to my wireless printer to print a document it couldn't connect.  I then attempted to ping from my phone and my computer and got "Destination Host Unreachable."

---

### Post by apohal9 on 2014-04-10
From what you describe it really figures out to be the wireless connection that is your issue. But the only way be sure is to try it with a cable. 
What you could do, is to check logs in /var/log/ for errors being noted when happens what you described last. Is there some kind of wifi-security-feature on the wireless router that blocks inter-client-communication?!

---

### Post by Benjamin_Smith on 2014-04-15
I wonder if my old a** wireless card is the issue. As far as I can tell there is no feature to block inter - client connection on my router. Plus when I had windows on there it worked just fine. I guess is possible to have a feature like that...It is a Comcast gateway afterall,  but I cannot find it in any advanced setting on the GUI.  I might try going back to my Trendnet router and configure my Comcast gateway as a bridge. It's just annoying and I can't figure it out. 

The only thing that points away from my card being the issue is the fact I can access it just fine from outside the LAN.

---

