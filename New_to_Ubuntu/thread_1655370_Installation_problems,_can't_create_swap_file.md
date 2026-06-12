---
title: "Installation problems, can't create swap file"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by TheDauntless on 2010-12-29
Hi,

I'm experienced in windows & OSX, but completely new to Ubuntu.

I have a laptop (Dell XPS M1730) which has 2 harddrives. One of them contains my W7x64 installation and the other is currently unpartitioned.

So, I downloaded the ubuntu CD and burned it to a disk. I tried creating a swap partition (8000mb, type:swap, mountpoint:  /swap, primary) and another one after that (140gb, type:ext4, mountpoint: /, logical) and clicked next.

At that point, ubuntu tells me that it was unable to create the SWAP file. (It tries for half a minute and then I get an error). Unfortunately I don't remember the error. If you guys want I'll try again and write it down. (It was something like 'unable to mount swap file')

Also, if I install ubuntu on the second drive, should I select my primary (W7) drive as the bootloader or should I select the drive that Ubuntu is on ?

Greets!

---

### Post by seawolf167 on 2010-12-29
Here is the [Ubuntu/Windows Dual Boot guide]("https://help.ubuntu.com/community/WindowsDualBoot")

If you create a swap partition, type=swap, you shouldn't have to set a mount point (it should become grayed out)

Example partition setup:

size - type - mount
50GB - ext4 - /
50GB - ext4 - /home
4GB - swap - n/a

Traditionally swap has been 2x your RAM size (though 2GB is more than fine with most modern computers)

As for the bootloader, you should NOT overwrite your windows loader. Grub2 (the Ubuntu bootloader) will load stage one, then if you choose to boot to windows (from the grub menu), it'll point to the drive/partition and load into windows stage 2.

---

### Post by lance bermudez on 2010-12-29
my hard drive is not big enough for the guid so i jus have 2 partions on windows xp and the other is ubuntu. in the ubuntu i installed i have a 2 gb swapfile. to make the swapfile keep every command in the same place i put mine in /
open terminal

cd /
sudo dd if=/dev/zero of=/swapfile bs=1M count=2048
sudo mkswap /swapfile

to add to fstab so that the swapfile is turned on at startup
you can use mousepad, egedit, nano, or vi as your text editor i use gedit

open terminal
sudo gedit /etc/fstab

go to the end of the file and add

/swapfile none swap sw 0 0

at the next restart the 2gb swapfile will be added

---

### Post by TheDauntless on 2010-12-29
Some screens:
[IMG]http://img218.imageshack.us/i/imag0053h.jpg/[/IMG]
[IMG]http://img190.imageshack.us/i/imag0054pn.jpg/[/IMG][img]http://img218.imageshack.us/img218/6976/imag0053h.jpg[/img]

[img]http://img190.imageshack.us/img190/387/imag0054pn.jpg[/img]
[img]http://img155.imageshack.us/img155/9889/imag0055yc.jpg[/img]

What am I doing wrong ?
[IMG]http://img155.imageshack.us/i/imag0055yc.jpg/[/IMG]

---

