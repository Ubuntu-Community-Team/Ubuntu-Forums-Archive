---
title: "can't boot from cd"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by Wraith619 on 2009-11-17
hey guys , basically when my pc is starting up , i hit F9 to go to boot menu and boot from cd cuz i wanna install win xp on my only ntfs partition , but the prob is that after i choose boot from cd , it continues booting normally to ubuntu like i didn't choose anything , so can anybody help?

---

### Post by Jon Monreal on 2009-11-17
> **Wraith619 said:**
> hey guys , basically when my pc is starting up , i hit F9 to go to boot menu and boot from cd cuz i wanna install win xp on my only ntfs partition , but the prob is that after i choose boot from cd , it continues booting normally to ubuntu like i didn't choose anything , so can anybody help?

Odd. Try opening the XP CD in Ubuntu to verify its contents.

---

### Post by NickJones on 2009-11-17
Sounds like the CD wasn't burned properly, I presume you know how to burn a CD? If so, try it again, this time at a lower speed.
Nick

---

### Post by Jon Monreal on 2009-11-17
> **NickJones said:**
> Sounds like the CD wasn't burned properly, I presume you know how to burn a CD? If so, try it again, this time at a lower speed.
Nick

From his description, it sounds like he's trying to install XP with Ubuntu already installed (which likely means a non-burned CD).

That said, is it a burned CD?

---

### Post by Wraith619 on 2009-11-18
yes , it isn't possible to install an os from an iso image file , so i burned my backup copy of xp to cd.
i know that the cd works cause i used it to install xp on a virtual drive in virtual box , and the cd drive also works.
when i converted to ubuntu , i deleted the c drive and and took 38 GB to EXT3 which is to be used as "/" and used 2gb from "SWAP File drive" , and left my remaining ntfs d partition unaltered which is about 556.6 GB , now i wanna install windows on the ntfs drive so that i don't delete the boot file of ubuntu , and also if possible how can i resize my ubuntu partition cause it would be better if i put xp on a partition different from the one that has all the "Stuff" , so that if i get a virus that force me to format , i don't delete i year of collecting movies , games , apps , etc...
i can't unmount the ext3 partition to resize it since it's mounted as "/" , i heard i can resize it from my ubuntu cd , if possible can any body give a guide or something?

thx in advance , and thx for caring guys.

---

### Post by Jon Monreal on 2009-11-18
> **Wraith619 said:**
> yes , it isn't possible to install an os from an iso image file , so i burned my backup copy of xp to cd.
i know that the cd works cause i used it to install xp on a virtual drive in virtual box , and the cd drive also works.
when i converted to ubuntu , i deleted the c drive and and took 38 GB to EXT3 which is to be used as "/" and used 2gb from "SWAP File drive" , and left my remaining ntfs d partition unaltered which is about 556.6 GB , now i wanna install windows on the ntfs drive so that i don't delete the boot file of ubuntu , and also if possible how can i resize my ubuntu partition cause it would be better if i put xp on a partition different from the one that has all the "Stuff" , so that if i get a virus that force me to format , i don't delete i year of collecting movies , games , apps , etc...
i can't unmount the ext3 partition to resize it since it's mounted as "/" , i heard i can resize it from my ubuntu cd , if possible can any body give a guide or something?

thx in advance , and thx for caring guys.

You can use the LiveCD. Simply boot from the LiveCD and when the desktop loads, go to System -> Administration -> Partition Editor. Once there, right-click and select "Resize/Move". Be cautious when downsizing the partition so that you do not loose anything.

As far as the XP CD goes, you could go into your BIOS settings and set the CD drive as the first boot device, and see if that works.

---

### Post by Wraith619 on 2009-11-18
thx for the resizing help

still remains the main prob though and the boot order is already set cd first.

btw , will ubuntu boot file be overwritten by the xp boot file if install it on another partition?

---

### Post by Jon Monreal on 2009-11-18
> **Wraith619 said:**
> thx for the resizing help

still remains the main prob though and the boot order is already set cd first.

btw , will ubuntu boot file be overwritten by the xp boot file if install it on another partition?

