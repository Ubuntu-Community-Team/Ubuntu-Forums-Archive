---
title: "Only Root can unmount"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by Slush8 on 2011-06-16
Hi Guys,
I need some help, I am really stupid and not a computer person.  My hard drive won't mount, keeps coming up with the same error about root has to remount.   I know it still sees it as I have checked on disc utility and also have checked that it is working.  I have looked throu the forums and tried everything suggested.   Any help would be welcome, please keep it very simple.   Thank you.

---

### Post by Slush8 on 2011-06-16
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

### Post by sanderd17 on 2011-06-16
I don't really understand your problem.

It's about an external hdd right? What happens when you plug it in? Do you see it appearing in the file manager? Do you get a popup? When do you get the message "root has to remount"?

---

### Post by dcsoldschool53 on 2011-06-16
> **Slush8 said:**
> Hi Guys,
I need some help, I am really stupid and not a computer person.  My hard drive won't mount, keeps coming up with the same error about root has to remount.   I know it still sees it as I have checked on disc utility and also have checked that it is working.  I have looked throu the forums and tried everything suggested.   Any help would be welcome, please keep it very simple.   Thank you.

With the drive connected to your PC, in a terminal, type```
sudo blkid
```I want to see if your drive has a name. And```
sudo fdisk -l
```to see how big is the drive

---

