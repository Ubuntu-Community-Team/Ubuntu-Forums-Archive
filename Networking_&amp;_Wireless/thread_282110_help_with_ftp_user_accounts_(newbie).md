---
title: "help with ftp user accounts (newbie)"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by jeckil on 2006-10-22
Hello all!

I am trying to create a ftp fileserver for various users but i am having trouble restricting users to specific folders.

My desired disk setups (i hope it makes sense)

disk1 <main> (ubuntu running here)
disk2 <private>
disk3 <all public>
disk4 </users/public> (only this specific folder)
disk5 <all public>
disk6 <all public>

I mount all the drives on /mnt such as:
```

/mnt/disk1
/mnt/disk2
/mnt/disk3
/mnt/disk4
/mnt/disk5
/mnt/disk6

```
I am using samba with user accounts (disabled public usage)

This is my main problem related to vsftp:

when creating links such as ln /mnt/disk3 for ftp users they will only work when the chroot jail is at NO.

the problem with this setup is that when the ftp user logs in, follows the link and then tries to go back to the root ftp folder it basically bumps him into /

such as:

**<root ftp dir>**```

.
..
disk2    <-created by (ln -s /mnt/disk2 disk2)

```
if user types 'cd disk2' and then 'cd..' the user ends up at

/mnt/ instead of **<root ftp dir>**

Now, if i turn on chroot jail on vsftpd.conf such as

/etc/vsftpd.conf 
```

chrool_local_user = YES

```

the links created become useless for some reason.

can someone please suggest stategies on how to control this behavior? are there any links outhere that can guide me on this topic? 

I am using vsftp but i am open to switching (preferably not)

Thanks a lot for all of your help on this

regards
jeckil

---

