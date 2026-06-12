---
title: "Ubuntu installed &quot;in&quot; XP?"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by kewl_123 on 2009-06-15
Hi,
    I have been using Hardy for quite some time now. I have dual boot and in XP, in add/remove programms, ubuntu is also shown. I remember reading something like Hardy is installed in Windows just like a windows program.
What I am worried about now is....if my XP gets corrupt or stops working...what will happen to ubuntu?

Thank you.

---

### Post by SunnyRabbiera on 2009-06-15
You are talking about Wubi, as for what happens to Ubuntu if XP goes down I dunno, but hey if you use Ubuntu for browsing then things might go smoothly

---

### Post by LowSky on 2009-06-15
I Never like WUBI, never trusted it.

If you do a real ubuntu install you can dualboot with Windows still. This way if you loose your NTFS partition to corruption, you dont loose Ubuntu.

---

### Post by ugm6hr on 2009-06-15
> **kewl_123 said:**
> if my XP gets corrupt or stops working...what will happen to ubuntu?

Wubi installs Ubuntu into an existing NTFS partition.

So if you corrupt the partition, Ubuntu may fail too.

But if the problem is a software issue with Windows (e.g. virus etc), Ubuntu should still work.

Although I am not 100% certain....

---

### Post by jmszr on 2009-06-15
kewl_123,

Sometimes a hard shutdown in Windows will cause problems:

                              Wubi Initframs

Wubi installs Ubuntu into a windows folder usually a NTFS type of file system, this file system has a known reaction of being unstable in other operating systems like Ubuntu when a hard shutdown happens.

Just boot into windows, then shutdown correctly and then try to boot into ubuntu as normal, everything should work. (From LowSky)

If it doesn't:
                    Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in. Click Properties. Select the "Tools" tab and click "check now" under error checking (with Vista you might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After the checking is done, shut down  by using the start menu (Do Not hard reboot) and  try using Ubuntu now. ( From Ago)
                  
You can also accomplish the immediate previous tip by running chkdsk/f  in Windows and then shutting down properly.

If your XP stops working then so will Wubi. If you have enough space on your hard drive (10 GB is enough, but more is much better, especially if you are going to mostly be using Ubuntu and adding apps and files), then I urge you to do a full dual-boot XP/Ubuntu. There are a lot of tutorials about dual-booting. This sticky by ugm6hr: [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404) has a lot of information and the Ubuntu Pocket Guide by Keir Thomas has a section concerning dual-booting (there is a link to the guide in the sticky). This is a good site: [http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html) , also: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
                                                    
 Hope that helps.

Edit: It is possible (though I've never done it) to transfer your present Wubi setup to a full dual boot configuration. Here are two sites that explain that: [http://flip.netzbeben.de/2008/08/move-wubi-installation-ubuntu-on-windows-to-a-native-ubuntu-system/](http://flip.netzbeben.de/2008/08/move-wubi-installation-ubuntu-on-windows-to-a-native-ubuntu-system/)  also: [http://www.linuxhaxor.net/2008/12/06/graduate-from-a-wubi-install-to-a-dedicated-partition/](http://www.linuxhaxor.net/2008/12/06/graduate-from-a-wubi-install-to-a-dedicated-partition/) .

ALWAYS backup your important data first!

---

### Post by wpshooter on 2009-06-15
> **LowSky said:**
> I Never like WUBI, never trusted it.

If you do a real ubuntu install you can dualboot with Windows still. This way if you loose your NTFS partition to corruption, you dont loose Ubuntu.

I agree, this IMO is the way to go.

---

### Post by philcamlin on 2009-06-15
i think ubuntu dies if xp dies :(

---

### Post by Mark Phelps on 2009-06-15
> **kewl_123 said:**
> if my XP gets corrupt or stops working...what will happen to ubuntu?

It depends .. on the particular XP problem.  IF you installed Ubuntu inside the XP OS partition, and that gets corrupted, you won't be able to boot into anything, including Ubuntu.

If you get a BSOD in XP, depends on when you see it. If you can boot into XP, then you should still be able to boot into Ubuntu.  IF you get the BSOD before you get the OS selection menu, then you won't be able to boot into Ubuntu, either.

---

### Post by donkyhotay on 2009-06-15
Wubi is really designed to give people a chance to try ubuntu without the limitations of the liveCD but without the hassle of dual-booting. Honestly if you've been using ubuntu for awhile now and are planning on keeping it I would recommend doing a true dual-boot so that if(when) windows crashes it won't take ubuntu down with it. BTW, not every form of windows crashing will take ubuntu with it but it's possible with a wubi install and not possible with a dual-boot (if it does you probably have a hardware issue).

---

### Post by H2SO_four on 2009-06-15
My preference is to go with a dual boot instead of Wubi.  I wouldn't be able to trust that my linux would work if my windows became unusable.

---

### Post by donkyhotay on 2009-06-15
> **H2SO_four said:**
> My preference is to go with a dual boot instead of Wubi.  I wouldn't be able to trust that my linux would work if my windows became unusable.

Wubi has it's place in the world. Ubuntu isn't for everyone and removing a dual-boot is quite a hassle for most people. Wubi is great for those wanting to try out ubuntu more then what the liveCD offers with the possibility of easily removing it. Now for people that have used ubuntu for awhile and made the decision to keep it as a permanent part of their system then definitely remove the wubi installation and go with a true dual-boot. Course then there are those like me who don't even dual-boot and run ubuntu as their sole operating system! (c:

---

