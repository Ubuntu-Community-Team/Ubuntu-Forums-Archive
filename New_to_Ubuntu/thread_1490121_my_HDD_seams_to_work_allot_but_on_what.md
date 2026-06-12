---
title: "my HDD seams to work allot but on what?"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by outlaw45k on 2010-05-21
i hear my hdd working like mad but i dont know on what 
is there a way too see the number of reads for a specific folder ?
iostat -d show e this 
```
Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
fd0               0.00         0.01         0.00         16          0
sda               0.03         0.28         0.00        604          0
sdb              72.61       525.26       749.39    1153521    1645728
sdc               0.19         1.91        31.96       4196      70176

```

---

### Post by earthpigg on 2010-05-21
what is on sdb?

---

### Post by mixmastamyk on 2010-05-22
Perhaps you don't have enough ram, causing use of virtual memory.  Or there is a process busy on io, try the top command to find out.

Try closing all open applications and opening one at a time.  A reboot might also alleviate the issue.  If the culprit is a busy daemon you could disable it, if it isn't needed.

Hard to tell exactly without more details, perhaps a df command.

---

### Post by The Eight-Bit Link on 2010-05-22
Another answer is probably not one you want to hear. My laptop does the same thing. It will all of a sudden seem like its looking furiously for something. This is because the harddiskdrive has contracted the click of death. It doesn't always click, but it sounds and operated like it's looking for something.

---

### Post by outlaw45k on 2010-05-22
> **earthpigg said:**
> what is on sdb?
ubuntu nothing more

> **mixmastamyk said:**
> Perhaps you don't have enough ram, causing use of virtual memory.
i got 2 gb of ram 

what you mean top command ?

> **The Eight-Bit Link said:**
> Another answer is probably not one you  want to hear. My laptop does the same thing. It will all of a sudden  seem like its looking furiously for something. This is because the  harddiskdrive has contracted the click of death. It doesn't always  click, but it sounds and operated like it's looking for  something.

atm is not doing this anymore, restarted the PC and dint run any app just he log in

---

### Post by Skorzen on 2010-05-22
outlaw45k, actually 'top' is a GNU/Linux command. ;-)

---

### Post by Nythain on 2010-05-22
sudo apt-get install htop

ftw

top/htop = incredible ncurses based (at least htop is i believe) command line system monitor tool... will list process, memory consumption, cpu consumption, think you can have it tell you i/o rates, all that jazz... might help you figure out whats being run when the hdd starts going crazy

---

### Post by outlaw45k on 2010-05-24
i dont know how and why but the sound made by hdd is gone even if i actually i made the HDD work on something

---

