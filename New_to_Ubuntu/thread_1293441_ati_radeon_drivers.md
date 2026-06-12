---
title: "ati radeon drivers"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by newtocade on 2009-10-17
can someone please give me some detailed instructions no how to install ati radeon drivers on ubuntu version 9.04 or give me a link to a site with good instructions...ive gone to ten different sites all with different instructions..one said something about rolling back to previos version...?

---

### Post by CaptainMark on 2009-10-17
the reason some people probably recommended going back to a intrepid is because jaunty/ati has given lots of problems, i had an ati card when jaunty was released. This site should be all you need [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

ps, if you dont know what xorg.conf is then i would read up on it first on google

---

### Post by newtocade on 2009-10-17
thanks...now does anyone know a good site for linux console commands i forgot how to navigate the console...been a while since i had my unix training class.

---

### Post by CaptainMark on 2009-10-17
that would be on this very forum [http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

---

### Post by 3rdalbum on 2009-10-17
Your card (ATI Radeon 8500) is not supported by ATI on Linux. ATI no longer makes Linux drivers for this card. There is an open-source driver for this card, that is operational by default.

Attempting to install any ATI driver on your system will result in you getting a blank screen on startup, so don't try it.

The HOWTOs you're referring to are for downgrading your version of Xorg so it is compatible with an old version of the ATI driver, that used to be able to run your card. You'd basically be ripping out a large portion of your system and replacing it with an old version. If I was doing it, I wouldn't feel confident of successfully doing it; and I've been using Ubuntu for years.

In short, if you can use your system for what you need it for, then don't mess with it! Otherwise, install a graphics card that is supported by the current official ATI or Nvidia graphics driver.

---

### Post by CaptainMark on 2009-10-17
Woah quit with the negative man, chillax. Worst case scenario get a copy of Ubuntu 8.04 and reinstall (after backing up your files of course) and your good for a while longer

---

### Post by newtocade on 2009-10-17
> **3rdalbum said:**
> Your card (ATI Radeon 8500) is not supported by ATI on Linux. ATI no longer makes Linux drivers for this card. There is an open-source driver for this card, that is operational by default.
 
Attempting to install any ATI driver on your system will result in you getting a blank screen on startup, so don't try it.
 
The HOWTOs you're referring to are for downgrading your version of Xorg so it is compatible with an old version of the ATI driver, that used to be able to run your card. You'd basically be ripping out a large portion of your system and replacing it with an old version. If I was doing it, I wouldn't feel confident of successfully doing it; and I've been using Ubuntu for years.
 
In short, if you can use your system for what you need it for, then don't mess with it! Otherwise, install a graphics card that is supported by the current official ATI or Nvidia graphics driver.
 
yup he was right even if hes negative...dont care though...had to reformat...will try to install earlier version of ubuntu (if available)...one that supports my card...agp cards are hard to get these days so getting a newer card or a diff card for this system isnt gonna happen...does anyone really know which version supports the ati Radeon 8500 card????

---

### Post by halitech on 2009-10-17
> **newtocade said:**
> yup he was right even if hes negative...dont care though...had to reformat...will try to install earlier version of ubuntu (if available)...one that supports my card...agp cards are hard to get these days so getting a newer card or a diff card for this system isnt gonna happen...does anyone really know which version supports the ati Radeon 8500 card????

AGP cards aren't really that hard to find

[http://www.tigerdirect.com/applications/Category/guidedSearch.asp?CatId=28&sel=Detail;55_158_2064_2064](http://www.tigerdirect.com/applications/Category/guidedSearch.asp?CatId=28&sel=Detail;55_158_2064_2064)

Finding an AGP card that's supported on the other hand...

Looking here 
[http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx](http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx)

it looks like you'd probably be looking at something around 6.06 that would be supported by the ATI driver and the file is also an rpm which means converting it with alien to get it to run.

---

### Post by 3rdalbum on 2009-10-17
PowerColour makes recent ATI cards in AGP versions. They've got at least one in the 3000 series, which is currently supported and should be supported for a while yet.

(I think they were making one in the 4000 series as well, but I'm not sure if that was a hoax or not)

---

### Post by newtocade on 2009-10-17
what about the linux drivers on the ati website? cant i just install that... and how do i install them
the site is:
[http://support.amd.com/us/gpudownload/Pages/linux-radeon-prer200.aspx?type=2.4.1&product=2.4.1.3.29&lang=English&rev=&ostype=Linux](http://support.amd.com/us/gpudownload/Pages/linux-radeon-prer200.aspx?type=2.4.1&product=2.4.1.3.29&lang=English&rev=&ostype=Linux) x86

---

### Post by 3rdalbum on 2009-10-17
> **newtocade said:**
> what about the linux drivers on the ati website? cant i just install that... and how do i install them
the site is:
[http://support.amd.com/us/gpudownload/Pages/linux-radeon-prer200.aspx?type=2.4.1&product=2.4.1.3.29&lang=English&rev=&ostype=Linux](http://support.amd.com/us/gpudownload/Pages/linux-radeon-prer200.aspx?type=2.4.1&product=2.4.1.3.29&lang=English&rev=&ostype=Linux) x86

Old drivers won't work with the new Xorg. New drivers work with the new Xorg, but don't work with your card.

The drivers you just linked to are three years old; that's ancient history in Linux.

---

### Post by newtocade on 2009-10-18
so you people are telling me that I'm screwed because theres no support for my graphics card... and i have to go buy a new card...jeez i thought ubuntu was supposed to be better than windows... open source and all that jazz hasn't somebody looked into this problem...they should let the old drivers work...I'm tired of looking at a flickering glitchy screen...at least my graphics card works in windows with catylist support...

---

### Post by iamgeniusrnti on 2009-10-18
> **3rdalbum said:**
> Your card (ATI Radeon 8500) is not supported by ATI on Linux. ATI no longer makes Linux drivers for this card. There is an open-source driver for this card, that is operational by default.
 
Attempting to install any ATI driver on your system will result in you getting a blank screen on startup, so don't try it.
 
The HOWTOs you're referring to are for downgrading your version of Xorg so it is compatible with an old version of the ATI driver, that used to be able to run your card. You'd basically be ripping out a large portion of your system and replacing it with an old version. If I was doing it, I wouldn't feel confident of successfully doing it; and I've been using Ubuntu for years.
 
In short, if you can use your system for what you need it for, then don't mess with it! Otherwise, install a graphics card that is supported by the current official ATI or Nvidia graphics driver.
 
YEP!  Found that out the hard way.  
 
I installed it a week ago for the first time in my entire life.  I thought it would be a great idea to install the ATI drivers since I used them for XP.  Installed and ran fine.  Then I rebooted and I got a black screen.  Took me about two days of searching until I stumbled upon someone else with ATI having the same issue and the commands to remove the drivers.
 
Phew!

---

### Post by 3rdalbum on 2009-10-18
> **newtocade said:**
> so you people are telling me that I'm screwed because theres no support for my graphics card...

No, nobody is telling you that.

We're telling you that the ATI Proprietary driver doesn't support your card anymore. There is an open-source driver that your system is already using. So there IS support for your graphics card - open-source support, straight from the Linux community.

If you want the benefits that the proprietary ATI driver has, then there are recent ATI cards that fit into AGP slots and work with the latest ATI proprietary driver.

> they should let the old drivers work...

ATI's drivers are closed-source. We can't modify the old ATI driver to work with the new Xorg, or modify the new ATI driver to support your card. What would you have us do?

If you don't like it, you should complain to ATI as they are the ones not supporting your card. We support your card. ATI doesn't. Be fair.

---

### Post by newtocade on 2009-10-18
[quote=3rdalbum;8122693]ATI's drivers are closed-source. We can't modify the old ATI driver to work with the new Xorg, or modify the new ATI driver to support your card. What would you have us do?
 
**how bout leaving elements of the old Xorg that supported the old drivers that work**...
just because drivers are old doesnt mean they dont work...not all of us can run right out and buy a new vid card to keep up with the updating monster...they should keep a few things that are a little backwards compatable...

---

### Post by 3rdalbum on 2009-10-18
> **newtocade said:**
> **how bout leaving elements of the old Xorg that supported the old drivers that work**...

It's not that simple, due to technical reasons that I'm not sure I can explain to a layperson. Xorg has its roots in 1980s code and it simply has to change and become more modern. It can't change if it has to maintain binary compatibility with what we were doing back in 2008. And there are big changes coming.

ATI dropped support for your card overnight, when a new release of Xorg was immanent. In other words, the changes had already been made with the assumption that ATI was going to keep supporting the old cards. You simply can't expect FLOSS developers to put in longer hours to support a binary-only proprietary driver that never really worked very well anyway. They don't get paid to work on that stuff. I mean, did Microsoft keep Windows XP's driver interface in Vista so it could keep supporting old devices? No, Microsoft didn't do that. It's not Microsoft's job and it's not the Xorg developers' job to pick up the pieces after a hardware manufacturer abandons its hardware.

I'll also point out that this would never have happened if ATI had open-sourced its old driver under the MIT license (or compatible). If that had happened, the Xorg developers would have either maintained the legacy driver forever, or would have used knowledge gained from it to build a better open-source driver.

In short, it's not our fault. If ATI dumps support for its hardware, then the open-source community will continue to support open-source drivers. But we're not about to maintain support for closed-source, binary drivers that simply cannot be maintained.

Your options are: Get a new card, settle for the open-source drivers that we support, downgrade to Ubuntu 8.10 or find a way to install the old version of Xorg on Ubuntu 9.04.

---

### Post by CaptainMark on 2009-10-18
Hey man id just reinstall ubuntu 8.04, your good until April 2011 with full support, after that you wont get any upgrades but you can still carry on using it long as you like.  
And dont say windows is better because you can use your card with it, XP is what 8 years old with ubuntu you only have to use a version thats 18 months old to get support, ati probaly havent made vista/windows7 drivers for your card just like ati havent made Jaunty 9.04 drivers for your card.  End of the day its ati you should be mad at, were only trying to help

---

### Post by newtocade on 2009-10-18
[quote=CaptainMark;8124753]Hey man id just reinstall ubuntu 8.04, your good until April 2011 
thats the only useful information ive gotten out of this whole forum...you people just tell me theirs no support and my videocard wont work and a whole big explanation on why it wont work with no solution...i dont care about "support"... i just want a working os...hell id revert back to win 98 because it works...you guys could have told me to use the older version of ubuntu in the fist place...and is it gona work?

---

### Post by CaptainMark on 2009-10-19
im pretty sure it should work fine because back ati made drivers for almost all their cards for ubuntu, here the wiki page for 8.04 [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) the best way to tell is to make a live cd and run it on your computor, if you get given the option to install restricted drivers, your all good. ill see if i can find a 8.04 download

---

### Post by CaptainMark on 2009-10-19
here we go, [http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/) youll want the PC X86 desktop, burn it as an image to a cd and boot from it to test it with your card.  If it deosnt work, i would be a bit stumped. Fingers crossed

---

