---
title: "Cant bootup live CD on Win98 laptop"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by sunwatt on 2010-04-03
A friend gave me a Compaq Presario 1600 laptop. Its got Windows 98 installed.

I got to the bios and put the cd rom on the top of the boot order, but it will not bootup with my Ubuntu, or Linux 7 live CD's. Windows98 starts. 

The cd rom works, I put a windows program install cd in there and it installed linksys wifi, so I actually got the laptop online using a linksys pcmcia wifi card.

I also tried to bootup to "removable devices", the Compaq has 1 USB port, but Windows failed to bootup to the live Linux Mint 7 memory stick, and then Windows tried to find a driver online, but failed.

So I cant even use the USB port except it will work with a extrnal mouse, leyboard, and monitor.

How can I make this 2000 or 2001 Windows 98 laptop bootup, and allow me to install Ubuntu, or Linux Mint?

Thanks!

Jim

---

### Post by howefield on 2010-04-03
If it has Windows 98 on it, chances are it isn't good enough to run a current Ubuntu.

What are the specifications of the laptop ?

---

### Post by Sir Jasper on 2010-04-03
Hi,

If you have at least 128 MB RAM  burning a Puppy Linux 4.3.1 CD may be ideal.

If you have only 64 MB RAM then perhaps consider Damn Small Linux (DSL).

My regards

---

### Post by oldfred on 2010-04-03
A couple of years ago I got an old Toshiba with only 128MB. The version of Ubuntu back then did install but it took many hours. It then took many hours to update. (I  think it was using a lot of swap). It was slow.

I then tried several others including puppy & DSL. They installed fine and worked ok but I had to use a USB to ethernet dongle and that did not work. I knew the dongle worked since Ubuntu used it for the updates. It also worked with several of the repair type installs. It turned out only certain newer kernels worked with the dongle and I found Zenwalk was smaller and just had released a new version that worked. Then they updated something and it quit on me & I have not gone back to fix. It was a good experience installing a variety of distributions.

---

### Post by lisati on 2010-04-03
My older desktop sometimes has trouble booting directly from CD, even though the BIOS supports booting from CD - the Win98SE disk that came with it seems to boot ok, but most of the other bootable CDs I've checked out don't. Among other things, the CD-ROM isn't the original. 

The solution I eventually used was to create a boot floppy of [Smart Boot Manager]("http://sourceforge.net/projects/btmgr/files/btmgr/3.7-1/")

Which distro to use is another story: I ended up putting a command-line version of Ubuntu 6.06 on my old machine, which doesn't seem to have enough RAM for the more usual GUIs.
Good luck getting the laptop working.

---

### Post by sunwatt on 2010-04-03
> **howefield said:**
> If it has Windows 98 on it, chances are it isn't good enough to run a current Ubuntu.

What are the specifications of the laptop ?

Its Win98SE Intel Celeron processor, 56MB of ram.

Jim

---

### Post by lisati on 2010-04-03
> **sunwatt said:**
> Its Win98SE Intel Celeron processor, 56MB of ram.

Jim

Puppy Linux might be worth checking. It ran on my old 133MHz Win98SE machine which has 64Mb RAM but was a bit slow for my liking.

---

### Post by roger_1960 on 2010-04-03
Hi

I dont think puppy will run with that little ram

You could try Tinycore.  Or, get some more RAM, its probably cheap for that machine.  Puppy (which is great) needs 64Mb, ubuntu really needs 256Mb.

---

### Post by mal205 on 2010-04-03
56mb may not be enough to be able to boot the Ubuntu live CD.

The minimum requirements are here:[ https://help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")

You could try the absolute minimum Ubuntu install, which is listed at the bottom of the page. It only needs 48mb of memory. But you'll need the alternate install CD (which you can get from any of the Ubuntu download sites). And it'll be command line only. I doubt that's what your looking for.

---

### Post by jim Kane on 2010-04-03
> **sunwatt said:**
> Its Win98SE Intel Celeron processor, 56MB of ram.

Jim

                                       that really is not enough ram for any current GUI based Linux disto to work on.
    [LEFT]I have a Toshiba with 64Mb ram and 133 processor it will just about run DSL and Puppy but quite honestly win98 runs much faster. 



JK
[/LEFT]

---

### Post by sunwatt on 2010-04-03
> **jim Kane said:**
> that really is not enough ram for any current GUI based Linux disto to work on.
    [LEFT]I have a Toshiba with 64Mb ram and 133 processor it will just about run DSL and Puppy but quite honestly win98 runs much faster. 



JK
[/LEFT]


Thanks folks!  I get the picture now, when I saw that I pretty much knew it was too little. 

This forum is great, even when its bad news.

Jim

---

