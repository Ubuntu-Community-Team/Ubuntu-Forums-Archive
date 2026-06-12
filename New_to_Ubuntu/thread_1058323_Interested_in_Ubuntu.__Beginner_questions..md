---
title: "Interested in Ubuntu.  Beginner questions."
date: 2009-02-02
forum: New to Ubuntu
---

### Post by Nicodemus144 on 2009-02-02
hello there!

i am interested in trying out Ubuntu as my new, everyday home desktop OS.    i went from DOS in my childhood to Windows for most of my life.  i transitioned to OS X a few years ago, and now i feel that it's time go to Linux.

i hope you can help me begin this process.  i intend to build a new machine for this endeavor.  i have a few questions.

are there any particular pieces of hardware i should acquire/avoid for Ubuntu compatibility, or can i build as if i were building a Windows box and expect it to work?

if i install Ubuntu as my primary OS, can i repartition later if i need to add a Windows partition?  Also, can i install Windows on a second HDD later if need be?

can i easily switch to another version of Ubuntu (like Kubuntu) later if i wish?

i already have the Ubuntu Pocket Guide pdf.  can you point me to any other beginner's guides that you feel are essential to entering the world of Linux?

thank you very much for your time, patience and assistance.  i eagerly look forward to becoming a member of the Ubuntu community!

---

