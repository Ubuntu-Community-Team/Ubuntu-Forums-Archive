---
title: "Fixing Startup code"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by NewBee2113 on 2010-03-17
A while back I had some issues launching Ubuntu, which I seemed to have fix by altering what I think is GRUB/kernel.

When I got the screen (after some hard restarts) that says Start Generic x.20 or in Recovery Mode or you can hit 'c' to commnd or 'e' to edit.  I have been hitting 'e' to edit.  Some series of "code" pops up and I have been erasing "quiet splash" and replacing it with "acpi=off".  This has worked and no problems running computer/ubuntu.

My question is:  how do I permanently incorporate this change, so that each time I shut down the computer at the end of the night I don't have to go through this process these the next day.  (couple of hard restarts before getting to the "Grub Screen".

Thanks for the help.

Any tips on getting my soundcard, and wireless connection working will be next...thx

---

### Post by rCXer on 2010-03-17
Do you have grub or grub2.  If you have grub you have to edit your boot menu which is stored in "/boot/grub/menu.lst".  Be very careful.  If you mess up Ubuntu will fail to boot.
* Back up your menu.lst in case you make a mistake.
```

cd /boot/grub/
sudo cp menu.lst menu.bak

```

* Open menu.lst.
```

gksudo gedit menu.lst

```

* Scroll down until you see the list of kernels.  Mine looks like this.
> 
...

title		Ubuntu 9.04, kernel 2.6.28-18-generic
uuid		05c96d83-05fd-4013-9fea-6035a543782d
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=05c96d83-05fd-4013-9fea-6035a543782d ro **[COLOR="Red"]quiet splash[/COLOR]** 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid		05c96d83-05fd-4013-9fea-6035a543782d
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=05c96d83-05fd-4013-9fea-6035a543782d ro  single
initrd		/boot/initrd.img-2.6.28-18-generic
...


* Change **[COLOR="Red"]quiet splash[/COLOR]** to **acpi=off** for your kernel.

---

### Post by linuxman94 on 2010-03-17
Do you have grub2 or grub-legacy?

---

### Post by rCXer on 2010-03-17
See above post

---

### Post by rCXer on 2010-03-17
Double post sorry again :(

---

### Post by NewBee2113 on 2010-03-18
Grub 2 i believe.  I downloaded the newest Ubuntu 9.10, so i think it is GRUB 2  xxx.20

---

### Post by NewBee2113 on 2010-03-19
When I typed the code above to edit:  

gksudo gedit menu.lst




A blank "Windows-style" screen opens up with nothing inside to scroll.  Suggestions?

---

### Post by tom.swartz07 on 2010-03-19
> **NewBee2113 said:**
> When I typed the code above to edit:  

gksudo gedit menu.lst




A blank "Windows-style" screen opens up with nothing inside to scroll.  Suggestions?

Try
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by NewBee2113 on 2010-03-19
NO luck, I opened the terminal and typed:

gksudo gedit /boot/grub/menu.lst

the same blank "window" opens with just a blank cursor designated at line 1 col 1.

---

### Post by PocketDog on 2010-03-19
```
gksudo gedit /etc/default/grub
``` Make the required changes, then ```
sudo update-grub
``` It's important to do the second bit

---

### Post by tom.swartz07 on 2010-03-19
> **PocketDog said:**
> ```
gksudo gedit /etc/default/grub
``` Make the required changes, then ```
sudo update-grub
``` It's important to do the second bit

+1

Since my last method didnt work, you (by process of elimination) have GRUB legacy. 

Use this method and itll fix you right up.

---

### Post by NewBee2113 on 2010-03-26
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=[COLOR=Red]acpi=off[/COLOR]
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

[SIZE=3]

[FONT=Arial][SIZE=3]ok it worked and I did the required changes: (i changed highlighted portion from ="quiet splash" to =acpi=off)

However, now my mouse does not work.  USB mouse and the light underneath mouse comes on, so there is power, but it will just not move cursor.  the touchpad still works though.  Any thoughts?[/SIZE][/FONT][/SIZE]

---

