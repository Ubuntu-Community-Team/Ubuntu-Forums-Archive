---
title: "Why Ubuntu?"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by Nanix on 2008-12-06
I have read a ton of stuff about Linux and Ubuntu and I am a fairly advanced computer user (technically advanced but not an under the hood know it all. In other words i don't discuss the advantages and disadvantages of hardrive formats over coffee). 

My interest in Linux comes from my need to customize everything perfectly to me and I know that Linux is good with that. However I dont understand what all the fuss is about Ubuntu and variations and why I would care to choose Ubuntu.

I have come to the conclusion that Ubuntu is basically Debian with a few conveniently added packages. Ubuntu's variations are simply Ubuntu with a different UI and maybe a few added packages in addition to whats already included. The first thing i would do after installation would probably be uninstalling almost all the applications and then finding my own. 

So if Ubuntu is only what I have concluded, and i am going to uninstall most of those packages, why would I install Ubuntu in the first place? Is there another distro of Linux that is bare bones and ready to be injected with my own ideas? Is package installation hard or something? Why dont people just do it on there own? and why couldnt I, if I wanted KDE as opposed to GNOME, not just replace it myself? why would I download a whole variation? and Why not just get Debian and install from there in the first place?

Please tell me if there is some unseen dimension to this whole thing.:KS

---

### Post by rev0lv3r on 2008-12-06
Ubuntu for me is better because it's updated a bit more often, it has polish, and it has great beginner oriented forums.

Debian is badass, I would use Debian if it weren't for Ubuntu. I love apt-get.

I think Fedora 10 is awesome, and I do like that Red Hat contributes back to the community more, but I'm sure Canonical is doing their best :)

---

### Post by OutOfReach on 2008-12-06
Ubuntu is meant to be easy to use for the average computer user. If you are looking for a distro you can build up try something like Arch Linux.

---

### Post by ugm6hr on 2008-12-06
If you've never used Linux before, I'd suggest you start with something pre-configured (like Ubuntu).

If you are just looking to customise the **look** of your OS, that is easily done.

The things to consider when choosing a Linux base:

The community / forum
Bleeding edge technology vs stability
Packaging system (e.g. apt vs rpm vs emerge)
6-month upgrade cycle, or continuously updated
Commercial support (if required)

Whether you choose a pre-configured desktop with applications, or custom pick your own is up to you, and can be done with any base.

An Ubuntu Minimal install CD is available if you want to configure everything yourself

But be aware, there is a good reason why Ubuntu has a reputation for being easy - most things just work.  If you just want to customise the look of the desktop / OS, that's easily done on top of the standard install (as is adding / removing applications).

---

### Post by jediborger on 2008-12-06
You are right that the variations of Ubuntu are all just different package selections. Ubuntu's relationship to Debian is that Debian provides the base package set and the Ubuntu devs just polish up some aspects to make it easier for the average person to use.

Now you sound pretty competent, if you want to get absolutely bare bones I would go for Linux from Scratch. This is more so a manual on how to build your own linux distro than really a distro, but they test out the versions that their manual specifies to make sure they work. If you don't want to compile everything yourself and like using Ubuntu/Debian packages you can just install a commandline version of Ubuntu and then add exactly what you want. I know this is an option from the alternate cd and it might be on the desktop cd as well. But basically this option will just install the bare bones components required to boot the computer and add more stuff to it, so there will be no graphical environment and you are left to add everything yourself. The nice thing about this approach is that the Ubuntu and Debian packages come with default working preset configurations so at least you will have a working setup once you install the package, then you can tweak the config files yourself.

So to answer your first question I prefer Ubuntu because of the many options you have although they might not be that obvious at first. Hopefully that answers your question.

---

### Post by Nanix on 2008-12-06
First of all: WOW! you guys are helpful!

Major question- stability? what exactly is stability? If I did LFS would that be significantly less stable than Ubuntu or other mainstream distros? Is Debian, since it's "badass" and the core of Ubuntu, more stable than Ubuntu? or is Ubuntu made to be more stable than its parent Debian?

and ugm6hr what do you mean by "most things just work"? Does Debian have more compatibility issues? Would LFS be be really picky and not fun to work with (and would I personally have to be working on it?)

---

### Post by binbash on 2008-12-06
> **Nanix said:**
> First of all: WOW! you guys are helpful!

Major question- stability? what exactly is stability? If I did LFS would that be significantly less stable than Ubuntu or other mainstream distros? Is Debian, since it's "badass" and the core of Ubuntu, more stable than Ubuntu? or is Ubuntu made to be more stable than its parent Debian?

and ugm6hr what do you mean by "most things just work"? Does Debian have more compatibility issues? Would LFS be be really picky and not fun to work with (and would I personally have to be working on it?)

First of all : 

If you never used linux or a little,it does not matter how advanced user(computer) you are, dont try lfs, gentoo or archlinux.


Instead of asking distro differences , in my opinion you should try them on your own.

---

### Post by kd7swh on 2008-12-06
> **Nanix said:**
> First of all: WOW! you guys are helpful!

Major question- stability? what exactly is stability? If I did LFS would that be significantly less stable than Ubuntu or other mainstream distros? Is Debian, since it's "badass" and the core of Ubuntu, more stable than Ubuntu? or is Ubuntu made to be more stable than its parent Debian?

and ugm6hr what do you mean by "most things just work"? Does Debian have more compatibility issues? Would LFS be be really picky and not fun to work with (and would I personally have to be working on it?)

First off stability, LFS could be as stable, less stable or more stable than other distros. That depends how you go about building it. Both Debian and Ubuntu have large teams, that work to produce a stable distro. If you are a new user I would select Ubuntu because it is easier to install than Debian but they are both just as stable as one another.

LFS is a lot of work. If you want to install or compile applications you may struggle with dependencies (the libraries and such programs need to run) With a pre-built distro dependency/package management is a snap out of the box.

You can customize basically any of them, but I think Ubuntu is an obvious first time choice.

---

### Post by Nanix on 2008-12-06
> **binbash said:**
> First of all : 

If you never used linux or a little,it does not matter how advanced user(computer) you are, dont try lfs, gentoo or archlinux.


Instead of asking distro differences , in my opinion you should try them on your own.
ok so the consensus is i really should test out plain ubuntu first?
sounds good to me and i can get a chance too test what i want to puy in my own (undistributed) distro.

---

### Post by ugm6hr on 2008-12-06
> First of all: WOW! you guys are helpful!
A good reason to choose Ubuntu

> Major question- stability? what exactly is stability? If I did LFS would that be significantly less stable than Ubuntu or other mainstream distros? Is Debian, since it's "badass" and the core of Ubuntu, more stable than Ubuntu? or is Ubuntu made to be more stable than its parent Debian
Stability: Packages can either be tried and tested (and work reliably), or be the latest and greatest with more features (with more likelihood of unexpected unreliability due to shorter testing period).

I am not an expert on this - so check these facts...

Debian comes in different flavours.  Debian "stable" is exactly that - tried and tested.  Debian Sid is more experimental with newer versions of all the packages.  Ubuntu is somewhere in between; it takes a 6-monthly snapshot of Sid, and then spends the rest of the supported time (18-60 months, depending on version) trying to ensure those packages are as stable as possible.

> what do you mean by "most things just work"? Does Debian have more compatibility issues? Would LFS be be really picky and not fun to work with (and would I personally have to be working on it?)
Ubuntu packages things together so that everything is pretty intuitive.  In fairness, the majority of that is dependent on the Desktop Environment (i.e. Gnome), but also includes things like Bluetooth support etc which would otherwise need to be added manually.

Compatibility with hardware is pretty universal; a Linux driver can be compiled to work with any distro.  The question is, whether it can be made to work with a few clicks, or whether you need to track down the driver and manually compile it. As for LFS - yes you would have to work on it (it is Linux from Scratch - it is exactly as it sounds).

Honestly, if you are unable to find out the answers to these questions by yourself with google etc, I would strongly advise against manually doing anything.  You will find it frustrating.  Gentoo / LFS etc are for people who enjoy the challenge of getting stuff to work.

---

### Post by newbee70 on 2008-12-06
> **Nanix said:**
> First of all: WOW! you guys are helpful!

Major question- stability? what exactly is stability? If I did LFS would that be significantly less stable than Ubuntu or other mainstream distros? Is Debian, since it's "badass" and the core of Ubuntu, more stable than Ubuntu? or is Ubuntu made to be more stable than its parent Debian?

and ugm6hr what do you mean by "most things just work"? Does Debian have more compatibility issues? Would LFS be be really picky and not fun to work with (and would I personally have to be working on it?)

Welcome to the forums Nanix.

What Operating system(s) have you been using?

From a complete Ubuntu Noob, you just found out the first and foremost reason for Ubuntu: the Forum support I have not found a more helpful friendly group of people.

My reason for switching is that < imho > Ubuntu is more robust than Windows xp pro or Vista. I changed over 3 Desktops and 1 laptop. 

<< cut out windows slam >>

in 2 months I have found 5 worms <all windows worms> didn't even affect Ubuntu. although I did quash them so they did not get spread by me.

1 crash in the 2 months, which I know now I could have recovered from without reloading software. <<Payment for being a Noob>>

time to bring my system up under a full reinstall <<from start to finish
installing / updating / loading applications and data >> just a tad over 2 hours.

---

### Post by Nanix on 2008-12-06
> **newbee70 said:**
> Welcome to the forums Nanix.

What Operating system(s) have you been using?

From a complete Ubuntu Noob, you just found out the first and foremost reason for Ubuntu: the Forum support I have not found a more helpful friendly group of people.

My reason for switching is that < imho > Ubuntu is more robust than Windows xp pro or Vista. I changed over 3 Desktops and 1 laptop. 

<< cut out windows slam >>

in 2 months I have found 5 worms <all windows worms> didn't even affect Ubuntu. although I did quash them so they did not get spread by me.

1 crash in the 2 months, which I know now I could have recovered from without reloading software. <<Payment for being a Noob>>

time to bring my system up under a full reinstall <<from start to finish
installing / updating / loading applications and data >> just a tad over 2 hours.

I use xp and mac os x
Primarily Mac OS X though

---

### Post by nakama85 on 2008-12-06
Ubuntu Is number 1 because it has notoriously better "out of box" support than many other distros. Secondly the forums. I have never found such an active community with any other distro (and I have tried many).

When it comes down to it I would say try whatever draws you in the most.

If you want to buil your system from command then try gentoo.

The most important question is: Would you rather have to buy a book 2 inches thick while your trying to learn linux or would you rather have a real interaction with others. The nice thing about a community over a book is that if something goes wrong you can say hey what do I do know and receive a response from someone who more than likely has had the same problem (try that with a book).

Just my 2 Cents

---

### Post by misfitpierce on 2008-12-06
I've been using Ubuntu for years. I've also tried Fedora and Mandriva with redhat and a few others. Ubuntu is getting to be the most user friendly and is updated a lot. Also there is a big community to help you with Ubuntu if help is needed. I have tried Debian itself but Ubuntu is a bit more spunked up. Ubuntu is definatly the way to go. I did not choose because it was popular or whatever, I have been using since a lot never even heard of it :) must say its just plain and simple the way to go and is just the best. I believe what Mark Shuttleworth is planning to accomplish with the open source world and with Ubuntu.

---

### Post by dannytatom on 2008-12-06
I know it's already been said, but one of the main reasons I chose Ubuntu is the community (both forums & IRC).  Aside from that, I love the 6 month release cycle and not having to compile from source constantly.

My friend uses gentoo, and I get frusterated/impatient just watching him try to get things working.

---

### Post by kansasnoob on 2008-12-06
The bottom line is you're only going to know what Linux suits you best after you've tried them all!

Maybe Linux won't suit you at all. My two favorites are Ubuntu and Linux Mint. When it comes to KDE I actually like Simply Mepis better than Kubuntu.

I simply prefer Debian based distros to Red Hat based distros, and I find Ubuntu to be the most convenient, user friendly, and gui respective distros I've used!

I think most end users want a gui friendly system, they'd prefer to seldom have to use the terminal, and they just want things to work o-o-b.

Is Ubuntu perfect? NO! But it just keeps getting better and better and I seriously doubt that Canonical will give up on the "open source" values of Linux as others have!

Just as kind of a "sideways" comment, I love the way PCLOS Gnome runs from Live CD but their installer sucks and I've never been able to install without ending up in Kernel Panic!

---

