---
title: "up from Damn Small Linux"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by hollowtd on 2009-03-25
Does anyone know the next smallest linux to use from Damn Small linux? Or, is it the best to use. I like Ubuntu and xubuntu but for some reason they just won't load on the computer even though the specs should handle it. Cheers

---

### Post by stone@bruti on 2009-03-25
Pupy Linux is nice, small and rather fast :

[http://www.puppylinux.org/]("http://www.puppylinux.org/")
[http://distrowatch.com/table.php?distribution=puppy]("http://distrowatch.com/table.php?distribution=puppy")

---

### Post by aeiah on 2009-03-25
if you want something that's based off ubuntu then look into installing ubuntu server with a custom desktop environment, or look into crunchbang, which uses openbox. what are the specs of the pc we're talking about here?

---

### Post by hollowtd on 2009-03-25
It has over 300 ram and 30 gig hd and currently runs windows ME. It's a dell inspiron 2500. (I use linux on these as it's more stable and as I take them as donation to Africa but have trouble getting ubuntu or even xubuntu on these.)

---

### Post by stalkier on 2009-03-25
> **hollowtd said:**
> It has over 300 ram and 30 gig hd and currently runs windows ME. It's a dell inspiron 2500. (I use linux on these as it's more stable and as I take them as donation to Africa but have trouble getting ubuntu or even xubuntu on these.)

Crunchbang is pretty nice. I have used it on a old DELL XPS system with a PII 500MHrz, 256MB RAM, 64MB graphics card. Ran fine. 

For some reason I had major trouble getting Linux to install on my system after I upgraded the hdd. there is an option you can input when you first startup the Live CD (before loading the OS). I forget what it is now but I am sure someone will know what I am talking about. BTW when you try to install or load Ubuntu what does it do? if it drops you to a command line then adding the option above will do the trick.

---

### Post by hollowtd on 2009-03-25
Often, It will load the bar and almost finish (getting ready to go to the screen) and then it just stops there.

---

### Post by ugm6hr on 2009-03-25
True booting with splash screen off to find out where it hangs.

Remove the "quiet splash" from the end of the relevant line on /boot/grub/menu.lst

---

### Post by hollowtd on 2009-03-25
I think I have to have it running (ubuntu) to do that. Right now the computer has no version of that on it, only crappy windows.

---

### Post by snowpine on 2009-03-25
For computers of that vintage, I've had pretty good luck with SliTaz and Puppy. I prefer SliTaz, but Puppy seems to have better driver support for obscure network and video cards.

The next "step" up from distros like DSL, Puppy, and SliTaz would be a "lighter" version of Ubuntu or Debian. There are many options in this range: Crunchbang, Fluxbuntu, Antix, etc. My personal favorite in this category is Crunchbang.

Good luck!

---

### Post by hollowtd on 2009-03-25
Thanks I may give it a whirl. Cheers

---

### Post by boof1988 on 2009-03-25
You could try using [Ubuntu Minimal Install](https://help.ubuntu.com/community/Installation/MinimalCD) and type "cli" at the boot to install a command-line and pick then applications you want installed from there (desktop, browser etc.).

If you are going to be installing on several computers, then you could use aptoncd (or other) to keep from having to download all the extra packages with each install.

I have used this method and the system usually uses about (max) of 220MB with Firefox running.  If you're interested in this, I (and other's) can help you with what packages might work for you.

