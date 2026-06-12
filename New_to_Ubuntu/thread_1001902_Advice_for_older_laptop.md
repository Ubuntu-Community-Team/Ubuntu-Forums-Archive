---
title: "Advice for older laptop"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by enricong on 2008-12-04
I have a somewhat old mini-laptop.  [1Ghz Pentium M, 768MB ram, 40GB](http://www.itreviews.co.uk/hardware/h565.htm).
It runs XP Pro right now but is alittle sluggish.  I basically use it for web browsing, email, IM, videos, etc when I am on travel.  Rarely I'll try a game or something.  Power management is a must since its a laptop.  I'd like to beable to plug in a USB device without having to manually set it up.  I'm basically looking for a performance speedup.

Which flavor would be recc? I have a slight preference to KDE.  so Kubuntu?  or maybe Xubuntu? or something else.  Since I will only use this laptop on travel, having alot of extra options in the UI is not that important.  It will prob. be better to keep things simple.

I have experience with linux and have used debian for years.  Mainly as a server without any GUI.

For my laptop, I'd have a heavy focus on speed and ease of use.  I don't want to have to pull up a terminal and debug/compile something while I'm sitting at the airport.

I think i will try setting up a live USB to try it on my laptop first.  (It doesnt have a CD drive)

Thanks

---

### Post by snowpine on 2008-12-04
Hi Enricong, welcome to the forums!
Your computer is not that bad; many of us (including myself) have installed Linux on far worse. :)

With 768mb of ram, you can definitely install any flavor of K/X/Ubuntu. They all support power managment and auto-mounting of USB drives, as far as I know (never personally tried Kubuntu). Xubuntu is the fastest and most stripped-down of those three options.

For best performance, I am a big fan of a windows manager such as Openbox instead of Gnome or KDE. I think configuring Openbox is fun, but not everyone agrees with me, so if you are looking for a great shortcut, there is a lightweight desktop environment called LXDE that can be added to any existing K/X/Ubuntu install. Or, you can try an Ubuntu derivative such as Crunchbang (highly recommended by yours truly!) that uses Openbox from the get-go. Other lightweight windows managers include Fluxbox, IceWM, JWM, etc.

And that's not even mentioning other non-Ubuntu distros such as Debian Lenny or Sidux (which is KDE by default)...

---

### Post by enricong on 2008-12-04
Thanks for the quick reply.

I guess I wasn't sure what is different between the variants other than the window manager.  The overview on the mainsite didnt go into too much detail.  Is there a comparison table somewhere that goes over what is stripped out in Xubuntu?


My goal is basically to have something that runs faster than windows with a similar amount of functionality for my purposes (web browsing, email, IM, videos, wifi, etc).

I took a look at Openbox, CrunchBang, LXDE, but it is hard for me to compare them.  They all give a general description but like Xubuntu, it isnt clear to me how it is faster.  I assume something is taken out, otherwise the main variant would be just as fast.  Do you know of any articles, threads, etc that directly compare some of these?

thanks

---

### Post by snowpine on 2008-12-04
Probably more detail than you are looking for :) but:

[http://packages.ubuntu.com/intrepid/ubuntu-desktop](http://packages.ubuntu.com/intrepid/ubuntu-desktop)
[http://packages.ubuntu.com/intrepid/kubuntu-desktop](http://packages.ubuntu.com/intrepid/kubuntu-desktop)
[http://packages.ubuntu.com/intrepid/xubuntu-desktop](http://packages.ubuntu.com/intrepid/xubuntu-desktop)

Basically, they do have different applications by default (Kubuntu has lots of KDE apps that start with K; Xubuntu includes Abiword and Gnumeric instead of Openoffice, etc.) but you can install any application you need yourself regardless of which you use, because they have the same repositories. For example, some people use Amarok (a KDE music player) in Gnome because they prefer it to Rhythmbox...

---

### Post by enricong on 2008-12-04
I see.

Well I think I'll take a hard look at Xubuntu with LXDE or Crunchbang.  Since Crunchbag doesnt look like an official variant, I may lean towards Xubuntu to avoid any problems.

---

### Post by snowpine on 2008-12-04
> **enricong said:**
> I see.

Well I think I'll take a hard look at Xubuntu with LXDE or Crunchbang.  Since Crunchbag doesnt look like an official variant, I may lean towards Xubuntu to avoid any problems.

I think that is a wise decision--Xubuntu would be the most "official" and hassle-free place to start. If you decide it is too slow, there are many possible tweaks, but you can cross that bridge when you get to it (as my dad always says).

---

### Post by mkvnmtr on 2008-12-04
Your machine has plenty of ram and speed to run the Ubuntu based distros. For some one that is beginning Ubuntu or Kbuntu will probably be the most comfortable.You can play with the minimal systems later when yoou are used to the Linux style of doing things. welcome.

---

### Post by enricong on 2008-12-04
Well, I plan try try making a live USB install first before I wipe out my windows system.  So I guess it should be pretty easy to try both.  Hopefully everything will work and it'll be faster than windows.  Crunchbang looks nice but I don't want to deal with random crashes or anything like that

---

### Post by snowpine on 2008-12-04
Sounds like a plan, just don't expect it to necessarily be faster than XP, especially running from a slow flash drive. Better, yes! :)

---

### Post by mkvnmtr on 2008-12-04
You are right you should try out the live disks for a while before you decide. Then give a lot of thought to a dual boot. You don't have to give up windows you can have both. Then if you are like me and mess up Ubuntu you just restart in the other system and ask for help here in the forums.

---

### Post by enricong on 2008-12-04
> **snowpine said:**
> Sounds like a plan, just don't expect it to necessarily be faster than XP, especially running from a slow flash drive. Better, yes! :)

Well, I can understand that it would run slower on a flash drive, but I'd be disappointed if it still was slower when running on the hard drive.  The main reason I wanted to try linux on my laptop was to try to have something run faster without the extra crap windows has.  I only use this laptop on travel to do simple things like web, email, videos, im, office, etc.  I don't really require any additional functionality or features.  I'd just like something faster.  I figured that windows has alot of extra bloat that I might be able to get rid of with a lite install of linux.

If installing linux on my laptop won't be any faster at all, then I should probably just stop now.

---

### Post by snowpine on 2008-12-04
> **enricong said:**
> Well, I can understand that it would run slower on a flash drive, but I'd be disappointed if it still was slower when running on the hard drive.  The main reason I wanted to try linux on my laptop was to try to have something run faster without the extra crap windows has.  I only use this laptop on travel to do simple things like web, email, videos, im, office, etc.  I don't really require any additional functionality or features.  I'd just like something faster.  I figured that windows has alot of extra bloat that I might be able to get rid of with a lite install of linux.

If installing linux on my laptop won't be any faster at all, then I should probably just stop now.

No, no, no, don't stop now! Learning Linux is a lot of fun, and there are many rewards and benefits.

All I was pointing out in my previous post is that there's much debate within the community about whether or not Ubuntu is faster than Windows XP, for example: [http://ubuntuforums.org/showthread.php?t=1001813](http://ubuntuforums.org/showthread.php?t=1001813)

What you have to keep in mind is that Windows XP is a 7 year old operating system that was released at a time when most consumers used Pentium 2 and 3 computers with 128-256mb of ram. Furthermore, many of these computers have "designed for Windows XP" stickers on them, meaning they are optimized and tested to run flawlessly with XP. 

On the other hand, Ubuntu Intrepid Ibex 8.10 is a two-month old operating system designed for the typical computer of today. If you are going to compare it with a Microsoft product, compare it with its contemporary, Vista.

There is no question in my mind that Linux distros designed to be fast (such as Arch or Slitaz) are really, really fast. However, speed was not the  #1 design goal of Ubuntu. First and foremost, Ubuntu is designed to be "Linux for human beings" meaning it is user-friendly, intuitive, attractive, and usable by people all over the world. This inevitably comes at a certain price in terms of performance and hardware requirements.

I am not saying that Ubuntu is horribly slow--far from it--but if your #1 goal is pure speed on old hardware, it is not even in the top 10 (in my opinion).

---

### Post by enricong on 2008-12-04
I'm not giving up using linux entirely.  I've already used linux for the past 10 years both at work and home.  I have a separate debian system that I use at home mainly for software development.  I use it through Exceed on my XP box so I havent really used the desktop environment much.

For my laptop, I use it for a much different purpose.  Just web, office, email, video, etc.  This works just fine in XP and Linux.  It doesnt matter if my OS is capable of doing much more.  The laptop is working just fine for me except it is a little sluggish.  I figured that if I get linux setup right, I could achieve this goal.  However if it won't run any faster, it will have just wasted my time.  Sure, I may have a better OS with alot more options, but for the main use of this laptop (web, office, email, video, etc) I will likely see no gain.

I assumed that if a lite-linux install will use less memory and be smaller in size and likely have less applications running (anti-virus, misc windows services, etc), my system should run faster.  Perhaps this assumption is wrong.

---

### Post by snowpine on 2008-12-04
Please don't let me scare you off Linux for your laptop. :) I think it is superior to Windows in just about every way. However, I am forced to use XP at work every day, and I would be lying if I said Ubuntu has a decisive speed advantage (assuming of course the XP system is free of viruses, spyware, etc--which is a pretty big if). Just being honest with you. ;)

Frankly, since you have lots of experience with Debian, I would heartily recommend Debian Lenny with either the LXDE or Xfce desktop environment. It is noticably faster than any flavor of Ubuntu in my experience. Xubuntu would be a good 2nd choice.

ps I'm sure you're aware you can set up a dual boot? That way you can compare them side by side on the same hardware and draw your own conclusion.

---

### Post by enricong on 2008-12-04
Well I think a dualboot is out of the question right now because my drive is very full.  otherwise I would have tried that.

Maybe I can mirror it so I can save it although doing a live USB might be faster to try.

Its interesting that you suggest debian.  I had thought that ubuntu would faster than debian.  I had also read that crunchbang would be faster than xubuntu but I guess that all depends on how "fast" is defined.

Anyways, thanks for your advice, I'll end up trying something.

---

### Post by snowpine on 2008-12-04
> **enricong said:**
> Its interesting that you suggest debian.  I had thought that ubuntu would faster than debian.  I had also read that crunchbang would be faster than xubuntu but I guess that all depends on how "fast" is defined.


Actually I am typing this message with Crunchbang right now. It is my favorite "every day" distro and I find it's faster than Xubuntu for sure. Crunchbang actually has quite a bit in common with LXDE (they both use Openbox for starters).

As for the Debian vs. Ubuntu thing, Ubuntu seems to have an extra layer--some call it "bloat"--that makes it noticeably heavier than a comparable Debian setup. Particularly if you are using the gnome desktop (which I don't). I would also give Debian the edge in stability as they have a slower release cycle and really try to solve every bug before labeling a release as "stable".

It is awesome that there are so many distros to choose from, though sometimes a bit overwhelming. I've been at it for  about a year, and I'm still learning.

---

### Post by enricong on 2008-12-04
How do you think crunchbang compares to Debian.  Since it is based on ubuntu, would it therefore run slower than debian?

Ever since I started using Debian several years ago, I stopped keeping tracking of other distros so I don't really know the difference between all of them.  I figure I could install or remove whatever I needed.  I guess I was hoping there was a quick solution for my laptop since I only plan to use it for a limited number of functions.

I think I may try crunchbang first, then perhaps debian with lxde.  In the past, I have always had problems getting power saving stuff to work and had to struggle for a while to get everything detected and setup properly.  Hopefully this install will go smoothly.

Also, by "sluggish" in my other post, I mean I think the computer doesn't have enough ram (768MB).  I often click something or load a webpage and have to wait a while for it to load up while accessing the hard drive cache.  I'd add more ram but 768MB is the max for this laptop.  I know that linux generally uses less memory but it also has less stuff preloaded.  If I look at what uses the most (RAM/page) right now in windows, its firefox (97MB/85MB), explorer (64/47), outlook (41/35), svchost (32/18), IM (16/34), antivirus (12/104)

I would think firefox and IM software would use the same amount of ram in linux.  don't know about the window manager and other services.  I guess I'd save on antivirus.  so I guess I can see how the speed may not differ much.

---

### Post by handydan918 on 2008-12-04
> **enricong said:**
> 
Its interesting that you suggest debian.  I had thought that ubuntu would faster than debian. 


That sure hasn't been my experience, at least on older boxen. I have Lenny and kde running on an ancient Dell gx110 733ghz/256megs, and while it doesn't scream, it is functional! Yes, even with kde...

---

### Post by enricong on 2008-12-04
Perhaps all this requires more thought.

I'm looking for a speed increase however I have not really taken much time to find out what my bottle neck is.

I have noticed there is a lag and it usually coincides with alot of HD access.  I know 1GB is usually minimal for XP to run smoothly so I assume that something in XP needs to use up alot of RAM causing all these memory access misses to goto virtual memory.

Assuming my hypothesis is correct, I either would need to add more RAM or lower the memory usage.  The HW is already maxed out and I've done all I know of to lower memory usage in XP.  I know that people are able to run linux in much older computers with much less memory so I assumed (maybe incorrectly) that if I switched to linux I'd automatically be running faster.  I guess eventhough linux can run with very low RAM, it may not run fast but at least it runs.

Or my hypothesis could be wrong and something else could be causing the lag.  Maybe I'm just use to my dual core 2ghz athlon64 with 4gb ram and am expecting too much.

---

### Post by theozzlives on 2008-12-04
I have an old Compaq 333 MHz  256 MB RAM and a 35 GB HD that Windows XP was slooooooow on, but I put Ubuntu on, with the GNOME desktop. It runs at a decent speed now. I use it with Apache for my web site.
  When I got my laptop with Vista on it, I  put Ubuntu on right away. Windows is to "bulky" and I don't like the  way KDE handles the network. Never tried Xubuntu as  I'm happy with Ubuntu, even on my older computers.

---

### Post by snowpine on 2008-12-05
> **enricong said:**
> How do you think crunchbang compares to Debian.  Since it is based on ubuntu, would it therefore run slower than debian?


Tough to say with 100% accuracy because hardware varies. For example, your computer seems to be slowing down with hard drive access, whereas mine might have a slow graphics card, so we might have different optimal distros. :)

In general though, I'd hypothesize Crunchbang is probably faster than a full Debian Gnome desktop, but probably not faster than a comparable Debian desktop with Openbox or LXDE.

(The main reason I like Crunchbang honestly is not so much the speed (which is a nice bonus) but that it comes with all the applications and codecs I need, so I can just install and start working.)

> **enricong said:**
> I think I may try crunchbang first, then perhaps debian with lxde.  In the past, I have always had problems getting power saving stuff to work and had to struggle for a while to get everything detected and setup properly.  Hopefully this install will go smoothly.


Install the package 'gnome-power-manager' (if necessary; it's already installed in a lot of distros) and add it to your startup script, and you should be good to go. It works flawlessly on my eee pc including suspend and hibernate.

---

### Post by mikjp on 2008-12-05
Vector Linux with KDE might be a good solution.

---

### Post by enricong on 2008-12-05
> **snowpine said:**
> (The main reason I like Crunchbang honestly is not so much the speed (which is a nice bonus) but that it comes with all the applications and codecs I need, so I can just install and start working.)

Actually, that was the main reason I was looking elsewhere from debian.  I was hoping to find something that comes with applications and codecs installed.  Usually after installing debian, I have to install a host of software and likely remove a bunch of software I don't need, then setup/configure/tweak the hardware so everything works right.  Then if I was using the UI, I'd have to setup the desktop the way I like it.  I usually end up with a ton of extra stuff I don't need.  I don't keep up to date with whats going on enough to know what is safe to remove.  I've tried starting with minimal first and adding stuff but I ran into similar problems trying to figure out what needs to be added.

I had hoped to skip all that for my laptop but speed is number one for my laptop.  Since memory usage is what I'm thinking is causing my slow down, I should prob go with whatever uses the least amount of RAM.

---

### Post by halitech on 2008-12-05
instead of doing a full install and then removing what you don't need, do a minimal install and build your own from the ground up

minimal install
[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

speeding up debian
[http://forums.debian.net/viewtopic.php?t=14129](http://forums.debian.net/viewtopic.php?t=14129)

debian tuning
[http://forums.debian.net/viewtopic.php?t=7314](http://forums.debian.net/viewtopic.php?t=7314)

---

### Post by xikarrousx on 2008-12-05
like everyone else said, your computer has the capabilities to run any of the linux desktop environments... it pretty much comes down to preference. check out the screenshots of x/k/ubuntu and see which one you like the most.

---

### Post by enricong on 2008-12-05
> **halitech said:**
> instead of doing a full install and then removing what you don't need, do a minimal install and build your own from the ground up

minimal install
[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

speeding up debian
[http://forums.debian.net/viewtopic.php?t=14129](http://forums.debian.net/viewtopic.php?t=14129)

debian tuning
[http://forums.debian.net/viewtopic.php?t=7314](http://forums.debian.net/viewtopic.php?t=7314)

I have thought of doing that.
I tried that once in the past but had problems figuring out what to add.  I'd have lots of stuff that wouldn't run right but also wouldn't give me any indication of what is missing.  For example, I wouldn't have known the name of the wifi configuration tool or the power saving tool if it wasnt already installed.

That thread looks promising though so I may give that a try.

---

### Post by halitech on 2008-12-05
I've used it for multiple installs on multiple machines and I'm impressed. Not sure if it gives any advice for wireless stuff but thats where you add synaptic and do a search for wireless :)

---

### Post by abn91c on 2008-12-05
> **enricong said:**
> I have a somewhat old mini-laptop.  [1Ghz Pentium M, 768MB ram, 40GB](http://www.itreviews.co.uk/hardware/h565.htm).
It runs XP Pro right now but is alittle sluggish.  I basically use it for web browsing, email, IM, videos, etc when I am on travel.  Rarely I'll try a game or something.  Power management is a must since its a laptop.  I'd like to beable to plug in a USB device without having to manually set it up.  I'm basically looking for a performance speedup.

Which flavor would be recc? I have a slight preference to KDE.  so Kubuntu?  or maybe Xubuntu? or something else.  Since I will only use this laptop on travel, having alot of extra options in the UI is not that important.  It will prob. be better to keep things simple.

I have experience with linux and have used debian for years.  Mainly as a server without any GUI.

For my laptop, I'd have a heavy focus on speed and ease of use.  I don't want to have to pull up a terminal and debug/compile something while I'm sitting at the airport.

I think i will try setting up a live USB to try it on my laptop first.  (It doesnt have a CD drive)

Thanks
 i use a dell inspiron 1000 2.2 ghz with 512mb ram,40 gig hDD, it runs windows Xp and Kubuntu 8.10 installed with Wubi. The kubuntu side runs a lot faster that XP, to play DVD's you  may have to add the medibuntu repositories and install the dvd codecs

---

### Post by mkvnmtr on 2008-12-05
Just a word about your ram. I have Ubuntu and usually use Gnome desktop. I usually do just what you say you want to do. I run 2 or 3 browsers open and maybe a game. My normal ram usage is 250 MB more or less. I don't remember it being over about 350MB. I don't think I have ever used the swap on the hard drive. I take these figures form having Htop open for long periods watching cpu usage. Kbuntu shoul give you a speed increase just from ram usage. You can also find browsers that are light and faster than normal.I would make the change. But remember most of us on the forum really like linux. If you can back up yoour personal files on another drive you could probably give your self enough room to dual boot.

---

