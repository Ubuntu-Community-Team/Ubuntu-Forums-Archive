---
title: "Installing Windows 7 in a VM?"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by Arla on 2010-05-06
I've read a number of threads that point to running windows in a VM as an answer to having to use some piece of windows software or another.

I've done SOME googling but so far all the links for how to do this I'm finding seem to be the wrong way around (installing ubuntu in a VM within Windows) does anyone have any good links for the way round I want to go (ideally, I wouldn't, but there are some pieces of software that I have to use under windows, and they don't work under WINE).

Thanks

---

### Post by derande on 2010-05-06
i run windows xp (not win7) in virtualbox to run the audio editing software i need. also set up a shared folder between lucid and the win xp virtual OS and it works great.

if you install virtualbox and need usb access, DO NOT install the OSE edition as it does not allow for usb.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by KdotJ on 2010-05-06
I too run windows xp in a VM using VirtualBox. Runs really well and the shared folder is great. To the OP I would maybe suggest installing XP instead of Windows 7 if possible, purely because it will run better. I only assign my XP virtual machine 512mb of ram. Windows 7 will require more...

---

### Post by spydeyrch on 2010-05-06
> **Arla said:**
> I've read a number of threads that point to running windows in a VM as an answer to having to use some piece of windows software or another.

I've done SOME googling but so far all the links for how to do this I'm finding seem to be the wrong way around (installing ubuntu in a VM within Windows) does anyone have any good links for the way round I want to go (ideally, I wouldn't, but there are some pieces of software that I have to use under windows, and they don't work under WINE).

Thanks

Hey, I wrote a really simple guide a while back that I could post here if it will help. It is for setting up vista in a VM but the same applies for win7. Also, it is using vb (virtual box)

Let me know if you would like the guide and/or some help getting it up and running. Also, while we are on the subject, what are your machine's specs:

CPU
GPU
RAM
HDD
ODD
OS

For example, mine is:

AMD Phenom 9950 2.6GHz oc'd 3.2GHz
2 x ATI HD 3870 in crossfire
4GB DDR2 1066
1TB, 3 x 500GB
CD/DVD Burner
Win7 Pro x64
Mint 8 x32
Ubuntu 10.04 x64

Depending on what you have and what you want, the outcome could be different.

Let me know! :guitar:

-Spydey :lolflag:

---

### Post by cap10Ibraim on 2010-05-06
I installed windows 7 using Sun Virtual Box 
just follow simple instructions through a wizard and insert the windows 7 dvd the virtual machine will boot the dvd and you will be installing it as if it is another machine 
but with my laptop windows 7  runs somehow slow on VM

---

### Post by Arla on 2010-05-06
> **spydeyrch said:**
> Hey, I wrote a really simple guide a while back that I could post here if it will help. It is for setting up vista in a VM but the same applies for win7. Also, it is using vb (virtual box)

Let me know if you would like the guide and/or some help getting it up and running. Also, while we are on the subject, what are your machine's specs:



Would love to have the guide, since I'm totally new to the whole virtual machine thing, right this minute I dual boot, but it would be nice to not have to do that for the few times I need windows.

CPU: T4200 Pentium Dual Core (or somewhere around there)
GPU: Some sort of built in one, don't recall what
RAM: 2GB
HDD: 160GB
ODD: DVD Reader, not sure if it writes DVD's or not (never used it for that)
OS: Ubuntu 10.04

---

### Post by cap10Ibraim on 2010-05-06
> **Arla said:**
> I need windows.

CPU: T4200 Pentium Dual Core (or somewhere around there)
GPU: Some sort of built in one, don't recall what
RAM: 2GB
HDD: 160GB
ODD: DVD Reader, not sure if it writes DVD's or not (never used it for that)
OS: Ubuntu 10.04
If you really need windows 7 continue dual booting or install xp on the virtual box , I have 4 gb ram and 2 duo and windows 7 was slow on virtual machine 
so i went back to dual booting 
you may need some quad core cpu !

---

