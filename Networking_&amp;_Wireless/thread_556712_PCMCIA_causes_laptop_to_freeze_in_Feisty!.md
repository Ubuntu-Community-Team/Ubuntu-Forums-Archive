---
title: "PCMCIA causes laptop to freeze in Feisty!"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by houms on 2007-09-21
My laptop freezes when I boot with my wireless Motorola w825gp PCMCIA card inserted and it is on battery power. It works fine if I boot with the AC adapter plugged in, but booting on battery power causes it to freeze up. Couple of observations: If I boot on AC and then unplug the AC after the network interface has been configured, it runs fine. Even if I reboot on battery power it will restart fine. But starting with just the battery the laptop freezes, even if i wait until I logged in to insert the card. 
But when it freezes, if I take the card out it  "unfreezes" and continues to load and work as normal. But if I try to plug the card in again in the same session, it freezes. Unplug unfreeze, plug it again and it freezes. Its not until I shutdown and plug AC in, then boot the laptop back up that the wireless card will start working again. This is a Dell Inspiron 8600, the motorola PCMCIA is using the 4306 broadcom chipset and I am using ndiswrapper, I blacklisted the bcm43xx driver which is the default driver used for this chipset using the following command:

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

If anyone has any ideas on this one. It would be greatly appeciated......

---

### Post by kevdog on 2007-09-21
Try booting the kernel with the noapci, nolapci flags.  Its probably more due to the poorly written power management routines, these commands might bypass or turn off these options.

---

### Post by houms on 2007-09-21
Thanks for the prompt reply kevdog.
forgive my ignorance but I assume i have to add that to my /boot/grub/menu.lst file. 
I did so like this. I dont know if this is correct or not... but it did not work unfortunetly..please let me know if there is anything else you can think of...

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d2647ece-d0f0-4f26-a63b-94229a9e7919 ro [COLOR="Red"]noapci nolapci[/COLOR] quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d2647ece-d0f0-4f26-a63b-94229a9e7919 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d2647ece-d0f0-4f26-a63b-94229a9e7919 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d2647ece-d0f0-4f26-a63b-94229a9e7919 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by kevdog on 2007-09-21
You did that correctly -- did it make any difference??

---

### Post by houms on 2007-09-22
unfortunately it had no effect... Any thing else you can suggest would be appreciated... Additionally if i leave those options in, what effect, if any , will it have...? I hear it does not effect single processor systems...? Thanks kevdog

---

### Post by kevdog on 2007-09-22
There are a few more kernel options you could try, but I dont remember the options off the top of my head.  Do a search on the forum for kernel options -- they are usually associated with the system crashing after if goes into hibernation.  Im not exactly sure if this would solve your problem, but it is worth a shot.  Things are always reversible.

---

