---
title: "Ubuntu as default OS"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by Dobbie03 on 2009-08-20
I have both Ubuntu and Crunchbang dual booting, I want to avoid the bit where you choose and have Ubuntu as the default OS that loads.  Is that possible to choose?  as well as having the option of booting Crunchbang when I want to use it.

---

### Post by earthpigg on 2009-08-20
in *whichever OS you installed _second_*,

install startup-manager and play with the settings and whatnot there. be careful when changing these settings, as a mistake on your part could be a pain to correct.

---

### Post by theaaronc on 2009-08-20
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by kestal on 2009-08-20
if you installed Ubuntu second, you'd just have to modify the grub menu around and switch the entries so that Crunchbang is first. I do this with my main computer as my parents still wish to use Windows, as I often mess around with Ubuntu a bit.

Jaunty's documentation is through that, but if your using Karmic..  has a different location for the new grub. Its no longer menu.lst, but

**Jaunty or Previous**
sudo gedit /boot/grub/menu.lst

[COLOR="Silver"]Karmic
sudo gedit /boot/grub/grub.cfg[/COLOR] (nevermind)

(or whatever you prefer when opening/editing)

**Warning:** Please be careful when editing this, as its dangerous if you set something wrong.

---

### Post by jrox717 on 2009-08-21
>  Karmic
sudo gedit /boot/grub/grub.cfg 

