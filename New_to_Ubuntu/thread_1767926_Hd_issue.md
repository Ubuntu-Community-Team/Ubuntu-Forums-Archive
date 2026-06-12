---
title: "Hd issue"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by spillage on 2011-05-26
Hi All,

I have 2 600gb drives installed..one has my ubuntu installation including home and the other has a load of files I need.

I have installed a 40gb drive that I want to install another copy of ubuntu on..

In Gparted its all fine and formatted to ext4.

But whenever I run the install I can only see my two 600 drives and not the 40gb...have spent hours trying to work it out and hit a wall..

Any help would be appreciated..

Cheers,

Spill.

---

### Post by coffeecat on 2011-05-26
Has the 40GB drive ever been used in a RAID array? Some RAID metadata is not removed by reformatting and can confuse the installer.

---

### Post by spillage2 on 2011-05-26
no that wouldnt be the problem..I have disconnected my main drive and I can now install onto my 3rd drive although I shouldnt have to do that..Will have to see what happens when all 3 are connected.  need to get my head around the home folder but thats another post..

cheers spill.

---

### Post by Prince Valiant on 2011-05-26
Do you know for certain that the drive is properly connected?  A basic issue, but mis-configuring slave/master/neutral pins can render the HD invisible.

Have fun!
-Val

---

### Post by spillage2 on 2011-05-26
this is really odd..there are no jumpers on the drive just a straight sata connection..I can save to the drive but in order to load 10.04 onto it I have to disconnect my main drive first..

cheers,

head scratching spill...:)

---

### Post by audiomick on 2011-05-26
Try using the alternate CD. I don't know for sure if it is still the case, but a while back the partitioning thing on the live CD was a different one to that on the alternate CD, and the alternate was better at dealing with multiple drives.

---

### Post by wildmanne39 on 2011-05-26
> **spillage2 said:**
> this is really odd..there are no jumpers on the drive just a straight sata connection..I can save to the drive but in order to load 10.04 onto it I have to disconnect my main drive first..

cheers,

head scratching spill...:)
Hi, I installed one recently that had no jumpers either,I think it is master slave according to where it is plugged into the mother board but I am not sure of that. Mine was recognized right away, you might look in the bios to see if it needs changed.

---

