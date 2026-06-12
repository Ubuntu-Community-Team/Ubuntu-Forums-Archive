---
title: "Installing Ubuntu on external drives for use in other computers?"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by hortstu on 2010-02-09
OK I've already learned the hard way that installing ubuntu onto a hard drive via a usb cable comes with an assortment of problems.  On the bright side I learned a little but about the terminal and the inner workings of Ubuntu but I don't need to make things hard for myself in the future.

What is the best way to install linux on a hard drive that will be used in another computer?

The first time I did it I didn't have any problems... but I've come to realize since that that was because the internal drive in the laptop was dead so the external was seen as the only drive.

Since then I've installed a new drive in the laptop and I've had problems accomplishing the same thing.  Is it possible to shut off the internal drive when I run the live CD and I'm about to install on an external or do I physically need to remove it?  Physically removing it is probably easiest for me but that comes with the slight risk of damaging something.

Thanks for the help, and as always if this is in the wrong forum please let me know where to put it.

---

### Post by ubername on 2010-02-09
If it is a USB external drive you just need to make sure that the target computer can boot from USB devices. Note you may end up with driver issues (video card / sound card / wireless etc.) but you should be able to sort these out once you are up and running. You will also need to play with grub to ensure that the computer can still boot into whatever other OS it has on its HD.

EDIT - Re-read your post and maybe I've got the wrong end of the stick - are you just asking how to install to the ext. drive from a Live CD? In which case you don't need to do anything to the existing HD - just make sure you point at the ext HD when selecting  partitions in the install process. Also, right at the end when the install asks for confirmation, click the 'advanced' button and make sure you install grub to the external HD.

---

### Post by hortstu on 2010-02-09
Thanks ubername but if you look at my last 3 threads you will see some of the problems I've run into with this.  Grub problems on the host computer, error 17, error 21, anyway I've come to the conclusion that I need to find a better way.  

I will remove the drive if necessary but I want to find the "right" way to do this. 

Thanks

> **ubername said:**
> If it is a USB external drive you just need to make sure that the target computer can boot from USB devices. Note you may end up with driver issues (video card / sound card / wireless etc.) but you should be able to sort these out once you are up and running. You will also need to play with grub to ensure that the computer can still boot into whatever other OS it has on its HD.

EDIT - Re-read your post and maybe I've got the wrong end of the stick - are you just asking how to install to the ext. drive from a Live CD? In which case you don't need to do anything to the existing HD - just make sure you point at the ext HD when selecting  partitions in the install process. Also, right at the end when the install asks for confirmation, click the 'advanced' button and make sure you install grub to the external HD.

---

### Post by hortstu on 2010-02-09
bump

---

### Post by hortstu on 2010-02-09
No one has any advice for this situation?  Maybe even a suggestion for a better place to put this question?

---

### Post by sideaway on 2010-02-09
Ok, you HAVE to install grub on the external drive. Unless ofcourse the host computer already has a HDD, in which case you can install grub on the internal drive. When you say 'computers' do you mean plural? Because that does mean GRUB has to be installed on the external.

---

### Post by hortstu on 2010-02-09
Yes grub was one of the original problems. Not only in the new install but also in the internal.

Another member helped me solve that one after the install.  So how do I install properly if I'm installing hardy onto a drive that will be a primary in another computer yet it is only a secondary usb external during the install.  What are the steps?  What do I have to do differently?  Or should I just pull out the internal drive run the computer off the live CD and let it be recognized as the primary in this computer that way? 


> **sideaway said:**
> Ok, you HAVE to install grub on the external drive. Unless ofcourse the host computer already has a HDD, in which case you can install grub on the internal drive. When you say 'computers' do you mean plural? Because that does mean GRUB has to be installed on the external.

---

### Post by DenysT on 2010-02-09
> **hortstu said:**
> Yes grub was one of the original problems. Not only in the new install but also in the internal.

Another member helped me solve that one after the install.  So how do I install properly if I'm installing hardy onto a drive that will be a primary in another computer yet it is only a secondary usb external during the install.  What are the steps?  What do I have to do differently?  Or should I just pull out the internal drive run the computer off the live CD and let it be recognized as the primary in this computer that way?

If I read your post correctly you are trying to install Ubuntu onto a USB drive on one computer that will then be transfered to another computer to be used as the primary drive internally in the other computer. Not sure how to do that but I would just put the drive into the second computer and boot the Live CD and install that way.

---

### Post by hortstu on 2010-02-09
Unfortunately that isn't an option. Thanks for the suggestion though.

---

