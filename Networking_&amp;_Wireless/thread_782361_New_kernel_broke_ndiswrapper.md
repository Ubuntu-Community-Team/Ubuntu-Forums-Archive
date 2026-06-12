---
title: "New kernel broke ndiswrapper"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by allspiritseve on 2008-05-04
Hello all,

I installed virtualbox today, and then restarted, and a new kernel must have been installed. When I booted up, my network adapter wasn't recognized, and I couldn't use my wireless. I am using ndiswrapper and b43 I believe, to run my dell 1490 wireless card. I went through and checked, and everything seemed to be installed correctly, but it said no wireless device detected or something like that. 

I'm sorry I can't be more detailed... I'm happy to run any commands and post output if it gives anyone a better idea of what went wrong and what needs to be fixed.

Thanks,

Cory

---

### Post by Ayuthia on 2008-05-04
> **allspiritseve said:**
> Hello all,

I installed virtualbox today, and then restarted, and a new kernel must have been installed. When I booted up, my network adapter wasn't recognized, and I couldn't use my wireless. I am using ndiswrapper and b43 I believe, to run my dell 1490 wireless card. I went through and checked, and everything seemed to be installed correctly, but it said no wireless device detected or something like that. 

I'm sorry I can't be more detailed... I'm happy to run any commands and post output if it gives anyone a better idea of what went wrong and what needs to be fixed.

Thanks,

Cory

Can you post your uname -r, your lsmod|grep -i -e b43 -e ndiswrapper?  You should only be using b43 or ndiswrapper.  Using them both will cause conflicts.

---

### Post by allspiritseve on 2008-05-04
> **Ayuthia said:**
> Can you post your uname -r, your lsmod|grep -i -e b43 -e ndiswrapper?  You should only be using b43 or ndiswrapper.  Using them both will cause conflicts.

I just went back and found the install instructions for my wireless.. it's ndiswrapper: [http://ubuntuforums.org/showthread.php?t=760568](http://ubuntuforums.org/showthread.php?t=760568)

```

spirit2@spirit-laptop:~$ uname -r
2.6.24-16-386

```

I did not get anything back for the second command. My original kernel was 2.6.24-16-generic.

---

### Post by Ayuthia on 2008-05-04
Well, your ndiswrapper module is not loaded.  You could try to load the module again (sudo modprobe ndiswrapper) and see if it starts up.  I have not seen a kernel change from generic to 386 without actually installing manually, but I am also using the 64-bit version.

Does your /boot/grub/menu.lst have the old kernel listed?  I would think that if there was a kernel upgrade, it should still provide a link to the old kernel.

---

### Post by allspiritseve on 2008-05-04
> **Ayuthia said:**
> Does your /boot/grub/menu.lst have the old kernel listed?  I would think that if there was a kernel upgrade, it should still provide a link to the old kernel.

Yeah, it's still listed, that's how I'm writing to you now. I definitely didn't manually install it, but.. does that mean the 386 version is just different than the generic, and not an upgrade? I would be fine removing it, if that's so.

I'll try that command and see what it comes up with.

---

### Post by Ayuthia on 2008-05-04
Something triggered the kernel change.  I did not get a kernel upgrade for my 32-bit laptop (just realized that my other laptop is using Hardy 32-bit).  

Before removing it, you might want to review /var/log/dpkg.log, see when 386 was installed, and what packages came with it.  The packages that came with it would have the same date and time in the log. It would be more helpful to why it was installed before removing it (in case it breaks another package).  I am not for sure about the differences between 386 and generic though.

You might also want to confirm that 2.6.24-16-generic is still installed or else you might not get another kernel update in the future.

---

### Post by allspiritseve on 2008-05-05
It looks like it was upgraded when I installed virtualbox.

---

### Post by Ayuthia on 2008-05-05
That's odd.  I went to my 32-bit laptop and typed sudo aptitude install virtualbox and it did not say that it needed the 386 kernel.  It only requested libxalan110, libexrecs27, virtualbox-ose virtualbox-ose-modules-2.6.24-16-generic.  Does your log show any other packages for that time period?

