---
title: "How to localise terminal to another partition"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by Trandok on 2010-11-28
I recently installed a plethora of operating systems and also LILO, so I could boot them all up. I messed up the ubuntu part in my lilo.conf but I was able to repair it using the Live CD. 

Here comes the problematic part: in order to implement the changes, I need to execute lilo in terminal, but right now anything I do in terminal is related to the Live CD's filesystem. Of course I can change the directories and all, but all terminal commands are dependent on its master filesystem(or partition) so it is unable to make any changes on the mounted partition and starts erroring me about missing files etc.

Is there any way I could apply terminal to a specific partition or mounted media, so that all the commands I enter are run and utilised on that partition?

---

### Post by bioterror on 2010-11-28
Here it goes:

> chroot /media/your-another-installation/ /bin/bash

---

### Post by Trandok on 2010-11-29
Looks like it works, at least I got another error.

```
root@ubuntu:/# lilo
Fatal: raid_setup: stat("/dev/sda")
```

Any bulbs lighting up?

---

