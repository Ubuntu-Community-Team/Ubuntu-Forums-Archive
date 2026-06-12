---
title: "Size requirement?  Size recommendation?"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by DigiTan on 2009-03-07
This question's super-easy.  Excluding videos and music collections, how much would you say is a decent amount of space for a desktop user to partition for Ubuntu?

Also, I want a /home partition separate from my Ubuntu install partition.  Will the installation process let me adjust these partitions during the install?

---

### Post by skymera on 2009-03-07
I run Ubuntu on a 10GB partition.

However 5GB is enough as the install is 2.1GB and easily 1.7GB trimmed.

---

### Post by Kareeser on 2009-03-07
Personally, I give ~8 GB for the / partition. This leaves enough room for heavy installations such as having both GNOME and KDE, plus whatever you care to throw at it.

I give all the other available space to /home

Hasn't steered me wrong yet :)

---

### Post by DigiTan on 2009-03-07
Ah, that's a good thing.  I was expecting it was a lot bigger.

And the swap space?...  Is 3 to 4GB excessive?

---

### Post by tracerbullet on 2009-03-07
> **DigiTan said:**
> And the swap space?...  Is 3 to 4GB excessive?
To me it sounds like a bit much, but I guess it would be fine.

I managed to do a minimal install on 2 GB including swap, and I had about 500 MB left after I added the most essential programs (desktop of course, web browser, GIMP etc.)

On second thought, this was a Debian install, I'm told they are very similar due to Ubuntu being a derivative, but I have discovered a lot of little things that are different.

Well for what it's worth, that's my experience =) 

I think I would dedicate 10 GB for the OS. That should be PLENTY of space for anything I would want to install.

---

### Post by mkvnmtr on 2009-03-07
For swap I install no more than 1Gb. I think that is too big. I was running xfce4 on 128Mb of ram while I was waiting for ram to get here. The most swap use I saw was about 100Mb. On a rig with 512Mb or more the most I have seen was about 15Mb but my ram use never topped out.

---

### Post by johnjohn2 on 2009-03-07
i had offered the / partition 50gb as i was used to windows

but i still have 45 remaining.

---

### Post by Agg23 on 2009-03-07
10GB is good for ubuntu, but I am trying to change my partition to 30GB for more programs and files.  I would recommend if you want a lot programs, use 15GBs.

---

### Post by ivanvajar on 2009-03-07
I made 25GB partition for Ubuntu and 1GB swap. I suggest a partition 25-30GB and swap 1GB. You don't want Ubuntu partition to be full ever. Swap is similar to paging file in Windows. But don't think that it should go up to 2,5 times your RAM size, cause, as mkvnmtr said, there is no use for swap that big. I have Ubuntu with GNOME, KDE and Xfce all installed, with tons of programs and files and I still have more than 10GB left.

---

### Post by mrbiggbrain on 2009-03-07
i found many times that haveing a swap area of 1.25x - 1.5x the size of your physical memory is the best way to go. this allows for total dumps, and makes hibernateing quicker (IMOH)

---

### Post by DigiTan on 2009-03-07
About this swapspace thing...  If I get a 2nd Linux distro, do I need a 2nd swapspace?

---

### Post by Syed_Muhammad_Shahbaz on 2009-03-08
Well I have a P3 processor along with an Intel D815 board, 80 GB hard disk and 256 MB of RAM. I only give thrice the size of RAM i.e., 768 MB to /swap, 15 GB to root( / ), and rest of the available space to /home. It works just fine on my machine. Hope it can do better on yours.

---

### Post by Elfy on 2009-03-08
> **DigiTan said:**
> About this swapspace thing...  If I get a 2nd Linux distro, do I need a 2nd swapspace?

No you don't

But I would add that if you need to hibernate then swap should be at least equal to RAM.

---

### Post by theozzlives on 2009-03-08
about 10 GB for root (/), the amt of RAM for swap, the rest for /home. I'm running the development edition of 9.04 on a 20 GB Hard Drive w/256 MB RAM.

---

