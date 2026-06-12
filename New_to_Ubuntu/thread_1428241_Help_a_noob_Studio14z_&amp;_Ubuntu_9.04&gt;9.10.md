---
title: "Help a noob: Studio14z &amp; Ubuntu 9.04&gt;9.10"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by linuxscrub9000 on 2010-03-12
[SIZE=2]Hai guys!

I'm on my third day of being a Linux user and am loving it! But, I am having a problem. Please, if it isn't too much to ask, give me a hand... Google hasn't been able to solve it (I'm a scrub.)

Ok, so, in a nutshell I have a new Studio 14z from DELL, specs as follows:[/SIZE]

[SIZE=1]1[/SIZE][SIZE=1]224-4967[/SIZE][SIZE=1]Studio 14z Notebook (Studio   1440)

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]317-1443[/SIZE][SIZE=1]Intel Core 2 Duo T6600, 2.2GHz, 800Mhz, 2M L2 Cache

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]317-1446[/SIZE][SIZE=1]3GB, DDR3, 1066MHZ, 1 SoDIMM

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]330-3607[/SIZE][SIZE=1]BACK-LIT KEYBOARD

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]320-7907[/SIZE][SIZE=1]14..0  HD TL LED Display

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]421-0258[/SIZE][SIZE=1]Facial Recognition SW

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]320-7909[/SIZE][SIZE=1]NVIDIA MCP79MX - merchandised as "NVIDIA

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]341-8865[/SIZE][SIZE=1]250G HARD DRIVE, 5400RPM

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]313-7572[/SIZE][SIZE=1]Black IMR with Black Utrim

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]421-1737[/SIZE][SIZE=1]Genuine Windows 7 Home Premium, 64bit, English

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]420-7938[/SIZE][SIZE=1]Dell Connect 2.1

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]421-0187[/SIZE][SIZE=1]Dell Support Center Software  64 Bit 2.0

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]420-9100[/SIZE][SIZE=1]Dell Dock Consumer

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]421-1193[/SIZE][SIZE=1]Download Store Links

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]420-6576[/SIZE][SIZE=1]DELL WELCOME,Software         Dimension/Inspiron

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]420-9691[/SIZE][SIZE=1]DataSafe Local BackUp 2.0     Basic

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]420-6436[/SIZE][SIZE=1]PC-Restore, Dim/Insp

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]421-0323[/SIZE][SIZE=1]Windows Live Search,Multiple  User Interface

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]330-6222[/SIZE][SIZE=1]Windows 7 Label

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]421-2086[/SIZE][SIZE=1]eBay Webslice

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]410-1883[/SIZE][SIZE=1]ADOBE READER 9.0 MULTI-       LANGUAGE

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]313-4783[/SIZE][SIZE=1]Integrated High Definition    Audio 2.2

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]430-2929[/SIZE][SIZE=1]Dell Wireless 1397 802.11g    Half Mini Card

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]410-2184[/SIZE][SIZE=1]McAfee Sapphire MUI, 30 Day

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]312-0878[/SIZE][SIZE=1]56 WHR 6-CELL LION PRIM BATT

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]412-1397[/SIZE][SIZE=1]No Productivity Software      requested

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]960-2780[/SIZE][SIZE=1]Dell Limited Hardware Warranty 7X24 Technical Support, Initial Year

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]950-9057[/SIZE][SIZE=1]No Warranty, Year 2 and 3[/SIZE][SIZE=1]1[/SIZE][SIZE=1]994-0170[/SIZE][SIZE=1]Mail-in Service after Remote Diagnosis , Initial Year

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]994-4037[/SIZE][SIZE=1]Dell Limited Hardware Warranty Plus Service, Initial Year

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]313-8349[/SIZE][SIZE=1]No WWAN Option, Inspiron

[/SIZE][SIZE=1]1[/SIZE][SIZE=1]330-5125[/SIZE][SIZE=1]Intel Core 2 Duo Label[/SIZE][SIZE=1]

[/SIZE][SIZE=2]I installed a copy of 9.04 desktop using a USB flash drive. I tried with 9.10 but either it locked up during installation, or, would install without wireless drivers. And, wireless is the only way I can connect to the web.

