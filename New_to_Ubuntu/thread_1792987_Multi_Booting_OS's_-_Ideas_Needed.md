---
title: "Multi Booting OS's - Ideas Needed"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by jcyshin on 2011-06-28
Hi Guys,
 
New to Ubuntu, have big plans but not sure how to go about it, any ideas would be great.
 
Wanting to have mutil boot of Ubuntu, Android 3.0, Windows 7, Mac OS, Windows XP, and Oracle Solaris. Will also be learning how to build Android Apps and Apple Iphone Apps also :)
 
I have played around with VirtualBox and VMware but it seems slow, which has lead me to this crazy task of trying to multiboot this way. 
 
I am very new to Ubuntu so my apologies if I don't seem to know what I am talking about :popcorn:
 
Thank you everyone in advance and I will take all feedback on board and work hard.

---

### Post by haqking on 2011-06-28
> **jcyshin said:**
> Hi Guys,
 
New to Ubuntu, have big plans but not sure how to go about it, any ideas would be great.
 
Wanting to have mutil boot of Ubuntu, Android 3.0, Windows 7, Mac OS, Windows XP, and Oracle Solaris. Will also be learning how to build Android Apps and Apple Iphone Apps also :)
 
I have played around with VirtualBox and VMware but it seems slow, which has lead me to this crazy task of trying to multiboot this way. 
 
I am very new to Ubuntu so my apologies if I don't seem to know what I am talking about :popcorn:
 
Thank you everyone in advance and I will take all feedback on board and work hard.

Well seeing as you have posted in a Ubuntu forum, is that your main OS ?


I personally run all that you said under virtual box (though i dont run solaris) and they all run fine inlcuding mac osx

Speed and performance will come down to your hardware and how many VM's you have open at the same time (with multiboot you can only have one at a time ;-)

so it is a trade off ?

what aspect did you find slow ? and what is your hardware ?

---

### Post by jtarin on 2011-06-28
How many drives are you using and how big? Windows will be installed first, regardless the order of others. I recommend EasyBCD (in my signature) to boot all OS's.

---

### Post by SoFl W on 2011-06-28
Run them under Virtualbox, if you find you really like one or two of them, then go with the dual boot method.

---

### Post by jcyshin on 2011-06-28
> **haqking said:**
> Well seeing as you have posted in a Ubuntu forum, is that your main OS ?
 
 
I personally run all that you said under virtual box (though i dont run solaris) and they all run fine inlcuding mac osx
 
Speed and performance will come down to your hardware and how many VM's you have open at the same time (with multiboot you can only have one at a time ;-)
 
so it is a trade off ?
 
what aspect did you find slow ? and what is your hardware ?
 
I have been testing Virtual Box running Windows 7 alone, I am running an AMD Phenom II X4 965 BE, applying 2GB DD3 1600 out of the 4GB I have and still find it sluggish. If my hardware is the issue then I would need 8GB plus to do what I want lol, fortunately my Asus MB does support up to 16GB.

---

### Post by trizrK on 2011-06-28
> **jcyshin said:**
> I have been testing Virtual Box running Windows 7 alone, I am running an AMD Phenom II X4 965 BE, applying 2GB DD3 1600 out of the 4GB I have and still find it sluggish. If my hardware is the issue then I would need 8GB plus to do what I want lol, fortunately my Asus MB does support up to 16GB.
Find some hdd drives, install those then use each of them seperatly for each OS.

---

### Post by jcyshin on 2011-06-29
> **haqking said:**
> Well seeing as you have posted in a Ubuntu forum, is that your main OS ?
 
 
I personally run all that you said under virtual box (though i dont run solaris) and they all run fine inlcuding mac osx
 
Speed and performance will come down to your hardware and how many VM's you have open at the same time (with multiboot you can only have one at a time ;-)
 
so it is a trade off ?
 
what aspect did you find slow ? and what is your hardware ?
 
> **trizrK said:**
> Find some hdd drives, install those then use each of them seperatly for each OS.
 
I will be buying either a few SDD or a few raptors but still comes back down to multibooting or running VMware/VBox. 
 
What stats do you guys think I need to do what I want to do. ideas ideas lots of them please lol.

---

### Post by slooksterpsv on 2011-06-29
> **jcyshin said:**
> I will be buying either a few SDD or a few raptors but still comes back down to multibooting or running VMware/VBox. 
 
What stats do you guys think I need to do what I want to do. ideas ideas lots of them please lol.

Honestly I really think VirtualBox is the way to go - I use it to run other OSes, try out OSes, etc. It's not slow to me, maybe your AMD-V isn't enabled.

Anyways, if you really really really want to Dual-boot I suggestion considering if you really want Solaris or if you want OpenIndiana (which forked from OpenSolaris after Oracle started thrashing everything).

Mac OS X you technically can't run legally.

