---
title: "Which Ubuntu Partition is Okay to Delete?"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by RookieUbuntuUser58 on 2008-12-29
The /boot partition or the swap file partition. I really want to keep the swap file partition for the hibernation feature. I have 3 partitions for Ubuntu (ext3 partition, /boot partition, and the swap file partition). Also will deleting whatever partition cause any negative effects on Ubuntu? Thanks in advance.

---

### Post by xjcannonx on 2008-12-29
without knowing much, i would say you shouldn't delete any partitions, is anything on the ext3 partition, what does ```
df -h
``` say? what are you trying to do?

Edit: my bad on the command, i fixed it, sorry its early

---

### Post by kansasnoob on 2008-12-29
Why are you wanting to delete any partitions:confused:

---

### Post by mkvnmtr on 2008-12-29
The boot partition is what starts the computer. If you delete it you can't start. It is very small so nothing is gained. The swap partition should also be very small. I can think of no reason for it to be more than 2 GB. The other partition is where your Ubuntu system lives. It might be a bad idea to delete it. So in the end you better not delete any of the three if you want to use your system. You can indeed resize your Ubuntu partition or even your swap partition.

---

### Post by RookieUbuntuUser58 on 2008-12-29
> **xjcannonx said:**
> without knowing much, i would say you shouldn't delete any partitions, is anything on the ext3 partition, what does ```
df -h
``` say? what are you trying to do?

Edit: my bad on the command, i fixed it, sorry its early

3.4GB's used of 22GB's. Trying to install a new OS.

> **kansasnoob said:**
> Why are you wanting to delete any partitions:confused:

To be able to create a logical partition for another OS install. The Ubuntu install took up all my logical partitions so I only have primary option.

> **mkvnmtr said:**
> The boot partition is what starts the computer. If you delete it you can't start. It is very small so nothing is gained. The swap partition should also be very small. I can think of no reason for it to be more than 2 GB. The other partition is where your Ubuntu system lives. It might be a bad idea to delete it. So in the end you better not delete any of the three if you want to use your system. You can indeed resize your Ubuntu partition or even your swap partition.

Not looking to gain space. Just looking to gain a logical partition as all I have left is the option to create primary ones. See above response.

---

### Post by mkvnmtr on 2008-12-29
Post a screen shot of the window of Gparted to display your partitions. I think you can resize your Main partition and leave it free space. Then click on the free space and make a new partition. It will me made an extended partition. But I want to look before I give advise. What os are you going to install. If it is linux you can use the same boot and swap partitions.

---

### Post by RookieUbuntuUser58 on 2008-12-29
Heres the screenshot. The first is XP Home and the rest is Ubuntu and unallocated space.


The OS Im trying to install is Mac OSX. So can't do that.

---

### Post by kansasnoob on 2008-12-29
mkvnmtr seems to have the right idea here. You see from my attached screenshot I have 3 Linux OS's (2 of which have separate /home partitions) all within one extended partition. (And they share the same SWAP)

[ATTACH]97957[/ATTACH]

---

### Post by kansasnoob on 2008-12-29
> **boost3d23 said:**
> Heres the screenshot. The first is XP Home and the rest is Ubuntu and unallocated space.


The OS Im trying to install is Mac OSX. So can't do that.

I've never installed Mac OSX so I don't know what to tell you, I can't see that you'd gain anything by deleting any partitions.

---

### Post by mkvnmtr on 2008-12-29
Are you on a mac? Anyway there is going to be a problem with booting when you install mac last. Maybe you should look into virtual install. They say that works well and you will have no problems booting, You should be able to put mac inside one of the others with a virtual install.

---

### Post by RookieUbuntuUser58 on 2008-12-29
> **mkvnmtr said:**
> Are you on a mac? Anyway there is going to be a problem with booting when you install mac last. Maybe you should look into virtual install. They say that works well and you will have no problems booting, You should be able to put mac inside one of the others with a virtual install.

Hmm then I should delete Ubuntu and install OSX first? That would really hurt since I got Ubuntu set up perfectly and would have to go about customizing it and tweaking it all over again. But if it is the only way, Ill have to do it.

---

### Post by shearn89 on 2008-12-29
looking at that last screenie, i'd say either delete some of the other linux partitions, or grab yourself a cheap, bigger hard drive off ebay (~320gb should be plenty), and ghost your current one onto that. Then you'd have plenty of room for macosx. Fitting a new hard drive shouldn't be too bad in a laptop, but i'm not sure how easy mac make it...

---

### Post by xjcannonx on 2008-12-29
I agree with mkvnmtr on the point that mac osx will be hard to install unless it is done first, if you really wanted a separate partition for mac, I think it would be worth backing(you can make a ghost copy so all your settings and everything is the same) everthing else to an external drive and start from scrath with mac first.

---

### Post by mkvnmtr on 2008-12-29
I think the problem is you can't extract the boot information off the mac disks. If you install mac first then the linux a linux boot partition is added to replace the mac one. You can get into it to edit it to add other partitions very simply. I think doing the clone and putting the mac on first might be the easiest way. Another might be installing the mac on another hard drive and going to the firmware to boot it up but I have no idea how to do that. Seems that if you save your windows and ubuntu systems you could install the mac and reinstall the other two in a virtual  system and only have one boot up and use which ever you wanted.

---

### Post by RookieUbuntuUser58 on 2008-12-29
Uninstalling Ubuntu as we speak and then gonna try the Mac OSX install.

---

