---
title: "Linux for I586 processor?"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by T4K3Z0U on 2008-12-12
I wanna run Linux on an old NEC laptop which has an I586 processor.

I have tried Ubuntu 7.10; Fedora 10; TinyMe and PCLinuxOS all to no avail.

Google told me the best OS would be Solaris 8. But I have heard that Solaris ain't for the beginner, which is me.

So does anyone know of a Linux OS that can operate on an I586 processor, and if so, could you kindly upload a CD Image of it for me?

Cheers.

---

### Post by Duck2006 on 2008-12-12
You could try puppy linux or DSL linux or xubuntu.

---

### Post by bluefrog on 2008-12-12
do you mean that none of the distro listed above worked on your computer?

---

### Post by tomtom1982 on 2008-12-12
Sidux should work.

kde-version:
[ftp://ftp-mirror.internap.com/pub/sidux/release/sidux-2008-03-ourea-kde-full-i386-amd64-200809221842.iso](ftp://ftp-mirror.internap.com/pub/sidux/release/sidux-2008-03-ourea-kde-full-i386-amd64-200809221842.iso)

xfce-version:
[ftp://ftp-mirror.internap.com/pub/sidux/release/sidux-2008-03-ourea-xfce-i386-200809221832.iso](ftp://ftp-mirror.internap.com/pub/sidux/release/sidux-2008-03-ourea-xfce-i386-200809221832.iso)

It is an debian-based linux like ubuntu.

OpenSuse also should work.

[http://software.opensuse.org/](http://software.opensuse.org/)

---

### Post by Therion on 2008-12-12
> **T4K3Z0U said:**
> I wanna run Linux on an old NEC laptop which has an I586 processor.
I586 is just industry jargon for a **I**ntel Pentium processor:  The fifth reflects the generation of CPU development, after i80186, i80286, i80386 and i80486.  Pent = 5 hence the I(ntel) **5**86.

Your fail rate would seem to indicated that maybe you're not burning the install media correctly?  What happened, or didn't happen, exactly, when you tried to install Ubuntu, PCLOS, et al.?

---

### Post by Duck2006 on 2008-12-12
They couldn't call it a 586 copy right and all that stuff, so they called  a Pentium processor.

---

### Post by T4K3Z0U on 2008-12-12
Thanks for all the fast replies people.

> **Duck2006 said:**
> You could try puppy linux or DSL linux or xubuntu.

I'm downloading DSL just as I read this, so will give that a try, as well as the other 2. Keep you posted. 

Thanks.

> **bluefrog said:**
> do you mean that none of the distro listed above worked on your computer?

That is exactly what I mean.

> **tomtom1982 said:**
> Sidux should work.

kde-version:
[ftp://ftp-mirror.internap.com/pub/sidux/release/sidux-2008-03-ourea-kde-full-i386-amd64-200809221842.iso](ftp://ftp-mirror.internap.com/pub/sidux/release/sidux-2008-03-ourea-kde-full-i386-amd64-200809221842.iso)

xfce-version:
[ftp://ftp-mirror.internap.com/pub/sidux/release/sidux-2008-03-ourea-xfce-i386-200809221832.iso](ftp://ftp-mirror.internap.com/pub/sidux/release/sidux-2008-03-ourea-xfce-i386-200809221832.iso)

It is an debian-based linux like ubuntu.

OpenSuse also should work.

[http://software.opensuse.org/](http://software.opensuse.org/)

Thank you, I will try them too, if the above mentioned ones don't work.

> **Therion said:**
> I586 is just industry jargon for a **I**ntel Pentium processor:  The fifth reflects the generation of CPU development, after i80186, i80286, i80386 and i80486.  Pent = 5 hence the I(ntel) **5**86.

Thank you. That actually really means absolutely nothing to me. I am too new. I thought that because I have I586, must be why the other distro's aren't working for me.

EDIT: Not sure how important this is, but Fedora said that my CPU was missing a "cmov" feature.

---

### Post by Locke_99GS on 2008-12-12
Anything built for the i386 architechture ought to work for your system, if it doesn't, I'd check the download or the burn's integrity.

i686 stuff won't work on a 586.

---

### Post by T4K3Z0U on 2008-12-12
> **Locke_99GS said:**
> Anything built for the i386 architechture ought to work for your system, if it doesn't, I'd check the download or the burn's integrity.

i686 stuff won't work on a 586.

That explains why Fedora won't work, I downloaded the I686 ISO.

How do I check the burn's integrity?

Ubuntu was a cd I was sent from Ubuntu. PCLinuxOS I have used the live cd on my machine, worked fine. Attempts to load kernel on old machine, but just wants to keep rebooting. The others all just stall/die during install. The disk stops spinning and the mouse stops moving.

You can now add DSL to the list too. It was looking good, then died.

Next up, puppy linux.

---

### Post by stchman on 2008-12-12
> **T4K3Z0U said:**
> I wanna run Linux on an old NEC laptop which has an I586 processor.

I have tried Ubuntu 7.10; Fedora 10; TinyMe and PCLinuxOS all to no avail.

Google told me the best OS would be Solaris 8. But I have heard that Solaris ain't for the beginner, which is me.

So does anyone know of a Linux OS that can operate on an I586 processor, and if so, could you kindly upload a CD Image of it for me?

Cheers.

How much RAM does this laptop have, what speed is the processor.  Is the processor a Pentium III, Pentium 4.  More information please.

---

### Post by T4K3Z0U on 2008-12-12
> **stchman said:**
> How much RAM does this laptop have, what speed is the processor.  Is the processor a Pentium III, Pentium 4.  More information please.

I forgot about that eh. Sorry fellows, should have said in the beginning.

It has 64MB RAM, I have a 256MB RAM coming from the states, shortly. 

CPU is 233MHz

Pentium with MMX is all I can find.

---

### Post by Locke_99GS on 2008-12-12
To check the burns integrity, (on the Ubuntu LiveCD, at least) you can use the "Check Integrity of Disc" option at the CD's boot menu.

Otherwise, most burning software will allow you to check the data after it is burned, to ensure it was burned properly. Burning on a very slow burn speed (say, 4x) usually prevents most burn problems, especially when burning Linux ISO's.

Downloads can be checked by comparing the hash of the completed download with the hash shown on the page where you got the file from.

Sometimes newer kernels have regressions in them that cause problems with older hardware, as the older hardware does not get tested as much. Installing an older release of whatever distro is usuallythe easiest way to get a bootable kernel, when you don't have a bootable kernel to begin with.

---

### Post by Locke_99GS on 2008-12-12
> **T4K3Z0U said:**
> I forgot about that eh. Sorry fellows, should have said in the beginning.

It has 64MB RAM, I have a 256MB RAM coming from the states, shortly. 

CPU is 233MHz

Pentium with MMX is all I can find.

You'll need to use a text-based installer to install on 64m of RAM - try the Ubuntu alternate cd.

The added ram will be beneficial.

Or better yet, something like DSL or Puppy (mentioned previously) would be better for your system. 233MHz isn't going to fly well for any full featured linux desktop.

---

### Post by Duck2006 on 2008-12-12
> **T4K3Z0U said:**
> I forgot about that eh. Sorry fellows, should have said in the beginning.

It has 64MB RAM, I have a 256MB RAM coming from the states, shortly. 

CPU is 233MHz

Pentium with MMX is all I can find.

At the moment puppy and dsl should work ok, when you get the 256Mb of ram the xubuntu should work ok.

---

### Post by T4K3Z0U on 2008-12-12
History of the laptop:

It's about 10yrs old (must be since it had windows 98.) it was used by it's owner only for surfing the net and emailing. It had been sitting around unused for a number of years, was used in February of '07 and not again, until a few weeks ago. Turn it on, during boot it instantly wanted to do a disk check and would freeze, just no possible way to boot it. I swapped out the old 8GB HDD and put in a 40GB HDD. Had to install Windows 2000 coz the 98 disk's whereabouts is unknown. 
It was working OK, rather sluggish coz I thought I'd be smart and throw in an old version of firefox. 
Installed AVG and thats when the SHTF, it was doing a scan and froze. Had to force it to shutdown, and now it wont boot. I tried to do the repair disk, with the boot cd, but that failed. So I thought bugger it, I will put Linux on it, coz Linux is cool, and kinda makes me feel like a computer nerd. Until I run into crap like this.

There are a few other minor issues, I am trying to sort out myself, but I need an OS for that.

Oh yea, Gparted won't work, once I click to do the partition, it freezes.

Almost forgot, I can't get a BIOS update for the machine. I found one online place, but they wanna charge me. Sounds like a scam, I never heard of paying fora BIOS update.

Ha ha, your probably thinking, just buy a new machine and be done with it. Well if I can avoid buying a new one, I'd prefer do that.

---

### Post by Locke_99GS on 2008-12-12
Those places that charge for BIOS updates usually just find them elsewhere. Most of the time, you can find one for free from the manufacture of the laptop, or the board it uses.

---

### Post by T4K3Z0U on 2008-12-13
I have got the Puppy linux live cd to work, it seems ok when using live, but when I tried to install it, the computer didn't reboot. I chose the full install option, which I thought was supposed to erase/overwrite the windows OS, however this is not the case.

Are you able to tell me, what may be going on?

EDIT: After rebooting, the puppy OS is not there.

---

### Post by Duck2006 on 2008-12-13
Did you read here first?

[http://www.puppylinux.org/manual](http://www.puppylinux.org/manual)

---

### Post by T4K3Z0U on 2008-12-13
> **Therion said:**
> 
Your fail rate would seem to indicated that maybe you're not burning the install media correctly?  What happened, or didn't happen, exactly, when you tried to install Ubuntu, PCLOS, et al.?

Didn't notice you had edited, until now. I think i mentioned it a bit earlier, but will repeat here again to save a bit of time, and in case I didn't say already.

Ubuntu got as far as loading the kernel, telling me I will need to force APCI (I think that was the abbrev. Something used for powering down.) Then it gave the Ubuntu logo and an orange bar that moves back and forward, it sticks there and the computer goes to sleep or something, becomes unusable, have to force a manual shutdown.

PCLOS, brings up the loading kernel window, gets to 100% then restarts computer, over and over. I have used this live cd before, so am sure its fine. I never installed this one on my PC because the version at the time, did not support languages. I need to write in another language.

DSL, gets as far as chosing my mouse and keyboard, then freezes. Again have to manually force a shutdown.

TinyMe, when installing, brought up a window asking for a name and password. I figured both would be root. I did not have time to enter that before the screen disappeared and brought up the TinyMe logo. Then the machine froze, again manual forced shutdown.

Fedora 10, told me I am missing something called "cmov" so need a suitable kernel for my CPU. I also learned here in an earlier post, that it most likely didn't work because I burned the I686 ISO.

As I said in my last post, I don't know what happened to puppy. It got the furthest, and I was able to use the live cd, but something happened to the install. EDIT: Forgot to mention, the laptop is now spitting out the blue screen of death. Whatever puppy did, the computer doesn't like it.

I have successfully burnt ISO's before, so I would say, it need be something to do with the soft/hardware rather than me personally.

---

### Post by T4K3Z0U on 2008-12-13
> **Duck2006 said:**
> Did you read here first?

[http://www.puppylinux.org/manual](http://www.puppylinux.org/manual)

Nope, just looking now.

EDIT: I read the instructions and realized a bit of what I did wrong. I need to run gparted to change the HDD from NTFS to a Linux format, which I believe would be best, rather than doing the frugal install. The only problem is, Puppy's gparted is showing the HDD with a padlock and wont let me alter the format, or to partition it. I have a gparted cd, but I don't have enough ram to run it. The computer ends up freezing.

Not sure what to do from here. Puppy looks the most promising.

---

### Post by ugm6hr on 2008-12-13
Your problem is 64MB RAM.

Did the DSL boot to the LiveCD Desktop at all?  If yes: use cfdisk to repartition and create a swap partition of about 100MB.

It's dead easy to do - from Terminal:

```
cfdisk
```

If that didn't work, I would suggest you use an AlternateCD - I think pretty much any ALternateCD should be able to do that.  Even the mini.iso: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

If that doesn't work (I'd be surprised), then it is worth trying a DSL 3.x CD, since I believe that 4.x moved to the 2.6 Linux kernel (can anyone confirm?)

Once you have created a swap partition, I suspect things will get easier.

---

### Post by Duck2006 on 2008-12-13
> If that doesn't work (I'd be surprised), then it is worth trying a DSL 3.x CD, since I believe that 4.x moved to the 2.6 Linux kernel (can anyone confirm?)

Yep.

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by T4K3Z0U on 2008-12-13
> **ugm6hr said:**
> Your problem is 64MB RAM.

Did the DSL boot to the LiveCD Desktop at all?  If yes: use cfdisk to repartition and create a swap partition of about 100MB.

It's dead easy to do - from Terminal:

```
cfdisk
```

If that didn't work, I would suggest you use an AlternateCD - I think pretty much any ALternateCD should be able to do that.  Even the mini.iso: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

If that doesn't work (I'd be surprised), then it is worth trying a DSL 3.x CD, since I believe that 4.x moved to the 2.6 Linux kernel (can anyone confirm?)

Once you have created a swap partition, I suspect things will get easier.

Nope. DSL asked what mouse I use, and IIRC it asked what keyboard. It showed the little penguin and then froze, wouldn't do anything. I think I have 4.x.

Biggest problem seems to be, the machine keeps freezing, during install. 

P.S I have edited 1 or 2 earlier posts of mine to add info, rather than posting a new post.

---

### Post by T4K3Z0U on 2008-12-13
> **ugm6hr said:**
>  Even the mini.iso: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

I think I already know the answer already, but ask just to be sure.

I will need to download the earliest mini ISO, which is Dapper Drake 6.06, yes? The 8.04 would require more RAM than I have, isn't this correct?

---

### Post by tomtom1982 on 2008-12-13
You also can try to install Debian Etch with text installer (expert mode). It's not the newest software, but the current version of debian.

---

### Post by ugm6hr on 2008-12-13
> **T4K3Z0U said:**
> I will need to download the earliest mini ISO, which is Dapper Drake 6.06, yes? The 8.04 would require more RAM than I have, isn't this correct?

Honestly - I don't know.  I don't think it matters actually.

The mini.iso has so few packages, it should run just fine.

---

### Post by theozzlives on 2008-12-13
> **Locke_99GS said:**
> Anything built for the i386 architechture ought to work for your system, if it doesn't, I'd check the download or the burn's integrity.

i686 stuff won't work on a 586.

is it a Cyrix or AMD 586? If so it's just a fast 486.

---

### Post by Twitch6000 on 2008-12-13
You could try out Tiny Core Linux.

This thing is meant for what you got.

[http://www.tinycorelinux.com/](http://www.tinycorelinux.com/)

---

### Post by theozzlives on 2008-12-13
did you highlight the partition and go to partition>unmount??? Then delete

---

### Post by T4K3Z0U on 2008-12-13
I dunno guys, I'm starting to think the machine has had it. I have got so many damn live boot CDs with different Linuxes on them, it's not funny.

Further updates.

I downloaded Sidux XFCE I386 that was linked in this thread, but it turned out to be I686.

OpenSuse, loaded the kernel, right at the beginning. The very next screen was just green with the opensuse logo, if froze nothing happened.

MiniIso 8.04 let me get as far as choosing a mirror something, I now just have a blue screen with white command line. I'm not sure if this is normal or not, but I presume that its another damn failure.

Will try Twitch's recommendation after I get some sleep. If that don't work, I will wait for my new RAM and see if anything new develops.

Just two quick questions. When you refer to CPU and Processor, these are both the same thing right? Is it possible to buy a new CPU for that bit extra speed, or is that just going too far with this old machine?

Thanks again guys (and girls?)

---

### Post by T4K3Z0U on 2008-12-13
> **theozzlives said:**
> did you highlight the partition and go to partition>unmount??? Then delete

Actually you know what, I did "try". I wondered if I needed to unmount it, unfortunately it refused, because it was apparently in use. 

Didn't mean to sound sarcastic there. Just happy, I managed to do something before being told to.

---

### Post by ugm6hr on 2008-12-13
> **T4K3Z0U said:**
> EDIT: I read the instructions and realized a bit of what I did wrong. I need to run gparted to change the HDD from NTFS to a Linux format, which I believe would be best, rather than doing the frugal install. The only problem is, Puppy's gparted is showing the HDD with a padlock and wont let me alter the format, or to partition it. I have a gparted cd, but I don't have enough ram to run it. The computer ends up freezing.

Not sure what to do from here. Puppy looks the most promising.

I've just seen this.

So you tried to unmount it in GParted.  Puppy doesn't mount partitions automatically, which makes this bizarre.

Also - try cfdisk in Puppy instead of GParted.

And when trying the mini.iso, were you connected to internet (i.e. broadband ethernet)?

---

### Post by T4K3Z0U on 2008-12-13
> **ugm6hr said:**
> I've just seen this.

So you tried to unmount it in GParted.  Puppy doesn't mount partitions automatically, which makes this bizarre.

Also - try cfdisk in Puppy instead of GParted.

And when trying the mini.iso, were you connected to internet (i.e. broadband ethernet)?

Yes I tried to unmount in gparted via puppy. I've never seen a padlock beside a partition either. EDIT: There is only 1 partition, if that makes any difference, which I don't think it does.

Will try cfdisk instead of gparted.

Yes I was connected to ethernet, when trying mini.iso. I guess your going to say that was my problem. Actually I have been connected during all the installs.

---

### Post by ugm6hr on 2008-12-13
> **T4K3Z0U said:**
> Yes I was connected to ethernet, when trying mini.iso. I guess your going to say that was my problem. Actually I have been connected during all the installs.

No.  You do need to be connected.

So Puppy seem to be your best bet to try and create a swap partition.

Try the command:
```
mount
```

It should list /dev/sdaX mounted, if your HD is in fact mounted.

If not - cfdisk should work fine.

---

### Post by T4K3Z0U on 2008-12-14
Another update:

Today I decided to try all the live cd's on my own computer. All worked very well, except fedora 10, which gave a > fatal module sp_mod not found message and another fatal message, plus dozens of error messages, and simply wouldn't work. Now I would have thought thta was because its an I686 ISO, but Sidux which said on the old machine that it was an I686 ISO, actually worked on my machine, though not too user friendly. 

OpenSuse, seemed to need a lot of power even to boot on my machine, or perhaps it's just a very slow bootdisk, definitely the slowest of them all. 

DSL gave me this error message > error only 1 processor found. PCI device oo.1f.1 not available because of resource collisions I could not get it to connect to the internet, so I guess the PCI device does something with the internet? Both wired and wireless wouldn't work. I am going to try DSL once more on the old machine because I realised that, yes, I made it to the desktop, then it froze. I didn't realize it was the desktop.

I didn't mention the others because there was nothing to say, other than they work.

I didn't try mini.ISO or Tiny core because they look like they install from the beginning.

Am about to retry puppy as well, see if the HD is actually mounted. Will report back soon.

---

### Post by T4K3Z0U on 2008-12-14
> **Twitch6000 said:**
> You could try out Tiny Core Linux.

This thing is meant for what you got.

[http://www.tinycorelinux.com/](http://www.tinycorelinux.com/)

Tinycore didn't quite get there. It gave me a yellow screen with a green bar at the top. (I believe this was a graphics issue. It wasn't a normal screen) and the writing was a slightly darker shade of yellow, and I just could not read it.

---

### Post by 3rdalbum on 2008-12-14
It's really quite irrelevent to be trying OpenSuse and Fedora on your machine, even if they are i386. You have 1/8th the necessary RAM for OpenSuse and less than a quarter of the RAM needed for regular Fedora. Without enough memory, Linux will grind to a halt and not start up (and probably give some odd error messages too).

Once you have the 256mb of RAM, you might be able to run Xubuntu, but it will have all the speed of a dehydrated slug, and it probably doesn't still have the ancient sorts of drivers needed for your hardware. The same is probably true of things like Fedora.

---

### Post by tomtom1982 on 2008-12-14
> **T4K3Z0U said:**
> 

Just two quick questions. When you refer to CPU and Processor, these are both the same thing right? Is it possible to buy a new CPU for that bit extra speed, or is that just going too far with this old machine?

Thanks again guys (and girls?)

Yes, CPU and Processor is the same thing (Central Processing Unit). It could be possible to buy a newer CPU, but I think for your old hardware you wan't get a new one and you won't get the speed you'll need.

Above all, it will be better to buy a new Mainboard, a new CPU and a new RAM.

Edit: Had have a look on [http://www.amazon.com](http://www.amazon.com). There it would cost 80,98 US-$ to buy NEW Mainboard, CPU, RAM which would be enough to run any version of ubuntu. Surely, USED stuff will cost less.

---

### Post by T4K3Z0U on 2008-12-14
> **3rdalbum said:**
> It's really quite irrelevent to be trying OpenSuse and Fedora on your machine, even if they are i386. You have 1/8th the necessary RAM for OpenSuse and less than a quarter of the RAM needed for regular Fedora. Without enough memory, Linux will grind to a halt and not start up (and probably give some odd error messages too).

I didn't see any system requirements, and was basically going through a process of elimination, trying to find something that will work.

---

### Post by T4K3Z0U on 2008-12-14
> **tomtom1982 said:**
> Yes, CPU and Processor is the same thing (Central Processing Unit). It could be possible to buy a newer CPU, but I think for your old hardware you wan't get a new one and you won't get the speed you'll need.

Above all, it will be better to buy a new Mainboard, a new CPU and a new RAM.

Edit: Had have a look on [http://www.amazon.com](http://www.amazon.com). There it would cost 80,98 US-$ to buy NEW Mainboard, CPU, RAM which would be enough to run any version of ubuntu. Surely, USED stuff will cost less.

Thanks for the info. I won't go down that path, I was just wondering about it.

---

### Post by T4K3Z0U on 2008-12-14
Drawing to a close. Finally!

I have managed to get DSL to run via livecd. I am trying to install it onto the HDD, by following [this]("http://www.damnsmalllinux.org/wiki/index.php/Installing_to_the_Hard_Disk") instructions. The 5th instruction has got me. > 5) Then follow the hd install script. because I don't see any install script to follow. I thought it would come up in the terminal, but no joy. So I followed the next instruction > The FAQ is at [http://www.damnsmalllinux.org/dsl-hd-install.html](http://www.damnsmalllinux.org/dsl-hd-install.html)) Your system will need to reboot again. and on the linked page, I followed instruction > 3. Execute "dsl-hdinstall" by typing "sudo -u root dsl-hdinstall" (without the quotes)
and enter the just created partition (e.g. /dev/hda1, /dev/sda2)
This will make a ext2 file system and copies the CD contents to it.

But got a message saying > hda1: Not enough space to build proposed filesystem while setting up superblock I really don't understand what that means, because I made the partition 1GB to be on the safe side.
Oh prior to that was a message > hda1 is not a special block device. Continue anyway? So I clicked yes.

I am hoping one of you very helpful folks, will be able to tell me how to sort the small, DSL issue, and we can put this thread to rest.

Puppy, just don't want to load correctly anymore. I wonder perhaps, is it hardware issue?

---

### Post by T4K3Z0U on 2008-12-14
I forgot to add this message from mkfs: > mke2fs 1.32 (09-Nov-2002) 

Maybe that will give you a clue.

---

### Post by fluxlizard on 2008-12-14
If you want a standard linux with all the latest apps in synaptic, pcfluxboxos will work just fine on that machine. I've got one with similar specs, but half the ram, and it runs everything just fine- open office, gimp, firefox, etc...

Sam linux may work as well for you and be a little easier for a beginner (fluxbox you have to do your own menus).

---

### Post by T4K3Z0U on 2008-12-14
A big thanks to all those who helped me through this damned trialling time.
 
Whilst I was waiting for replies to my last message (which I never got ;)) I started messing around to see if I could get DSL to work myself. I tried doing a 2GB swap partition and that didn't work. I got really frustrated and then all of a sudden it clicked. I was typing the device as hda1, when it should have been /dev/hda1. Actually /dev/hda2 coz 1 as the swap partition. I realised I had gotten confused by having to refer to 2 different sets of installation instructions, 1 for swap partition and the other for the main install.

Anyways, I got there, it seems fine. Only problem I encounter is the only decent default browser, firebird, is making the web pages GIANT. Only 1/4 of a page is displayed so I have to scroll down and across, thats if it allows you to scroll across, which is annoying.

Again, a big thank you to you all. I know some of you were probably ready to rip your hair out, since I am such a beginner. But with perseverance, we got there in the end.

---

### Post by Duck2006 on 2008-12-14
> **T4K3Z0U said:**
> I forgot about that eh. Sorry fellows, should have said in the beginning.

It has 64MB RAM, I have a 256MB RAM coming from the states, shortly. 

CPU is 233MHz

Pentium with MMX is all I can find.

Nice to see you have got it going.
When you get 256Mb of ram you should have a better short at installing Xubuntu in the system.

---

### Post by T4K3Z0U on 2008-12-15
OK I didn't realize this until just now, but the keyboard has gone funny.

Funny as in, some of the letters are being output as numbers. Normally you have to press the function button to operate the number keys, not that I have ever used them before. I found that pressing th Fn key makes the letter come up.

Is there a way to fix this? And the display issue I mentioned in a post or two before this one?

---

### Post by T4K3Z0U on 2008-12-15
OK I didn't realize this until just now, but the keyboard has gone funny.

Funny as in, some of the letters are being output as numbers. Normally you have to press the function button to operate the number keys, not that I have ever used them before. I found that pressing th Fn key makes the letter come up.

Is there a way to fix this? And the display issue I mentioned in a post or two before this one?

---

### Post by Kennedy Bushnell on 2008-12-15
Some laptops, even old old ones had a way to Fn-lock, that is to the the function(Fn) key.  See if you can figure out how to get it to unlock. That may be the problem.

---

