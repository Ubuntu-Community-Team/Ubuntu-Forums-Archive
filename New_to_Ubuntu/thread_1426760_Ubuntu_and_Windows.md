---
title: "Ubuntu and Windows"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by noworldorder on 2010-03-10
I am a total newbie - a newbie's newbie.  I have Windows 7 and need to continue using it but I would like to use Ubuntu also. Can I partition my drive and have both?  If so:

How big should the Ubuntu be?
How do I switch from Windows to Ubuntu
How do I install to the partition and not overwrite windows.


Rookie questions eh.

Thanks for your help,
Chris

---

### Post by J V on 2010-03-10
Ubuntu can run nicely on only 5 gigs, very nicely on 10, but if you want to feel seriously overpowered go for 30 or 40 :)

Just install ubuntu :)

Just choose "install alongside windows"

---

### Post by spiky001 on 2010-03-10
Hi there I dual boot with xp, I only give windows 15gig on a 100gig drive but I use ubuntu all the time, windows is only for some games, so it depends on what you want windows for. The partion is all organized when you boot from disk,
 So windows is not over written you install side by side.
If you have not tried linux before there is an option to try before you install

---

### Post by noworldorder on 2010-03-10
Thanks for your replies.  One more newbie question.  When you boot up how do you decide which OS you will be using.

---

### Post by Tahakki on 2010-03-10
Ubuntu installs a thing called GRUB by default, which is a bootloader. When you boot up you'll see a list of OSes you have installed and can choose from there. :)

Enjoy Ubuntu!

---

### Post by ubudog on 2010-03-10
Sure!  That's what I used to do, now I use Ubuntu for everything, work, play, whatever.  Just select "Install with other Operating Systems" or something like that.  Hope you like Ubuntu! :p

---

### Post by undecim on 2010-03-10
Quick word of advice:

Put most of your extra space towards Windows, rather than Ubuntu.While you are in Ubuntu, you will still be able to access your Windows partition, but in Windows, you cannot access your Ubuntu partition without special software..

Also, welcome to Ubuntu! Remember, don't hesitate to ask a question here on the forums if you need help.

---

### Post by ubudog on 2010-03-10
> **undecim said:**
> Quick word of advice:

Put most of your extra space towards Windows, rather than Ubuntu.While you are in Ubuntu, you will still be able to access your Windows partition, but in Windows, you cannot access your Ubuntu partition without special software..

True.  And Ubuntu needs much less space than Windows.

---

### Post by Jerry N on 2010-03-10
Since it hasn't been mentioned yet, **DO NOT** use the Linux partition tools to shrink your Win 7 partition to make room for Linux.  Use the tools built into Win 7.  Otherwise, you might destroy Win 7.  In my experiments with Win7RC, I set up dual boot and triple boot (Win XP, Win7RC, Ubuntu) without any difficulty.  As usual, if you are going to mess with your hard drive (modifying partitions) be sure that you have created backups of all your important data.  There are no guarantees that you won't have trouble!  Of course you already have backups of your important data, don't you?

Jerry

---

### Post by Running_Dualboot on 2010-03-10
I dual boot win7 and ubuntu 9.10. Just do this and itll work easy.

[http://wubi-installer.org/]("http://wubi-installer.org/")

---

### Post by presence1960 on 2010-03-10
If you want to install ubuntu to it's own partition do this:

1. back up any data you don't want to lose
2. turn off System restore and page file until after the resize.
3. defrag windows once or even better twice
4. Shrink the windows partition using windows disk management utility
5. When the resize is complete reboot and make sure windows boots properly. If it does turn System Restore & page file back on.
6. Boot from the ubuntu Live CD and at the prepare disk space window choose "use largest continuous free space" option. This will install Ubuntu to the unallocated space from the windows resize. 
7. When install is complete you will get a GRUB menu giving you the option of which OS to boot into.

---

### Post by dmzamora on 2010-03-11
I run Ubuntu alongsid my Win 7, I used wubi to install Ubuntu.
Aside from few glitches, everything is working very well now.

---

### Post by Merk42 on 2010-03-11
A couple warnings about WUBI.[list]
[*]It doesn't run as fast as a native install
[*]If something happens to Windows, Ubuntu is gone too (so you can't completely switch without a format and reinstall if you want to)[/list]

---

### Post by lotharmat on 2010-03-11
To echo what other people have said:

Definately try ubuntu first - Boot from the CD and select try Ubuntu. This will give you a good idea of what hardware works 'out of the box'

---

### Post by Kazade on 2010-03-11
> **Merk42 said:**
> A couple warnings about WUBI.[list]
[*]It doesn't run as fast as a native install
[*]If something happens to Windows, Ubuntu is gone too (so you can't completely switch without a format and reinstall if you want to)[/list]

Add to that if your NTFS disk isn't unmounted properly (e.g. you power off the machine) it can screw up your Ubuntu install.

---

### Post by ubudog on 2010-03-11
> **Merk42 said:**
> A couple warnings about WUBI.[list]
[*]It doesn't run as fast as a native install
[*]If something happens to Windows, Ubuntu is gone too (so you can't completely switch without a format and reinstall if you want to)[/list]

Yeah, it would be better to just do a dual boot without using WUBI.

---

### Post by Mark Phelps on 2010-03-12
Agree with the dual-boot using separate partition approach ...

If you decide to do that, pay special attention to what's below:

> **presence1960 said:**
> ...
4. Shrink the windows partition using windows disk management utility
5. When the resize is complete reboot and make sure windows boots properly...

Don't let the Ubuntu installer shrink your Win7 partition.  Doing so risks corrupting that partition and not being able to boot into Win7 anymore.

Also, before you do this, use the Win7 backup feature to create and burn a Win7 repair CD.  It will come in handy later if you need to repair the Win7 boot loader.

---

