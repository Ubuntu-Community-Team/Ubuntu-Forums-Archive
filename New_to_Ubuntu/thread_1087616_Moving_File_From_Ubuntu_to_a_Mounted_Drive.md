---
title: "Moving File From Ubuntu to a Mounted Drive"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by RookieUbuntuUser58 on 2009-03-05
Well one of my partition/OS is messed up (missing a file so I cant boot into it). Im able to mount and view the files of the partition through Ubuntu but it won't allow me to move the file needed to the correct section (says its read only). Its a HFS+ partition. Is there anyway I can override this and move the file through terminal or Im I SOL. Thanks in advance.

---

### Post by mike555 on 2009-03-05
Open nautilus as root , then try , if you still can't move it try copying and pasting ....

---

### Post by Brandon.Viking on 2009-03-05
You would need to see if HFS+ is mounted read-only and whether you can mount it read-write. Once that is mounted read-write then you should be able to move the file to the partition.

Hope that helps.
Brandon.

---

### Post by RookieUbuntuUser58 on 2009-03-05
> **mike555 said:**
> Open nautilus as root , then try , if you still can't move it try copying and pasting ....

Whats the code to open nautilus as a root?


> **Brandon.Viking said:**
> You would need to see if HFS+ is mounted read-only and whether you can mount it read-write. Once that is mounted read-write then you should be able to move the file to the partition.

Hope that helps.
Brandon.

How would I check if it is possible to mount it as read-write?

---

### Post by simtaalo on 2009-03-05
> **boost3d23 said:**
> Whats the code to open nautilus as a root?

```
gksu nautilus
```

---

### Post by RookieUbuntuUser58 on 2009-03-05
> **simtaalo said:**
> ```
gksu nautilus
```

Thanks.

Just tried to move it as root and still no luck. Said its only read only again.

---

### Post by Brandon.Viking on 2009-03-05
check mounted status using mount command
if its listed as ro, then its read only
unmount it 
mount it with option "-o rw"
eg. if I was to mount a partition it might look like "mount -t HFS+ /dev/sda1 /mnt -o rw

man mount gives you details on the mount command.

Hope that helps.
Regards,
Brandon.

---

### Post by RookieUbuntuUser58 on 2009-03-05
> **Brandon.Viking said:**
> check mounted status using mount command
if its listed as ro, then its read only
unmount it 
mount it with option "-o rw"
eg. if I was to mount a partition it might look like "mount -t HFS+ /dev/sda1 /mnt -o rw

man mount gives you details on the mount command.

Hope that helps.
Regards,
Brandon.

Just tried that code and it returns this:
```
mount: unknown filesystem type 'HFS+'
```

---

### Post by Brandon.Viking on 2009-03-05
hfsplus not hfs+ ... sorry

This thread might be helpful [http://ubuntuforums.org/showthread.php?t=239370](http://ubuntuforums.org/showthread.php?t=239370)

Regards,
Brandon.

---

### Post by RookieUbuntuUser58 on 2009-03-05
Tried everything mentioned so far and still no luck. I was able to mount it but whenever I put the file in it says unable to do so, read only.

---

### Post by avtolle on 2009-03-05
Did you turn off journaling as mentioned? That has to be done, as I understand it, from the OSX side.

---

### Post by RookieUbuntuUser58 on 2009-03-05
> **avtolle said:**
> Did you turn off journaling as mentioned? That has to be done, as I understand it, from the OSX side.

I cant get into OSX to turn off journaling. When I try to boot into it it says Im missing the file needed to start OSX (what Im trying to replace through Ubuntu).

---

### Post by RookieUbuntuUser58 on 2009-03-05
Wow I'm saved. Looked through Google and found a program that lets windows read/write to HFS+ partitions. Replaced the file and I can boot into OSX again.:D

---

