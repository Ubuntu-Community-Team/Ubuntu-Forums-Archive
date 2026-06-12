---
title: "How to get Linux working on an Acer Aspire 4730Z"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by NutCase2000(INSANE) on 2010-08-26
[FONT=Arial]Okay, so I've been using Windows ever since my mom first brought home a computer when I was so young I thought MS Paint rocked. Now 16, and I've pretty much decided that Windows is junk. So I want to switch to Linux, preferably Ubuntu, but I'll take anything I can get. Right now I've just got an Acer Aspire 4730Z, and I can't afford to get anything else, so don't just tell me that Acers stink. I already know that. I just need help figuring out how to get a Linux installed on it. I know it's possible, because a bunch of people using that model have been using Linux. The only thing is that I need to keep Windows on my laptop, because I still have some tools on it that are not yet compatible with Linux. I may switch completely to Linux one day (hopefully soon), but that day is not today.
So, to sum it up I need:
Help figuring out how to get ANY Linux to work on my Acer,
Help figuring out which one, if not Ubuntu,
and your forgiveness for being a noob.[/FONT]

---

### Post by lukeiamyourfather on 2010-08-26
Download Ubuntu, burn it to a disc, insert the disc and boot from it, follow the directions Ubuntu provides. Let us know which parts you need help with and we'll be glad to do so.

---

### Post by _0R10N on 2010-08-27
I'm not familiarized with Acer models but if it's relatively new and installation process fails when attempting to begin the whole process you could add the following to the install instruction
```
 acpi=off
```
Remember that, if you want to keep your Windows installation, two extra partitions would be required (one for your Linux filesystem and another one for SWAP).

---

### Post by NutCase2000(INSANE) on 2010-08-27
Is there no way to get Wubi to work? I'm sorry, but I honestly can not risk messing up my laptop, because if I do then I can't get a new one. The Windows installer looked like it was good, except that it said it couldn't download the metalink. What was that all about?
Again, sorry for a being a noob.
And thanks for answering so quickly.

---

