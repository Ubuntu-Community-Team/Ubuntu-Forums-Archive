---
title: "Installing Ubuntu 9.04 w/ dual boot"
date: 2009-05-16
forum: New York - US
---

### Post by sear on 2009-05-16
Greetings newbie land.

My MS Vista DVR software (Media Center software) got nuked by a no fee anti-malware package called Malwarebyte. I do not recommend that software.

Anyway, I'd like to install what I suspect is Ubuntu 9.04 64 bit, possibly Jaunty ...
w/ dual boot.

I'm on low bandwidth dial-up Internet connection.
A cyber-friend snail-mailed me Ubuntu/kUbuntu/xUbuntu/mythbuntu CDs from Australia.

But I'd like to retain the Vista OS, for emergencies (thus my choice of dual-boot).

I've just defragged my only internal HDD.

I'd like to partition it again.
It's a ~500 gig internal HDD, currently partitioned into logical C: & logical D:

C:
325 GB of 452 GB free
D:
1.75 GB of 12.7 GB free

I thought devoting ~300 gigs to Ubuntu would leave me a functioning MS Vista system. I use external HDDs for most of my DVR, word processing, and other functions.
So I think of the internal HDD as mainly the OS drive.

Right now, my questions for installing dual boot Ubuntu 9.04 are:

 - What partition size should I install Ubuntu in? Will 300 gigs leave MS Vista enough room? It seems MS Vista is taking up ~127 gigs of the 452 gig logical drive.
If I make a 300 gig partition for Ubuntu, that will leave the ~127 gig Vista with ~25 gigs of elbow room. Is that enough? I'll hope to not use it much, if at all, once I've got the Ubuntu DVR, Internet Browser (Firefox?), and Word Processing functions up and running.

 - What file system should I use?
I gather the options are:
Ext3
Ext4
Ext2
ReiserFS
jFS
SFS
FAT16
FAT32
swap area

Since DVR files are titanic (12 gigs or more), I'll need a system that can handle them.
But apart from that, the largest user files I deal with may be a text file of perhaps 3 megs in size, or so.

Can you tell I don't really know what I'm doing?

sear

---

### Post by sear on 2009-05-18
I've been working on it for a few days now.

I'm trying to produce a dual-boot result with two MS Vista partitions,
and three Ubuntu partitions.
The first Ubuntu partition is the root (/) partition.
The second Ubuntu partition is the swap partition, so if the system wants to use some HDD space in lieu of RAM, it can.
The third Ubuntu partition was to be 288 GiB, for whatever else Ubuntu / Linux might need or want.

[IMG]http://images.yuku.com/image/png/d241564f6b1d9e703fda5f99f8014493cc0bfc2.png[/IMG]

But as you can see, GParted won't allow me to make this final partition.

It says I can't do it as a primary.

Splendid.

Can I do it as an extended, or any other type?
Or must I leave over half my ~500 GiB hard drive (HDD) idle and unusable?

---

### Post by amgalitz on 2009-05-19
Well, where to start....

You have set yourself quite a task for you experience level so I commend you gumption. You need to read some guides to get this done as it is likely too tricky for anyone to lay it out for you in even several posts.

This [ [COLOR="Blue"]**guide**[/COLOR] ]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty")is a very useful starting point for several of your questions. Can't help you much with Vista as I use XP still. Googling something like Vista size etc might help. 

I refer often to this site [ [COLOR="Blue"]**Illustrated Dual Boot Site **[/COLOR]]("http://users.bigpond.net.au/hermanzone/"). You will need a boot manager like GRUB to do what you want and that still confuses me mightily. I usually have [**[COLOR="Blue"]this[/COLOR]**]("http://users.bigpond.net.au/hermanzone/p15.htm") open when I'm working on my multiboot set ups. 

I usually install 3 instances of ubuntu sharing a /home partition, and a partition for an initial GRUB menu.lst. One production, one backup and one for testing. The initial GRUB menu allows loading choice for which of the ubuntu (or XP) systems. Each of the ubuntu systems has its own GRUB menu so the automatic updating still works. This is explained on the GRUB PAGE ABOVE. I haven't tried Jaunty yet, still on Hardy and Interpid

Your partitioning problem is explained in the error message. You can have only 4 primary partitions on a drive. To get the number of partitions you want, one of those primary partitions must be an extended partition which will contain several logical partitions. Ubuntu and any linux will boot fine from logical partitions.

[ [COLOR="Blue"]**This tech paper from Microsoft also looks helpful**[/COLOR]]("http://support.microsoft.com/kb/919529") but I just skimmed and bookmarked it as it explains the windows boot process in nice detail.

Note this section from [ **[COLOR="Blue"]here[/COLOR]** ]("http://en.wikipedia.org/wiki/Dual_boot") 
...
**Windows and Linux**

Further information: Disk partition and Linux distribution

A popular multi-boot configuration is a mixed-OS system in which Linux is one of the secondary (or primary) installations. In terms of business strategy, Windows does not facilitate or support multi-boot systems, other than allowing for partition-specific installations, and no choice of boot loader is offered. To deal with such installs requires consultation with Linux afficionados and techs, who are typically well-versed in the concept.

The basic concept involves partitioning a disk, to accommodate each planned installation, including separate partitions for data storage or backups. The partitions should be done with a Windows partitioning tool (diskpart, Disk Management), rather than a Linux tool (parted, QTparted), for the simple reason that Windows is more particular (cf. "picky") about how the partition table is written and will occasionally complain or even show errors if its installed to a Linux-created (or sometimes modified) partition table. Linux tools are powerful, (ie. shrinking an NTFS drive) but Windows has particularities which must be considered. (See master boot record and extended boot record).

