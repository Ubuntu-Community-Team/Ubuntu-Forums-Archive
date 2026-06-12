---
title: "Is there a CLI email-notify program~~"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by haha.ysj on 2009-05-07
I try to find a cli email-notify program~ but I didn't find it.

It will be gratefull if someone give me some clue~~

3x in advance : )

---

### Post by cmnorton on 2009-05-07
What's an email-notify program?

If you are referring to the ability to use command line email,

sudo apt-get install -y mailutils

will get you command line email.

---

### Post by lykwydchykyn on 2009-05-07
There is the classic "biff" in the repositories.  I haven't actually tried it, but that's more or less what it does.
> 
Description: a mail notification tool
 biff is a small program that prints a message to your terminal when new email arrives. Actually, the message is printed by the comsat daemon, and biff just
 enables/disables the u+x permission flag for the terminal, which comsat uses to determine whether or not to write to your terminal.

 biff is mainly of historic interest, since there are much better alternatives (such as xlbiff and gbuffy) that are network-aware and do not require a
 daemon. Although there are no known security problems, running additional services is often considered risky.

 By default, the biff service is disabled. To use biff email notification, you must enable this service by running 'update-inetd --enable biff' after the
 package is installed. You may also need to modify the configuration of your mail transport agent to enable comsat notification.


---

