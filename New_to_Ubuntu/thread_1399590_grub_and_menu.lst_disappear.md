---
title: "grub and menu.lst disappear"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by jvofvnopz on 2010-02-05
hi,
i have just reinstalled ubuntu 9.10 (because i ended up botching some settings and removing myself from the sudoers list). i formatted the partition where the old ubuntu 9.10 was installed, and then reinstalled on the empty partition (using the livecd's partitioner). 

however, when i turn on the computer, it says "grub is loading..." for a split second and it never shows up. i wouldn't need to even use the grub menu, except there are a few important programs that i need to boot into windows for (and i have too little ram to virtualize). i browsed the forums for help, and i tried "sudo update-grub",and i get no error messages, but grub doesn't return. i have also tried "sudo gedit /boot/grub/menu.lst", but the file is empty! how can i regenerate the menu.lst file?

---

### Post by Mr Nemo on 2010-02-05
So Ubuntu loads right after it says grub is loading? 9.10 does not use menu.lst anymore. To modify grub you need to edit the files in /etc/grub.d. Then use sudo update-grub.

[http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)   this link should help. explains how to hide/unhide the grub menu at boot.

---

### Post by pdlethbridge on 2010-02-05
Can you change a setting in Start up manager for that? Timeout can be adjusted for a few more seconds

---

### Post by jvofvnopz on 2010-02-06
now grub loads, but windows is absent from the list (even though i did not format the windows partition (partition #6) ) and i installed on the correct drive

---

### Post by theozzlives on 2010-02-06
Try bootin off the live CD, go to terminal and try:
```
sudo -i
mount /dev/sdax /mnt
install-grub /mnt/ /dev/sda
```
Boot into Ubuntu and do:
```
sudo update-grub
```
oh, the x after sda is your / partition

---

### Post by jvofvnopz on 2010-02-06
so to clarify, would sdax be my windows partition (/dev/sda5) or my ubuntu partition (/dev/sda6)?

---

### Post by theozzlives on 2010-02-06
> **luolimao said:**
> so to clarify, would sdax be my windows partition (/dev/sda5) or my ubuntu partition (/dev/sda6)?

If sda6 is your Ubuntu, then it's sda6 (don't do your Windows partition).

---

### Post by jvofvnopz on 2010-02-06
> **theozzlives said:**
> Try bootin off the live CD, go to terminal and try:
```
sudo -i
mount /dev/sdax /mnt
install-grub /mnt/ /dev/sda
```Boot into Ubuntu and do:
```
sudo update-grub
```oh, the x after sda is your / partition

1. i tried it, and it said "install-grub: command not found"
2. is this to install grub, or to put my windows partition back on the grub menu? because the solution that told me to edit the /etc/grub.d file worked fine for displaying grub
3. how do i get my windows partition back on the grub menu?

---

