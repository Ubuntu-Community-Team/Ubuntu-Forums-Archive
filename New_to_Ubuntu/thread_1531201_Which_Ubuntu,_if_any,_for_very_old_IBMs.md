---
title: "Which Ubuntu, if any, for very old IBMs?"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by murphyac on 2010-07-14
I have two IBM PC750s PCI/Microchannel.
One has an AMD K6 II, 400 MHz overdrive processor and 192 Mb RAM (not upgradeable) and about 8 Gb hard disk space for installation.
The other has an Intel 233 MHz overdrive processor, 192 Mb RAM (again, not upgradeable) and will have more than 8 Gb on one disk and a whole 9 Gb disk for installation.

Both these computers can run Windows 98 SE.  Both have 3Com, 3C529 network cards, and I'd like to network them to my Dell Dimension 4700 (Windows XP/Ubuntu 10.04 LTS) through my Linksys router.

My question:  is there any form of Ubuntu that will run on these computers?  Can I possibly do a Wubi installation, or do the low memory and old processors preclude this?

I'd be grateful for any help the Ubuntu community can give me.
Angela C. Murphy

---

### Post by mike555 on 2010-07-14
Lubuntu might run on them ,but Puppy Linux  (the one based on Lucid) might run better ..
[http://www.murga-linux.com/puppy/viewtopic.php?t=53897](http://www.murga-linux.com/puppy/viewtopic.php?t=53897)

---

### Post by lighth0use on 2010-07-14
Lubuntu uses about 72mb of ram, but I had issues with it detecting some of my hardware. I say stick with Ubuntu and use a lightweight WM.

Try installing the minimal iso and then choosing a light wm, like icewm or openbox. That way it will be a clean slate and shouldn't have too much "fat".

---

### Post by Jerry N on 2010-07-14
I had some computers with specs like that (I think there are still a couple buried under the electronics bench) and I didn't find any version of Ubuntu that worked well enough to suit me, not nearly as well as Win 98SE or Windows 2000.  I tried a bunch of the so-called "light" versions of Linux and most of them performed poorly also.  Damn Small Linux (still available, I think, but all development has ended) worked fairly well but printing was a real kluge and it might or might not work with your network adapters (it worked with mine).  Puppy Linux should work adequately but I had trouble with printing there too.  I haven't tried Puppy 5 (based on Lucid Lynx) and I should dig out the old Pentium 233 and give it a try.

Jerry

---

### Post by spcwingo on 2010-07-14
Slitaz would be perfect for those machines.  Here's a link to their site:

[http://www.slitaz.org/en/]("http://www.slitaz.org/en/")

---

### Post by Jerry N on 2010-07-15
Followup on my previous comments:  I ran the Puppy 5.0.1 Live CD on my old Pentium 233 with 256mb RAM this evening.  The boot time was very long and the performance was unaceptable.  It did find the network adapter.  I think I will try an earlier version of Puppy, probably 4.3.1, tomorrow.  Puppy 5.0.1 on this computer, even running in RAM, is far far slower than Windows 2000 SP3.  I have several hard drives I can plug in so I will investigate this further as I really expected more out of Puppy.  I had Xubuntu 6.06.1 running on this class of computer some time back and felt that its performance was minimally acceptable but I was never able to get it to print.  

Jerry

---

### Post by egalvan on 2010-07-15
A few (personal) observations...

Software:
TinyCore Linux is another distro that uses little RAM.
website:
[http://www.tinycorelinux.com/](http://www.tinycorelinux.com/)

a quote from the FAQ..

[I]What are the minimum requirements?

An **absolute minimum of RAM is 48mb**.
 TC won't boot with anything less, no matter how many terabytes of swap you have.
[COLOR="Red"]Microcore runs with 36mb of ram[/COLOR].
The **minimum cpu is i486DX** (486 with a math processor).

[B]A recommended configuration:
Pentium 2 or better, 128mb of ram + some swap [/B][/I]

It's not Ubuntu.

You could also try a Command Line version of Ubuntu.


Hardware:
192M RAM is a severe limit for modern graphical Linux.

The K6-II is a far better core than the Pentium I.

Drive space is limited, but this is trivial to fix...
use storage on the "server". The 100Mb network is faster than the ide channels on those older machines (ATA-33, I believe)

In fact, depending on the power of the Dell 4700, you could even run these as terminals, using the LTSP packages 
( Linux Terminal Server Project )
The Edubuntu version has all the packages and instructions you will need.


But first...
What is it you are trying to do with this set-up?
Learn something?
Solve some specific problem?
Solve some generic problem?
Have fun with Linux?

---

### Post by Jerry N on 2010-07-15
egalvan:  It is my understanding that Tinycore comes from the original developer of Damn Small Linux and that there will be no future development of DSL.  I just downloaded the latest version of Tinycore since I am still looking for ways to utilize really old PCs.  This is just for fun, of course;)

---

### Post by gr4nf on 2010-07-15
If you are already used to the ubuntu style package manager, installing debian from floppy would work pretty well, so long as you have a decent connection speed.

---

### Post by bodhi.zazen on 2010-07-15
> **spcwingo said:**
> Slitaz would be perfect for those machines.  Here's a link to their site:

[http://www.slitaz.org/en/](http://www.slitaz.org/en/)

+1 slitaz

If you wish to stay with Ubuntu, do a minimal install and install small applications (gedit rather then OpenOffice) and only applications you need (gnome or XFCE rather then ubuntu-desktop or xubuntu-desktop).

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Results are very similar to what can be achieved with a minimal Debian or Arch install.

---

### Post by SeePU on 2010-07-15
AVOID Lubuntu...unless you want frustration and stress... horrible "release."

---

### Post by Singlebbl on 2010-07-15
> **murphyac said:**
> 
One has an AMD K6 II, 400 MHz overdrive processor and 192 Mb RAM (not upgradeable) and about 8 Gb hard disk space for installation.
 
The other has an Intel 233 MHz overdrive processor, 192 Mb RAM (again, not upgradeable) and will have more than 8 Gb on one disk and a whole 9 Gb disk for installation.
 
From my recent experience, neither of these systems are going to cut it with full 10.04 or Lubuntu or Puppy or the 10.04 text based alternate installer. 
 
I had a '98 Aptiva 400 MHz, 192 Mb RAM, 8 Gb hard drive and all of those distros failed with drive errors. It was not the drive ... Drivescrubber cleaned it w/o any problems and I used the full 10.04 live CD to install on my new "sandbox", a Dell 4600 that I "purloined" from my daughter. 
 
For reference, one of my friends is able to run full 10.04 on a 800Mhz AMD with 768M ram. 
 
Don't know what your finances are, but you can get real decent refurb systems from places like buy.com for less than $200. It will be well worth the cost in terms of your time, energy, and mental health.

---

### Post by Cam! on 2010-07-15
Honestly, it would be a lot easier if you just shelled out $200 for a netbook, and then put Ubuntu on it.

---

### Post by Jerry N on 2010-07-15
> **Cam! said:**
> Honestly, it would be a lot easier if you just shelled out $200 for a netbook, and then put Ubuntu on it.

An old IBM Aptiva I was playing had a mini-ATX compatible hardware layout so I installed a low cost MB and dual core celeron.  I already had an ATX compatible power supply and it did take a little surgery to mount it.  Works fine on my electronics bench, dual booting Ubuntu and Windows 2000, with wireless networking back to my LAN.  I probably could have bought an entire new machine for the same price though, but that wouldn't have been as much fun.

Jerry

---

### Post by mike555 on 2010-07-15
I had puppy (can't remember which version) running on a AMD K6 II, 400 MHz  with 128 ram ... a while ago .

---

### Post by Anxious Nut on 2010-07-15
Crunchbang linux on IBM Pentium II, 256 MB RAM, 4GB HDD, running well! ...  as well as running xchat IRC client 24/7, been months!

---

### Post by murphyac on 2010-07-17
OK, I see a bit more detail is in order.  I can't boot from CD on my 2 old IBMs.  I can only boot floppies, hard disks and RPL from network (whatever that is).  Both machines have Ultra (narrow) SCSI controllers and SCSI hard disks and CDROMs. Both have network and sound cards and a second SCSI 2 controller for external devices.

Why am I doing this?  I want to learn more about Linux.  Windows 98SE is the latest Windows I can run on these (Microsoft dropped support for the Microchannel bus after that) and I hate the bloatware and instability.  If I make a mistake, blooey, time to reinstall.  I have a modern computer, my Dell Dimension, running both Windows XP Sp3 and Lucid 10.04.  I'd like to see if it can function as a sort of server and learn a bit more about networking.  The IBMs were good solid workstations in their day, and can still function.  Parts are still available for them, and as** secondary** computers to the Dell, why not?  I like the two Debian-based distributions, Xandros and Ubuntu, that I have used so far on the Dell.  I also like Ubuntu's official and community-based support.
       I just wondered if I could use Ubuntu on the IBMs.  I like the idea of a home network where I could surf the web and read my email while my husband was also doing so.  I think our DSL connection would support this.  I also like the idea of sharing our router-connected all-in-one HP printer.  
       I've looked at the SliTaz and Puppy web pages.  The SliTaz looks possible, but the newest Puppy, although I like its being based on Ubuntu, might not be.  I don't know if I know enough about Linux to go straight to Debian.  Maybe a minimal installation of Ubuntu is the way to go - but which version, 6, or higher?
       My thanks for the help and ideas you all have given me so far.
Angela C. Murphy

---

### Post by Jerry N on 2010-07-17
Question for someone in the know:  Does any current version of Linux support Microchannel?  This is crucial to answering the OPs question.

Jerry

---

### Post by Jerry N on 2010-07-17
> **murphyac said:**
> I have two IBM PC750s PCI/Microchannel.
One has an AMD K6 II, 400 MHz overdrive processor and 192 Mb RAM (not upgradeable) and about 8 Gb hard disk space for installation.


Just out of curiosity, do these IBMs have the old heavy IBM keyboards?  I am using one dated 1987 and one dated 1994 on my secondary computer and have 2 or 3 more somewhat dirty ones stashed someplace.  I like the feel and heft of these KBs better than anything else I have tried.

---

### Post by murphyac on 2010-07-19
Yes, these computers do have the heavy keyboards.
I should also mention that the bus speed is 66 MHz.  There is a motherboard jumper that sets the speed at 66 MHz rather than 33 MHz if the processor is above a certain speed.
There is one Linux distro that I know of that definitely still supports microchannel - Slackware.  I went to its web page also, but it seems to be for a more advanced user than I am.  I need a distribution that is newbie-friendly, but allows room for learning more.  I thought that might be Ubuntu, but my computers may just be too old and slow.
Thanks for all your help and suggestions.
Angela C. Murphy

---

### Post by spcwingo on 2010-07-19
You could give Zenwalk a shot...it's Slackware/XFCE based.

---

### Post by confused57 on 2010-07-19
I have an old 500 Mhz, K6-II, 256 mb ram, which doesn't boot from cd, but was able to use Smart Boot Manager to boot first to floppy, then to cd:
[http://ubuntuforums.org/showthread.php?t=619593&page=3](http://ubuntuforums.org/showthread.php?t=619593&page=3)
It's an old thread, but may have some useful info for SBM.

Also, PlopBootManager may work:
[http://www.plop.at/en/bootmanager.html#runflp](http://www.plop.at/en/bootmanager.html#runflp)

---

### Post by Paqman on 2010-07-19
The Ubuntu minimal ISO is great, but building up a system from the command line can be a little daunting if you've not done it before. Check out the script in my sig, it'll get a minimal system set up for you with no hassle.

---

### Post by 4Orbs on 2010-07-19
This suggestion based on my own experience 2 years ago. Use the older version of DamnSmall Linux. It actually installs as Debian Woody to the hard drive. It was the only live cd I was able to boot without a kernel panic (because of the old BIOS. The kernel cutoff date for most Linux kernels is the year 2000).

---

### Post by walt.smith1960 on 2010-07-19
> **Jerry N said:**
> Just out of curiosity, do these IBMs have the old heavy IBM keyboards?  I am using one dated 1987 and one dated 1994 on my secondary computer and have 2 or 3 more somewhat dirty ones stashed someplace.  I like the feel and heft of these KBs better than anything else I have tried.

You are not alone in loving the "classic" IBM keyboard.  This site sells some interesting keyboards, including "buckling spring" models that have the wonderful "touch" of the classic IBM keyboards.

[http://pckeyboards.stores.yahoo.net/keyboards.html](http://pckeyboards.stores.yahoo.net/keyboards.html)  I've never ordered anything from this site but have kept it bookmarked because they have some unique solutions.

---

