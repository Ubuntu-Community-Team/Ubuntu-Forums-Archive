---
title: "A few questions about ramdisk"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by inukai on 2011-02-26
Hello all, 
I am new to the Linux/Ubuntu scene and so far I am loving it. I'm using 10.10 Maverick Meerkat. My questions involve two ramdisk file systems that I have on my comp. One is set to be created on startup by modding /etc/fstab and adding this line to the bottom

```
tmpfs /var/ramdisk2      tmpfs defaults,size=100M                 0 0
```

The other is created in a .sh when I launch the script and it uses this line

```
sudo mount -t tmpfs /var/ramdisk /var/ramdisk -o size=500M
```

My questions should be simple. How can I tell beyond a shadow of a doubt that these lines are working properly and actually mounting the folders into my RAM and not just mounting the folders to my HDD as separate file systems, like mounting a CD or Flash Drive. 

Also, with the .sh script I have some lines that, on startup, copy everything from a folder into ramdisk and when the program exits copy everything from ramdisk back to that folder, and I just want to see if the code is right. The copying back shouldn't happen until the application closes. I'm replacing the path to the backup with "backup" and the path to ramdisk with "ramdisk"

```
cp -r "backup" "ramdisk"
Program runs
cp -r "ramdisk" "backup"

```

Also if someone could show me how to modify this so it backs up every 5 mins or so, that'd be great. Thanks and sorry this is such a long post, I've tried looking online for this but these were the questions I couldn't find.

---

### Post by inukai on 2011-02-26
And yes, I do have a umount command at the end of the .sh if it's important to mention.

---

### Post by inukai on 2011-02-28
Bump?

---