### Post by Crafty Kisses on 2009-02-02
For the hardware, for video I'd say go with NVIDIA, and if you're thinking about getting a wireless card, you should probably read this: [https://wiki.ubuntu.com/WifiDocs/WirelessCardsSupported?action=show&redirect=HardwareSupportComponentsWirelessNetworkCard](https://wiki.ubuntu.com/WifiDocs/WirelessCardsSupported?action=show&redirect=HardwareSupportComponentsWirelessNetworkCard). For the installing Windows again if needed, I mean you can but it would probably be easier to install Windows on another physical drive instead of partitioning, it's kind of a pain to partition when Linux is installed first. Yes you can switch to Kubuntu, in fact you can switch between sessions, from GNOME to KDE which would be (Kubuntu and Ubuntu).

---

### Post by &#32 Greg on 2009-02-02
> **Nicodemus144 said:**
> hello there!

i am interested in trying out Ubuntu as my new, everyday home desktop OS.    i went from DOS in my childhood to Windows for most of my life.  i transitioned to OS X a few years ago, and now i feel that it's time go to Linux.

i hope you can help me begin this process.  i intend to build a new machine for this endeavor.  i have a few questions.

are there any particular pieces of hardware i should acquire/avoid for Ubuntu compatibility, or can i build as if i were building a Windows box and expect it to work?

if i install Ubuntu as my primary OS, can i repartition later if i need to add a Windows partition?  Also, can i install Windows on a second HDD later if need be?

can i easily switch to another version of Ubuntu (like Kubuntu) later if i wish?

i already have the Ubuntu Pocket Guide pdf.  can you point me to any other beginner's guides that you feel are essential to entering the world of Linux?

thank you very much for your time, patience and assistance.  i eagerly look forward to becoming a member of the Ubuntu community!

-Intel offers good Linux support. As a general rule, don't go with really obscure hardware, and double-check to see if there's a linux driver before buying.

-Doing a dual-boot with Windows is annoying as it needs to be on the first partition. Doing a dual-boot with two hard drives is more annoying than it's worth. If you might want to do a dual boot, then throw XP on from the start. You can always separate installation files and actual download files, and just mount another HD as another drive with no actual boot stuff.

-Switching is easy

-http://linux.oneandoneis2.org/LNW.htm
[http://www.whylinuxisbetter.net](http://www.whylinuxisbetter.net)
--When partitioning, use a separate / and /home

---

### Post by yeats on 2009-02-02
I think most hardware that runs Windows will do fine with Linux.  Wireless cards and video cards seem to be the sticking points, but there's more and more support for a wider variety of options (I'll let others speak to specifics).  As for partitioning for other OS's (Windows or otherwise) it's a good idea to plan this up front (and it's highly recommended to have a separate /home partition where your personal settings and data live). 

Good luck - and you've made a good decision to start here on the Ubuntu Forums - you'll get awesome support here. :-)

---

### Post by Nicodemus144 on 2009-02-02
thanks for the fast response!

ok, so it sounds like i'll be throwing XP on first before i repartition for Ubuntu.

now, when i used to run Windows i also partitioned to separate Windows from my user files.  

is it viable to do this again?  meaning, in the end i'd have 4 partitions (XP/XP user stuff/Ubuntu/Ubuntu user stuff.)

is it better to do this all on one HDD, or is it possible/beneficial to get one small HDD for the two OSes and another large HDD for all the user files?  i'm not sure how i would partition and format the second HDD.

Linux file system and NTFS can't read each other, right?

---

### Post by &#32 Greg on 2009-02-02
Linux can mount an NTFS file system, but it's not preferable.

The partitioning you want is definitely viable (though you should add a swap) on either on HD or two.

Basically, Linux can read the NTFS stuff, but you really want an ext3 partition for data.

---

### Post by Crafty Kisses on 2009-02-02
I mean as stated above you could partition on one drive, but you probably want Windows installed first. Linux can mount NTFS just fine, I have a NTFS external HD and internal both work great.

---

### Post by Nicodemus144 on 2009-02-02
thanks, greg.  could you elaborate on a few items for me?

> **  Greg said:**
> Linux can mount an NTFS file system, but it's not preferable.

what exactly do you mean by "not preferable'?  how so?


> **  Greg said:**
> The partitioning you want is definitely viable (though you should add a swap) on either on HD or two.

oh, right, i think i read about that.  that linux creates a swap partition much like the windows paging file?  so would it look like:

HDD: XP/XPUser/Root/Swap/Home

or

HDD1: XP/Root/Swap
HDD2: XPUser/Home

is that the right terminology and layout?


> **  Greg said:**
> Basically, Linux can read the NTFS stuff, but you really want an ext3 partition for data.

what is an ext3 partition?

---

### Post by jeremyblake on 2009-02-02
Webcams on Linux can be a slut! lol. Drivers aren't all that easy to find for them. Personally, i'd have Windows already on it, and install Ubuntu inside of Windows. But there are a lot of things i still, unfortunately. need Windows for. So maybe that's just me.

---

### Post by &#32 Greg on 2009-02-02
> **Nicodemus144 said:**
> thanks, greg.  could you elaborate on a few items for me?



what exactly do you mean by "not preferable'?  how so?




oh, right, i think i read about that.  that linux creates a swap partition much like the windows paging file?  so would it look like:

HDD: XP/XPUser/Root/Swap/Home

or

HDD1: XP/Root/Swap
HDD2: XPUser/Home

is that the right terminology and layout?




what is an ext3 partition?

Oh, what I meant by NTFS not being preferable is that you're using Linux; in general people view other file systems as better/faster for a /home partition. ext3 is a type of journaled file system that's generally the default for most Linux distros.

Your terminology/set up is what I would do.

---

### Post by mkvnmtr on 2009-02-02
If you do a small install of XP first then you can later do anything you want with your Ubuntu system. If your building you will probably have a pretty good sized hard drive. Set up your windows in like 50 Gb and you have the rest for Ubuntu. Be aware that you can have several linux installations on the same disk. If your home is in one partition it will serve for all the linux distros you want to try. Your one swap partition will serve all the distros. It is so easy to reinstall a Ubuntu or linux distro that your can do it once a week just to see if you like another one better. On an old laptop I have a windows xp that I never use. A Ubuntu 8.10 and another partition that right now has Ubuntu 9.04 but last week had Debian. Unlike mac or windows you can do what ever you like and then change it tomorrow if you think of something else.

---

### Post by The Cog on 2009-02-02
Linux absolutely will not work on NTFS - neither the root partition nor your /home user partition. ext3 is the default Linux filesystem, though there are many others.

Linux is able to read and write NTFS though, and ext3 drivers are available for windows. So they will be able to access files on each others filesystems.

Don't try to have a mixture of IDE and SATA hard drives. Go for one or the other. SATA HDDs and IDE CE/DVD is OK though.

---

### Post by Nicodemus144 on 2009-02-02
thank you all very much.  i feel like i now have a course of action planned out.

someone recommended i check to see if there are linux drivers for my hardware.  how do i do this?  

i understand that the drivers are a part of the kernel, and not available separately?  yet sometimes i read about people installing new drivers, so i'm not quite sure how things work on this side of the fence.

*edit*

found on the wiki a list of supported video cards, so i imagine it'll be the same for other products.

can anyone chime in on how good it is to run the NVIDIA drivers over the ones that come with Ubuntu 8.04?  since i doubt i'll be buying one of the cards on the supported list here: [http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/appendix-a.html)

probably gonna get a 9x00 model or GTX.

---

### Post by AlucardArg on 2009-02-02
There's a GTX in that list, in case you are talking about a Nvidia model.

Anyway, I think I misunderstood, but the drivers that come with Ubuntu are "NVIDIA drivers." To give you an example, when I installed Ubuntu, when I started it up for the first time, a little tray icon said "There are new drivers for your video card" [or something like that]. I clicked there, selected the driver (the one that said "Recommended", bleh), "Activate", and in a few minutes, Linux downloaded and installed the driver. I didn't even had to reboot...

---

### Post by Nicodemus144 on 2009-02-02
i'm sorry, i should've been more clear.  there are GTXs on that list, but not GeForce GTX 295 or GeForce GTX 285.

since they and the Geforce 9 series aren't on that list, i assume they're not immediately supported in Ubuntu and will require the newest drivers from Nvidia here:
[http://www.nvidia.com/object/linux_display_ia32_180.22.html](http://www.nvidia.com/object/linux_display_ia32_180.22.html)

---

### Post by Gotaro on 2009-02-02
Those are pretty powerful cards..  ;)  I don't know what use that much power is going to be with Linux!  A good site to check reviews on graphics cards and drivers for Linux is [_Phoronix_](http://www.phoronix.com/), but I don't know if they have the GTX 285/295 reviewed yet.

As far as installing OS's, the plan I used was to have 3 partitions:
hd0,0 Ubuntu,
hd0,1 FAT 32 Storage (Shared between OS's),
hd0,2 Windows 7 Beta.

This way I don't have to choose which OS my documents, music, movies, you name it gets stored on.

Before this setup, I had Windows installed on one HDD, and Ubuntu on another, with no problems, so I don't know why it was said that it wouldn't work.  You can also install Windows later, if you decide to (as in, you don't have to do it first, pre-emptively).  Just be prepared to reinstall the GRUB loader with the Ubuntu LiveCD afterwards, as Windows replaces it and leaves you with no way to boot back into Linux!  :P  I just had to deal with all of that, so just a heads-up.

---

### Post by Nicodemus144 on 2009-02-02
thanks Gotaro!  i'm still in the planning stage, but when i used to build machines i tended to buy forward.  i doubt i'll get those GTX cards, but i like to be informed. =)

i know that what i do need to do is have better hardware than an iMac. ;)

*edit* ooo, i think i may get now what alucard was saying.  ubuntu will automatically DL and update my video drivers from nvidia if i want it to, is that correct?  if so, that is convenient indeed.

---

### Post by Gotaro on 2009-02-02
> **Nicodemus144 said:**
> thanks Gotaro!  i'm still in the planning stage, but when i used to build machines i tended to buy forward.  i doubt i'll get those GTX cards, but i like to be informed. =)

