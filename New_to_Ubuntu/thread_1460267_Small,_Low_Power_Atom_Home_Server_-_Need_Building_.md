---
title: "Small, Low Power Atom Home Server - Need Building Advice"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by Kestrel87 on 2010-04-22
Howdy Everyone!  I'm new to the forums, and relatively new to Ubuntu, so I figured I'd start in the Absolute Beginner Talk forum before moving up.

I currently have an old PC running Ubuntu Server 9.10 for very simple tasks, mainly a file, print, and backup server (NAS).  However, it takes up way too much room and pulls a lot of power, so I'd like to build a smaller, more energy efficient server.  The problem is, I'm not used to building servers, let alone servers using this form factor.  I've built several gaming PCs in the past, but this is a slightly different beast.  So I'd like your input.

Here is what I've come up with so far, starting with the things I know for sure:
[LIST]
[*]An [Intel Atom D510 board]("http://www.intel.com/products/desktop/motherboards/D510MO/D510MO-overview.htm").  Mini-ITX form factor, energy efficient, perfect for what I'll be needing it for.
[*]1GB (maybe 2GB) DDR2-800 RAM.
[*]Two [3.5" 1TB WD Green hard drives]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136490") in a software RAID 1 (mirror) array.  The case I'm considering (see below) has only one 5.25" drive slot and one 3.5" drive slot.  I plan on using the 5.25" drive slot, along with [brackets like these]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811993004"), to hold one of the two 3.5" hard drives.
[/LIST]

Now the things I'm not so sure about:
[LIST]
[*]This [Lian-Li case]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811112227").
[*]The Intel board supports a [USB embedded flash drive like these]("http://www.logicsupply.com/categories/flash_storage/usb_flash_modules").  I know very little about them, but I was thinking about installing Ubuntu Server 10.04 on to a 2GB or 4GB version, thus allowing the entirety of the two drives to be devoted to backup and file storage.  Might this work with Ubuntu Server 10.04?  I suppose if it can be installed on to a Live USB drive, it should work, but as I said, I have zero experience with these.
[*]The Lian-Li case does not come with a power supply, so I would need to buy a small (roughly 100W-150W) power supply.  Again, here is where my gaming PC building experience proves worthless.  Usually I go with some 450W-500W monster, but that's grossly inappropriate here, as the system should only be pulling about 60W-80W under peak loads.  Unfortunately, it's hard to find an ATX PSU that would fit in that case but has a maximum power rating of under 150W and comes with a 24 pin connector that fits the Intel board.  There are some [non-ATX kits]("http://www.logicsupply.com/categories/power_supplies/power_kits") out there, but I'm not that fond of leaving a big hole where the PSU should go.  So, how inefficient would a 200W PSU be for this application, considering it'd be amazing if the system could use even half of that current?  And are there any ATX-sized power supplies out there that only produce, say, 100W?
[/LIST]

Thank you so much in advance!  I greatly appreciate those of you who take the time to read through my dilemma and offer your advice!  I look forward to your replies!

---

### Post by tgalati4 on 2010-04-22
A good-quality 200-watt power supply is probably the way to go.  If it has a power factor of 98%, then it's only rejecting 2% as heat, that's ~4 watts at full load.  Most of the time you will be drawing ~15 watts.

The bigger power supply will give you more power overhead, more surge protection, and probably more life than a 100-watt supply.  I presume that you will be running this 24/7.  Capacitors are the weak point in power supplies.  I presume that you can get better (higher-voltage) capacitors in a 200-watt supply.

I've used embedded flash drives.  They do tend to fail because Ubuntu is not optimized to reduce writes on flash.  With enough RAM, you could simply run from a Live-CD or respin your own live-cd with just the services that you want.  It makes upgrading a pain.  With a long-term-support (LTS) you can expect a lot of updates over 5 years.  Just make a small partition on one of your green drives.  Server drives tend to spin 24/7 anyway because of the logging and cron jobs and port polling.  If you set up tracks ([http://getontracks.org](http://getontracks.org)) or drupal ([http://drupal.org](http://drupal.org)) you will probably need a 20 GB partition for root.  You can certainly slim down the boot partition, but it's a pain to grow it again as you add services.

Back up your boot partition every now and then so you have a way to restore quickly in case of drive failure.

Share your experiences after the build so we know what works and what doesn't.  Get yourself a kill-a-watt meter so you can measure the power consumption of the final system.

