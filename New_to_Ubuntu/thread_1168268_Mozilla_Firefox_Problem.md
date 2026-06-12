---
title: "Mozilla Firefox Problem?"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-05-23
Today when i started Firefox and i got this error "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsIStringBundle.formatStringFromName]"

What may have caused this and how to solve this

---

### Post by Kareeser on 2009-05-23
It [sounds like either a problem](http://ubuntuforums.org/showthread.php?t=873586) with one of your add-ons, or a permissions problem with your ~/.mozilla folder.

Can you run this for me, and reply with the output?
```
ls -ld ~/.mozilla
ls -l ~/.mozilla
```

---

### Post by ravi_buz on 2009-05-23
Thanks fr the reply ,And here is the output
ravi@ravi-desktop:~$ ls -ld ~/.mozilla
drwx------ 5 ravi ravi 4096 2009-05-17 09:03 /home/ravi/.mozilla
ravi@ravi-desktop:~$ ls -l ~/.mozilla
total 12
drwx------ 3 root root 4096 2009-05-17 12:05 eclipse
drwx------ 4 ravi ravi 4096 2009-05-23 18:52 extensions
drwx------ 3 ravi ravi 4096 2009-05-15 20:00 firefox
ravi@ravi-desktop:~$ 



I got this problem after installing some addons(dont remember wat it was)

---

### Post by asmoore82 on 2009-05-23
> **ravi_buz said:**
> Thanks fr the reply ,And here is the output
ravi@ravi-desktop:~$ ls -ld ~/.mozilla
drwx------ 5 ravi ravi 4096 2009-05-17 09:03 /home/ravi/.mozilla
ravi@ravi-desktop:~$ ls -l ~/.mozilla
total 12
drwx------ 3 [COLOR="Red"]root root[/COLOR] 4096 2009-05-17 12:05 eclipse
drwx------ 4 ravi ravi 4096 2009-05-23 18:52 extensions
drwx------ 3 ravi ravi 4096 2009-05-15 20:00 firefox
ravi@ravi-desktop:~$ 



I got this problem after installing some addons(dont remember wat it was)

[COLOR="Red"]This[/COLOR] looks out of place ...
```
sudo chown -R ravi:ravi ~/.mozilla
```

---

### Post by ravi_buz on 2009-05-23
Problem solved,Thank u so much :KS:KS

---

