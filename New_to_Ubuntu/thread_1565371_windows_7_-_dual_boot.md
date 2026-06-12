---
title: "windows 7 - dual boot?"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by Tom16 on 2010-08-31
I'm new new new.
I have a windows 7 machine... which version of Ubuntu should I load?
Do all versions provide dual boot capability?
Thanks so very much!!

---

### Post by TimEnid on 2010-08-31
you should be able to install any version.

---

### Post by Mark Phelps on 2010-08-31
> **Tom16 said:**
> I'm new new new.
I have a windows 7 machine... which version of Ubuntu should I load?
Do all versions provide dual boot capability?
Thanks so very much!!

Just be sure to NOT install side-by-side when you load Ubuntu.  Allowing the Ubuntu installer to shrink your Win7 OS to make room for Ubuntu is asking for filesystem corruption on the Win7 side.

Also, BEFORE you do anything regarding installation, be sure to use the Backup feature to create and burn a Win7 Repair CD.  That will prove invaluable later should you need to repair the Win7 boot loader.

---

### Post by Tom16 on 2010-09-01
Thanks all very much!
 
I'm not sure, though, what you mean by "side-by-side"?
 
What/how would you suggest to repartion?
 
(Is there some detailed doc's on this so I don't have to ask 'stupid' questions?)
 
Thanks again.

---

### Post by BrockStrongo on 2010-09-01
You can install ubuntu inside windows using Wubi
 Here is some info on dual booting if you decide Wubi is not for you.  [http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/](http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/)
There are lots of how-to's for dual booting windows 7 and ubuntu, I would suggest reading through a couple of them before you start anything. 
Hope this is of some help

---

### Post by Cypress421 on 2010-09-01
You can also virtualize Ubuntu using VirtualBox within Windows 7, if your PC has enough grunt.

---

### Post by Tom16 on 2010-09-01
You are too quick!!:p
 
