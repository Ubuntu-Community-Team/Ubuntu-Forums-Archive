---
title: "Ubuntu install without desktop?"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by jfed on 2011-08-25
Hi. I have two questions.

I am going to be attempting to restore an old Pentium 3 for back in the day, these things ran like windows 95', maybe some less modern even. Also there is a lot of, shall we say wear-and-tear on these boxes I have too. So, what I need to know is

Can I install Ubuntu without a graphical environment? Because I'm not entirely sure if these things can even run one. Can/How do I do this?

Also, if that actually works, can I install a lightweight  desktop environment after the cli install? I would like to try and get LXDE running. How would I do that?

Thanks in advance!

P.S. I'm not sure this is in the right section, but I thought it should be a fairly simple thing to do (to find the .iso atleast)

---

### Post by dave01945 on 2011-08-25
ubuntu serever edition doesn't come with a graphical environment you could just remove the server apps you don't need also i hear lubuntu is a lightweight desktop never used it myself though

or the other optin is to buid up a custom distro not sure how you would do that though that's beyond my knowledge

---

### Post by wojox on 2011-08-25
Sure, just download and install the [MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD") and do a cli install and add to it. :P

---

### Post by soldersplash on 2011-08-25
Have a look here :-
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

The ubuntu-11.04-alternate-i386.iso can run a non-graphical installer but install normal desktop versions.

The ubuntu-11.04-server-i386.iso can be used to install a with no desktop at all. Then it would be up to you to set up a graphical environment.

I'd try the first, first. The later is quite a trial. You don't mention how much RAM the old box has? That will be the main parameter to limit what will run OK or not. I have in the past ran Ubuntu Desktop Edition on old boxes with 512MB of ram and it been usable for web browsing/email.

---

### Post by amjjawad on 2011-08-28
> **jfed said:**
> I am going to be attempting to restore an old Pentium 3 for back in the day, these things ran like windows 95', maybe some less modern even.

Please post the Hardware Details of your machine. 


> Can I install Ubuntu without a graphical environment? Because I'm not entirely sure if these things can even run one. Can/How do I do this?Yes, you can but before you rush into this approach, there are some steps to be taken into consideration. Again, please post your Hardware Details.

There are many Lightweight Linux Distributions. Lubuntu is definitely one of the best choices. If that didn't help, antiX, SliTaz and some other distributions might be helpful but keep in mind that you'll get the best support if you go for Lubuntu. AntiX has a perfect support on their forum too. Tried Slitaz but you'll have to do some extra work to get some drivers, etc. Slitaz is 30MB OS ONLY so don't expect very much. However, Slitaz will dazzle you :)


> Also, if that actually works, can I install a lightweight  desktop environment after the cli install? I would like to try and get LXDE running. How would I do that?Yes but before telling you how, please refer to my above paragraphs :)


> P.S. I'm not sure this is in the right section, but I thought it should be a fairly simple thing to do (to find the .iso atleast)It's the right section so don't worry ;)

Edit:
I have installed Mint LXDE on P2 @ 366MHz with 64MB RAM on a broken HP Laptop I guess it's from 1999 or 1998 and it worked. Didn't even have to go the alternate CD approach.

---

### Post by arlen_audio93 on 2011-08-28
Hello good forum, 

This is my first post. I recently installed Ubuntu along with windows 7 on a laptop. I don't have to use my CD but I know it's not a full version of Ubuntu that I installed. Perhaps this is not the right area to post this, as it's not specifically related to the first thread. It may be that someone can help though. (: 

i burned the ISO from the home site to disk and installed. all is working well; however, i have a few questions: 

if this is a limited version, what things would i not be able to do? 
i'm having trouble gaining root (if i use the su, or sudo commands) i receive an error message

i don't see how to mnt my C drive which has some windows files i'd like access to from the command line-when i switch to the /mnt folder, i do not see any drives listed after doing a ls command 
will it be much easier if i completely switch my laptop over to Ubuntu? 
I don't like  7 at all and i've lost my installation cd for XP


