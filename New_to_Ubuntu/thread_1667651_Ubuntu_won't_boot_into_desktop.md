---
title: "Ubuntu won't boot into desktop"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by Norman Thom on 2011-01-15
Well here's the story, a stupid one.
I had previously used Ubuntu dual booted with XP on one computer.
Both OSs were on separate drives. I got another computer and thus gave Ubuntu it's own machine. In doing so I thought as I now longer needed to choose my Operating system I would uninstall the start up manager. Now Ubuntu will only start up in the Memory Test configuration ( a very long process ). does anyone know how I can correct this problem and have it boot correctly.  Thanks

---

### Post by Quackers on 2011-01-15
Try holding down the shift key during boot. This should bring up the grub menu where you will be able to choose to boot Ubuntu (top item). When it boots up, change the default selection in SUM.

OOPS, it may be the Esc key if you are using 9.04

---

### Post by Norman Thom on 2011-01-15
Quackers.  You say that I can change my default selection in 'SUM' could you explain what this is , how I access it and use it.  Thanks Norm

---

### Post by Quackers on 2011-01-15
StartUpManager :-) . Or is it now gone? Don't despair, we can fix it if you can get it booted up. Did you see my edit in the first post? It may be Esc to be held down, if you are using 9.04

---

### Post by Norman Thom on 2011-01-15
Quackers:  Sorry for the omission, using Ubuntu 10.10.  Will try your suggestion and respond as to result.  Norm

---

### Post by Norman Thom on 2011-01-15
Ok.  I tried to boot holding down the Shift key.  It did open the startup manager but for some reason I was unable to change the setting as my keyboard was disabled.  this may have something to do with the fact that I am running both machines on the one monitor using a KVM switch.  do you have any other suggestions or must I now reinstall the whole OS thus losing all the info on that drive.  Norm

---

### Post by Quackers on 2011-01-15
Hmm, on the grub menu was Memtest the highlighted option? I presume so. Do you have a usb keyboard that you can plug in? Or are you already using one?

---

### Post by Norman Thom on 2011-01-15
Already using USB keyboard

---

### Post by Quackers on 2011-01-15
I can think of only one thing now.
Try booting from the live cd/usb and choosing "try ubuntu". When the desktop loads you can chroot into your existing system and edit /etc/default/grub to change the default boot option and/or turn off Memtest options.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Norman Thom on 2011-01-15
Forgive me again Oh great and mighty Linux mage :)
This chroot you speak of how do I access it and how do I use it.
Can I find the information in the document you suggested.
Norm

---

### Post by Quackers on 2011-01-15
The shortest method I know of is as below. Bear in mind that you must change the partition number (in red) to match your own /root partition number.
```
sudo mkdir /mnt/temp
sudo mount /dev/[COLOR="Red"]sda3[/COLOR] /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
sudo chroot /mnt/temp[COLOR="Black"][/COLOR]

```
At this point your terminal prompt should change from ubuntu@ubuntu to root@ubuntu

---

### Post by Norman Thom on 2011-01-15
Thank you Quackers you have been very helpful.  I now know which way to proceed.  Norm

---

### Post by Quackers on 2011-01-15
Go for it :-)

---

