---
title: "Can't change SSH Port from 22"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by ImNeat on 2007-01-05
I had SSH and FreeNX configured and working for Port 22, but I can't get them working on a different port.

I have thus far:
in **/etc/ssh/sshd_config**
changed &#8220;Port 22&#8221; to &#8220;Port 1025&#8221;
in **/usr/lib/nx/nxloadconfig**
changed &#8220;SSHD_PORT=22&#8221; to SSHD_PORT=&#8221;1025&#8221;
in **/etc/nxserver/node.conf**
changed &#8220;SSHD_PORT=22&#8221; to &#8220;SSHD_PORT=1025&#8221;
ran *sudo /etc/init.d/ssh restart*

After Googling around, I have noticed that a few people fixed this issue by editing **/usr/bin/nxserver** and changing SSHD_AUTH_PORT="22" to SSHD_AUTH_PORT="####"
-I tried to do this, but noticed that my /usr/bin/nxserver doesn't have that line.

Another weird thing is that my the status of my nxserver sais something about port 22:
```
brandon@dimension:~$ sudo /usr/NX/bin/nxserver --start
NX> 500 Service already running.
NX> 999 Bye.
brandon@dimension:~$ sudo /usr/NX/bin/nxserver --status
**NX> 900 ssh: connect to host 127.0.0.1 port 22: Connection refused**
NX> 110 NX Server is stopped.
NX> 999 Bye.
brandon@dimension:~$ sudo /usr/NX/bin/nxserver --start
NX> 500 Service already running.
NX> 999 Bye.
brandon@dimension:~$ 
```
Quite stange.  Anyone know what I need to do to make it look at 1025 instead of 22?

---

### Post by Epica on 2007-01-12
looks like you're set up ok for ssh i don't know about NX as i don't use it.

try this to login to ssh

```
ssh your_username_on_server@ip_of_your_server -p 1025 
```

the problem lies in that your clint programs are trying to connect to the default ports

hope this helps

---

### Post by weisbm on 2007-01-12
I ran into this and solved it by changing the SSHD_PORT=22 in node.conf to whatever you changed your SSH port to.  Of course, your mileage may vary...

Although, you should also check the client.  Mine connects to SSH on the new port, but had to be tweaked to connect to NX on the new port.

---

### Post by altonbr on 2007-02-05
Make sure to type in

```
& sudo /etc/init.d/ssh restart
```

After changing anything in "/etc/ssh/sshd_config"

---

### Post by matemargo on 2007-03-04
Hi.

I'm having this problem while trying to connect to SSH in my computer:

```

ssh: connect to host localhost port 22: Connection refused

```

And when I run this command: *sudo /etc/init.d/ssh restart* I get:

```

sudo: /etc/init.d/ssh: command not found

```

The only SSH related process running in my system is **ssh-agent**.

Any ideas how to solve this?

Thanks.

---

### Post by T-MAN3000 on 2007-03-16
I'm having the exact same problem as matemargo, I'm suspecting there's some kind of process not running. Does anyone know an answer?

---

### Post by matemargo on 2007-03-16
**T-MAN3000**: I should said that I had already solved this.

```

sudo apt-get install openssh-server

```

---

