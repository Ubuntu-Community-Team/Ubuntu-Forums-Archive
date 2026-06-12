---
title: "Disable ipv6/enable ipv4"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by reidar4 on 2010-12-09
Hello

While trying to watch net tv using Mplayer,I get this message:"couldn't resolve name for AF_INET6.I've read this is caused by ipv6 that has got to be shut off.
Can anyone tell me step by step what to do?I dont't know much about computers.I use Ubuntu 10.04

                                                                      Best regards Reidar

---

### Post by tajiknomi on 2010-12-09
[SIZE=2]1st try this:- You need only to edit ~/.mplayer/config by adding this line:[/SIZE]
     ```
prefer-ipv4 = yes
```

[SIZE=2]if it isn't working for you.[/SIZE]..then
             
[SIZE=2]Try this>[/SIZE] [http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)

---

