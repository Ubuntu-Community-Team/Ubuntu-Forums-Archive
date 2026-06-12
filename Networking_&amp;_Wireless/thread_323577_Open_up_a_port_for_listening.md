---
title: "Open up a port for listening?"
date: 2006-12-22
forum: Networking &amp; Wireless
---

### Post by wjbell on 2006-12-22
I need to get telnet to accept connections on my ubuntu edgy box.  I know the dangers of telnet but this machine is behind a firewalled linux machine.  I'm familiar with linux in general and have used it for years but can't get ubuntu to listen on port 23.   I've installed the telnetd package and made sure there's no firewall running but when I telnet into it I get this error:

[root@serengeti /root]# telnet 192.168.0.20
Trying 192.168.0.20...
telnet: Unable to connect to remote host: Connection refused

I've checked /etc/services and telnet's listed there.

I installed firestarter just in case there was a firewall somewhere and opened up the correct ports but still no go.  Uninstalled that and am back to no firewall.

Can someone tell me how to get ubuntu to accept telnet connections?

TIA

---

### Post by koenn on 2006-12-22
Probably connections to telnetd are managed by inetd or xinetd and you'll have to confogure those to allow connections to telnetd. I've seen a post elsewhere on these forums explaining how to. maybe you can search  ? (or find  :-) )

---

### Post by beardiggin on 2008-01-18
I know this is an old message.  

Were you trying to telnet from outside of your network?

The 192.168.---.--- is a non-rouuteable address so it should be impossible to telnet in unless your Router has been given a static IP address by your service provider.  If the router has a static IP then you can configure your router to send telnet requests to a specific PC on your network.

---

