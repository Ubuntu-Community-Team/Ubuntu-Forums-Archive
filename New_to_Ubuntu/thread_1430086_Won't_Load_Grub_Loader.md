---
title: "Won't Load Grub Loader"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by robbiek01 on 2010-03-14
Hi all just installed Windows 7 first then Ubuntu 9 straight after but the grub loader goes straight into Ubuntu and does not give me a choice of operating systems 

I made sure I used different partitions for each install.

---

### Post by mcoleman44 on 2010-03-15
Did you try 
sudo update-grub

---

### Post by bumanie on 2010-03-15
What version of ubuntu are you using? There is a 9.04 and 9.10 - they have different default grub boot loaders and thus to help, we need to know which version. You can find the version by putting the following code in to terminal > lsb_release -a

---

### Post by lindsay7 on 2010-03-15
One thing to try is to load "startup manager" you can find it in Synaptic package manager. Once it is loaded you will find it under System/administration. You will be able to choose how long the grub menu in on the screen before it auto boots to either Ubuntu or windows.  You may be auto booting so fast that you are not seeing the booting list.  If windows is not shown in the "startup Manager menu list, then you will need to do a few things go add it to your grub menu.

Tell us which Ubuntu version you have as the other post stated and you may also want to post the output of "sudo fdisk -l"  that is the small letter L, this will give a little info on how your drive is set up.

---

### Post by robbiek01 on 2010-03-15
Hi all thanks for the reply..

I am running version 9.10 karmac

I have tried using the "Startup manager" but still not working all that appears is a quick message that says vga==79 and some other stuff that flashes to quickly to read.

HERES WHAT I GOT WHEN I DONE sudo update -grub

  	 	 	 	 	 	  robert@robert-desktop:~$ sudo update-grub 
 Generating grub.cfg ... 
 Found linux image: /boot/vmlinuz-2.6.31-14-generic 
 Found initrd image: /boot/initrd.img-2.6.31-14-generic 
 Found memtest86+ image: /boot/memtest86+.bin 
 done 
 robert@robert-desktop:~$ 





AND WHEN I DONE sudo fdisk -l


   	 	 	 	 	 	  Disk /dev/sda: 500.1 GB, 500107862016 bytes 
 255 heads, 63 sectors/track, 60801 cylinders 
 Units = cylinders of 16065 * 512 = 8225280 bytes 
 Disk identifier: 0xe145caad 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1   *           1          13      102400   82  Linux swap / Solaris 
 Partition 1 does not end on cylinder boundary. 
 /dev/sda2              13        5185    41538560   83  Linux 
 /dev/sda3            5185       60802   446743552    7  HPFS/NTFS

---

### Post by leorolla on 2010-03-15
Did you ever run Windows 7 before installing Ubuntu?

Maybe there is a problem with the install.

One solution is:
1. Make a Ubuntu 9.10 installation USB with some persistent memory.
2. Boot the installation USB, just to be sure it works.
3. Use the Windows 7 CD to repair the installation.
4. Boot from the Ubuntu USB and reinstall Grub2 to the MBR.

It can also be a problem with the partitioning......

Notice that with your partitioning scheme, cylinder 13 is shared by both swap and linux, and cylinder       5185 is shared by linux and windows. I don't recomend that.

---

### Post by oldfred on 2010-03-15
Your swap partition looks suspiciously like the windows boot partition - 100mb and boot flag. Did swap overwrite the windows boot partition? Is the rest of your windows partition in sda3 then it may be repairable.

To see if the parts are there run this script:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by lindsay7 on 2010-03-15
Do what Oldfred suggested. When you ran update-grub it should have found the windows boot loader and it did not which is strange if windows is installed.  Also the partitioning looks strange too.  So run the script and post back with the results.

---

