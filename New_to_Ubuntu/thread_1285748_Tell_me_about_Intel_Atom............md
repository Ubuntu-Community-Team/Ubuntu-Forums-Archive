---
title: "Tell me about Intel Atom..........."
date: 2009-10-08
forum: New to Ubuntu
---

### Post by Harshana on 2009-10-08
:confused:I got **HP MINI 110-1001 TU NETBOK** that with intel atom processor, 1GB RAM-533mhz FSB.It was originaly come with windows xp home edition.Will ubuntu work on it? Which version? 
I actually don't know about Atom processer.How it's perfomence comparing with celeron?
Will Atom ok for documentation, Matlab using , contril system and Electroniccircuit simulations?

---

### Post by shafin on 2009-10-08
Ubuntu Netbook Remix and ubuntu Moblin Remix will work on it. I can't answer the other questions as I dont have an atom powered computer.

---

### Post by zeroseven0183 on 2009-10-08
Hi and welcome to the Community!

Yes, Ubuntu will most likely work on it. What's the model of your HP netbook?

I would suggest trying [Ubuntu Netbook Remix]("http://www.ubuntu.com/getubuntu/download-netbook"). The installation procedure is detailed in [https://help.ubuntu.com/community/Installation/FromImgFiles]("https://help.ubuntu.com/community/Installation/FromImgFiles").

By the way, Intel Atom processor is built especially for netbooks, if I'm not mistaken (although I'm now seeing desktops using it). It's basically used for ultra-low voltage machines and for mobility.

References: [http://en.wikipedia.org/wiki/Intel_Atom]("http://en.wikipedia.org/wiki/Intel_Atom"), [http://www.intel.com/technology/atom/]("http://www.intel.com/technology/atom/")

---

### Post by Harshana on 2009-10-08
> **shafin said:**
> Ubuntu Netbook Remix and ubuntu Moblin Remix will work on it. I can't answer the other questions as I dont have an atom powered computer.

Thanx
:guitar:

---

### Post by Harshana on 2009-10-08
> **zeroseven0183 said:**
> Hi and welcome to the Community!

Yes, Ubuntu will most likely work on it. What's the model of your HP netbook?

I would suggest trying [Ubuntu Netbook Remix]("http://www.ubuntu.com/getubuntu/download-netbook"). The installation procedure is detailed in [https://help.ubuntu.com/community/Installation/FromImgFiles]("https://help.ubuntu.com/community/Installation/FromImgFiles").

By the way, Intel Atom processor is built especially for netbooks, if I'm not mistaken (although I'm now seeing desktops using it). It's basically used for ultra-low voltage machines and for mobility.

References: [http://en.wikipedia.org/wiki/Intel_Atom]("http://en.wikipedia.org/wiki/Intel_Atom"), [http://www.intel.com/technology/atom/]("http://www.intel.com/technology/atom/")

It is HP mini 110-1001 tu

Thankx:guitar:

---

### Post by mo0nykit on 2009-10-08
**@zeroseven0183**

you actually mean low **power**, not voltage. :) forgive me for being finicky, but it's an important distinction :)

Peace! :)

---

### Post by zeroseven0183 on 2009-10-08
> **Harshana said:**
> It is HP mini 110-1001 tu

As mentioned in [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#HP Mini 110 / Compaq Mini 100c]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#HP Mini 110 / Compaq Mini 100c"), sound does not work out of the box but has ways of fixing it. Follow the instructions in the page and if you have troubles just open a new thread in the forums to get help.

---

### Post by zeroseven0183 on 2009-10-08
> **mo0nykit said:**
> **@zeroseven0183**

you actually mean low **power**, not voltage. :) forgive me for being finicky, but it's an important distinction :)

Peace! :)

Yeah, sure. Thanks for correcting. **Power**

---

