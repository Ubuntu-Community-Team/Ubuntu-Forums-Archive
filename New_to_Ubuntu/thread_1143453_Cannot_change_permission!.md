---
title: "Cannot change permission!"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-04-29
For some reason, the permission on my microSD card changed to read-only and I cannot change it. Here's the error message I get:

Sorry, could not change the permissions of "R4 #2": Error setting permissions: Read-only file system

I tried using chmod 775 but it doesn't work either

```
 sudo chmod 775 ../../media/R4\ #2/
[sudo] password for sylvainrb:
chmod: changing permissions of `../../media/R4 #2/': Read-only file system
```

How can I change it so I can copy & paste again? Thanks!

PS: It works fine in Windows!

---

### Post by x33a on 2009-04-29
did you unmount it properly from windows? sometimes, that causes problems.

---

### Post by steve101101 on 2009-04-29
> **x33a said:**
> did you unmount it properly from windows? Sometimes, that causes problems.

+1

---

### Post by sylvainrb on 2009-04-30
> **x33a said:**
> did you unmount it properly from windows? sometimes, that causes problems.

The problem happened before I went to try it on Windows to see if it was working at all.

Also I erased all the files that were on the microSD before the permission was changed automatically. Could it be the reason why?

Would formatting it under Windows fix it? (I'm not sure how to format in Ubuntu hehe)

Thanks...

---

### Post by masterkoppa on 2009-04-30
> **sylvainrb said:**
> The problem happened before I went to try it on Windows to see if it was working at all.

Also I erased all the files that were on the microSD before the permission was changed automatically. Could it be the reason why?

Would formatting it under Windows fix it? (I'm not sure how to format in Ubuntu hehe)

Thanks...
The software used for formating is called gparted. You can download it though synaptic or apt-get

---

