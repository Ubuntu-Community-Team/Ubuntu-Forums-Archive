---
title: "SSH:  Multiple Local Ccomputers; Access From Outside Network"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by Ek0nomik on 2007-07-15
I have two desktop computers on my local network.  They are all connected into a switch.  As I am sure you know, each one has its own internal IP address.  192.168.1.103 and 192.168.1.1.  Both desktop computers are running openssh.  I know for certain SSH works, because I can connect by issuing "ssh username@192.168.1.103" and the same for the other IP.

I want to be able to connect to these two computers from outside the network with my laptop.  I changed the default port for both desktops.  One is running 2008, and the other 1987.  I have both ports forwarded in my router for both internal addresses.  When I issue the command, this is my output:

```
dove@edelweiss:~$ ssh -p 2008 my.external.ip.adress
ssh: connect to host my.external.ip.adress port 2008: Connection timed out

```

But, when I issue the same command, simply with the internal IP, I can connect:

```

**dove**@edelweiss:~$ ssh -p 2008 politician@192.168.1.103
politician@192.168.1.103's password: 
Linux liberty 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have mail.
Last login: Sun Jul 15 01:26:19 2007 from edelweiss.local
**politician**@liberty:~$ 

```

**Edit**:  Problem solved!  I checked my router again and I seem to have mistyped "103" with "3".  Well, as Al Franken said, "Mistakes are a part of being human. Appreciate your mistakes for what they are: precious life lessons that can only be learned the hard way. Unless it's a fatal mistake, which, at least, others can learn from."

---

### Post by eentonig on 2007-07-15
Actually, I personally would recommend having only one system reachable from the internet. And use that to hop on to the next PC.

This way, only one PC is open to hackers to try and breach it.

---

