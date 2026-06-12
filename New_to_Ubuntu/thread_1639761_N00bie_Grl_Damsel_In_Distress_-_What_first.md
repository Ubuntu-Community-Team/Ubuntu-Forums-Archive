---
title: "N00bie Grl Damsel In Distress - What first?"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by yellowchi on 2010-12-07
Okay here goes:

I have a computer, an old HP 1140n.

It had XP Media Center on it but it died, and I couldn't find the install CD (plus I don't want to use Windows anymore).

So my question is, what do I do first?

Keep in mind, I am not only a Linux n00b, I'm even a Windows n00b. Actually, a computer idiot. But I learn fast.

So................

1. **Do I have to do anything to my hard drive before installing?**
2. How do I find out what drivers I'm going to need and if they're available (for sound, etc.) when I don't have access to the OS anymore.
3. I am currently using Cable internet. How can get make sure I can get online with it. Does my ethernet need a driver? (I assume so)
4. Are there other Linux OS's that are cool besides Ubuntu?
5. Is there software to run Windows programs in Linux?


I also have 5 other computers and among everyone I know, I would like to convince them all to use Linux. 

:popcorn:

---

### Post by julio_cortez on 2010-12-07
> **yellowchi said:**
> 1. **Do I have to do anything to my hard drive before installing?**Usually you may want to backup old data, so maybe you can try booting Ubuntu from a Live CD and backup the data (the ones that were on the Windows partition and that you think were important) on an USB disk.

> **yellowchi said:**
> 2. How do I find out what drivers I'm going to need and if they're  available (for sound, etc.) when I don't have access to the OS anymore.Usually Ubuntu recognizes all the hardware with no problem. Maybe you'll struggle a bit with wireless, but it isn't said.

> **yellowchi said:**
> 3. I am currently using Cable internet. How can get make sure I can get  online with it. Does my ethernet need a driver? (I assume so)And this makes my sentence about wireless useless. :)
Ethernet drivers are usually loaded with no problem when you install Ubuntu. How do you conenct to Internet? Via a router (always on) or via a modem? Might need a little bit of information more on this.

> **yellowchi said:**
> 4. Are there other Linux OS's that are cool besides Ubuntu?It depends on what you like most. Kubuntu is more similar (in look adn feel) to Windows, even if it's still Ubuntu. Debian is way more stable, and so on..

> **yellowchi said:**
> 5. Is there software to run Windows programs in Linux?[WINE]("http://www.winehq.org/")!!
Though I must warn you that not everything runs perfectly in WINE :)

Other than that, please consider **I'm not *that* experienced yet** so maybe I won't be of total help, but be confident that there will be people that will help you further ;)

---

### Post by potat on 2010-12-07
> 
1. Do I have to do anything to my hard drive before installing?
2. How do I find out what drivers I'm going to need and if they're available (for sound, etc.) when I don't have access to the OS anymore.
3. I am currently using Cable internet. How can get make sure I can get online with it. Does my ethernet need a driver? (I assume so)
4. Are there other Linux OS's that are cool besides Ubuntu?
5. Is there software to run Windows programs in Linux?


Short answers:
1. No. The Ubuntu installer can handle formatting your hard drive (as long as you are planning on having it be the only operating system on your computer).

2. You don't need to install drivers in Linux because most drivers are included in the kernel. This basically means that if the driver is available, the device will work out of the box. There are some exceptions to this (wireless cards and video cards can be problematic) but all the basics should work.

3.Assuming you are connected via Ethernet, Ubuntu's NetworkManager should handle it automagically. Ethernet should work out of the box.

4. There certainly are. Ubuntu is almost definitely the best distribution for jumping into Linux.

5. There is. Once you have installed Ubuntu, you can go to the "Software Center" to add and remove programs. A program called Wine is what you're looking for. It doesn't work perfectly with every program (especially games, multimedia, etc.) but basic programs will work. winehq.org has more information about individual programs.

EDIT:
This document, though a little verbose, might help you during the install process.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

