---
title: "Help :)"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by bd41 on 2008-12-27
Alright, im finally switching to Linux. After being fed up with vista and all, i did some research and i want to try ubuntu. 

For the record i have Windows Vista Home Premium running on Gateway Gt5414e machine. 2G ram (2 more comming) with 1.3 TB memory, amd64, etc etc. (1tb external drive, 300G internal drive.)

First, i wanted to partiton my external and boot linux off that, but i just partitioned my internal drive (with 3.91G, is that enough?)

Im downloading the latest ubuntu, and i am going to use infra recorder to burn it to a disc. 

So tips on what to do after i get the iso on the disc?

Thanks! :)

---

### Post by jimmy the saint on 2008-12-27
Welcome to the forums!
First, a tip.  use descriptive thread titles.  Many people here are becomming less tolerant of unhelpful thread titles like "newbie here" and "help."  They do nothing to identify an issue and, frankly, are a little irritating. Use a title like "how do I dual boot?"  Also, if you search this forum for "dual boot vista" you will find literally dozens of threads regarding this very issue that will likely answer any question you may have and more!  

I would recommend dual booting, which it seems you are planning to do.  In vista, shrink the vista partition and free up at 15 gigs of space to play around with.  You can load Ubuntu onto 3.1 gigs, but you won't really be able to do much with it.  Install Ubuntu on the free space created.

MAKE A FULL BACKUP FIRST!!!  Do NOT assume that everything will just work. Humans make mistakes and you do not want to overwrite everything by mistake and lose everything because you didn't backup.

Burn the iso slowly to prevent any error.  Unplug the external drive during the install just to elimintate confusion.  Be prepared for Grub to replace the Vista bootloader.  This means that when you power on, you will be presented with a text menu to choose which OS to boot.

Feel free to ask SPECIFIC questions here and we will be glad to help you!

---

### Post by Michael.Godawski on 2008-12-27
welcome bd41

are you planning to switch to Ubuntu completely or do you want to dual-boot for some time?

For setting up a dual-boot see these guide:

[LIST]
[*][http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)
[/LIST]
Just select the vista and linux option.

If you want to install Ubuntu and need a guide see here:


[LIST]
[*][http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)
[/LIST]

---

### Post by nhasian on 2008-12-27
If you just want to try Ubuntu, i recommend wubi.

[http://wubi-installer.org/](http://wubi-installer.org/)

Wubi is an officially supported Ubuntu installer for Windows users that can bring you to the Linux world with a single click. Wubi allows you to install and uninstall Ubuntu as any other Windows application, in a simple and safe way. Are you curious about Linux and Ubuntu? Trying them out has never been easier!

[LIST]
[*]Wubi is Simple -  No need to burn a CD. Just run the installer, enter a password for the new account, and click "Install", go grab a coffee, and when you are back, Ubuntu will be ready for you.
[*]Wubi is Safe - You keep Windows as it is, Wubi only adds an extra option to boot into Ubuntu. Wubi does not require you to modify the partitions of your PC, or to use a different bootloader, and does not install special drivers. It works just like any other application. Wubi is spyware and malware free, and being open source, anyone can verify that.
[*]Wubi is Discrete - Wubi keeps most of the files in one folder, and if you do not like it, you can simply uninstall it as any other application.
[/LIST]

[IMG]http://wubi-installer.org/images/wubi-123_small.png[/IMG]

---

### Post by hyper_ch on 2008-12-27
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

