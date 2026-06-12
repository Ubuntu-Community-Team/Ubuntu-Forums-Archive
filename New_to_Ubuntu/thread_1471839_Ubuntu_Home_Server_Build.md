---
title: "Ubuntu Home Server Build"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by ilynx on 2010-05-03
Hello,

I am a new here, new to Linux and new to servers, so if this post is in the wrong forum, I apologize.  Since I am an absolute beginner, I am posting in this forum.  Also, I do realize that some of my concerns are not specifially Linux-related, but I am asking them here in hopes that the answers from this forum would have more relevance to a Linux server setup.  I am currently looking over the beginners guides and tutorials, but didn't find specifics that applied to these questions.

I have recently been gifted a motherboard/cpu combo and I want to use it to build a server running some form of Linux.  So far, all signs point to Ubuntu.  I am currently in school trying to change careers to something in the computer industry, so I figured a great way to learn about Linux and servers would be to build one myself.  The combo did not come with any other items (no installation cd, no cables, etc.) and I am not sure which CPU was installed (I tried removing the fan/heatsink rig but it didn't happen easily and I don't want to ruin anything).  I have already found the support and drivers page for the motherboard on the manufacturer's website.  All of the available drivers are for the Windows variants, so I am not sure if I can use them, but from the research I've done so far, it seems like they should work as long as I match them with the right specs (e.g. 32- or 64-bit).  Is there a way to find out what CPU is installed when I first fire up the machine?  I am fairly capable of installing software and most hardware upgrades, but have never built a system completely from scratch without the motherboard setup CD, so I am not sure about the steps I need to take.  Do I need to install the drivers for the motherboard or will they already be there?  The following is a list of steps that I think I need to do, listed in order.  I would love some help in determining if I have missed anything, if the order is inaccurate, etc.  Plus, I am open to suggestions and discussions on how best to proceed.


- complete my system build (I am using some old parts and some new ones, but I think they have all been found to work with Linux)

- turn on system for the first time, check if BIOS is up-to-date, any other things I should check on?  Can I check for the CPU here?  If not, where and how?

- update motherboard BIOS with USB flash drive 

- install latest drivers from motherboard website for CPU, chipset, on-board LAN, on-board audio, HDMI, USB 2.0, and SATA AHCI/RAID (any order for these?  where do these install to?  hard drive? motherboard, somehow?)

- install Ubuntu Server

- install any Ubuntu/Linux specific drivers?

- install video card



How does that look?

The motherboard is a Biostar TA785GE 128M 6.1.  Website is here: [http://www.biostar.com.tw/app/en/t-series/introduction.php?S_ID=455](http://www.biostar.com.tw/app/en/t-series/introduction.php?S_ID=455)

The video card is a ATI Radeon HD 4350.  Website is here: [http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-4000/hd-4350/Pages/ati-radeon-hd-4300-overview.aspx](http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-4000/hd-4350/Pages/ati-radeon-hd-4300-overview.aspx)

I want to use the server as a general purpose home server - backups, media server, perhaps a web server in the future - and also as a box to tinker with so I can learn the ins and outs of Ubuntu/Linux.  I have ordered one 320 GB WD Caviar to be my OS drive, and two 1TB WD Caviars to run in a RAID configuration (I think RAID 1, but not sure yet) for backup/media server purposes (Can I do both with the one set of hard drives?).  All drives have been reported to work with Linux in general and/or Ubuntu in particular.  I can get the model numbers if necessary.  

Is it possible to run Ubuntu from the Desktop CD/LiveCD in my situation?  Also, is Ubuntu server too much for a home server?  Is there a specific flavor of Ubuntu that might work better as a server for a first-timer?  (Like Kubuntu, which is mentioned in one of the links for beginners?)  Is Ubuntu Server all command line, or is it GUI-based?

I realize that I am asking a lot of questions, so let me end by saying...

Thanks so much for all your help and time,
ilynx

---

### Post by The_Fool on 2010-05-03
You can view your computer's hardware in the BIOS.  Did that computer come with RAM and a hard drive?  You'll need that as well.  If you are planning to use Ubuntu server edition, you won't need anything but an integrated graphics card.  Most servers in companies don't even have a keyboard, monitor, or mouse installed on it once it is up and running.  It can be configured remotely.  Ubuntu Server does not come with a GUI (graphical user interface) installed.

You won't need any additional drivers to run Ubuntu since the basic ones come on the boot-up installation CD.  You can get started right away once Ubuntu is installed.  Even if you plan to install the desktop version, it will come with a simple graphics driver so you can use the GUI.  Before you install Ubuntu, be sure you take a look at your hardware information in the BIOS.  If you have a 64-bit processor in it, you can install 64-bit Ubuntu.  There are many programs that can take advantage of a 64-bit setup.

Since this is your first time using Linux, I would recommend that you use the desktop version first since it comes with a GUI.  If you are used to how DOS works, the command line of Linux is mostly different.

---

### Post by amauk on 2010-05-03
First up, Linux is [monolithic](http://en.wikipedia.org/wiki/Monolithic_kernel), meaning you do not need to install drivers*
The drivers are already included 'within' Linux, and there should not be any need to manually select (or install) drivers

How to tell whether your CPU is 32 or 64bit?
Ideally, you should know the CPU installed, but if not I would install the 32bit version of Ubuntu
(32bit will work equally well on a 64bit CPU)

With Linux installed, you can do
```
cat /proc/cpuinfo
```

This will output info on the CPU.
Easiest is to just look up the CPU model on the net to see whether it's 32 or 64bit

So, finish installing the hardware
then install the OS
should be all that's required

Ubuntu Server is entirely command line based
You can install a GUI
but if you really want to learn, then I'd stick with the CLI
(server are all about editing config files, anyway. A GUI is a) not necessary, b) a resource drain, and c) a potential security hole)

