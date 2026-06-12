---
title: "Deleting Multiple boot entries in Grub"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by South Shore Pats Fan on 2009-12-02
Hi all, I have a dual boot Vista and Ubuntu 9.10 setup. That works fine, however on the Grub screen when I start up my computer, there are multiple duplicate entries for Ubuntu. When I had 9.04 installed I would just edit the menu.lst file but now there doesn't seem to be a menu.lst file. I was just wondering how I can delete multiple entries so that it looks neater.

Sorry if my terminology is incorrect or if this has already been posted before.

Thanks.

---

### Post by Locke_99GS on 2009-12-02
It is likely multiple Kernels, as Grub2 shouldn't create duplicate entries when it makes the config. Remove the old Kernels that aren't needed anymore via a package manager, and they should disappear from your Grub menu.

---

### Post by maedox on 2009-12-02
There is a guide [here ]("https://wiki.ubuntu.com/Grub2")about GRUB 2 (1.97). They have changed it, so you cannot just edit menu.lst. You can edit /boot/grub/grub.cfg and then you must run update-grub to make the changes active. You can hide the menu also, but I'm sure you knew that. Anyways, I would recommend you read the guide before doing anything.

---

### Post by South Shore Pats Fan on 2009-12-03
> **Locke_99GS said:**
> It is likely multiple Kernels, as Grub2 shouldn't create duplicate entries when it makes the config. Remove the old Kernels that aren't needed anymore via a package manager, and they should disappear from your Grub menu.

Thanks for the advice. That's exactly what the problem was. I decided to not remove the other kernel just in case.

And maedox, thanks for the guide. It really illuminated how the new grub works.

---

### Post by MrMarkAZ on 2009-12-31
I had the same question as South Shore Pats Fan and this thread saved me from doing something really stupid, so thanks for the heads-up. However, I have a follow-up question.

The fact that each entry in Grub for Ubuntu reflects a different kernel is confusing to me, as I just repartioned and formatted my hard drive into a dual-boot configuration between Windows XP and Karmic. Nothing remotely Linux-like has been installed on this computer, ever, so this had to be done during setup. Why would the Ubuntu setup process install two kernels?

Thanks.

---

### Post by oldfred on 2009-12-31
The original install CD is not updated every day. You install the CD and then run updates. If a newer kernel has been released then it will be downloaded. On my desktop I have 3 kernels as I installed soon after release and have had two kernel update. -15, -16, 17

I recently updated my Laptop and it only has two kernels as the original and the newest. -15 & -17

---

### Post by Rowanmf on 2009-12-31
and if you run computer janitor it does clean up older kernels , normaly leaves the newst 2 , just in case ......but it works well for me ...

---

### Post by presence1960 on 2009-12-31
I would leave one kernel as a backup in case the newest one borks. So leave the 2 newest kernels and their recovery options. 

To remove the others simply uninstall the others by removing linux-headers-2.6.31-x and linux-image-2.6.31-x in Synaptic or use the command line. When all done use terminal to run ```
sudo update-grub
``` if the references were not removed from grub.cfg

---

