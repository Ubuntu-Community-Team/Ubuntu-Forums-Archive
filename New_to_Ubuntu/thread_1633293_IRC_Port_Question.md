---
title: "IRC Port Question"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by StuMcBill on 2010-11-29
Hi

I am new to Ubuntu, but I think I am finally getting to grips with it (still got a bit to learn, but I am picking up the basics), however, I cannot seem to connect to any IRC servers.

I have downloaded XChat-GNOME IRC Chat via the Ubuntu Software Centre and I am trying to connect to irc.freenode.net (32.1.20.4) on port 8001 (although I have tried port 6667, which I believe is the default for freenode) and it keeps saying "Connection failed. Error: Connection timed out".

Would anyone have any ideas as to why I cannot connect to this IRC server?

If it helps, I have updated my HOSTS file, is it possible that this is blocking it?

Thanks

StuMcBill

---

### Post by zipteye on 2010-11-29
I think you need to Ident to connect to freenode.

If you want to check out whats going on in the Raw, telnet to it.
telnet irc.freenode.net 6667

It's kind of cool to see how it talks in the raw.

And check this out:
[http://oreilly.com/pub/h/1963](http://oreilly.com/pub/h/1963)

---

### Post by StuMcBill on 2010-11-29
I ran telnet irc.freenode.net 6667 in terminal and I got this in reply:

Trying 32.1.6.176...
telnet: Unable to connect to remote host: Connection timed out

Does that mean anything to you?

Thanks for the quick reply.

---

### Post by prshah on 2010-11-29
> **StuMcBill said:**
> 
Trying 32.1.6.176...
telnet: Unable to connect to remote host: Connection timed out


Either you have not connected to your Internet, or your DNS servers are not working/accessible.

Can you browse normally? What changes have you made to your HOSTS file? (I assume you mean the /etc/hosts file, not HOSTS as in Windows)

---

### Post by StuMcBill on 2010-11-29
Yeah I am connected to the internet, I am posting this from the same computer.  And everything else seems to connect OK.

Opera, Firefox and Pidgin all connect.

Yeah it was my /etc/hosts file, I found a list on the internet that claimed that it should be added to it.

I might try editing it again and see if that makes any difference?

Thanks

Stu

---