Yes, Windows XP will overwrite Grub. [This guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") explains how to recover after this.

That said, your problem is an interesting one. I've heard of [problems with a Windows XP CD and multiple partitions]("http://www.ozzu.com/mswindows-forum/won-boot-t73477.html"), but in those cases the CD will hang, not fail to boot entirely. 

Was it the same CD that was used to install XP on that computer before? Or was it an OEM installation and you're using a generic XP CD? It's possible that the CD doesn't have the proper drivers for your hard drive.

---

### Post by Wraith619 on 2009-11-19
it's the same cd , thx for the guide.
btw it's says in the guide that recovering will overwrite windows boot loader , if that happens , can i boot windows through the GRUB menu , or any other way?

---

### Post by sandy8925 on 2009-11-19
I think you're CD isn't proper.

When you recover Grub you can still boot Windows. If there isn't an entry you'll have to create it yourself.

A really good guide for doing GRUB stuff is here:

[http://members.iinet.net.au/%7Eherman546/p15.html](http://members.iinet.net.au/%7Eherman546/p15.html)   (GRUB)

[http://members.iinet.net/%7Eherman546/p20.html](http://members.iinet.net/%7Eherman546/p20.html)   (GRUB 2)

---

### Post by lisati on 2009-11-19
Two thoughts, which might not be relevant:
[LIST=1]
[*]Was the ISO file burned using an option like "Burn disk image"?
[*]Some Windows CDs I've seen briefly pop up a message along the lines of "Press any key to boot from CD": if such a message pops up and you do nothing (maybe you're topping up your coffee and don't see it) a normal boot which ignores the CD will happen
[/LIST]

---

### Post by Wraith619 on 2009-11-19
i know what windows does before booting , but this time just proceeds to boot normally directly.

---

### Post by Jon Monreal on 2009-11-19
> **lisati said:**
> Two thoughts, which might not be relevant:
[LIST=1]
[*]Was the ISO file burned using an option like "Burn disk image"?
[*]Some Windows CDs I've seen briefly pop up a message along the lines of "Press any key to boot from CD": if such a message pops up and you do nothing (maybe you're topping up your coffee and don't see it) a normal boot which ignores the CD will happen
[/LIST]


It can't be #1 because he already said he used the CD to install XP in VirtualBox.

> i know what windows does before booting , but this time just proceeds to boot normally directly.

By this you mean it doesn't show the "Press any key to boot from CD" whatsoever, correct?

I have found several [other examples]("http://www.computing.net/answers/windows-xp/unable-to-boot-from-cdrom/71528.html") where people haven't even been shown the "Press any key" message at all; of those: [this one is the most interesting]("http://www.technologyquestions.com/technology/windows-xp/42034-no-press-any-key-boot-cd-option-install.html"). The user had installed earlier to a 300GB drive, but when this didn't work well, the user decided to partition and then install. After the partitioning, the XP CD didn't show the "Press any key to boot from CD" message at all, just as in your situation, and you both have multiple partitions (which I have heard can cause problems with XP).

---

### Post by Wraith619 on 2009-11-19
yeah , but i know it's not a partition problem cause it would have *Atleast*  seen the partition D which is now mounted as "windows".
and i yeah it never shows the press any key to boot from cd now......

---

### Post by Jon Monreal on 2009-11-19
> **Wraith619 said:**
> yeah , but i know it's not a partition problem cause it would have *Atleast*  seen the partition D which is now mounted as "windows".
and i yeah it never shows the press any key to boot from cd now......

Right, but we're not talking about not having a partition mounted a certain way or in a certain format, but instead the possibility that the reason the XP CD is failing is the fact that you have multiple partitions. Enough people have had problems that some recommend the "[first partition rule]("http://www.dslreports.com/forum/r18694528-Windows-on-first-partition-rule")" - that is, installing XP on the first partition (which, I'm taking it, was your configuration before on C:\).

Also, do you have any logical partitions?

---

### Post by Wraith619 on 2009-11-19
DAMN , now i remember , c:/ and D:/ were formatted using a western digital program , the C:/ was static , and i don't remember if D:/ was dynamic or static , if it's dynamic , it's impossible to install windows on it.
how ever i met one of my relatives today , which was the person who actually told me about ubuntu in the 1st place , he told me i can go to GRUB menu  , the press c to go to command line , then boot from cd , also high told me if upgrade my GRUB to GRUB 2 , then i can boot directly from iso , also now i think i know how to boot from live cd to resize the ubuntu partition

---

