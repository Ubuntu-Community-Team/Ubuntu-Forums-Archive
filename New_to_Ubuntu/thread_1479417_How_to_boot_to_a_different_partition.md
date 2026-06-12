---
title: "How to boot to a different partition?"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by camn on 2010-05-10
I recently partitioned my HD and installed Windows 7... But it will only let me boot to Windows... How do you boot into another OS/partition?

---

### Post by mikewhatever on 2010-05-10
Reinstall Grub, the Ubuntu boot loader.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by camn on 2010-05-10
> **mikewhatever said:**
> Reinstall Grub, the Ubuntu boot loader.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Umm... I can't get on my Ubuntu partition at all to do that... Is there another way?

---

### Post by wilee-nilee on 2010-05-10
> **camn said:**
> Umm... I can't get on my Ubuntu partition at all to do that... Is there another way?

mikewhatever's link is perfect you have to boot from a live Ubuntu CD to do this step 11 which the link goes straight to is what you want and the only way to reload the MBR with grub, that I know of. If you have any questions go to the live cd run sudo fdisk -l and post the results while still on the live cd I or somebody else will help you out, by the way l= a small case L.

---

### Post by camn on 2010-05-10
> **wilee-nilee said:**
> mikewhatever's link is perfect you have to boot from a live Ubuntu CD to do this step 11 which the link goes straight to is what you want and the only way to reload the MBR with grub, that I know of. If you have any questions go to the live cd run sudo fdisk l and post the results while still on the live cd I or somebody else will help you out, by the way l= a small case L.
Ahh, ok... I shall try that when I find the LiveCD >_<
However, open to suggestions on how to do it on Windows until I can get to my house and find the CD ;P

---

### Post by wilee-nilee on 2010-05-10
> **camn said:**
> Ahh, ok... I shall try that when I find the LiveCD >_<
However, open to suggestions on how to do it on Windows until I can get to my house and find the CD ;P

You can't do this from windows also notice I changed the command to 
sudo fdisk -l   I had left out the -.

---

### Post by spydeyrch on 2010-05-10
Well, you could use a windows program, EasyBCD, and add ubuntu to the boot menu. It is kind of tricky but it does work, if you do it correctly. Just a suggestion.

-Spydey:guitar:

---

### Post by wilee-nilee on 2010-05-10
> **spydeyrch said:**
> Well, you could use a windows program, EasyBCD, and add ubuntu to the boot menu. It is kind of tricky but it does work, if you do it correctly. Just a suggestion.

-Spydey:guitar:

I don't think easybcd will read a ext4 partition, so lets stay on track here with a proper fix rather then getting things screwed up. Just to clarify, I use XP and W7, I am not a guru, or expert but this is a simple area as far as getting stuff working.

---

### Post by camn on 2010-05-10
> **mikewhatever said:**
> Reinstall Grub, the Ubuntu boot loader.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
That actually didn't work, now that I found the LiveCD... Any other ways..?

---

### Post by wilee-nilee on 2010-05-10
> **camn said:**
> That actually didn't work, now that I found the LiveCD... Any other ways..?

I suspect you didn't do it correctly, but thats is okay. :) Post this boot script in code tags. Just paste the script which is run from a live cd in a reply and highlight the text then click on the # in the reply gui.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

