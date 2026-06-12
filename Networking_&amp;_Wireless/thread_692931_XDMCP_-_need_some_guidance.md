---
title: "XDMCP - need some guidance"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by RudolfMDLT on 2008-02-10
Hi there,

I have enabled XDMCP on one of my Ubuntu machines, and when I, from the client side, choose XDMCP from the session list, the server is in the list. How ever, upon clicking connect, the screen flashes black and back once or twice and then I'm back at the login screen. I have also tried Xnest, but still no success?

Any help or advice would be appreciated!

Thanks,

Rudolf

---

### Post by Temp08 on 2008-02-10
I assume you're using Gusty 7.10. If that's the case remote login via xdmcp is messed up for now. I've been researching it for some time now and apparently there is no solution as of yet. If I find anything or get mine to work I'll post a solution, good luck though.

---

### Post by RudolfMDLT on 2008-02-11
:frown:](*,):neutral::x#-o

thanks for the reply anyway! :-) I'll see what i can find and if I have any success I'll post back! Thanks!

---

### Post by RangoTheClown on 2008-02-13
Sounds exactly like the problem I have.  I installed Fiesty from a cd and it worked fine from that version, but after upgrading it didn't work.  I have two computers wit Gusty installed and have this problem on both.

---

### Post by RudolfMDLT on 2008-02-13
bump

Has ANYBODY got this to work? :)

---

### Post by nodanero on 2008-02-15
There is a bug in XDMCP-GDM and only listen in IPv6, if you use netstat you will see it.

You must disable ipv6 in aliases, and change the remote gdm screen to show the "simple screen with users list".

---

### Post by TurboRush on 2008-02-16
> **nodanero said:**
> There is a bug in XDMCP-GDM and only listen in IPv6, if you use netstat you will see it.

You must disable ipv6 in aliases, and change the remote gdm screen to show the "simple screen with users list".

Details on how to do the ipv6 part?

---

### Post by nodanero on 2008-02-21
In the file /etc/modprobe.d/aliases

```
sudo gedit /etc/modprobe.d/aliases

```

and change this line: 
alias net-pf-10 ipv6

with this:
alias net-pf-10 off

---

