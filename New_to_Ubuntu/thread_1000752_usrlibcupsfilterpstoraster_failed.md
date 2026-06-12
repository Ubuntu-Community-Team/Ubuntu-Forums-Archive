---
title: "/usr/lib/cups/filter/pstoraster failed"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by T4K3Z0U on 2008-12-03
Hey folks, it's been a while since I have needed your help. Actually a year and a few days, according to the last log in date.ied to print, i got the a

Anyway straight to my problem. I have updated to version 8.04 and don't know whether or not I had printed anything since updating, but today when I tried to print, I got this message.

> /usr/lib/cups/filter/pstoraster failed

Now I googled it, so don't say "just f**king google it." What I found was [this]("https://answers.launchpad.net/ubuntu/+question/43058") place. I typed in "ID" into terminal, and this is what it spat out at me.

> t4k3z0u@T4K3Z0U:~$ id
uid=1000(t4k3z0u) gid=1000(t4k3z0u) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),125(sambashare),1000(t4k3z0u)


Looks pretty much the same as the fellows problem on supplied link, but I can't still get mine to work.

Any suggestions?

---

### Post by Michael.Godawski on 2008-12-03
On the launchpad page you linked to, the guy says his issue is solved since he updated the kernel.
On what kernel are you?
```
uname -a
```

---

### Post by T4K3Z0U on 2008-12-03
That would be 

> t4k3z0u@T4K3Z0U:~$ uname -a
Linux T4K3Z0U 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux

I wasn't sure about the kernel part, because since updating my version, the startup thing.... GRUB (is it?) shows now 4 Ubuntu kernels.

---

### Post by Michael.Godawski on 2008-12-03
Can you please post the result of 

```
cat /boot/grup/menu.lst
```

Did you try to boot into a older kernel and check if the printer is working?

---

### Post by T4K3Z0U on 2008-12-03
> **Michael.Godawski said:**
> Can you please post the result of 

```
cat /boot/grup/menu.lst
```

I figure I done something wrong, I don't know how to use terminal very well.

> t4k3z0u@T4K3Z0U:~$ cat /boot/grup/menu.lst
cat: /boot/grup/menu.lst: No such file or directory
t4k3z0u@T4K3Z0U:~$ /boot/grup/menu.lst
bash: /boot/grup/menu.lst: No such file or directory


> **Michael.Godawski said:**
> Did you try to boot into a older kernel and check if the printer is working?

I have no idea which is older and which is newer. I'm so clueless when it comes to computers, I make the term "green" sound like a compliment.

---

### Post by Michael.Godawski on 2008-12-03
mea culpa

typo, sry

```
cat /boot/grub/menu.lst
```

---

### Post by T4K3Z0U on 2008-12-03
I have absolutely no idea what any of this means.

t4k3z0u@T4K3Z0U:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=fd4fa1f0-07bd-41ba-b56d-00a25aeb8f2b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=fd4fa1f0-07bd-41ba-b56d-00a25aeb8f2b ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=fd4fa1f0-07bd-41ba-b56d-00a25aeb8f2b ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=fd4fa1f0-07bd-41ba-b56d-00a25aeb8f2b ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=fd4fa1f0-07bd-41ba-b56d-00a25aeb8f2b ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fd4fa1f0-07bd-41ba-b56d-00a25aeb8f2b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fd4fa1f0-07bd-41ba-b56d-00a25aeb8f2b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fd4fa1f0-07bd-41ba-b56d-00a25aeb8f2b ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fd4fa1f0-07bd-41ba-b56d-00a25aeb8f2b ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Michael.Godawski on 2008-12-03
The important part is at the end. It tells us what kernel versions are available. I see four different ones:

Ubuntu 8.04.1, kernel 2.6.**24-22**-generic
Ubuntu 8.04.1, kernel 2.6.**24-21**-generic
	Ubuntu 8.04.1, kernel 2.6.**22-14**-generic
Ubuntu 8.04.1, kernel 2.6.**20-16**-generic

Comparing the numbers we see which one is the newest and which one the oldest.
Just try to boot into one of the - perhaps the kernel before the upgrade - and check if everything is correct. Do not boot into the recovery mode.

If you find a working kernel change the default boot number which is rather at the beginning of the file from 0 which means the first entry is going to be executed to the kernel you want. 

To do so open the menu.lst with this command (after making a backup) and save then:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst

```

---

### Post by T4K3Z0U on 2008-12-04
> **Michael.Godawski said:**
> The important part is at the end. It tells us what kernel versions are available. I see four different ones:

Ubuntu 8.04.1, kernel 2.6.**24-22**-generic
Ubuntu 8.04.1, kernel 2.6.**24-21**-generic
[COLOR="Red"]Ubuntu 8.04.1, kernel 2.6.**22-14**-generic[/COLOR]
Ubuntu 8.04.1, kernel 2.6.**20-16**-generic

Comparing the numbers we see which one is the newest and which one the oldest.
Just try to boot into one of the - perhaps the kernel before the upgrade - and check if everything is correct. Do not boot into the recovery mode.

I tried 2 others so far. The kernel in red there, works a little, but there are a problem or 2. I can't setup paper size anymore, and it doesn't seem to be printing properly. When I tried to print a photo, it took a while printing, but the paper came out blank, which makes me think that ink went squirting all over the inside of my printer.

Actually I tried all the kernels, but didn't print from the last one there, when I noticed it doesn't let me change paper sizes. 
Is it I'm missing a driver or some other software for paper sizes since my updrade to V.8.04?

---

### Post by T4K3Z0U on 2008-12-12
The other day there were updates for Ubuntu. They happened to be cups or cupsy? I remembered this has something to do with printers, so decided to try my printer after the updates, and it worked on the number one kernel.

---

