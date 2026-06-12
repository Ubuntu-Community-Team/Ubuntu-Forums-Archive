---
title: "where's my windows hard drive?"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by sir_guy on 2009-07-21
I'm pretty sure this is me and not xubuntu, I'm trying to find my second hdd and i don't know where to look, it's not in media or file system but i know xubuntu knows it's there because it shows in catfish as a search location.
Rob

---

### Post by saj0577 on 2009-07-21
It needs to be mounted first. Double click in thunad (file manager and it should mount it)

and then it will appear under /media/xxx

/media/disk for example


Saj

---

### Post by sir_guy on 2009-07-21
i'm sorry i don't understand.
if i go to thunar and dev and doubleclick on sdb or sdb1 nothing happens.

I'm new to xubuntu by the way.

Rob

---

### Post by zerhacke on 2009-07-21
You need the ntfs-3g package and the ntfs-config package would help a lot too.

---

### Post by saj0577 on 2009-07-21
On Thunar on the left hand side it should say "24.8gb Media" (With 24.8 being the size of your windows partition)

When you double click it it should show your windows files/folders (windows.program files,documents and settings)

YEah?

Saj

---

### Post by sir_guy on 2009-07-21
on the left pane of thunar i've got:
>rob
>wastebasket
>filesystem
i'm running xubuntu 8.10 if that makes any difference.

---

### Post by sir_guy on 2009-07-21
if i plug in my usb stick it comes up in thunar.

---

### Post by pizza-is-good on 2009-07-21
Somehting similar happened to me when I started using Xfce. It wasn't showing up in the 'files browser'(sorry, I'm not familiar with xfce, is it nautilus?). I solved it by just typing the location. For me it was /media/OS

---

### Post by sir_guy on 2009-07-21
downloaded ntfs-3g
the install instructions say:

The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

i'd hate to see the hardest way if thats the simplest!

---

### Post by sir_guy on 2009-07-22
[FONT=Arial]Would upgrading to ubuntu or a more recent version of xubuntu make any difference? I&#8217;m getting quite despondent with it now, I really like the idea of ubuntu and the philosophy behind it (I aren&#8217;t keen on windows and Microsoft either) but ever since I&#8217;ve installed it I&#8217;ve had problems. Not being able to get to my hdd, not being able to get on the net (that was resolved fairly easily), not being able to see my remaining balance on my wireless broadband dongle. And all the solutions seem to involve trawling the net in search of programming language that I don&#8217;t understand. Am I unique in my experience? Does it just work for most people?[/FONT]
  [FONT=Arial]I don&#8217;t want to give up yet but the truth is at this stage for me &#8230; I hate to say it, but windows is easier.[/FONT]
  [FONT=Arial]I want to be able to use xubuntu for a while to get used to it but I can't do that when I can't get to any of my files.[/FONT]
  
  [FONT=Arial]Rob. xx

P.S i also tried this
[/FONT]      [COLOR=black][FONT=&quot]sudo aptitude update[/FONT][/COLOR]
  [COLOR=black][FONT=&quot]sudo aptitude install ntfs-config[/FONT][/COLOR]
  
  
with no joy.

---

### Post by Tyke91 on 2009-07-22
```

 sudo mkdir /media/windows
 sudo cp /etc/fstab ~/fstab.bak
 sudo echo /dev/sdb1 /media/windows ntfs defaults 0 0 >> /etc/fstab

```Copy and paste these 3 commands separately

The first should create a mountpoint for windows in /media/windows

the second backs up the file that you're about to change, in case you (or I) did something wrong.

The third uses echo to append (>>) the line "/dev/sdb1 /media/windows auto defaults 0 0" to your /etc/fstab file, which controls how devices are mounted in linux.
[B]
/dev/sdb1[/B] is the device you want to mount

**/media/windows** is the mount point

**ntfs** is the file system. you SHOULD also be able to use "auto" for this spot instead, but this will save a few resources

**defaults **will give you the normal options for mounted filesystems

**0 **for dumping

**0** for fsck checks (you don't want that running through a windows filesystem)


please tell me if I missed something.

**PS:** This is all assuming you have windows on the second hard drive, first partition. If it's somewhere else then use this naming convention.

```
/dev/sd<hard drive a-z><partition #>
``` so 1st hard drive 3rd partition is /dev/sda3 , 4rth hard drive 2nd partition is /dev/sdd2 and so on

---

### Post by JKyleOKC on 2009-07-22
You can go into Synaptic, find the entry "pysdm" and click to install it. This will add the Storage Device Manager to your System menu, and you can use it to automatically do all the editing of the fstab file and other housekeeping necessary to make devices mountable. I've used it to add two WinXP internal drives to my Xubuntu 8.04 main system and it went like clockwork...

---

### Post by Vined Adobo on 2009-07-22
I haven't tried xubuntu, but on my 9.04 Ubuntu system, I click on Places, upper left on the panel between Applications and System.  I have an ACER laptop, and if I click on Acer in that menu and then type my passwork, it automatically mounts the hard drive.  I have set up Ubuntu to boot from a usb Cruzer Memory stick.  If the stick is not present on boot, the machine boots to Windoze.  I never boot Windoze anymore.  Can't stand waiting that long.  The wife also has stopped using Windoze on her laptop.  As a matter of fact, I no longer ever access the hard drive except for old data files which I copy to the memory stick.
I hope this doesn't duplicate what you've already read, and I hope I helped just a little.
Dave

> **sir_guy said:**
> [FONT=Arial]Would upgrading to ubuntu or a more recent version of xubuntu make any difference? I’m getting quite despondent with it now, I really like the idea of ubuntu and the philosophy behind it (I aren’t keen on windows and Microsoft either) but ever since I’ve installed it I’ve had problems. Not being able to get to my hdd, not being able to get on the net (that was resolved fairly easily), not being able to see my remaining balance on my wireless broadband dongle. And all the solutions seem to involve trawling the net in search of programming language that I don’t understand. Am I unique in my experience? Does it just work for most people?[/FONT]
  [FONT=Arial]I don’t want to give up yet but the truth is at this stage for me … I hate to say it, but windows is easier.[/FONT]
  [FONT=Arial]I want to be able to use xubuntu for a while to get used to it but I can't do that when I can't get to any of my files.[/FONT]
  
  [FONT=Arial]Rob. xx

P.S i also tried this
[/FONT]      [COLOR=black][FONT=&quot]sudo aptitude update[/FONT][/COLOR]
  [COLOR=black][FONT=&quot]sudo aptitude install ntfs-config[/FONT][/COLOR]
  
  
with no joy.

---

### Post by jim Kane on 2009-07-22
> **sir_guy said:**
> I'm pretty sure this is me and not xubuntu, I'm trying to find my second hdd and i don't know where to look, it's not in media or file system but i know xubuntu knows it's there because it shows in catfish as a search location.
Rob

read this thread
[http://cafelinux.org/xubuntuforums/index.php/topic,327.0.html](http://cafelinux.org/xubuntuforums/index.php/topic,327.0.html)

thats how i eventually got my windows ntfs slave drive going.

---

