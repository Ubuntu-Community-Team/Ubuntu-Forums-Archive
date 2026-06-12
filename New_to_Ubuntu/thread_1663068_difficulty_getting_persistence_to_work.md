---
title: "difficulty getting persistence to work"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by chah on 2011-01-09
Hi, I've just started using Ubuntu, and I wanted to do a "USB" install but on my HDD, rather than on a USB drive. I have Windows installed on sda1, Knoppix installed on sda2 (in a similar fashion that that I also want to keep Ubuntu as a liveCD but booting from my hard drive partition), and I've created/installed an Ubuntu partition on /dev/sda3. Right now everything is being boot by GRUB 0.97 which is installed to my MBR.

I "installed" Ubuntu using unetbootin to create a bootable USB drive and then copying the contents of that drive to /dev/sda3, which I formatted as ext3. I then edited menu.lst as follows:
```

default 0
timeout 10

title Knoppix_6.4.3
kernel /boot/isolinux/linux ramdisk_size=100000 lang=en vt.default_utf8=0 apm=power-off video=vga16fb:off initrd=minirt.gz nomce quiet loglevel=1 tz=localtime no3d noprompt
initrd /boot/isolinux/minirt.gz
boot

title Knoppix_6.4.3_noImage
kernel /boot/isolinux/linux ramdisk_size=100000 lang=en vt.default_utf8=0 apm=power-off video=vga16fb:off initrd=minirt.gz nomce quiet loglevel=1 tz=localtime no3d noprompt noimage
initrd /boot/isolinux/minirt.gz
boot

title Ubuntu_10.4_LTS
root (hd0,2)
kernel /ubnkern initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash persistent --
initrd /ubninit
boot

title Windows
rootnoverify (hd0,0)
makeactive
chainloader +1
boot

```I took the portion of syslinux.cfg that I found on the USB drive created by unetbootin, and tagged it onto the end of the kernel line for booting ubuntu. Then after searching around on the net a bit more at the unetbootin page, I found instructions for how to make it persistent. These instructions seemed to match what I read at [https://help.ubuntu.com/community/LiveCD/Persistence.]("https://help.ubuntu.com/community/LiveCD/Persistence")

According to these instructions, I created casper-rw (I tried once on /dev/sda2, the Knoppix partition and once on /dev/sda3, the new Ubuntu partition neither of which worked), I made casper-rw a 10GB sparse file, to save time filling it up with zeros, then formatted it as ext3. I can mount it and see there is just lost+found on the empty loopback file. I added persistent as the last parameter of the kernel line for Ubuntu in menu.lst, and rebooted, but for some reason, casper-rw is not mounted and I have no persistence. I wonder if 10GB is too large for a persistent space? Or should I not be storing it on an ext3 filesystem?

Thanks in advance.

---

### Post by C.S.Cameron on 2011-01-09
Instead of the 10GB casper-rw file, try making a new ext4 partition and naming it casper-rw.

---

### Post by chah on 2011-02-03
Hi Cameron,

Thanks for your reply and help. I'm taking another stab at this again. I'm trying to get the casper-rw file to work instead of creating a partition at this time. I believe that the file can't be larger than 4G?

My question is: must the underlying filesystem be FAT32 for the casper-rw file to be found and used? I've shrunk the file down to 3G and still no persistence.

Thanks

---

### Post by chah on 2011-02-04
I'm still having some difficulty getting persistence to work. My latest setup is with multibook of Ubuntu 10.10, Knoppix6.4.3, LinuxMint10, and Backtrack Linux. Most of these are booting from iso files using GRUB2, that I got working with [help from this thread]("ubuntuforums.org/showthread.php?t=1673793"). Knoppix6.4.3 and Backtrack are booting from copies that I made of the CD on their own partition. 

I could not get Ubuntu to recognize a casper-rw file. I tried creating the file in both ext3 and vfat file systems. I shrunk the casper-rw file down to 3GB as I thought there might be issue with files larger than 4GB, but still no success.

Then I tried using a separate partition. I followed instructions from here: [geekdeck.wordpress.com/2010/02/03/booting-iso-images-with-grub2-among-other-things/]("geekdeck.wordpress.com/2010/02/03/booting-iso-images-with-grub2-among-other-things/")

I've ended up with sda1 having a copy of Windows, sda2 holding Knoppix and all the *.iso files that I'm booting from, sda3 holding a copy of Backtrack Linux and sda4 holding casper-rw:
```
$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda4     vfat     11G  8.0K   11G   1% /media/sda4
/dev/sda1  fuseblk     68G   41G   27G  61% /media/sda1
/dev/sda3     vfat    2.1G  1.9G  111M  95% /media/sda3
/dev/sda2     ext3     39G   14G   23G  38% /media/sda2
```

I used the -n flag with mkfs.vfat to name the volume casper-rw as suggested in the webpage above. However I cannot see the volume label name as casper-rw, either with cfdisk, fdisk, ls... so not very easy to confirm the name. In windows however, I see the volume label.

At first Ubuntu just wasn't finding anything, same as when I used the loopback file. Irealized that after I had changed to grub2 (and created a new boot directory for it), I had not added the "persistent" parameter to the end of the grub.cfg stanza. On doing that, I'm now getting the error:
```
(initramfs) mounting aufs failed
```

This was not happening before I added "persistent". I was getting a bootable Ubuntu system, but without persistence.

Searches on this string have not yielded very helpful results so far. Anybody can suggest what might be wrong?

TIA.

---

### Post by chah on 2011-02-04
So I realized that I did not follow the instructions at the webpage mentioned exactly. There they format the casper-rw partition to ext3, whereas I formatted it to fat32. I'm about to go to bed, so won't have time to retry that tonight. But I thought that FAT32 would be more sure to work than ext3.

---

### Post by chah on 2011-02-04
Turns out I was wrong. we can't use FAT32 as the underlying filesystem for a casper-rw partition. I found this info while browsing [https://help.ubuntu.com/community/LiveCD/Persistence]("https://help.ubuntu.com/community/LiveCD/Persistence").

So I currently have 10.10, Backtrack4 and LinuxMint10 all sharing the same casper-rw partition. I note that it's quite nice that I installed google-chrome under Ubuntu 10.10, and it also appears and works under LinuxMint.

I haven't tried the casper-rw loopback file recently, but I think can probably get it to work now. 

But I'd like to know whether we can pass some parameter to the kernel in the grub.cfg that will cause it to use a different filename than casper-rw? Can I have different persistent storage for 10.10, LinuxMint and Backtrack?

---

