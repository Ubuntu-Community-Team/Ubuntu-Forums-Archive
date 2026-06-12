---
title: "Dual boot two linux systems"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by mesmith on 2009-11-10
I currently have two primary partitions on my hdd.  One contains xubuntu 8.10 and the other is a swap.  I have a good sized chunk of unallocated space.  I would like to install xubuntu 9.10 into that space.

I am confused as to whether I should format the unallocated space prior to install or let the install do it after I point to it.  Also, I assume installing 9.10 would bring in grub2.  I don't understand root partitions, new MBR, where to put the new MBR, etc.  Is all this handled by the install?  Am I overcomplicating things?  I want to know the correct respnses to the install questions.

What happens to the old grub?

Thanks.

---

### Post by Jose Catre-Vandis on 2009-11-10
Allowing 9.10 to install to the unallocated space is fine if that is what you want to do. Just take care when using the partitioner during the install that you pick the right options. Make sure also you install grub2 to the mbr (hd0) or /dev/hda (sda). Grub2 will take over from legacy grub at boot and should offer you your two Ubuntus to choose from.

Alternatviely you can choose to only use some of the unallocated space by creating a partition of your chosen size ( I usually go for 10 -15GB as I store all my "personal files" on a separate partition.)

---

### Post by ajgreeny on 2009-11-10
If you do not like grub2 after installing 9.10, you can easily go back to legacy grub by booting into your xubuntu 8.10 and using the command ```
sudo grub-install /dev/sda
```This assumes your hard disk is sda, of course; change that part if it is different.  You can then edit the /boot/grub/menu.lst file on that system to include the newer 9.10 version by adding a stanza in the same format as your 8.10 stanza, just changing the UUIDs or grub device names to fit.

This is almost exactly what I have done, except I have two hard disks and 4 operating systems in total.

---

### Post by kansasnoob on 2009-11-10
This tutorial is written for dual-booting with Windows but it basically describes my favorite way to multi-boot (pictures too):

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

A couple things to consider though:

(1) I would use a new primary partition for your new installation because if you decide to delete the original primary partition at some point it's best to have a primary partition at the beginning of the drive.

(2) It's best not to move or resize swap! If you do you'll end up in what I call UUID hell. It can be fixed but why create problems.

(3) There is no need to create another swap partition. Any number of Linux OS's can share the same swap.

---

### Post by kansasnoob on 2009-11-10
Oh, regarding the boot-loader. If you have only one hard drive I'd just go with the defaults. That is DO NOT click on the advanced button:

[ATTACH]135626[/ATTACH]

---

### Post by ranch hand on 2009-11-10
> **kansasnoob said:**
> oh, regarding the boot-loader. If you have only one hard drive i'd just go with the defaults. That is do not click on the advanced button:

[attach]135626[/attach]
+962

---

