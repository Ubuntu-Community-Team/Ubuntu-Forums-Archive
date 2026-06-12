---
title: "Why do rsync want to move this file?"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by Frozen Forest on 2011-08-19
I would like to synchronize some photos between two computers, but for some reason do rsync see these two files as different.
```

-rwxrwxrwx 1 remoteA remoteA 598720 2009-05-17 20:15 Pictures/06/06/P01.JPG
-rw------- 1 localB localB 598720 2009-05-17 20:15 Pictures/06/06/P01.JPG

```

Rsync command used.
[PHP]
rsync -rtlu --progress --dry-run --modify-window=10
[/PHP]

---

### Post by papibe on 2011-08-19
Maybe they are different? Try getting their md5sum.

Regards.

EDIT: or have different seconds timestamps. Remember that using --modify-window=10 will relax the time comparison (10 secs).

---

### Post by Frozen Forest on 2011-08-19
> **papibe said:**
> Maybe they are different? Try getting their md5sum.

Regards.

EDIT: or have different seconds timestamps. Remember that using --modify-window=10 will relax the time comparison (10 secs).

Thanks for the tip, but strangle enough is the md5sum the same. Might there maybe be something wrong with the command I use?

Command used
[PHP]
rsync -rtlu --progress --dry-run --modify-window=100 -e "ssh -i .ssh/id_rsa -p 222222 dator@22.22.22.22" Pictures/06/06/ remoteA@22.22.22.22/home/remoteA/Pictures/06/06/
[/PHP]

---

### Post by papibe on 2011-08-19
Did you check the Access/Modify/Change time in seconds on those files? 
Try this for both copies:
```
$ stat Pictures/06/06/P01.JPG
```
Regards.

---

### Post by Frozen Forest on 2011-08-19
> **papibe said:**
> Did you check the Access/Modify/Change time in seconds on those files? 
Try this for both copies:
```
$ stat Pictures/06/06/P01.JPG
```Regards.

Now we are getting somewhere :)

The following are diffrent:
Access # write permission 777 and 0600
Uid # user name
Access # file accessed date
Changed # file changed date this might be causing it? possible to ignore?

EDIT:
It might be that I missing something very basic, but when the file name is shown is an indication that a file will be transfered, right? At at lest how I work when using rsync between two folders on a single computer

EDIT2:
Size only worked

---