I used this [Ubuntu Community Guide](https://help.ubuntu.com/community/Installation/LowMemorySystems) to help when I installed my system.

HTH...

---

### Post by stalkier on 2009-03-25
> **hollowtd said:**
> Often, It will load the bar and almost finish (getting ready to go to the screen) and then it just stops there.

Have you run a memtest or have checked the burn of the CD??

---

### Post by hollowtd on 2009-03-25
The burn seems good and all. I just posted this on another thread not knowing if I could or should put it here. 

What is going on, I've tried xu Ub and now crunch bang on a Dell inspiron 2500 with over 300 ram, 30 gig and plenty of power. Whenever the bar is a micro centimeter from finishing, it just stops loading with the live cds. What the heck is going on? Anything i can do?

I am baffled, it even happens with the live cd sent to me from Canonical. What the heck

---

### Post by boof1988 on 2009-03-25
> **hollowtd said:**
> The burn seems good and all. I just posted this on another thread not knowing if I could or should put it here. 

What is going on, I've tried xu Ub and now crunch bang on a Dell inspiron 2500 with over 300 ram, 30 gig and plenty of power. Whenever the bar is a micro centimeter from finishing, it just stops loading with the live cds. What the heck is going on? Anything i can do?

I am baffled, it even happens with the live cd sent to me from Canonical. What the heck

Have you tried one of the alternate-install CDs?  Sometimes they can solve some of these wierd issues.  Also the mini.iso may be able to work.  Ask about this if you're interested.

---

### Post by features on 2009-03-25
I have had some issues with older machines, where none of the live CD's would work, for Hardy or greater.  I had to install using a Dapper (minimal - only had 64MB ) CD, then run a do-release-upgrade to get to Hardy (and then Intrepid).

I forget exactly what kind of machine this was (it's since been junked), but I think it was about a Duron 800 and a VIA chipset.

As far as I could tell there was a change in the ISOLinux kernel in Hardy that prevented the CD from booting.  The same change was present in Puppy Linux too, since Puppy 4 would not boot, but Puppy 3 would.

HTH

Mark

---

### Post by LowSky on 2009-03-25
Debian (Ubuntu's ancestor) and will run on much lower specifcations.

---

### Post by lkraemer on 2009-03-25
Why not give Tiny Core a try, along with PCLinuxOS TinyME Acorn,
or PCLinuxOS Minime.  They seem to work pretty well as LiveCD's.
I've installed TinyME Acorn on my old Compaq Presario 1672.

[http://www.tinycorelinux.com/](http://www.tinycorelinux.com/)

[http://www.pclinuxos.com/](http://www.pclinuxos.com/)

lkraemer

---

### Post by hollowtd on 2009-03-25
I may have to give those a try unless someone can help me. I just loaded ubuntu alternate cd 8.10 and now it works but there is just text. It's like it's on Terminal only. Is there a user interface with the ubuntu alternate cd? I sure hope so?

---

### Post by halitech on 2009-03-25
the alt cd should have given you the same results as using the live cd. Did you uncheck anything when you were doing the install? If you are connected to the net with the machine you can try ```
sudo apt-get install ubuntu-desktop
```
you can change ubuntu for (k)(x)ubuntu if you prefer.

---

### Post by Dragonbite on 2009-03-25
> **hollowtd said:**
> It has over 300 ram and 30 gig hd and currently runs windows ME. It's a dell inspiron 2500. (I use linux on these as it's more stable and as I take them as donation to Africa but have trouble getting ubuntu or even xubuntu on these.)

I've had 2 low-memory systems
a PIII @ 500 Mhz w/128 MB Ram (before upping it to 256) which ran **Edubuntu** 7.? alright.  I used Abiword instead of OpenOffice and tried Xfce for a while but it did work, just not very fast.

The other is a PI w/MMX technology running at 233 Mhz and has 128MB of Ram. I had 4.10 (?) installed on it but it was a dog. I also had **TinyMe** (a derivitive of PCLinuxOS) which worked alright and **Damn Small Linux** (DSL) which worked the best on it.  I did manage to get **Suse 9.1** running KDE installed on it but it was touchy.

I am about to see about ressurecting it either with an **Ubuntu Alternate** installation (and add a low-resource windows manager), **Ubuntu Studio** (a portable web  server) or **Lubuntu** (Ubuntu with LXDE).

There used to be a project called **Fluxbuntu** which did work pretty well on the PI/MMX.

---

### Post by Chemical Imbalance on 2009-03-25
> **Dragonbite said:**
> 

There used to be a project called **Fluxbuntu** which did work pretty well on the PI/MMX.
Its still here and being developed:

[http://fluxbuntu.org/](http://fluxbuntu.org/)

---

### Post by halitech on 2009-03-25
> **Dragonbite said:**
> 

The other is a PI w/MMX technology running at 233 Mhz and has 128MB of Ram. I had 4.10 (?) installed on it but it was a dog. I also had **TinyMe** (a derivitive of PCLinuxOS) which worked alright and **Damn Small Linux** (DSL) which worked the best on it.  I did manage to get **Suse 9.1** running KDE installed on it but it was touchy.

I am about to see about ressurecting it either with an **Ubuntu Alternate** installation (and add a low-resource windows manager), **Ubuntu Studio** (a portable web  server) or **Lubuntu** (Ubuntu with LXDE).

There used to be a project called **Fluxbuntu** which did work pretty well on the PI/MMX.

personally I would go with Debian net install and install XFCE on it. Won't be a speed demon but will run better then any of the *buntu family. [http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

---

### Post by hollowtd on 2009-03-25
So I'd have to redo what I just did then?

---

### Post by hollowtd on 2009-03-25
The problem is I can't get this computer on the internet as it doesn't have wireless.

---

### Post by halitech on 2009-03-25
no, just run the command I posted earlier to get a desktop installed. Just hook up to the wired connection for now.

---

### Post by hollowtd on 2009-03-25
is there a way to put it on a stick and transfer it cause I won't be able to get this on the internet with or without a wire for some time.

---

### Post by hollowtd on 2009-03-25
I just booted it up and pushed esc. My choices show ubunt kernel 2.6.27-7-generic, the recovery mode and then memtest86

---

### Post by halitech on 2009-03-25
I doubt if you would get all the programs and dependencies required without being connected. Something obviously went wrong if you didn't get a DE with the install. What file did you download?

---

### Post by hollowtd on 2009-03-25
I did the !386 alternate cd for ubuntu 8.10 I though I did it right. when it asks about partitioning, which one should I have chosen? I can redo it I think?

---

### Post by hollowtd on 2009-03-25
should I choose" guided- use entire disk and set up encrypted lam" ??

---

### Post by halitech on 2009-03-25
I've never used the encrypted so can't comment on that. Is there anything else on the drive right now?

---

### Post by hollowtd on 2009-03-25
there's nothing on it but that. I can go through it tomorrow and check it out if you got any other ideas. I probably just chose the wrong guided partition thing. Wife's calling so I have to run. Thanks for all your help today. Thanks again until tomorrow Im sure.

---

### Post by utnubuuser on 2009-03-25
debian lenny netinstall - minimum system, Once that completes, install xorg and gnome-desktop

---

### Post by halitech on 2009-03-25
> **utnubuuser said:**
> debian lenny netinstall - minimum system, Once that completes, install xorg and gnome-desktop

he says he doesn't have access to net with this machine unless we can get the wireless going

---

### Post by Dragonbite on 2009-03-25
I know there is somewhere the Ubuntu ultimate DVD of all packages you can download somewhere. Maybe you can install that on a USB key drive (an 8GB will have plenty of space and they're pretty cheap now). Or order the DVD.

---

### Post by hollowtd on 2009-03-26
So I've got the alt cd for ubuntu 8.10. What choice should I choose (I want to use the whole hd space)? 

1. guided- resize scsI1 (000) partition #1 (sda) and use freed s
2. guded- use entire disk
3.guided - use entire disk and set up lvm
4. " and set up encrypted lvm
5. manual

Yesterday, I did this and got only "text" ubuntu. I would like to make the right choice when I install so that I have a user-friendly interface, the normal 8.10 look. I can't get this computer on the inet now though. Can anyone help me? Thanks

---

### Post by ugm6hr on 2009-03-26
Option 2.  Use entire disk.

---

### Post by LiamWilson on 2009-03-26
I don't suppose anybody's mentioned Xubuntu yet, have they? I can't be bothered reading all 4 pages. 
I run it on my olde Dell Optiplex GX1 with 192MiB RAM, and it runs like a Dream!

Edit// 
Oh, yeah. So you've said.

How about TinyCore Linux? 10Mib! Not tried it myself, but I read about in Linux Format.

Here's the link:
[http://tinycorelinux.com/](http://tinycorelinux.com/)

---

### Post by hollowtd on 2009-03-26
So, I opted to try Puppy just to see if anything would work, as I've now erased Windows from the computer, so I hoped to have something on there--It's better dead than to run Windows the way I see it. At any rate, I've uploaded Puppy and did all the steps and now when I turn on the computer it simply says: Grub> I don't know what to type to get puppy to work. I've tried xubuntu to no avail too. arg...It works with the cd in but not when it's out and I've set aside I though 1.25 gig for it on a partition.

---

### Post by anticapitalista on 2009-03-26
You won't get XUbuntu to fit on a 1.25GB partition.
It probably needs 3GB or more

---

### Post by hollowtd on 2009-03-26
Oh sorry, I got puppy to do so, though it's the only thing on the 20 gig computer. I just don't know how to start it, Puppy that is. It just says Grub once I power on. any ideas?

---

### Post by LiamWilson on 2009-03-26
Yeah, Xubuntu needs a 4gb Partition to work, that's probably why it isn't.

---

### Post by Chemical Imbalance on 2009-03-26
> **LiamWilson said:**
> Yeah, Xubuntu needs a 4gb Partition to work, that's probably why it isn't.

I have Xubuntu installed on my 4gb.  It is currently taking up 2.11 gb of space.

I have firefox and openoffice installed. Oh yeah...and GNOME is also installed.  ;)

I believe it takes around 1.8 gbs installed if I remember correctly.

---

### Post by stone@bruti on 2009-03-27
sounds as if your grub loader isn't configured. retry an install following the guide on the puppylinux site : [http://www.puppylinux.org/wiki/installation/hdd-full-installation]("http://www.puppylinux.org/wiki/installation/hdd-full-installation")

Stone

---

### Post by cjv8888 on 2009-03-27
> **hollowtd said:**
> Oh sorry, I got puppy to do so, though it's the only thing on the 20 gig computer. I just don't know how to start it, Puppy that is. It just says Grub once I power on. any ideas?

This is probably due to using Gparted to partition the disk and the Puppy Grub is not compatible with 256 inode size made by Gparted.

Have a look at this [thread]("http://www.murga-linux.com/puppy/viewtopic.php?t=39396")

I found Puppy was the only thing I could make run well on a computer with about 170 MB RAM.  I tried before that Xubuntu, DSL, Crunchbang and GOS - all of which failed due to varying problems.  Connecting wireless was a breeze in Puppy.  I have a Linksys USB54GC and a D-link DWA-110.  Both of these worked out of the box in puppy with straightforward configuration.

---

### Post by stone@bruti on 2009-03-27
wow, didn't know about that problem. Thanks for the info.
another site in my "to remember" bookmarks ^^

Stone

---

