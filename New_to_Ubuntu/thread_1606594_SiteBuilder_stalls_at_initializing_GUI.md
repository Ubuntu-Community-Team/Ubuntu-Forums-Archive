---
title: "SiteBuilder stalls at initializing GUI"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by DayLite on 2010-10-26
I installed Homesteads SiteBuilder in wine. Trying to launch it for the first time it stalled when it came to 'Initializing GUI. 

Any suggestions?

---

### Post by ironic.demise on 2010-10-26
> **DayLite said:**
> I installed Homesteads SiteBuilder in wine. Trying to launch it for the first time it stalled when it came to 'Initializing GUI. 

Any suggestions?

Firstly, I prefer to use plain txt html editing...
Secondly, Try installing Virtualbox (sudo apt-get install virtualbox-ose)
then install WinXP, then install SiteBuilder.

Almost gauranteed to work.

---

### Post by ubudog on 2010-10-26
Can you try running it from the terminal?

---

### Post by DayLite on 2010-10-26
> **ironic.demise said:**
> Firstly, I prefer to use plain txt html editing...
Secondly, Try installing Virtualbox (sudo apt-get install virtualbox-ose)
then install WinXP, then install SiteBuilder.

Almost gauranteed to work.

I am now in the process of installing Virtualbox. I don't know anything about it or what it is? How do I install WinXP? Tell me the steps to take.  Remember, I am new to all this.

Ok, it installed.  My new question is that I don't understand the boot instructions and space required.  Does it mean that when I boot, instead of booting into Ubuntu it boots into a virtual machine?  If that is the case, doesn't it make more sense to just boot into my Windows partition?

Also is it possible to use a flash drive instead?

---

### Post by ironic.demise on 2010-10-26
> **DayLite said:**
> I am now in the process of installing Virtualbox. I don't know anything about it or what it is? How do I install WinXP? Tell me the steps to take.  Remember, I am new to all this.

Apologies for being brief.

Virtualbox is an emulator, you can use it to install and run an operating system within Ubuntu (or whichever OS you are using, beit Xubuntu, Archlinux etc.).

Download an ISO of Windows XP or insert an XP cd.
Open Virtualbox and create a new vitual machine.
the settings are relatively self explanatory but it's just setting hard drive space, ram and other settings that will be JUST for Windows XP (Or vista, or 7 if you install that).
Once virtualbox has the settings it needs, which won't take too long, it will begin to install Windows XP, that means that the virtualbox window will act as though it IS windows XP and will ask you to install XP to a drive(a "pretend" drive that Virtualbox is emulating).
once the windows setup is complete it will run, then you can download and install any Windows .exe file and it "should" run as if you weren't even aware ubuntu existed.

One warning, Virtualbox does NOT like 3d acceleration so games such as world of warcraft with intense grpahics wont run, but a web editor should run well.

It can be a bit resource intensive so it may run slower than a "native" installation but it should do the job, I hope this helps.

---

### Post by DayLite on 2010-10-26
> **ubudog said:**
> Can you try running it from the terminal?

I tried the terminal but I don't understand what to type. 

Example" sudo homestead and sudo sitebuilder, doesn't work.

---

### Post by ironic.demise on 2010-10-26
If you want to "try" and run it natively look at "playonlinux" it's a nice frontend for WINE that might help get some settings right.

Yes it's a virtual machine, it saves restarting the PC though.
Sometimes a WINE first run can take a while.
Are you running Applications>wine>programs>sitebuilder?

---

### Post by DayLite on 2010-10-26
> **ironic.demise said:**
> Apologies for being brief.
Virtualbox is an emulator, you can use it to install and run an operating system within Ubuntu (or whichever OS you are using, beit Xubuntu, Archlinux etc.).
.

Wow..you flooded my mind with all the detail. Now I understand why you were brief :confused:

This is very complicated for me to absorb. No big deal, I will just boot into my XP partition to run SiteBuilder.

