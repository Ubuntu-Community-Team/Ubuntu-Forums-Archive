---
title: "[SOLVED] ports sometime closed"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by stringkarma on 2008-06-24
I am having an unusual issue. I hope someone may have some insight for me.
I have 3 computers. Lets call them home, work and server.

When connecting through ssh I can connect:
- from home to server
- from server to work
- from home to server to work
but when I try to connect from home to work I get:
```
ssh: connect to host ems4.rrc.uic.edu port 22: Connection refused
```
Also when I nmap from home to work I get:
```
Starting Nmap 4.53 ( http://insecure.org ) at 2008-06-24 21:48 CDT
All 1714 scanned ports on work.workserver.com (***.***.***.***) are closed

Nmap done: 1 IP address (1 host up) scanned in 0.235 seconds

```
though from server (or home to server) to work I get:
```
Starting Nmap 4.53 ( http://insecure.org ) at 2008-06-24 21:51 CDT
Interesting ports on work.workserver.com (***.***.***.***):
Not shown: 1707 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
111/tcp  open  rpcbind
113/tcp  open  auth
631/tcp  open  ipp
1234/tcp open  hotline
5900/tcp open  vnc
8000/tcp open  http-alt

Nmap done: 1 IP address (1 host up) scanned in 0.129 seconds

```
I wonder if this is due to the ssl key stuff, but then why could I go from home to server but not home to work. And besides nmap comes up empty too which would not have anything to do with ssl. So perhaps I am off base there.
As a note all comps are running Ubuntu 8.04 and are regularly updated, the server does not run X.
Thanks for any help

---

### Post by stringkarma on 2008-06-25
So I have been doing some testing and the nmap results are the most important. I have been trying to vnc in from various computers and they all work (even some windows boxes) except from the "home" computer.

Basically it comes down to all ports on work are closed to "home," but ports are open to all others.
 
Any ideas?

---

### Post by vascotia on 2008-06-25
> **stringkarma said:**
> So I have been doing some testing and the nmap results are the most important. I have been trying to vnc in from various computers and they all work (even some windows boxes) except from the "home" computer.

Basically it comes down to all ports on work are closed to "home," but ports are open to all others.
 
Any ideas?

Can you paste the Netmask of all machines?

---

### Post by stringkarma on 2008-06-25
From ifconfig:
home has mask: 255.255.255.0
server: 255.255.255.0
work: 255.255.255.0

Is this what you were asking for?
If not let me know.

---

### Post by vascotia on 2008-06-25
> **stringkarma said:**
> From ifconfig:
home has mask: 255.255.255.0
server: 255.255.255.0
work: 255.255.255.0

Is this what you were asking for?
If not let me know.

Ok, the netmask seems ok..
Just to make sure.. did you update your ssh client and server?
if not..
login as root... and do:

apt-get update
apt-get dist-upgrade 

when you do this, the dist-upgrade will show you what packages needs to be updated, tell me if openssh is in the list and also, when it is.. just upgrade/update it..

---

### Post by stringkarma on 2008-06-25
As I said, I keep my computers updated, all the same I just did the upgrade and after today's new updates (the closest of which was vino) I never saw any openssh packages.

To add to the pool of knowledge I installed an ssh client on my wife's computer (Vista) which is also wirelessly connected behind my home router. Her's was able to connect to the work computer. This confirms that it is not the settings of the router.

As I am able to connect to the server (outside the router) I think I am left to think that either home blocks connections to work or work blocks connections from home. I think perhaps active blocking, perhaps blacklisted somehow.

Also Thanks Vascotia for the attention.

---

### Post by lisati on 2008-06-30
Your home machine might be blocked at your work's end. Some IT departments get nervous about who they let in.

---

### Post by stringkarma on 2008-07-02
see my other thread on this if you need an answer to a similar problem: 

[http://ubuntuforums.org/showthread.php?t=843388](http://ubuntuforums.org/showthread.php?t=843388)

---

