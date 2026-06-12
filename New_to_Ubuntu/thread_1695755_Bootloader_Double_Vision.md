---
title: "Bootloader Double Vision"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by inukai on 2011-02-26
I had Windows 7 installed when I installed ubuntu. Now the ubuntu boot loader works just fine, but one problem. Below is a horribly paraphrased boot loader. 

> Ubuntu 10.10 (64-bit)
Ubuntu 10.10 (64-bit) recovery mode
Ubuntu 10.10 (64-bit)
Ubuntu 10.10 (64-bit) recovery mode
memory check
Windows 7
Windows Vista

My question is why is there two copies of Ubuntu and why is there a Windows Vista option? This doesn't make much sense to me. How can I fix this?

---

### Post by Quackers on 2011-02-26
The two entries for Ubuntu are two different kernels. The recovery entrys are  self-explanatory.
The Vista entry could possibly be a Windows recovery partition. Have you tried booting it?

---

### Post by inukai on 2011-02-26
Two different kernels? Why would there be two? It's not a problem but I don't want it potentially messing something up.

---

### Post by col48 on 2011-02-26
There are two pairs of Ubuntu entries.

Perhaps you have two kernels on your machine?  In this case each pair would relate to one of these kernels.  One would be more up-to-date than the other and there would be slight differences between them, although you are unlikely to be able to tell the difference as you run them.  Canonical generally repair security loopholes and repair bugs in releasing a new kernel, which they do through the routine package update procedure.

I make no comment on the advisability of trimming the menu.

---

### Post by Quackers on 2011-02-26
Every time a new kernel is issued (via updates) a new pair of entries will appear in the grub menu. Some people recommend that you keep the current kernel and one other (for backup purposes). Once I know that the newest one works ok, I delete the previous one(s) via synaptic package manager. (enter 2.6.35, or whatever, in synaptic's search box and all currently installed kernels will appear). Take care to leave at least the last one! :-)
After deleting kernels run ```
sudo update-grub
``` in the terminal

---

### Post by inukai on 2011-02-26
Ok, I figured it out. The Vista is a recovery partition, and the second entry boots into a text-only console mode. And col48, I think you may be right about trimming the menu. I'll just let sleeping dogs lie with this one, thanks.

---

### Post by oldfred on 2011-02-26
As updates are made kernels will be added to the menu. We generally recommend that you keep two, they do not take much space on drive and in case you have an issue with the new one you may be able to boot the older one.

Grub almost always sees the vendor recovery partition as Vista with newer computers. That will let you create the DVDs that reinstall your system image to as it was the day you purchased it, erasing everything.

I have not used either of these gui tools:
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
The easiest way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

If you delete the kernel you are running you will not be able to reboot:
Check what version you are running first:
fred@fred-LT-A105:~$ uname -r
2.6.35-25-generic

In synaptic search for linux-image to choose to delete old ones

Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
[http://www.go2linux.org/clean-linux-kernel-images-grub-menu](http://www.go2linux.org/clean-linux-kernel-images-grub-menu)

---

### Post by inukai on 2011-02-26
Ok, I will leave these two until the next update. I was just worried it may have been left over from a bad install or something. Thank you everyone!

---

