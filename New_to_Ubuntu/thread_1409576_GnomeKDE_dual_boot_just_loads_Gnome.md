---
title: "Gnome/KDE dual boot just loads Gnome"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by zaivala on 2010-02-17
I have been happily running Karmic Koala with Gnome since it came out.  I got hold of an installation disk, and decided to try Kubuntu, partitioning my largish hard drive to load both.  Of course, it took a while to get Kubuntu installed...

After installation, the computer just loads Ubuntu.  No grub loader options come up.  Hitting Esc during Grub only lets me select which kernel to load, not which desktop.

What did I do wrong?  If it is not doable, do I need to use GPartEd to get my disk space back?  (I assume yes, but I'd like to hear it's doable.)

Moss

---

### Post by warp99 on 2010-02-17
Did you know that you can install Kubuntu in Ubuntu with one command?

```
sudo aptitude install kubuntu-desktop
```

At the GDM login menu you'll be able to login to Gnome (Ubuntu) or KDE (Kubuntu). To uninstall just do the opposite:

```
sudo aptitude remove --purge kubuntu-desktop
```

Make sure you use aptitude to install and remove so all remnants of Kubuntu can be purged.

---

### Post by zaivala on 2010-02-17
> **warp99 said:**
> Did you know that you can install Kubuntu in Ubuntu with one command:

```
sudo aptitude install kubuntu-desktop
```

At the GDM login menu you'll be able to login to Gnome (Ubuntu) or KDE (Kubuntu). To uninstall just do the opposite:

```
sudo aptitude remove --purge kubuntu-desktop
```

Make sure you use aptitude to install and remove so all remnants of Kubuntu can be purged.

Not what I wanted to do.  I love Gnome and want to keep using it.  I wanted to try a dual-boot to choose Gnome or KDE, so I wouldn't change my working and beloved system but can get to know KDE in my spare time.

---

### Post by warp99 on 2010-02-17
You don't understand. Ubuntu and Kubuntu are the same thing except for the desktop. Ubuntu uses Gnome while Kubuntu uses KDE. All the other underlining files **are exactly the same**. By installing separate partitions you're doing twice the work for no additional gain.

---

### Post by zaivala on 2010-02-17
> **warp99 said:**
> You don't understand. Ubuntu and Kubuntu are the same thing except for the desktop. Ubuntu uses Gnome while Kubuntu uses KDE. All the other underlining files **are exactly the same**. By installing separate partitions you're doing twice the work for no additional gain.

I do understand that.  But I want my choice of which desktop to load -- doing it the way you said would make KDE the desktop.  Nonetheless, it installed it correctly, there is no reason I can think of why Grub doesn't give me the choice of which partition to boot to.

I also have prior experience with KDE which says that it is incredibly slow compared to Gnome... so loading KDE into my Gnome installation would still load all the KDE files and slow my system down.

Maybe I'm stoopid.  But I want options, and the installation procedure gave them to me and now won't let me exercise them.

---

### Post by wojox on 2010-02-17
What versions are you using? Are they both 9.10?

---

### Post by zaivala on 2010-02-17
> **wojox said:**
> What versions are you using? Are they both 9.10?

Yes.

---

### Post by warp99 on 2010-02-17
> **zaivala said:**
> But I want my choice of which desktop to load -- doing it the way you said would make KDE the desktop... 

No it doesn't remove Gnome but only adds the KDE desktop. You can have multiple desktops installed on the same Ubuntu install. When you login at the GDM menu you can choose the desktop you want to load. When you're done just logoff and choose a different desktop. If you want you can also install the xubuntu-desktop and have all three on your machine to choose from.

Edit: At the GDM login menu you would choose "select session" and in the drop down list there would be an option to use KDE.

---

### Post by zaivala on 2010-02-17
Warp 99: See Post #5

---

### Post by wojox on 2010-02-17
In Gnome terminal try running:

```
sudo update-grub2
```

Technically since you loaded kde last, on another partition, it should boot first. Do you even see the kubuntu splash screen?

Also try holding down the left shift key on reboot.

---

### Post by zaivala on 2010-02-17
> **wojox said:**
> In Gnome terminal try running:

```
sudo update-grub2
```

Technically since you loaded kde last, on another partition, it should boot first. Do you even see the kubuntu splash screen?

Also try holding down the left shift key on reboot.

Thanks, I'll try the SUDO command.  No, I do not see anything KDE, and it is definitely loading the Gnome partition.  I'll also try the left shift key... get back to you soon.

---

### Post by zaivala on 2010-02-17
[sudo] password for zaivala: 
sudo: update-grub2: command not found

so much for sudo... now rebooting and trying the left-shift trick.

Edited to state: Nope, left shift did nothing.

---

### Post by wojox on 2010-02-17
No grub2 heh. How about:

```
sudo update-grub
```

Also what does 

```
sudo fdisk -l
```

show us?

---

### Post by egalvan on 2010-02-17
> **zaivala said:**
> I do understand that.  But I want my choice of which desktop to load -- **doing it the way you said would make KDE the desktop. **

No, it does not. When you log in, is when you choose which desktop to load... KDE or Gnome, or whatever desktop environment you have available.


> 
 Nonetheless, it installed it correctly, there is no reason I can think of why Grub doesn't give me the choice of which partition to boot to.