I'd do separate hard drives for your multi-boot. 1 drive dedicated to your main OS. The others, put 2-3 on another drive.

---

### Post by nzjethro on 2011-06-29
> **jcyshin said:**
>  
What stats do you guys think I need to do what I want to do. ideas ideas lots of them please lol.

In terms of computer resources, if you are dual-booting, the OSes aren't sharing resources, so you'll need only the specs to run the most resource intensive OS (not too sure, but I imagine it'll be 7). But in terms of drives, yes, get plenty. If you are worried about cost, but still want to use SSD, you could install one or two (or three at a stretch) of your main used OSes on there (I imagine with that many OSes you'll be using one on two a lot more than others), and then the rest on HDDs. It's more modular that way, plus you don't have to worry about running up against partition limits. Where possible (yes for Ubuntu, no for Windows, not sure about the rest), consider using extended and logical partitions, just becouse this will increase modularity.

I'm "quad-botting" at the moment, although 3 of the four boots are *buntu (Ubuntu 10.10, Ubuntu 11.10, Xubuntu 10.04, and Win 7) and that works fine on my HP dv5 (don't know the HDD specs but it's got 2GB of RAM, and about 2.1GHz clock speed) and it runs well. I've heard similar testimonials form *buntu/Windows/OSX multi-boot with my specs, but I'm not sure what would happen when you get into 6 OSes.

And fair enough wanting to go DB over VM, even with super specs VM is a bit iffy at times. Bu then, if you are planning on frequently switching OSes you may be a but gutted having to shutdown-boot each time.

---

### Post by cariboo on 2011-06-29
Also keep in mind that it is against Apples's EULA to install OSX on anything but Apple branded hardware, so if you run into problems, don't even think of asking for help here.

---

### Post by jcyshin on 2011-06-29
Hi Everyone thank you all for the great ideas, keep them coming, would love to hear all the expert opinions as I will be using Ubuntu as my main OS.
 
With regards to the Mac OS EULA issue, thank you to those who reminded me as it completely slipped my mind that Apple doesn't like anyone putting Mac OS on anything thats not a Mac. I do have a legal licenced Mac OS X as my Mac Pro just died, hence why I wanted to see if I should just put it in a PC :popcorn:
 
Still not too keen on VirtualBox itself, seems to me like I need a lot more RAM to do what I want to do for it not to become so sluggish to put me to sleep.
 
Ok main things I am keen on:
 
1) Ubuntu to be main OS
2) Android 3.0 OS to use as it looks cool and I am trying to build Android Apps
3) Need to figure out how to make Iphone Apps and what OS to do it in, hence trying everything
4) Windows 7 is more for gaming and Visual Studio, Uni work blah blah blah(if I can still do it without Windows 7 then thats fab.
5) need XP to run the bank apps my wife needs as Win 7 is kicking up a problem as the security patches needed won't work, not even on Ubuntu. It does however work ok XP.
 
Those are the main reasons for now. 
 
Keep the ideas coming, you guys are opening my eyes to a world of possibility.
 
Thank you thank you thank you:P

---

### Post by pjd99 on 2011-06-29
> **cariboo907 said:**
> Also keep in mind that it is against Apples's EULA to install OSX on anything but Apple branded hardware, so if you run into problems, don't even think of asking for help here.

Is that really an issue here? Do we need to make sure people have passed the WGA test before giving help on Windows issues? I'm pretty sure there will be more people on these forums violating Microsoft's EULA's than Apple's...


Back on topic, I'd go with the virtual machines. I've never noticed speed problems using VMWare player, on a Core 2 Duo (2.53 GHz, 6MiB cache) laptop with 4GiB ram. I only allocate a single core and 1 GiB RAM to my Windows XP and Ubuntu virtual machines. OK there's a small lie in there, if more than 2 VM's are open things slow down quite a bit.

Once made a LFS VM and allocated both cores and 2 GiB ram, and compiling time wasn't noticeably slower than on my native install (Maverick) at the time.

I dual boot Windows 7 for some games and work software (and the work software is only there as I had run out of space on my VM and needed it on the spot). Haven't yet tried 7 in a VM so have no comments on its performance inside one.

---

### Post by slooksterpsv on 2011-06-29
> **jcyshin said:**
> ...
3) Need to figure out how to make Iphone Apps and what OS to do it in, hence trying everything

...

Now this isn't directed at you, but this is how Apple works, they suck you in by saying that the only way to develop apps for their iOS devices is to own one, to fork out anywhere from $700+ for one of their computers to make programs for them.

I've been nice and polite for too long about things like that, but there is one reason I CAN'T stand Apple. Yet I can use Windows, Linux, or Mac OS X to develop Android Apps.

EDIT: I don't know about Windows phone, I take it I have to have Windows to do that, but it's easier to get a Windows machine than a Mac.

---

