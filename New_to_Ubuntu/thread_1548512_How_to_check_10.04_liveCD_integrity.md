---
title: "How to check 10.04 liveCD integrity?"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by japhyr on 2010-08-08
Hello,

The menu on the 10.04 liveCD looks different than the 8.04 cds I've been looking at for a long time.  I only see two options, to try ubuntu or to install ubuntu.  How do I check to see if the cd burned properly before installing?

---

### Post by fancypiper on 2010-08-08
Bad advice removed.

---

### Post by japhyr on 2010-08-08
I tried that, but I get an error message:
"media/cdrom0 is a directory"
Which file am I supposed to md5sum?

---

### Post by jimbop99 on 2010-08-08
Isn't there an option for that on the disk? I think when you first boot up the disk and the first splash screen comes up with the man and keyboard on it, hit any key and it will give you options.

---

### Post by japhyr on 2010-08-08
I will try that again.  I always see it using the 8.04 cds, but I didn't see it when I tried the 10.04 cd the first time.

---

### Post by oldos2er on 2010-08-08
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Ozymandias_117 on 2010-08-08
> **japhyr said:**
> I tried that, but I get an error message:
"media/cdrom0 is a directory"
Which file am I supposed to md5sum?

Usually, you would do an MD5 on the .iso before burning it. Since it's already burned, at the first purple screen, you can press esc, select your language, and select "Verify disk integrity".

If you require an MD5 on a burnt CD, first you need to figure out the exact size of the .iso (Just type "ls -l" in the directory that your .iso is) then use dd to only read that much from the CD and pipe it into md5sum:

```
dd if=/dev/cdrom bs=1 count=716185600 | md5sum
``` (That is the size for my ubuntu 10.10 32-bit CD. You will have to replace the number after count with the size of your iso)

edit: Note, this will take a while, and will not provide you with any notification that it is still running

---

### Post by japhyr on 2010-08-08
I checked the iso before burning the cd, but I like to check the cd as well.  I've had a few cd's fail, and I think it saves a lot of headaches to know that ahead of time.

I used the check function on the cd itself; I just didn't see it the first time because now it seems you need to press a key in order to see that menu.

Thanks everyone.

---

