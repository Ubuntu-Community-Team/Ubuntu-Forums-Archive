---
title: "server 12.04 using hundreds of sessions"
date: 2014-06-19
forum: Networking &amp; Wireless
---

### Post by patdundee on 2014-06-19
Hi Guys
I am running several Ubuntu Servers all on 12.04. Over the past 2 days one of these servers is behaving very strange. It is constantly trying to connect to its DNS server and as such is Maxing out the CPU on my firewall. If i limit the sessions in the firewall for the Server IP address this solves the Max out problem, but it very quickly uses up all sessions assigned to it. I have tried allowing 500, 2000 and 4000 permited sessions through the firewall for the base IP of the server and within 5 minutes it has used them all up. As it does this it prevents other users to connect to the server as it cannot get back out on the Wan again due to session limit. 

When i check my firewall logs, it is full of the source IP (the ubuntu server) making a connection to the outside DNS servers i use. I tried a work around and told it to use the firewall for DNS but the result is the same.

Has anyone come across this before. Any help would be greatly appreciated

P

---

### Post by tgalati4 on 2014-06-20
DNS resolution used to be a simple framework, but now it is quite complicated and therefore more things to check when things go wrong.

Check the following on all of your servers for changes:

```
cat /etc/resolvconf/interface-order
man interface-order
```

It's possible if one device (virtual or otherwise) is stuck that could cause an issue.

Install *htop* across the servers and watch them.  What is the specific process that is taking up CPU cycles?

---