---

### Post by allspiritseve on 2008-05-05
> **Ayuthia said:**
> That's odd.  I went to my 32-bit laptop and typed sudo aptitude install virtualbox and it did not say that it needed the 386 kernel.  It only requested libxalan110, libexrecs27, virtualbox-ose virtualbox-ose-modules-2.6.24-16-generic.  Does your log show any other packages for that time period?

I don't think so:

```

2008-05-04 12:43:38 startup archives unpack
2008-05-04 12:43:38 install linux-image-2.6.24-16-386 <none> 2.6.24-16.30
2008-05-04 12:43:38 status half-installed linux-image-2.6.24-16-386 2.6.24-16.30
2008-05-04 12:43:45 status unpacked linux-image-2.6.24-16-386 2.6.24-16.30
2008-05-04 12:43:45 status unpacked linux-image-2.6.24-16-386 2.6.24-16.30
2008-05-04 12:43:45 install libxerces27 <none> 2.7.0-5
2008-05-04 12:43:45 status half-installed libxerces27 2.7.0-5
2008-05-04 12:43:46 status unpacked libxerces27 2.7.0-5
2008-05-04 12:43:46 status unpacked libxerces27 2.7.0-5
2008-05-04 12:43:46 install libxalan110 <none> 1.10-3.1
2008-05-04 12:43:46 status half-installed libxalan110 1.10-3.1
2008-05-04 12:43:46 status unpacked libxalan110 1.10-3.1
2008-05-04 12:43:46 status unpacked libxalan110 1.10-3.1
2008-05-04 12:43:46 install virtualbox-ose <none> 1.5.6-dfsg-6ubuntu1
2008-05-04 12:43:46 status half-installed virtualbox-ose 1.5.6-dfsg-6ubuntu1
2008-05-04 12:43:48 status unpacked virtualbox-ose 1.5.6-dfsg-6ubuntu1
2008-05-04 12:43:48 status unpacked virtualbox-ose 1.5.6-dfsg-6ubuntu1
2008-05-04 12:43:48 install virtualbox-ose-modules-2.6.24-16-386 <none> 24
2008-05-04 12:43:48 status half-installed virtualbox-ose-modules-2.6.24-16-386 24
2008-05-04 12:43:49 status unpacked virtualbox-ose-modules-2.6.24-16-386 24
2008-05-04 12:43:49 status unpacked virtualbox-ose-modules-2.6.24-16-386 24
2008-05-04 12:43:49 install virtualbox-ose-modules-2.6.24-16-generic <none> 24
2008-05-04 12:43:49 status half-installed virtualbox-ose-modules-2.6.24-16-generic 24
2008-05-04 12:43:49 status unpacked virtualbox-ose-modules-2.6.24-16-generic 24
2008-05-04 12:43:49 status unpacked virtualbox-ose-modules-2.6.24-16-generic 24
2008-05-04 12:43:49 install virtualbox-ose-modules-generic <none> 24
2008-05-04 12:43:49 status half-installed virtualbox-ose-modules-generic 24
2008-05-04 12:43:49 status unpacked virtualbox-ose-modules-generic 24
2008-05-04 12:43:49 status unpacked virtualbox-ose-modules-generic 24
2008-05-04 12:43:50 startup packages configure
2008-05-04 12:43:50 configure linux-image-2.6.24-16-386 2.6.24-16.30 2.6.24-16.30
2008-05-04 12:43:50 status unpacked linux-image-2.6.24-16-386 2.6.24-16.30
2008-05-04 12:43:50 status half-configured linux-image-2.6.24-16-386 2.6.24-16.30
2008-05-04 12:44:10 status installed linux-image-2.6.24-16-386 2.6.24-16.30
2008-05-04 12:44:10 configure libxerces27 2.7.0-5 2.7.0-5
2008-05-04 12:44:10 status unpacked libxerces27 2.7.0-5
2008-05-04 12:44:10 status half-configured libxerces27 2.7.0-5
2008-05-04 12:44:10 status installed libxerces27 2.7.0-5
2008-05-04 12:44:10 status triggers-pending libc6 2.7-10ubuntu3
2008-05-04 12:44:10 configure libxalan110 1.10-3.1 1.10-3.1
2008-05-04 12:44:10 status unpacked libxalan110 1.10-3.1
2008-05-04 12:44:10 status half-configured libxalan110 1.10-3.1
2008-05-04 12:44:10 status installed libxalan110 1.10-3.1
2008-05-04 12:44:10 configure virtualbox-ose 1.5.6-dfsg-6ubuntu1 1.5.6-dfsg-6ubuntu1
2008-05-04 12:44:10 status unpacked virtualbox-ose 1.5.6-dfsg-6ubuntu1
2008-05-04 12:44:10 status unpacked virtualbox-ose 1.5.6-dfsg-6ubuntu1
2008-05-04 12:44:10 status unpacked virtualbox-ose 1.5.6-dfsg-6ubuntu1
2008-05-04 12:44:10 status unpacked virtualbox-ose 1.5.6-dfsg-6ubuntu1
2008-05-04 12:44:10 status unpacked virtualbox-ose 1.5.6-dfsg-6ubuntu1
2008-05-04 12:44:10 status unpacked virtualbox-ose 1.5.6-dfsg-6ubuntu1
2008-05-04 12:44:10 status unpacked virtualbox-ose 1.5.6-dfsg-6ubuntu1
2008-05-04 12:44:10 status unpacked virtualbox-ose 1.5.6-dfsg-6ubuntu1
2008-05-04 12:44:10 status half-configured virtualbox-ose 1.5.6-dfsg-6ubuntu1
2008-05-04 12:44:11 status installed virtualbox-ose 1.5.6-dfsg-6ubuntu1
2008-05-04 12:44:11 configure virtualbox-ose-modules-2.6.24-16-386 24 24
2008-05-04 12:44:11 status unpacked virtualbox-ose-modules-2.6.24-16-386 24
2008-05-04 12:44:11 status half-configured virtualbox-ose-modules-2.6.24-16-386 24
2008-05-04 12:44:19 status installed virtualbox-ose-modules-2.6.24-16-386 24
2008-05-04 12:44:19 configure virtualbox-ose-modules-2.6.24-16-generic 24 24
2008-05-04 12:44:19 status unpacked virtualbox-ose-modules-2.6.24-16-generic 24
2008-05-04 12:44:19 status half-configured virtualbox-ose-modules-2.6.24-16-generic 24
2008-05-04 12:44:20 status installed virtualbox-ose-modules-2.6.24-16-generic 24
2008-05-04 12:44:20 configure virtualbox-ose-modules-generic 24 24
2008-05-04 12:44:20 status unpacked virtualbox-ose-modules-generic 24
2008-05-04 12:44:20 status half-configured virtualbox-ose-modules-generic 24
2008-05-04 12:44:20 status installed virtualbox-ose-modules-generic 24
2008-05-04 12:44:20 trigproc libc6 2.7-10ubuntu3 2.7-10ubuntu3
2008-05-04 12:44:20 status half-configured libc6 2.7-10ubuntu3
2008-05-04 12:44:20 status installed libc6 2.7-10ubuntu3


```

I'm pretty sure that's all for the virtualbox install.

---

### Post by Ayuthia on 2008-05-05
You could try to remove the linux-image for the 386.  I am not for sure if it will hurt anything or not.  I am not for sure if you saw it or not, but the installer also installed virtualbox-ose-modules-386 along with virtualbox-ose-modules-generic.

The way I see it is that if you remove it, you could end up breaking something.  You should be able to fix it by reinstalling it if needed but it might not be that easy.  Of course the other side is that nothing happens and all is good.

If you don't remove it, any kernel updates for you will cause it to download the generic and 386 versions every time.  If you don't like it booting to the 386 kernel, you can always go into menu.lst and comment it out.  Of course, you might have to do that every time a kernel update happens.

If you are not afraid of the consequences, go for it!

---

