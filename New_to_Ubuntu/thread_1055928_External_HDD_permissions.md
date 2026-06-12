---
title: "External HDD permissions"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by methodmarvel on 2009-01-31
I have just formatted my western digital external hard drive 300GB to ext3 using gparted. I have two questions:

1 - I don't seem to have any permissions over the disk as my normal user and need to be root - How do I change the permissions of the disk so they are similar to the home folder's level of permissions for a normal user?

2 - Is it ok that it is all one partition or are there drawbacks to this?

Thanks

---

### Post by taurus on 2009-01-31
1.  Since it's an ext3, you can change the ownership of the mount point for that drive from root to your login name.  Then, you can write to it anytime you want without using sudo/gksudo.  

Assuming your login name is method and the drive is mounted to /media/sdb1, you would do

```
sudo chown -R method:method /media/sdb1
ls -la /media
```

2.  One partition to take up the whole disk is fine.

---

### Post by methodmarvel on 2009-01-31
> **taurus said:**
> 1.  Since it's an ext3, you can change the ownership of the mount point for that drive from root to your login name.  Then, you can write to it anytime you want without using sudo/gksudo.  

Assuming your login name is method and the drive is mounted to /media/sdb1, you would do

```
sudo chown -R method:method /media/sdb1
ls -la /media
```

2.  One partition to take up the whole disk is fine.

Awesome - that seems to work perfectly

Just for my learning: 

chown is to change the owning group/user

This is shown by the method:method where it is user:group

-R option makes the action recursive

And /media/sdb1 is the location of the action

That sound about right? I was googling the chown command

---

### Post by taurus on 2009-01-31
> **methodmarvel said:**
> Awesome - that seems to work perfectly

Just for my learning: 

chown is to change the owning group/user

This is shown by the method:method where it is user:group

-R option makes the action recursive

And /media/sdb1 is the location of the action

That sound about right? I was googling the chown command

That sounds perfect.  No need to googling around.  Just read the manpage.

```
man chown
```

---

### Post by methodmarvel on 2009-01-31
> **taurus said:**
> That sounds perfect.  No need to googling around.  Just read the manpage.

```
man chown
```

Thanks

I can't seem to make the thread as solved or "thank" you though.

---

### Post by taurus on 2009-01-31
Here's the announcement from ubuntu-geek regarding those options.

[http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)

---

