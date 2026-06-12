---
title: "Cannot write aurhorization file"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by RealG187 on 2009-07-23
Yesterday I was using Vista and I was reading and writing files to my Ubuntu EXT3 partition with EXD2FSD and now when I try to login it says "GDM cannot write your authorization fle...Contact your system administrator"

I hate when it says to contact the system administrator. because I am the system administrator and have no idea what the **** to do!e

EDIT: So it appears I have two kernels in my Grub
2.6.28-13 (Default)
2.6.28-11

The first time I booted I assume I went into 2.6.28-13 and that's when it said it could not write the file, the secong time I am not sure what I used but it logged in, but when I did it said I had no free space. The third time I logged it it didn't login, it said the same message. The forth time I was using 2.6.28-11 and it logged in again but still said I had no free space.

So I cannot login and when I do it says I have no free space.

---

### Post by LowSky on 2009-07-23
Actaully your not the admin, unless you use sudo/root to log in which is disabled in Ubuntu.

sounds like your file permissions change, though I'm not sure how

---

### Post by cariboo on 2009-07-23
Start in recovery mode and check the permissions of you home directory, I believe the default permissions are 755. IF the permissions have changed, type at the prompt:

```
chmod -R 755 /home/<uer name>
```

You'll get some errors about not being able to change permissions, but you should now be able to login. At the prompt type exit, then select resume to continue to the desktop.

---

### Post by RealG187 on 2009-07-23
I think it couldn't write because the disk was "full"

I restarted and tried logging in again and it did for some reason, but it says I have 0 bytes free even though  have more than that. I even deleted some files and the free space did not go up...

I think there is a problem with the reported free space not being the actual freespace, is there a way to fix this?

---

### Post by llamabr on 2009-07-23
Try:

```
sudo apt-get clean
```

Then, look around your home directory for some stuff to delete.  If you can't find anything big, try using the 

```
df -h
``` 

command.

---

### Post by RealG187 on 2009-07-23
> **llamabr said:**
> Try:

```
sudo apt-get clean
```

Then, look around your home directory for some stuff to delete.  If you can't find anything big, try using the 

```
df -h
``` 

command.The problem isn't that I don't have free space, it's that I do, but it says I don't.

I am in Vista now and it reports 3.44 GB free (It's a big hard drive, just full, but not so full there is no space left)

---

### Post by RealG187 on 2009-07-24
I ran fsck in recovery mode and it is still doing this and now I cannot log in again. Everytime  I try to login it says that, except the second time, but when I did login it said I had no free space.

---

### Post by llamabr on 2009-07-25
> **RealG187 said:**
> The problem isn't that I don't have free space, it's that I do, but it says I don't.

I am in Vista now and it reports 3.44 GB free (It's a big hard drive, just full, but not so full there is no space left)

I'm not sure why you think you do, when it says you don't.

---

### Post by RealG187 on 2009-07-26
> **llamabr said:**
> I'm not sure why you think you do, when it says you don't.
I know I have free space because I didn't put enough data on to fill it up. Vista still detects my free space. Even if I delete files to make more space it still says I have 0 bytes free, which is wrong because deleting 100 MB would make 100 MB free...

---

