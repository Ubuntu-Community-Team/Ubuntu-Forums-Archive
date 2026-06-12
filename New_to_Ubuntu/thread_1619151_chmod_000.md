---
title: "chmod 000"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by su_penguin on 2010-11-11
Hello all,

I've recently setup net2ftp on my machine and it works great but I did a silly thing. On the Control Panel, which displays the listing of all the files to ftp, I was under the / directory and accidentally chmoded all the files and folders to 000. Now, when I go back to the machine and try to log into the server account, I can't log in. I still have another account on the machine which I can log into, which has admin access but, I'm not sure how to get to the files on the other account to un-mod them. 

Any help would be great.
Thanks,
Pengu

---

### Post by lisati on 2010-11-11
Ouch! I had a brain freeze the other day and used a misplaced chmod on some of my server's files as well. 

If your other admin account has sudo access, you might be able to repair some of the damage from there.

---

### Post by su_penguin on 2010-11-11
Yes, but, how exactly am I to know what files were modded? I was under / on the machine but, if I go to / under the admin account will I be able to see the same files? I'm not trying to say there is more than one / but, where would those files be located?

Sorry for my ignorance.
Thanks,
Pengu

---

### Post by lisati on 2010-11-11
I'm not fully up to speed with chmod, it's a command I avoid if possible.

If you are unable to login to an account as a result of a misdirected chmod, one place to check would be the account's home directory.

---

### Post by janpol on 2010-11-11
If you can't sudo with the other account, you can always boot from a livecd and try to fix things from there. 

```
chmod 775
```

---

### Post by janpol on 2010-11-11
> **su_penguin said:**
> Yes, but, how exactly am I to know what files were modded? I was under / on the machine but, if I go to / under the admin account will I be able to see the same files? I'm not trying to say there is more than one / but, where would those files be located?

Sorry for my ignorance.
Thanks,
Pengu
Run this from a terminal:

```
cd /
ls -l
```

That will show file's and folder's permissions under /. Look for the ones with lots of '-'. 

A file's permission with chmod 000 would look like this:

```
----------
```

In the case of dirs:

```
d---------
```

More info: [http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html")

Good luck!

---

### Post by holiday on 2010-11-11
try 

$ sudo find / -perm 000

Weird that you would do that, though. What were you thinking? I also don't believe you could do that unless you were root. / is the base directory of the whole system. You went 

$ chmod 000 /  ?

Maybe I'm not understanding you.

---

