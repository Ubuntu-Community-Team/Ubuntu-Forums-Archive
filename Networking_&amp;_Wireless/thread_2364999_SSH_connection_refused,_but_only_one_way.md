---
title: "SSH connection refused, but only one way"
date: 2017-06-30
forum: Networking &amp; Wireless
---

### Post by chunkydrew2 on 2017-06-30
I'm having trouble SSHing from my server (Ubuntu Server 16.04) to my desktop (Ubuntu 16.10). I can SSH from the desktop to the server with no problem, but I can't SSH the other direction, or even Ping. Both have static IP addresses, 1492.168.2.150 for server and 192.168.2.4 for desktop.
Again, I have no issues using **ssh 192.1682.150** from the desktop, but using **ssh 192.168.2.4** from server returns '***connection refused'*** , and ping doesn't connect. I ran the **netstat** command. but, honestly, can's make heads or tails of it.
Checking my ssh configuration file indicates that it is listening on port 22. so why can't I make it work? Any ideas, anyone?

BTW. I do plan to change the listening port from 22 when all my devices are connecting with no problems, but I need to get the connections working first.

---

### Post by The Cog on 2017-06-30
Can you post the output of these two commands, and we'll go from there:
```
netstat -lt
sudo iptables-save
```
that's a lower-case L after netstat. iptables-save will want your password, and might not output anything - that's OK. But please post your commands as well as the response - it always helps to make sure there was no typo in the command.

---

### Post by SeijiSensei on 2017-06-30
First, just to state the obvious, did you install openssh-server on the client?

If you did, then perhaps the client is running a firewall?

---

