---
title: "Problems with Belkin 802.11g PCI card"
date: 2004-11-24
forum: Networking &amp; Wireless
---

### Post by digital1 on 2004-11-24
Hi, I am new to Linux and very new to Ubuntu.

After haveing successfully installed Ubuntu I have got all my hardware working except for my Belkin 802.11g pci card. 

The hardware profile says it's BCM94306 802.11g Broadcom PCI and the vendor is Belkin module no F5D7001. 

I have spoken to Belkin and they tell me that they do not support Linux.

If anyone can help I would really appreciate it.

Thanks

---

### Post by darrell on 2004-11-24
If you have no joy finding a linux driver for your card, try ndiswrapper, which will allow you to use the supplied windows driver under linux. 

You can install this package through apt or synaptic, and then follow the installation instructions in the ndiswrapper wiki: [http://ndiswrapper.sourceforge.net/wiki/index.php/Installation](http://ndiswrapper.sourceforge.net/wiki/index.php/Installation) - obviously you can skip the first steps which are all about compiling your kernel with ndiswrapper support, and then downloading/installing ndiswrapper - this will already be there after installing the ubuntu ndiswrapper package via synaptic.

I may be able to add something to the ubuntu wiki on ndiswrapper. Will keep you posted.

darrell

---

### Post by spirospr on 2004-11-25
I think you could also check what i did to work my wireless card with ndiswrapper. I think that you will have to do sth similar.

[http://ubuntuforums.org/showthread.php?t=5464](http://ubuntuforums.org/showthread.php?t=5464)

---

### Post by digital1 on 2004-11-25
Thanks for the help I will try out your solutoins, unfortunatly the computer I am useing is Ubuntu only so I don't have MS sitting on the same machine.

---

### Post by darrell on 2004-11-25
[QUOTE=digital1]Thanks for the help I will try out your solutoins, unfortunatly the computer I am useing is Ubuntu only so I don't have MS sitting on the same machine.[/QUOTE]
 to use ndiswrapper, you do not need a windows installation, all you need is the wireless card driver, either that which came with the card, or downloaded from the card manufacturers website.

---

### Post by jogego on 2004-11-26
I would like to know if ndiswrapper is bundled with Ubuntu? I know it does come bundled with Mepis.

---

### Post by atp123 on 2004-11-26
I am having trouble with this card also.  It appears ubuntu does not come with ndiswrapper - at least i cant find it on the CD.. And its no good using synaptic since theres no way of accessing the internet without ndiswrapper doh!
So is there any hope of ndiswrapper being included in future releases so I cant start using this distro online?

---

### Post by jogego on 2004-11-27
I think the guys making this distros available need to understand that not everybody using a laptop can use an ethernet connection. I for one was pleasantly surprised that ndiswrapper was bundled with mepis. I dont understand the reasoning that if my wireless card does not work, how am i supposed to download ndiswrapper?/ DUUHHHHH :-?

---

### Post by darrell on 2004-11-27
[QUOTE=jogego]I think the guys making this distros available need to understand that not everybody using a laptop can use an ethernet connection. I for one was pleasantly surprised that ndiswrapper was bundled with mepis. I dont understand the reasoning that if my wireless card does not work, how am i supposed to download ndiswrapper?/ DUUHHHHH :-?[/QUOTE]
 workaround: you could download the .deb directly, here:
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils_0.10-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils_0.10-1_i386.deb)
and save this either to your ubuntu partition (if you can access it from the OS you're using to download), or to a windows  partition, or a floppy disk. You might want to download the howtos/posts from this forum etc so they're available to you in ubuntu before you get online.

then reboot into ubuntu and mount the floppy/windows partition if necessary, then

sudo dpkg -i /path/to/the/downloaded/ndiswrapper-utils_0.10-1_i386.deb

will install it.

---

### Post by jogego on 2004-11-28
This would be a nice solution except for 
[list]
[*]the laptop am installing on does not have a floppy drive
[*]I have only 6GB to play with and am therefore not interedted in dual booting
[/list] 

so how do I go about getting ndiswrapper on my ubuntu?

---

### Post by darrell on 2004-11-29
[QUOTE=jogego]This would be a nice solution except for 
[list]
[*]the laptop am installing on does not have a floppy drive
[*]I have only 6GB to play with and am therefore not interedted in dual booting
[/list] 

so how do I go about getting ndiswrapper on my ubuntu?[/QUOTE]
 Burn a cd on whatever machine you are using to get on the web at the moment? I know it shouldn't be this hard, but at the moment it is :-(

---

### Post by Blind-Summit on 2006-02-11
I am having the same issue. I got hold of ndiswrapper on my WinXP box and copied it to a usb key then installed it from there when I loaded Ubuntu.

I can see my ssid, but can't connect to the internet still :-k

---

