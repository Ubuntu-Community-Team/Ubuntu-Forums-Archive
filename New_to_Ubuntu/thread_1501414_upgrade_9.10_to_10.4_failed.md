---
title: "upgrade 9.10 to 10.4 failed"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by jumpingchump on 2010-06-04
Hi there, 

After searching web forums I didn't find anything I could use -- I hope someone here can help!  

I'm new to Ubuntu. After using and enjoying two previous versions, most recently 9.10, every day for the past 8 months, I upgraded to 10.4 through the update manager (I think this is called wubi?). It all seemed to go fine until I got to the reboot stage. I haven't successfully booted into 10.4 yet. Every time I get the following message: 

Gave up waiting for root device. Common problems:c054eebf6e3
-Boot args (cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; 1s /dev)
ALERT! /dev/disk/by-uuid/8681ba84-e [etc etc big long string of numbers and letters] does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) 

I have no idea what any of this means, nor can I see any obvious command to make when I type in 'help.' 

All of this is on a Toshiba netbook 200, so I don't have a CD drive, nor do I have a USB key to boot from. I'm quite happy going back to 9.10 if that is the easiest thing to do.  

Any help much appreciated! 

Mark

---

### Post by Paddy Landau on 2010-06-04
Did you install Ubuntu as a program in Windows?

**If so:**

[LIST]
[*]You're using Wubi. Unfortunately, Wubi is not terribly stable -- especially for upgrades -- and is susceptible to corruption.
[*]I suggest that you simply uninstall, reinstall that latest version of Wubi, and restore your data (you did have a backup, right?). Remember what I said, though, that Wubi is a bit unstable. It would be best if you can create a USB bootable disk and install Ubuntu as a proper dual boot.
[*]I know that I say another thread similar to yours not too long ago. Try searching the forums for a similar problem to yours; unfortunately I don't know whether the problem was solved.
[/LIST]
If you're not using Wubi, sorry, I hope someone else can help you.

---

### Post by kansasnoob on 2010-06-04
Since you have no Ubuntu Live Media (CD or USB) I'd assume you have a Wubi install, if so hopefully you have a Windows recovery disc so you can restore the Windows MBR as described here:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

That will hopefully get Windows booting and you can go from there, but I fear you may also have been bitten by this:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

Please tell me that you did NOT check every box there if you saw this:

[ATTACH]159321[/ATTACH]

If you did things could get very messy with no ability to run an Ubuntu Live session :(

---

### Post by jumpingchump on 2010-06-04
Hello, thanks for getting back to me on this. 

I created a dual partition when I first installed Ubuntu as an OS about ten months ago, so no, I don't think I'm actually running Wubi. 

I do have all my stuff backed up, yes.

I did come across something similar in the forums, but it wasn't really helpful. 

If I want to uninstall 10.4 and reinstall 9.10, is that something I can do from a USB key? 

Thanks again,

Mark

---

### Post by kansasnoob on 2010-06-04
> If I want to uninstall 10.4 and reinstall 9.10, is that something I can do from a USB key?


Without seeing some actual info from a Live session we can't be sure, but from what you're saying, yes.

If you had a Live USB we could also probably fix your current install. So if you can get one first please post the results of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by jumpingchump on 2010-06-04
Hi Kansasnoob,

I'm going to go back and follow through the discussion on that link you posted in more detail -- it is relevant to my situation! A few points of clarification: I can still boot into Windows just fine, and, when I was upgrading to 10.4, I wasn't asked if I wanted to "check all" the boxes at any point. I will follow up on the other thread too about Live USB keys and report back. 

Cheers,

Mark

---

### Post by kansasnoob on 2010-06-04
> **jumpingchump said:**
> Hi Kansasnoob,

I'm going to go back and follow through the discussion on that link you posted in more detail -- it is relevant to my situation! A few points of clarification: I can still boot into Windows just fine, and, when I was upgrading to 10.4, I wasn't asked if I wanted to "check all" the boxes at any point. I will follow up on the other thread too about Live USB keys and report back. 

Cheers,

Mark

So you do get the grub menu and selecting Windows does boot Windows, but selecting Ubuntu results in the error?

If so that's definitely something we can fix using a Live USB. In fact I've read about being able to boot Ubuntu under such circumstances:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by kansasnoob on 2010-06-04
Perhaps I should have specified the section of that HowTo:

> Step 1: Boot into your OS

At the grub menu at boot up (you might have to hold the "shift" key or press "Esc" to get to the Grub menu) select the OS you are trying to boot. But do not press "enter", press "e" instead to edit the menuentry. Delete the line

    search --no-floppy --fs-uuid --set 86d32ee3-aec6-490b-8dab-e5cfff9c7af9

and then press "Ctrl+X". This should boot your OS. If you were not able to boot into you OS, you are infected by a different problem and should not continue this howto. 

That is only a temporary fix, the permanent fix is there too.

---

### Post by Frogs Hair on 2010-06-04
If you choose to reinstall with Wubi , run disk cleanup in Windows first or wipe free space if you have a tool to do so.

---

### Post by Contra75 on 2010-06-04
It may actually be an issue with your Intel video chip. Take a look here: 
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Workaround D worked for me on my Dell laptop, but when I tried Workaround A (which I now know I should not have  ](*,):evil:) my system crushed to a point where I had to reinstall Ubuntu Karmic from LiveCD.

---

