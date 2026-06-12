---
title: "[SOLVED] SSH Broken after VirtualBox install"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by jjmatt on 2008-12-02
So, I can no longer ssh into my machine from outside of my LAN, nor can I ssh into any other machines outside my LAN.  However, I can ssh locally (into my computer, and other computers on my LAN and visa versa. I'm behind a router, but it is setup to port forward port 22 to this specific computer. I know this configuration is fine, because prior to several weeks ago, everything was working fine. The only "major" event that happened between ssh working and ssh not, was that I installed virtualbox, and I'm thinking it messed with some of the network settings, only I don't know what to look for, or how to fix it. Honestly, I'm not even positive that's what messed it up, I just can't think of anything else that could have gone wrong. 

Anyone have any thoughts?

---

### Post by Masuran on 2008-12-02
Could you give some more information on any errors you might receive?

---

### Post by jjmatt on 2008-12-02
The only error that I've receieved thus far is:

When ssh'ing from outside my lan with a windows computer (secure shell): Host is unreachable
However, when I ping my home, it works fine...

When ssh'ing from inside my lan with this computer (ubuntu 8.10) I get "ssh: connect to host [host] port 22: Connection refused"
But I know that ssh is working on their end, because I can ssh into that host fine from my ipod touch, and I used to be able to ssh into that host fine with this computer until [something happened]

Need any other info?

---

### Post by superprash2003 on 2008-12-02
did you install firestarter or ufw or anything similar recently?? it could be iptables blocking

---

### Post by Masuran on 2008-12-02
> **superprash2003 said:**
> did you install firestarter or ufw or anything similar recently?? it could be iptables blocking

Good idea, could you do a 
**sudo iptables -L**
in a terminal and post the output? This command lists the iptables rules. 

Also, is it possible *at all* to ssh from your internet connection. Perhaps your provider decided to start blocking port 22?

---

### Post by jjmatt on 2008-12-02
That would make sense, but no I haven't. Really the only thing I've touched/installed was virtualbox, other than usual daily updates.

Here's my iptables -L output:

Actually, nevermind! I had mobloquer installed (wasn't a problem before, but I guess the lists got updated, or something) and I totally forgot about it. Just opened it up and there was the ip that I had been trying to ssh to. Thanks for your help.

Two more questions though, I've been trying to learn more about iptables and such, do you guys know any good place to read up/learn about them besides their man pages?

Also, any Idea how to tell mobloquer to ignore everythign on port 22?

Thanks again!

---

### Post by superprash2003 on 2008-12-03
iptables is huge.. lots of commands .. it depends on what specifically you want

---

### Post by jjmatt on 2008-12-03
Well let's say my issue wasn't with mobloquer, but with iptables, what steps would I take to figure it out?

---

### Post by superprash2003 on 2008-12-04
well if it was an iptables issue, its usually because of messed up iptables, so you generally flush your iptables

---

