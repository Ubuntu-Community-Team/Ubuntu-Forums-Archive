---
title: "How to SFTP into Ubuntu Box from Outside LAN?"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by phiaward on 2008-05-12
I'm sorry if this question has been asked a million times before. I have set up sshd on my Ubuntu Hardy Heron box at home. I can sftp from my eeepc laptop to the Ubuntu box using the LAN ip, but I cannot connect via sftp using my WAN ip or DDNS name either from home or work. The network at my work is wide open - we have no IT department, lol. I'm not a complete idiot. I've set port forwarding on my router to forward the ssh port to my Ubuntu box. I've checked /etc/hosts.allow and /etc/hosts.deny and both are empty except for comments. I'm running firestarter but I have opened the ssh port to all traffic. I searched in my spare time for days but most of the problems I've seen have to do with routers, firewalls, or a setting in a hosts file. As far as I can tell, that is not my problem. Any help would be greatly appreciated.

---

### Post by breadlord on 2008-05-12
The first thing you need to do is run a traceroute from an external network so you can see how far it gets. The commands is available from the command line on *nix and windoze machines:

traceroute <<ip address>> // linux
tracert <<ip address>>    // windows.

It might well be that your employer blocks ssh traffic. Many do to external sites.

---

### Post by phiaward on 2008-05-12
Thanks. I'll give that a try and report back.

---

### Post by phiaward on 2008-05-12
Ok. I'm an idiot, lol. It seems that mp WAN ip changed overnight although I didn't reset the router and the power didn't go out. Also, for some reason or other, my DDNS service didn't update my IP. So, I was using the wrong ip. I looked up my current WAN IP, went next door and tried to sftp from the neighbor's and it worked first try.:guitar:

---

### Post by breadlord on 2008-05-12
You'll find that ISPS will shift you about for the hell of it... Rather than going for dynDNS, try asking them how much a static IP address will set you back.

---

