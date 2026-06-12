---
title: "Fresh install of Ubuntu receiving out of range IP addresses"
date: 2016-09-21
forum: Networking &amp; Wireless
---

### Post by mbrowell on 2016-09-21
I'm having trouble connecting my Ubuntu laptop to my local network. I have multiple windows computers as well as smartphones connected to the network, but any Linux computers that connect get a strange IP address. For example, the IP range in the router settings if from 192.168.1.100 - 192.168.1.199, but my laptop gets 192.168.1.207. Sometimes the IP addresses are below 100 as well. All the other settings DNS server addresses and everything are correct.

---

### Post by newbie-user on 2016-09-22
You may have a rogue dhcp server on your network.

---

### Post by coldraven on 2016-09-23
Any use?
[https://wiki.wireshark.org/DHCP](https://wiki.wireshark.org/DHCP)

---

### Post by mbrowell on 2016-09-23
For now, I've set a static IP, and without picking the Google DNS servers, which I did, I was still getting no love. This is a functional workaround, but I'd love to be able to either track down the rogue DHCP server or figure out what else could be causing this. Also, I downloaded Wireshark, but I don't know how to set it to get relevant info. Lastly, why is Linux more susceptible to this than Windows?

---

### Post by newbie-user on 2016-09-23
It's not that Linux is more or less susceptible. It's about which DHCP server responds to the client requests first.

What DHCP server are you using? Are you assigning IPs based on mac addresses? Do you have any other devices on the network that might have a DHCP server installed?

---

### Post by mbrowell on 2016-09-26
As far as I know, the only DHCP server on our network is the router. After the router, we have 3 switches and before the modem, a one port modem. The only thing I can think that's on the network that could even conceivably be hosting a DHCP server besides the router is my bosses server that he uses for his accounting program, and the only reason I think that is I've never touched the thing. I have no idea what's running on that server, but it's only set up to host an accounting program, so it's probably not running a DHCP server. Literally, the only other things on the network are our PXE based HW tester and a network HDD my boss uses to back up his computer.

---

### Post by newbie-user on 2016-09-27
If you can't get Wireshark to work, then you could log into the router and view the list of DHCP leases that it handed out. If your Linux boxes aren't listed, then there's definitely another DHCP server on the network. You mentioned a PXE-based tester. You need DHCP to start up PXE. Where are PXE network settings defined? On the router?

---

### Post by 1clue on 2016-09-27
Use wireshark on the linux box as mentioned. Then you'll know for sure what the dhcp server is.

A rogue dhcp server could be an accidental thing with somebody's laptop or it could be a deliberate phishing attack, either manual or malware.

If your switch has a monitoring port you might want to make use of that. In my opinion any unauthorized dhcp server is malware.

---

### Post by 1clue on 2016-09-27
filter on 'port 67 or port 68' as in that wireshark dhcp link above

---

