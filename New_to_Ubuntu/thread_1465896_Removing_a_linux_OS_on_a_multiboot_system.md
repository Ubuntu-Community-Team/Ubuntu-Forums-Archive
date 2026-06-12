---
title: "Removing a linux OS on a multiboot system"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by ShadowMage on 2010-04-29
Hi,

I just installed Ubuntu 10.04 Lucid Lynx on a system with several operating systems (more than 2), including Ubuntu 9.10 Karmic Koala. I plan on removing Karmic once I'm settled in with Lucid, but want to keep it until then.

Since Lucid installed new GRUB, now Lucid is my "system partition". This is what I want, so, so far so good. However, my concern is the following:

I seem to remember messing up GRUB in the past by deleting a partition containing an OS recognized by GRUB. So, how can I safely remove Karmic once I'm ready?

Thanks in advance for any help,
ShadowMage

---

### Post by cuberts on 2010-04-29
> **ShadowMage said:**
> Hi,

I just installed Ubuntu 10.04 Lucid Lynx on a system with several operating systems (more than 2), including Ubuntu 9.10 Karmic Koala. I plan on removing Karmic once I'm settled in with Lucid, but want to keep it until then.

Since Lucid installed new GRUB, now Lucid is my "system partition". This is what I want, so, so far so good. However, my concern is the following:

I seem to remember messing up GRUB in the past by deleting a partition containing an OS recognized by GRUB. So, how can I safely remove Karmic once I'm ready?

Thanks in advance for any help,
ShadowMageso you want to clear the other kernels?
well when it shows the grub menu you have to press the key it tells you to to edit the entries or something.

---

### Post by ShadowMage on 2010-04-29
Thank you for your quick response, cuberts.

What I want to do (not yet, but soon) is to delete/reformat the partition containing karmic koala, freeing up that space (most likely giving it to lucid), but I don't want to mess up GRUB in the process. If I just delete the partition from say gparted, GRUB won't like this if I'm not mistaken.

Anyone have any ideas?

---

### Post by limey_rick on 2010-04-29
If you delete your Karmic partition, you can then run 

> sudo update-grub

This will rebuild the GRUB2 menu by looking for OSs on your disks. If you removed the Karmic partition, GRUB2 will not find it, so it won't be on the boot menu.

---

### Post by lockalidiot on 2010-04-29
According to my modest knowledge, after removing karmic, run the following command in terminal:
```
sudo update-grub
```
That will automatically update your "grub.conf" file an it should as well automatically register the fact that there is one less boot option. At least thats how it works _the other way around_.
IE. I installed windows 7 as a dual-boot after installing ubuntu. Then I had to reinstall grub.-> I could only boot to ubuntu. Then I ran the aforementioned command and the issue was solved.

You might want to wait confirmation for this though.

EDIT: It seems you got it.

---

### Post by ShadowMage on 2010-04-29
Thank you for your response, limey_rick.

So if I do this from let's say within lucid on gparted, and run sudo update-grub before I reboot, GRUB will understand that karmic is gone and won't complain when I reboot?

EDIT: Wow, another response as I was typing this. You guys are great, thank you so much! Since I don't plan on removing karmic just yet anyway, though, I will wait for some sort of confirmation that this at least SHOULD work. Worst to worst, I'll re-install lucid (which will re-install GRUB), but I do wish to avoid this :D

---

### Post by limey_rick on 2010-04-29
Exactly that. 

You will see the output from GRUB - here is mine for example from a multi boot system:

rick@RICKY-UBUNTU:/media$ sudo update-grub
Generating grub.cfg ...
Found Debian background: The-Simpsons.tga
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 8.04.4 LTS (8.04) on /dev/sda3
Found Microsoft Windows XP Professional on /dev/sdc1
Found openSUSE 11.2 (i586) on /dev/sdd1
Found Fedora release 12 (Constantine) on /dev/mapper/vg_rickyfedora-lv_root
done

GRUB goes through all your disks and finds the OS you have installed and builds the menu from these. If you have no Karmic, it will not be found.

---

### Post by ShadowMage on 2010-04-29
Ok great! It makes sense. Thanks you so much for the quick replies, everyone!

---

### Post by oldfred on 2010-04-30
What I think you are remembering as the problem is when you uninstall a system that controls the MBR. When you delete that one your grub has no place to go and gives error messages. As long as you install grub from a system you are keeping before deleting another system you will be in good shape.

---

### Post by ShadowMage on 2010-05-14
Thank you, oldfred. And yes, actually I'm pretty sure that's exactly what happened last time. I'm getting more familiar with this stuff now and I'm marking this thread as solved.

Thanks again for everyone's help!

---

