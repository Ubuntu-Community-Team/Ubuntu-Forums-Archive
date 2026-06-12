---
title: "Timing out when connecting to 6.10 via ssh, after new HD install"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by caffienda on 2007-02-23
I am getting a time out when I connect to my server install.  
I'm typing:
```
ssh caffiendo@192.168.1.111
```
I'm getting a:
"192.168.1.111 port 22: Connection Refused"

I can connect to other boxes from this PC, but not into it.  Here 
here are the results from:
```
ps -ef | grep ssh
```
caffiendo     3749  3729   0   13:36  tty1     00:00:00  grep ssh


What does this mean?  When I do the 
```
ps -ef | grep ssh
```
on another machine, I get 5-7 lines..

---

### Post by Strider on 2007-02-23
SSH server is not installed by default.  You need to do an apt-get and install "openssh-server".  It will do all the preconfiguration and start the service, at which point you should be able to ssh to the server.

Once that's done you can run "ps -ef | grep ssh" and you should see additional lines now... you want to look for "/usr/sbin/sshd" specifically.

-Mike

---

### Post by caffienda on 2007-02-23
I was able to ssh to the server before.  I had copied files to and from it, but it stopped all the sudden.

---

### Post by Strider on 2007-02-23
Run "/etc/init.d/ssh start" to see if you can bring the service up.  If not, run "apt-get install openssh-server" to make sure the package is still installed... just a suggestion.

---

