---
title: "basic ssh query"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by kikazaru on 2007-02-16
I'm trying to use ssh, and scp to copy some files over my local network, but my computer is refusing the ssh connection even to itself. It says, 

ssh: connect to host xxxx port 22: Connection refused

I got my local ip number from ifconfig, and also tried localhost etc. 

The hosts.allow and hosts.deny files are both empty aside from # comments. 

ssh-agent is running as:

 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager

Any suggestions?

ps Running Edgy Eft

---

### Post by rbalfour on 2007-02-16
Sounds like ssh server is not installed.

Try

# sudo apt-get install ssh

Then try ssh again.

---

### Post by sdide on 2007-02-16
Hey.

sshd needs to run,

```
# ps -ef | grep sshd
root      9073     1  0 11:22 ?        00:00:00 /usr/sbin/sshd
root      9134  8986  0 11:23 pts/1    00:00:00 grep sshd
# 
```

Where the last line is grep catching the grep itself (not important)

if sshd is _not_ running, do: 

```
# /etc/init.d/ssh start


```

---

### Post by kikazaru on 2007-02-16
Thanks guys, you fixed my problem.

I was pretty dumb... I almost installed ssh before, but when I looked at the description I saw some blurb about ssh being a transitional package subsumed by some other ssh stuff that seemed to be installed already, so I didn't bother. D'oh.

---

