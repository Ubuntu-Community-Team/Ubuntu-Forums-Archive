---
title: "Touchpad not working"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by nyvietvet on 2010-12-02
I have read previous posts showing this problem as solved...
 	Quote:
 	 	 		 			 				 					Originally Posted by **Oaty** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10153659#post10153659") 				
 				[I]Here&#8217;s the fix:

1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX=&#8221;i8042.nopnp&#8221;
2. Run: sudo update-grub
3. Reboot.[/I]
 			 		 	 	 
here's what I get:

bill@bill-VPCEE3WFX:~$ sudo update-grub
[sudo] password for bill: 
/etc/default/grub: 1: &#65279;#: not found

Sony Vaio VPC laptop, AMD Athlon II P340 Dual Core, 2200 Mhz CPU, 4GB DDR3 RAM, 500 GB hdd

---

### Post by Zookalicious on 2010-12-02
Try typing 
```

sudo grub-install
sudo update-grub

```
and then trying the original directions (including updating grub a second time). It sounds like you simply don't have grub set up.

---

### Post by nyvietvet on 2010-12-06
> **Zookalicious said:**
> Try typing 
```

sudo grub-install
sudo update-grub

```
and then trying the original directions (including updating grub a second time). It sounds like you simply don't have grub set up.
Thanks, Zook, my neighbor to the North.  Here's what I get:

bill@bill-VPCEE3WFX:~$ sudo grub-install
[sudo] password for bill: 
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
  --disk-module=MODULE    disk module to use

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into /boot/grub (or /grub on NetBSD and
OpenBSD), and uses grub-setup to install grub into the boot sector.

If the --root-directory option is used, then grub-install will copy
images into the operating system installation rooted at that directory.

I then tried:

bill@bill-VPCEE3WFX:~$ sudo grub-install--root-directory, and got:

sudo: grub-install--root-directory: command not found

Now what?

---

### Post by Zookalicious on 2010-12-06
Oh man, silly me, I forgot that you need to specify where grub is to be installed. 

Type in 
```

sudo fdisk -l

```That will show you how your drive is set up. Now, assuming you only have one hard drive, the very first line after you input your password should say something like **"Disk /dev/sda: 1000.2 GB, 1000204886016 bytes" **Which is an example from my computer.  What comes right after the word "Disk" is what you are going to use in the grub-install command. So for my example I would type in:

```

sudo grub-install /dev/sda

```If you get errors, try 
```

sudo grub-install --recheck /dev/sda

```Then finally just to refresh grub...
```

sudo update-grub

```Sorry, can't believe I missed that :P you should have better luck with these commands.


Edit: I just noticed your signature, and it made me chuckle.

---

### Post by owiknowi on 2010-12-07
Maybe way to simple:
I ran into the same problem on several notebooks.
-On one notebook the touchpad was disabled in it's BIOS(!)
-On another the key combination Fn+Fx (x stands for the key enable/disable touchpad) was turned on by default.

---

### Post by nyvietvet on 2010-12-11
Worked like a charm, zook.  Thanks ever so much.

---

### Post by Zookalicious on 2010-12-11
Fantastic :) glad to help.

---

