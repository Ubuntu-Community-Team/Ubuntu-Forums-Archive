---
title: "[SOLVED] SSH Server not working: blocked?"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by ragingcaribou on 2008-06-22
Hey Ubuntu forum dudes and dudettes,

Firstly, I'm so-so in linux know-how, but I've used it for years (for school/research), just never had to do admin stuff.  Converted to linux on my desktop and now my laptop in the last few months (ubuntu 8.04).

SSH would be nice, so I followed all the threads I could and set it up.  I can 

ssh localhost

, no problem, but I can't 

ssh username@myipaddress

which sucks (timeout).  

I figure the port I'm using is blocked somehow (I've tried a few to no avail; 22, 2222, 512, 23456). Maybe it's my internet provider (rogers cable based), or my router (I saw this on a few threads...not understanding...) that are responsible.

Can anyone help? 

Thanks!

---

### Post by jpkotta on 2008-06-22
I have the exact same problem.  I've never had this happen before.  I think it's not a problem with ssh, because I tried using netcat to listen for connections on random ports, to no avail, e.g.
```
nc -l -p 22222
```
It's always blocked according to nmap *from other machines*, but open when on the localhost.  I'm baffled, and I'm looking for solutions.  It is not a firewall issue, AFAIK, because I checked iptables.

I have other machines that work correctly.  There was weirdness in the dist-upgrade of the broken one, but so far this is the only issue I've had.

---

### Post by kevdog on 2008-06-22
You have done nmap from Local Machines?

What is your iptables policy?
sudo iptables -L

What about trying to connect to the server using the ssh -vvv (3 v's) in the client command statement?

---

### Post by ragingcaribou on 2008-06-22
Hey guys,

ssh -vvv myipaddress doesn't work.

------------------------------------

sudo iptables -L 

gives:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

------------------------------------

nmap localhost

gives:

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-06-22 17:38 EDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1712 closed ports
PORT    STATE SERVICE
512/tcp open  exec
631/tcp open  ipp

-------------------------------------

nmap myipaddress -PN

timeout.

Seems things are set right to me...just not working!  
btw I'm on port 512 right now.

Thanks for the help and feedback so far!
Dennis

---

### Post by ragingcaribou on 2008-06-23
CONCLUSION:

This is actually a very normal issue that leads to (for me) a somewhat complicated solution.  What's happening is that I'm setting up SSH on a router. 

SUGGESTION TO THOSE WITH SIMILAR PROBLEMS:

You need to get into the port forwarding.  I found this thread helpful (i.e. I got ssh working on both of my computers (using different ports)):  

[http://ubuntuforums.org/showthread.php?t=247563&highlight=ssh]("http://ubuntuforums.org/showthread.php?t=247563&highlight=ssh")

---