### Post by spydeyrch on 2010-05-06
> **Arla said:**
> Would love to have the guide, since I'm totally new to the whole virtual machine thing, right this minute I dual boot, but it would be nice to not have to do that for the few times I need windows.

CPU: T4200 Pentium Dual Core (or somewhere around there)
GPU: Some sort of built in one, don't recall what
RAM: 2GB
HDD: 160GB
ODD: DVD Reader, not sure if it writes DVD's or not (never used it for that)
OS: Ubuntu 10.04

Ok, so I am going to do some quick research on your hardware so that I can customize the guide, if needs be, to your hardware. Typically I don't need to. The most important thing is if your CPU has hardware virtualization. How do you want your system to be setup:

Host OS (Main OS): Ubuntu 10.04 or Windows 7 or XP
Guest OS (VM OS): Windows 7, XP, or Ubuntu

Also, are you running a x32 or x64 flavor of ubuntu? And do you have x32 or x64 or Win7 and/or XP?

Ok, I am going to start getting this thing posted. It will take me a little bit to get it up correctly. :KS

-Spydey :lolflag:

---

### Post by spydeyrch on 2010-05-06
> **cap10Ibraim said:**
> If you really need windows 7 continue dual booting or install xp on the virtual box , I have 4 gb ram and 2 duo and windows 7 was slow on virtual machine 
so i went back to dual booting 
you may need some quad core cpu !

Well, to some degree I would agree with you. But, I recently, like a year ago, took an old machine and ran a VM on it.  The machine was an old P4 2.8GHz HT, 1.5 GB DDR 400MHz, 100GB IDE HDD. It booted ubuntu 8.10, ran virtualbox, and ran an XP VM.

Granted it wasn't super fast, but with some tweaking and optimization, it ran acceptable for what was needed.

I would recommend that if you had to choose between win7 and xp, due to your hardware I would go with xp. If you are worried about virus infections with xp, there are some pretty cool and sneaky things that you can do to avoid all that stuff.

Just answer the questions from my previous post, of how you want your system setup, and we, meaning everyone here, will see what we can do. :p

-Spydey :lolflag:

---

### Post by spydeyrch on 2010-05-06
> **Arla said:**
> Would love to have the guide, since I'm totally new to the whole virtual machine thing, right this minute I dual boot, but it would be nice to not have to do that for the few times I need windows.

CPU: T4200 Pentium Dual Core (or somewhere around there)
GPU: Some sort of built in one, don't recall what
RAM: 2GB
HDD: 160GB
ODD: DVD Reader, not sure if it writes DVD's or not (never used it for that)
OS: Ubuntu 10.04

One more thing that I just thought of, VB currently doesn't have a version of VB out for ubuntu 10.04. They do have one for 9.10 but I am not sure if it will work the right way or not in/for 10.04. We will just have to test, right. And hope that it works!!! hahahaha [-o< 

-Spydey :lolflag:

---

### Post by QIII on 2010-05-06
I'm using the PEUL version of VirtualBox on Lucid without any problems.

---

