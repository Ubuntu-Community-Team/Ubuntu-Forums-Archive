---
title: "Question about having 3 partitions...."
date: 2009-12-04
forum: New to Ubuntu
---

### Post by Space-Wolf on 2009-12-04
Okay, I currently have two partitions, Ubuntu and Vista.  I feel like making a third and installing Mint just to check it out.  Will the installation mess up Grub?  And if I eventually delete Mint, will the deletion effect Grub and my ability to access ubuntu?

---

### Post by bodhi.zazen on 2009-12-04
You should be fine, but if you have problems post back.

I do not know if Mint uses grub or grub2, so be sure to describe any problem you may have.

---

### Post by avtolle on 2009-12-04
FWIW, I have Vista, 9.10 and Mint on a laptop. Installing Mint to a partition of its own caused Grub under Mint to be installed, and it picked up the other two OS with no problem. As to deleting Mint and its effect on Grub, I've not done that, but would think that running grub-update would take care of that. I'm sure someone with more knowledge than I can get you better information.

---

### Post by Sir Jasper on 2009-12-04
Hi,

There is no reason to expect problems, but you could probably try Mint using a live CD (though not as fast as installing).

Do you have a swap file, if not you could make one or make a swap partition using Gparted.

If you decide to change your partitions and if you have an external drive to clone to - then personally I would do that - and I would continue to do it on a regular basis.

My regards

PS I see bodhi has posted and he is a proper guru.

---

### Post by Space-Wolf on 2009-12-04
Cool, I'll give it a shot.  Hopefully Mint's Grub is as good or better than Grub 2.

---

### Post by desperado665 on 2009-12-04
Mint 8 "Helena" is based on Ubuntu 9.10, so it also uses grub 1.97 beta, although it does have a nice background pic  :)

---

### Post by Space-Wolf on 2009-12-05
Well I put Linux Mint on a Live USB, and it loaded up fine but it seemed like the resolution was very poorly calibrated.  What is the reason behind that?

---