Seeking and open to suggestions: 
I'd like to switch completely over to Ubuntu. I have a laptop with Windows 7 on it, a desktop full of viruses with XP on it (without the installation cd) dua processor decent desktop once i get the viruses off) and a much older desktop. I was thinking of creating a home network for the learning experience and maybe as a server for online gaming etc

i actually would love to have a linux system set up as a Digital Recording Workstation. I have (hardware-Mbox 2 pro) and Pro Tools LE 7 (older version) and Reason 4.0 
I read about WINE but haven't to use it
i'm looking at using Reason Record, Reason and Recycle and possibly buying another ASIO device considering if i sell my Mbox 2 Pro
what ASIO devices work best with Ubuntu? 


so my main question is what would you suggest i do about my little situation.

---

### Post by arlen_audio93 on 2011-08-28
> **arlen_audio93 said:**
> i'm having trouble gaining root (if i use the su, or sudo commands) i receive an error message.

i'm actually able to issue the su command but get an error after entering the password
i guess this means i've forgotten my root password ?

do i have to reload and select Ubuntu to have access to the gui and command line because of this type of installation? 

i guess i should consider what programs and all i'll miss in 7 before switching over completely. i cannot think of anything in particular (: 
Pro Tools LE 7 and the hardware I have doesn't work with Windows 7 anyhow
only was able to use my MIDI controller with Reason 4.0 

you know some say the best way to fix windows is
format C:

---

### Post by amjjawad on 2011-08-28
arlen_audio93,

Please, start your own thread. You are confusing this thread and to get better help, start your own thread in here:

[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

Thanks for your understanding :)

---

### Post by jfed on 2011-08-31
amjjawad, I don't exactly have the hardware specs nor do I have any  way of aquireing them, seriously though these things are dinosaurs, I don't think the specs even matter when they're this old haha

also I haven't tried anything because I was unable to find a vga cable to plug into the machines :mad: but i will be trying a few suggestions soon, and i'll let you know how it goes

---

### Post by Lars Noodén on 2011-08-31
You can use the alternate installation cd.  That gives an option of installing a "Command Line System" which will be without graphics.  If you want something light, then you might try [Lubuntu](http://lubuntu.net/)

---

### Post by amjjawad on 2011-08-31
> **jfed said:**
> amjjawad, I don't exactly have the hardware specs nor do I have any  way of aquireing them, seriously though these things are dinosaurs, I don't think the specs even matter when they're this old haha

Usually you can tell that when you enter BIOS but your BIOS may not show that, it depends on the BIOS. Sometimes, you can tell from the first screen once you turn your machine ON. Another way is to boot into the LiveCD and you can run some System Info Apps.

LXDE works on very old machines but not sure how old is yours?

> i will be trying a few suggestions soon, and i'll let you know how it goes

Just let us know :)

Good luck with it. Installing Linux on Old Machines is one of my favorite things to do ;)

---

### Post by jfed on 2011-08-31
> **Lars Noodén said:**
> You can use the alternate installation cd.   That gives an option of installing a "Command Line System" which will be  without graphics.  If you want something light, then you might try [Lubuntu]("http://lubuntu.net/")
I was going to try something even lighter (I mean, assuming this machine can actually render a GUI) than LXDE, I was looking into using Fluxbox.

---

### Post by Lars Noodén on 2011-09-01
If you want even lighter then you might also look at FVWM-crystal.

---

### Post by jfed on 2011-09-01
> **amjjawad said:**
> Usually you can tell that when you enter BIOS but your BIOS may not show that, it depends on the BIOS. Sometimes, you can tell from the first screen once you turn your machine ON. Another way is to boot into the LiveCD and you can run some System Info Apps.

LXDE works on very old machines but not sure how old is yours?



Just let us know :)

Good luck with it. Installing Linux on Old Machines is one of my favorite things to do ;)