### Post by OmegaBLK on 2010-05-06
The current beta version of Virtualbox, 3.2.0_BETA1, has Lucid debs.  Check here and remember that it is in beta still:  [http://download.virtualbox.org/virtualbox/3.2.0_BETA1/](http://download.virtualbox.org/virtualbox/3.2.0_BETA1/)

---

### Post by mbzn on 2010-05-06
I run 64bit ubuntu 9.10 with win7-64 in Sun v-box haven't really tested the speed but it seems fine. i allocated 1.2GiB ram to win7 on a duel-core.

---

### Post by spydeyrch on 2010-05-06
> **QIII said:**
> I'm using the PEUL version of VirtualBox on Lucid without any problems.

So you are using the PEUL version for 9.10 but in 10.04? Awesome, I just recently did a fresh install of 10.04, last night actually, and hadn't gotten to transferring/testing my VMs yet. Thanks for the heads up! :KS

-Spydey :lolflag:

---

### Post by cap10Ibraim on 2010-05-06
> **spydeyrch said:**
> One more thing that I just thought of, VB currently doesn't have a version of VB out for ubuntu 10.04. They do have one for 9.10 but I am not sure if it will work the right way or not in/for 10.04. We will just have to test, right. And hope that it works!!! hahahaha [-o< 

-Spydey :lolflag:

I tested it works fine and i am running xp on it

---

### Post by spydeyrch on 2010-05-06
> **Arla said:**
> Would love to have the guide, since I'm totally new to the whole virtual machine thing, right this minute I dual boot, but it would be nice to not have to do that for the few times I need windows.

CPU: T4200 Pentium Dual Core (or somewhere around there)
GPU: Some sort of built in one, don't recall what
RAM: 2GB
HDD: 160GB
ODD: DVD Reader, not sure if it writes DVD's or not (never used it for that)
OS: Ubuntu 10.04

Ok dude, so after doing some research on your CPU, [http://ark.intel.com/Product.aspx?id=37251](http://ark.intel.com/Product.aspx?id=37251), I have determined that it does not support virtualization. Now that doesn't mean that you won't be able to do it. VB has some special coding in it that can still do a VM but it uses a lot more resources than normal. Like I previously posted, I did a VM on a P4 before, and it worked fine, just not lightning fast.

So it is your call, if you want me to post the guide, I am more than willing to do so. I would just hate to have you go through it and then not have it be worth your while/time because the performance isn't what you need. Just my $0.02  :p

Let me know.

-Spydey :lolflag:

---

### Post by spydeyrch on 2010-05-06
> **cap10Ibraim said:**
> I tested it works fine and i am running xp on it
 
Awesome!! I am glad to hear that. Now I am just a little worried about the op's cpu, it doesn't support hardware virtualization. So if he/she does run a vm, it is going to use a lot more resources than if the cpu did support it. Still doable, but there will be performance penalties. :mad:

-Spydey :lolflag:

---

### Post by spydeyrch on 2010-05-06
Alright, I have finished editing my previously created vista guest based on windows 7 host guide. It is now for windows 7 guest with ubuntu host. hopefully everything is clear.

If you want to enable shared folders, let me know. If you want to enable a really cool way of virus protection, let me know. If you want to try something else, or have questions let us know. Have fun at it. I have 3 OSs and in each OS I have about 2 - 3 VMs. 

I need my flavors!! hehehehe):P

-Spydey :lolflag:

EDIT: I can't get it to upload, to big of a file. Even if I break it up into smaller chunks, I can't get it to fit. I think I am going to zip it. Give me a few moments. sorry about the delay. ;)

---

### Post by spydeyrch on 2010-05-06
Alright guys, I can't get it to compress to where the ubuntuforums will accept it, too big, even with zip compression.

Any other ideas on how to get it uploaded? There are screen shots (important) and so that is why it is such a large file, around 2.5 MB. I can't just upload the guide, via cut and paste, to the thread because the screen shots don't carry over correctly.

Any thoughts?

Sorry.

-Spydey :lolflag:

---

### Post by UnknownFear on 2010-05-06
> **cap10Ibraim said:**
> but with my laptop windows 7  runs somehow slow on VM

As with mine, so I just dual-boot Windows 7 along side Ubuntu 10,04, which I would strongly suggest the OP of doing. Windows 7 will run quite slow compared to Vista or XP in a VM environment.

---

### Post by Arla on 2010-05-06
So, your correct in your assumption, I want Lucid as the host and Windows 7 as the interloper, or guest, or whatever. I'll check the CPU tonight when I get home to make sure I got it right (that was from a Y450 laptop specs site that I found, which is what mine is).

I'm curious to try it, will obviously leave my dual-booting in for the time, it was just a curiosity from reading other posts.

Unfortunately I don't know many other ways to post your guide on here, perhaps stick it on a free FTP site and link to it here? (I have a google sites page for doing that kind of thing, although I've never really used it).

Or I can just start playing, I should be able to figure it out, just hadn't done much looking before now.

