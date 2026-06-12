---
title: "Dual booting on external issues"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by pokera75 on 2010-06-01
Hello all,

I recently installed ubuntu on an external drive using the entire drive to install it. I did this in the hopes of being able to boot from my windows 7 partition no matter what when I'm not connected to the drive, and when I am using grub to choose between the two. 

The installation went smoothly. I did nothing to alter my internal drive's partitions. I simply installed to the external drive. The first time I booted I ran into issues where even if I was connected to the external drive, grub would throw an error about not being able to find the drive. It gave the drives giberish hardware ID if I remember correctly. After a bit of searching what to do I found a tutorial which I can't find now.

Anyways what I did was like this one for grub in the MBR section
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20and%20Boot%20Manager](https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20and%20Boot%20Manager)

after that I pulled out my 7 cd and used the console and the 2 bootrec.exe commands.

This seemed to solve the problem. 

However, I guess maybe a recent update or something changed that. Today, I got to work without my external and tried to boot. Instead of going directly to the windows 7 it booted grub. Which of course failed to find the external drive because it is at home. Basically I don't want to go through the same steps constantly to fix the boot loaders after every update. 

I'm wondering if I should how would I install a complete installation of grub on my main hard drive. Thus I would always use grub to boot and select what I wanted to boot.

---

### Post by NUboon2Age on 2010-06-01
From [this other thread]("http://ubuntuforums.org/showthread.php?t=1498913"), something that might be useful:
[egalIvan]("http://ubuntuforums.org/member.php?u=521362") wrote:
"GRUB can be set up on the main boot drive, or you can even set up GRUB with it's own partition...

here is a link to a how-to on that...

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)"

Which says
"Why would anyone want a 'Dedicated GRUB 2 Partition?

When GRUB 2 is in its own dedicated partition it is 'operating system independant', so we can add or remove one or two operating systems without the inconvenience of losing the boot of the remaining operating systems... "

---

### Post by oldfred on 2010-06-01
Grub remembers or defaults - this should change that comments by others that I copied. change drives or partitions to yours from this posters notes

reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
[COLOR=DarkRed]sudo dpkg-reconfigure grub-pc[/COLOR]
I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/debconf/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda2 after grub-pc package updates to keep stage1 install in sync.

---

