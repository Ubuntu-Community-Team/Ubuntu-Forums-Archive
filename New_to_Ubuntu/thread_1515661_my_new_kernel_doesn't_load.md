---
title: "my new kernel doesn't load"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by lolzwut on 2010-06-22
Hi,

about a week ago I installed updates on my ubuntu 9.04 system. I didn't upgrade to 10 though I just installed updates. When I restarted, my GRUB loaded and I noticed I had a new kernel (2.6.33-22). I also noticed that there was two new partitions at the bottom (/dev/sda) which said it had windows vista on it. I selected the first one, the newest one.
This was the message it gave me:

"error you need to load the kernel first

press any key to continue...".

so I went down to my old kernel (2.6.33-20) and it loaded fine. My windows also loads fine. I installed linux using wubi-installer by the way. Anyone know what's wrong? Thnaks!

---

### Post by lolzwut on 2010-06-22
bump

---

### Post by lolzwut on 2010-06-22
bump

---

### Post by lolzwut on 2010-06-22
bump

---

### Post by overdrank on 2010-06-22
Please be patient, only bump your threads once a day (24 hr) thanks. :)

---

### Post by lolzwut on 2010-06-22
Oh sorry, I just bumped it when it got to the 2nd page lol. Sorry, thanks for the inadvertent bump though. Do you have an answer by the way?

---

### Post by lolzwut on 2010-06-23
bump

---

### Post by Paqman on 2010-06-23
Try reinstalling the new kernel.

---

### Post by lolzwut on 2010-06-23
well my system isn't seriously damaged or anything now, it's just a annoying thing. I'm just asking if any harm can be done from this, and how would i reinstall the kernel?

---

### Post by Paqman on 2010-06-23
> **lolzwut said:**
> how would i reinstall the kernel?

Go to System > Admin > Synaptic and search for "linux-image" and filter for installed packages only. You should find you've got a couple installed, just right click on the latest one and choose "reinstall", then hit "apply".

You won't have done any damage to the system, you've never even booted that kernel from the sound of it.

---

### Post by fslezak on 2010-06-23
Your kernel is not damaged. It sounds like GRUB *forgot* to define the kernel.
There should be a part of (/boot/grub/grub.cfg) that is like this (# means your setting!):

```

menuentry 'Ubuntu, with Linux 2.6.32-##-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext#
    set root='(hd0,#)'
    search --no-floppy --fs-uuid --set [COLOR=Black]########-####-####-####-############[/COLOR]
   [COLOR=Red] linux    /boot/vmlinuz-2.6.32-##-generic root=UUID=########-####-####-####-############ ro  splash quiet  quiet splash[/COLOR]
    initrd    /boot/initrd.img-2.6.32-##-generic
}

```I think the red line is missing or not complete.

Hope this helps!

If this is the problem, run "sudo update-grub" (without the quotes).

---

### Post by lolzwut on 2010-06-23
thanks for the advice. I think I'm going to play it safe and just leave it all alone. I plan to remove ubuntu very soon anyway and try another distro. So I'm just gonna make sure my files are safe. Thanks a lot.

---

### Post by -humanaut- on 2010-06-23
2.6.32-23 killed my Xorg (I'm using a Nvidia Geforce6150SE) which I know is the problem damn Nouveau

---

