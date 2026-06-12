---
title: "Fstab - mount folder caption with spaces"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by pinsky on 2009-01-28
Hy

I've just set up my USB disk to auto-mount at startup. It mounted itself before that only when i accessed it manually, and I whanted it to be mounted the whole time, so i don't have to access it every time i want my music playlist to be avalible. 

That is not the topic actually. The thing is, whent it mounted itself (like in the upper example) , the hard was mounted to a folder named "My book", so the name contained spaces. 
When i was setting it up in fstab, i mounted it to a folder Mybook.

I didn't want to risk writing My book, because i thought that then the system whould see "book" as the <type> parameter.

Was that a correct assumption, if so, how do you add a folder that contains spaces?


tnx

---

### Post by capnthommo on 2009-01-28
hinthere,  i don't know if this is right or not - i'm sure if not then others will correct me.  but might it work like you want if you added an underscore as in (My_book)?  afraid i cant tell you how to do this but perhaps that would be the correct syntax?  sorry i can't be more help but i'm pretty new here.
like i said, don't take this as gospel - it's only a suggestion.
good luck
nigel

---

### Post by cubeist on 2009-01-28
I am pretty sure you denote space in a similar fashion to a terminal session with a backslash, like so:
```

My\ book/
```

after using unix/linux for a while you get into the habit of never using spaces for naming...not sure if this is a good thing or not!

Hope this works

---

### Post by Denestria on 2009-01-28
You create the space character in fstab with **\040**

This is a samba shared network folder called "Shared Media".  The \040 represents the space between Shared and Media.

```
//192.168.10.194/Shared\040Media /media/warthog/shared
```

---

### Post by kk0sse54 on 2009-01-28
You  can try to wrap quotations around it. For example ```
/media/"My Book"
``` test it out by entering in the terminal ```
sudo mount /dev/sd(whatever the drive is) /media/"My Book"
```

---

### Post by cubeist on 2009-01-28
> **Denestria said:**
> You create the space character in fstab with **\040**

This is a samba shared network folder called "Shared Media".  The \040 represents the space between Shared and Media.

```
//192.168.10.194/Shared\040Media /media/warthog/shared
```

Thank You! I'll bookmark this for future reference

---

### Post by pinsky on 2009-02-02
I've edited the fstab, but i didn't quite work the way i wanted. 
I added a new line in fstab :

> /dev/sdc1       /media/My\040Book/     vfat   auto,user   0   0

I've checked with fdisk, the disk I want to mount is definitely sdc1. What i get as a result is "My disk" folder (the icon is like a hard drive with the USB sing in an orange circle). But when i access it it's empty.

Then again, sometimes the disk mounts itself automatically and I get two same looking ikons on the desktop.

Any suggestions?

---

### Post by Denestria on 2009-02-02
Because it is a USB device it isn't always being connected as /dev/sdc1.  Mount it with the UUID.
With the drive plugged in:
```
ls -la /dev/disk/by-uuid/
total 0
drwxr-xr-x 2 root root 140 2009-02-02 12:17 .
drwxr-xr-x 5 root root 100 2009-01-31 13:45 ..
lrwxrwxrwx 1 root root  10 2009-02-02 12:17 **0072-1536** -> ../../sdb1

```

This is my USB thumb drive.
Then edit fstab to use UUID=**0072-1536**

```
UUID=**0072-1536**  /media/My\040Book/ vfat auto,user 0 0 
```

---