Plus, you will probably not be using the server locally (apart from initial install)
instead, logging into it from a desktop machine, using SSH

That said,
If you do have need for graphical apps on your server (Eg. some services provide GUI editors, like MySQL)
I would recommend using what's called X-forwarding
This forwards the graphical display for your application to another machine (Ie. your desktop) so you do not need a GUI running on the server


* There are some proprietary drivers that you do need to do manually
Examples are the Nvidia binary driver, and some wireless networking drivers
but unlikely to run into this with a server install

---

### Post by ilynx on 2010-05-04
The_Fool and amauk,

Great info and insight!

> **The_Fool said:**
> Did that computer come with RAM and a hard drive? 

It did come with the proper RAM, the hard drives arrive today.  I am still torn between the desktop and server editions, but probably leaning towards the desktop, since this is my first attempt at getting into Linux.  But I am not sure if I will have the time or opportunity to start from scratch again, so I am still considering the server version.

Also, a new question... Most of the online documentation and beginner's guides deal with dual booting with Windows or replacing it, I can't find anything specific to a fresh install on a new machine.   Would there be any different tips for this process?


Thank you both for your prompt replies!

ilynx

---

### Post by Zill on 2010-05-04
> **ilynx said:**
> ...turn on system for the first time, check if BIOS is up-to-date, any other things I should check on?  Can I check for the CPU here?  If not, where and how?

- update motherboard BIOS with USB flash drive...
BIOS updates come, IMHO, in the category of "if it ain't broke don't fix it"!

If the BIOS works as *you* want it to work then any "updates" are irrelevant.  I would only consider updating a BIOS if I *needed* additional functionality.

It is also unlikely that you will find a "linux-friendly" BIOS update program as they often require MS Windows.  There may be work-arounds, but do you *really* want the hassle when you may still end up with a paperweight? :-|

---

### Post by ki4anr on 2010-05-04
Dear ilynx,

First I like the name...LOL. 
Second, welcome to the world of Linux and you made the right choice in choosing a server build. I am not going to suggest any technical knowlege here you will get a whole lot of quality suggestions from others much more knowlegable than me, and I see that The_fool and Amauk have already given you great help.
Your not going to find a better server than Ubuntu Server and following the suggestions you will get here will enhance your experience. Since you don't have a preconceived idea about how Linux and servers work together, you have already removed a big stumbling block that most have had to deal with by having Microsoft experience to cloud your perception. I am not against Microsoft servers totally, its just a different way of looking at the world without all the needless distractions you will get with the other OS (Not to mention the licensing debacle that you constantly are dealing with with MS).
Ubuntu server is a perfect server for the home in its already stripped down version, there are others that offer possibly a more user friendly interface, but you will learn the way you should learn doing it the way you are by coming here. Get good with the command line, it will be your best friend and do wonders for your new found experience.

Many cheers!:D

Kevin
ki4anr

---

### Post by ilynx on 2010-05-04
Zill,

Excellent points, I will pass on the BIOS update unless absolutely necessary.  Thanks!

Kevin,

Thanks for your encouraging words!  Out of curiosity, how did my name bring a smile to your face?  I'm wondering if there are other meanings, or if I actually finally ran into someone who knows what it means after nearly 20 years of using it.

BTW, I hope to finish my build this afternoon since all of the necessary parts arrived today.  Maybe I'll even get to the installation of Ubuntu tonight!  After reading more here and having a discussion with my brother, I have decided to go with the server edition.  Looking forward to a wild ride!

ilynx

---

### Post by ki4anr on 2010-05-04
ilynx,

Nothing in your name but it matches up with the newest Ubuntu (Lucid Lynx), and taken from the ipod,iphone,ipad type of wording. Just wish I had thought of it first..LOL 
Glad you enjoyed the post. I have been using all kinds of Linux ditros (Started out with Fedora Core before there was a number on the end, Suse, Mepis, Debian, Mint, Slackware,Gentoo,Puppy,DSL,PC Linux OS, Mandrake, Vector, Deli, Libranet (long gone),Slax,Feather,Crunchbang, and last but not least Linspire (Now part of Xandros)) for about 10 years and always seem to come back to Ubuntu in the end. The only other distro that I really love is Arch Linux, but for simplicty and support its hard to beat Ubuntu. Have fun building your server and by all means don't feel bad about asking anyone here if you run into a problem.

