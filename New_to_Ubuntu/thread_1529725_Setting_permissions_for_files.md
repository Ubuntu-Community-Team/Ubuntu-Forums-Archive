---
title: "Setting permissions for files"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by TekMuzik on 2010-07-12
Hello...
I'm still really bad with understanding permissions set on files, so I was wondering what command in the terminal would do the following.
Say I have a directory /example/. It has subdirectory /example/1/ and /example/2/. I want all files in /example/ and both it's subdirectories to be r/w/e for user, r/w/e for group, and --- for all others. The directories themselves I want to be r/w/e for user,group, and others.

And I already did "sudo chown -Rf user:group /example"

And no, user/group are not the actual names, just using those for examples. So I just need the permission set. Thank you.

---

### Post by endotherm on 2010-07-12
well, 777 is all permissions, and 770 is all for user and group, none for other.

the basic command would look like
```
sudo chmod -R 770 <path>
```
but you will have to go back and specifically grant the read on the folders for the other group since you want it to be different from the files.

---

### Post by TechBeastie on 2010-07-12
Consequently, while this probably isn't the cleanest solution, it should do the trick:
```
 
chmod -R 770 example/*
chmod 777 example
chmod 777 example/1
chmod 777 example/2

```

The random numbers are bitmaps, by the way, where each digit in the triad represents a "rwx" permission set (where the x permission is assigned a value of 1 or 0, the value of w is either 2 or 0, and the value of r is either 4 or 0, depending on whether or not each permission is allowed or denied).  The sevens shown above thus represent full permissions (1+2+4).

---

### Post by TekMuzik on 2010-07-12
Oh...so 7 turns on all r/w/e for that position. Thanks both you, I learned something today. :)

---

### Post by bodhi.zazen on 2010-07-12
> **TekMuzik said:**
> Oh...so 7 turns on all r/w/[s]e[/s]x for that position. Thanks both you, I learned something today. :)

Fixed that for you =)

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

For those who can not recall the numbering convention, use the lettering system

chmod u = user
chmod g = group
chmod o = other
chmod a = all

You can mix and match 

chomd ug = user and group

And the letters

chmod a+rwx == chmod 777

chomd a+x

chmod a+r

---