### Post by zeroseven0183 on 2010-08-27
I assume you already have the .ISO of Ubuntu. I usually do this to make Wubi work, download a copy from [http://wubi-installer.org/](http://wubi-installer.org/) and save it on the same folder where you're Ubuntu .ISO is. Then launch it from there. Follow the instructions carefully and post anything you want to clarify here.

---

### Post by NutCase2000(INSANE) on 2010-08-27
Sorry, I'm a mega noob as far as Linux goes. It said it was supposed to download the ISO. No, I don't have the Ubuntu ISO.

---

### Post by sidzen on 2010-08-27
Here's what I would do:

Get clonezilla and clone your hard drive after removing all non-essentals -- [http://clonezilla.org/download/sourceforge/](http://clonezilla.org/download/sourceforge/).
Get SystemRescueCD and burn it to a CD -- [http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/](http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/) 
(I recommend 1.3.5)
Use from sysresccd  either *dban* or the dd command < dd if=/dev/zero of =/dev/sda bs=4096 conv=notrun,sync > to wipe hard drive with zeros for a clean install.
Partition your hdd with *gparted* (fom sysresccd), making sure to flag the / partition as_ bootable_.
Once all this is done, come back for further help, but . . . Don't use wubi!

Install the ubuntu of your choice.
(I assume you have at least one gig of RAM - correct?  If not, please state your system specs.)



Best wishes for a good Linux experience.

---

### Post by NutCase2000(INSANE) on 2010-08-27
as I said, I'm a total noob... :( PLEASE speak in a way that is easier for me to understand. I know it's hard, but please think, what if you were me? And the reason I was going to use wubi was because I am such a noob, and I want to use Ubuntu, but not change a bunch of stuff. I know a guy who MAYBE can help me get Ubuntu working on my system, but he would completely replace windows. I wanted an easy way to try Ubuntu before deciding...

And thanks for the advice.

---

### Post by sidzen on 2010-08-27
Check this out, then -- [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
and [http://www.osdisc.com/cgi-bin/view.cgi/products/usb/ubuntu](http://www.osdisc.com/cgi-bin/view.cgi/products/usb/ubuntu)[]("http://www.pendrivelinux.com/")

---

### Post by NutCase2000(INSANE) on 2010-08-27
[sidzen,]("http://ubuntuforums.org/member.php?u=1054457") thank you for the links, but I do not intend to pay anything for a Linux. that's why I want Linux instead of just switching to Mac, because Linux is FREE. *sigh* I guess I'll just keep trying on my own.

---

### Post by zeroseven0183 on 2010-08-28
> **NutCase2000(INSANE) said:**
> Sorry, I'm a mega noob as far as Linux goes. It said it was supposed to download the ISO. No, I don't have the Ubuntu ISO.

Alright. You can download Ubuntu here [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) The file is about 700 megabytes and fits to a CD. The instructions are also on that page.

Once you're done downloading, burn the ISO image to a disk using any tool you like. But be sure you "burn image".

---

### Post by NutCase2000(INSANE) on 2010-08-30
hey, thanks. I'll try that!

---

### Post by NUboon2Age on 2010-08-30
I've been running a Wubi install of 10.04 on that exact model for months and it worked fine.  Amazingly simple to do the install and mostly just works.

If you're able to connect to the web from your machine you can do a net install off their web site (mentioned above) without even needing to burn a disc (though its a good idea to have one handy anyway).  Backing up is always a good idea at any rate.  Usually there are no problems with Wubi, but lately i ran into a serious bug with Wubi (i don't think it would apply in your case if you only have one partition and one OS on there already) but its always a good idea to be safe and back up at any rate.

---

### Post by gabriel8a2002 on 2010-08-31
I have a suggestion, why dont you just reduce your hard drive space in windows by like 10 gb and then install ubuntu through the live cd.  I think thats easier than wubi.

---

### Post by NutCase2000(INSANE) on 2010-08-31
I actually have no clue what a .ISO is... :/
And to the one that said that Wubi just worked, it told me that it couldn't download the metalink, and therefor the .ISO...

---

### Post by NoNameWill on 2010-08-31
Before I went all linux on my laptop aspire 4520 I installed wubi under win 7. I had a internet connection so wubi installed ubuntu 10.4 from the net. If you have a nvidia card be prepared to install the driver from terminal. Not hard and is a good exercise in linux and use of terminal. 

Once I was confident in linux took me about a week to throw caution to the wind. lol 
And went all exclusive.

Here is what I had to do to get nvidia to work properly

[http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+lynx](http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+lynx)

This phrase below is correct in the link but the current build is different. So after d/ling from nvidia write the name of the package down and use that.
     ```

     sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run[FONT=Verdana]
```


[/FONT]

---

### Post by NUboon2Age on 2010-09-08
> **NutCase2000(INSANE) said:**
> 
And to the one that said that Wubi just worked, it told me that it couldn't download the metalink, and therefor the .ISO...

Actually i said "mostly just works", (mostly being operative) and that's absolutely true -- mostly but not 100% of the time -- then i went on to say i'd run into some bugs with it, but they probably wouldn't apply to you.  So i'm sorry to hear you ran into some different problems.

Don't forget i mentioned that i've actually done a Wubi Kubuntu 10.04 install on your very model of computer, so i know it can be done.  I used a wireless connection to do a Wubi net install.  If Wubi net install doesn't work for you, try the following method:

BTW, an .iso file is the image file of the OS you want to install.  You can download it directly from [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) .  Probably you'll want the 32bit version.  You said you didn't know how to burn a disk, but for the below Wubi install method you won't need to.

I did some googling for "wubi, metalink" (As they say, "Google is your friend") and found this:
> 
[http://ubuntuforums.org/showthread.php?t=1131901&page=2](http://ubuntuforums.org/showthread.php?t=1131901&page=2)
Hi, I had the same problem, and as suggested by antrunner85, I simply placed the .iso in the same dir as the wubi.exe and it worked fine.

Elsewhere on that page someone mentioned they had trouble with running the Ubuntu 64bit version (even though their computer was AND YOUR COMPUTER is 64bit), but did fine with 32bit version.

---

### Post by chris winter on 2010-11-21
Nutcase2000 (INSANE)
I have the Acer Aspire 4730Z, a $230 reconditioned little gem.
I dumped Windows XP last year after 3 months of back & forth with tech support to remove
2 rootkits, a bunch of trojans & assorted malware, spy-ware & keystroke loggers.
Being a K.I.S.S. (Keep It Simple, Stupid!) guy, I ordered the Free Ubuntu 9.04 CD & installed it on the Acer.
But first, back up all your personal stuff, Music, Docs, Pictures, etc.
Look up pricewatch.com. I bought another 120 Gig hard drive & a USB case to save my Windows files to.
You can either order a FREE CD from Ubuntu, or download an ISO directly.
I download to a USB Memory stick, (it's only 600-750 MB), then plug it in, (change the
boot device in Bios to USB Drive), & follow the instructions.
I now have Ubuntu 10.10, but LinuxMint looks good also.
You won't be playing any good Windows games on the Acer, it just isn't fast enough.
If you do use Ubuntu, set up Gufw 10.04.5, the firewall! 
SheildsUp! (Web site) will check your firewall for free.
And on Firefox, install WOT, (Web of Trust) as an extension, it will keep you out of trouble.

You're 16 & don't know any Otaku (computer nerd)? 
Find one, preferably a cute EMO girl with skills.
Enjoy Ubuntu, remember, no question is stupid, don't quit, keep asking until you get an answer.

---

