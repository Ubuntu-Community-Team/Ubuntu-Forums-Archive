---
title: "Softresets Failed and a Fatal During Boot"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by SoulMazer on 2009-05-12
When I had Ubuntu 8.10, I was perfectly fine. But, as soon as I upgraded to Jaunty via the Update Manager, I have had three errors during my boot sequence. They do not prevent me from booting normally, however the fatal slightly scares me.

The three errors I get are:

> [2.376018] ata1: softreset failed (device not ready)
> [3.472017] ata3: softreset failed (device not ready)
> modprobe: FATAL: could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory

From a quick Google search, I am guessing the first two errors have to do with hardware problems, and I have no idea about the third error. Would anybody be able to explain/tell me the solution to these errors?

Thank you in advance.

---

### Post by bswilson on 2009-05-12
Your problem is that your storage (hard disk drive) controller's driver isn't properly compiled for the kernel that was installed when you upgraded to Jaunty.  You can fix this by using initramfs instead of initrd in the boot sequence.  I'm going to assume you're using grub as the boot loader.  Try these steps.

1. Install inintramfs-tools.

```
sudo apt-get -y install inintramfs-tools
```

2. Configure inintramfs to recognize the kernel you want to run.

```
cd /boot && sudo update-inintramfs -c -k 2.6.28-11-generic
```

3. Apply your newly created bootloader instruction set to the grub menu, so that it'll be used when you reboot.

```
sudo echo "initrd        /boot/initrd.img-2.6.28-11-generic" > /boot/grub/menu.1st
```

4. Reboot to make changes effective.

5. Celebrate.

---

### Post by SoulMazer on 2009-05-12
Thanks for the detailed reply, bswilson, but when I try to get the inintramfs-tools, I get an error that says it was unable to find that package. Do I need to add something to my list of software sources or what?

Thanks again.

---

### Post by Jazzy_Jeff on 2009-05-12
I had those same errors when I tried to run the live cd to install Ubuntu 9.04 and the system would not boot into the live cd.

I downloaded the alternate install cd and that worked fine for installing. I still get the first two errors at boot up but Ubuntu loads fine afterward and everything runs fine.

---

### Post by SoulMazer on 2009-05-12
Thanks for the info Jeff, however I am looking for a solution that does not require a complete reinstall.

---

### Post by Colin@oxford on 2009-05-16
I see "softreset failed" messages when I upgraded to Jaunty.  They appeared when I booted from disk and are still there after the install.  However, they also existed in the syslog of Intrepid (and probably Hardy) but just did not appear on the screen.  I think (hope!) that it is safe to ignore them.

My message pair is:
ata2: softreset failed (device not ready)
ata2: failed due to HW bug, retry pmp=0

---

### Post by khamil8686 on 2009-05-18
many people replied that they cannot find the package, inintramfs is supposed to be intramfs. i ran all this code and it didnt work for me. the first part i did through synaptic because i also ran into the cant find package and found it was just a typo. so i updated intramfs-tools to the most recent version and then tried to run the second part, no problems here, the third line of code looks like it replaces your whole /boot/grub/menu.lst file with "initrd        /boot/initrd.img-2.6.28-11-generic" which i dont think it is meant to do because that would mess up grub i believe, menu.lst gives you the listing of all oses on the computer, > means overwrite, as opposed to >> which is append, and the line of code even as sudo wont run on my computer, i was denied even as sudo! either way. hopefully bswilson sees this and can come back and clarify :) i think (hope?) this error is related to my problem of being able to suspend once just fine, then on resume gnome-power-manager puts a plug in my tray saying it cant get data... and then i cant suspend again. if i logout and back in it tells me HAL failed to initialize and locks up, warranting a hard restart. maybe this has to do with the HAL module not being properly loaded on boot? i unno. shooting in the dark is fun :) just trying not to hit my foot :P

---

### Post by khamil8686 on 2009-05-19
look at this: [http://ubuntuforums.org/showthread.php?p=7311539]("http://ubuntuforums.org/showthread.php?p=7311539")

---

### Post by Colin@oxford on 2009-05-20
This might be relevant for the softreset:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285392]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285392")

---

