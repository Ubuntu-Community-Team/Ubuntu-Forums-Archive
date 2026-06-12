---
title: "Multiple sessions, XBMC / Ubuntu, etc"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by vtwin0001 on 2010-01-03
Hello,

I'm posting this thread here, because I have absolutely no idea how to do this...

Here's my situation:

I have a huge DVD Collection I want to rip into ISO Files, and I want to be able to run XBMC to watch them on my HDMI TV.

Now, since I have this huge collection, I am on the market to buy a computer which might have these specs:

10 DVD-ROM readers
1 High RPM Hard Drive (Low Storage Space) <---for Ubuntu
1 Low RPM High Storage Space with easy access to remove and put another disk, etc

Now, here's the deal:

On 1 session I want to run Ubuntu and be able to rip these DVDs I own into the Hard Drive, on the other session I want XBMC (Ubuntu version, obviously) to do its stuff.

Questions:

- How can I add the sessions?
- How can I add XBMC on one and run XBMC on the other?
- Is it possible to buy an Acer Revo, and fabricate a 10 DVD-ROM "external" and connect it via SATA so that this is only done when I want to (and not have the complete Ubuntu session running all the time) 
- Is it possible to use the Standby Mode in XBMC whilst working on the Ubuntu complete? (and viceversa)
- Is it possible to run jDownloader or other apps outside gnome, by using a vncserver, so that it runs on the background whilst using only the XBMC session?

Sorry if these are too many questions :(

Hope you can help me out (and others find the info useful as well)

Cheers! :)

---

### Post by Paqman on 2010-01-03
So do you want to have the DVDs ripping while you're using XBMC? If it's just either/or then just create two user accounts. Have one load straight into XBMC, and the other into a desktop.

If you're going to separate OS and storage onto separate drives i'd highly recommend putting the OS onto an SSD instead of a magnetic drive. You can get 30GB drives for reasonable prices, and that's more than big enough.

I'm a bit confused about where you're planning to locate your storage though. Are you building an array? Is this going to be network storage? If you've got enough DVDs that you need 10 drives to rip them you're never going to fit them all onto one drive. Have you actually figured out how much storage you need?

---

### Post by vtwin0001 on 2010-01-03
Thanks for your reply Paqman :)

Yes, I intend to do both tasks at the same time, this means that 2 users will be using the computer at the same time

1 user xbmc
1 user ripping the dvds

As my collection is quite big, I decided to put all these DVDs in various 1.5 tb (or more Gb) Hard Drives, since I know its a lot of data being transferred into a sata hard drive, I believe all this should be done using sata all the time (not involving hubs and usbs, cause this makes the tasks a lot more slow)
After the Hard Drive is full, I'll just store the disk somewhere and plug in another one.

The intention for this is because since the collection is very big, its easier to manage the collection between 10 drives rather than 10 000 dvds

I need aprox 16 Tb, I've already filled 5 1.5 Tb drives, but the task takes so much time, that I'm about to give up :(

So, the intention is buying the appropriate machine (the smaller the better) and be able to plug in (to a toaster, where you insert a hard drive and you're done) and watch the ISOs that are inside.

About the OS: Now that you bring the SSD idea, sounds nifty.. I might consider one of those and as you said it's not that expensive compared to 10000RPM drives, however I might even be comfortable using a pendrive (LOL.. really)

As I mentioned "the smaller the better" I would be more than happy to build an array (if that's what it is) of 10 DVDs + 1 HDD apart from the CPU, if this works for a fast transfer (using eSATA to connect to it I guess) :)

---

### Post by Paqman on 2010-01-03
> **vtwin0001 said:**
> 
Yes, I intend to do both tasks at the same time, this means that 2 users will be using the computer at the same time


Well, if you want to do both at once you can just do it all on one account. Your hardware is going to be the main limitation, not the software. Having that many optical drives ripping in parallel would probably saturate the SATA bus to your hard drive, let alone be within the fairly unimpressive write capability of a single magnetic hard drive.

You might want to do some actual testing to see what kind of read/write rates you need, then base your hardware on that.

---

### Post by vtwin0001 on 2010-01-04
Well.. The DVD-ROMs are capable of 18x each, this (according to google) means aprox 24 Mb/s each, therefore the data being transferred to the slow sata drive (not the high rpm drive, that one is just for the OS) is equal to 240 Mb/s
 I read that sata is capable of 150 Gb/s therefore it might not saturate the bus, would it?
 
I cannot do actual testing, 'cause I havent bought yet, my actual config is an ubuntu desktop machine (out of and uber-old amd cpu w/ 1 gb ram and 2 IDE Hard Drives and 2 IDE DVD-ROMs) It even has a Floppy Drive :)

 On the other side, I wont like to wait for ubuntu to load (i know it doesnt take too much time) and then load xbmc, instead, I'd rather make it go straight to xbmc and use a vncserver to control the other session and rip the dvds.
 
 btw.. should I just buy something similar to a raid? will this work with the dvds?
 remember: 10 dvd-roms and 1 1.5 tb drive

EDIT: Just checked the specs of the Hard Drive and it only is capable of 110 Mb/s sustained speeds, therefore, I believe I might go down to 4 DVD-ROMs....

---

### Post by Paqman on 2010-01-04
> **vtwin0001 said:**
> Well.. The DVD-ROMs are capable of 18x each, this (according to google) means aprox 24 Mb/s each, therefore the data being transferred to the slow sata drive (not the high rpm drive, that one is just for the OS) is equal to 240 Mb/s
 I read that sata is capable of 150 Gb/s therefore it might not saturate the bus, would it?


SATA 2 is 3Gbits/sec, which is about 300MB. 

> 
EDIT: Just checked the specs of the Hard Drive and it only is capable of 110 Mb/s sustained speeds, therefore, I believe I might go down to 4 DVD-ROMs....

I think you'd be lucky to actually get 110MB/sec. Maybe from a high end 10,000RPM drive. But that's [at the very top end]("http://www.tomshardware.com/charts/2009-3.5-desktop-hard-drive-charts/h2benchw-3.12-Avg-Write-Throughput,1013.html") of what traditional hard drives can do.

You don't need RAID to install multiple optical drives. You just need enough headers on the motherboard and power cables from the PSU to plug them all in. You'll probably want to get SATA optical drives for this reason.

---

### Post by vtwin0001 on 2010-01-05
Thanks Paqman :)

OK.. so I'm back to what I thought it would work better: 2 computers, one for ripping, the other one for XBMC

Now, my doubt is:
Should I just ssh to the XBMC computer (XBMC uses Ubuntu as main OS, but no Gnome), create a second user, install vncserver and fluxbox (and java, etc), make it run at startup, and then log on to it to run jDownloader in the background?

Will this work / help?

---

