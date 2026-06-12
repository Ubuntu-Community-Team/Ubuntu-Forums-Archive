---
title: "[SOLVED] Removing r8169 driver"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by Tekmo on 2008-10-02
I'm changing my ethernet adapter's driver to r8168 (from r8169) since there is a bug in the r8169 driver that sometimes does not recognize the card.  I've successfully installed the r8168 driver and verified that it works correctly, but I'm having trouble getting rid of the r8169 driver.  Even after r8169 to /etc/modprobe.d/blacklist and renaming the module file, it still loads on system reboot.  From what I've read so far, I've heard that this may be because it is in initrd.img.  Does this mean that I have to recompile the kernel to remove the r8169 module?

---

### Post by nixscripter on 2008-10-03
No, it just means you have to modify the initrd image that came with it if you think the driver's in there.

Instructions for extracting and rebuilding one are here: [http://wiki.openvz.org/Modifying_initrd_image](http://wiki.openvz.org/Modifying_initrd_image)

Hope this helps.

---

### Post by Tekmo on 2008-10-04
I'll take a look at it.  I think this is what I was looking for.  Thanks for your help.

EDIT: Yes, this solved the problem.  Thanks a lot for your help!  I found a good set of instructions on how to do it from another thread in these forums that was in fact specific to this problem:

> I had the same problem. I had to use Google for a long time, till i found a solution in a german forum (i am from germany; sorry for my english if it's too bad). Here are the instructions:



First, you need to rename the r8169 driver, because it won't work with this one.



> mv /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko.old

> depmod -a



To save the current ramdiscimage and make a new one:

> mv /boot/initrd.img-`uname -r` /boot/initrd.img-`uname -r`.old

> mkinitramfs -o /boot/initrd.img-`uname -r`



Now you have to reboot. After this, it worked for me. To see weather the right module is loaded, you can use this:

> lsmod | grep r81*



There it showed me the right module, r8168.



Maybe it helps you, too.



Globemaster

---

### Post by Tekmo on 2008-10-07
Actually it stopped working.  It only worked once.  r8169 keeps popping up alongside r8168.  But at least I have a good idea of how to troubleshoot it now that I know the initrd image has an effect.

---

### Post by nixscripter on 2008-10-07
Perhaps now blacklisting will work? I assume it wasn't working becaue it was being loaded at boot, so perhaps now it's also being loaded after boot.

---

### Post by Tekmo on 2008-10-08
It works completely now.  I've restarted it 10 times now and it never fails (although there is now another problem that is not as big of a deal, but I want to troubleshoot it myself first).

I don't know exactly what worked, but I'll try to go over why it was such a weird solution.

First off, I already had it blacklisted and the driver renamed so that it would not load after the boot before I tried the first time.  I also aliased eth0 to r8168.  I don't think any of those were responsible for the fix because they were already applied before the first time I remade my initrd.img.  What fixed it was just remaking the initrd.img file a second time.  After that it never stopped working.

What I think happened is that something else on the system restored the old initrd.img file somehow (I have no idea what might have done that), because I found an initrd.img.bak file in the directory that I didn't think was there originally (and I know I didn't make it, because my backup naming convention is just to add a ~ to the filename).  I can't yet tell if that if that is essentially a stored version of my first attempt or not since I don't know how to read their contents, but my guess is that my 2nd attempt didn't get undone so it stuck.

Either way I'm marking this thread as solved.  Thanks a ton for your help.

---

