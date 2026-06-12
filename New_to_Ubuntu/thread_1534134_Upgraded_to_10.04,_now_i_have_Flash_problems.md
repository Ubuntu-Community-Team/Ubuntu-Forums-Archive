---
title: "Upgraded to 10.04, now i have Flash problems"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by mastablasta on 2010-07-19
Ok, so i recently UPGRADED to Ubuntu 10.04 (32bit), because it's an LTS. And i switched the graphics card (an old ATI Rage 16 MB with Radeon 9800 XT). Computer is apparently an underclocked AMD (to 833Mhz) with 1.2 MB RAM.
Everything works nicely except for the flash. You tube used to work well before, however now it's jerky. and also pages with flash load really slow. i thought about installing  ATI driver however i see they only support Xorg until 7.4 (Ubuntu 9.10?!). But now i am thinking that maybe graphics drivers aren't the issue here. or are they?

Is there anything i can do about it or am i stuck with this kind of system? I planned to upgrade this computer with newer celeron and new motherboard. that's why i need to know, because if linux won't provide what i need it would be best for me to buy Win Home with the new motherboard.

---

### Post by Legendary_Bibo on 2010-07-19
Go to 

**System -> Administration -> Hardware Drivers**

wait for it to install the drivers.

See if that helps, if not I have other ideas in mind.

edit: sorry I only skimmed what you wrote. Anyways I would go ahead and install the drivers. They'll still work.

---

### Post by CaptainMark on 2010-07-19
it does sound like a graphics driver issue but its worth making sure you have the latest versions of the flash packages, i think its called flashplugin-installer now or something,

---

### Post by mastablasta on 2010-07-19
If i go under 
[B]System -> Administration -> Hardware Drivers 

it[/B] says no proprietary drivers are in use in this system. and that's it. it doesn't offer any drivers for graphics card.

i think i would have to download them from the site and then figure out how to install them. however i am a bit afraid in case it doesn't work because the site specifically says it only supports xorg until 7.4. while Lucid has it 7.5.

