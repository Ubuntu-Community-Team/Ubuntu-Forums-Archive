---
title: "Netgear wndr4300v3 and telnet"
date: 2014-04-23
forum: Networking &amp; Wireless
---

### Post by fritz5 on 2014-04-23
So I've been driving myself insane trying to telnet in to my netgear router to use the CLI. Does anybody know how to do this? 
I've gotten this far: I establish a telnet connection on port 23, which is not rejected. Then it just gives me a blank line no matter the commands I type. I thought it was supposed to give me a # so I knew I was in the CLI. Is this a security feature? Do I need static IP's? Or do i need to send all my commands through port 23? Or do I need a virtual emulator (if that's a thing)? telnet enable isn't helping either. 
Any help is appreciated, thanks!

fritz@fritz-HP-ENVY-TouchSmart-Sleekbook-4:~/Downloads/telnetenable$ telnet 192.168.1.1
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.

---

