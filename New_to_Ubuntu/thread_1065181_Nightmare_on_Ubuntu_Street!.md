---
title: "Nightmare on Ubuntu Street!"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by Naastik on 2009-02-09
Hello. I have been having a nightmare with Ubuntu.
 I installed it on my laptop  but the problem there was that it dominated Vista as the primary boot option. And when I installed it on my desktop it took all the disc space.
 In order to rectify the boot issue I used EasyBCD to reinstate Vista as the default booter. I followed a step by step illustrated guide called how to install vista and ubuntu with vista installed first. However, I saved the  boot details that I needed to access when I was back on Vista in the wrong place ( I saved it in the documents of Ubuntu but not in the Vista documents), and consequently when I was back in Vista, I was unable to dual boot. Ubuntu was completely inaccessible.
   I went on the Neo Smart Technology forum to get some support and though it was well meant, I wasn't able to resolve the problem.
 So, in the end I resorted to restoring both computers back to factory settings. And now I am not going to install Ubuntu on my laptop, just my desktop. But Ubuntu won't resize the partition. It keeps telling me there is an error and is having to abort.
  It won't let me do it(that is to say I can't/it won't) manually either. So all in all I hope this is of use to other novices and perhaps you know some way I can get it installed without any hassle. After all it is a free os and that is not to be sniffed at. But still it has cost me a lot of time and effort an if time is indeed money then it is an expensive operating system that for me is failing miserably.
  Hope you other novices are having Daydreams on Ubuntu Street!:guitar:

---

### Post by unplugged23 on 2009-02-09
Well, what i would suggest for someone new to hard drive partitioning would be to go pick up a cheap hard drive 50gb or less, so your not creating new OS partitions on the same drive. partitioning/dual booting is much easier when you have a separate hard drive for each OS you want to install. this is how i learned about partitioning and how it works. also, make sure that you ALWAYS have your boot flagged partition or your in for a real head ache. you don't need a separate one for each hard drive though. also i would recommend formating the linux Hard drive to the ext 3 file system ad also creating a linux swap partition. most of this can be read about here

