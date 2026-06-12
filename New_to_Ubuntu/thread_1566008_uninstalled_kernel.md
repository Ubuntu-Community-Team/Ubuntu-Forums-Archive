---
title: "uninstalled kernel"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by rvgsd on 2010-09-01
I was removing an old (extra) version of kernel, and by mistake I think I uninstalled the current one as well. Now my machine shows only Windows and the MEMTEST in GRUB entries.
Is there a way i can install the kernel by booting from something and regain my customized Xubuntu install?
Thanks for any help.

---

### Post by cariboo on 2010-09-01
You can boot from the Live CD, and re-install a kernel. Not knowing what version of Xubuntu you are using it's kind of hard to give exact instructions

---

### Post by rvgsd on 2010-09-01
Oh, sorry I should have specified. 
I am using Ubuntu 10.04 32 Bit. 
So once I boot using the live cd, do I just use ```
sudo apt-get install 
``` and install the linux headers ?
Thanks for your help.!

---

### Post by rvgsd on 2010-09-02
can someone help me with this??

---

### Post by rvgsd on 2010-09-02
bump!

---

### Post by rvgsd on 2010-09-03
Another bump! I am stuck on using window$!!

---

### Post by Silent Warrior on 2010-09-03
It might be easier to just reinstall - installing a kernel from the LiveCD to your harddrive will probably require some mount-voodoo, and I for one can ABSOLUTELY not help you with that. Depending on how you partitioned (separate / and /home being the critical step), you can have at least all your files and desktop/panel preferences and configurations back as if nothing ever happened. Your installed packages, though... If you really want to avoid going through that dance again, best if you wait for someone else before you reinstall. I hope you've learned for the future to be... a little extra careful dealing with kernels...? :)

(Honestly, reinstalling is probably the least bother, as long as your partitioning is sane.)

---

### Post by rvgsd on 2010-09-03
Yeah..definitely I'll be super carefull while dealing with kernels again!!
My partitions are good, but by reinstalling all the configurations in my XFCE would be gone then, and I preferably don't want to spend that much time on it again..!!
hopefully there is some hope!

---

### Post by rvgsd on 2010-09-03
Solved the problem. 
I downloaded the kernel deb file, and booted using livecd. Then mounted my "/" in /mnt/root, then changed the root to this folder, and then copied the deb here, and installed. Was so close to re-installing everything, but saved.!
Was not expecting this to work, but it did! sweet!

---