Thank you for your time, I guess I am really just a beginner :(

(My desktop is Ubuntu 10.04 and the machine in question was for my Ubuntu 10.10 laptop).

---

### Post by DayLite on 2010-10-26
> **ironic.demise said:**
> 
Are you running Applications>wine>programs>sitebuilder?

Yes, I installed it with Wine and that is how I can launch it. Like I said, It begins but halts at initializing GUI.

---

### Post by ironic.demise on 2010-10-26
SiteBuilder, a paid for program.
Sitebuilders homepage won't even recognize my browser to allow me to download the software and try it, It says it recognizes firefox but, Apparantly not Linux Firefox.

The software seems very incompatable with Linux and I don't think you'll be able to get it to run in Wine.

Wine has trouble with some, but not many, windows programs, for example, it won't run online games that have a "hackgaurd" software bundled.

The only way I expect will work is with dual booting or virtualisation using virtualbox.

My suggestion is that you try a native to linux site-builder or code websites by hand until site builder develops support for linux.

---

### Post by ubudog on 2010-10-26
+1 for VirtualBox and Windows (preferably Windows XP, but others work fine too).  For me, it never fails and is a great tool for work if they have an insufficiently intelligent (lol) IT department and have Windows-only pages.

---

### Post by ubudog on 2010-10-26
> **ironic.demise said:**
> My suggestion is that you try a native to linux site-builder or code websites by hand until site builder develops support for linux.

Also a good idea.  There are some on sourceforge.net.  They are completely free and open-source too (since they are on sourceforge).

---

### Post by DayLite on 2010-10-26
> **ironic.demise said:**
> Sitebuilders homepage won't even recognize my browser to allow me to download the software and try it, It says it recognizes firefox but, Apparantly not Linux Firefox.


It **does** recognize Ubuntu. Try this add-on:  
****

**[[SIZE=4]User Agent Switcher     0.7.2[/SIZE]]("https://addons.mozilla.org/en-US/firefox/addon/59/")           **

[https://addons.mozilla.org/en-US/firefox/addon/59/](https://addons.mozilla.org/en-US/firefox/addon/59/)

You can even download stuff from Microsoft! It works and fools the site into thinking your operating system is Windows.

---

### Post by ubudog on 2010-10-26
> **DayLite said:**
> It **does** recognize Ubuntu. Try this add-on:  
****

**[[SIZE=4]User Agent Switcher     0.7.2[/SIZE]]("https://addons.mozilla.org/en-US/firefox/addon/59/")           **

[https://addons.mozilla.org/en-US/firefox/addon/59/](https://addons.mozilla.org/en-US/firefox/addon/59/)

You can even download stuff from Microsoft! It works and fools the site into thinking your operating system is Windows.

Cool addon, but still, try it with VirtualBox if you can.

---

### Post by DayLite on 2010-10-26
> **ubudog said:**
> Cool addon, but still, try it with VirtualBox if you can.

It sounds like it may mess up my partitions. Scares me when it told me to choose how much space to set aside on my hard drive.

I don't understand this. [https://help.ubuntu.com/community/VirtualBox/FirstVM](https://help.ubuntu.com/community/VirtualBox/FirstVM)

---

### Post by ubudog on 2010-10-26
Choose the harddrive named "VBOXHARDDISK" or something.  It should be the only option, and stores everything in a .vdi file or something like that.  There really is no danger, but if you want, back up your important stuff first.

---

### Post by ironic.demise on 2010-10-27
Everything is just pretend, if you set aside 500gb of space for VirtualBox on a 1tb hard-drive, No space on the 1tb harddrive will get lost, it just means it makes a file (usually nowhere near 500gb) that reflects the space used on Windows. You can set it to "dynamically" grow in which case the file will only grow when it needs to, so it can start at a few kb and then install XP on the virtual machine it will be about 2gb.

---

### Post by ubudog on 2010-10-27
> **ironic.demise said:**
> Everything is just pretend, if you set aside 500gb of space for VirtualBox on a 1tb hard-drive, No space on the 1tb harddrive will get lost, it just means it makes a file (usually nowhere near 500gb) that reflects the space used on Windows. You can set it to "dynamically" grow in which case the file will only grow when it needs to, so it can start at a few kb and then install XP on the virtual machine it will be about 2gb.

Yeah, it's pretty awesome. :)

---

### Post by ironic.demise on 2010-10-27
This guys like my new best friend ^_^

---

