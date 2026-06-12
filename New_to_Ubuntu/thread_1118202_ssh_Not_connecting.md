---
title: "ssh Not connecting"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by tbear55387 on 2009-04-06
I have a server behind a netgear router. and I am tring to connect to the server(boxA) from machine B, but when I type ssh boxA it hangs. I have checked the iptables and nothing is found. I am able to use svn+ssh to connect, Putty connects. No other computers connects to boxA. Any ideas????

---

### Post by ptn107 on 2009-04-06
Try:
```
ssh -vv boxA
```
see what it says.

---

### Post by MrWES on 2009-04-06
> **tbear55387 said:**
> I have a server behind a netgear router. and I am tring to connect to the server(boxA) from machine B, but when I type ssh boxA it hangs. I have checked the iptables and nothing is found. I am able to use svn+ssh to connect, Putty connects. No other computers connects to boxA. Any ideas????

Do you have an account on boxA?

Bill

---

### Post by tbear55387 on 2009-04-07
Sorry about that I ran a command and it took down the server all night - oops!
OpenSSH_4.3p2, OpenSSL 0.9.8b 04 May 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
then hangs

---

### Post by tbear55387 on 2009-04-07
Okay after trying again here is some more of what I recieved:
OpenSSH_4.3p2, OpenSSL 0.9.8b 04 May 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to xx.servername.xx [xx.xx.xx.xx] port 22.
debug1: connect to address xx.xx.xx.xx port 22: Connection timed out
ssh: connect to host xx.servername.xx port 22: Connection timed out

i have checked the router and it forwards to the server. I am able to connect using programs like putty just not from command line or using tools like sftp or scp or ssh from command line

---

### Post by The Cog on 2009-04-07
Let's make sure it is trying to connect.
While SSH is trying to connect, i.e. before it says Connection timed out, run this command from another shell:
**netstat -tn**
and see if you can see a connection to the server in question port 22 in the SYN_SENT state. If not, then for some reason SSH isn't really trying to connect. If the entry is there, then suspect router forwarding not being right, or a firewall issue.

---

### Post by tbear55387 on 2009-04-07
I went and typed ssh to box A from box B; boc B states it is trying to connect, I then netstat -tn and found SYN_SENT.

---

### Post by The Cog on 2009-04-07
Then it must be a port forwarding problem so the router isn't actually forwarding port 22 properly, a firewall blocking the connection, or a plain routing problem where B can't each a at all. If your request was getting through (and replies getting back) you would quickly either get the connection accepted. Or rejected if SSH wasn't listening.

SYN_SENT means the connection request has been sent but no response received yet.

---

### Post by tbear55387 on 2009-04-09
Thanks you for your help. I will look down that path and see what I can find out. Many thanks.

---