Cheers,

Kevin
ki4anr

---

### Post by ilynx on 2010-05-04
> **ki4anr said:**
> ilynx,

Nothing in your name but it matches up with the newest Ubuntu (Lucid Lynx), and taken from the ipod,iphone,ipad type of wording. Just wish I had thought of it first..LOL 


Ahhhh, I see!  I have seen the Lucid Lynx name before, but never even realized how close my forum name was to it.   FWIW, ilynx is an old Greek word which loosely translates as the "search for a natural high", and is often referred to as vertigo or dizziness.  (Hmmm, I sound all professorial there, but I assure you I am not - I picked up the word from a physical education class in college.)


ilynx

---

### Post by The Real Dave on 2010-05-04
I run a few Ubuntu servers, one like yourself as a general home server [incl proxy, torrent and a few other things]. 

The first thing that strikes me is the size of your OS drive. If you want it JUST to hold the OS, it's overkill, and wasting good GBs. My main server has an old 8GB IDE harddrive as the OS drive, with 2GB gone to swap space and another 3GB or so free for expansion. You can pick up drives like these on Ebay for next to nothing. They will however be quite a bit louder than new drives, owning to their age. That said, something even slightly newer (a ~20Gb Seagate IDE that I have for example) is almost silent. Either way, it's cheaper, and you really don't need the space. Throw that 320GB drive into another computer, somewhere it would be better used.

Ubuntu is a fantastic server OS, but getting familiar with the command line interface can seem scary but there is only a few quite simply tools that you'll really need for a home server [Nano being the most important :)].

Installing the desktop system and using it as a server is something I would not do. Many things will still have to be edited by the command line [it's generally easier] and it'll take much more resources. Ubuntu 10.04 Gnome uses ~150Mb at idle boot, Ubuntu 10.04 Server uses ~25Mb. It's a massive difference, and you could be wanting that RAM.

If you really wish to give the command line a decent try, I'll happily help you step by step. But what I would really recommend, is to use something like [FreeNAS]("http://freenas.org/freenas").

[FreeNAS]("http://freenas.org/freenas") is a great little OS, designed specifically for Network Attached Storage, though it'll function as many other things. It fully supports RAID [Soft and Hardware], JBODs and also ZFS. It can act as a backup server with RSync and Unison, share files through AFP, NFS and Samba to Mac, Linux and Windows respectively, and even has a torrent GUI. 

The best thing about it is that it is all controlled from a simply Web Interface. It's extremely straightforward, and will run on very low power computers. For someone with little experience, it's a great entry point, and just as versatile as any other OS [though the BSD command line isn't as easy as Ubuntu's, but you won't have to use it.].

A nice feature of FreeNAS is that you can run it from a LiveCD, it'll take it's config from a USB or Floppy, and run in RAM. That way, you won't need an OS drive at all, and you can set the other drives to spin-down, saving energy and prolonging their life.


Yes, this was a very long post, but I hope it's cleared somethings up. Here's a few youtube videos on FreeNAS that could be interesting to you, including one of my FreeNAS server.

[http://www.youtube.com/watch?v=GzcwtY9Cb1w](http://www.youtube.com/watch?v=GzcwtY9Cb1w)  -  My FreeNAS Server

[http://www.youtube.com/watch?v=t5Smc4VzaXM](http://www.youtube.com/watch?v=t5Smc4VzaXM)  -  Hak5 Build a FreeNAS Server

[http://www.youtube.com/watch?v=aAEm6910gLE](http://www.youtube.com/watch?v=aAEm6910gLE)  -  Building a 3TB FreeNAS Server

[FreeNas Howto Page]("http://freenas.org/documentation:howto")

---

### Post by Simfan147 on 2010-05-04
> BIOS updates come, IMHO, in the category of "if it ain't broke don't fix it"!

Yes, I agree. Don't bother updating it. You should install the server edition if it's for a server. You can install a GUI if you want too. 

[http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html](http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html)

---

### Post by ilynx on 2010-05-05
The Real Dave,
I don't think the post was too long at all.  You make some great points, but I have decided that I really do want to learn how to work with the CLI.  And I do want it to be much more than just a home server eventually.  I realize it will be much more difficult, and there will undoubtedly be stumbles along the way, but I am in no hurry to have this server running.  Besides, I am trying to earn a degree in computer science, I want to actually take this time to learn everything I can rather than taking short cuts or the easiest way out.  I look forward to the challenge and all the help and discussions I can get from this board.  This place seems very welcoming and helpful!

And, yes, the OS drive is huge.  Perhaps it is a mistake, but at $40, it didn't seem like much of an issue.  Maybe I can get something smaller soon so I can re-purpose it.


ilynx

---

### Post by The Real Dave on 2010-05-05
I'm glad you decided to stick it out. It's a great thing to look back on as an accomplishment, and you'll learn more than you can imagine. 

Your right, this place is great. There are plenty of guides for just about everything you'll want to do, and like I said, I [and plenty of other people] will be happy to help you along the way. 

Best of Luck mate!

---