Finishing the questions, I'm using 32 bit Windows 7, and 32 bit Lucid right now (from a little reading 64 bit versions of both still, from what I read, seem to have some quirks that make it just not worth it for me to move onto 64 bit).

---

### Post by spydeyrch on 2010-05-06
@ Arla - I got your PM and sent you the guide via email.

For those of you that would like it too, I am working on getting it up in my public drop-box account and will link that here shortly. Until then, if you need/want it, post your request here and I will email it to you. PM your email to me so as not to share with everyone.  ;)

@Arla - Hope it works out for you.

-Spydey :lolflag:

---

### Post by Raithe on 2010-05-06
> **spydeyrch said:**
> One more thing that I just thought of, VB currently doesn't have a version of VB out for ubuntu 10.04. They do have one for 9.10 but I am not sure if it will work the right way or not in/for 10.04. We will just have to test, right. And hope that it works!!! hahahaha [-o< 

-Spydey :lolflag:

Sorry to butt in, I'm new both in this community and to the OS, but I set up Win7 (32bit) using the Karmic VB release.
I'm running the 64 bit version of Lucid 10.04, so I'm assuming there wont be any extra tricks to configuring 32bit if thats what you are running.

From a newbie to a newbie...

Once I had my image on a local drive, which took a while for this microsoft child, it was simply a case of making sure VB could find the image and it installed out of the box.
My only initial hurdles were the "no bootable media" errors.

Runs well, but I ended up giving it nearly 2 gigs of ram just to keep it nice and quick.

I might take the advice of the posters above me though, and just use XP for resource reasons.
I want to run my Adobe programs "natively" for production reasons, other than that, I'm happy /rooting around from here on in.

I've been a card carrying geek for a while, but it's time to achieve enlightenment...

