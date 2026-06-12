---
title: "New user - many problems!"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by ChrisBrunet on 2009-11-22
So this is my first time using any Linux OS and it's not going well to this point... I am unable to install any programs as I keep getting error messages.  All I have are the programs that were installed with Ubuntu.  I did print-screens of the messages I got but at this point I'm thinking that it may be easier to just try a total reinstall before I try to trouble-shoot.  So I put my boot disk into my cd drive and restarted, but it just restarted the O/S.

Question - how do I do a complete reinstall?  Do I need to download a different file since the first disk I made was probably for users switching from Windows?

Many thanks!
Chris

---

### Post by marshmallow1304 on 2009-11-22
How did you install?  Did you boot from the CD, or did you put the CD in after you already started Windows (i.e. wubi)?

---

### Post by ChrisBrunet on 2009-11-22
I put the cd in while Windows was running, then it prompted me to restart.  I restarted and went through the installation process.

I've tried restarting my computer with the disk in but it just reboots from the hard drive.  How do I force it to boot from the cd?  I am assuming this is how I will be able to reinstall?

---

### Post by vkcaspervk on 2009-11-22
There is a problem with the update/install servers for some people. ( me included ) You will get funny error if trying to update or install stuff.
Give it some time I am sure they will work sometime soon...
If you are errors you get while booting, that is different, and we will need more info. =x
[URL="http://ubuntuforums.org/showthread.php?t=1333810"]
http://ubuntuforums.org/showthread.php?t=1333810[/URL]

---

### Post by roger_1960 on 2009-11-22
Hi

How are you trying to install programs?  The easy ways are by using Synaptic Package manager (in menu/system/administration) or by using Add/remove...  Isuspect you might be trying to install .exe files? (if not  - sorry, dont mean to insult)

To reinstall from scratch (which I'm not sure you need), set your BIOS to boot from CD first (you may have done this to install Ubuntu) put the CD in the drive before turning off and then reboot with the disc in.  Select the option to "use whole disc" or similar to completely rewrite your hard drive.  (Dont do this if you wish to dual boot or keep any data)

---

### Post by ubume2 on 2009-11-22
Edit: There weren't any responses when I first started typing this. Now there are 5. If you did an install within Windows (WUBI) and want to keep it that way, disregard this post.
Well, you can do a complete reinstall.

How did you install Ubuntu in the first place?  I would recommend a live CD.
If you already have a live cd, it sounds like your computer is not set to boot the cd first as I think you are saying that you are going into the installation of Ubuntu.

Do you have any other Operating Systems on the hard drive you installed Ubuntu?

Use the live CD to reinstall and do a manual reinstallation to erase the existing Ubuntu.

Here is a general guide to installing from a CD:
[HTML]http://www.psychocats.net/ubuntu/installing[/HTML]

Here's how you get an image to download a live cd:
[HTML]http://www.ubuntu.com/getubuntu[/HTML]

I have used Ubuntu for 3 years and am still new to Ubuntu.

---

### Post by ChrisBrunet on 2009-11-22
I've tried the Synaptic Package manager but it won't even start - an error window pops up with 5 or 6 messages that are Greek to me.  Otherwise, when I download something using Firefox(Adobe Flash Player for example), I select "run" when it asks me what I want to do with the file and then I am prompted to select an application to use, but there are no applications on the list.

Anyway, nothing seems to be working so I want to try a full reinstall.  Hopefully this will fix whatever the problem is.

---

### Post by asuastrophysics on 2009-11-22
> **ubume2 said:**
> 
I have used Ubuntu for 3 years and am still new to Ubuntu.
+1!
haha...same here, I'm always learning something new

ChrisBrunet, if there is a problem w/ installing / uninstalling, perhaps it is an issue with the newest version of Ubuntu, 9.10 Karmic. What version of Ubuntu did you install? Have you tried installing an earlier, more stable (and more perfected) release? 

Ubuntu 8.10 (Intrepid) is an excellent release, and I highly recommend installing this earlier version of Ubuntu for the most bug-free experience. You can find the ISO here:
[http://releases.ubuntu.com/8.10/](http://releases.ubuntu.com/8.10/)

Just make sure to click on the link for your processor. :D

I hope this helps! If not, just reply back, I'm sure we can get this fixed. ;)

---

### Post by t0p on 2009-11-22
If you want to reinstall, reinstall.  But I can't see the point.  It may be very easy to fix your problem if you give us more details.

It's very odd for Synaptic to not "even start", as you put it.  If you post here the error messages you're getting, someone may be able to help/explain where you're going wrong.

Installing programs you've downloaded from the internet is not the simplest thing in the world for a newbie to do.  You'd be much better of posting the error messages you got from Synaptic.

---

### Post by Bradtek on 2009-11-22
```
an error window pops up with 5 or 6 messages that are Greek to me.
```

It may be greek to you, but unless you tell us what 
the errors say, how do you expect to get help ?

---

### Post by Claus7 on 2009-11-22
Hello and welcome,

> **ChrisBrunet said:**
> So this is my first time using any Linux OS and it's not going well to this point... I am unable to install any programs as I keep getting error messages.  All I have are the programs that were installed with Ubuntu.  I did print-screens of the messages I got but at this point I'm thinking that it may be easier to just try a total reinstall before I try to trouble-shoot.  So I put my boot disk into my cd drive and restarted, but it just restarted the O/S.

Question - how do I do a complete reinstall?  Do I need to download a different file since the first disk I made was probably for users switching from Windows?

Many thanks!
Chris

Since you have pics of the errors it would be nice to upload them and post them here. That way someone will be able to help you seeing which problems you are facing.

I still have not understood how you did the installation. Generally there is the "simulated" installation inside windows which means that you are using ubuntu inside windows and secondly the "normal" installation in which either you dual boot with another OS or you have a clean install of ubuntu.

In order to make a fresh install of the ubuntu OS, then I suppose than inserting the ubuntu cd inside your drive and enabling from the BIOS to boot from there, you will be able to have a fresh and new installation very quickly.

Do not forget to specify the ubuntu version you have and how you intend to do the installation.

Regards!

---

### Post by ChrisBrunet on 2009-11-22
Hey guys, thanks for all your suggestions and offers to help if I posted the error messages... but I did a full reinstall and now everything seems to be working fine.

I think the problem occurred when I was installing updates shortly after my first boot of Ubuntu, my computer overheated and shut off in the middle of the installation.  When I restarted is when I started having the problems.

Clean install, no overheating or interruptions when installing updates and all is well so far.  Thanks again,

Chris

---

