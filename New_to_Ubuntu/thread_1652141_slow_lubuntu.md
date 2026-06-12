---
title: "slow lubuntu"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by sve$hnikov on 2010-12-24
hi!
i have ubuntu 10.10 
and i turn the desktop to LXDE because gnome it was slow
but also here in lubuntu desktop also slow
i have 512mb ram and card graphic 16 mb
when i open a 5 windows it will be so slow
there is any solution ?

---

### Post by Bölvaður on 2010-12-24
follow your ram usage with the command "free -m" and look at the row "-/+ buffers/cache:" in column "used"


my laptop is old and has also 512mb ram and can be slow with gnome. I currently have linux mint with fluxbox on it. before that I have had xubuntu and Awesome (a tiling window manager) and both worked well... awesome should be the best but it might be too difficult to adapt to using

---

### Post by sve$hnikov on 2010-12-24
:D thanks 
this is what you tel me 
-------------------
             total       used       free     shared    buffers     cached
Mem:           496        442         53          0         75        105
-/+ buffers/cache:        [COLOR=Red]261[/COLOR]        235
Swap:          254         96        158
---------------
so the LXDE fast than Xbuntu or there is other fast than LXDE

---

### Post by sve$hnikov on 2010-12-24
so what i can do ?

---

### Post by t4thfavor on 2010-12-24
Use lighter applications, or get more ram. You can also add swap space, but that tends to be almost as slow. 

Some have had luck with using fast flash drives as better swap space than standard disks as they have no seek time (this will make the drive ware out faster though).

---

### Post by t4thfavor on 2010-12-24
Use lighter applications, or get more ram. You can also add swap space, but that tends to be almost as slow. 

Some have had luck with using fast flash drives as better swap space than standard disks as they have no seek time (this will make the drive ware out faster though).

---

### Post by amjjawad on 2010-12-24
> **sve$hnikov said:**
> hi!
i have ubuntu 10.10 
and i turn the desktop to LXDE because gnome it was slow
but also here in lubuntu desktop also slow
i have 512mb ram and [SIZE=4][COLOR=Red]**card graphic 16 mb**[/COLOR][/SIZE]
when i open a 5 windows it will be so slow
there is any solution ?

Is your Graphics Card built-in? if it's not then no matter how big your RAM is, we're talking about 16MB here so what do you expect? 

If your Graphics Card is built-in then try to increase the shared memory from BIOS. Most likely your card is not built-in so you can't do anything about it.

I strongly suggest to try the lightest distributions ever or try to get a better hardware. Don't expect Ubuntu to be fast with 16MB Graphics Card.

---

### Post by sve$hnikov on 2010-12-24
yes i geuss all my probleme with ubuntu is the card graphic
thanks for all

---