lol i like it too, and these things are DINOSAURS. from more than 15 years ago, I don't even think I will be able to boot from a livecd sucsessfully haha i don't think the gfx card can render such a gui, i've hit a bit of a reef seeing as i don't have any vga cables, but as soon as i find one i'll resume my work haha

---

### Post by Redmage913 on 2011-09-01
I would suggest using Ubuntu's mini.iso image, and doing a netinstall if you are able to hook it up to a wired network. If not, use the alternate ISO. You can tell it to install absolutely nothing other than the base system, and you can manually configure it to whatever you want.  Keep in mind, though, after you install this (if using 11.04), you'll boot up to a completely blank screen or a blank screen with a cursor: pressing Alt+F1 will bring up a text-based login.

You also may want to consider Arch Linux for the P3. It is perfect for this type of situation, and the text installer, while slightly more complicated, is almost just as easy. They have a beginner's guide that'll take you step-by-step through the process.

---

### Post by jfed on 2011-09-02
> **Redmage913 said:**
> I would suggest using Ubuntu's mini.iso image, and doing a netinstall if you are able to hook it up to a wired network. If not, use the alternate ISO. You can tell it to install absolutely nothing other than the base system, and you can manually configure it to whatever you want.  Keep in mind, though, after you install this (if using 11.04), you'll boot up to a completely blank screen or a blank screen with a cursor: pressing Alt+F1 will bring up a text-based login.

You also may want to consider Arch Linux for the P3. It is perfect for this type of situation, and the text installer, while slightly more complicated, is almost just as easy. They have a beginner's guide that'll take you step-by-step through the process.

Funny you should say that, I already have a P3 running arch with LXDE haha I'm using it as a seedbox, I wanted to try something different.

And yes, I can pull off a net install, but you mentioned two .iso's, which is the one that can "install nothing but the base system" and can be "Manually configured to do whatever I want" with? This was the mini iso correct? or both lol

---

### Post by Lars Noodén on 2011-09-02
> **jfed said:**
> ... you mentioned two .iso's, which is the one that can "install nothing but the base system" and can be "Manually configured to do whatever I want" with? This was the mini iso correct? or both lol

The Alternate install disc will have that option.

---

### Post by jfed on 2011-09-02
Ah, I see. I guess I'll try that one then.

---

### Post by pissedoffdude on 2011-09-02
> **jfed said:**
> Hi. I have two questions.

I am going to be attempting to restore an old Pentium 3 for back in the day, these things ran like windows 95', maybe some less modern even. Also there is a lot of, shall we say wear-and-tear on these boxes I have too. So, what I need to know is

Can I install Ubuntu without a graphical environment? Because I'm not entirely sure if these things can even run one. Can/How do I do this?

Also, if that actually works, can I install a lightweight  desktop environment after the cli install? I would like to try and get LXDE running. How would I do that?

Thanks in advance!

P.S. I'm not sure this is in the right section, but I thought it should be a fairly simple thing to do (to find the .iso atleast)

As suggested in this thread, you could get an alternate cd and install a base-system with a lightweight window manager.  But considering you said it was a very old system, I suggest you run something other than ubuntu. Post your full system specs for a more appropriate answer. But with what you said in mind, Feather Linux, although not updated recently, should give you the greatest speed in conjunction with working applications for the type of system I'm assuming you have.  Again, not sure exactly how powerful your rig is, but I'd recommend feather, dsl, and puppy over an ubuntu alternate install, as they are better-suited for older systems

---

### Post by Lars Noodén on 2011-09-02
> **Lars Noodén said:**
> The Alternate install disc will have that option.

On the Alternate disc, F4 should give the option to "Install a command-line system" from there, light weight window managers like FVWM-crystal or OpenBox can be installed manually.

---

### Post by jfed on 2011-09-02
oooh, alright, thanks again. I've found a VGA cable so I think tomorrow night I can resume my attempt at resurrecting this thing haha

thanks for everyone's input once again :)

I'll definitely try to go for an alternate install without a gui first

---

