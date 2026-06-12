---
title: "How to encrypt full disk?"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by sarc on 2010-11-27
Hello I am using home directory encryption in ubuntu 10.04 but from web search I undersand that it's not possible to encrypt root therefore accessed files list and other info could be readily accessed. I am running Ubuntu from USB disk (no hardware encryption) can anyone suggest a way to encrypt the whole disk (still making it bootable) or how to secure / directory?

p.s. How important is it to encrypt swap directory?

Thanks

---

### Post by sandyd on 2010-11-27
encrypt the entire disk using truecrypt

[http://www.truecrypt.org](http://www.truecrypt.org)
[http://www.truecrypt.org/docs/?s=rescue-disk](http://www.truecrypt.org/docs/?s=rescue-disk)
[http://ubuntuforums.org/showthread.php?p=4287308](http://ubuntuforums.org/showthread.php?p=4287308)

---

### Post by sarc on 2011-01-06
Thanks Sandyd... but I understand from your link that this would not work:
"Note that with linux installed you can only encrypt the windows partition and not the whole drive, because Linux cannot yet root itself when encrypted with TC like that."

My USB disk is Linux only (and file system is ext4...) thence my problem...

---

### Post by ezsit on 2011-01-06
In order to encrypt an entire disk, you will need to do so at install time and using the alternate cd, not the desktop cd. The text-based installer on the alternate cd has the option to encrypt the entire disk I believe.

---

