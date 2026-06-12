---
title: "Samba share permissions (no write access)"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by lordgibbness on 2006-11-22
Can anyone fathom out why the following mounted samba share won't allow anyone except root to have write access to my uploads folder.

/etc/fstab
```
//windowspc/uploads /mnt/uploads smbfs username=user,password=pass,users,rw,gid=samba-users 0 0
```

I have tried many different variations of the line above - using umasks etc. I only recently added the gid option as I read that this would allow users in that group write access.

When the share is mounted the directory looks like this.
ls -l
```
drwxr-xr-x 1 root samba-users 4096 2006-11-22 23:00 uploads
```

As you can see only root has write permissions. And chmod won't change them.

Any ideas how I can make a bunch of users on my ubuntu system able to write to the share?

Thanks.

---

### Post by awbassett on 2006-11-22
What I do to get around this is to create a group specifically for system users who need to write to the mount. Add the users to this group and change the line in /etc/fstab to resemble something like this:

//windowspc/uploads /mnt/uploads smbfs username=user,password=pass,gid=samba-write-users 0 0


This website has some useful information:
[http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently](http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently)

---

### Post by awbassett on 2006-11-22
Also, note that if you have multiple users on your machine, it's not a good idea to put your windows credentials in /etc/fstab. Utilize the instructions for a credentials file from the link in the previous post.

---

### Post by lordgibbness on 2006-11-23
> **awb4422 said:**
> What I do to get around this is to create a group specifically for system users who need to write to the mount. Add the users to this group and change the line in /etc/fstab to resemble something like this:

//windowspc/uploads /mnt/uploads smbfs username=user,password=pass,gid=samba-write-users 0 0


This website has some useful information:
[http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently](http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently)

That's exactly what I already have in my fstab.

In the end I had to add dmask and fmask entries to make it work. Is this the only way to do it?

---

### Post by awbassett on 2006-11-23
not entirely - you had 'users,rw' in your fstab line. 

Are you adding users to the group, and can you post your fix so other people can see what you did?

---

### Post by lordgibbness on 2006-11-24
I did add the users to the group. I may try removing "users,rw" when I get home tonight and see if that makes a difference.

However, for now, this is the line that I have in my fstab file that appears to work as I wanted.

```
//windowspc/uploads /mnt/uploads smbfs username=user,password=pass,users,dmask=777,fmask=777 0 0
```

I will do some more testing around this and see what I find...

Edit: On my system it seems that only the line above using dmask and fmask give me permissions to read and write to a shared folder. Now to put my user/pass in a credentials file...

---

### Post by diverjustjim on 2006-11-24
I had similar problems and the following solved it,

sudo chmod a+wrx dirname

Jim

---

### Post by lordgibbness on 2006-11-25
From what I have seen the fstab permissions seem to take precedance to anything you set on the folder yourself. For example I gave the folder 777 permissions, but when I mounted it, it reverted back to 755 automatically, which is why I had to the the fmask and dmask options to the fstab file.

---

### Post by amr2205 on 2006-12-06
Thanks! It was a really headache to get it work, but with your help it does.

---