### Post by Harshana on 2009-10-08
> **zeroseven0183 said:**
> As mentioned in [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#HP Mini 110 / Compaq Mini 100c]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#HP Mini 110 / Compaq Mini 100c"), sound does not work out of the box but has ways of fixing it. Follow the instructions in the page and if you have troubles just open a new thread in the forums to get help.

Now the problem is how i get CD of Ubuntu 9.04 Netbook Remix?
There are no CD providing & i don't have internet connection either.Now i'm in office and there are no way to download it.
:(

---

### Post by zeroseven0183 on 2009-10-08
Ohhh You really don't have to get the "CD" of UNR. It's only an .IMG file to download. After download it (somewhere else), use the application suggested in the site to create it on a USB thumb drive.

---

### Post by Harshana on 2009-10-08
> **zeroseven0183 said:**
> Ohhh You really don't have to get the "CD" of UNR. It's only an .IMG file to download. After download it (somewhere else), use the application suggested in the site to create it on a USB thumb drive.

 But it is defficul to download with over connection on office.
Is there any way to get a CD?

Thankx.
:guitar:

---

### Post by zeroseven0183 on 2009-10-08
UNR is designed for netbooks which mostly do not have built-in optical drives therefore the best way to install it is through USB.

I suggest you download the IMG file somewhere else, internet cafe or at your friend's house then process it there (following the instructions in the link) and store it on your USB.

Sure it's worth the download time.

---

### Post by ram2500 on 2009-10-08
I have never used an Intel Atom device, but I don't recommend it as a primary machine, partly because it is viewed by many as a rebadged, beefed-up Pentium III. Who wants that??? If you are in the market for a laptop/netbook, if you spend $50 - 100 extra dollars, you'll get a FULL FUNCTIONING system with a DVD burner and a suitable Celeron/Sempron processor. Be careful!!! I'm sure Linux can and will do okay on an Atom, but I'm talking about screen size, capabilities (even in resource-friendly Linux, if, for example, you run GIMP, you'll slow it down) and just the fact that they cost about the same as an entry-level, full featured laptop. 

I haven't seen Netbook Remix. Does it take certain features away?

---

### Post by Kapitän Rotbart on 2009-10-08
The Atom processor can handle Linux well. I've toyed with netbooks and Ubuntu pwns them. Yes, the netbook remix version is lighter, on the account that it won't ship with compiz. In fact, compiz won't even install well on it, so you're renouncing some eye candy here. Otherwise, you could install the normal Ubuntu, you'll get compiz out of the box, but expect compiz to crash. Hence I'd recommend the netbook remix. Also be careful what you run on Wine. I have run some apps on Wine flawlessly, but some apps (*ahem* IE6) are resource hogs to begin with (though when you need IE, it's still best to run it in Wine than to have to boot windeuce on a netbook). Still worth having Wine installed, but use it sparingly! Expect to be using Linux-native software on a netbook (if your computing needs grow beyond this, why are you using a netbook??).

I wouldn't recommend an Atom computer as a primary computer on the account of netbooks being small. Would you want to do most of your typing on a small keyboard? Hopefully not! Would you want to do media editing (audio/video) on a small screen? Why bother? Would you use VirtualBox on it? That's probably ridiculous...at most DOSBox! Hopefully you won't game on it too much, either (especially in Wine). If you have to game on the netbook, get into Scumm games that run in the ScummVM...it's all mouse-controlled :) but then you might wear down your trackpad faster.

I would recommend waiting for Karmic, though (being so close to the release date)...depending on how badly you need an Ubuntu netbook...it may even be best to leave the Atom netbook in its box (other than for hardware tests) until the Karmic release date, here's why:
[LIST]
[*]Ubuntu netbook remix will look much better in Karmic
[*]KDE will have a netbook remix! This offers choice, especially if you like KDE (I don't use KDE, so I don't care that much, but still)
[*]Anjal...use it instead of Evolution (Evolution is a resource hog, Anjal is webkit, snappy fast and uses tabs for everything, plus it's in the repos!!!)
[*]More goodies on the Gnome suite (Empathy instead of Pidgin, smaller text and less of a resource hog, getting rid of Ekiga that took unecessary space)
[*]And more!
[/LIST]

There is no shortage of reasons to wait for Karmic for booting some Ubuntu Netbook Remix on any netbook.

---

### Post by marshmallow1304 on 2009-10-08
> **zeroseven0183 said:**
> UNR is designed for netbooks which mostly do not have built-in optical drives therefore the best way to install it is through USB.

Also, the UNR image is nearly 950 MB, so it's not going to fit on ordinary CDs.

---

### Post by zeroseven0183 on 2009-10-08
> **ram2500 said:**
> Who wants that???...

Students, maybe, who want electronic devices instead of their notepads.

Netbooks are I think (super, if not) stripped-down versions of notebooks - limited in size and function. Therefore, it's cheaper.

And yes, students don't make (or get) enough money to buy laptops. Oooppsss sorry

---

### Post by LinuxRocks9.04 on 2009-10-09
I agree, you should wait for Karmic to come out and then, if possible, install UNR. Unfortunately, while sensible, Ubuntu does not ship "Live USB's" like they do for Live CD's. Getting to the point, the only efficient way to get Ubuntu is downloading the image file and creating a startup USB. XD

---

### Post by egalvan on 2009-10-09
> **mo0nykit said:**
> **@zeroseven0183**

you actually mean low **power**, not voltage. :) forgive me for being finicky, but it's an important distinction :)

Peace! :)

Well, as the butcher said while chopping rabbits in half

"that's kinda splitting hares"  :guitar:


The MAIN way EE's lower **POWER** is by lowering **VOLTAGE**.

Shrinking die size is the other biggie "power reducer".

"Under-volting" is a popular way for laptop users to extend battery life. "Under-clocking" is another.
Not all CPU platforms are u-v friendly...
some can do it via software, some via hardware (usually shorting pins on the CPU)

---

### Post by fooman on 2009-10-09
there is a version of netbook remix made just for hp mini's....

[ hp mini remix]("http://psychocats.net/hpminiremix/download/")

based on ubuntu 9.04, it works great on my hp mini 1035nr.  everything worked right "out of the box".....sound, graphics, wireless all worked without me lifting a finger!  :)

---

### Post by Zoot7 on 2009-10-09
> **Harshana said:**
> Will Atom ok for documentation, Matlab using , contril system and Electroniccircuit simulations?
Matlab and specialized Electronic simulations should work, but they'll be slower than if you'd a full blown Core 2 Duo or something similar. The Atom wasn't really designed for number crunching such as Matlab.

As for putting Ubuntu on that machine, it'll love it. ;)

---

### Post by 3rdalbum on 2009-10-09
You don't *need* Ubuntu Netbook Remix on a netbook. You can run regular Ubuntu, which comes on a CD. Netbooks are just small, low-powered computers and they are compatible with the same operating systems you might use on a desktop.

EDIT: I run ordinary Ubuntu 8.10 on an Atom-based netbook and server.

Also, the Intel Atom is NOT a "rebadged Pentium 3". It is based on the technology Intel developed for "Nehalem" (Core i5 and Core i7), but designed for ultra low power consumption. It's true that Atom has some things in common with the Pentium 3, but it has almost as much in common with the P3 as the Core 2 does. In addition, Atom has Hyperthreading, which the Pentium 3s never had, and some Atoms are 64-bit and dual-core which was never done on Pentium 3.

---

### Post by gjoellee on 2009-10-09
> **shafin said:**
> Ubuntu Netbook Remix and ubuntu Moblin Remix will work on it. I can't answer the other questions as I dont have an atom powered computer.

+1 for moblin

---

### Post by LewRockwell on 2009-10-09
[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

this netbook gets thrashed every day and still shows up for work...lol

.

---

### Post by Irick on 2009-10-09
I have this exact netbook, in fact i am posting from it right now running the 9.10 beta UNR.

the stable UNR runs flawlessly with one exception.
Sound.
However the fix is quite simple: [https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/175](https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/175)

The 9.10 beta "just works" including most Compiz effects, however it is beta until the end of this month.

*Edit*

As for performance, the Atom in general performs at about 1/2 the computational power of a similarly clocked Celeron.
I have found it exceeding the performance of my 700mhz desktop Duron circa 2001, but it is by no means a powerhouse. It should be able to do what you need if you are not in too much of a hurry, however the real benefit is obviously the portability.

---

### Post by LewRockwell on 2009-10-09
> **Irick said:**
> I have this exact netbook, in fact i am posting from it right now running the 9.10 beta UNR.

the stable UNR runs flawlessly with one exception.
Sound.
However the fix is quite simple: [https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/175](https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/175)

The 9.10 beta "just works" including most Compiz effects, however it is beta until the end of this month.

Thank you for extending your valuable time to make this report!

.

---

### Post by cholericfun on 2009-10-09
instead of matlab you may want to use octave,
its not as pretty but its for example 100 times quicker to start up.
of course if you're in for numbercrunching, its not gonna make any difference whether your in matlab or octave or whatever. its going to be slow!

---

### Post by ram2500 on 2009-10-09
> **3rdalbum said:**
> You don't *need* Ubuntu Netbook Remix on a netbook. You can run regular Ubuntu, which comes on a CD. Netbooks are just small, low-powered computers and they are compatible with the same operating systems you might use on a desktop.

EDIT: I run ordinary Ubuntu 8.10 on an Atom-based netbook and server.

Also, the Intel Atom is NOT a "rebadged Pentium 3". It is based on the technology Intel developed for "Nehalem" (Core i5 and Core i7), but designed for ultra low power consumption. It's true that Atom has some things in common with the Pentium 3, but it has almost as much in common with the P3 as the Core 2 does. In addition, Atom has Hyperthreading, which the Pentium 3s never had, and some Atoms are 64-bit and dual-core which was never :done on Pentium 3.

Did I hear **Atom based server**?!?!?! Oh my goodness, how do they do it? It's Houdini working at Intel:) 

I've heard from people that they have trouble with Opteron servers at times. Let's just hope that these Atoms never run servers that banks, our government and the e-mail servers would use. Then, if that happened, we'd be in a world of hurt.:P

---

### Post by Harshana on 2009-10-16
Thanx. i'll try it...........

---

### Post by Harshana on 2009-10-16
> **ram2500 said:**
> I have never used an Intel Atom device, but I don't recommend it as a primary machine, partly because it is viewed by many as a rebadged, beefed-up Pentium III. Who wants that??? If you are in the market for a laptop/netbook, if you spend $50 - 100 extra dollars, you'll get a FULL FUNCTIONING system with a DVD burner and a suitable Celeron/Sempron processor. Be careful!!! I'm sure Linux can and will do okay on an Atom, but I'm talking about screen size, capabilities (even in resource-friendly Linux, if, for example, you run GIMP, you'll slow it down) and just the fact that they cost about the same as an entry-level, full featured laptop. 

I haven't seen Netbook Remix. Does it take certain features away?

Thanx 
:guitar:

---

### Post by Harshana on 2009-10-16
> **Kapitän Rotbart said:**
> The Atom processor can handle Linux well. I've toyed with netbooks and Ubuntu pwns them. Yes, the netbook remix version is lighter, on the account that it won't ship with compiz. In fact, compiz won't even install well on it, so you're renouncing some eye candy here. Otherwise, you could install the normal Ubuntu, you'll get compiz out of the box, but expect compiz to crash. Hence I'd recommend the netbook remix. Also be careful what you run on Wine. I have run some apps on Wine flawlessly, but some apps (*ahem* IE6) are resource hogs to begin with (though when you need IE, it's still best to run it in Wine than to have to boot windeuce on a netbook). Still worth having Wine installed, but use it sparingly! Expect to be using Linux-native software on a netbook (if your computing needs grow beyond this, why are you using a netbook??).

I wouldn't recommend an Atom computer as a primary computer on the account of netbooks being small. Would you want to do most of your typing on a small keyboard? Hopefully not! Would you want to do media editing (audio/video) on a small screen? Why bother? Would you use VirtualBox on it? That's probably ridiculous...at most DOSBox! Hopefully you won't game on it too much, either (especially in Wine). If you have to game on the netbook, get into Scumm games that run in the ScummVM...it's all mouse-controlled :) but then you might wear down your trackpad faster.

I would recommend waiting for Karmic, though (being so close to the release date)...depending on how badly you need an Ubuntu netbook...it may even be best to leave the Atom netbook in its box (other than for hardware tests) until the Karmic release date, here's why:
[LIST]
[*]Ubuntu netbook remix will look much better in Karmic
[*]KDE will have a netbook remix! This offers choice, especially if you like KDE (I don't use KDE, so I don't care that much, but still)
[*]Anjal...use it instead of Evolution (Evolution is a resource hog, Anjal is webkit, snappy fast and uses tabs for everything, plus it's in the repos!!!)
[*]More goodies on the Gnome suite (Empathy instead of Pidgin, smaller text and less of a resource hog, getting rid of Ekiga that took unecessary space)
[*]And more!
[/LIST]

There is no shortage of reasons to wait for Karmic for booting some Ubuntu Netbook Remix on any netbook.


Thankx
:guitar:

---

### Post by 3rdalbum on 2009-10-16
> **ram2500 said:**
> Did I hear **Atom based server**?!?!?! Oh my goodness, how do they do it? It's Houdini working at Intel:)

Home server.

> I've heard from people that they have trouble with Opteron servers at times. Let's just hope that these Atoms never run servers that banks, our government and the e-mail servers would use. Then, if that happened, we'd be in a world of hurt.:P

Funny you should say that - there's a new school of thought that says you should create racks of servers based around Mini-ITX machines with the VIA Nano or the Intel Atom. I generally disagree with this school of thought, but remember you'd be talking about large numbers of Atom-based servers, which means high redundancy compared to a similar dollar value of Opteron-based servers.

---

### Post by 3rdalbum on 2009-10-16
Regular Karmic is pretty awesome on my Aspire One. When I installed Ubuntu previously, I used the Ext2 filesystem because I'd been told that it minimised the wear on my SSD; but I was having problems with Firefox temporarily freezing after every web page. With Karmic and Ext4, Firefox runs fast.

And Karmic looks awesome - I blew someone away with Karmic today, and a little bit of restrained Compiz goodness :-)

---

### Post by francsal on 2009-10-18
Speaking from personal experience I can tell you that the Atom does the work and does it well. I have a MSI Wind U120 (Atom N270 1.6Ghz 1GB Ram) and it runs Kubuntu Karmic like a charm. And it did Run Jaunty really good, too. Now, obviously, it's not a utrla fast computer, but ffor everyday use (web surfing, normal office use, music play and the ocassional DVD movie -via an external DVD player) it works, and works really good, with the added benefit of ultra portability. I usually read about people saying "dont use this as yyour main computer".... I'll say, it depends entirely on what people use the computer for. Video editing? Obviously not!!! Gaming? On an Intel GFX card? Never! (Altough, when I still had XP installed, I used to play MS Flight Simulator 2004, and it worked pretty well)

Again, I think it depends a lot on how people use the computer. And, after about 4 months using my netbook, and considering that I do not demand extremely performance for specialized software, I can say that it's a wonderful choice.

Cheers.

Frank.

---

### Post by Kegusa on 2009-10-22
Cheers! Another testimonial of using a Compaq/HP mini 110c - 1011SO running Ubuntu 9.04. (N270 1.6GHz, 1GB RAM)

In my personal experience after I had passed the initial hiccups described in the wiki (sound / wired nic problems) and first trying it out using the default OS (some kind of winXP that made the machine slow down to a crawl) this machine really loves Ubuntu. Oh, and most of the compiz settings do work, I'm addicted to wobbly windows so cant live without it ;)

I actually use it as my main machine 90% of the time, since I can take my work with me everywhere and enjoy ubuntus "it just works" for the most of the time. Since the keyboard is fairly big for a netbook with 92% of the usual size it works perfect for me as a programmer. Also have a 22" monitor at my workstation that I use when I need a bit bigger screenspace for some programs (GIS related mapshowings etc)


Last buisniss meeting got a few awes as I took the netbook from the bag, powered it up in seconds since I never turn it off, but use the sleep function. Then hooking it up with a never before used projector and got the screen up in less than a few seconds and ready for presentation. The next person after me booted up his laptop (took a minute with Vista) and then tried hooking up the projector, fiddled with display settings for few minutes before getting started then his presentation crashed halfway through.. 

Ofc netbooks are not made for gaming and heavy video editing and stuff like that.

---

### Post by kwacka on 2009-10-22
I bought a Atom netbook (Asus) after lugging a laptop on a 13 hour flight and it didn't work when I got there - it went home by post (found out later it was a faulty power cord). Had to wait until I got home to put remix on - Australia's got horrific charges.

And no, I don't transcode videos on the netbook or laptop, neither do I use GIMP all that much on either; there's the desktop for that.

It does everything I need when I'm away from home - it's definitely a different market to a laptop. 

Presently getting it set up for outdoor (away from home) low-power amateur radio & digital photography use - ideal for a quick look at photos before deciding whether to bin/keep. 

And there's no way I'd get 7 hours use out of a laptop battery.

---

### Post by 3rdalbum on 2009-10-22
I like the netbook form factor so much that I'd love to have a machine with a Core 2 ULV, Nvidia 9200M and a 9 inch or 10 inch screen. Plus a nine-cell battery like the one I have on my Aspire One, so it runs for a while.

How awesome would that be? But no, they're either making 10 inch netbooks with Atoms, slow SSDs and Intel 945G; or 13 inch Core Solo (or AMD equivilant) notebooks that are overpriced for their specification and still bigger than I want.

---