[http://lissot.net/partition/partition-04.html](http://lissot.net/partition/partition-04.html)

dont give up on ubuntu as once you start using it it will quickly take over as your primary OS!

---

### Post by bodhi.zazen on 2009-02-09
Naw, you do not need a new HD at all.

First, start in Vista and defragment the hard drive. You can then resize the vista partition while running vista with the disk tools included in vista.

If that fails, boot the Ubuntu CD and try resizing again.

If that fails  please post the error message and/or a screen shot of gparted.

---

### Post by joey-elijah on 2009-02-09
My 2 cents is just to install Ubuntu via WUBI from inside windows. This saves on partitioning anything, and the windows bootloader will give you Ubuntu as an option during boot up. Solved!

[http://wubi-installer.org/](http://wubi-installer.org/)

Sleep/Suspend don't work in WUBI - but then they don't work period unless you have the 1 or 2 pieces of supported hardware.

---

### Post by unplugged23 on 2009-02-09
> **bodhi.zazen said:**
> Naw, you do not need a new HD at all.

First, start in Vista and defragment the hard drive. You can then resize the vista partition while running vista with the disk tools included in vista.

If that fails, boot the Ubuntu CD and try resizing again.

If that fails  please post the error message and/or a screen shot of gparted.

Of course he doesn't need a new hard drive, i  was just suggesting this as an easy way to use the partitioner, with little risk to other system files, also while gaining experience and knowledge.

---

### Post by kansasnoob on 2009-02-09
> **Naastik said:**
> Hello. I have been having a nightmare with Ubuntu.
 I installed it on my laptop  but the problem there was that it dominated Vista as the primary boot option. And when I installed it on my desktop it took all the disc space.
 In order to rectify the boot issue I used EasyBCD to reinstate Vista as the default booter. I followed a step by step illustrated guide called how to install vista and ubuntu with vista installed first. However, I saved the  boot details that I needed to access when I was back on Vista in the wrong place ( I saved it in the documents of Ubuntu but not in the Vista documents), and consequently when I was back in Vista, I was unable to dual boot. Ubuntu was completely inaccessible.
   I went on the Neo Smart Technology forum to get some support and though it was well meant, I wasn't able to resolve the problem.
 So, in the end I resorted to restoring both computers back to factory settings. And now I am not going to install Ubuntu on my laptop, just my desktop. But Ubuntu won't resize the partition. It keeps telling me there is an error and is having to abort.
  It won't let me do it(that is to say I can't/it won't) manually either. So all in all I hope this is of use to other novices and perhaps you know some way I can get it installed without any hassle. After all it is a free os and that is not to be sniffed at. But still it has cost me a lot of time and effort an if time is indeed money then it is an expensive operating system that for me is failing miserably.
  Hope you other novices are having Daydreams on Ubuntu Street!:guitar:

I have an idea! How about breaking things down?

Like one computer at a time?

And IMHO I'd start with the desktop because it's generally easier!

IMHO Vista should only be resized using Vista's own tools:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2)

Then I'd install Ubuntu 8.04.2 from the live CD:

[http://releases.ubuntu.com/releases/8.04/](http://releases.ubuntu.com/releases/8.04/)

---

### Post by Naastik on 2009-02-09
> **joey-elijah said:**
> My 2 cents is just to install Ubuntu via WUBI from inside windows. This saves on partitioning anything, and the windows bootloader will give you Ubuntu as an option during boot up. Solved!

[http://wubi-installer.org/](http://wubi-installer.org/)

Sleep/Suspend don't work in WUBI - but then they don't work period unless you have the 1 or 2 pieces of supported hardware.

I have installed using wubi and now I can't install flashplayer. I keep getting some nonsense that it is available to the users of Mozilla. And I am using firefox. So what is this rubbish about? When I had ubuntu via the disc I could get it but this wubi doesn't seem to want to know. What is that all about?

---

### Post by Naastik on 2009-02-09
> **kansasnoob said:**
> I have an idea! How about breaking things down?

Like one computer at a time?

And IMHO I'd start with the desktop because it's generally easier!

IMHO Vista should only be resized using Vista's own tools:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2)

Then I'd install Ubuntu 8.04.2 from the live CD:

[http://releases.ubuntu.com/releases/8.04/](http://releases.ubuntu.com/releases/8.04/)

Well I did do that initially. I shrank the volume and created a partition via computer> manage> disk management>. But my issue was with EasyBCD and not being able to dual boot with Vista (as that is the OS I am most familiar with) as the default. Having said that I installed the 8.10 version and not the 8.04. So perhaps  the 8.10 version does have certain issues with it.

---

### Post by kansasnoob on 2009-02-09
Well, you seem to be just jumping all over the place!

But right now you need Flash in Ubuntu in a Wubi install. 

That should be easy! While in Ubuntu go to terminal and run:

```
sudo apt-get install ubuntu-restricted-extras
```

Then I strongly recommend installing the newest Flashblock (1.5.8) through Firefox. (You may only be able to get Flashblock 1.5.7)

---

### Post by benhur99ph on 2009-02-09
> **Naastik said:**
> I have installed using wubi and now I can't install flashplayer. I keep getting some nonsense that it is available to the users of Mozilla. And I am using firefox. So what is this rubbish about? When I had ubuntu via the disc I could get it but this wubi doesn't seem to want to know. What is that all about?

I'm running a wubi install and to install flash, all I did is to got to Adobe's website, downloaded the .deb flash-player installer, double-clicked on it, let it install. It worked right away.

---

### Post by Naastik on 2009-02-10
> **kansasnoob said:**
> Well, you seem to be just jumping all over the place!

But right now you need Flash in Ubuntu in a Wubi install. 

That should be easy! While in Ubuntu go to terminal and run:

```
sudo apt-get install ubuntu-restricted-extras
```

Then I strongly recommend installing the newest Flashblock (1.5.8) through Firefox. (You may only be able to get Flashblock 1.5.7)

You are right about me jumping all over the place. I just reinstalled Ubuntu for real on my desktop after creating a partition in Vista and all seems to be well apart from the fact that now Vista won't download a thing not even a image- when I say download I mean that it won't open after download or show up anywhere apart from the download box.
    When I was installing Ubuntu the option to import Vista was there, and I took it. Could that be the reason? Has Vista now become a Virtual Operating System?

---

