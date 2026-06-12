---
title: "Cannot Ping Edgy?"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by bsahm on 2007-02-09
Hello,

I was having difficulty networking XP and Ubuntu (I followed the guide from another thread) so I got down to basics and tried pinging Ubuntu from both my router and XP.  I was unable to ping from either.  BTW, pinging using IP address, not by name.

I booted up the Dapper Live CD and was able to ping just fine.
I booted up the Edgy Live CD and am unable to ping.  

Is there a way to fix this?  Not sure if any of it has to do with the networking problems I was having but if I can't do a basic ping, that can't be good.  

Thanks for your help,,

BANDS

---

### Post by gradedcheese on 2007-02-09
So, just to verify: you boot up via the Edgy live CD, open a terminal, run 'ifconfig' to see what your IP address is, and then ping that address from another PC but the ping fails?  Can you ping other PCs (at their known addresses) from the shell in the booted up Edgy live CD?

---

### Post by bsahm on 2007-02-09
Yes, that is correct.  

Yes, I can ping other PCs from Edgy.  

Tks

BANDS

---

### Post by m3_del on 2007-02-09
Sounds like it might be a iptables issue. perhaps something is blocking incoming echo requests?!?!? Someone here may know more about how to check that.

---

### Post by bsahm on 2007-02-09
That is what I was thinking but I am not familiar enough with Ubuntu.  Hopefully somebody has had the same experience.  

Tks!

---

### Post by bsahm on 2007-02-10
bump

---

### Post by bsahm on 2007-02-12
bump

---

### Post by dannyboy79 on 2007-02-12
do you have a router? where are you trying to ping it from? what is the output from 
sudo iptables -L (or maybe it's a lower case L, i forget.)

---

### Post by bsahm on 2007-02-15
Well the problem seems to be fixed.  I did a "sudo iptables flush" and it cleared out all the many entries in ip tables and vuala! I was able to ping my ubuntu box from both router and XP and am able to browse both machines from each other.  

I find it interesting that nobody else has run into this yet.  I am not sure why iptables had so many entries from the start.  Thoughts on that would be appreciated.

Tks,  BANDS

---

### Post by dannyboy79 on 2007-02-16
iptables DOESN'T have any entries by default. not unless you installed something that did this automatically? or if you ran a firewall script that added them? or maybe you use firestarter? but I can tell you for sure that iptables doesn't have any rules to begin with because ubuntu comes with no services enabled by default which means no open ports, which means no need for any iptables rules. just so you know now, your ubuntu box is wide open! you can do a ```
sudo netstat -pat 
```to see what ports are listening for connections.

---

### Post by bsahm on 2007-02-16
Thanks!  I will give it a go when I get home.  I started reinstalling Edgy last night and will finish tonight.  I will check iptables before I do anything else to see if it is preventing access again.  I don't want to be open to world though so I will have to find a simple iptables for dummies document to help me.  Any links to such a document would be greatly appreciated.  

Tks again for your input!

---

### Post by dannyboy79 on 2007-02-19
as I said, if you don't enable any services that listen for connections, than you don't need any iptables rules since you're not allowing any connections to your box. do the sudo netstat -pat to see if there is anything listen for OUTSIDE connections, if so, you'll want to enable iptables rules that protect you from outsides, but allow YOU the access you want.

---