I rescued a a couple of curbside computers (1 GHz celeron, and 600 MHz celeron).  Hardy server runs fine on them.  One uses 46 watts, the other 36 watts.  Cost--$60/year to run the 1 GHz machine--$0.13 kwh in Los Angeles.

---

### Post by Kestrel87 on 2010-04-22
Thanks so much for the speedy reply!  I will likely do exactly that: use a 200W power supply (or maybe even a little larger, if there's no major downside) and not use the embedded flash drive.  Assuming I don't get any more replies, I'll probably order the parts and build it in the coming weeks.  I'll be sure to report back and tell you how it goes!

Thank you again!

---

### Post by mal1958 on 2010-04-22
If you go with a 200 watt like tgalati4 says, or go higher, I would recommend that you get an extra fan or two for the box.  Heat build up has caused more headaches to comp users then beer hangovers.  Just my two cents worth here folks.

Mike

---

### Post by capscrew on 2010-04-23
I have thought about this lately myself.  I would go another way with the PSU.  I would use an external PSU (brick).  The case you have selected uses passive cooling (heat sinks) rather than fans if I'm not mistaken. 

Most of the internal heat on a Atom CPU device is from the PSU and the HDD.  The two things you should investigate more.  Intel makes SSD's that are reliable (to a point) and external PSU's are ubiquitous.

---

### Post by 3rdalbum on 2010-04-23
I'd echo the sentiment to NOT run Ubuntu 24/7 from a flash drive. I did for a while and it destroyed the flash drive rather quickly. You'd probably get the same thing with any operating system, I suspect.

I didn't know Lian Li did Mini-ITX cases, but Aywun does. You should be able to coax two 3.5 inch hard drives into at least one of their models; mine has a space for a 3.5 inch, a floppy drive and a DVD burner.

Some Aywun cases have a power supply included too. I didn't really have much faith in this PSU, but it's been running almost continuously for a year without issues.

---

### Post by oldfred on 2010-04-23
I think some of these links may be older but related:

Server with extras
[http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3)
[http://www.amahi.org/](http://www.amahi.org/)

Thread on servers
[http://ubuntuforums.org/archive/index.php/t-1286445.html](http://ubuntuforums.org/archive/index.php/t-1286445.html)

---

### Post by AlexanderDGreat on 2010-04-28
To everyone reading and patronizing this thread BEFORE buying, read this SCARY performance of Ubuntu with Intel Atom D510...

[http://ubuntuforums.org/showthread.php?t=1395838]("http://ubuntuforums.org/showthread.php?t=1395838")

You've been warned. :)

---

### Post by SixedUp on 2010-04-30
I did something very similar to this back in the days of Fiesty Fawn, so 3 years ago now. I did a lot of metal-bashing to adapt an existing case to my needs (which you probably dont want to do!), but otherwise our thoughts were/are similar. In the end I decided against booting from flash because of the complexity of adapting Ubuntu to limit writes to the flash drive (which would kill it fairly quickly). 

Technology has moved on of course, so you ought to be able to build something with higher performance and lower power consumption than I achieved, but you can see some info on what I did here in case it's useful:

[http://appleby.is-a-geek.net/server/index.html](http://appleby.is-a-geek.net/server/index.html)

BTW, I'm using an external power brick and a PicoPSU, which works *really* well.

Good luck.

---

### Post by Paqman on 2010-04-30
Mini-itx.com is a really good resource for building mini-itx systems, they detail exactly what options you've got for various cases. Even if you buy from somewhere else, it's worth checking out.

---

### Post by bihe on 2010-05-18
Have you tested WOL with this configuration? I want to build a D510MO base NAS and would like to use WOL.

---

### Post by jap1968 on 2010-05-28
All I can say is that I am writing this post on a [64 bit Ubuntu 10.04 running on a Intel D510 MO]("http://ubuntuforums.org/showpost.php?p=9374835&postcount=17"). Everything works fine and I have finally achieved a silent computer with a very low power consumption.

> **AlexanderDGreat said:**
> To everyone reading and patronizing this thread BEFORE buying, read this SCARY performance of Ubuntu with Intel Atom D510...

[http://ubuntuforums.org/showthread.php?t=1395838]("http://ubuntuforums.org/showthread.php?t=1395838")

You've been warned. :)

---