i know that what i do need to do is have better hardware than an iMac. ;)

*edit* ooo, i think i may get now what alucard was saying.  ubuntu will automatically DL and update my video drivers from nvidia if i want it to, is that correct?  if so, that is convenient indeed.
Yes, you're correct.  When you first start, you'll get a "Hardware Drivers" popup that searches for drivers automatically and recommends one (in your case, nVidia's proprietary driver), that it will download and install for you if you choose.  Another useful app that does the same thing, but may have more options is EnvyNG.

---

### Post by Revenged on 2009-02-03
> **The Cog said:**
> Don't try to have a mixture of IDE and SATA hard drives.

Can I ask why?

---

### Post by channerhewitt on 2009-02-03
I'm also interested with this OS. What are its features?

---

### Post by jrusso2 on 2009-02-03
> **Codename said:**
> For the hardware, for video I'd say go with NVIDIA, and if you're thinking about getting a wireless card, you should probably read this: [https://wiki.ubuntu.com/WifiDocs/WirelessCardsSupported?action=show&redirect=HardwareSupportComponentsWirelessNetworkCard](https://wiki.ubuntu.com/WifiDocs/WirelessCardsSupported?action=show&redirect=HardwareSupportComponentsWirelessNetworkCard). For the installing Windows again if needed, I mean you can but it would probably be easier to install Windows on another physical drive instead of partitioning, it's kind of a pain to partition when Linux is installed first. Yes you can switch to Kubuntu, in fact you can switch between sessions, from GNOME to KDE which would be (Kubuntu and Ubuntu).

Most of the cards on that list are so old you would have to find them online in old stock or used.

---

### Post by bobpur on 2009-02-03
I'll have to agree with Gotaro about the dualbooting issues.

IMO, I'd rather have two separate OS's on two different Hard drives. The main reason for that is if you lose a hard drive the other one is intact. Also, as you're new to linux, the chances of you borking the other OS is reduced if you're not messing around on the same drive.

As to partitioning, The first drive (hda if PATA, sda if SATA) should be all NTFS for Windows. The second drive (hdb if PATA, sdb if SATA) should be a EXT3 partition with a small SWAP partition, also, present on that drive.

IMO, people tend to make more out of dualbooting than is necessary. Once you get Windows installed on the first drive (or partition) the Ubuntu live cd will take care of the rest. Just be sure of what you are clicking on and you'll have no problems.
That's what the forums are for. :)

And last, GRUB is a non-issue. As a newbie you shouldn't worry about tweeking GRUB until down the road somewhere. As it is installed, It will default to Ubuntu and you'll have to use your arrow keys to get Windows. Later, when you are more knowledgeable, you can tweek GRUB to boot Windows first or add other OS's for a Tri-boot or a Quad-boot machine. 

TIP: Installing Windows first is good advice. Yeah, you can go ahead and install it second; but, you'll have to fix GRUB as Windows will overwrite it making Ubuntu inaccessible.

TIP: there are plenty of "How to's" for dualbooting and about any other issue you'll run into.

If building a computer my preference is: AMD cpu's, Nvidia graphics, older Creative Labs Soundblaster Audigy 2, 4, & SE soundcards, PATA Hard drives all hooked to an ASUS motherboard.
In linux, you don't have to use cutting edge hardware. IMO, linux tends to lag behind Windows on hardware because of driver development. This is not a bad thing.

Some of what I put down here may be outdated but it works for me still.

Good Luck.

---

### Post by Crafty Kisses on 2009-02-03
> **jrusso2 said:**
> Most of the cards on that list are so old you would have to find them online in old stock or used.

True. From my experience though, Linksys works well, so if you can find a newer Linksys one, give it a shot.

---

### Post by Gotaro on 2009-02-03
> **channerhewitt said:**
> I'm also interested with this OS. What are its features?
That's a tough question to answer!  Why don't you download the LiveCD and give it a try?  The more people that try it out and give feedback, the better it will ultimately be!  Keep these forums in mind, in case you have questions.

---

### Post by ronelc on 2009-02-03
I've just started trying ubuntu a month ago. It's a little difficult at first but you'll love it when you get used to it. This forum has help me a lot. If you still want to run windows, you can do it by virtualization. I used virtual box and now running windows xp on it.

---

### Post by jmszr on 2009-02-03
Nicodemus144,
             This is an extremely good beginner's resource: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by Crafty Kisses on 2009-02-03
> **jmszr said:**
> Nicodemus144,
             This is an extremely good beginner's resource: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Yes, that has a lot of good reading material, also the official Ubuntu documentation is great too.

---

### Post by halovivek on 2009-02-03
I use to refer most in this [site]("https://help.ubuntu.com/")

---

### Post by Nicodemus144 on 2009-02-03
thank you all so much for all your support and advice!  you're too kind. =)  believe me, it goes a long way to getting new people to comfortable with linux.  i have high hopes and really think this is going to be fun and worth it.

i have another question, if you'd be so kind.  should i go with the last LTS release 8.04, or go instead with 8.10 or even maybe the upcoming 9.04?  

i hear 8.10 has better wi-fi compatibility, but is less stable.  is this still the case?

or should i go with the supposedly more stable 8.04 and manually fix the wi-fi issues (assuming i can)?

---

### Post by AlucardArg on 2009-02-03
I don't use a Wi-Fi card, so I can't advise you on that. Still, I'm completely new here, and I'm using 8.10 (Intrepid Ibex) and any problem I run into, I just go to google, and find the solution in no time. That's the spirit of Ubuntu: Help each other.

But, I wouldn't try 9.04 yet. It's still in development, and it's likely to be quite buggy. I'll stick to Ibex for now...

---

### Post by The Cog on 2009-02-03
Re mixing IDE and SATA drives:
I have seen several posts where Ubuntu won't boot (GRUB bootloader error message), apparently because of confusion over hard disk numbers between the installer and bootloader. I never really understood the details, but I do gather it only arises when mixing IDE and SATA.

---

### Post by Revenged on 2009-02-03
> **The Cog said:**
> Re mixing IDE and SATA drives:
I have seen several posts where Ubuntu won't boot (GRUB bootloader error message), apparently because of confusion over hard disk numbers between the installer and bootloader. I never really understood the details, but I do gather it only arises when mixing IDE and SATA.

How odd. I have a SATA drive as my windows partition and as some file storage, and two IDE drives, one Ubuntu and one for music/movies, and I have yet to have any problems.

---

### Post by handydan918 on 2009-02-03
I would ALWAYS advise anyone not 'expert' in Ubu to use the LTS version. It's a lot easier to breathe life into a wireless card than to try to do a "Lazarus" on your system after an upgrade gives you borkage...


*Dons asbestose undies, awaits flames....*

---

### Post by Nicodemus144 on 2009-02-03
> **handydan918 said:**
> I would ALWAYS advise anyone not 'expert' in Ubu to use the LTS version. It's a lot easier to breathe life into a wireless card than to try to do a "Lazarus" on your system after an upgrade gives you borkage...


*Dons asbestose undies, awaits flames....*

alright, dan.  so, just to be clear, is this to say that, for the non-expert Ubuntu user, there's no benefit in 8.10 that substantially outweighs the cost of potential stability problems?

my research is leading me to choose 8.04, but i just like to engage people directly on the matter.

---

### Post by AlucardArg on 2009-02-03
I've had no problems with 8.10 so far, but still, he has far more experience than me, so go for the LTS. All in all, I'm sure that you'll be able to use the WiFi card in 8.04, one way or another.
And if one day, you say "Hey, I'm done with the LTS, I'll give 8.10 a shot", you just upgrade from the Updates Manager.

---

### Post by Crafty Kisses on 2009-02-03
Yeah you can simply run a dist-upgrade, but I prefer fresh installs.

---

### Post by Nicodemus144 on 2009-02-03
sounds good.  i'll start with 8.04 and just go from there.

thanks again to everyone for all your help and patience.  i feel well grounded and informed now, with a course of action.

now i'll begin speccing out my build.

i have to say, it feels good to be moving over to Linux.  i feel more free already. ;)

---

### Post by handydan918 on 2009-02-03
> **Nicodemus144 said:**
> alright, dan.  so, just to be clear, is this to say that, for the non-expert Ubuntu user, there's no benefit in 8.10 that substantially outweighs the cost of potential stability problems?


With case-specific exceptions, yeah, I'd write the rule that way. The LTS distros tend to be more stable, although nothing like Debian stable. I think the most traumatic thing a noob can be faced with is a borked update on a machine that used to work, has all his data captive, and that he can't use to get help.

---

### Post by Gotaro on 2009-02-03
What makes 8.10 unstable, anyway?  I never tried 8.04, but what, for example, happens now in 8.10 that wouldn't in 8.04, making it more stable?  I understand the theory *behind* it being "more stable," but I can't put my finger on anything specific that has gone wrong in my real-world use that wouldn't have in the LTS version.  Honestly, I thought 8.10 was the stable release lol.  I mean, 9.04 is the unstable one, right?  Lol.  I feel behind the times with MY release, and don't understand why people choose to stick with older ones.

---

### Post by Temposs on 2009-02-04
> **Gotaro said:**
> What makes 8.10 unstable, anyway?  I never tried 8.04, but what, for example, happens now in 8.10 that wouldn't in 8.04, making it more stable?

Gotaro, the idea is that with each new version of Ubuntu, new features are added to the OS that significantly change the functionality and/or interface. With an LTS, the approach to the new features is one that is supposed to minimize the breakages, and focus on stability. A non-LTS release gives more emphasis to trying new things. Also, an LTS will have more time fix bugs and such, which is the focus after the first few months of release.

Specifically, I know that the nvidia driver supporting my video card in 8.10 is less functional than the one in 8.04. I cannot resume from suspend very well. I also know that the intel video driver on 8.10 prevents another computer I have from starting Compiz, and it's a known bug that has no remedy. The 8.04 version worked fine. Just a couple cases of greater instability off the top of my head.

:-)

