---
title: "Trying to run Ubuntu on my old Sony Vaio Laptop"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Sam The Bam 4 on 2009-01-27
Hi Fellas
Ok I'm new here however I have a problem that I wonder if you guys could help us out with.  I've downloaded and burned the latest version of Ubuntu (8.10 I Think it is now) and I try to boot it up on my old Sony Vaio Laptop, however I can't boot the Live CD version cause I think my laptop's either too old or it's DVD drive is a bit weak or something.

  However I can install the alternative install disk fine although Ubuntu runs incredably slowly on my setup.  Here is my Vaio's spec.

800MHz Mobile AMD Duron Processor
128MB RAM
15GB Hitachi Hard drive
Mobility ATI Rage Fury 8MB 3D Graphics card
DVD-ROM drive
Stereo Sound Card
2 USB(I think they're only version 1.1)ports, LAN, AUDIO, PARALELL port,floppy drive, PC Card slot,etc etc

Sorry I don't know the computers main chipset but I was lead to believe that Ubuntu should run fine with this config according to the bare minimum specs required by the OS, i know that 128MB of RAM might be the cause of the slowdown but I don't have money to upgrade it's memory right now, though the Ubuntu Documentation says the OS should get running on 64MB Ram, but Can anyone suggest anything I can do to improve performance or suggest why the Live CD has errors when I try to boot it?  

  Any Help would be much appreciated.
Cheers
Sam The Bam

---

### Post by snowpine on 2009-01-27
Hi Sam, I would not recommend Ubuntu on an old computer with only 128mb of ram. Something like Puppy Linux would be a much better choice--check it out!

---

### Post by LowSky on 2009-01-27
you dont have enough RAM. Ubuntu reccomends 384 MB

> 
[https://help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")
Recommended minimum requirements
Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly. 

700 MHz x86 processor 
384 MB of system memory (RAM) 
8 GB of disk space 
Graphics card capable of 1024x768 resolution 
Sound card 

A network or Internet connection 


---

### Post by boof1988 on 2009-01-27
You will get much better performance (at least the performance will be acceptable) if you use a lighter distribution.  Maybe DamnSmallLinux, PuppyLinux or the like.

You may be able to run Ubuntu on your system... but as you've noticed... it will go at a snails pace.

Would you consider a lighter distribution?

---

### Post by LowSky on 2009-01-27
Ubuntu will run on 64MB of ram but it need to be tweeked a bit to even attempt such a thing
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

---

### Post by snowpine on 2009-01-27
> **LowSky said:**
> Ubuntu will run on 64MB of ram but it need to be tweeked a bit to even attempt such a thing
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

Do you realize that guide is from 2005, for Ubuntu Warty?

---

### Post by TJCIB on 2009-01-27
if you MUST stick with the Ubuntu family, you will want to install Xubuntu.  It is lighter.  It may work.

However in light of the other posters who are hitting "reply" at the same time...

I would also recommend Puppy Linux.  Not only does it bark at you when you start up, but it will fly on your computer with yet have the same functionality.

I run Puppy Linux on a system with 64 MB of RAM flawlessly.  You can also download stripped down versions of Puppy and then install only the packages you want.  It makes for an even faster experience...

---

### Post by boof1988 on 2009-01-27
> **LowSky said:**
> Ubuntu will run on 64MB of ram but it need to be tweeked a bit to even attempt such a thing
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

Thanks for the link.

---

### Post by TJCIB on 2009-01-27
From the Xubuntu Website
> System Requirements

Xubuntu is available for PC, 64-Bit PC.

CDs require 128MB RAM to run, or 192MB RAM to install. Desktop install requires at least 1.5GB of free space on your hard disk. 

Sorry, looks like Puppy is your best bet.  I find it more friendly than Damn Small Linux....I mean...it's a puppy...it's your best friend...

---

### Post by snowpine on 2009-01-27
Of course Xubuntu will run on the OP's computer, since its requirements are lower than Ubuntu (and Ubuntu works). However, if Ubuntu is incredibly slow, Xubuntu will be incredibly slow as well, since Ubuntu and Xubuntu share the same core system.

You definitely need to go outside the Ubuntu family here if reasonably fast performance is a concern. Puppy is my #1 recommendation for you. It won't be super-fast, but it should be usable.

---

### Post by roger_1960 on 2009-01-27
Hi

Another vote for puppy linux - 128Mb isn't enough for Ubuntu or Xubuntu (might run, but horribly slow)

---

### Post by Sam The Bam 4 on 2009-01-27
> **snowpine said:**
> Of course Xubuntu will run on the OP's computer, since its requirements are lower than Ubuntu (and Ubuntu works). However, if Ubuntu is incredibly slow, Xubuntu will be incredibly slow as well, since Ubuntu and Xubuntu share the same core system.

You definitely need to go outside the Ubuntu family here if reasonably fast performance is a concern. Puppy is my #1 recommendation for you. It won't be super-fast, but it should be usable.Cherrs for the heads-up fellas.

The only thing that's concerning me over other distro's is thier lack of y'know completeness, OS's like Ubuntu etc feel more complete and widely supported by lots of people, take Ubuntu it has Firefox, Open Office and A near professional like feel to it with installing apps etc easy and the OS generally easy to use, it has nearly the best of all the open-source apps already as part of the OS itself.

  Something confuses me though, how comes Windows XP runs fine on my Vaio yet an OS like Ubuntu which appears to be similar in erms of interface etc and doesn;t look like its that demanding of your system needs more processing power?  Why is 256MB of RAM needed to run what is talked up to be a lightweight OS? after all isn't Linux meant to be good for older machines?

  I understand that was a very generalised statment as not all distro's are the same in terms of thier use, but you'd think such a well known and most supported one like Ubuntu that anyone who's a beginner is recommended to start with, would be more scaleable than it is so's the maximum number of folk could try it.  Oh well seems not eh?

---

### Post by snowpine on 2009-01-27
> **Sam The Bam 4 said:**
> Cherrs for the heads-up fellas.

The only thing that's concerning me over other distro's is thier lack of y'know completeness, OS's like Ubuntu etc feel more complete and widely supported by lots of people, take Ubuntu it has Firefox, Open Office and A near professional like feel to it with installing apps etc easy and the OS generally easy to use, it has nearly the best of all the open-source apps already as part of the OS itself.

  Something confuses me though, how comes Windows XP runs fine on my Vaio yet an OS like Ubuntu which appears to be similar in erms of interface etc and doesn;t look like its that demanding of your system needs more processing power?  Why is 256MB of RAM needed to run what is talked up to be a lightweight OS? after all isn't Linux meant to be good for older machines?

  I understand that was a very generalised statment as not all distro's are the same in terms of thier use, but you'd think such a well known and most supported one like Ubuntu that anyone who's a beginner is recommended to start with, would be more scaleable than it is so's the maximum number of folk could try it.  Oh well seems not eh?

You have to remember that Windows XP is an 8-year-old operating system. The average home/business computer had very different specs back then compared with today. Try walking into Best Buy and buying a computer with less than 512mb of ram, for example. That was high-end when XP first came out.

Many of the things you love about Ubuntu (great software applications, easy to configure, user friendly, etc) are also demanding on the system. As a result, Ubuntu is near the top end of Linux distros in terms of its system requirements. Its developers have made it pretty clear where their priorities lie, in my opinion, and they must being doing something right, as it is currently the #1 distro in the world. They are actively marketing themselves as a modern, full-feature competitor to Vista and OSX in the home and workplace, not so much the low-end, semi-obsolete hardware market. :)

I have tried many Linux distros that claim to be "lightweight versions of Ubuntu" such as Xubuntu, Fluxbuntu, Crunchbang, etc. None of them come even close to "specialized" mini-distros like Puppy, DSL, or SliTaz in the "lightweight" department...

---

### Post by LowSky on 2009-01-27
Windows XP started to be developed in 1999 to run on the current systems availible.

Ubuntu and the many parts that make it up, including Gnome, Firefox, OpenOffice, and so on,  were developed to run on mid to low-end equiptment around 2004 when the first releases were being distrubuted. Unlike WinXP, Ubuntu has been being upgraded every 6 months with new applications and system abilities while XP didn't upgrade much for 8 years, and when Vista came out MS couldn't get rid of XP support because too many people wouldn't switch as there systems weren't really ready, now 7 is coming and people still are not sure to switch.

I will note that while Vista is a hog compared to Ubuntu, Windows 7 is much more streamlined and runs much smoother. So windows might have a leg up on Ubuntu in  a year or so... but its anyones game.

Canonical is trying to build a quicker booting version of Ubuntu by taking out some processes that have been added over the years that many users may not need or use at all. But in the end Time will tell.

---

### Post by TJCIB on 2009-01-27
And you can add OpenOffice AND Firefox to Puppy Linux.  But it will slow down your system the more you have.

That is what the deal with Ubuntu is, if you pile on lots of PROGRAMS that take resources, your OS will take resources.
Puppy can easily be everything you need.  And their package installation program is pretty simple to use.

I asked all these same questions when trying to revive an old Win98 computer: "why can I run powerpoint in windows 98, but I can't run OpenOffice Impress?"  Answer: The version I had was more than a decade old, where as Open Office is a little newer than that.

You can't expect cutting edge performance on obsolete hardware.  But you can get full functionality.  Try puppy...it's even easier to try than Ubuntu.  It's less than 100MB to download, you'll be playing in less than an hour.

---

### Post by Sam The Bam 4 on 2009-01-27
> **TJCIB said:**
> And you can add OpenOffice AND Firefox to Puppy Linux.  But it will slow down your system the more you have.

That is what the deal with Ubuntu is, if you pile on lots of PROGRAMS that take resources, your OS will take resources.
Puppy can easily be everything you need.  And their package installation program is pretty simple to use.

I asked all these same questions when trying to revive an old Win98 computer: "why can I run powerpoint in windows 98, but I can't run OpenOffice Impress?"  Answer: The version I had was more than a decade old, where as Open Office is a little newer than that.

You can't expect cutting edge performance on obsolete hardware.  But you can get full functionality.  Try puppy...it's even easier to try than Ubuntu.  It's less than 100MB to download, you'll be playing in less than an hour.Cheers I'm doing it right now, although I live in the UK with a 2Mb/s internet connection and the server looks like it's running on a 56k modem, download tops out at about 49kb/s or so, and I'm still waiting on it to finish. I'll get it up and running and tell you what I think.

Yes this laptop's nuts and bolts are obsolete and I can respect that XP was made 8 years ago at a time when the average PC had far inferior hardware to today but whats the myth floating about that Linux is meant to be lightweight and more suitable for older hardware when most distro's are lookin to newer tech eh?  bit misleading there I think. 

 Oh! BTW can you add Firefox to the OS? just wondering cause I'm really just looking to make this old retired beast a productivity and general web surfer so that it's getting used and not just lying about, I am thinking about pluggin in my Netgear USB wireless-g stick so's I can connect to the internet, although if I can't find drivers for it (which I probably won't) ,I'll just use the ethernet port round the back.
Cheers
Sam The Bam

---

### Post by sports fan Matt on 2009-01-27
What is really odd is my father's old hp with 192mb ram hasnt bluescreened once while my lenovo with 3 gigs did every single week..explain that

---

