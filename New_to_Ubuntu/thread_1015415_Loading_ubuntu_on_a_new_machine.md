---
title: "Loading ubuntu on a new machine?"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by iceman09 on 2008-12-18
Hi, has anyone bought a new computer and just loaded ubuntu right on it out of the box? Does it void the warranty not having windows on it? 
I've looked at system 76 and Dell. I dont know anything about system 76 but I have had Dell's and even though they offer Ubuntu on new computers the prices aren't the best but you can always find a deal on a laptop with windows on it. Seems wrong doesn't it?

---

### Post by Kellemora on 2008-12-18
Hi Iceman

I guess it depends upon where you shop!

I can get the same machine with No OS, XP-Pro for 120 bucks more or The Ulimate Spyware OS Vista for whatever.

A brand spanking new bare bones computer with 650 watt power supply, a dual core AMD or Intel, your choice, with 2 gigs of Ram is 255 bucks, 2 more gigs is another 40 bucks.  There are 4 Mobo choices he offers, only one of them is a few bucks higher than the rest, but it's geared primarily to Gamers and Winders and can take a quad core too I think.
There are 4 SataII ports on the board and 6 PCI slots.  From there it's whatever hardware you want installed at the price for that particular hardware.
Includes a nice side opening tall tower cabinet.

Other options are Pawn Shops for a late model used computer.  I picked up a Dell OptiPlexGX270 with Doze XP-Pro, pretty well loaded, also 650 watt power supply for like 175 bucks, and an HPpavilian753n for 150 bucks, had Vista on it, so I wiped the hard drive as the first order of business.  It's now my primary Ubuntu machine!  Meaning the one that feeds the monitor "in" my desk.
4 other machines, 3 Ubuntu, feed the monitor on 'top' of the desk through a KVM switch.

Check around, you should find a place that builds computers nice n cheap and not get ripped by the Packaged Computers.  Many only have 2 SataII ports and SUPER CHEAP hardware add-ons that only last a month or two anyhow before they go south.

I use a BackPack brand DVD burner, external, sits on my desk (along with everything else in the world that don't belong up here), hi hi.......

Back home I could have got much better deals than I mentioned above, because I'm still NEW to this town and don't know where the best deals are yet!

TTUL
Gary

---

### Post by dwasifar on 2008-12-18
Hey Iceman,

I've been building my own desktop machines since a 286-12 with 1MB of RAM was considered a speed demon.  Three or four or them have been built since switching to Ubuntu a few years back, so I've definitely installed Ubuntu on new machines.  But there's not a warranty issue there, so I don't think that really answers your question.

However... Earlier this year I bought a Dell XPS M1330 laptop.  This machine is available with Ubuntu preinstalled but the Vista version was cheaper.  So as soon as I took it out of the box, I removed the original hard drive, replaced it with a (faster and larger) blank drive, and installed Ubuntu.  The machine never booted to Vista, but I still have the original untouched drive if I need it for warranty purposes.

---

### Post by pmains on 2008-12-18
Usually, you can request a copy of the pre-loaded OS so that you can do a complete recovery of your system. I had a laptop that I did this with. Wasn't even the original owner -- just went to HP's website and ordered the disks needed to reimage the box the way it originally came.

If you can do that, how do they know if you loaded Linux at one point? Why would they care? The product you ship back to them (which you probably won't do anyway) is identical to the one they shipped to you. No harm done.

Bottom line, I HIGHLY doubt that loading Linux would void the warranty. And, really, what does a 1337 H4x0r like yourself need with a warranty?

---

### Post by pmains on 2008-12-18
Oh, and I loaded Ubuntu on my HP Slimline right out of the box. I was pleasantly surprised by how easy it was. Really, I find it to be much better than setting up partitions, dual-booting -- blah.

---

### Post by dwasifar on 2008-12-18
> **pmains said:**
> Bottom line, I HIGHLY doubt that loading Linux would void the warranty. And, really, what does a 1337 H4x0r like yourself need with a warranty?
When hardware fails on a major manufacturer's machine, the only way you can get them to replace it is to first go through the dumb-*** first-level support techs, who will ask you to try all sorts of obviously irrelevant things.  "My DVD burner is scratching discs."  "Okay, sir, I understand you tell me that your DVD burner is scratching discs.  Have you tried clearing your browser cache?"  This inevitably ends in being instructed to reinstall the operating system.  If you don't jump through those hoops, they will say you refused to perform troubleshooting and decline to replace the part.  And of course, you can't perform the steps if your system does not have the operating system they shipped it with.

---

### Post by donkyhotay on 2008-12-18
I generally build my own systems, the last time I bought a complete computer it was from a local computer recycling shop that pre-installs ubuntu on all their systems and the warranty it comes with assumes you're going to keep linux. (c;

---

### Post by theozzlives on 2008-12-18
My ex-girlfriend had a Gateway that came with Win 98, she put Win XP on it... Gateway restored the OS 4 times before they admitted it was a bad mobo. I have  a Dell laptop that I never gave Vista a chance on. I went straight to Ubuntu. I hope I don't need warranty work, but if they "restore" my system, I got backups.

---

### Post by anim on 2008-12-18
I've had dell fix this laptop two times, the first with hardy and the second with intrepid, both under warranty. They don't give a dang which OS you choose to install on their computers. Dell support won't be entirely helpfull with hardware/software problems, but don't worry we will!

But yeah, bottom line, your hardware in completely safe under warranty with Ubuntu installed on it.

---

### Post by Roadkill Bill on 2008-12-18
First of all, I'm a Mac user, so I'm lost on a PC anyway.

I just ordered a Dell laptop and I want to load Ubuntu on it. It's gonna come with Vista preloaded. So, what is the best way to get rid of the Vista and load Ubuntu?

---

### Post by dwasifar on 2008-12-19
> **Roadkill Bill said:**
> I just ordered a Dell laptop and I want to load Ubuntu on it. It's gonna come with Vista preloaded. So, what is the best way to get rid of the Vista and load Ubuntu?

If you don't care about ever reloading Vista again, and you're not worried that it might cause you support problems (see my previous post about that in this thread), then just boot the machine from an Ubuntu live CD, pick Install, and let it use the whole disk.  Bye-bye Vista, for good.

If you DO think you might want to reinstall Vista at some time in the future, then you have two choices: 

1) Obtain system restore disc(s) from Dell, which I recommend you do right away if you're going to do it, or:

2) Generate your own restore discs from the system itself, if there is a utility provided for that purpose.

Dell puts a system diagnostic utilities partition and a restore partition at the beginning of the drive.  Getting rid of the utilities partition is no big deal; you can usually download a bootable disc image from Dell that contains the same utilities.  If you blow away the restore partition, and you don't have restore discs, and you want to reinstall Vista at some time later for whatever reason, Dell will not help you.  So be prepared.

Actually there is a third choice, if you don't mind a little extra expense:

3) Put in a blank hard drive as soon as you take the machine out of the shipping box, and set the Vista drive aside.  This makes sense if you wanted a bigger and/or faster drive without paying premium Dell upgrade prices for it.

BTW, if you install the Dell remix of Ubuntu (available [here]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04")), it will set up a restore partition as part of the installation, plus a few Dell tweaks to support their specific hardware.  However, it does not include the commercial DVD player app you would get if you bought preinstalled Ubuntu from Dell; the latest available version is Hardy; and only the 32-bit version is available.

---

