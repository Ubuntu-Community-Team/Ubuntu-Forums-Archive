---
title: "installing a new hard drive? automatic mount at boot?"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by MertTheGreat on 2010-12-22
I have just installed a new hard drive and follow this [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) tutorial. but when I try to do automatic mount at boot part which's first code is this ```
/dev/sdd1    /media/westen   ext2    defaults     0        2
```
it says ```
bash: /dev/sdd1: Permission denied
```

how can I make it work?

---

### Post by Verbeck on 2010-12-22
the line is not to be run from a terminal, its to be added to /etc/fstab
1. run the command [I]gksu gedit /etc/fstab

2. [/I]add a new line```

/dev/sdd1    /media/westen   ext2    defaults     0        2

```and save the file

3. run [I]sudo mount -a

edit:
[/I]and just to make sure you've got the correct drive id and mount point, post the output of
```
sudo blkid -c /dev/null
and
ls -l /media
```

---

### Post by MertTheGreat on 2010-12-22
> **Verbeck said:**
> could you try *sudo mount -a*

yes I can but I have to do it every time I boot my computer, I need it to do automatically

---

### Post by tajiknomi on 2010-12-22
> **MertTheGreat said:**
> yes I can but I have to do it every time I boot my computer, I need it to do automatically

[SIZE=2]When you edited your FSTAB and save, it will auto-mount the drive at boot time, you don't have to edit it again....

"sudo mount -a" is the command use to mount all the drive in FSTAB, You don't have to DID this command,once you had edit your fstab
[/SIZE]

---

### Post by Verbeck on 2010-12-22
> **MertTheGreat said:**
> yes I can but I have to do it every time I boot my computer, I need it to do automatically
if its correctly added to fstab, then it should mount at boot
also, please re-read the post, i've edited it

---

### Post by MertTheGreat on 2010-12-22
solved thank you guys

---

### Post by tajiknomi on 2010-12-22
> **MertTheGreat said:**
> solved thank you guys

[SIZE=2]You can mark the **thread-as-solved** in **thread-tools** Above[/SIZE] :p

---

### Post by amjjawad on 2010-12-22
I know it's solved but perhaps you want to have a look at this:
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

### Post by MertTheGreat on 2010-12-22
> **amjjawad said:**
> I know it's solved but perhaps you want to have a look at this:
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

nice tutorial ;)

---

### Post by amjjawad on 2010-12-22
> **MertTheGreat said:**
> nice tutorial ;)

It helped me a lot actually. I'm doing that with my NTFS partitions and I have no problems with that.

Hope it will help you too :)

---