No, don't do this!
>  Unlike Grub Legacy's menu.lst file, grub.cfg is NOT MEANT TO BE EDITED!!! 
You can find out how to correctly edit Grub2 here: [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by agray on 2009-08-21
Thanks for the link jrox, that's answered some of my questions about grub version 2

---

### Post by kestal on 2009-08-21
> **jrox717 said:**
> No, don't do this!

You can find out how to correctly edit Grub2 here: [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Hmm... Thanks for the tip. I did it the way I mentioned before, and I did not run into any problems.. but I will take a look at that method.

---

### Post by jrox717 on 2009-08-21
I think the problem is that grub.cfg is overwritten every time you issue the command "update grub" (which is what you need to do after editing the files in the grub.d folder, as well as to update Grub2)

---

### Post by Dobbie03 on 2009-08-21
Thanks everyone I looked at grub\menu list.  There is no way in hell I am fiddling with that, I have no idea what I am doing.

---

### Post by LewRockwell on 2009-08-21
> **MattDobson said:**
> Thanks everyone I looked at grub\menu list.  There is no way in hell I am fiddling with that, I have no idea what I am doing.

the grub menu.lst file is easy to edit to your pleasure

we posted on it yesterday in case you are interested

.

---

### Post by Dobbie03 on 2009-08-21
I am interested where do I find this list?

---

### Post by Liolikas on 2009-08-21
There is file menu.lst in /boot/grub folder. Edit it and be careful not mess up too much or you end up with no boot at all.

---

### Post by eagle416 on 2009-08-21
anything that starts with a # is a comment, it will have no impact on the startup process. Usually stuff with a # will explain what everything does/ what it's for.

I believe near the top there is a countdown timer that it set to 10. Change this number to 1. This will look like "timeout                 1".

Next, find where it says "#hiddenmenu". Delete the # so it just says "hiddenmenu" (minus the quote marks).

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		1

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```

Now scroll down through a ton of examples until you're near the bottom. There will be the choices of OS in the order that they appear in GRUB. Find the one that you want to start automatically and move it to the top of the list (cut/paste).

```
title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		1fdff7db-0369-4fd5-a4cb-5e2de272ae6a
kernel		/vmlinuz-2.6.28-15-generic root=UUID=2ca651bd-7f8e-4f4c-a168-8da248486365 ro quiet splash 
initrd		/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		1fdff7db-0369-4fd5-a4cb-5e2de272ae6a
kernel		/vmlinuz-2.6.28-15-generic root=UUID=2ca651bd-7f8e-4f4c-a168-8da248486365 ro  single
initrd		/initrd.img-2.6.28-15-generic
```

Save. What this will do: First, instead of counting down from 10 before booting, it will start at only 1. Then the actual grub menu will be hidden, you won't be able to see it unless you hit ESC. Third, it will boot your preferred OS automatically.

YOU WILL NEED SUPERUSER PRIVILEGES AND YOU SHOULD MAKE A BACKUP OF MENU.1ST in case you mess something up. If you mess up and you can't boot at all, boot with a liveCD and restore the Original MENU.1ST.

---

### Post by Dobbie03 on 2009-08-21
Ok for some reason all mine show up as Crunchbang:


```
title		CrunchBang, kernel 2.6.28-15-generic
uuid		604fa28b-b439-4216-ad93-bb4c873b9611
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=604fa28b-b439-4216-ad93-bb4c873b9611 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		CrunchBang, kernel 2.6.28-15-generic (recovery mode)
uuid		604fa28b-b439-4216-ad93-bb4c873b9611
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=604fa28b-b439-4216-ad93-bb4c873b9611 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		CrunchBang, kernel 2.6.28-14-generic
uuid		604fa28b-b439-4216-ad93-bb4c873b9611
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=604fa28b-b439-4216-ad93-bb4c873b9611 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		CrunchBang, kernel 2.6.28-14-generic (recovery mode)
uuid		604fa28b-b439-4216-ad93-bb4c873b9611
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=604fa28b-b439-4216-ad93-bb4c873b9611 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		CrunchBang, kernel 2.6.28-11-generic
uuid		604fa28b-b439-4216-ad93-bb4c873b9611
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=604fa28b-b439-4216-ad93-bb4c873b9611 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		CrunchBang, kernel 2.6.28-11-generic (recovery mode)
uuid		604fa28b-b439-4216-ad93-bb4c873b9611
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=604fa28b-b439-4216-ad93-bb4c873b9611 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		CrunchBang, memtest86+
uuid		604fa28b-b439-4216-ad93-bb4c873b9611
kernel		/boot/memtest86+.bin
quiet
```

Any ideas?  would it be easier just to delete Crunchbang off and run it as Ubuntu only, I dont really care either way.

---

### Post by eagle416 on 2009-08-22
wow. you seem to have a lot of older kernals installed.... Rummage around in there until you find something that says Ubuntu 9.04 like mine. If you find it, just make sure it's at the top of the list.

If you can't find it post your entire menu.1st here and we can look through it.

---

### Post by Dobbie03 on 2009-08-22
Ok this is everything, I have no Ubuntu listed.  I do know for a fact that crunchbang is at the top when I goot then a few kernels down Ubuntu is there.  Anyway the list:
```

 menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=604fa28b-b439-4216-ad93-bb4c873b9611 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=604fa28b-b439-4216-ad93-bb4c873b9611

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
##      howmany=4
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		CrunchBang, kernel 2.6.28-15-generic
uuid		604fa28b-b439-4216-ad93-bb4c873b9611
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=604fa28b-b439-4216-ad93-bb4c873b9611 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		CrunchBang, kernel 2.6.28-15-generic (recovery mode)
uuid		604fa28b-b439-4216-ad93-bb4c873b9611
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=604fa28b-b439-4216-ad93-bb4c873b9611 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		CrunchBang, kernel 2.6.28-14-generic
uuid		604fa28b-b439-4216-ad93-bb4c873b9611
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=604fa28b-b439-4216-ad93-bb4c873b9611 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		CrunchBang, kernel 2.6.28-14-generic (recovery mode)
uuid		604fa28b-b439-4216-ad93-bb4c873b9611
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=604fa28b-b439-4216-ad93-bb4c873b9611 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		CrunchBang, kernel 2.6.28-11-generic
uuid		604fa28b-b439-4216-ad93-bb4c873b9611
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=604fa28b-b439-4216-ad93-bb4c873b9611 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		CrunchBang, kernel 2.6.28-11-generic (recovery mode)
uuid		604fa28b-b439-4216-ad93-bb4c873b9611
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=604fa28b-b439-4216-ad93-bb4c873b9611 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		CrunchBang, memtest86+
uuid		604fa28b-b439-4216-ad93-bb4c873b9611
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by eagle416 on 2009-08-22
I see.... and you can still select ubuntu at the GRUB stage of bootup?

---

### Post by Dobbie03 on 2009-08-22
Most definatly.  I will reboot and hand write the order of my grub and post it here.

---

### Post by eagle416 on 2009-08-22
that'll be great. Are Crunchbang and Ubuntu installed on separate partitions? I'm starting to think that GRUB might be using the menu.1st from Crunchbang, not Ubuntu. Go into the Crunchbang partition, look for a menu.1st in there, and see if the order on that one is the same as what you write down.

---

### Post by Dobbie03 on 2009-08-22
They are definatly on different partitions.  I will post what I come up with.

---

### Post by eagle416 on 2009-08-23
...anything?

---

### Post by Dobbie03 on 2009-08-24
Nothing, I accidentally killed my Ubuntu set up yesterday by trying to run openSuSE alongside it.  I reformatted and installed Kubuntu. 

Thanks very much for your help, it is appreciated.

---

### Post by eagle416 on 2009-08-24
no problem. Sorry that you had to start over.

---

### Post by Dobbie03 on 2009-08-25
Hey I don't mind.  It could have been worse.

---

