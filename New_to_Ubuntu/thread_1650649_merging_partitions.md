---
title: "merging partitions??"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by jezebel on 2010-12-22
I installed Ubuntu, and messed up my windows bootloader; my pc ended up booting directing into Ubuntu. After some small thought, I realized I needed nothing from the windows side anyway, and in Ubuntu (for netbooks), I used gparted and formatted the partition (450 gbs) that had my Win 7 install. Now I really really want to use that space for my ubuntu stuff because now Ubuntu has only 40 gbs. 

So, my question is - is there any way I can merge the partitions (the one that has all my sys files and the one that should now be empty???)

Thanks very much.

J.

---

### Post by bodhi.zazen on 2010-12-22
yes. You can do it by booting a live CD or in your case likely a usb, same as when you installed Ubuntu.

From there run gparted.



[http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C](http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C)

---

### Post by jezebel on 2010-12-22
Ubuntu is running great on this machine - I can run gparted from the hd in Ubuntu, no problem. 

My problem is that I want to combine the 460 gigs with the 40 gigs on which Ubuntu already resides. And I don't know how to do that.

---

### Post by Verbeck on 2010-12-22
> **jezebel said:**
> Ubuntu is running great on this machine - I can run gparted from the hd in Ubuntu, no problem. 

My problem is that I want to combine the 460 gigs with the 40 gigs on which Ubuntu already resides. And I don't know how to do that.
you'll need to run gparted from a live cd/usb if you want to change an existing installation

---

### Post by jezebel on 2010-12-22
Thanks - so - is it possible to use a live cd (usb) and merge partitions without disrupting my current ubuntu install??

---

### Post by Verbeck on 2010-12-22
> **jezebel said:**
> Thanks - so - is it possible to use a live cd (usb) and merge partitions without disrupting my current ubuntu install??
yes, but its recommended to backup important data before making changes incase anything goes wrong

---

### Post by jezebel on 2010-12-22
Great - actually I have no important data so not worried about that! I don't have my usb with me, but will work on this tomorrow!!

J.

---