E6850
8800 GTX
only 4 gigs RAM =(
Ubuntu 10.04 64bit

---

### Post by VastOne on 2010-05-07
> **Raithe said:**
> Sorry to butt in, I'm new both in this community and to the OS, but I set up Win7 (32bit) using the Karmic VB release.
I'm running the 64 bit version of Lucid 10.04, so I'm assuming there wont be any extra tricks to configuring 32bit if thats what you are running.

From a newbie to a newbie...

Once I had my image on a local drive, which took a while for this microsoft child, it was simply a case of making sure VB could find the image and it installed out of the box.
My only initial hurdles were the "no bootable media" errors.

Runs well, but I ended up giving it nearly 2 gigs of ram just to keep it nice and quick.

I might take the advice of the posters above me though, and just use XP for resource reasons.
I want to run my Adobe programs "natively" for production reasons, other than that, I'm happy /rooting around from here on in.

I've been a card carrying geek for a while, but it's time to achieve enlightenment...

E6850
8800 GTX
only 4 gigs RAM =(
Ubuntu 10.04 64bit

I run V-Box Win7 32 bit on my Lucid 64 bit perfectly.  I tried the 64 bit of Win7 and found it to be slow and cumbersome compared to the 32 bit.

---

### Post by KdotJ on 2010-05-07
Out of interest, how much ram do you allocate to the win7 guest? Does it run smoothly? I figured to install XP due to its lower system requirements. But I may give win7 a spin in a VM in this case...

---

### Post by spydeyrch on 2010-05-07
I would recommend that you partition just under half of your RAM for your VM. For Win7 you will want at least 1GB.

-Spydey :lolflag:

---

### Post by muteXe on 2010-05-07
I could never get my XP VM properly authenticated.
First time i installed it quite rightly asked me for authentification, which i successfully gave it (the dvd was the official MS one that came with the laptop in the first place), but every time i booted up again it would still want me to enter in those details. Weird.

---

### Post by KdotJ on 2010-05-07
Thanks, I have 4gb ram on my machine so I think I can spare it lol

---

### Post by VastOne on 2010-05-07
> **KdotJ said:**
> Thanks, I have 4gb ram on my machine so I think I can spare it lol

I would also tweak the video card ram as well.  I am not at home right now to check my settings but I know I bumped it up to perhaps double the default setting. I will get you info later on.

---

### Post by spydeyrch on 2010-05-07
> **VastOne said:**
> I would also tweak the video card ram as well.  I am not at home right now to check my settings but I know I bumped it up to perhaps double the default setting. I will get you info later on.

Yes, in the quick guide that I shared with the op, I mentioned both the RAM and VRAM. But they are very important. Thanks for mentioning it for others. :p

Anyone else want a copy of the quick guide?

Here is the link to my guide. Let me know if you can get to it and if it works. It is in a word 2003 format.

[Virtual Box Quick Guide - Ubuntu Host OS / Windows Guest OS]("http://dl.dropbox.com/u/6344305/Install%20VB%20ubuntu.doc")

-Spydey :lolflag:

---

### Post by VastOne on 2010-05-07
> **spydeyrch said:**
> Yes, in the quick guide that I shared with the op, I mentioned both the RAM and VRAM. But they are very important. Thanks for mentioning it for others. :p

Anyone else want a copy of the quick guide?

Here is the link to my guide. Let me know if you can get to it and if it works. It is in a word 2003 format.

[Virtual Box Quick Guide - Ubuntu Host OS / Windows Guest OS]("http://dl.dropbox.com/u/6344305/Install%20VB%20ubuntu.doc")

-Spydey :lolflag:

WOW  +101010101010101011

This should be a sticky in the [_[COLOR="Blue"]Virtualization Forum[/COLOR]_]("http://ubuntuforums.org/forumdisplay.php?f=308")

Extremely well written and informative...An easy guide and must have for V-Box users...

Well Done!  :guitar: :popcorn:

P.S.  Do you have a location that I could use in my sig to get this?

P.P.S  I see it above...Thanks

---

### Post by spydeyrch on 2010-05-07
> **VastOne said:**
> WOW  +101010101010101011

This should be a sticky in the [_[COLOR="Blue"]Virtualization Forum[/COLOR]_]("http://ubuntuforums.org/forumdisplay.php?f=308")

Extremely well written and informative...An easy guide and must have for V-Box users...

Well Done!  :guitar: :popcorn:

P.S.  Do you have a location that I could use in my sig to get this?

P.P.S  I see it above...Thanks

Wow, thanks a ton for the compliment. I was actually kind of worried that it wouldn't be very clear for a few reasons.

I put it together about 6 months ago for other people in a computer basics class that I was taking (pre-requisites for school, very informative but sloooooooowwwww class). They didn't want to install over their already existing system and it was required to use Vista Business.

I was running Windows 7 Pro x64. I put it together in like 45 mins so in my opinion it was very sloppy and not well organized.

So, the guide was written with win7 as host and vista as guest. So to change it over to ubuntu as host and windows 7/xp as guest was kind of just minor editing and simple notes. Plus I was being kind of lazy, hehehehehe, and didn't want to have to re-write it from scratch to be 100% accurate. But hey, if it works then great!

--------

But I am glad that it was clear and easy to use. Thanks a ton for the compliment. I appreciate it very much. Feel free to put it in your sig if you want. Share it, edit it, make suggestions, change it, what ever you would like. Have at it! ;)

If you guys have questions, suggestions, spelling mistakes, etc. let me know and I will try to update it.

-Spydey :lolflag:

---

### Post by flyfishingphil on 2010-05-10
> **spydeyrch said:**
> Hey, I wrote a really simple guide a while back that I could post here if it will help. It is for setting up vista in a VM but the same applies for win7. Also, it is using vb (virtual box)

Let me know if you would like the guide and/or some help getting it up and running. Also, while we are on the subject, what are your machine's specs:

CPU
GPU
RAM
HDD
ODD
OS

For example, mine is:

AMD Phenom 9950 2.6GHz oc'd 3.2GHz
2 x ATI HD 3870 in crossfire
4GB DDR2 1066
1TB, 3 x 500GB
CD/DVD Burner
Win7 Pro x64
Mint 8 x32
Ubuntu 10.04 x64

Depending on what you have and what you want, the outcome could be different.

Let me know! :guitar:

-Spydey :lolflag:
Toshiba Satellite L305, ACPI x86 based, Intel pentium Dual CPU T3400 @ 2.16 GHz, RAM 3.0GB, Disk Drive Hitachi HTS543225 224GB (156 free), DVD-CD Matshita DVD-Ram UJ880AS,
Where do I find the GPU info? What is it?
OS 10.04 Lucid Lynx

Have Sun VurtualBox installed. Version 3.1.6 r 59388 Best choice? Better choice?

Have Vista on dual boot. Should be on back up external hard drive. Only disks I have for Vista are the startups I cut as soon as I turned it on. Have lots of stuff I wouldn't need there. Noted on other psot. I did buy a copy of XP recently for grandson but installed 9.10 instead. I can get that cd and use XP in VBox. From what I've seen sounds better than Vista and I can add in just what I need.

---

### Post by spydeyrch on 2010-05-10
> **flyfishingphil said:**
> Toshiba Satellite L305, ACPI x86 based, Intel pentium Dual CPU T3400 @ 2.16 GHz, RAM 3.0GB, Disk Drive Hitachi HTS543225 224GB (156 free), DVD-CD Matshita DVD-Ram UJ880AS,
Where do I find the GPU info? What is it?
OS 10.04 Lucid Lynx

Have Sun VurtualBox installed. Version 3.1.6 r 59388 Best choice? Better choice?

Have Vista on dual boot. Should be on back up external hard drive. Only disks I have for Vista are the startups I cut as soon as I turned it on. Have lots of stuff I wouldn't need there.

Your GPU would be your Graphics Processing Unit, or in other words, your video card. :)

