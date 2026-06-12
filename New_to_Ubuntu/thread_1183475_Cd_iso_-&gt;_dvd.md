---
title: "Cd iso -&gt; dvd"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by ~sHyLoCk~ on 2009-06-10
Hi! I have downloaded Ubuntu 9.04 CD Iso. However the problem is that since a few months the CDs in the shops around here have vanished! lol..people prefer DVDs anyway, and so they don't bring in CDs anymore. So I was wondering if it is possible to burn the CD Iso into a DVD? And if yes, how? I presently have Hardy installed and have K3b.

---

### Post by jolx on 2009-06-10
any iso can be burned to either cd or dvd iirc it just depends on the size of the image (if its > 700MB then it would need a dvd, > 4.7GB then a dual layer dvd)

so just burn as an image, in k3b Tools > Burn Image...

---

### Post by anaconda on 2009-06-10
well. you CAN burn a CD iso to a dvd, BUT the resulting dvd won't be bootable. So you wouldnt get what you want.

Did you know, that you don't have to burn the ubuntu cd. You can install ubuntu from USB stick too...

---

### Post by MDNZ on 2009-06-10
> **anaconda said:**
> well. you CAN burn a CD iso to a dvd, BUT the resulting dvd won't be bootable. So you wouldnt get what you want.

Did you know, that you don't have to burn the ubuntu cd. You can install ubuntu from USB stick too...

The CD is bootable if you just use image burning software. Doesn't matter if you burn it on a CD, DVD or Dual layer DVD.

---

### Post by MrWES on 2009-06-10
> **MDNZ said:**
> The CD is bootable if you just use image burning software. Doesn't matter if you burn it on a CD, DVD or Dual layer DVD.


Very true! I burn Ubuntu iso's to DVDs all the time and the boot just fine.


Bill

---

### Post by anaconda on 2009-06-10
> **MrWES said:**
> Very true! I burn Ubuntu iso's to DVDs all the time and the boot just fine.
Bill

Strange. I have tried it, and the resulting DVD wasn't bootable!

Thanks for correcting me.

I will try that again today, when I get home.  
The reason I prefer dvd:s is that dvd is cheaper here than a cd...

---

### Post by MrWES on 2009-06-10
> **anaconda said:**
> Strange. I have tried it, and the resulting DVD wasn't bootable!

Thanks for correcting me.

I will try that again today, when I get home.  
The reason I prefer dvd:s is that dvd is cheaper here than a cd...

Just make sure you're not burning it to a data DVD; otherwise it'll just burn the iso file as a single file instead of growing it into the proper structure. I've always used K3b, or growisofs from the command line.

Bill

---

### Post by ~sHyLoCk~ on 2009-06-10
> **MrWES said:**
> Just make sure you're not burning it to a data DVD; otherwise it'll just burn the iso file as a single file instead of growing it into the proper structure. I've always used K3b, or growisofs from the command line.

Bill

Thank you all for your reply! So I'll just use k3b and burn the image onto a DVD [not as Data DVD] abd it will be bootable? That's so simple :D Thnx again

---

### Post by MrWES on 2009-06-10
> **~sHyLoCk~ said:**
> Thank you all for your reply! So I'll just use k3b and burn the image onto a DVD [not as Data DVD] abd it will be bootable? That's so simple :D Thnx again

Right, choose burn cd/dvd iso when using K3b.

---

