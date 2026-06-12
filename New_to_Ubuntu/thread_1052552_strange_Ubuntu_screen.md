---
title: "strange Ubuntu screen"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Jack Shankle on 2009-01-27
My system is a triple boot system. Vista, another OS and Ubuntu.
I can boot to Vista, the other OS and Ubuntu for a short period.
I get the logon window and the sliding orange bar for about 10 seconds and then I get the following (see attachment) screen and it hangs there. Sorry for the blurry picture but I think you can see enough to get some meaning from it.
Thank you for any help.

---

### Post by Jack Shankle on 2009-01-28
Please won't someone give me a hand with this.
I'm stuck.

1% Ubuntu working on 2% Ubuntu.
Thanks for any help.

---

### Post by philinux on 2009-01-28
Looks like fsck (the disk checker) is having a tantrum.

Reboot and press esc at the grub menu. Choose the second item down, recovery mode. At the menu choose fsck.

---

### Post by Jack Shankle on 2009-01-30
Thank you Philinux for responding.
I did the fsck thing and I'm getting different results but nowhere
what it should be.
I reinstalled Ubuntu. I can boot into it but then I get the black screen with the following:
    loading new partition
    cannot load from harddisk
    Insert System Disk and hit any key

If I hit enter it takes me back to the boot choice screen.
This is a triple boot setup. Windows, another OS and Ubuntu.
I'm beginning to think that Ubuntu is beyond my capabilities.
1% Ubuntu working on @% Ubuntu

---

### Post by sirebral on 2009-01-30
is that really as clear as the picture can be?  It looks doubled up for some reason.

---

### Post by Jack Shankle on 2009-01-30
Not being a photographer I couldn't get a better picture.
Thought someone could get the general idea from it. I shouldn't be
seeing it at all.

---

### Post by hyperhopper on 2009-01-30
> **sirebral said:**
> is that really as clear as the picture can be?  It looks doubled up for some reason.
is your avatar as clear as it can be? It looks doubled up for some reason.

---

### Post by Jack Shankle on 2009-01-30
So I gather from the answers that I am on my own.........

---

### Post by Gulyan on 2009-01-30
Try to post the content of the file /boot/grub/menu.lst here

---

### Post by Jack Shankle on 2009-01-30
The problem is now solved................

---

