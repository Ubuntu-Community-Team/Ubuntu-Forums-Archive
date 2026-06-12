---
title: "linux mint"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by misswham on 2010-02-24
i have been trying to put linux mint on a flash drive and there aren't many people on the linux mint site and i thought I would post my question here.



   usb reading for helena

Postby misswham on Sun Feb 21, 2010 5:58 pm

Hi there. I am new to Linuxmint but not ubuntu. I installed it to a 8 gb flash and it installed fine, but my confusion is that when I went to my BIOS settings I didnt see where I could boot into a flash. I should have checked it first. It says removable, cdrom yada yada. I chose network option and i saw the helena and i highlighted and hit enter and the grub menu came up but nothing happens. It wont do anything when i hit enter and it wont let me move the arrows up or down. It is as if it is frozen. What does this sound like and do you all think that my computer CAN boot from a flash? ON my laptop, which is only one year old a Toshiba Satellite, I dont see a boot from usb or flash either.


Re: usb reading for helena

Postby misswham on Mon Feb 22, 2010 4:50 pm

I went to the boot menu and selected Hard Disk and there was my flash listed. It says USB-HDDD:Patriot Memory PMAP. I hit enter and it started and went to the Grub and the Helena is the first choice. I hit enter and nothing happened. So i went through it again and this time at the bottom of grub it said operating system chosen with start in and then it counted down to 0 but after that nothing happened and it acted as if it was frozen. Also while I sat there and looked at the flash drive the red light on it is continuously flashing. I also installed the system on a completely different flash drive and the same is happening. What does it sound like now? Also the grub menu that has Helena on it also have the other 2 operating systems listed also as a choice. I have XP and Ubuntu 8.04 on it. I didnt think that the grub on my flash drive would know anything about what was on my internal harddrive.

by misswham on Tue Feb 23, 2010 10:17 pm

I finally got it to boot on my laptop and it worked wonderfully. I did the 196 updates and then browsed a bit but then i logged off. When I logged on i got past grub and the next screen stalled and it says

mount: mounting /dev/disk/by-uuid/2010efa8-0dc5-a1dd-234258703155 on /root
failed? Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/ sys failed: No such file or directory
mount: mounting / proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing inut= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

why did this happen and what should i do?

also it still never made it past grub on my desktop



These are the questions i posted over there but got only one response after a day.  They dont have very many people on there.  3 questions.

1.  Does anyone know why I am having the problems above?

2.  Can I get Linux mint support on this site?

3.  If I decide to use Linux Mint, do I have to erase my harddrive   totally and start over or can I just override my harddrive with the linux mint installation cd?

---

### Post by spiderbatdad on 2010-02-24
Many people ask for linux mint help here; so you are not alone.

It sounds like you were running from an 8gb flash drive with the OS installed...that is not a live usb. Therefore when you installed updates you probably exceeded the capacity of the device and broke the installation.

It is possible to run from a live usb just like from a live cd but you cannot update the system...there is sometimes a little room left for user preferences.

You can use the partitioning tool on the installer to use the space Ubuntu currently occupies if you want to install mint in place of Ubuntu on your HDD.

---

### Post by BrandonBan6 on 2010-02-24
I have followed these instructions:
[http://www.pendrivelinux.com/create-a-linux-mint-8-usb-flash-drive-from-cd/](http://www.pendrivelinux.com/create-a-linux-mint-8-usb-flash-drive-from-cd/)

Put it on an 8gb flash drive runs great... not sure how the steps differ from yours, but may be worth a looksie.

---

### Post by misswham on 2010-02-24
Oh ok so I shouldnt update.  I kinda figured that.  Now I have installed it on another flash drive and it works fine on my laptop.

The next question is when I boot from the same USB flash drive it takes me to the grub menu and then it freezes.  It will say it is counting down and it will boot in the os chosen but it never does. I then rebooted and when it got to grub, I hit enter and nothing happens.  The light on the flash drive is REALLY blinking but it never goes past the grub menu.  What does it sound like is happening, because I will purchase an external harddrive and put it there if I can figure out how to get past the grub on my desktop and get into Mint.  Also can I use the partitioning tool on the installer to add yet another OS?  I already have XP installed first and Ubuntu installed second.

PS  I have tried to boot in every USB port on my PC. and still the same, stops at grub but works fine on laptop.

---

