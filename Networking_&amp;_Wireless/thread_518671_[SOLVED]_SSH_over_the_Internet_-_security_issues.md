---
title: "[SOLVED] SSH over the Internet - security issues"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by petit.padavoine on 2007-08-06
I have a laptop with Ubuntu Feisty and openssh-server installed.

It's connected to the net through a router and has a private IP address (192.168.*.*).

My router is set up to redirect port 2222 of my public IP address on the Internet to port 22 of my laptop's private IP address.

1. Will this enable me to ssh to my laptop from wherever I am using ```
ssh -p 2222 user@publicipaddress
```?
2. Does this pose a security threat?

---

### Post by petit.padavoine on 2007-08-06
Well I can answer my own question number 1...

I tried ssh -p 2222 mypublicipaddress from another computer and it just hanged...

Is there anything I should know to get it to work?

---

### Post by eentonig on 2007-08-06
1. It should work. Try first if you can connect locally on port 22. Then do a regular portforwarding on port 22 on your router. And then do portforwarding/translation form 2222 to 22. (alternatively, you could also instruct your ssh server to listen to port 2222 and just do regular portforwarding on your router)

2. Everytime you open a port to the internet, there is a security risk. But, due to the fact that you use a none standard port, it's limited. 
- Another methode, and the one I use, is to configure iptables to only allow ssh traffic from the networks your expecting to use ssh from. (99% of the time, I know there are only 2 public ranges where I'll be using to connect to home)
- alternatively/additionally: when I'm moving around, I configure IP tables to block ssh from a host that opened more then three (new) connections over five minutes. This blocks most attempts as well.

---

### Post by petit.padavoine on 2007-08-06
Ok got it to work. For some reason it didn't like port 2222, so I gave it port 23...
Thanks for the info about security ;)

---

### Post by OoooMatron on 2007-08-06
> **petit.padavoine said:**
> Ok got it to work. For some reason it didn't like port 2222, so I gave it port 23...
Thanks for the info about security ;)

i use port 2222 on all my ssh services but I actually change the port in the sshd config file instead of mapping the ports from 2222 to 22 via the router.

another thing you can do to tighten it up is put the allow users tag in the config file and name the people that can log in (and disable root logins of course).

As a belt and braces approach i use shorewall firewall and limit the ip ranges that can connect to port 2222.

---

