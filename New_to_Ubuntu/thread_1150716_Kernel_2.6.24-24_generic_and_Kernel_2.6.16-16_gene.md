---
title: "Kernel 2.6.24-24 generic and Kernel 2.6.16-16 generic"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by robertron76 on 2009-05-06
After installing updates and restarting, I see many versions of Ubuntu Menu :


[LIST]
[*]Ubuntu 8.04.2, kernel 2.6.24-24 generic
[*]Ubuntu 8.04.2, kernel 2.6.24-24 generic [recovery]
[*]Ubuntu 8.04.2, kernel 2.6.24-16 generic
[*]Ubuntu 8.04.2, kernel 2.6.24-16 generic [recovery]
[*]Vista
[*]Vista
[/LIST]
I think I'm seeing this after the updates I installed last night, but how do I get rid of the unwanted kernale and its version?

Or is this normal?

---

### Post by halitech on 2009-05-06
anytime you upgrade the kernel it will be added to grub so you can confirm the new one is working and boot into a previous version if needed to fix issues. If it just updated last night, I would wait for a few weeks before removing the old ones just to make sure.

---

### Post by robertron76 on 2009-05-06
Thanks for the advice, that's a good recommendation.I'll definitely wait for few weeks.

I did a search as well, and found this command :

sudo gedit /boot/grub/menu.lst

menu.lst content :

> 
title        Ubuntu 8.04.2, kernel 2.6.24-24-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=396ff67b-04cc-4b6b-b023-cd546f7b6c9f ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=396ff67b-04cc-4b6b-b023-cd546f7b6c9f ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.2, kernel 2.6.24-16-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=396ff67b-04cc-4b6b-b023-cd546f7b6c9f ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=396ff67b-04cc-4b6b-b023-cd546f7b6c9f ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1


---

### Post by whoop on 2009-05-06
I always try to have the latest kernel and the last working kernel before that. So in your case I would not remove any kernel at all (for the moment). If you want to be stubborn ;) or you are getting more than 2 kernels you can remove them with synaptic. Search for linux-image and be sure to remove the right one(s) and do not remove linux-image-generic.

---

### Post by whoop on 2009-05-06
> **robertron76 said:**
> Thanks for the advice, that's a good recommendation.I'll definitely wait for few weeks.

I did a search as well, and found this command :

sudo gedit /boot/grub/menu.lst

menu.lst content :
If you remove them from menu.lst you are only removing them from the boot screen, in that case the kernels are still on your machine they are just not referenced and/or selectable when you boot up.

If you remove a kernel with synaptic (as I described earlier) it will automatically be removed from menu.lst.

And again, as a rule leave at least two kernels on your system (just like you have now) an keep them in your menu.lst as well. You'll be very great full if you run into problems with your latest kernel and you can temporarily use the old(er) one. This situation should of course never happen, but I have had to use an older kernel a couple of times in the past to get out of trouble.

---

### Post by robertron76 on 2009-05-06
Thanks a lot,guys.

I'm gonna leave it as suggested, as am planning to install next ver Ubuntu when next LTS is out.

---

### Post by mick8985 on 2009-05-06
On 9.04 this behaviour no long happens, old kernels are removed.

---

### Post by whoop on 2009-05-06
> **mick8985 said:**
> On 9.04 this behaviour no long happens, old kernels are removed.
Are you sure about this mick8985? I can't disprove this as my current jaunty installs have only one kernel installed atm, but isn't this because of an upgrade from intrepid? If a new kernel would be released for jaunty and the previous one would be removed automatically (what I think you are saying) it would be insane imho. Did you read this somewhere? I seriously hope you are wrong...

---

