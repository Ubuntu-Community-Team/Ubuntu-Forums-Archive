---
title: "Help with connecting to open  tcp ports"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by max00355 on 2010-12-09
so im new to ths whole port scaning thing and i was scanning my desktop for vulnerabilities with nmap it says 

23/tcp open ssh but i dont know how to connect to it. an also can you tell me how to connect to telnet service to

thank

---

### Post by wojox on 2010-12-09
Try telnet. 23 is usually the telnet port. 22 is ssh.

---

### Post by max00355 on 2010-12-09
but what do i use to connect to these ports

---

### Post by CharlesA on 2010-12-09
Port 23 is usually telnet, you'd use telnet to connect.

Telnet offers no security at all. Use SSH with a super strong password if you need to connect to a remote box.

EDIT: Were you running nmap against the localhost?

---

### Post by max00355 on 2010-12-09
can someone explain to me ow i connect in terminal i put telnet than my ip adress and it said invalad command

---

### Post by wojox on 2010-12-09
Do you have telnet installed?

It's not installed by default in Fedora. Like Charles said use ssh.

If it is installed try *telnet localhost*

---

### Post by max00355 on 2010-12-09
it is installed and what do u mean telnet local host

---

### Post by CharlesA on 2010-12-09
> **max00355 said:**
> can someone explain to me ow i connect in terminal i put telnet than my ip adress and it said invalad command

What do you mean?

You can post the output please.

---

### Post by max00355 on 2010-12-09
ok i put 

[HTML]telnet my ip[/HTML]

than what came out was

[HTML]Trying Myip...
Connected to myip.
Escape character is '^]'.
Connection closed by foreign host.
[/HTML]

could it be because its a mac

---

### Post by CharlesA on 2010-12-09
It connected. What's the problem?

---