i iwll see if there is some option for that flash. because most other things seem to work (such as special effects (Which i turned off at the moment and GIMP is faster now). although i haven't tried any games yet.

Addition: flashplugin-installer is already installed.

---

### Post by cloyd on 2010-07-19
Two possible suggestions:
1. I you are using Mozilla try Chrome. Some say it helps. I found Chrome better for some things, but not necessarily for flash.  
2. If you want to use Mozilla, try this. This one really worked for me, though it is a bit irritating because it is always giving you the option to reinstall it . . . but it worked :
  	 	 	 	 	 	  [COLOR=#000080]_[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)_[/COLOR]
[U]

[/U]

---

### Post by lovinglinux on 2010-07-19
> **cloyd said:**
> This one really worked for me, though it is a bit irritating because it is always giving you the option to reinstall it . . . but it worked :
  	 	 	 	 	 	  [COLOR=#000080]_[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)_[/COLOR]

Please [get version 1.0.8 from my site](http://flash-aid-extension.blogspot.com)  Stable Channel. It fixes a problem, that affects only some 32bit users, in which flash is only removed and not installed back. Additionally, now it won't ask you to reinstall if you update from versions beyond 1.0.5 and has a new option to only remove flash if you need.

Mozilla hasn't reviewed it yet, because it was released today, but if you get it from my site it will continue to be updated with new versions as soon as Mozilla approves the latest version.

---

### Post by CaptainMark on 2010-07-19
not sure if thats a typo but is it a 16mb graphics card, your onboard graphics would be better no? i dont know a lot about graphics cards though

---

### Post by dv3500ea on 2010-07-19
As a work around, you could download the videos using a program called [abby]("apt:abby"). You can then watch them with a movie player. This should be a bit better because flash performance on linux generally sucks. This works for youtube and several other sites but not all sites.

---

### Post by Legendary_Bibo on 2010-07-19
> **dv3500ea said:**
> As a work around, you could download the videos using a program called [abby]("apt:abby"). You can then watch them with a movie player. This should be a bit better because flash performance on linux generally sucks. This works for youtube and several other sites but not all sites.

There's also minitube, but when I used it, it felt slow.

---

### Post by lovinglinux on 2010-07-19
> **Legendary_Bibo said:**
> There's also minitube, but when I used it, it felt slow.

There is also an extension that I develop that allows you to watch flash videos with other plugins, without the need to download the video. It replaces the flash video on site, allowing you to watch it with gecko-mediaplayer, gxine, kaffeine, mozplugger, totem and xine plugins. Currently it works with YouTube, Vimeo and Blip.tv, but I will be adding new sites soon.

[https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)
[http://flvideoreplacer-extension.blogspot.com](http://flvideoreplacer-extension.blogspot.com)

---

### Post by Legendary_Bibo on 2010-07-19
> **lovinglinux said:**
> There is also an extension that I develop that allows you to watch flash videos with other plugins, without the need to download the video. It replaces the flash video on site, allowing you to watch it with gecko-mediaplayer, gxine, kaffeine, mozplugger, totem and xine plugins. Currently it works with YouTube, Vimeo and Blip.tv, but I will be adding new sites soon.

[https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)
[http://flvideoreplacer-extension.blogspot.com](http://flvideoreplacer-extension.blogspot.com)

I use 64-bit flash, and whenever i watch a video it can make my system get quite hot. Does it fix this without a hindrance on the speed of watching a video? As long as it works with youtube I'm fine.

---

### Post by lovinglinux on 2010-07-19
> **Legendary_Bibo said:**
> I use 64-bit flash, and whenever i watch a video it can make my system get quite hot. Does it fix this without a hindrance on the speed of watching a video?

Yes. Additionally, some users that weren't able to watch HD videos on YouTube due to the lack of vdpau support can now watch them without problems.

> **Legendary_Bibo said:**
> As long as it works with youtube I'm fine.

Yes. It works on YouTube. Currently there is no support for featured channels, but single video pages opens just fine.

---

### Post by mastablasta on 2010-07-20
> **CaptainMark said:**
> not sure if thats a typo but is it a 16mb  graphics card, your onboard graphics would be better no? i dont know a  lot about graphics cards though

No it is not a typo. no onboard graphics here. I wrote it was an old 16 MB graphics card and it worked well. however i decided to switch it with another card i had lying arround that has 256 MB. and is actually not that old.

> **dv3500ea said:**
> As a work around, you could download the videos  using a program called [abby]("apt:abby"). You  can then watch them with a movie player. This should be a bit better  because flash performance on linux generally sucks. This works for  youtube and several other sites but not all sites.

That's for the idea, but it's not just videos that are causing problems. any site with even a little bit of flash loads slow.

> **lovinglinux said:**
> Please [get version 1.0.8 from my site]("http://flash-aid-extension.blogspot.com")  Stable Channel. It fixes a problem, that affects only some 32bit users, in which flash is only removed and not installed back. Additionally, now it won't ask you to reinstall if you update from versions beyond 1.0.5 and has a new option to only remove flash if you need.

Mozilla hasn't reviewed it yet, because it was released today, but if you get it from my site it will continue to be updated with new versions as soon as Mozilla approves the latest version.

Thank you for the suggestion. i think i iwll give it a try a bit later. 
at the moment i figured out using system monitor that processor seems to be the weak point as it goes up to 100%. i plan an upgrade of this maschine (hopefully components will be compatible with linux - they should be...)

I tried chromium, same issue. i then tried (but just you tube) to reduce the video quality and it was a bit better. So i plan to upgrade it with a newer celeron (i actually wanted an AMD but since they don't have many motherboards with AGP slot arorund here, choice is limited...) and a better motherboard. Then we will see if it all works better. if not i will just use your plugin and hopefully it will work.

BTW i noticed that   flashplugin-installer and also some flash has 64 next to the version. is that OK? shouldn't it be 32bit since i have 32bit OS system?

---

### Post by lovinglinux on 2010-07-20
> **mastablasta said:**
> Thank you for the suggestion. i think i iwll give it a try a bit later. at the moment i figured out using system monitor that processor seems to be the weak point as it goes up to 100%. i plan an upgrade of this maschine (hopefully components will be compatible with linux - they should be...)

Flash is a very CPU intensive plugin. If you have a single core CPU, there isn't much you can do. Take a look at my tutorial [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html).

My FlashVideoReplacer extension would definitely help in this case.

> **mastablasta said:**
> BTW i noticed that   flashplugin-installer and also some flash has 64 next to the version. is that OK? shouldn't it be 32bit since i have 32bit OS system?

It is 32bit. That 64 is just a coincidence, because is part of the flash version number. Most packages doesn't even contain any info regarding architecture, although you can find some with different names according to architecture, like w32codecs and w64codecs.

---

### Post by mastablasta on 2010-07-22
> **lovinglinux said:**
> Flash is a very CPU intensive plugin. If you have a single core CPU, there isn't much you can do. Take a look at my tutorial [Flash Optimization]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html").

My FlashVideoReplacer extension would definitely help in this case.


Thanks for the information. Yah it seems this processor (underclocked to 800Mhz is not good for flash videos (at least in Linux). In XP they run reasonably well with 256 MBram and 1.2 Ghz, but even there they can be a bit jerky. i know flash is not so optimised in Linux. I hitnk i will use your opitmization and hopefully new processor and new motherboard (that will actually use all AGP speed will do fine).

Single core processor is fine in WinXP (as long as there is enough RAM ...), so i am hoping it will also be ok in this computer, because i just ordered a 2,5Ghz Celeron (read the review and they say it's good value) as i am short on money and i couldn't find AMD socket motherboard here that would have AGP (the AGP card i have is not that old and works well, so i don't want to throw it away yet). I iwll also try with optimization...

---

### Post by CaptainMark on 2010-07-22
theres definatley no problem using a single core cpu, you only need dual or more for extremely cpu intensive tasks like encoding large videos and such. I dont think youll find a new amd board with agp connections, i had so much trouble that i bit the bullet and upgraded to pci and that was over a year ago, but i have a really bizzare cpu socket at the time.

---

### Post by mastablasta on 2010-07-25
Actually i found an interesting ASROCK motherboard. should arrive this week, cause they said there is stock. Now ASROCK makes them both intel and AMD. This one i only ofund intel version and surprisingly it has both AGP and PCIe for graphics card. It also has two slots for DDR (which i have on this old maschine) and also 2 slots for DDR2. It has SATA and enough IDE for older disks. So i am kind of looking forward to it. IT's not the latest trend motherboard, but i hope it will upgrade this computer to a nice working capacity. computer will be used for picture manipulation in GIMP and  mostly internet browsing and chatting. before i had plan to assemble a new one, but since i got this one for free and i am currently short on money i went for an upgrade. 

similary a notebook with not enough RAM for XP will get Lubuntu or Mint LXDE. I don't think flash will work good there, but i don't actually need it.

---

### Post by mastablasta on 2010-07-26
Problem solved - new mobo and better CPU - Flash works ok.

Now to get the sound wokring.

---

### Post by lovinglinux on 2010-07-26
> **mastablasta said:**
> Problem solved - new mobo and better CPU - Flash works ok.

Now to get the sound wokring.

Great news. Please create a new thread for the sound issues if you didn't already.

---

