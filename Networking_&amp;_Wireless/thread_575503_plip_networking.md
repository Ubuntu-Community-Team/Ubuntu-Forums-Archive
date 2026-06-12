---
title: "plip networking"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by turtles on 2007-10-14
HI there I have a older laptop that does not have an Ethernet port and I am using plip to connect to it from an ubuntu laptop.
I can connect fine from the host ubuntu to the client laptop (running gentoo) I am unable to access the LAN or the Internet. I have added the name servers and edited the /etc/hosts file on the older laptop.
I can ping the laptop from my ubuntu laptop as well.
Question is do i need IPtables or can I just forward everything from the plip0 th the ath0 interface some how?
I do have iptables enabled on the host based on[ this how to]("http://help.ubuntu.com/7.04/installation-guide/i386/plip") but it is not working.

I have read this [http://www.debuntu.org/iptables-how-to-share-your-internet-connection](http://www.debuntu.org/iptables-how-to-share-your-internet-connection)
and used the script there with no luck.
Since I am already behind a firewall I need no added security

thanks for your help or ideas

---

