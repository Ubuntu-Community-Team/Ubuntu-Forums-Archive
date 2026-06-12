---
title: "Dual boot"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by shaolinmilk on 2009-01-29
The last time I tried to dual boot Windows with Ubuntu, I screwed up big time and Ubuntu overwrote everything. So now I need help with dual-booting Windows with Ubuntu. I have Ubuntu installed already and want to install Windows 7. I read many tutorial's, but I'm afraid to lose all my data once again. Please be kind and help me, thank you.

---

### Post by Raccoon1400 on 2009-01-29
It shouldn't be any different from any other windows/linux dual boot.

Download the beta from the microsoft site
make a new ntfs partition with gparted, which is on the ubuntu live CD
install win7 to the new partition
you will have to reinstall grub. I don't know the ubuntu method for this, but you could look up super grub disk
you will also have to create a grub boot entry for windows, at least if you use super grub disk

---

### Post by shaolinmilk on 2009-01-29
So I went to GParted and resized my harddrive. It is resizing right now and making another partition I think. Is this how it's done? I hope it is, because when I did this the first time, everything was gone.

---

### Post by Raccoon1400 on 2009-01-29
gparted is actually resizing partitons on my other machine now

it's hard to say if this is how it's done without seeing it, but it sounds like you are doing the right thing. As long as you don't delete the partition your stuff is on, you should be alright.

But just make sure to back up data when doing this, more peace of mind

---

### Post by bumanie on 2009-01-29
There are various ways to set up a dual boot system - search google and you you will find many methods, none being more right than another, it comes down to personal preference. In short I set up a separate / ; /home ; and swap. To do this one must choose manual at the partitioning stage and fill in the appropriate windows after choosing 'new partition'. / - 8-10gb; /home as large as you like ; swap generally 1-2gb is enough. 

Top window  - set size of partition in mb
middle window - set filesystem or swap space (if up to swap allocation)
bottom window - set partition name ie / ; /home ; swap

Hope that makes sense.

---

### Post by Raccoon1400 on 2009-01-29
> **bumanie said:**
>  swap generally 1-2gb is enough. 

Hope that makes sense.

Should be at least the size of your ram, especially if you want to use hibernate.

---

### Post by kspncr on 2009-01-30
This could be just what you're looking for [http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

---

