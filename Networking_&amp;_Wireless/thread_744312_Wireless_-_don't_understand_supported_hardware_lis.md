---
title: "Wireless - don't understand supported hardware list"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by entryname on 2008-04-03
Hi guys long time no post

I have to admit to being thick here and not understanding the supported wireless hardware list at [http://linux-wless.passys.nl/](http://linux-wless.passys.nl/). 

I'm not clear if I need to worry what chipset I need. I would like to connect a ten year old (formerly windows ninety-eight) PC now running Breezy Badger to a BT HomeHub I don't know whether that is 802.b or 802.g or what chipset my laptop or the HomeHub are using. I don't know which of these two would be supported by badger specifically being an old build. I don't know if any of the hardware in the lists would be incompatible with a PC that old. I don't know which if any would be supported by badger as it stands. I can't really install anything else on badger since synaptic doesn't work any more and compiling from source always fails due to assorted errors. I have a horrible feeling that rules out installing a new driver on badger.

If I need to upgrade badger first, I don't know if the old hardware would run a newer version of ubuntu, I don't know if I can upgrade from a disk or a file since the old PC can only do dial up at the moment, and if it can upgrade from a disk or file I don't know which one since I don't want to wipe the files on the old PC - that is, I don't want to wipe the hard disk and reinstall from zero.

I'm sorry if someone posts "go read the FAQs you idiot", I have printed the hardware list for PCI cards, all 11 pages which finished my ink cartridges, and that's just PCI not USB, but I really, honestly, don't understand enough to do this. Can anyone shed any light on any of it??

Regards

Michael R :confused:

---

### Post by kidders on 2008-04-05
Hi there,

First thing's first ... If you're not too confident about what you're doing, upgrading to a currently supported version of Ubuntu is the best way to be sure you can get quick, accurate help ... so if I were you, I would consider giving Feisty a try.

> If I need to upgrade badger first, I don't know if the old hardware would run a newer version of ubuntuSupport for old hardware does get removed from time to time, so if your computer really is *very* old, you may have problems. Typical reasons for dropping Linux support for old hardware include...[LIST]
[*]The manufacturer withdraws supports for its own hardware.
[*]The development burden of supporting something continually troublesome on an ongoing basis is simply prohibitive.
[*]The hardware or its driver conflicts with too many things.
[/LIST]Hardware support is not normally dropped by Linux for trivial reasons though, so if whoever built your computer made reasonably good hardware choices, you shouldn't need to worry too much. The possibility of having to go back to Badger does (at least in theory) exist though.

> I'm not clear if I need to worry what chipset I need.You don't need to be *too* concerned. Your priority should be finding a good deal on a good card. Before you actually _buy_ it though, there are a few issues to consider...[LIST]
[*]**Compatibility with your system.** You may find you're missing a critical requirement, such as a minimum amount of RAM, minimum clock speed, or (more obviously) the right kind of slot (PCI, USB, etc.). If you're not quite sure, you could try bringing your motherboard's manual with you to a shop. You'll also need to know what kind of CPU you have, and how much RAM.
[*]**Linux compatibility.** Your hardware compatibility list can help you with that.
[*]**Badger compatibility.** More-so than *whether* something you plan to buy is on the list, you'll need to take a look at *why* it's on it. For example, if your card's driver is part of the Linux kernel, you'll need to check when it was added, and that your Badger kernel is new enough. On the other hand, if it's there thanks to a third party driver, you should visit its website, and check that your Badger satisfies its software requirements (kernel, gcc version, etc.). All good driver sites clearly list them.
[/LIST]

Anyhow, I hope that helps. Just a couple of notes...

- 1 -
Not having a working compiler does narrow your options. That's worth fixing!

- 2 -
If you do decide to update to a more recent Ubuntu, reinstalling from scratch is by far the best approach. To be honest, I can't say I would recommend Breezy -> Dapper -> Edgy -> Feisty. Too much could go wrong!

---

### Post by entryname on 2008-04-07
Hi and thanks for posting.

As of now, I have got broadband on both PCs, but only by moving the hub upstairs. I added a network card billed (by Maplin although not on the box) as being linux compatible, and it worked, no problems. I then upgraded to 6.06 LTS (whichever one that is). I don't intend to upgrade again until support for 6.06 is withdrawn (whenever that is). 

I should point out however for any upgraders that although downloading the files took about half an hour, for linux to actually install them took a lot longer, hours and hours, and it did ask a lot of irritating questions (stopping at each question). If asked do you want to replace the existing config file for blah blah the correct answer would appear to be yes, even though it then forgets things like display tweaks. It complains on startup that it can't find (now where did I write that) .... unable to locate rsdp is what it says. I don't know what an rsdp is and why it can't locate it, but the list of start up thingies that then goes through all say OK and Ubuntu starts with no obvious horrid problems so it doesn't appear to be critical.

I still don't know my way around the Linux hardware list. I don't understand what it's telling me. I've had problems with these lists before where anything you can get in maplin etc. isn't on the lists and vice versa. I have 11 pages of printout upstairs but no idea what it means. Let me try and explain why not...

I know I have PCI as I saw two slots on the motherboard and put the network card in one, and it worked. I still have a spare slot. My BIOS saw the network controller incidentally, and said so on the POST screen. As I said, no problems with that. So I printed the list for PCI. I got as far as, I need something listed green, but let's just take one as an example. The first green one is 3Com 3CRDAG675. Maplin says sorry no products found when ask for it. RS says we found no results. PC World says no results found. However...
It says 802.11a/g. I don't know what type of wireless network the home hub is running, that is, what signalling standard. I can't find it in the manual or on the hub. My laptop does b and g so it must be one or other. But what if it's b and this card only does a and g?
It says chipset Atheros. I don't need to know that or worry about that, correct?
The driver is Mad WiFi and it has a web address to get it from. I can find the website and the download link, though it does say that it depends on proprietary code. That's not a show stopper, right?
So having consulted the hardware list, the bottom line for this example is, I can't get this card, and don't know if it would work if I could.
I note that it is apparently possible for a card to be compatible with linux generally but not one specific distribution or build. Er, not sure how I'd know if a card fell into that category. I'm assuming the list means compatible with linux kernel, and presumably with the most recent i.e. current version. I notice incidentally that some entries say driver and some say driver available at. Does that mean if it just says driver its in the kernel already??

I tried and tried to get the thing to compile source code. I installed this and that compiler and package. Yes I have compilers including GCC and they should have all the bits. But compiling source never, never, never works. It gets to the compiler and runs it but then I always get some annoying message saying it can't gobbledyobbledy because it can't geekyspeaky. And after a while I just gave the whole business up as a bad job and took it that compiling other peoples' source code on your own machine is strictly for highly advanced students only. I now have synaptic again, and that should work, so if I can get it on that, I can have it.

So any clues on how to decode this list? How do I tell what system my home hub is using for instance? Is there any hope of finding any of these in maplin? Is there any way of finding a compatibility list for one specific kernel as opposed to linux generally? Is there an equivalent Ubuntu list somewhere or not?

Regards

Michael R

PS. Some people will doubtless be saying to their screens, he says he's got broadband working with the network card, I don't get it, what's his problem? I don't know how much speed I'm losing doing that. I'm getting 300KB (kilobytes) per second a mile and a quarter from the exchange. Running a hub off an extension socket is supposed to be slower and less reliable. If I ever reported a problem I'd be told to move it downstairs. If I could get wireless working on Ubuntu and it was reasonably inexpensive (the network card was only about £7) and reasonably aggro free I think I'd want to do it.

---

### Post by chili555 on 2008-04-07
> Some people will doubtless be saying to their screensI am saying, "he sure is a prolific writer!"

COMPILING: Compiling is a somewhat advanced skill. Developers write for a variety of linux distributions from Ubuntu to Suse to Fedora, etc. all of which have their little quirks. The trick is to have the right dependencies installed and to know what to do when you see the error to get the compilation to run without errors. The dependencies you need, in most cases, are included in *build-essential* which you can install with Synaptic. 

If you post your compile errors here, we'll be glad to help. But why are you trying to compile a wireless module before you have even picked a card? 

COMPATIBILITY LIST; This lists cards that are compatible, possibly with some additional steps, with Linux generally. If the card is shown in green, it will work with Ubuntu. Many cards have modules, or drivers, as they are called in Redmond, built in to the kernel; more are added in every new kernel. Few, if any, are removed. If the card you pick has a module built in to the kernel, your life just got easier: give Ubuntu your ESSID and encryption key, if any, and you should be connected!

802.11a/b/g:  These are generally forward and backward compatible. If you have an 802.11b or g router, you should easily connect to any b or g card. I do.

MAPLIN: They have a Sitecom card here  [http://www.maplin.co.uk/module.aspx?ITAG=FAQ&ModuleNo=45078&doy=25m3](http://www.maplin.co.uk/module.aspx?ITAG=FAQ&ModuleNo=45078&doy=25m3)  The website says it's based on the ralink chipset and they even point you to the Linux module! The module rt2x00pci.ko is built in to the kernel, so I'd try that first.

Good luck. We are here for you if you get stuck.

Hmmmm. Looks like I'm pretty prolific, too.

---

### Post by kidders on 2008-04-07
Hey again,

I'll try to help with as many of your questions as I can ...


> **entryname said:**
> I don't intend to upgrade again until support for 6.06 is withdrawn (whenever that is).Dapper is very old at this stage ... unless you have a good reason for needing to use it (eg you're running production servers with it), I would recommend against doing so. It's an LTS release, by the way, supported 'til 2011.

> **entryname said:**
> it did ask a lot of irritating questions (stopping at each question).You can suppress that behaviour if you want to. For many users, the default answers to configuration questions tend to do the trick.

> **entryname said:**
> I don't know what an rsdp is and why it can't locate itThere are some threads here about that issue. It's ACPI related, afaik.

> **entryname said:**
> I still don't know my way around the Linux hardware list. I don't understand what it's telling me.The list you mentioned in your o/p tells you...[LIST]
[*]Vendor & product codes which, in theory, uniquely identify any device.
[*]The bus type, so you can distinguish easily between USB & PCI devices, for example.
[*]The IEEE 802.11 standard the devices comply with (a/b/g/n), so you can get a rough idea of the bandwidth each one is capable of.
[*]The device chipset, and the name of the appropriate driver. (One implies the other.)
[*]The level of compatibility you can expect with a typical Linux system.
[/LIST]I very much doubt the list is intended to be printed ... unless perhaps you're engaged in academic or software development research.

> **entryname said:**
> I don't know what type of wireless network the home hub is running, that is, what signalling standard.Its remote management interface should tell you its capabilities. Alternatively, you could search online, or ask a computer that's using its WLAN.

> **entryname said:**
> My laptop does b and g so it must be one or other. But what if it's b and this card only does a and g?That's unlikely to happen. Most devices that support 802.11g also support 802.11b.

> **entryname said:**
> It says chipset Atheros. I don't need to know that or worry about that, correct?Well, the device chipset tells you the driver you'll want. To many people, the chipset in their hardware matters, for a variety of reasons ... on the other hand, some people just don't care.

> **entryname said:**
> The driver is Mad WiFi and it has a web address to get it from. I can find the website and the download link, though it does say that it depends on proprietary code. That's not a show stopper, right?That's sort of a philosophical question, really ... but in terms of whether your hardware will work, it's not a show stopper.

> **entryname said:**
> I notice incidentally that some entries say driver and some say driver available at. Does that mean if it just says driver its in the kernel already??Probably.

> **entryname said:**
> I installed this and that compiler and package.Bad start! It's always best to think carefully before tinkering with your toolchain, and try to keep it as neat as possible. Doing random things to it will almost certainly break it. To compile software, all you really need is to...[LIST]
[*]Have a clean toolchain.
[*]Take note of the software's dependencies, and be sure your system fulfills them. Often, compile-time errors relate to unmet dependencies.
[*]Follow the instructions (which normally consist of something like **./configure && make && sudo make install**)
[/LIST]It can be very difficult to sort out a toolchain, once it's gotten tangled up in a mess. It's often easier to reinstall it (or the entire OS) from scratch.

> **entryname said:**
> Is there any hope of finding any of these in maplin?Personally, I have no respect for Maplin lol. That aside, you seem to be preoccupied by that hardware list ... it's just a reference ... something you might find handy once you've already chosen a wireless card, so you can double-check that it's likely to work with your Linux before you buy it. If I were you, I'd ignore it completely, until I'd been round to my local shop to see what's cheap/available/recommended.

> **entryname said:**
> I don't know how much speed I'm losing...I assume you're talking about a wired network connection. If that's true, there's simply no comparison between it and the wireless option. If it's convenient to do so, you should _always_ wire up a box...[LIST]
[*]It's vastly more secure
[*]It's more reliable
[*]It's less hassle
[*]It's significantly faster
[/LIST]A typical ethernet connection operates at a theoretical maximum of either 100 or 1,000Mbps. 802.11b operates at 11Mbps (in perfect conditions), and 802.11g at 54. No matter how low-quality a wired connection might be, it's not likely to be anything like as slow as a high-quality wireless one.

Anyhow, I hope something here helps.

**Edit:** Yikes... it looks like I'm just as waffly as you two hehe.

---

### Post by entryname on 2008-05-05
OK I've noted the card listed in Maplin, and there are two in my local store. A poster on the Maplin site says it does work with Ubuntu although you have to compile the driver yourself. As my success rate at that is absolutely nil, I'm not optimistic but may try it anyway as it's not expensive. The Maplin code is A02CG. 

The additions to compiler packages were because it didn't work as installed from the disk. I installed libc6-dev at one point as it seemed to be required, and that did help, but still not to the point that compiling worked. Call my cynical but I will be surprised if anything ever compiles successfully on this machine.

I can't unfortunately wire both PCs to the ethernet sockets on the hub. One is upstairs and one down. I gather cabling ethernet is not for beginners. That seems to leave ethernet via mains. Although that's possible it's horribly expensive. If I was going to do that it would be cheaper to buy another second hand PC that had wireless on it and install Ubuntu on that.

So unfortunately it doesn't seem possible to escape wireless. The hub does wireless anyway. It seems to expect to be running 24 hours. I don't think speed is an issue since the wireless link (between the hub and the laptop) runs vastly faster than the broadband - 48 to 54meg, whereas the hub reports the speed of the broadband as around 3.5meg max (and it therefore doesn't exceed 3meg). Actual download speeds as reported during downloads are around 300-400kbytes.

Oh the other comment about why am I running a geriatric Ubuntu - because it's on a geriatric machine. At the time I wanted a very plain simple linux to avoid straining the poor thing. After several tries Ubuntu was the one that worked. I picked it because it had a good reputation and the available free version wasn't erm crippleware or private use only. As it is now, upgrading has upgraded open office. It still runs but very very slowly. Upgrading software can be bad news.

Just for the record, with things as they are now, Ubuntu is quite happy with broadband, whereas windows XP, running on a much newer machine, for reasons that are not clear is freezing about every three hours on average, and that started about the time I got broadband.

btw ref long bits of writing - someone at work told someone else it was better to ring me in response to emails, as if he replied to war and peace, "you're obviously going to get war and peace volume 2!" :lolflag:

---

### Post by entryname on 2008-05-23
Well here I am again with another installment :-(

Fitted said card. That is to say Sitecom Wireness Network PCI Card 54g Turbo 802.11g, 2.4Ghz WL-171. Operating system recognises it but can't actually get web pages over it. 

It is said I need to install from [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads") but that really leaves me none the wiser. The bit at the top leads to weird instructions about servers. I installed GIT and Cogito from synaptic but the rest didn't seem to make any sense. All I want is a wireless driver.

The bits underneath, I wasn't sure which I wanted, but as the box says 2.4Ghz I went for 2400. Unfortunately it doesn't appear to actually be a package, it's some sort of repository list.

I then tried the utilities package listed on the same page. It came as absolutely no surprise at all that it wouldn't compile. First of all it didn't understand being told to configure. On being told to configure.sh it then objected that I didn't have GTK+ 2.6. On installing some development packages for that from synaptic, it then objected something like it hadn't found any kernel sources and the kernel in the header wasn't the same as my kernel.

So is there any hope of this thing ever working, or have I merely spent 20 quid to prove that there's no point doing anything that requires software that isn't on Synaptic?

That is, I was right to start with - the hardware list has no value unless you are a very highly skilled computer expert? ?

---

### Post by faizal123 on 2008-05-25
I was able to make it work the sitecom wl-171. (ubuntu 8.0.4) 
It defaults to being recognised by rt61pci module. Since the card gives me problems (dying connection with router, slow) I tried the original windows xp drivers from the cd as well. (still no stable card though...)

Here is what I did:
prevent rt61pci from being loaded:
edit /etc/modprobe.d/blacklist
===== add ====
blacklist rt61pci
blacklist rt2x00pci
blacklist rt2x00lib

install ndiswrapper-common / ndiswrapper-utils
sudo apt-get install ndiswrapper-common

cd to windows xp driver folder on cd
sudo ndiswrapper -i Rt61.INF 

(this will copy the driver to /etc/ndiswrapper)

add ndiswrapper to the /etc/modules on a line of it's own so it gets loaded on startup. (check with dmesg if your wlan0 card is recognized through ndiswrapper).

add to /etc/rc.local  (before "exit 0" ofcourse)
/etc/init.d/networking restart

I can now internet etc but the card is still not working to satisfaction.
Will update this post whenever I get it to really work..

Faizal Abdoelrahman

---

