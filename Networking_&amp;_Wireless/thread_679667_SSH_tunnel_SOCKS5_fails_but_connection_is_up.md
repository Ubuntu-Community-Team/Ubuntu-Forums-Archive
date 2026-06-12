---
title: "SSH tunnel SOCKS5 fails but connection is up"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by Contess on 2008-01-27
Hi

I connect to my remote machine (prixoxy server) using putty and the SSH connection is solid. When I then configure firefox use that socks5 ..oxy ( 127.0.0.1 p:1088 ) firefox cannot connect to any website at all. the direct connection works fine

The same settings work fine in windows on another machine.

I have also tried to turn off the firewall (firestarter) but that didn't make any difference.

How to troubleshoot this ?

Thanks for your input

---

### Post by kevdog on 2008-01-27
Can you try a different port perhaps.  And you establish the ssh connection with the socks proxy using the command line correct?  Just to test a few things out, once you make the connection using the command line into an interactive shell, you can ping from the server correct??  You want to make sure the server computer doesnt have a firewall up not allowing outgoing connections.

Also with the firefox dialog, make sure you have only socks 5 completed (not http, ftp, etc).  User 127.0.0.1 as the host computer rather than localhost since Ive heard this causes problems for some.

---

### Post by Contess on 2008-01-27
> **kevdog said:**
> Can you try a different port perhaps.  And you establish the ssh connection with the socks proxy using the command line correct?  Just to test a few things out, once you make the connection using the command line into an interactive shell, you can ping from the server correct??  You want to make sure the server computer doesnt have a firewall up not allowing outgoing connections.

Also with the firefox dialog, make sure you have only socks 5 completed (not http, ftp, etc).  User 127.0.0.1 as the host computer rather than localhost since Ive heard this causes problems for some.

Hello Kevdog

1. I establish the connection using Putty because I don't know how to use SSH on the command line

2. I tried with port 80 instead 443 (those are the only two allowed on the remote Prixoxy box) .

3. Firefox: Yes, only the socks line is filled in, the others are blank and it's 127.0.0.1 not localhost.

4. I have tried to tunnel another application through the Putty SSH tunnel (ICQ) but the same error happens. The error happens so quickly (just when I hit the enter key), it is obvious that the connection never even leaves my laptop

---

### Post by kevdog on 2008-01-27
From what you are describing it sounds like the ssh connection is being made.  Anyway of opening up a terminal with putty and trying to ssh that way?

---

### Post by Contess on 2008-01-28
> **kevdog said:**
> From what you are describing it sounds like the ssh connection is being made.  Anyway of opening up a terminal with putty and trying to ssh that way?

yes, that worked. Took me a while to figure out the ssh command line though ;) 
The reason I used Putty was because that's what I'm used to but really, what's the point if we have the "real" ssh client built in anyway. Dropped Putty :-)

Thanks and cheers

---

### Post by kevdog on 2008-01-28
Putty is great for windows machines if cygwin is not installed.  On Linux machines, other that if the user is familiar with putty, it really serves no purpose.

---