I just did a quick search and see 'fdisk' and 'cfdisk' as suggestions/references (don't know if these are available on standard version of Windows 7.)  I'll check out your suggested link though - thanks!

---

### Post by [::AP::] on 2010-09-01
> **Tom16 said:**
> What/how would you suggest to repartion?
 
(Is there some detailed doc's on this so I don't have to ask 'stupid' questions?)

I have a Windows XP Machine, when I installed I just shrunk the size of the XP partition with the slider bar. I had no problems. However, don't trust me, I am no where near an expert. Wait for a pro to comment on this thread...

Make SURE to backup, although in my opinion there are rarely issues. 

Detailed documents/websites? Ah...I don't have anything currently, I will look around. Just remember, Google is your friend :D

And, there is no such thing as a 'stupid' question, we were all at the newbie stage at one point or another (don't worry, you learn quickly). 

FYI, not criticizing, but it is 'par**ti**tion', not 'partion'. Just FYI :D

[::AP::]

---

### Post by [::AP::] on 2010-09-01
I forgot, Welcome to the forums!

And, pay attention to other's advice...just because I had no problems with *my* install doesn't mean yours will be flawless.

Best of Luck! :D

[::AP::]

---

### Post by wilee-nilee on 2010-09-01
> **BrockStrongo said:**
> **Grub, the bootloader for ubuntu, has a habit of overwriting the windows MBR making it almost impossible to boot into your windows partition.** 


This is incorrect as far as grub booting Windows, millions of us have no problems.

---

### Post by Cypress421 on 2010-09-01
> **wilee-nilee said:**
> This is incorrect as far as grub booting Windows, millions of us have no problems.

Doesn't GRUB replace the windows bootloader with options for Windows and other OS's?

---

### Post by alphacrucis2 on 2010-09-01
> **Cypress421 said:**
> Doesn't GRUB replace the windows bootloader with options for Windows and other OS's?

It replaces the MBR. How else would it be possible to get control at boot. Grub and Grub2 also store some stuff in the gap between the MBR and the first partition. Grub2 uses a little bit more of this space than the old grub legacy which has turned up a problem with some windows oem software that store license info in that gap area blowing away grub2 and requiring a reinstall of grub2 from the CD to fix. Note that Windows/Microsoft itself does not do this, it is third party OEM software on some makes. The grub2 dev is aware of this issue and trying to come up with a foolproof solution. See this:

[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html]("http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html")

---

### Post by Cypress421 on 2010-09-01
> **alphacrucis2 said:**
> It replaces the MBR. How else would it be possible to get control at boot. Grub and Grub2 also store some stuff in the gap between the MBR and the first partition. Grub2 uses a little bit more of this space than the old grub legacy which has turned up a problem with some windows oem software that store license info in that gap area blowing away grub2 and requiring a reinstall of grub2 from the CD to fix. Note that Windows/Microsoft itself does not do this, it is third party OEM software on some makes. The grub2 dev is aware of this issue and trying to come up with a foolproof solution. See this:

[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html]("http://www.chiark.greenend.org.uk/ucgi/%7Ecjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html")

Noted.

---

### Post by ssulaco on 2010-09-02
> **Tom16 said:**
> Thanks all very much!
 
I'm not sure, though, what you mean by "side-by-side"?
 
What/how would you suggest to repartion?
 
(Is there some detailed doc's on this so I don't have to ask 'stupid' questions?)
 
Thanks again.
Read this..
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)


> **Tom16 said:**
> I'm new new new.
I have a windows 7 machine... which version of Ubuntu should I load? 
[COLOR="Red"]http://www.psychocats.net/ubuntu/whichbuntu[/COLOR]
[COLOR="Blue"]https://help.ubuntu.com/community/BurningIsoHowto[/COLOR]
Do all versions provide dual boot capability?[COLOR="Red"]Yes[/COLOR]
Thanks so very much!!

---

### Post by Mark Phelps on 2010-09-02
> **Tom16 said:**
> Thanks all very much!
 
I'm not sure, though, what you mean by "side-by-side"?
 
What/how would you suggest to repartion?
 
(Is there some detailed doc's on this so I don't have to ask 'stupid' questions?)
 
Thanks again.

The side-by-side options allows you to shrink the Win7 partition to make room for Ubuntu -- which has been known to cause corruption of the Win7 OS partition in the process.  

A much less risky alternative is to shrink the Win7 partition using its own Disk Management utility.  Then, when installing Ubuntu, just use the "largest free space" option and allow the installer to do the default partitioning using that space.

---

### Post by Captain Lightning on 2010-09-02
> **Mark Phelps said:**
> The side-by-side options allows you to shrink the Win7 partition to make room for Ubuntu -- which has been known to cause corruption of the Win7 OS partition in the process.  

A much less risky alternative is to shrink the Win7 partition using its own Disk Management utility.  Then, when installing Ubuntu, just use the "largest free space" option and allow the installer to do the default partitioning using that space.

Yes this is what I did recently with no problems

---

### Post by bezbelin on 2010-09-02
> **Tom16 said:**
> Thanks all very much!
 
I'm not sure, though, what you mean by "side-by-side"?
 
What/how would you suggest to repartion?
 
(Is there some detailed doc's on this so I don't have to ask 'stupid' questions?)
 
Thanks again.

Hi, 
Myself - a 2 day old linux user but I have installed both XP and  Ubuntu 9.04 in same disk but different drives. I will tell you what I  did. But I am not sure whether it will work for you with your windows7,  so please wait for comments of our peers before you do this. 

I  have two different hard drives -had partitioned it c,d,e (Ist one) and  similarly g, h for second with windows xp installed in 'c' . What I did  initially is shifted all data files from d and e to the second drive and  deleted the logical partitions 'd & e' using "disk management" in  XP so as to get continuous space for linux. Within windows XP, I popped  in Ubuntu CD selecting option to install and followed instructions till  you reach the portion for creating partition table. (Before that make  sure of all partition size and format type from XP so that u r  absolutely sure of not installing Linux to any partition containing  windows OS or your data).

A good explanation is provided in the  following page for further steps which I followed and now have a dual  boot system with XP and Ubuntu.

[https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)

Also read the following for other options. There's an application called Wubi (haven't tried)

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://seogadget.co.uk/the-ubuntu-installation-guide/#install-from-CD](http://seogadget.co.uk/the-ubuntu-installation-guide/#install-from-CD)

And make sure u have all backups ready. Hope this will help you... Enjoy Linux

---

### Post by BrockStrongo on 2010-09-02
> **alphacrucis2 said:**
> It replaces the MBR. How else would it be possible to get control at boot. Grub and Grub2 also store some stuff in the gap between the MBR and the first partition. Grub2 uses a little bit more of this space than the old grub legacy which has turned up a problem with some windows oem software that store license info in that gap area blowing away grub2 and requiring a reinstall of grub2 from the CD to fix. Note that Windows/Microsoft itself does not do this, it is third party OEM software on some makes. The grub2 dev is aware of this issue and trying to come up with a foolproof solution. See this:

[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html]("http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html")


Wish I had known this before, the first dual boot I tried to setup was with a OEM version of vista, and 9.04 which left vista unbootable. Not really much of a loss I guess:) If I only I had the foresight to check the forums before I got started .

---

