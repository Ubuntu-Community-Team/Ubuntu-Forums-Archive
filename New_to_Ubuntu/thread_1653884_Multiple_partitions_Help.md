---
title: "Multiple partitions? Help"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by laugh1 on 2010-12-27
[http://imgur.com/kyK5d.png](http://imgur.com/kyK5d.png)


That is what I have...I don't know how to create a partition for windows and which one is my Ubuntu one.

---

### Post by germanix on 2010-12-27
What you see there are just 2 partitions, both for Ubuntu. The ext4 partition is where your OS and Home currently are, and the smaller "swap" partition at the end. If you want to install an additional OS like Windows, you need to make space for it. So you will need to shrink your ext4 partition from right to left. So you have to click on the ext4 partition to select it. You will then be given options to resize the partition. Two arrows will appear at each end of the partition. Grab the arrow at the right end and drag it towards the left to the size that you want. Click apply and let it do its work. You then have a free/Unallocated space where you can install another OS. Click that free partition and choose to create a new partition, then format it to what you want (ntfs/fat32)
I am telling you this off the top of my head so I may have missed some smaller details. If you run into trouble come back.
You do not mention which windows you aim to install but here is a how-to installing ubuntu and windows 7 as a dual boot:
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
and here some community how to:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
and here how to use Gparted:
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by davidmohammed on 2010-12-27
click on sda1 - you can then shrink it.

Then click on the unallocated space - assign it against NTFS

n.b. I presume you are going to install windows now that you've got ubuntu installed?  

If so remember installing windows will overwrite your GRUB2 boot loader.  You'll need to reinstall it again using [these]("https://help.ubuntu.com/community/Grub2") instructions.

---

### Post by dbowlin17 on 2010-12-27
Now everything i have read here was absolutely correct. If you are currently using ubuntu without a live cd, you will need to boot into ubuntu with a live cd, or use partedmagic or similar software. that will enable you to shrink your sda1 partition, freeing up some non partitioned space. then you will be able to create a new partition from that empty space, which you will probably want as ntfs. And then follow the instructions that davidmohammed provided to reinstall grub 2.

---

### Post by laugh1 on 2010-12-27
> **germanix said:**
> What you see there are just 2 partitions, both for Ubuntu. The ext4 partition is where your OS and Home currently are, and the smaller "swap" partition at the end. If you want to install an additional OS like Windows, you need to make space for it. So you will need to shrink your ext4 partition from right to left. So you have to click on the ext4 partition to select it. You will then be given options to resize the partition. Two arrows will appear at each end of the partition. Grab the arrow at the right end and drag it towards the left to the size that you want. Click apply and let it do its work. You then have a free/Unallocated space where you can install another OS. Click that free partition and choose to create a new partition, then format it to what you want (ntfs/fat32)
I am telling you this off the top of my head so I may have missed some smaller details. If you run into trouble come back.

The re-size option is grayed it for some reason.

---

### Post by davidmohammed on 2010-12-27
it is greyed out because you are using gparted from ubuntu.  Boot from the live CD instead - use the option "try ubuntu without installing"

---

### Post by germanix on 2010-12-27
I edited my post and provided some links that you can read to help you better understand what you need to do.

---

### Post by laugh1 on 2010-12-27
Ok, I made a 50gb partition. 

Wish me luck that I don't delete Ubuntu! :P

---

### Post by davidmohammed on 2010-12-27
dont need luck - just need a backup!

---

### Post by laugh1 on 2010-12-27
Ok, so now I install windows onto the new partition? Then do that thing to restore grub?

---

### Post by davidmohammed on 2010-12-27
wow that's a fast windows install - yes.  Once installed into the NTFS partition, follow the instructions to reinstall the grub2 boot loader.

---

### Post by laugh1 on 2010-12-27
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2
 
There is a lot of different options....what should I choose?

---

### Post by presence1960 on 2010-12-27
> **laugh1 said:**
> [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2
 
There is a lot of different options....what should I choose?

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

which is #12, #1 from the menu of links to the right of the page. Use simplest method. 

If you can't figure it out and need detailed, exact commands to run do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

