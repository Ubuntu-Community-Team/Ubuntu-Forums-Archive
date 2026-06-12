---
title: "Bootloader problem"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by Sushil Bhingardive on 2010-02-08
installed WinXP on 1st primary partition,openSUSE on 2nd primary partition along with its bootloader and Ubuntu on 2nd logical partition(Extended)..but i didnt installed Ubuntu's bootloader at the time of Ubuntu's installation.
At present GRUB of SUSE shows me Windows XP and openSUSE option but doesnt show Ubuntu,
please do help to install ubuntu's bootloader explicitly without reinstalling Ubuntu on its own partition.

---

### Post by blazemore on 2010-02-08
Please post the output of running the command:
```
sudo fdisk -l
```

Thanks!

---

### Post by Grenage on 2010-02-08
Thankfully it's a simple task, so we won't need to spoon feed you through it. ;)

Reinstall Grub2; a quick 'Google' of that and you'll get the few commands needed.

---

### Post by blazemore on 2010-02-08
```
sudo apt-get install --reinstall grub2
```

---