---

### Post by Gotaro on 2009-02-04
> **Temposs said:**
> Gotaro, the idea is that with each new version of Ubuntu, new features are added to the OS that significantly change the functionality and/or interface. With an LTS, the approach to the new features is one that is supposed to minimize the breakages, and focus on stability. A non-LTS release gives more emphasis to trying new things. Also, an LTS will have more time fix bugs and such, which is the focus after the first few months of release.
I understand that this is the *theory* behind it.  But I guess I'm just not an experienced enough user to understand when something should have worked, but didn't, because the OS was unstable.  In fact, it almost seems like more things don't work than do!  Lol.  It's hard to say what is to blame, though..  I always assume it's just because I'm doing something the wrong way.  It's all so confusing, especially when I consider that KDE is mostly what I interact with, and Ubuntu is just something going on in the background!  If I put KDE 4.2 on Ubuntu 8.04, I probably wouldn't even know I was using a different release!  Lol..

---

### Post by theozzlives on 2009-02-04
Windows/Windows stuff/Ubuntu/home/swap

If you  do dialup, don't get a winmodem I got 4 useless ones.

---

### Post by Temposs on 2009-02-04
> **Gotaro said:**
> I understand that this is the *theory* behind it.  But I guess I'm just not an experienced enough user to understand when something should have worked, but didn't, because the OS was unstable.  In fact, it almost seems like more things don't work than do!  Lol.  It's hard to say what is to blame, though..  I always assume it's just because I'm doing something the wrong way.  It's all so confusing, especially when I consider that KDE is mostly what I interact with, and Ubuntu is just something going on in the background!  If I put KDE 4.2 on Ubuntu 8.04, I probably wouldn't even know I was using a different release!  Lol..

