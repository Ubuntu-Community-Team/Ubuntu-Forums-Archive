---
title: "Problem in dual boot (ubuntu 8.04.1) with RHEL 4"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by chanakyakv on 2008-12-05
Hi,

My partitions are as shown below (screenshot taken using ubuntu live session)
> Please look at the attached png image.

sda1, sda2, sda3, sda5 - are used by RHEL4 (Redhat Enterprise Linux 4)

sda6 & sda7 by Ubuntu Desktop 8.04.1

Initially I had only RHEL4 on the entire hard disk. I created partitions sda6 & sda7 while installing ubuntu. During Ubuntu installation I selected to install grub on /dev/sda6 as I dint want to disturb the grub installation (on MBR) already present while I was using RHEL4.

Now after installing ubuntu, I'm not able to boot it. I have tried exhaustive ways editing /boot/grub/menu.lst inside RHEL4 to add ubuntu to my grub booting list but in vain.

Right now my /boot/grub/menu.lst file inside RHEL4 looks as follows:
```
default=0
timeout=5
splashimage=(hd0,0)/grub/splash.xpm.gz
hiddenmenu
title Red Hat Enterprise Linux WS (2.6.9-67.EL)
	root (hd0,0)
	kernel /vmlinuz-2.6.9-67.EL ro root=LABEL=/ rhgb quiet
	initrd /initrd-2.6.9-67.EL.img
title Ubuntu 8.04.1, kernel 2.6.24-19-generic
	root (hd0,5)
	kernel	/boot/vmlinuz-2.6.24-19-generic root=UUID=c5ac35ad-8e47-4698-92c6-02e2643f4cc5 ro quiet splash
```

I have even tried the below:
```
kernel	/boot/vmlinuz-2.6.24-19-generic root=/dev/sda6 ro quiet splash
```
and
```
kernel	/boot/vmlinuz-2.6.24-19-generic root=/dev/hda6 ro quiet splash
```

Ubuntu is not even getting listed in boot menu list when I power on my laptop.

And if I try to do a forcible boot by manually feeding the grub commands at the grub command prompt, it hangs with an error saying:
```
root=[invalid device]
```

Please help or get back to me for more questions if unclear.

Thanks & Regards,
CHANAKYA K V

---

### Post by pdtpatrick on 2008-12-05
Looks to me you only have / directory specified which is in one of the higher partitions.. the other is /mnt/root and /home .. are those suppose to be ubuntu? If so might want to repartition your drives.. since RHEL is working fine.. create new partitions for ubuntu .. you will need /boot and / and if you want to use /home or /usr ... up to you but u gonna need /boot and / to setup initially.. 

you can also restart and go into single user mode .. when you boot hit space at the splash screen and press e to edit the highlighted selection (say maybe RHEL) .. then once you get to the next screen, press e again to edit and at the end of the line add single and then save it and boot.. that will take you to a screen where you can edit all your files on your system ..

---

### Post by handydan918 on 2008-12-05
Why people insist on installing grub somewhere else is beyond me...

Looking at your menu.lst, i notice a suspicious line:

```
default=0
timeout=5
splashimage=(hd0,0)/grub/splash.xpm.gz
[COLOR="Red"]hiddenmenu[/COLOR]
title Red Hat Enterprise Linux WS (2.6.9-67.EL)
	root (hd0,0)
	kernel /vmlinuz-2.6.9-67.EL ro root=LABEL=/ rhgb quiet
	initrd /initrd-2.6.9-67.EL.img
title Ubuntu 8.04.1, kernel 2.6.24-19-generic
	root (hd0,5)
	kernel	/boot/vmlinuz-2.6.24-19-generic root=UUID=c5ac35ad-8e47-4698-92c6-02e2643f4cc5 ro quiet splash
```

I think I would try commenting that line out just to see what happens. You can change it back easily enough...

EDIT: Confirmed in man grub:

```
Command: hiddenmenu
    Don't display the menu. If the command is used, no menu will be displayed on the control terminal, and the default entry will be booted after the timeout expired. The user can still request the menu to be displayed by pressing ESC before the timeout expires. See also 12.4 The hidden menu interface. 

```

---