GRUB *should* have detected the extra installation.
It´s possible the install went south, or GRUB did not detect the extra OS.

> I also have prior experience with KDE which says that **it is incredibly slow compared to Gnome**... 

Yes, it is.
and no it is not.
My work system has KDE, Gnome and XFCE DE´s, 
and KDE is NOT `incredibly slower` than Gnome.
You experience may vary, but most would agree that KDE is about the same as Gnome.
Linus Torvalds thinks that KDE is superior to Gnome,
and has said so publicly several times.

> so loading KDE into my Gnome installation would still **load all the KDE files and slow my system down**.

No, it doesn´t... the system only loads the files that it needs...
if you launche with Gnome, *very* few KDE files are loaded.
if you launch with KDE, *very* few Gnome files are loaded.
What *is* loaded are the menus...
but these have NO effect on the system speed.

> Maybe I'm stoopid.  But I want options, and the installation procedure gave them to me and now won't let me exercise them.

Again, GRUB should have detected the extra installation.
It´s possible the install went south, or GRUB did not detect the extra OS.

---

### Post by zaivala on 2010-02-17
> **wojox said:**
> No grub2 heh. How about:

```
sudo update-grub
```

Also what does 

```
sudo fdisk -l
```

show us?

1.  zaivala@zaivala-desktop:~$ sudo update-grub
[sudo] password for zaivala: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-19-generic
Found kernel: /boot/vmlinuz-2.6.31-17-generic
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-15-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

zaivala@zaivala-desktop:~$ 

2. zaivala@zaivala-desktop:~$ sudo fdisk -l

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91ad5aa9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12135    97474356   83  Linux
/dev/sdb2           12136       19929    62605305    5  Extended
/dev/sdb5           19368       19929     4514233+  82  Linux swap / Solaris
/dev/sdb6           12136       19066    55673194+  83  Linux
/dev/sdb7           19067       19367     2417751   82  Linux swap / Solaris

Partition table entries are not in disk order
zaivala@zaivala-desktop:~$

---

### Post by zaivala on 2010-02-17
> **egalvan said:**
> 
Linus Torvalds thinks that KDE is superior to Gnome,
and has said so publicly several times.



No, it doesn´t... the system only loads the files that it needs...
if you launche with Gnome, *very* few KDE files are loaded.
if you launch with KDE, *very* few Gnome files are loaded.
What *is* loaded are the menus...
but these have NO effect on the system speed.



Again, GRUB should have detected the extra installation.
It´s possible the install went south, or GRUB did not detect the extra OS.

I am very happy for Linus.  However, recent articles have stated that he has ditched KDE for Gnome. (from Slashdot)

My experience is, well, my experience, and has been tested on the same machine I'm typing on.  I installed Kubuntu 8.04 on it, and it was soooooo sloooow I thought I was in a handicapped version of Windoze, almost gave up on Ubuntu.  I tried Ubuntu (default, Gnome) and it was a world of difference.  I have not attempted to repeat that experience with later versions of Ubuntu, and in fact that is what I was attempting to do with this installation... if Grub would see that I have two installations of Ubuntu, one being with KDE, then I would have some data to either report or keep to myself.

And no, Grub is not detecting the KDE partition, or is not doing anything about it.  See previous post, where I listed the results from some sudo commands.

Moss

---

### Post by occams_beard on 2010-02-17
> **warp99 said:**
> You don't understand. Ubuntu and Kubuntu are the same thing except for the desktop. Ubuntu uses Gnome while Kubuntu uses KDE. All the other underlining files **are exactly the same**. By installing separate partitions you're doing twice the work for no additional gain.

I was thinking of doing a dual boot with kubuntu too, just to try it out. I don't like to install kubuntu-desktop along side my main Gnome because it pulls in a lot of KDE Krap that I don't want and always seems hard to get rid of it. 

Ended up just installing Kubuntu in virtual box... And decided I still can't stand KDE 4.x.

---

### Post by warp99 on 2010-02-18
> **occams_beard said:**
> I was thinking of doing a dual boot with kubuntu too, just to try it out. I don't like to install kubuntu-desktop along side my main Gnome because it pulls in a lot of KDE Krap that I don't want and always seems hard to get rid of it.

This is the reason why you use the command "sudo aptitude install kubuntu-desktop". Unlike using apt-get when you go to remove kubuntu-desktop using aptitude it removes all of the dependency packages.

Edit:

Even if you don't use aptitute getting rid of the KDE packages is not that hard. In fact it's copy and paste:

[http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

---

### Post by zaivala on 2010-02-22
warp99, you're just not getting what we're saying, and think you know what we're talking about.

We want to run KDE and Gnome desktops independently, not all on one installation.  It installs perfectly, and then Grub does not give the choice of boots.

It doesn't matter one bit that we COULD load KDE into our Ubuntu installation, or that we could delete it or not.  We have working Gnome systems, have had problems (mostly with slowness) with KDE, and want a separate boot partition to test KDE and see if it is any better than it was the last time we tried it, which partition we have already set up and installed Kubuntu to.  We do not want this test to slow down or otherwise affect our Ubuntu-Gnome installation -- or have the Ubuntu-Gnome installation affect our test of KDE.

We are asking a technical question:  Why is Grub not giving us the boot options we installed?  This is far different from anything you have supplied in answers.

Moss

---

