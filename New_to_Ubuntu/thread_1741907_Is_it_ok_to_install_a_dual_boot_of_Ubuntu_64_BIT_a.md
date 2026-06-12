---
title: "Is it ok to install a dual boot of Ubuntu 64 BIT and Windows 7 32 BIT ?"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by Syotos on 2011-04-28
Just wondered if :

a) it's possible
b) gonna cause complications 


personally i dont think so cause they have nothing to do with each other but maybe im wrong.

---

### Post by roger_1960 on 2011-04-28
Hi

Should be OK so long as its a 64 bit machine.  As the OS's run separately (one or the other) it shouldn't cause problems.

---

### Post by Leppie on 2011-04-28
the difference in 64bit and 32bit is not going to cause issues.
what may cause issues, is the combination of win7 and ubuntu as ubuntu nowadays uses grub2 which writes into the extended mbr. some windows applications also write into this exact same area which may cause the corruption of grub2.

---

### Post by Syotos on 2011-04-28
> **Leppie said:**
> the difference in 64bit and 32bit is not going to cause issues.
what may cause issues, is the combination of win7 and ubuntu as ubuntu nowadays uses grub2 which writes into the extended mbr. some windows applications also write into this exact same area which may cause the corruption of grub2.

How likely is this to happen with windows 7 and what are the outcomes when this happens if ever ?
This is very upsetting...:(:confused:

What if it's a different type of windows?
If I intall XP or Vista. 

Will it cause the same issues ?

---

### Post by Leppie on 2011-04-28
> **Syotos said:**
> How likely is this to happen with windows 7 and what are the outcomes when this happens if ever ?
This is very upsetting...:(:confused:

What if it's a different type of windows?
If I intall XP or Vista. 

Will it cause the same issues ?
you may want to have a look at this page: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

i do not recall any people using xp complaining about this issue, but i may be wrong there.

a solution would be to use the windows boot loader instead of grub2, or install grub legacy.

---

### Post by Syotos on 2011-04-28
> **Leppie said:**
> you may want to have a look at this page: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

i do not recall any people using xp complaining about this issue, but i may be wrong there.

a solution would be to use the windows boot loader instead of grub2, or install grub legacy.

Thanks Leppie, so this is the solution and it works %100 ?

---

### Post by Blasphemist on 2011-04-28
I've had a dual boot just as you described running for a year or so. Win 7 was installed first and then ubuntu. I've done multiple ugrades of ubuntu without issue. I've done updates to windows but of course no upgrades.

---

### Post by Leppie on 2011-04-28
grub legacy is much smaller than grub2, so that should work out well.

---

### Post by Syotos on 2011-04-28
So which one should I install first and how much Space allocate for each of the OS's?

I have 250 gb.

Windows is mainly for games (not too many) and for stuff like Office and basically anything Linux can't do.

I will try to make Ubuntu my primary one.

---

### Post by Leppie on 2011-04-28
if you are going to install grub legacy, you could install any of the windows versions. just bear in mind that a higher version requires a considerable amount of more disk space. i believe that a bare windows 7 system uses about 15gb of space.
you could assign 80gb for windows, 80gb for linux and 85gb as repository for files you want to access in both windows and linux. this will leave you some space on the disk for the ubuntu swap partition as well.

---

### Post by Blasphemist on 2011-04-28
Install windows first and I recommend using half the drive or less. Here is a good link on the dual boot install of Ubuntu.

[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)

---

### Post by ianc1 on 2011-04-28
Not wishing to start an argument about this just wondering why Linux can't do "Office"?  I use MS Office at work (not by choice) and LibreOffice at home and have no issues.

---

### Post by Blasphemist on 2011-04-28
Not sure what you mean. As you say, ubuntu does include LibreOffice.

---

### Post by Leppie on 2011-04-28
there's both openoffice and libreoffice....

---

### Post by ianc1 on 2011-04-28
> **Blasphemist said:**
> Not sure what you mean. As you say, ubuntu does include LibreOffice.
What I meant was why can't Linux do office since it provides excellent tools for the job.  An earlier post suggested that Windows 7 was used for games and Office "things linux can't do".  I was merely trying to highlight that excellent alternatives to MS Office exist.  I agree I could have been clearer.

---

### Post by Syotos on 2011-04-28
> **ianc1 said:**
> What I meant was why can't Linux do office since it provides excellent tools for the job.  An earlier post suggested that Windows 7 was used for games and Office "things linux can't do".  I was merely trying to highlight that excellent alternatives to MS Office exist.  I agree I could have been clearer.

Maybe I am mistaken but doesn't the open office provides you with less features ? and I am not familiar with LibreOffice.

@Blasphemist thank you for the link, gonna check it out now.

---

### Post by Syotos on 2011-04-28
> **Leppie said:**
> if you are going to install grub legacy, you could install any of the windows versions. just bear in mind that a higher version requires a considerable amount of more disk space. i believe that a bare windows 7 system uses about 15gb of space.
you could assign 80gb for windows, 80gb for linux and 85gb as repository for files you want to access in both windows and linux. this will leave you some space on the disk for the ubuntu swap partition as well.

Maybe I didn't explain but I am pretty much a newbie. So when you are saying grub legacy, I am not really sure what you mean by it. What did you mean by: "if you are going to install grub legacy, you could install any of the windows versions. just bear in mind that a higher version requires a considerable amount of more disk space."
Also what did you mean by Swap Partition: " this will leave you some space on the disk for the ubuntu swap partition as well."

So 80 GB for Drive C for windows
Another 80 for Ubuntu OS
And devide the rest for a extra drive (non primary)

What's swap though. (So sorry for my ignorance):confused:

---

### Post by Blasphemist on 2011-04-28
I'm sure you could find some feature of MS Office that isn't in LibreOffice but very few users will find it won't do what they need. It is a quite full featured suite. You can use this link to drill down and get more information.

[http://www.libreoffice.org/features/](http://www.libreoffice.org/features/)

---

### Post by Syotos on 2011-04-28
> **Blasphemist said:**
> I'm sure you could find some feature of MS Office that isn't in LibreOffice but very few users will find it won't do what they need. It is a quite full featured suite. You can use this link to drill down and get more information.

[http://www.libreoffice.org/features/](http://www.libreoffice.org/features/)

Wow this looks much cleaner than MS Office, looks like it's more user friendly and nothing essential is missing. You have made your point :)

BTW still waiting for a reply to my question above you, kinda confused.

---

### Post by bodhi.zazen on 2011-04-28
> **Syotos said:**
> Just wondered if :

a) it's possible
b) gonna cause complications 


personally i dont think so cause they have nothing to do with each other but maybe im wrong.

Friends don't let friends boot Windows :twisted:

Other then that , I do not see any problem with your dual booting habits.

---

### Post by Syotos on 2011-04-28
> **bodhi.zazen said:**
> Friends don't let friends boot Windows :twisted:

Other then that , I do not see any problem with your dual booting habits.

LOL, If I had the knowledge the pro's have here, I would be more than happy to tell windows to F*** Off... I just don't know how to use ubuntu too well so the transition has to be moderate.

---

### Post by quesadilla on 2011-04-28
just another option if you cant get dual boot to work... just install one and make the other as a virtual machine, depending on how mush you plan on using each operating system

---

### Post by Blasphemist on 2011-04-28
> Maybe I didn't explain but I am pretty much a newbie. So when you are saying grub legacy, I am not really sure what you mean by it. What did you mean by: "if you are going to install grub legacy, you could install any of the windows versions. just bear in mind that a higher version requires a considerable amount of more disk space."
Also what did you mean by Swap Partition: " this will leave you some space on the disk for the ubuntu swap partition as well."

The link I'm including here is the best I have on preparing a system and includes much on partitioning. A swap file is for swapping memory to the hard disc when needed. I only notice it being used when importing a large number of pictures into Shotwell and maybe a couple other things. It is also used to hibernate the computer. So it should be a little larger than the amount of memory you have.

Users that have been around long enough have experience with Grub legacy but Grub 2 is what Ubuntu uses now, and has for a while though I'm not sure just how long. As I understand Ubuntu started using Grub 2 when it was still buggy and some people still prefer it. You have to go through grief above me to use it so I don't recommend you worry about it.

Herman's site is full of good information and links. It may take some study but it is worth looking into this for your questions. I'm including the page I recommend you start with but go to his home page for the site as you need.

[http://members.iinet.net.au/~herman546/p17.html#Preparation_For_The_Install_](http://members.iinet.net.au/~herman546/p17.html#Preparation_For_The_Install_)

---

### Post by Syotos on 2011-04-28
> **Blasphemist said:**
> The link I'm including here is the best I have on preparing a system and includes much on partitioning. A swap file is for swapping memory to the hard disc when needed. I only notice it being used when importing a large number of pictures into Shotwell and maybe a couple other things. It is also used to hibernate the computer. So it should be a little larger than the amount of memory you have.

Users that have been around long enough have experience with Grub legacy but Grub 2 is what Ubuntu uses now, and has for a while though I'm not sure just how long. As I understand Ubuntu started using Grub 2 when it was still buggy and some people still prefer it. You have to go through grief above me to use it so I don't recommend you worry about it.

Herman's site is full of good information and links. It may take some study but it is worth looking into this for your questions. I'm including the page I recommend you start with but go to his home page for the site as you need.

[http://members.iinet.net.au/~herman546/p17.html#Preparation_For_The_Install_](http://members.iinet.net.au/~herman546/p17.html#Preparation_For_The_Install_)

Amazing, I honestly don't know how to show my appreciation to everyone who invested their time to help me, each of you is what truly makes Ubuntu.

I LOVE LINUX.

---

### Post by Syotos on 2011-04-28
> **quesadilla said:**
> just another option if you cant get dual boot to work... just install one and make the other as a virtual machine, depending on how mush you plan on using each operating system

I thought about it and VM just not going to do it for me right now.
Thanks, quesadilla.

---

### Post by bodhi.zazen on 2011-04-28
> **Syotos said:**
> LOL, If I had the knowledge the pro's have here, I would be more than happy to tell windows to F*** Off... I just don't know how to use ubuntu too well so the transition has to be moderate.

There is nothing wrong with dual booting and many people dual boot as they transition. My guess is that it takes 2-6 months to transition, sort of depends on how much you use Ubuntu.

One day you wake up and realize you have not booted Windows for 6 months.

---

### Post by Frogs Hair on 2011-04-28
I dual boot with Win 7 32 bit and Ubuntu 64 bit with no problems and I have some games also . I may not be using the next version of Windows unless need to . I have to interact with work and school websites and Firefox currently won't work with those sites for other than viewing . User Agent Switcher simply doesn't work.

---

### Post by Timmer1240 on 2011-04-28
For a year I had Ubuntu XP and Win 7 triple booted I never had a problem with it I rarely ever booted either Windows.Now Im just running Mint Debian the whole disk Xp in a virtual machine.

---

### Post by Syotos on 2011-04-28
> **Timmer1240 said:**
> For a year I had Ubuntu XP and Win 7 triple booted I never had a problem with it I rarely ever booted either Windows.Now Im just running Mint Debian the whole disk Xp in a virtual machine.

So all of you who say you never had problems dual or even triple booting, did you use any tutorial that was supplied here by other users so you wont "mess up the grub" or "install it properly" ? or you all just installed it regularly ?

---

### Post by Blasphemist on 2011-04-28
I never chose manual options and didn't know to think about grub. And never had an issue with grub2.

---

### Post by BertN45 on 2011-04-28
I would just install  install Ubuntu after you have installed Windows 7.  The programs mentioned in the articles are special programs used to restore your disk (or part thereof) to the factory settings. You do not have to worry about any of the normal applications used in windows 7.

All versions of GRUB will have the same problem. The chances that it will effect you are only smaller with the legacy GRUB version.

I have done the dual install many times with XP, Vista and Win 7 and and never had any problem. I never used the recovery disk of Dell, since I did not like their factory settings.

---

### Post by Syotos on 2011-04-29
> **BertN45 said:**
> I would just install  install Ubuntu after you have installed Windows 7.  The programs mentioned in the articles are special programs used to restore your disk (or part thereof) to the factory settings. You do not have to worry about any of the normal applications used in windows 7.

All versions of GRUB will have the same problem. The chances that it will effect you are only smaller with the legacy GRUB version.

I have done the dual install many times with XP, Vista and Win 7 and and never had any problem. I never used the recovery disk of Dell, since I did not like their factory settings.

Haha good to know. But I still wonder what kind of problems, what will I experience if there are issues with the grub..?

---

### Post by Erlander on 2011-04-29
I have been dual booting Ubuntu and Win 7 for 6 months now.  Have just updated from Ubuntu 10.10 to 11.04 (about 3 weeks ago with a beta copy).  Prior to that I have been dual booting since 2006.  No problems experienced.

If Windows is installed first then the Ubuntu install goes well and provides the GRUB menu for both operating systems.

---

### Post by Syotos on 2011-04-29
I am OFFICIALLY using Ubuntu now !!!
This message is typed proudly on Ubuntu 11.04!

LOVE IT bye bye Windows.

Everyone here has taught me so much i love this community, soon i will be able to contribute too! :guitar:

---

