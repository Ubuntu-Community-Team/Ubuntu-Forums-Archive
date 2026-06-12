---
title: "sudo update-grub question"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by mikodo on 2010-12-12
The only time I had a dual boot system was with Hardy and Lenny. When I removed Lenny, I found I had hosed the grub to Hardy, and wound up reinstalling Hardy.

Question:

If I had ran in terminal from Hardy: 
 ```
sudo update-grub
```before removing Lenny, would I have continued to have a bootable Hardy system?

I want to dual boot another distro, but not at the expense of my quick-silver running configuration of Lucid and loose it when I remove the other distro.

Thanks.

---

### Post by Ozymandias_117 on 2010-12-12
Boot into whichever one you're planning on keeping, and run ```
sudo grub-install *install_device*
``` then ```
sudo update-grub
``` where "install_device" is the /dev/sd code for the hard drive you want it on. If you're unsure, post the results of ```
sudo fdisk -l
```

---

### Post by mikodo on 2010-12-12
ikodo@mikodo-desktop:~$ sudo fdisk -l
[sudo] password for mikodo: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232
Here is output of sudo fdisk -l   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1402    11261533+  83  Linux
/dev/sda2            1403        3503    16876282+  83  Linux
/dev/sda3            3504       38913   284430794+   5  Extended
/dev/sda5            3504        4140     5116671   82  Linux swap / Solaris
/dev/sda6            4141       14624    84212698+  83  Linux
/dev/sda7           14625       17830    25752163+  83  Linux
/dev/sda8           21036       24253    25848553+  83  Linux
/dev/sda9           24254       27449    25671838+  83  Linux
/dev/sda10          17831       21035    25744131   83  Linux

Partition table entries are not in disk order
mikodo@mikodo-desktop:~$ 

Below is a screenshot of Gparted showing my partitions. I have boot on it's own partition. I have no other natively booting distro;s other than lucid. I have a couple of distro's in Vbox in a couple of the partitions.

I would like to natively boot that new distro of Linux mint that is based on Debian that is a rolling release; just to try it.

Thanks.

---

### Post by mikodo on 2010-12-12
So being that Lucid's (/) is on /dev/sda2, would I do this to have Lucid still booting after removing other distro's?

```
sudo grub-install /dev/sda2

``````
sudo update-grub
```**Or should it be written to the partition that boot is in? like:**

```
sudo grub-install /dev/sda1
``````
sudo update-grub
```Is that all there is to it. I suppose that would write the grub attaching it to the MBR for Lucid. Right?

Thanks.

---

### Post by mikodo on 2010-12-12
Kinda late in Canada here; I'll check for any clarifications/affirmations of what I wrote earlier, tomorrow.

Thanks.

---

### Post by sikander3786 on 2010-12-12
Which distro are you planning to install? If that presents an option during the installer to install the boot loader or not, choose not to install it. Then you may boot Ubuntu after completion and run *sudo update-grub* to add that distro to your Grub menu and dual boot ;-)

If your Ubuntu's Grub gets messed up, you can re-install it using these simple commands. Just 2 of them.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

If you could please clarify what you are planning to achieve, we would be able to adivise better.

---

### Post by mikodo on 2010-12-12
> **sikander3786 said:**
> Which distro are you planning to install? If that presents an option during the installer to install the boot loader or not, choose not to install it. Then you may boot Ubuntu after completion and run *sudo update-grub* to add that distro to your Grub menu and dual boot ;-)

If your Ubuntu's Grub gets messed up, you can re-install it using these simple commands. Just 2 of them.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

If you could please clarify what you are planning to achieve, we would be able to adivise better.

As I said earlier in the thread, I want to dual boot with Lucid and install another distro (Mint Debian). When I remove Mint Debian later, I don't want to mess up the grub for Lucid, like I did before in a similar situation and wind up not being to boot back into Lucid.

Thanks.

---

### Post by sikander3786 on 2010-12-12
Mint should present you with an option not to install the bootloader as mentioned earlier. You just need to do that. Don't install the boot loader and just boot Ubuntu and run update-grub to add it to your existing Grub menu. And if you achieve that, when you remove Mint, you just need to run update-grub once more to get rid of Mint entry.

And if you don't get a choice or miss it and Mint's Grub gets installed. You should still be able to boot Ubuntu from its Grub. Boot Ubuntu and then install Grub from inside Ubuntu. If your HDD is sda, you command will be,

```
sudo grub-install /dev/sda
```

Note, it is just sda without an integer and not sda1 or sda2 as you are going to install Grub to the MBR of that HDD and not a partition.

You can also follow the link in my above post and re-install Grub from Live CD.

There are many possibilities. Install Mint and don't install boot loader. Simple!

If you run into problems, come back with the output of this bootinfoscript as per instructions here and we are sure we'll be able to fix that ;-)

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Good Luck!

---

### Post by mikodo on 2010-12-12
Thanks sikander3786 and Ozymandias 117__

Nice concise directions and education for me!

Mike

---

