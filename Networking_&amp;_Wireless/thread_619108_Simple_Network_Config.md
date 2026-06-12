---
title: "Simple Network Config"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by aero2600 on 2007-11-21
I've just installed Ubuntu 7.10 for the first time, so please be patient with me.

I'm simply trying to connect to the internet with my DSL modem. It's Speakeasy OneLink ADSL. I talked to Speakeasy Customer Support before installing Ubuntu 7.10, and I sent them a list of things that the official Ubuntu documentation said I might need to know to configure my network connection. So I have all the information I need: IP, Gateway. DNS, etc.. all the way down to PCR, VPI, VCI, and even Encapsulation type. 

I installed Ubuntu, and it didn't configure the network by default. I was prepared for this. But when I use the network manager to setup a new connection, it doesn't connect. I've entered my IP, Subnet Mask, Gateway, Primary and Seconday DNS. I've saved the connection. I hit the check mark to use it as my current configuration. I've made sure that wired networking is enabled.

So what am I doing wrong at this point? I'd like to get away from using Windows, but this is my third or fourth attempt trying to switch to Linux. I've tried Slackware, Mandrake, Debian, Fedora. The system is dual boot, so I can keep using XP to post here and do my work.

Any help would be greatly appreciated.

Thanks, 
  Aero

---

### Post by 1/0 on 2007-11-21
How do you connect? PPTP or what?

---

### Post by aero2600 on 2007-11-21
I don't believe it's PPTP. From what I've found, PPTP is for VPN and L2TP, neither of which have I heard associated with my connection. If I had to guess, I'd say it's PPPoE, but I haven't been able to find a definite answer in Speakeasy's User Manual.

This connection didn't require any special configuration with Windows XP. To the best of my knowledge, it's a standard ADSL connection with a static IP address.

Aero

---

### Post by 1/0 on 2007-11-21
LoL, yeah I meant PPoE and not PPTP. Sorry. 

I've got a firewall now days so, its been a while since I set up anything but DHCP. Anyway, you need pppoeconf installed (I thought it was installed per default). Then just launch it and setup the connection, or maybe you already did that?

---

### Post by 1/0 on 2007-11-21
I just realized you said static IP which is not PPPoE. I'm not sure how Gnome does this so try these links:

[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html)
[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

They should help.

---

### Post by aero2600 on 2007-11-21
Your first link there is to the standard Ubuntu documentation, which was no help at all. It has you using the network-admin gui tool, and I'm not even sure that thing works.

I have questions about the second link. It starts off with this:

Desired new sample settings:
=> Host IP address 192.168.1.100
=> Netmask: 255.255.255.0
=> Network ID: 192.168.1.0
=> Broadcast IP: 192.168.1.255
=> Gateway/Router IP: 192.168.1.254
=> DNS Server: 192.168.1.254

What are Network ID and Broadcast IP? I've never seen these before, and weren't provided these by my ISP. I'm not sure this is for a standard static IP configuration. 192.168 is for internal networks, right? My static IP starts with 69.

Another question from the second link, about the resolv.conf file. It shows this:
search myisp.com
nameserver 192.168.1.254
nameserver 202.54.1.20
nameserver 202.54.1.30

The first line, 'search myisp.com'. What is that? 

I'm going to see what I can do with the second link, but I'm guessing that I will be back.

Thanks,
  Aero

---

### Post by aero2600 on 2007-11-21
I've managed to get it working. I think it was the 'search' line in the resolv.conf, which doesn't make any sense.

Thanks for your help.

Aero

---

