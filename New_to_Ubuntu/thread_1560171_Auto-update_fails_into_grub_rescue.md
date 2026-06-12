---
title: "Auto-update fails into grub rescue"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by mr.grimlock on 2010-08-24
Hi all.  I have seen similar problems, but nothing that exactly matches my issue.

I had windows XP on one drive and decided to try ubuntu on my second drive.  Used Wubi and it all worked perfectly.  Booted into XP then Ubuntu via the boot choices and was offered an auto-update, which I selected.

When all updates were downloaded it rebooted my machine and now it goes into
grub rescue having stated
error: no such device and a batch of hex chars.

I have a very limited set of commands in grub which include
ls
insmod (which wouldn't work, but was present)


unknown command when I try
root
exit
sudo
setup
cd
find
help


When I do LS I get
(hd0) (hd1)
if I LS (hd0) or LS (hd1)  I get
error: unknown filesystem


I can't get into XP now or Ubuntu.  Using an XP boot disc, I managed to get to my xp files and they are all there, but I just have no way to boot to either OS.

Could anyone make any suggestions please?

Many thanks

---

### Post by bcbc on 2010-08-24
> **mr.grimlock said:**
> Hi all.  I have seen similar problems, but nothing that exactly matches my issue.

I had windows XP on one drive and decided to try ubuntu on my second drive.  Used Wubi and it all worked perfectly.  Booted into XP then Ubuntu via the boot choices and was offered an auto-update, which I selected.

When all updates were downloaded it rebooted my machine and now it goes into
grub rescue having stated
error: no such device and a batch of hex chars.

I have a very limited set of commands in grub which include
ls
insmod (which wouldn't work, but was present)


unknown command when I try
root
exit
sudo
setup
cd
find
help


When I do LS I get
(hd0) (hd1)
if I LS (hd0) or LS (hd1)  I get
error: unknown filesystem


I can't get into XP now or Ubuntu.  Using an XP boot disc, I managed to get to my xp files and they are all there, but I just have no way to boot to either OS.

Could anyone make any suggestions please?

Many thanks
boot the xp disc to a repair command prompt and run:
```
fixmbr
```

(This puts back the windows bootloader in the MBR). This is the bug report if you are interested:[https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)

---

### Post by mr.grimlock on 2010-08-24
brilliant!  Worked within seconds.  I presume I now reload wubi and Ubuntu install?

Thanks very much for your help :-)

---

### Post by bcbc on 2010-08-24
> **mr.grimlock said:**
> brilliant!  Worked within seconds.  I presume I now reload wubi and Ubuntu install?

Thanks very much for your help :-)

You're welcome. Wubi should work perfectly as before. No need to reinstall

---

### Post by mr.grimlock on 2010-08-24
I was going to leave this til tomorrow, but as you seem so confident I tested it now.  You are perfectly correct.  Thanks again and again! :-)

---

