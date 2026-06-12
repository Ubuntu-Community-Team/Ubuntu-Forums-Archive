---
title: "Is this somethingI should be concerned with?"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by Baldrick_NZ on 2011-04-08
Whilst playing with the 'disk Usage Analyser', I discovered there was a user called 'Tommy' (see pic attached) on my PC.

I have no idea how this got there, and I'd have to say it's a bit concerning.

I've checked under users and groups, and only my profile appears.

Can onyone shed any light on this please? 

Cheers,
Baldrick.

---

### Post by plucky on 2011-04-08
Open a terminal and post output of ```
ls -l /home
df -h
```

Is it possible someone created the user "tommy" and then removed it,leaving the /home directory still there?

Are you running out of space in your /home?

---

### Post by jmszr on 2011-04-08
Never mind, sorry.

---

### Post by Rubi1200 on 2011-04-08
Do you use remote desktop software like vino or vnc?

---

### Post by coffeecat on 2011-04-08
Your /home/tommy folder appears to be associated with Google Picasa. I have no experience of Picasa, but I found these on Launchpad and you are not alone:

[https://answers.launchpad.net/ubuntu/+source/openssh/+question/138058](https://answers.launchpad.net/ubuntu/+source/openssh/+question/138058)

[https://bugs.launchpad.net/ubuntu/+bug/691476](https://bugs.launchpad.net/ubuntu/+bug/691476)

Seems to be down to Google, but whether it's as large a security risk as someone is making out on one of those links, I don't know.

---

### Post by Baldrick_NZ on 2011-04-08
> **plucky said:**
> Open a terminal and post output of ```
ls -l /home
df -h
```

Is it possible someone created the user "tommy" and then removed it,leaving the /home directory still there?

Are you running out of space in your /home?

Nope it's only me with a user account. I don't know a 'tommy'.

```
baldrick@baldrick-desktop:~$ ls -l /home
total 24
drwxr-xr-x 66 baldrick baldrick  4096 2011-04-09 08:36 baldrick
drwx------  2 root     root     16384 2011-02-09 22:45 lost+found
drwxr-xr-x  3 root     root      4096 2010-07-20 18:34 tommy
baldrick@baldrick-desktop:~$ 

```

```
baldrick@baldrick-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              26G  4.0G   21G  17% /
none                 1003M  272K 1003M   1% /dev
none                 1007M  6.5M 1001M   1% /dev/shm
none                 1007M   84K 1007M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sda1             428G   20G  386G   5% /home
baldrick@baldrick-desktop:~$ 

```

---

### Post by Baldrick_NZ on 2011-04-08
> **coffeecat said:**
> Your /home/tommy folder appears to be associated with Google Picasa. I have no experience of Picasa, but I found these on Launchpad and you are not alone:

[https://answers.launchpad.net/ubuntu/+source/openssh/+question/138058](https://answers.launchpad.net/ubuntu/+source/openssh/+question/138058)

[https://bugs.launchpad.net/ubuntu/+bug/691476](https://bugs.launchpad.net/ubuntu/+bug/691476)

Seems to be down to Google, but whether it's as large a security risk as someone is making out on one of those links, I don't know.

I have never used picassa personally, but my wife may have. I'll ask.

But why would this add a new user account, one that doesn't show up under Users and Groups?

How do I remove it as admin?

Thanks heaps.

---

### Post by Baldrick_NZ on 2011-04-08
> **Rubi1200 said:**
> Do you use remote desktop software like vino or vnc?

Nope, I have remote desktop turned off as a start-up app.

---

### Post by SeijiSensei on 2011-04-08
Maybe you wife has a child named Tommy that she's been keeping from you all these years?

---

### Post by plucky on 2011-04-09
> How do I remove it as admin?

Open Nautilus as root and navigate your way to the /tommy directory and see what it contains.Might give you a clue why it was created if it contains anything.

Otherwise just delete the directory as there is not a "tommy" user in user & groups.

Good Luck

---

### Post by Baldrick_NZ on 2011-04-09
> **plucky said:**
> Open Nautilus as root and navigate your way to the /tommy directory and see what it contains.Might give you a clue why it was created if it contains anything.

Otherwise just delete the directory as there is not a "tommy" user in user & groups.

Good Luck

Thanks Plucky, worked a treat!

I'll keep a close eye on this to see how it gets there if it return again..

---

### Post by tgalati4 on 2011-04-10
Tommy is going to be angry to find his files missing--next time he pays a visit.

---

### Post by coffeecat on 2011-04-10
> **tgalati4 said:**
> Tommy is going to be angry to find his files missing--next time he pays a visit.

:)

@Baldrick_NZ, try running Picasa and see if...

It errors out.

Or...

Tommy puts in a reappearance.

---

