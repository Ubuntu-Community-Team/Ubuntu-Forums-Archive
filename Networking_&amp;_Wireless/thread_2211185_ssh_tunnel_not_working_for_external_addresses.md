---
title: "ssh tunnel not working for external addresses"
date: 2014-03-14
forum: Networking &amp; Wireless
---

### Post by Nathan_Paul on 2014-03-14
I am at a client site and they block some addresses so I am trying to use ssh -tunnel. 

I am connecting to my corp ssh machine 

It is working for my intranet sites but failing for pubic addresses like yahoo.com

Following is working

[FONT=Menlo] ssh -L 9291:intranet.bugzilla.com:80 [email]myname@ssh.mycomany.com[/email] 

localhost:9291 is taking to  bugzilla.

But If I do 

 ssh -L 9292:[www.yahoo.com:80](www.yahoo.com:80) [email]myname@ssh.mycomany.com[/email] 

then localhost:9292 is not working for yahoo. It is taking me to ssh.mycompany.com  internal address and timing out

Is there any flag I need to set on ssh.mycompany.com?.

Thanks for the help.

NP


[/FONT]

---

### Post by papibe on 2014-03-14
**Thread closed**.

From the Ubuntu Forum rules (found here: [http://ubuntuforums.org/misc.php?do=showrules](http://ubuntuforums.org/misc.php?do=showrules) ):
> We do not support circumventing TOS, EULA, etc here.
This applies to circumventing network owners restrictions.

Regards.

P.S.: feel free to post in the [Resolution Centre]("http://ubuntuforums.org/forumdisplay.php?f=123") subforum if you have any questions regarding this action.

---

