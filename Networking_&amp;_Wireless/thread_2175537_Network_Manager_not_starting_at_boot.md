---
title: "Network Manager not starting at boot"
date: 2013-09-19
forum: Networking &amp; Wireless
---

### Post by mafsi on 2013-09-19
Hi,

I messed up with my computer and as far as i remember i only played with iptables and deleted from /etc/iptables..local or something.
I realize now that on boot &#8206;i get the message:

```
Waiting for network-manager to start...
Waiting another 60 seconds to start...
Booting without full network configuration

```

typing in terminal: sudo service network-manager start is starting the process but i don't have all the options in applet like: edit connetion a.s.o

Reinstalling did not solved the problem.

[I found this help]("https://help.ubuntu.com/community/IptablesHowTo") but i still dont know how to solve my problem.

I'm using Linux Mint 64bit and i posted here because i didn't find any help on mint forums.

My iptables now is empty

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     
``` 

Can anyone help me?
Thanks in advanced

---

