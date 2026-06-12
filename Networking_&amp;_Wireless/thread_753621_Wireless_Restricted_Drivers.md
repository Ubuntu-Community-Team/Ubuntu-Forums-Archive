---
title: "Wireless Restricted Drivers"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by Sup3rkirby on 2008-04-12
Call me a noob here, but I'm just not sure I understand this.

In my particular case, my wireless card uses a 'restricted driver' and my wireless internet on my laptop doesn't work.

In a more general sense though, what are 'restricted drivers' and what should I know about them?  What do I need to do about them and how can I get devices that use them working?

I am really syched about getting back into linux and going strong with Kubuntu 8.04, but of course a computer becomes almost useless when i don't have any internet access.  I'm basically stuck with the default everything, and that is no fun.  No downloads of games, updates, etc. as well as no internet browsing and things like youtube....

Anyways, just trying to figure this out.  The topics I read for wireless and restricted drivers simply talked about how they couldn't get their wireless to work and they noted they had restricted drivers, but even one topic said something about download something that made it work....


Could I just temporarily run an ethernet cable to my laptop to get internet to download something that will fix my restricted wireless card driver problem?


Thanks in advance.

---

### Post by kutjara on 2008-04-12
> **Sup3rkirby said:**
> Call me a noob here, but I'm just not sure I understand this.

In my particular case, my wireless card uses a 'restricted driver' and my wireless internet on my laptop doesn't work.

In a more general sense though, what are 'restricted drivers' and what should I know about them?  What do I need to do about them and how can I get devices that use them working?

I am really syched about getting back into linux and going strong with Kubuntu 8.04, but of course a computer becomes almost useless when i don't have any internet access.  I'm basically stuck with the default everything, and that is no fun.  No downloads of games, updates, etc. as well as no internet browsing and things like youtube....

Anyways, just trying to figure this out.  The topics I read for wireless and restricted drivers simply talked about how they couldn't get their wireless to work and they noted they had restricted drivers, but even one topic said something about download something that made it work....


Could I just temporarily run an ethernet cable to my laptop to get internet to download something that will fix my restricted wireless card driver problem?


Thanks in advance.

Wireless is still one of the areas in which Linux could use some improvement, largely because the wireless card manufacturers guard their drivers as if they were precious jewelery. This makes it difficult for the open source community to break open proprietary driver software and see how it works, which, in turn, makes it difficult to get it working with Linux.

There are basically three solutions that the OS community has come up with for dealing with this problem. No single solution works with all wireless cards, so you have to read around a bit on ther forums to see which one is preferred for your card. The three solutions are:

(1) Restricted drivers. These are proprietary drivers, often created by the card manufacturer itself, which work in Linux, but are not open source (hence the "restricted" label). If you're lucky enough to have a wireless card for which there is a restricted driver, well getting wireless networking working couldn't be easier. It'll all happen automagically. Unfortunately, very few cards work with the restricted drivers. Even worse, Ubuntu will often mistakenly identify your card as being compatible with a restricted driver, so you'll be in the perplexing position of seemingly having a working setup, but being unable to connect to anything.

(2) Ndiswrapper. This is a piece of software that "wraps around" the Windows drivers for your wireless card, and translates the inputs and outputs of the card between Linux and the Windows driver software. It seems to work best with cards which use a Broadcom chipset. To use this, you have to download the latest Ndiswrapper packages, and have access to the Windows drivers for your wireless card.

(3) Madwifi. This software attempts to recreate the drivers for your wireless card directly in a form that works with Linux. Madwifi tends to work best with cards which use an Atheros chipset.

Another piece of software, called fwcutter, works with other (usually Broadcom cards).

The best thing to do is search on the forums for some of the HOWTOs that have been written, detailing how to get various types of wireless cards working.

This all seems terribly complicated, I know, but the HOWTOs do a good job of simplifying things considerably.

---

### Post by kevdog on 2008-04-12
madwifi is part of the restricted drivers as of the 7.10 release -- just an fyi.

---

### Post by kutjara on 2008-04-12
> **kevdog said:**
> madwifi is part of the restricted drivers as of the 7.10 release -- just an fyi.

Interesting, but Hardy didn't install Madwif by default on my laptop with an Atheros wifi card. Instead, I got an "Atheros" restricted driver that did nothing, so I had to compile and install the Madwifi one myself. Presumably, there is some prioritization scheme Ubuntu uses in deciding which restricted driver is most appropriate. Unfortunately, it got it wrong with me.

---

### Post by kevdog on 2008-04-12
Possibly your newer version of Madwifi (since you compiled a more recent version) supports a wider array of atheros chipsets than the older version that was contained in the restricted drivers package.  I always prefer to use the svn compiled sources personally!

---

### Post by Sup3rkirby on 2008-04-12
madwifi is actually something I would like to try.  I'll probably do this tomorrow as I would need to reboot in order to do this, but yes, my laptop is using an 'Atheros' chipset and I was notified of the 'restricted drivers' thing but since I still couldn't use my wireless card, I was very confused about what 'restricted drivers' really were and why they didn't work when they were enabled.

So if I'm using 8.04 I would need to get and compile madwifi myself to use it?

---

### Post by kutjara on 2008-04-12
> **kevdog said:**
> Possibly your newer version of Madwifi (since you compiled a more recent version) supports a wider array of atheros chipsets than the older version that was contained in the restricted drivers package.  I always prefer to use the svn compiled sources personally!

That certainly sounds reasonable.

I'm hoping that Mr. Shuttleworth's announcement about Indolent Iguana (or whatever it's called), saying that it was going to be focused on "mobile computing" and wireless ubiquity, means that some big effort is going to go into streamlining the whole wifi experience. It's the one area in which Linux still manages to send me straight to the nearest wall, for a prolonged cranial-interfacing session.

---

### Post by kevdog on 2008-04-12
The restricted drivers are a bunch of drivers that were put into a package when the developers created the ubuntu kernel.  Some of the drivers were contained in the default vanilla kernel (such as b44 or bcm43xx) while others the ubuntu developers added to the generic vanilla kernel (madwifi, nvdia graphics drivers, etc.).  If you ever compile your own kernel, you will become quickly familar with what comes from the vanilla linux kernel, and then what comes from the kernel the ubuntu developers modified. 

Yes madwifi is released as source code.  You need to download, compile and install the source code which takes less than 1 minute if you have ever done it before.  If you can read instructions, your first time might take like 10-20 minutes just to know what the steps are.

---