Well, really, Ubuntu is everything, including KDE/GNOME. Ubuntu is all the software that Canonical puts together for you. Now, the Linux kernel, that's going on moreso in the background.

Also, computer systems are such complicated things. When you have a few issues that affect you, it may seem like so many things aren't working, but to think about how many things are working, it is truly amazing that it can all be brought together as much as it is.

One definition of technology: stuff that doesn't quite work yet.

---

### Post by longtom on 2009-02-04
Ah well...there's always something.  Here I am sitting,an absolute beginner quite proud I got Ubuntu 8.10 running and now I hear I should have installed 8.04....:p

On some of the PCs I access there are old 128Mb Nvidia Videocards involved...reading what Temposs has to say 8.04 might have worked better.

Is there any way to revert to 8.04 or is a reinstall on the cards?

longtom

---

### Post by The Cog on 2009-02-04
If it ain't broke, don't fix it. If 8.10 is working for you, then that's fine and you have newer versions of some software than you would have had with 8.04.

In my opinion, 8.10 severely broke the network manager thingy so that you can't configure a static IP address using the GUI - you have to resort to editing text files. And they added a service that I don't use that prevents you from seeing the contents of USB cameras. I didn't notice anything working better than 8.04. But each person has different requirements, and I have seen posts saying how much better 8.10 is than 8.04. It's a bit of a lottery really. Each version has its own hiccups, but overall it's going in the right direction and getting better.

---