According to the info that I have found on your machine, your GPU is a Mobile Intel® Graphics Media Accelerator 4500M with 128MB-1342MB dynamically allocated shared graphics memory. Here are the remainder of the specs:

[http://www.toshibadirect.com/td/b2c/retail-product.jsp?poid=440042](http://www.toshibadirect.com/td/b2c/retail-product.jsp?poid=440042)

How did you get Virtual box installed? Did you do it via the repos, the terminal, or did you download the .deb package from the virtual box website and install it via that? I know that the latest version on the website is for 9.10 but I haven't had any issues with using it in ubuntu 10.04 and others in this thread have said that same thing. So I say go for it. :popcorn:

Hopefully that answers your questions. If you have more questions, feel free to ask them here.  :P

Oh, and one more thing. Your CPU doesn't have hardware support for virtualization. This doesn't mean that you cant do a VM, but just be aware that it will tax your system more than if you did have the hardware support for virtualization. Just and FYI.

Let me know if you have any questions.

-Spydey :guitar:

---

### Post by emoguitarist06 on 2010-05-10
Robbie hosts a tech show every tuesday @ [www.Category5.tv](www.Category5.tv)
he was featured in Ubuntu 9.10 example's folder
[http://www.category5.tv/show_notes/episode_116.php](http://www.category5.tv/show_notes/episode_116.php)
there's an episode of him install windows 7 in virtualbox

---

### Post by flyfishingphil on 2010-05-10
spydeyrch-


Actually mine is an L305-5933, not the S5945 shown on that page. Couple of differences when you look at the info:

5933     *  Intel® Pentium® Processor T3400
    * Genuine Windows Vista® Home Premium (SP1, 32-bit)
    * 3GB PC6400 DDR2 800MHz SDRAM
    * 250GB HDD (5400rpm)
5945    *  Intel® Pentium® Processor T3400
    * Genuine Windows Vista® Home Premium (SP1, 64-bit)
    * 4GB PC6400 DDR2 800MHz SDRAM
    * 160GB HDD (5400rpm)
3G vs 4G in RAM and 250 vs 160 in HD's


*How did you get Virtual box installed? Did you do it via the repos, the terminal, or did you download the .deb package from the virtual box website and install it via that? I know that the latest version on the website is for 9.10 but I haven't had any issues with using it in ubuntu 10.04 and others in this thread have said that same thing. So I say go for it.*

I think it was in the directions somewhere else and I got it thru a repository. (Mind getting cloudy with all of the time spent bouncing around in this.)

---

### Post by spydeyrch on 2010-05-10
> **flyfishingphil said:**
> Actually mine is an L305-5933, not the S5945 shown on that page. Couple of differences when you look at the info:

5933     *  Intel® Pentium® Processor T3400
    * Genuine Windows Vista® Home Premium (SP1, 32-bit)
    * 3GB PC6400 DDR2 800MHz SDRAM
    * 250GB HDD (5400rpm)
5945    *  Intel® Pentium® Processor T3400
    * Genuine Windows Vista® Home Premium (SP1, 64-bit)
    * 4GB PC6400 DDR2 800MHz SDRAM
    * 160GB HDD (5400rpm)
3G vs 4G in RAM and 250 vs 160 in HD's


Ok, thanks for the clarification. I wasn't aware that there were two different ones. :)

So, 3GB should still be fine. The main thing though is your CPU having/not having hardware support. It will still run on it but just don't expect it to run super fast. 

Take into account that I ran ubuntu 8.10 as a host and windows XP as guest (VM) with a P4 2.8GHz HT and 1.5GB DDR2 400MHz RAM. It took a while for the system (XP) to come up and I had to let it load everything. It was a little touchy in some instances but over all, with patience, it was fine for what was needed.

In your case, you have a dual core, not a single core, so you can dedicate a core to your XP-VM. Your CPU is a better architecture than a P4, more efficient. You have double the ram that I had in that particular case. Plus you will optimize the system if you decided to go this route.

I would say that you should be fine. :)

-Spydey :guitar:

---

### Post by spydeyrch on 2010-05-10
> **flyfishingphil said:**
> spydeyrch-

*How did you get Virtual box installed? Did you do it via the repos, the terminal, or did you download the .deb package from the virtual box website and install it via that? I know that the latest version on the website is for 9.10 but I haven't had any issues with using it in ubuntu 10.04 and others in this thread have said that same thing. So I say go for it.*

I think it was in the directions somewhere else and I got it thru a repository. (Mind getting cloudy with all of the time spent bouncing around in this.)

Yeah, I went back and read some of the first posts, it looks to me like you did it via the repos & cli.

-Spydey :guitar:

---

### Post by jack frost on 2010-05-10
If you have issues with sound, i saw some other post and you can download the realtek driver from here:

[http://www.realtek.com.tw/Downloads/downloadsCheck.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/Downloads/downloadsCheck.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false)

Not sure if this will work with everyone; but my Asus board has realtek so it worked for me.

running 10.4 64 host w/ win7pro64 guest in virtual box.

---

### Post by spydeyrch on 2010-05-11
> **jack frost said:**
> If you have issues with sound, i saw some other post and you can download the realtek driver from here:
 
[http://www.realtek.com.tw/Downloads/downloadsCheck.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/Downloads/downloadsCheck.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false)
 
Not sure if this will work with everyone; but my Asus board has realtek so it worked for me.
 
running 10.4 64 host w/ win7pro64 guest in virtual box.
 
 
Awesome! I am glad to see that you were able to get your sound working properly. I have an Asus board too but I don't remember if I needed to install any drivers or if it just work otb. Anywho, good job geting that to work.
 
Did ou take a look at the guide? What did you think of it? Should I add a part about audio, about shared folders? Any other ideas?
 
-Spydey :guitar:

---

### Post by VastOne on 2010-05-11
> **emoguitarist06 said:**
> Robbie hosts a tech show every tuesday @ [www.Category5.tv](www.Category5.tv)
he was featured in Ubuntu 9.10 example's folder
[http://www.category5.tv/show_notes/episode_116.php](http://www.category5.tv/show_notes/episode_116.php)
there's an episode of him install windows 7 in virtualbox

Thanks for this link...Although I have V-Box and WIn7 working perfectly, I checked out the link and I am very impressed with this method of instruction that is real time and very informative.  

I will be checking them out live the next time around. :guitar:

---

