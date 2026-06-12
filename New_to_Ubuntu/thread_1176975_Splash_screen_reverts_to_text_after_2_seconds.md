---
title: "Splash screen reverts to text after 2 seconds"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by prvteprts on 2009-06-02
Hello.

After resizing my swap and main partitions and then when booting up, the splash screen appears for 2 seconds then disappears and I get the text based loading sequence which appears during recovery boot mode. (*Reading files needed to boot...)

It doesn't really affect anything, in fact, it seems to boot faster. However I am just wondering how and why this happened, and if there is a way to get it back to the original behavior.

---

### Post by Nixie Pixel on 2009-06-03
Please check /boot/grub/menu.lst and post the entry you are concerned about here.

It should look something like this:
```
title Ubuntu, kernel 2.6.17-10-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```

The "kernel" line above contains "quiet" (which hides the text during boot) and "splash" (logs in through the splash screen). You may not have "quiet," it seems.

---

### Post by pspsampsp on 2009-06-03
i had this problem ([http://ubuntuforums.org/showthread.php?t=1167553](http://ubuntuforums.org/showthread.php?t=1167553)) after changing my swap partion , i think it is because the uuid of a partion changes whenever you format/edit it. here is how i solved it :
I Ran the command "sudo blkid" which told me the uuids of my partitions.
I then ran "sudo gedit /etc/fstab" and made sure everything was correct in there.
Next I made sure the uuid in /etc/initramfs-tools/conf.d/resume ("sudo gedit /etc/initramfs-tools/conf.d/resume") was the same as the swap uuid.
After i had corrected those files i updated the initramfs ("sudo update-initramfs -u") and then restarted and presto all was fixed.

---

### Post by prvteprts on 2009-06-03
First of all, Nixie, I can't believe you replied to my post. I just found out about your YouTube channel a few days ago :D. I already checked menu.lst and it was ok. Btw, keep posting those nice vids about Ubuntu/GNU/Linux.

pspsampsp, I tried your fix, and it worked :D. When I edited the swap partition size, it wasn't mounting, so I edited fstab. So now it's obvious the problem is with initramfs resume. I was wondering though, what's the advantage of using the UUID in fstab? Why not just use /dev/<partition> by default?

Thanks to you both for your help.

---