And the more general documentation for once you get started:
[https://help.ubuntu.com/10.10/index.html](https://help.ubuntu.com/10.10/index.html)

---

### Post by mcduck on 2010-12-07
1. Do I have to do anything to my hard drive before installing?

No, the installer will handle everything for you.

2. How do I find out what drivers I'm going to need and if they're available (for sound, etc.) when I don't have access to the OS anymore.

Most likely all the drivers are included already, no need to do anything.

Anyway, the Ubuntu CD allows you to try Ubuntu without any changes to your computer. That should allow you to check that everything works before you do the install.

3. I am currently using Cable internet. How can get make sure I can get online with it. Does my ethernet need a driver? (I assume so)
If have external cable modem and connect to it thorough Ethernet, then as long as your network card works you should have no troubles getting online. And lie I said above, most likely the drivers for the network card are already included and everything will just work.

4. Are there other Linux OS's that are cool besides Ubuntu?

All of them? Depends on what you want. :D

5. Is there software to run Windows programs in Linux?

Wine. Although it's not a perfect solution, some stuff works, some doesn't. If you have a specific application in mind check the WineHQ website, they have a list of programs that are know to work (or fail).

Of course there's always the option of running Windows inside a virtual machine, at least if you have a reasonably powerful computer.

If you plan on playing lots of Windows games, though, you'd better off with a dual-bot setup.

---

### Post by Megaptera on 2010-12-07
Have you got Ubuntu on a live CD? If so boot from it and use the option to try Ubuntu (not install at this stage).
Bear in mind it'll run slow on CD not like it will when you finally install. Once running in "try" mode, test internet connection, sound, etc & see if it works.

What are the system specs for your machine? I think Ubuntu 10.04 and 10.10 need 512mb RAM.

Backup all your docs, photos, vids etc to external media - you can do this while running live CD. Install will wipe all off your hard drive.

Some Windows progs will run under Wine. [http://www.winehq.org/](http://www.winehq.org/)  but there are Ubuntu/linux alternatives to most of what you'll need.

Other linux ... well there are loads to choose from. Often sugested for those starting with linux along with Ubuntu is Mint which is Ubuntu plus some extras and a different menu/appearance: [http://www.linuxmint.com/](http://www.linuxmint.com/)

or PinguyOS which is Ubuntu plus some extras and a different menu/appearance: [http://pinguy-os.sourceforge.net/](http://pinguy-os.sourceforge.net/)

Hope some of that info helps?

---

### Post by NightwishFan on 2010-12-07
Hello and welcome to Ubuntu and the forums! I will answer your questions and give you a few links to read. I would offer more help but I am going to catch some Z's. :)


> 1. Do I have to do anything to my hard drive before installing?
No, if you do not have data you want to keep, Ubuntu can simply write the whole drive on its own. Here is more about installing:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
> 2. How do I find out what drivers I'm going to need and if they're available (for sound, etc.) when I don't have access to the OS anymore.
I would say 90% of drivers are actually built into Ubuntu with no need to search for them. You can actually "try" Ubuntu before you install right from the CD. Here is where you can download:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Here is how to burn a live cd (which also includes the installer.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
> 3. I am currently using Cable internet. How can get make sure I can get online with it. Does my ethernet need a driver? (I assume so)
I have never had an ethernet card that did not work. If your internet is already set up (was working before), just plug and go. :)
> 4. Are there other Linux OS's that are cool besides Ubuntu?
Plenty, though the user experience is generally the same. If I were to recommend one it would be Ubuntu. Though Fedora and OpenSUSE are nice as well. Some people swear by the Ubuntu variant Linux Mint. Here is a good reference:
[http://distrowatch.com/dwres.php?resource=major](http://distrowatch.com/dwres.php?resource=major)
> 5. Is there software to run Windows programs in Linux?
Technically two ways. Some software works using a utility called Wine, and you can also run a Windows installation in a "fake" or "virtual" machine. Though to be honest if you are willing to try Linux I would advise you do your best to not rely on Windows applications. It is hard to find a program that does not have a free and better alternative available in Ubuntu. Both are actually included as one click installs in the Ubuntu Software Center.

Wine FAQ: [http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)
Virtualbox: [http://www.virtualbox.org/](http://www.virtualbox.org/)

Also here are some other links you might like (I highly recommend the Ubuntu Manual even if you choose another distribution):
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
[http://askubuntu.com/](http://askubuntu.com/)
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

The point is to have fun and feel free to ask questions on here and askubuntu.com!

---

### Post by mastablasta on 2010-12-07
LOL so many posts.
 
ok here is just somethign that wasn't said. you mentiuoned you are iwndows newbie. when you install ubuntu (unless you plan to dual boot - two systems on same computer) you will format the drive during install. this will erase any data you have.
 
the easiest way to test computer compatibility is to donwload the Ubuntu CD, burn it to a CD disk and then boot the ocmputer from this CD. then you can select try it out and this will start up the system via CD (it won't make any changes on disk). note that it iwll run much slower than actual install you will do later on.
 
when in a live session you can try it out. see if you like it and also backup your files (copy them to another computer etc.).
 
the rest was already said. i would just like to add that there are plenty good alternatives to windows programmes. sometimes they have different names, but some are very similar to their windows "relatives".
there are also some linux versions of windows programmes (for example Skype, Adobe Flash...).  
 
Hope you enjoy the experience and the speed. 
 
You can also see the Ubuntu manual (though instalation part is a bit different in latest 10.10 version).

---

### Post by owiknowi on 2010-12-07
If you want to take a look at other brands of Linux:
[http://distrowatch.com](http://distrowatch.com)

But Ubuntu is truly a very good start to learn how to use Linux.
It runs on almost every PC to my knowledge.

And: keep asking!

---

### Post by Ustonkey on 2010-12-07
> **owiknowi said:**
> If you want to take a look at other brands of Linux:
[http://distrowatch.com](http://distrowatch.com)

But Ubuntu is truly a very good start to learn how to use Linux.
It runs on almost every PC to my knowledge.

And: keep asking!
One thing that all replies seem to forget is to ensure your first Boot in your BIOS is from your CD/DVD. I'm a NOObie and no one told me that was required, causing me lots of problems. Perhaps one of the above GURUS can advise you of this.
 Stonkey

---

### Post by rvchari on 2010-12-07
you have got lots of answers and i dont have to add any, i started as new bie for linux way back say in 1998... with erstwhile redhat 5.2 (non gui)... i am not a programmer nor do i have a background in programming. i am an OS freak and i can only say that ubuntu seems to be the most user friendly linux distro and i didnt find any difficulty in installation or hardware config. its a breeze and it detected my wireless automatically....

dont worry, this forum has lots of techies and experts to guide you thru and help u spread ubuntu .....

happy ubuntuing ... !!!

---

### Post by julio_cortez on 2010-12-07
> **Ustonkey said:**
> One thing that all replies seem to forget is to ensure your first Boot in your BIOS is from your CD/DVD.
Nice find.
I overlooked it as now it's quite always set like that by default (at the extent that I had to manually change the boot order to have my HD on top and gain a couple of seconds during boot time) :)

---

### Post by yellowchi on 2010-12-07
@julio_cortez

The first system is a bare system. It has no data on it. So what would be the next step?
I do have a router on my other computer, which I imagine I will eventually migrate to Linux also. But this computer uses an ethernet connection to the router. Do you think there will be a conflict with a Linux computer accessing my router? My router is a Linksys Wireless G. The Wireless G router is currently on my Vista Machine with a Modem. I am currently using Comcast (although that may change eventually).
How is Kubuntu still Ubuntu? Is it just a version with software and the look was skinned? What's the similarities and differences?
I read Debian is not compatible with Ubuntu. Are there OS's in Linux that are compatible and/or can share packages/software?
Which version is best for kids?
How is Debian more stable?
Can you give me any examples of things that do not work perfectly in WINE?

@potat

Are there any wireless cards or videocards that do not have a workaround that I should be aware of? My HP video card (I think) is on board on that PC. I'm not 100% sure what the video card does. :(
How do you feel about the 2 other distributions mentioned by Julio (a) Kubuntu (b) Debian
What multimedia are you aware of that may be popular but problematic?
I went to winehq but I don't see where it has a list of compatible programs and incompatible programs.

@mcduck

What are some other OS's besides Ubuntu for Linux? Are there more besides the ones mentioned by Julio (Kubuntu and Debian)?
I'm attempting to NOT use anything from Microsoft or most big companies (Apple, Adobe, etc.)
However, some stuff I know I might need Windows. How do you run Windows inside a virtual machine? Is that better than having 2 operating systems?

@Megaptera

The specs of the machine are here:
[http://h10025.www1.hp.com/ewfrf/wc/documentSubCategory?tmp_rule=6039&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&os=228&product=483895&sw_lang=](http://h10025.www1.hp.com/ewfrf/wc/documentSubCategory?tmp_rule=6039&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&os=228&product=483895&sw_lang=)

It has 2GB Ram right now. I could upgrade no problem. It is old though.

You say there are alternatives to most of what I'll need. I did have 1 odd question. Is there any way to run iTunes in Wine? That's the only 1 I think that might be important because my kids buy music from there.

---

### Post by julio_cortez on 2010-12-07
> **yellowchi said:**
> The first system is a bare system. It has no data on it. So what would be the next step?
So if you don't have to backup anything, just insert the Ubuntu CD and you'll be probably ready to install it (by choosing "Install Ubuntu 10.10" when asked).
Then you can happily use the whole drive for your Ubuntu :)
*There's a far chance that the default boot device of your PC is still the HD (like ustonkey pointed out), but I suggest you to think about it only if booting with the CD doesn't work.*

> **yellowchi said:**
> Do you think there will be a conflict with a  Linux computer accessing my router?Not really. Most likely you will plug the LAN cable in and enjoy the Internet.
I guess you have DHCP enabled on the router, so you'll most likely get an IP address automatically. *If not, sorry but I don't know that router so maybe someone more expert will help* ;)

> **yellowchi said:**
> How is Kubuntu still Ubuntu? Is it just a version with software and the  look was skinned? What's the similarities and differences?
Kubuntu is Ubuntu, indeed. It has only a different windows manager (which is responsible of the look and feel of the OS). Ubuntu uses [Gnome]("http://www.gnome.org/"), Kubuntu uses [KDE]("http://www.kde.org/").

About various distros, well, Ubuntu is based on Debian but it's more user-friendly from my point of view. A perfect point to start from if you ask me.
If you are looking for something more specific for the kids, maybe [Edubuntu]("http://www.edubuntu.org/about") is the choice for you.
About Debian, well, for "more stable" I mean that the packages that ship with Debian have been quite "proven" rock-solid and undergo a smaller amount of changes/updates during their lifetime, but also Debian is usually less updated than Ubuntu. In any case if this is your first Linux experience I'd suggest you to use Ubuntu :)

About WINE, well.. You may want to have a look at WINE's [appdb]("http://appdb.winehq.org/"). Keep in mind that some games don't run on WINE, as long as for example SonicStage (if you have a SONY mp3 player) and, to some extent, the latest Adobe products like CS5.

---

### Post by 3rdalbum on 2010-12-07
Yellowchi, the Ubuntu CD runs "live" - so Ubuntu runs from the CD as a trial, and then you can install it. The live session will let you see what hardware works and what the main features are. Don't worry about anything until you have tried the CD.

---

### Post by mcduck on 2010-12-07
> **yellowchi said:**
> 
@mcduck

What are some other OS's besides Ubuntu for Linux? Are there more besides the ones mentioned by Julio (Kubuntu and Debian)?
I'm attempting to NOT use anything from Microsoft or most big companies (Apple, Adobe, etc.)
However, some stuff I know I might need Windows. How do you run Windows inside a virtual machine? Is that better than having 2 operating systems?

Well, there are thousands, if not tens of thousands, of different Linux distributions, some made for desktop use, some for servers, some for beginners, some for experienced users, and some made for specific purposes like to serve as a media center or to run on you iPod or wireless router.

Take a look at [http://distrowatch.com/]("http://distrowatch.com/"), they have a pretty good list (of course excluding very specific Linux builds used on consumer electronics, industrial purposes and such) 

Anyway, you have already picked the right distribution to start with. :)

What comes to virtualization versus dual booting, virtualization allows you to run the Windows apps from inside Ubuntu, without having to reboot your computer to switch between the operating systems. On the other hand, running a virtual machine is slower and some stuff that requires direct access to the computer's hardware, like games requiring 3D acceleration, will not usually work.

If I had a Windows program I'd need to run I'd first check if it works with Wine, if not then I'd try a virtual machine (more complicated and not as good performance). And if even that doesn't work reasonably well (or if it's a game or some program that really needs all the computing power I can give to it) I'd dual boot with Windows.

Anyway, which one is best solution really just depends on what you prefer. (same goes with the different Linux distributions, by the way).

---

### Post by mastablasta on 2010-12-07
> **yellowchi said:**
> @julio_cortez
 
The first system is a bare system. It has no data on it. So what would be the next step?
Dowload CD, burn the iSO (as per instruciton) on CD and then put it in the computer. then set in BIOS (the thing that boots before your OS) to boot from CD first. it difficult to give exact instructions as each computer has a bit different bios and also keys that need to be pressed to get into it. in newer ones you can change only boot order without actually going to BIOS.
 
 
> 
I do have a router on my other computer, which I imagine I will eventually migrate to Linux also. But this computer uses an ethernet connection to the router. Do you think there will be a conflict with a Linux computer accessing my router? 

Router (the maschine) most likely uses Linux to run anyway :-) you don't have to make any changes.
 
> 
How is Kubuntu still Ubuntu? Is it just a version with software and the look was skinned? What's the similarities and differences?

Kubuntu is Ubutnu that uses KDE environment. Xubuntu uses Xfce (that needs less resources), normal Ubuntu uses GNOME. What this affects is basically how windows are drawn on your screen. and also some other things. Kubuntu looks a bit more like windows on first glance, but is still very different.
 
both use more or less same commands from terminal. Linux is what lies under the hood, while desktop environment is what you see and where you give commands to the maschine.
 
> 
I read Debian is not compatible with Ubuntu. Are there OS's in Linux that are compatible and/or can share packages/software?

All that are based on ubuntu. it is compatible, just not so easy to make things work... Even instalation is a bit more difficult.
There are some other distributions that are based on Ubuntu (such as Linux Mint). They are quite compatible.
 
> 
Which version is best for kids?

Go with Ubuntu or Mint. Remember if you boot form CD you can simply just try the system without doing any install at all.
 
> 
How is Debian more stable?

They do a lot more testing (a year or so) before they release it. to fix the bugs and polish it all. Ubuntu just adds new features and doesn't test as much. but releases are more far appart and usually they have older software as a result. but still a very good distribution especially for servers. Ubuntu LTS (Long term support version - current is Ubuntu 10.04) is also considered to be more stable. 
> 
Can you give me any examples of things that do not work perfectly in WINE?
 
Games that use Directx11, STEAM (i think certain games at least from it), Photoshop (certain versions), Microsoft MSN (the messanger) etc.
> 
@potat
 
Are there any wireless cards or videocards that do not have a workaround that I should be aware of? My HP video card (I think) is on board on that PC. I'm not 100% sure what the video card does. :(
Yes some have issues. Just try it with live CD to see if it works or not. video card makes it possible for computer to display things on your screen/monitor.
 
> 
How do you feel about the 2 other distributions mentioned by Julio (a) Kubuntu (b) Debian

They are both good. Just a bit different. I tried them all with live CD before deciding to go Ubuntu. It just seemed more intuitive to me as a newbie.
> 
What multimedia are you aware of that may be popular but problematic?

Multimedia? it all works appart from occasioanl webcam and TV cards (Not video cards).
> 
I went to winehq but I don't see where it has a list of compatible programs and incompatible programs.

 
Here you go: [http://appdb.winehq.org/](http://appdb.winehq.org/)
 
 
> 
@mcduck
 
What are some other OS's besides Ubuntu for Linux? Are there more besides the ones mentioned by Julio (Kubuntu and Debian)?

Ubuntu is a distribution of Linux. Distrowatch (link given before) will show other distributions. Ubuntu is porbably one of the simples ones for us beginners out there.
> 
I'm attempting to NOT use anything from Microsoft or most big companies (Apple, Adobe, etc.)
However, some stuff I know I might need Windows. How do you run Windows inside a virtual machine? Is that better than having 2 operating systems?

It's not better as it needs more memorry and porcessing power to run. You install windows in a virtual box. or you can use Wine. 
> 
@Megaptera
 
The specs of the machine are here:
[http://h10025.www1.hp.com/ewfrf/wc/documentSubCategory?tmp_rule=6039&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&os=228&product=483895&sw_lang=](http://h10025.www1.hp.com/ewfrf/wc/documentSubCategory?tmp_rule=6039&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&os=228&product=483895&sw_lang=)
 
It has 2GB Ram right now. I could upgrade no problem. It is old though.

 
Uf with 2GB it will fly!!! I run it on 256MB (=0.25GB) and it runs ok. On another maschine i have 1.3GB ram and runs really fast. 
 
> 
You say there are alternatives to most of what I'll need. I did have 1 odd question. Is there any way to run iTunes in Wine? That's the only 1 I think that might be important because my kids buy music from there.
 
I dont' run them, but i read on forums that they indeed can be run in Wine. this info is for version 10 but i just read 11 work much better: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=21302](http://appdb.winehq.org/objectManager.php?sClass=version&iId=21302)
 
EDIT: actually version 7 is the most ocmpatible it seems.

---

### Post by migs73 on 2010-12-07
I think someone will have to add to the sticky 'Suggestions on how to get your support questions answered as quickly as possible' that putting 'Damsel In Distress' in your title is as good as anything.

:lol:

---

### Post by surfer on 2010-12-07
> **migs73 said:**
> i think someone will have to add to the sticky 'suggestions on how to get your support questions answered as quickly as possible' that putting 'damsel in distress' in your title is as good as anything.

:lol:

+1

---

### Post by julio_cortez on 2010-12-07
> **migs73 said:**
> I think someone will have to add to the sticky 'Suggestions on how to get your support questions answered as quickly as possible' that putting 'Damsel In Distress' in your title is as good as anything.

:lol:Yeah, I'm considering adding a female avatar instead of this damn turntable and.. ermmm.. maybe having my name changed in [Julia]("http://www.linuxmint.com/") would be a little too much and create a little confusion, don't you think?

---

### Post by NightwishFan on 2010-12-07
I do not discriminate.  :)

---

### Post by Megaptera on 2010-12-07
I thought it said "Damson" and that picqued my curiosity!!

---

### Post by potat on 2010-12-07
> **yellowchi said:**
> 
@potat

Are there any wireless cards or videocards that do not have a workaround that I should be aware of? My HP video card (I think) is on board on that PC. I'm not 100% sure what the video card does. :(
How do you feel about the 2 other distributions mentioned by Julio (a) Kubuntu (b) Debian
What multimedia are you aware of that may be popular but problematic?
I went to winehq but I don't see where it has a list of compatible programs and incompatible programs.


First of all, I agree with the other posters on this matter: If you are installing from an Ubuntu CD (which you should be), select "Try Ubuntu without installing". You will get a working OS, and you can also try connecting to a wireless network at this point to see if the card works out of the box. It probably will.

- If your wireless card doesn't work, there are tons of threads on this forum that can help, and the fixes are generally straightforward. Just do a search for your card's make and model.
(Hint: even if wireless doesn't work, worry about this after you have your system up and running)

- The video card, in the sense I'm talking about, is the part of the video card that does graphics processing to speed up video and games and such (called hardware acceleration). Your monitor and everything will work out of the box.
If you are concerned about faster graphics, there is a quick way to find out whether they work out of the box (I suggest doing this after a the full install, though). Go to the Main Menu > Preferences > Appearance, click Visual Effects, and select Extra. If it works, you are good to go. If not, ask for help on the forums.

- Once you have Ubuntu, you can easily try out Kubuntu. The only difference is in the desktop environment (Ubuntu uses GNOME, Kubuntu uses KDE). It's a matter of installing KDE and selecting it when you login.
Debian is the OS upon which Ubuntu is based. It is similar but considered more stable, though also more difficult to configure. I suggest learning your way around Ubuntu first.

-By multimedia I am mostly talking about playing videos, which can be affected by whether you have hardware acceleration. See above.

- As for WineHQ, try the "AppDB" link. [http://appdb.winehq.org/]("http://appdb.winehq.org")

---

