---
title: "cant open port 143?"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by compudude86 on 2007-02-01
i have installed dovecot imap, and squirrelmail, but squirrelmail is telling me:

> ERROR: Error connecting to IMAP server "localhost:143".Server error: (111) Connection refused

i think i remember going through this issue when i installed vnc and mysql.  any help?

---

### Post by compudude86 on 2007-02-01
i should also mention, i have no firewall up on the server, as it is already behind a hardware firewall.

---

### Post by dannyboy79 on 2007-02-01
did you create any firewall rules? please post sudo iptables -L for us so we can see if you have any firewall rules. if you have a rule that blocks all traffic, than you'll need to add port 143 to allow connections. this is already been defined within this forum, use the search function and you'll be set. plus, I would have thought the tutorial for what you are using as your mail server would have mentioned this to you?

---

### Post by DaveArb on 2007-02-01
> **dannyboy79 said:**
> if you have a rule that blocks all traffic, than you'll need to add port 143 to allow connections.

If I may add, if you have a rule that blocks *any* traffic to localhost, you are IMO making a mistake. The machine -likes- to talk to itself, and blocking it generally makes for a lot of pain to the user.

My first inclination (because I know I block nothing to/from localhost) would be that dovecot isn't running properly.

Unless you're not running it as a daemon but rather from xinetd or other superdaemon. Then, 100% of the time, the problem I'd be having would be because I forgot that listening on all ports is disabled by default.

---

### Post by compudude86 on 2007-02-01
iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by dannyboy79 on 2007-02-01
ok, so you don't have any rules in your firewall, so that answers that question! 

and to DaveArb, it's common in iptables to block all incoming traffic and then open certain ports. I assumed anyohe who is smart enough to play with iptables, knows they would have to allow loop-back traffic. I guess I shouldn't have made that assumption with you.

here is a thread that solves this issue if you are running your imap server thru xinetd. [http://www.directadmin.com/forum/archive/index.php/t-1039.html](http://www.directadmin.com/forum/archive/index.php/t-1039.html)

here is a solution for dovecot and squrrilmail. gogle is your friend, use it.
[http://www.dovecot.org/list/dovecot/2005-August/008477.html](http://www.dovecot.org/list/dovecot/2005-August/008477.html)

and then just keep clicking on the "next thread" for further help with similar setup issues.

---

### Post by DaveArb on 2007-02-01
> **dannyboy79 said:**
> and to DaveArb, it's common in iptables to block all incoming traffic and then open certain ports. I assumed anyohe who is smart enough to play with iptables, knows they would have to allow loop-back traffic.

Sure, but the connection that is failing is *"localhost:143"*

I try not to assume anything, it's so often the simple things that trip people up.

---

### Post by dannyboy79 on 2007-02-01
> **DaveArb said:**
> Sure, but the connection that is failing is *"localhost:143"*



I don't know what you're trying to point out here???? Just because it states that localhost:143 connection failing doesn't neccessarily mean that his firewall is blocking loop-back connections. He doesn't have any firewall rules so that's not the problem as I stated above. It has to do with his configuration of his programs just like you said easrlier.

---

