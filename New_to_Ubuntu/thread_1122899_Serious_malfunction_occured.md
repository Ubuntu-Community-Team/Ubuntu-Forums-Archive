---
title: "Serious malfunction occured"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by shreyanshjain8 on 2009-04-11
i wanted to to do a force check on restarting my ubuntu ..
so i runned the following script in root shell...

# init 1
# umount /dev/sda8
# fsck /dev/sda8
# fsck -t ext3 /dev/sda8
# mount /home
# init 3


..................................

and after this when i rebooted my system.. it gave an error messages on boot screen stating that..

init event/ ctrl+alt+del not found
init event/tt1 not found
intin event/tt2 not found.... (i don remember exactle but it was giving some error messages like this)

please help me out...
i am unable to access my ubuntu..

---

### Post by shreyanshjain8 on 2009-04-11
please help me .. its urgent..
as i m unable to access anything... just able to see those erroe messages only...

---

### Post by xir_ on 2009-04-11
if its urgent to get something off you pc use the live cd and mount the file system then at least you might be able to get the files that you need.

You may even be able to remove the script

---

### Post by shreyanshjain8 on 2009-04-11
please help me to return in my original boot .. so that i can access ubuntu again.....

---

### Post by xir_ on 2009-04-11
right well to me and my limited knowledge you have messed up the the init demon. Firstly if you can't get access to the terminal via the usual channels then you will likely need a live cd.

Once you have the live cd in mount the file system then look for the file that you install and sudo remove it. Reboot the system without the live cd installed.

If the script hasn't caused any damage to the system then it should boot up as usual.

Do you have a live cd available?

---

### Post by shreyanshjain8 on 2009-04-11
yes sir i have a live cd...

i checked my linux filesystem from vista in my system..

there i found that in my etc/event.d ... the required tty1, tty2  and all those files are missing.. thats why it is unabel to boot..
how to corect that...

---

### Post by RetchingRabbit on 2009-04-11
> **shreyanshjain8 said:**
> 
i checked my linux filesystem from vista in my system..


Wow. I'd LOVE to hear how you pulled that off...

---

### Post by mgranet on 2009-04-11
In the future, you can just run the following command to force check on next reboot: ```
sudo tune2fs -c 1 /dev/sda8
```
When you've rebooted, reset the value to how ever many boots you want before a recheck with the same command, substituting 1 with the number of boots you want.

---

