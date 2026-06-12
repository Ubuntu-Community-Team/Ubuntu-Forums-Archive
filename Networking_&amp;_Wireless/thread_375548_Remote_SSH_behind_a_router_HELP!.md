---
title: "Remote SSH behind a router HELP!"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by ADloser on 2007-03-03
I'm trying to set up a remote server on my desktop at home so that I can access my files from my school computer. I am behind a router.

I can connect to USER_NAME@192.168.1.12 which is my LAN address since I am connected via a router. However I need to be able to connect with computers outside of my LAN. I tried ssh USER_NAME@<external IP> but it just hangs. I set up my router to foward the correct port to my computer, but it doesnt help. WHat am I doing wrong?

 Thanks in advance for the help!

---

### Post by nyinge on 2007-03-04
How about telnetting it first to check if the port forwarding is working?

```
 telnet <External IP> 22 
``` should return something about openssh together with some garbage.

---

### Post by ADloser on 2007-03-04
Thanks for the quick reply. Here is the output:

Trying <external IP>...
Connected to <external IP>.
Escape character is '^]'.
SSH-2.0-OpenSSH_4.3p2 Debian-5ubuntu1

That's from my own computer.

I also tried this: 
SSH to university computer, 
then: telnet <External IP> 22
output: Trying <external IP>...
telnet: Unable to connect to remote host: Connection timed out

---

### Post by tribaal on 2007-03-04
I know my school blocks outgoing ssh connections for some reason... Maybe yours does too?

- Trib'

---

### Post by Bobtheknight on 2007-03-04
I had almost the exact same problem as you, maybe my experience can shed some light.  Here is the steps I tried.

1.  Port-scan my external IP to find out if the port is responding.  The internet program I used is 
recommended by RandomJoe who said:
I have used GRC's ShieldsUP web-test to check open ports - [http://www.grc.com/default.htm](http://www.grc.com/default.htm) Scroll down to ShieldsUP. Select that, and pick the type of scan you want.


2.  I found my port 22 is "stealth" meaning packets are dropped (I think) so I checked to ssh into my ubuntu box from within my network (192.168.0.2) no response.

3.  I checked if a daemon is listening on port 22 suggested by Mr. C.  
netstat -an | grep :22

it is.

4.  I checked if a firewall is blocking the port (I used firestarter, then forgot I had it installed) but that's the problem.  So I added a rule to enable that port.  And it worked!

---

