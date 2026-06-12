---
title: "grub 2 causes beeping on acer aspire"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by blade2445 on 2010-04-08
After installing grub2 (version 1.97~beta4-1ubuntu4.1) with ubuntu 9.10, my computer sometimes beeps continuously during startup. This happens with both 32-bit and 64-bit ubuntu. I've been fighting this issue for a while and my computers are usually dual boots with windows7 and ubuntu, so that may be part of the issue.

The computer is an acer aspire 4530 laptop. Grub begins to boot the ubuntu OS and shows the ubuntu icon while loading, but then suddenly starts to beep continuously very loudly. This doesn't occur during ever bootup, but maybe 1 in 10 times. Has anyone else had this problem and is there a workaround. Is there a way to go back to the old version of grub?

---

### Post by -humanaut- on 2010-04-08
Beeps generally aren't a good sign. Is it beeping pre-post? during post? generally beeps indicate some type of hardware/memory failure

---

### Post by blade2445 on 2010-04-08
It happens after POST and after I select an operating system (Ubuntu) in grub. It doesn't happen when booting windows7, only ubuntu. I don't think it's a hardware problem. I think it may be an issue with the mapping file in grub. The problem is tough to track down because it's intermittent, so I never know when it's going to happen. I have another dell laptop with pretty much identical OS configuration and this never happens, so it's something with the acer computer, maybe it is hardware. The beeping is constant and doesn't stop unless I shutdown the computer. 

The installed version of grub is grub-pc. This is what I get when I run 
sudo dpkg --configure -a

Setting up grub-pc (1.97~beta4-1ubuntu4.1) ...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Ubuntu 9.10 (9.10) on /dev/sda5
done

This may have fixed the problem, I don't know. It's a triple boot laptop with window7, ubuntu 9.10 32-bit, and ubuntu 9.10 64-bit.

---

### Post by -humanaut- on 2010-04-08
Does your particular model of Acer happen to have an ATI card in it?

---

### Post by Mark Phelps on 2010-04-09
Maybe the link below will help you identify the cause of your "beeps":

[http://www.computerhope.com/beep.htm]("http://www.computerhope.com/beep.htm")

---

### Post by wangsuda on 2010-04-09
I, too, have an Acer Aspire (4730z). I get two beeps during boot each and every time. I have no idea why, but I run just fine (no crashes, no nothing).

---

### Post by proxess on 2010-04-09
It simply happens when you were pressing a key before GRUB 2 actually appears. Acer BIOS are really really lacking, you can't turn off the internal Audio for example, and you can't turn off the internal speaker either.

---

### Post by blade2445 on 2010-04-09
Thanks for all the help. I don't think this a problem with POST because OS loading gets to the grub boot menu. And if I boot into windows, the beeping never occurs, only in ubuntu 9.10 (both 32-bit and 64-bit versions). The problem did not seem to occur with ubuntu 9.04, which makes me think it's not a hardware failure issue.

It's doubtful that I'm just pressing a key during bootup to cause this error since I think it has occurred several times without me touching it, but I'm not certain. The video card is a nvidia GEFORCE 9100 M TurboCache. I wouldn't be surprised if it was a video card issue but there's no easy way to find out. I'm using another computer now, but the beeping on this computer was like a police siren and it would go off randomly in class, the library or anywhere I was booting the computer. 

The beeping hasn't occurred recently, so maybe it was a mapping file error in grub that was fixed.

---

