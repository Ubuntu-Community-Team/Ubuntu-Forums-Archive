---
title: "Port forwarding problems with 80 and 22"
date: 2014-10-24
forum: Networking &amp; Wireless
---

### Post by vincent.mcgreevy on 2014-10-24
I just moved into my new place with Comcast and trying to forward ports 22 and 80 to my Ubuntu machine.

The local machine IP is 10.0.0.217, I can load webpages and create a SSH connection locally with no problems.

Externally I cannot access my web server or my SSH, but when I check the ports on canyouseeme.org it says that both 22 and 80 are open.

I'm trying to create a SSH connection on a Windows machine with Putty. If anyone is familiar with the program, its pretty simple you put the host ip and port in, then it asks you for your Username and Password, again this works fine locally but when I try to use my external IP it cannot create a connection. 

But what is confusing me the most is this... If I SSH into my MediaTemple hosting account through Putty in Windows, and run this:

telnet XX.XXX.XXX.X 22

The home Ubuntu server responds with "SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.4" which tells me the port forwarding is set up fine. Also when I am connected into my MediaTemple account and run this command:

SSH [email]user@XX.XXX.XXX.XX[/email]

It prompts me for my password and hey I'm into my home server. So really it is looking like I can't connect into my home server at home through my external IP address, although its looking like everything may work externally?

---

### Post by slickymaster on 2014-10-24
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by weatherman2 on 2014-10-24
Many home routers don't do "loopback."  That is, they can't allow you to access your external IP from inside the network.

Other routers certainly can do loopback.  I use a TomatoUSB router/firewall behind my Comcast modem, which I use in (in effect) bridge mode - that is, I don't use the modem's DHCP server.  I have a router connected to it instead, and that does the DHCP/firewall for my entire network.  You should be able to disable the NAT firewall in your Comcast modem to allow that.

Anyway, with my TomatoUSB router doing the loopback, I'm happily able to access my home server from inside my local network.

TomatoUSB is an open source firmware (similar to DD-WRT) - like putting Linux on your router. You can't put it on your Comcast modem, but you can do what I did - get a compatible router and use that instead.  TomatoUSB (and DD-WRT) also have cool features like OpenVPN servers built in as well.

FYI, Comcast home (consumer) may not block port 80, but they block port 25, so don't plan on running an SMTP (mail) server with such a connection.  Also, if you don't have static IP on your Comcast connection, you may want to get a DDNS domain (another feature built into TomatoUSB and DD-WRT).

---

