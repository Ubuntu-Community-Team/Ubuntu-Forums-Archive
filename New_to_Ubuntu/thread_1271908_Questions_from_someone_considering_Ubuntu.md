---
title: "Questions from someone considering Ubuntu"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by PH3 on 2009-09-21
Hello,

First, I apologize in advance if I am asking questions that have already been asked and answered a million times.  However, I have read or skimmed through nearly the entire [Ubuntu Pocket Guide and Reference]("http://www.ubuntupocketguide.com/"), as well as spending a couple of hours searching and reading here in the Ubuntu Forums, and there are still a few things I'm not sure about.  First some background:

I have a brand-new Dell Inspiron 537s desktop computer, with Windows Vista.  I have never used Ubuntu before, but there is a particular issue that is causing Windows to be difficult for me to use, and I have never been a big fan of Windows anyway.  Thus I am considering installing Ubuntu.  I plan to configure the machine as a dual-boot system, with both Windows and Ubuntu.  It sounds like this is reasonably easy to do. So far so good, but here are the main questions that I have right now:

(1)  At some point, maybe after configuring Ubuntu and using it for a few weeks, I plan to make a decision -- either stick with Ubuntu or stick with Windows.  At that point, I will probably want to completely wipe out whichever operating system I don't plan to use, and preferably get rid of its separate partition so that the entire hard drive is available to whichever OS I decide to keep.  Is this hard to do?  And is the answer different depending on which OS I am getting rid of?  

I don't necessarily need instructions for this right now (though that could be helpful), but mainly just some indication of whether this is a simple task or a complex one, particularly for someone who has no experience with Ubuntu and with disk partitioning.

(2)  Assuming that I decide to continue using Ubuntu, at some point in the future I will most likely want to upgrade to a newer version of Ubuntu.  Is it easy to upgrade?  Does Ubuntu keep all of your personal settings (e.g., desktop theme settings and the like)?  Is it an automated process that requires minimal user input?

(3)  I have read several threads here on the pros and cons of 32-bit Ubuntu vs. 64-bit Ubuntu.  Basically, it sounds as if the main "con" for 64-bit is that some particular applications might require additional tweaking to get them to work properly.  However, things change quickly with computer technology, and much of the information I read on this topic is at least half a year old.  Is this still a "con" for using 64-bit?  Are there still certain applications that might require some additional work to get them to function correctly on 64-bit Ubuntu?  Or have any such problems pretty much been ironed out by now?

(In case it matters for question #3, I'll mention that my computing needs are fairly simple.  I mainly plan to use the computer for the following tasks or programs:  e-mail, web browsing, OpenOffice, listening to music, watching DVDs or other video, burning CDs and DVDs, viewing and organizing photos, and audio editing.)

---

### Post by Clopin on 2009-09-21
(1)
You can delete and edit partitions using the Windows install CD (Atleast I can do that with my WinXP CD)

(2)
Ubuntu got an update manager in System -> Administration -> Update Manager.
Whenever developers update their software (which you've got installed) it will automaticly update it all using that. You can even install new distros, like go from 9.04 to 9.10. And yes, you will keep your data.

(3)
I can't answer this really, as I've never used a 64-bit operative system.

I hope I atleast answered a bit of your questions.

---

### Post by philinux on 2009-09-21
3) No tweaking at all. Everything runs just great.

---

### Post by gordintoronto on 2009-09-21
Here's some personal opinions.

1.  Using the entire hard drive is easy after you pick one OS.  (Ubuntu will have full access to your Windows partition.)

2. I have never upgraded, so I should not comment on that.  I stuck with one version for almost two years, then built a new computer, on which I installed the latest version.

3.  I have been running 64-bit for over a month.  The only issue was trying to install the latest version of Firefox, then flash.  I took the simple approach: fall back to Firefox 3.0.  I expect this will not be an issue when I upgrade to the next version of Ubuntu.

Other comments: I suggest you download the 64-bit version of Jaunty and burn it to CD.  Boot from the CD and see how it goes.  You can play around without affecting your Windows installation at all.  In particular, you can check that your hardware will work.

Also: you might consider Linux Mint, which is built on Ubuntu.  It can do everything you list "out of the box," while Ubuntu requires that you install "restricted extras," among other things.

---

### Post by LewRockwell on 2009-09-21
you will feel much more comfortable experimenting with one of your older machines

if you do not have one, there are many good used machines for free or low investment(check out your local craigslist)

it is highly probable that you actually know someone who has one or more machines you might choose from(again, either free or low cost)

if you decide to buy a used machine just be aware that with brand-new, name-brand, full-sized, full-functioning warranteed computers selling for $300.00 to $400.00...prices in the used market have fallen very significantly

we never offer more than $100.00 to $150.00 for ANYTHING used

as always, your mileage may vary, buyer beware, and buyer be aware

due diligence is your responsibility...fortunately, good information abounds on the interwebs

.

---

### Post by Bucky Ball on 2009-09-21
> **PH3 said:**
> I'll mention that my computing needs are fairly simple.  I mainly plan to use the computer for the following tasks or programs:  e-mail, web browsing, OpenOffice, listening to music, watching DVDs or other video, burning CDs and DVDs, viewing and organizing photos, and audio editing.)

Hello and welcome. What kind of audio editing do you intend to do? What do you use in Windows to do it?

As for the rest of what you mention dive right in. You will find lots of people doing just that with Ubuntu (among other distros).

Upgrading: depends. Can be tedious, lengthy and problematic. Better to just install the newer version and keep your /home directory intact with your personal settings saved there. Upgrading is okay for some.

You might like to check out this thread if you have [NEVER TRIED LINUX]("http://ubuntuforums.org/showthread.php?p=7922209#post7922209"), the second HOWTO in my signature, which is for people in your position. Skip to the part you're interested in ...

---

### Post by yoyowazzup on 2009-09-21
Hi PH3,

I'll see if I can answer your questions...

[INDENT]1.  Ubuntu is a great operating system, and I feel sorry for anyone who still uses Windows.  However, there are some differences.

Installing Ubuntu is very easy to do.  In fact, you don't even have to install it to check it out. (Look into the Live CD on the download page)  The live CD is slow, but it will give you an idea of if your hardware will work out of the box or not.  If everything works, (display, sound and networking are the big ones) and you like what you see, just click on the 'Install' icon on the desktop and follow the instructions to install the OS.

If you decide to keep Ubuntu, you can blow away the Windows partition easily with GParted, but if you don't keep Ubuntu, you are in for some big headaches unless you have a copy of your Windows disk.

When you install Ubuntu, it writes a new bootloader to the disk.  This bootloader happens to live on the Ubuntu partition.  When that partition is deleted, so is the bootloader.  When you restart your computer, you will get an error saying that the bootloader failed to launch.  Just insert your Windows disk, and use the BIOS to boot to that.  Then click the 'Repair your computer' option, and follow the steps. (Easy to do and takes about 3 mins on average hardware).  There are all sorts of howtos on the net and these forums.

2. Ubuntu is by far, the easiest system to upgrade.  When 9.10 comes out next month, Ubuntu will notify you of the new release and ask you if you want to upgrade.  Just tell it yes, wait an hour then come back and enjoy the new release.  It keeps all of your settings and prefrences.

3. If your hardware supports it, then go ahead and get the 64-bit release.  I use many different advanced programs on my system, and have never had any issues.
[/INDENT]
It looks like, from your list of requirements, that Ubuntu will do exactly what you need.

Hope this helps, and good luck!:)

