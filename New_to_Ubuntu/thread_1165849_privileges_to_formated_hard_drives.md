---
title: "privileges to formated hard drives"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by nadpro on 2009-05-21
I have been haveing a huge issue with obtaining read write privileges to hard drives I just formated.  I have over come most other issues iv'e been having with ubuntu and like it so far but the fact that only root can access the drive and the user you create when you install ubuntu and the same user that created it has not rights to it at all is just frustrating and im about to throw it out the window.  I can not find any utilities that work and no straight answer to fixing the problem.  And all the other forums all go to SUDO and the terminal, I dont like the terminal and i always get a command not found!  This could be easily fixed if you could just have one user account with root privilages but no that would be to easy and now you wont feal like the uber geek that you are!  I think that this could be a great operating system and give windows a run for its money, but now i wont sujest this operating system to anyone because as soon as they hook up an external hard drive and cant access it they will call me looking for answers and most of them are computer retarted, "their words" and i cant walk them throug umpteen comands that i cant even get to work, so pleas if im just flipping out and you know an efficant way to help it would be appreciated.

---

### Post by iaculallad on 2009-05-21
Could you be more specific:

Of what filesystem did you format your hard drives?

NTFS = Try using umask

Linux Filesystem:

```
sudo chown -R username:username /media/mount_point_of_your_partition_or_drive
sudo chmod -R 777 /media/mount_point_of_your_partition_or_drive
```

?

---

