---
title: "How to change machine name?"
date: 2006-08-09
forum: Networking &amp; Wireless
---

### Post by Jabran Asghar on 2006-08-09
Hi, 

I am using Dapper Server version. Just changed /etc/hostname to "dapper1" from "dapper", and did a reboot. Now, network will not come up! When using sudo, I get following message:

```
sudo: unable to lookup dapper1 via gethostbyname()
```

Where else should I also change the machine name to make it work?

Thanks.

Jaban

---

### Post by MacMan on 2006-08-09
> **Jabran Asghar said:**
> Where else should I also change the machine name to make it work?

Have a look in the /etc/hosts file: it may be still referencing to the old server name.

Ciao.
-- 
Mac

---

### Post by bscbrit on 2006-08-09
System -> Administration -> Networking

Select the General tab and ensure that the name is changed there also.  Reboot.

Make note to yourself in your Ubuntu notebook - don't change settings unless you are _sure_ you know what will happen. :D

---

### Post by Jabran Asghar on 2006-08-09
> **MacMan said:**
> Have a look in the /etc/hosts file: it may be still referencing to the old server name.

Ciao.
-- 
Mac

Yup, This worked. I had to reboot in recovery mode to be able to edit hosts file as sudo was not working. 

Re:bscbrit: I am uning server version so cannot do that. Text only.

Thanks all.

---

### Post by bscbrit on 2006-08-09
Apologies - glad to see that it is cured.

---

### Post by georgew on 2007-12-07
> **bscbrit said:**
> System -> Administration -> Networking

Select the General tab and ensure that the name is changed there also.  Reboot.



Great!

Now how do we do this from a command prompt?  there are those of us that sit
thousands of miles away from our servers, and do all of our administration from 
the command line, without ever touching the unix gui...  We are the old farts
that are more at home on the command line anyway, and we are used to
manipulating the matrix with text...  We are lost with a gui, we still use vi,
and /like/ it...  It's been 10 or 15 years since I messed with xwindows...

Plus, the whole reason I need to make this change is I build virtual machines, 
and need to be able to clone a fully configured machine, and the clone needs
a different name, among other things.  Any /my/ network always comes up...
it /has/ to...;)

---

### Post by Keith_Beef on 2007-12-07
Hostname.

[http://www.linuxmanpages.com/man1/hostname.1.php](http://www.linuxmanpages.com/man1/hostname.1.php)


Beef.

---

### Post by georgew on 2007-12-07
It looks like the answer is to edit /etc/host*, run 
"hostname newhost.name.com"
and run
sysctl kernel.hostname="newhost.name.com"
Then reboot.
then apt-get remove ssh openssh-server
remove the ssh keys:
rm /etc/ssh/ssh_host*
and then reinstall ssh:
apt-get install ssh openssh-server
reboot one more time for good measure

Now everything is correct...

I'm sure I did it wrong, but I got the results I was looking for.

I'm more of a unix bulldozer than a unix hacker I guess...:lolflag:

---

### Post by georgew on 2007-12-07
oh, and I forgot...  The work required to make the ethernet com up...

You must edit /etc/iftab with the new mac address of your new ethernet interface.

Doh!

---

