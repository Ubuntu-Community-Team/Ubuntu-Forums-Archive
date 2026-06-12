---
title: "Grub Boot Loader"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by markymark64 on 2011-04-17
I hope I have the right name for the file. Anyway, here's my problem folks. I went ahead and tried to install the beta version of 11.04. After reboot I got an error message which I knew was related to my nvidia card that wasn't being recognized. So, after trying various troubleshooting tips I reinstalled 10. Now when the boot screen comes up I have four instances of ubuntu at the top and two memory tests. I know which lines should be deleted but I have no idea how to delete them. I can get into the grub at the beginning with the escape key but can anyone tell me what I do from here to remove this erroneous information from my boot sequence?

Thanks,

Mark

---

### Post by weedeater64 on 2011-04-17
~$ sudo update-grub

---

### Post by markymark64 on 2011-04-17
Thanks but that tip didn't work because there are a few files in the boot folder that reference the new update that has been overwritten. This is my problem. Should I boot up in safe mode and try to delete those files from the actual boot folder? I am guess they would have to be removed from the grub loader before I actually deleted them, right?

---

### Post by coffeecat on 2011-04-17
You have...

> **markymark64 said:**
> four instances of ubuntu at the top and two memory tests.

If you did an update of your new 10.10 and installed a kernel upgrade, that would seem right. I have two memtest entries in my Maverick grub menu, "Memory test (memtest86+)" and "Memory test (memtest86+, serial console 115200)". I've never understood what the second ones means, but I simply ignore it.

And if you have two versions of the kernel installed, then you will have four menu entries, one each for normal and recovery mode.

Tell us exactly what the grub entries say, and we can take it from there.

---

### Post by weedeater64 on 2011-04-17
grub2 is a gawd awful mess of bloat and not very unixy.  I downgrade to grub legacy, if you know what you are doing.  That said, and again, if you know you need some entries gone, and some files deleted..  I dont' see any reason to go into safe mode for it, just delete them, and the new ridiculously messy  file you want to edit has been moved/renamed  /boot/grub/grub.cfg

---

### Post by thecamelcoder on 2011-04-17
Hey mate, linux is pretty special in the way that it will allow you to boot into a number of different kernels. Seeing as there was kernel upgrade from 10.10 to 11.04 you will now see two versions of the linux kernel in the grub. 

If you want to remove the older one then you can follow the instructions here: [http://www.linux-geek.co.nz/2011/04/11/how-to-clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.linux-geek.co.nz/2011/04/11/how-to-clean-up-the-new-ubuntu-grub2-boot-menu/)

If you need any further help just let me know. 
):P

---

### Post by markymark64 on 2011-04-17
camelcoder, that's exactly what I was looking for. Cheers and thanks. :p

---

### Post by thecamelcoder on 2011-04-17
> **markymark64 said:**
> camelcoder, that's exactly what I was looking for. Cheers and thanks. :p

No worries mate anytime. 

Could I ask a favor though. Could you place a comment on that post saying how helpful it was. 

Its my site and trying to build traffic. 

Thanks

---

### Post by markymark64 on 2011-04-17
Camel, I think your tip may have worked but I'm probably running grub 2. Not sure but let me post what my boot looks like


Ubuntu, with Linux 2.6.38-8-generic-pae
Ubuntu, with Linux 2.6.38-8 (recovery mode)
Ubuntu, with Linux 2.6.35-28-generic-pae
Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)
Memory Test (memory test 86+)
Memory Test (memtest 86+ Serial Console 115200)
Windows Vista

Now, if you look at the boot sequence you probably know that the lines I want to remove are the one's with 2.6.38-8 however none of these are referenced in the synaptic package manager. Only 2.6.35 is referenced. That said, where do I find these old kernels to remove them?

---

### Post by drs305 on 2011-04-17
I recommend Ubuntu Tweak. It's a great GUI app that can clean older kernels (which also will remove the entries from Grub2). Here is a thread describing it and other methods of removing kernels:
[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by markymark64 on 2011-04-17
drs thanks for the tip about ubuntu tweak. I have heard about that program before but hadn't installed it until you recommended it. Unfortunately, I'm having the same luck with you as I did with Camel here. The reference to ubunt 2.6.38-8 doesn't show up in ubuntu tweak. That said, how do I fix this now? Any thoughts?

---

### Post by drs305 on 2011-04-17
> **markymark64 said:**
> drs thanks for the tip about ubuntu tweak. I have heard about that program before but hadn't installed it until you recommended it. Unfortunately, I'm having the same luck with you as I did with Camel here. The reference to ubunt 2.6.38-8 doesn't show up in ubuntu tweak. That said, how do I fix this now?

You can try via Synaptic by doing a search for 2.6.38-8 and removing anything you find (linux-image..., headers, etc).

You can *hide* them from the Grub2 menu using Grub Customizer. You won't be physically removing the kernel (if it exists on your machine) but you won't see it. See the "Customizer" link in my signature line on how to use GC.

---