[/SIZE][SIZE=2]No problems with the 9.04 installation, everything except the internal microphone was working out of the box... but for some reason I couldn't use the newest NVIDIA accelerated graphics driver (version 180) and had to settle for using 173.[/SIZE]

[SIZE=2]Apparently this is causing some conflict with Wine for running a game. I got it going OK but some of the graphic options were glitchy... not a big deal. Anyway, I read that by upgrading to 9.10 I could probably solve both of these problems... I need the microphone, so I clicked into the update manager and did so.

No wireless, again. Reformatted and reinstalled to 9.04 so I could post this, and, as per, [http://www.linlap.com/wiki/dell+studio+14z](http://www.linlap.com/wiki/dell+studio+14z), I have downloaded the hybrid drivers.

I also downloaded RPM Fusion to get the kmod-wl, but it's saying it's for Fedora.. will this be compadible?

In the two days I've had this I've worked with a few tar balls and am going to try manually configuring my wireless card after 9.04 updates to 9.10. If that doesn't work I'll reinstall 9.04 and eagerly await someones advice.[/SIZE]

[SIZE=2]Oh, and for some reason Thunderbird did not want to work with 9.04. It would load, and even get mail, sometiems, but it would sort of freeze and not display things correct. Never crashed though.

[/SIZE]

---

### Post by linuxscrub9000 on 2010-03-12
Oh, one other thing is perplexing me.

This box has a 250GB HDD. When installing I select Linux to use the whole thing.

Filesystem properties tells me that there is 3.7GB of data on the drive with 206.9GB free. Where's the other 40GB?

---

### Post by linuxscrub9000 on 2010-03-12
EDIT: Got the wireless working with 9.10 AND the NVIDIA 185 driver AND the internal microphone working when I performed a fresh install of 9.04, upgraded everything in the update manager, and then upgraded to 9.10.

Sorry for wasting your guys time. Loving Linux even more!

...still not understanding the missing GB, there must be a partition I can't see or something.

---

### Post by Hospadar on 2010-03-12
As to 9.10:

You could try installing with the "alternate" cd, which doesn't use a GUI, it tends to be a little more reliable.  I know of a couple machines where the alternate installer worked fine where the regular desktop installer was a no-go (and after installation 9.10 worked fine), so that's what I'd try first.

If it still doesn't work though:

I would just stick with 9.04 if it seems to be working fine, if you want some newer versions of stuff without upgrading all the way to 9.10 you can install the backport repositories.  These contain packages which have been [back]ported from the more recent releases.  Go to System->Administration->Software Sources, on one of the tabs in there you'll find a checkbox for the backport repo, afterwords check for updates.  

Also if the concern is wine, the wine project maintains its own repository which always has the latest versions of wine.  [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

I kind of doubt either of these things will solve your mic issue in 9.04, but it might be better than nothing.

As to your hard disk:
Some of that space is probably the swap partition, and some is probably due to the discrepancy in terms of binary/decimal prefixes:
Most hard drive manufacturers list their disk sizes in SI (Systeme Internationale or some such similar french nonsense ;-) meaning that a gigabyte is 1000^4 bytes, but software tends to report gigabytes in terms of the binary prefix, aka 1024^4.  Long story short, the manufacturer uses the more favorable measurement. [http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)

It's entirely possible also that things got partitioned in a way you didn't expect.  You can take a look at the command line with "sudo fdisk -l", or by installing and running gparted

---

### Post by ubuntpetbe on 2011-09-02
I also had some troubles with ubuntu when running it from an USB stick. You should really try to avoid running ubuntu from a USB stick. Next time run it from a CD.


About your file system properties.
Could you add the whole numbers. The sizes without prefixes.
Then we can see how much is actually in there. And what part is of the binary/decimal stuff.

Here's a calculator:[URL="http://www.dr-lex.be/info-stuff/bytecalc.html"]
http://www.dr-lex.be/info-stuff/bytecalc.html
[/URL]

206.9 + 3.7 = 210.6 GB but it's actually 210.6 GiB
This then becomes: 226.13 GB.
Thus you're only missing: absolute value of (226.13-250)/250 is then 0.09548 or 9.548 %. This difference is 23.87GiB.
That could be your swap partition and some other stuff such as the overhead from the file system I think.



Using binary prefix in calculations with decimal prefix is nonsense.

---