Windows should be installed to the first primary drive. Though Windows can be installed to another drive, certain particularities (drive letter assignments, expected system partition number) can make such installations problematic, while Linux installations on primary or logical drives have no such problems whatsoever.

The boot manager/loader should be installed by the Linux distribution. All Windows installations will be easily found by Linux, but Windows boot managers do not find Linux installations (nor does Windows deal natively with Linux file systems)...

Finally a few tips learned the hard way:

If you can, put your data on a different drive that your OS and /Home; drive space is dirt cheap these days. This would be good for your video files. The video data drive heads won't have to move to load software while the video data is getting crunched. You will also, I believe be using multiple data channels. The biggest time waster is drive head movement.

Get enough memory so you never need swap space, usually 2 - 4 gig, but you need 64 bit OS for above 3 GB. For large video file editing with a 64 bit OS perhaps more, but I don't do that and can't say.

Can't speak for Jaunty, but mixing IDE and SATA drives was a nightmare in Intrepid for me on an ASUS M3A78(and I suspect Jaunty) since the drive order changed from 1st stage GRUB to and the second stage. Could be a bios firmware issue. Learn about partition labels and use them when you can in fstab and menu.lst. Pay attention the the difference in drive lettering and number in GRUB and Linux; very easy to get confused.

DO NOT tell the Ubuntu initial installer about your data drive if you have set up permissions carefully for security. Edit /ect/fstab to add the data partition into your file system tree where you want it (Ubuntu installer tends to set permission and ownership for maximum ease of use rather than security. If you like that, well then let it). I'm picky about permissions and ownerships. If you plan to keep everything in your /home directory, are the only user, and don't care too much about getting hacked then don't worry about this. Make sure you are behind a hardware firewall/router and go to [ [COLOR="Blue"]**Shields UP**[/COLOR] ]("http://www.grc.com/intro.htm") to test your internet exposure.

Choice of file system get like a religious discussion. No one can make the choice for you. If you want it simple (and you do since you asked the question) use Ext3 for the OS partition (/), and /home (if it is not too large (30g?) and reiserFS for larger partitions. Ext3 is very solid and recovers well from power loss while writing. BUT, the system will force a check disc every so many boots which can take several minutes on a large (several hundred gig partition). reiserFS is very stable and safe, but does not have this annoying tendency. (let the flame wars begin..) At your experience level you likely won't see enough performance differences to use the newer bleeding edge systems.

Now how about a different approach: buy a small (160 - 200 gb) drive and and swap your first drive using either a removable drive rack or [[COLOR="Blue"]**this**[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817392022") for vista and your ubuntu installs. Put you video on a permanent second drive. You've spent how long on this already?

have at it tiger

---

### Post by sear on 2009-05-19
Thanks much for the guidance here amgalitz.

I'll try to take the methodical approach here, and review the information step by step.

Thanks for pointing me in the right direction.

PS
I notice I left out a word in my opening post.
My intended wording was:

Greetings [from] newbie land.

Please pardon me.

Thanks again amgalitz.
This may take a while ...

---

### Post by sear on 2009-05-19
>  "You've spent how long on this already?" amgalitz 
The Malwarebytes software neutralized the Media Center (DVR portion) of my MS Vista system over a month ago.

I've been trying to get Linux ever since.

But the truth is amgalitz, I guess I'll just either buy a MS Vista Home Premium (the Vista version of XP Media Center Edition) disk.
I think it's about $240.oo

I severely hate to send that kind of $cash to Bill Gates.
I'd almost rather send it to Ahmadinejad.

But though in VCR days the consumer could choose from a dozen different models and brands, with DVRs, it's TiVo (which means monthly payments, a deal-breaker), or nothin'.

Here are some possibilities:

[http://reviews.cnet.com/desktops/sony-vaio-lv250b/4505-3118_7-33644803.html](http://reviews.cnet.com/desktops/sony-vaio-lv250b/4505-3118_7-33644803.html)

I'm eager to break the Microsoft treadmill. Apple would help with that.

But $240.oo for a disk, or $1,500.oo for a Mac ...

---

### Post by sear on 2009-05-20
Update:
The install snag was; I designated the boot partition as /boot (which didn't work) and /root (which didn't work).
I then tried /
and that worked.
I partitioned 3 (with format) as follows:

/ reiserfs
/swap EXT3
/home EXT3

the set-up did not recognize the swap area.
In fact, a warning message appeared indicating no /swap partition had been selected, despite the fact that the list clearly listed the ~8 gig partition as "/swap".

BUT:

I had to type the "/swap" in. It was not an option listed from the several choices made available.

Set-up / Install offered a -go back- option, so I went back and tried every option on the list. "/swap" was not on the list. So I typed it in.
But though I tried every option from the list, except for ones I should obviously not pick, such as /home and /
it didn't recognize the /swap partition as such (even though it's labeled "/swap").

None the less, it did accept the install instruction. And as you can see (because I don't have Linux Internet access) the dual-boot function is working (meaning, I'm in MS Vista mode right now).

I'll dial back into Ubuntu and see if I can figure out the Internet connect thing.
I'll also try to install Mythbuntu, which I assume is the DVR software.

I've also got the Xubuntu, and Kubuntu disks. I haven't tried those yet, and I'm not sure what's to be done with them.

amgalitz,
You were right about GRUB.

BUT:

It installed itself with the one Ubuntu CD I had, and has defaulted to Dual-Boot, with Ubuntu as the the default boot OS.
That means, to boot Vista (which I'm using right now) intervention via keyboard is required.

---

