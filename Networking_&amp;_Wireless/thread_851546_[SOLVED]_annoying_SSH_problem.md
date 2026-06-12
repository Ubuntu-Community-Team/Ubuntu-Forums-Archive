---
title: "[SOLVED] annoying SSH problem"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by isellapples on 2008-07-06
hi, bit of a strange one this (i think). Basically, ive got a web server set up using ubuntu and have been connecting to it from my windows laptop via SSH (putty) and remote desktop. 

Was all working fine, then for some reason SSH has completely stopped working - but only from my laptop (regardless of what IP address it has)! I can still SSH using any other computer connected either via our LAN or through the WWW. Remote desktop still works fine too, but its a little slow for when I only need the command line. 

So yeh... any ideas on why this might be/how to solve this would be great! Ive got guarddog as my ubuntu firewall, and have tried disabling it but it made no difference. likewise ive disabled the firewall on my laptop but with no joy. :confused:

oh, and port forwarding in the router is all correct too...

---

### Post by tamoneya on 2008-07-06
you say it doesnt work.  Are there any specific errors or does it just silently fail.

---

### Post by isellapples on 2008-07-06
comes out with the message:

"Server unexpectedly closed network connection"

...

---

### Post by tamoneya on 2008-07-06
i find my computer does this as well sometimes.  I think it has to do with my ISP but Im not positive.  My solution is just to try it again.  Sometimes it takes 2 or 3 times but never more than that.

---

### Post by isellapples on 2008-07-06
but it should be independant of my isp - im working on the same LAN. I'm thinking i might have gone and got my computer blacklisted, unfortunately i dont know how to find out! so annoying

---

### Post by issih on 2008-07-06
I've no idea if this is your problem, or indeed if it is even how this problem would arise.

I was wondering if you had set up your laptop to access the server using a generated key that has been blacklisted during the recent security debacle.

Just a thought as if it was that, I'd expect other computers to work as you would need to log in using a password.

Just a thought.... probably wrong

---

### Post by isellapples on 2008-07-06
alas no, i was still using username/password to login from my laptop just as any other computer - never got round to setting up a key

is there a limit to the number of times you can incorrectly enter a password before being blocked? perhaps i was retarded and went over the limit...?

---

### Post by isellapples on 2008-07-07
right, solved! for some reason ubuntu had decided to block the local ip addresses assigned to my laptop, but not (im guessing) any of those assigned to my other computers.

in /var/log/auth.log

```
Jul  7 12:09:31 ZionicWeb sshd[17195]: refused connect from ::ffff:10.0.0.4 (::ffff:10.0.0.4)
```

so added  

```
sshd : 10.0.0.* : allow
```

to /etc/hosts.allow and it appears to have solved the problem. bit of a strange one though... wish i knew where it had been blocked and what by


edit: blocked in hosts.deny, appropriately enough. very odd

---