-yoyowazzup

---

### Post by mike555 on 2009-09-21
If you decide to try Ubuntu install , don't be in a hurry, read every screen , and pick manual partitioning , set a partition size you want and install to that partition , again being careful to not wipe out Windows (you might need it for something later).........

---

### Post by PH3 on 2009-09-21
Thanks, everyone, for your helpful replies!

A couple of things I wanted to reply to or comment on specifically:

> **gordintoronto said:**
> Other comments: I suggest you download the 64-bit version of Jaunty and burn it to CD.  Boot from the CD and see how it goes.  You can play around without affecting your Windows installation at all.  In particular, you can check that your hardware will work.

Thanks for the suggestion.  I definitely do intend to boot from the CD and play around for a while before I decide to install.

> **gordintoronto said:**
> Also: you might consider Linux Mint, which is built on Ubuntu.  It can do everything you list "out of the box," while Ubuntu requires that you install "restricted extras," among other things.

Out of curiosity, what tasks or applications specifically would require "restricted areas"?  (And I have no idea what a restricted area is, but I can probably find some documentation about it if/when I need to know.)

> **Bucky Ball said:**
> Hello and welcome. What kind of audio editing do you intend to do? What do you use in Windows to do it?

Currently, I use an ancient version of Cool Edit Pro in Windows for audio editing.  I have investigated Audacity, and it looks like it will run in Ubuntu and do everything I want it to do -- at least based on some stuff I read over a year ago.  I'm not planning to do multi-track mixing (at least not often); I just want to be able to do some basic editing of wave files (I think maybe they are called PCM format in Linux?).

In fact, one extra point to make is that even if I stick with Windows Vista on my new computer, I am planning to use Firefox as my web browser, OpenOffice as my word processor and spreadsheet, and Audacity as my audio editor.  (I already use Firefox and OpenOffice on my old computer.)  So I'm thinking that moving to Linux might not be such a huge change for me, as I would be using many of the same programs either way.

---

### Post by jmszr on 2009-09-21
PH3,

This will help explain ubuntu-restricted-extras: [http://en.wikipedia.org/wiki/Ubuntu-restricted-extras](http://en.wikipedia.org/wiki/Ubuntu-restricted-extras) and: [http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras](http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras) . It is a very useful package to install.

You are right, it shouldn't be too difficult a transition for you. You have obviously put some time and effort into your preparations.

Welcome aboard!

Edit: Since you mentioned watching DVD's as among your interests you will need to install Medibuntu: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)  including libdvdcss2. Also, I would suggest using K3B for CD/DVD burning.

---

### Post by nothingspecial on 2009-09-21
> **PH3 said:**
>  I mainly plan to use the computer for the following tasks or programs:  e-mail, web browsing, OpenOffice, listening to music, watching DVDs or other video, burning CDs and DVDs, viewing and organizing photos, and audio editing.)

I do all these things and have never used widows ..... if that`s any help

---

### Post by Bucky Ball on 2009-09-21
PCM is PCM in any language: 44100, 16 bit. It is the CD standard or 'Redbook'. :)

Sounds like Ubuntu could be right up your alley. Just watch the minimum requirements as mentioned and if you are having trouble try installing Xubuntu. Less demanding of system resources.

---

