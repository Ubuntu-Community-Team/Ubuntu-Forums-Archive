---
title: "Too slow (only 256 MB of RAM, 500 MHz processor)"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by jhsu802701 on 2009-09-15
How can I speed up Xubuntu?  I'm trying to run it on a 10-year-old laptop with only 256 MB of RAM and a 500 MHz processor.  Even with no applications running, it already goes into swap space.

What unnecessary processes, programs, etc. can I disable to significantly improve the speed?  Can I switch to JWM or Fluxbox (the window managers for Puppy Linux and Damn Small Linux) but still have a user-friendly interface?  (I tried the XFCE version of Debian, and I couldn't get the wireless Internet to work and couldn't even find the control for it.)

I'm hoping I can make Xubuntu as fast as Puppy Linux, which flies along seamlessly with only 256 MB of RAM but doesn't have the vast software repository of Xubuntu.

---

### Post by raymondh on 2009-09-15
> **jhsu802701 said:**
> How can I speed up Xubuntu?  I'm trying to run it on a 10-year-old laptop with only 256 MB of RAM and a 500 MHz processor.  Even with no applications running, it already goes into swap space.

What unnecessary processes, programs, etc. can I disable to significantly improve the speed?  Can I switch to JWM or Fluxbox (the window managers for Puppy Linux and Damn Small Linux) but still have a user-friendly interface?  (I tried the XFCE version of Debian, and I couldn't get the wireless Internet to work and couldn't even find the control for it.)

I'm hoping I can make Xubuntu as fast as Puppy Linux, which flies along seamlessly with only 256 MB of RAM but doesn't have the vast software repository of Xubuntu.

I have found Xubuntu a little lacking nowadays .... unlike before.  My current favorite (also ubuntu-based) is crunchbang and its' openbox.

---

### Post by earthpigg on 2009-09-15
> **raymondhenson said:**
> I have found Xubuntu a little lacking nowadays .... unlike before.  My current favorite (also ubuntu-based) is crunchbang and its' openbox.

crunchbang is indeed nice.

may also want to consider lxde, which also uses openbox, and which wont require a full reinstall:

```
sudo apt-get install lxde
```

log out. at the login screen, select sessions -> lxde.


either way, i suspect that you will experience a significant performance increase.

---

### Post by jhsu802701 on 2009-09-15
Thanks, [raymondhenson]("http://ubuntuforums.org/member.php?u=769495").  I'll have to give Crunch Bang Linux a try since it promises the speed and lightness of Puppy Linux with the vast software repository of Ubuntu, right?

---

### Post by earthpigg on 2009-09-15
crunchbang is not as fast and light as puppy, no.

not much out there is.

---

### Post by raymondh on 2009-09-15
> **earthpigg said:**
> crunchbang is not as fast and light as puppy, no.

not much out there is.

quite true.

I (as mentioned) prefer crunch because of my bias and comfort towards/for Ubuntu.

---

### Post by misfitpierce on 2009-09-15
I also recommend LXDE environment instead of Xubuntu. According to recent test I saw the recent Gnome ran a little lighter than XFCE environment with firefox and other apps open. LXDE did the lightest by over 100MB less. sudo apt-get install LXDE then at login screen hit sessions and choose session as LXDE. Enjoy.

---

### Post by benj1 on 2009-09-15
> **misfitpierce said:**
> I also recommend LXDE environment instead of Xubuntu. According to recent test I saw the recent Gnome ran a little lighter than XFCE environment with firefox and other apps open. LXDE did the lightest by over 100MB less. sudo apt-get install LXDE then at login screen hit sessions and choose session as LXDE. Enjoy.

or just wait for lubuntu.

its a shame what they did to xubuntu, it really is no faster than ubuntu (except thunar loads faster than nautilus) i read that article aswell, still cant believe it uses more memory than ubuntu.

im running crunchbang at the mo, very quick and shows memory usage of about 100mb after startup, its just annoying that as i write this firefox uses literally half my ram usage, oh well the hunt for that elusive lightweight browser (that does everything i want) continues.

---

### Post by gn2 on 2009-09-15
> **jhsu802701 said:**
> How can I speed up Xubuntu?  I'm trying to run it on a 10-year-old laptop with only 256 MB of RAM and a 500 MHz processor.  

Start with a minimal install CD and only add what you need.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Instead of adding xubuntu-desktop, which pulls in all manner of stuff, try just adding xfce.

Or if you want a distro that's ready to go, try Antix.

---

### Post by kerry_s on 2009-09-15
> **jhsu802701 said:**
> How can I speed up Xubuntu?  I'm trying to run it on a 10-year-old laptop with only 256 MB of RAM and a 500 MHz processor.  Even with no applications running, it already goes into swap space.

What unnecessary processes, programs, etc. can I disable to significantly improve the speed?  Can I switch to JWM or Fluxbox (the window managers for Puppy Linux and Damn Small Linux) but still have a user-friendly interface?  (I tried the XFCE version of Debian, and I couldn't get the wireless Internet to work and couldn't even find the control for it.)

I'm hoping I can make Xubuntu as fast as Puppy Linux, which flies along seamlessly with only 256 MB of RAM but doesn't have the vast software repository of Xubuntu.

modern linux is just rough on are old rigs, my specs are similar 450mhz 256mb ram, i would go command line & build up from there.
i don't have a way to burn cd's so, i'm stuck with the normal desktop, but if you do away with the fancy stuff, strip the heck out of it, its usable. :lolflag:

i just did a fresh install a couple of hours ago, been tweaking it since.

---

### Post by Cope57 on 2009-09-15
Does not matter what Linux distribution you use.  Install openbox to Ubuntu, Debian, Slackware, or whatever, the speeds will increase significantly.

---

### Post by jhsu802701 on 2009-09-16
Thanks for the suggestions.  I was going to try Crunch Bang Linux, but people say it's unstable.

How do I do a minimal installation of X/Ubuntu?  The idea is to only install the bare-bones OS and use AptGet/Synaptic to get just the stuff I actually need.

---

### Post by NexusZA on 2009-09-16
Another alternative ... try [Fluxbuntu]("http://www.fluxbuntu.org/"). Its Ubuntu but using Flux instead of Gnome or even XFCE

---

### Post by mike555 on 2009-09-16
There are many Puppy versions , some probably have what you want ... lighthouse version for instance ...    [http://www.lhpup.org/about.htm](http://www.lhpup.org/about.htm)

---

### Post by halitech on 2009-09-16
> **NexusZA said:**
> Another alternative ... try [Fluxbuntu]("http://www.fluxbuntu.org/"). Its Ubuntu but using Flux instead of Gnome or even XFCE

my main concern with using Fluxbuntu is the last release is only using 7.10 which is pretty old now. Would be better to do a minimal install and install flux and whatever apps needed after that.

---

### Post by khelben1979 on 2009-09-16
[Comparison of Linux distributions]("http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions") is one of my favourites and describes quite a few Linux alternatives to choose from.

From my experience by using Debian Lenny on my old Powerbook G3 (320 MB of RAM) it was working quite good. It's not in use at the moment because of a crashed harddrive, but it never had any problems running KDE for example.

---

### Post by snowpine on 2009-09-16
> **jhsu802701 said:**
> Thanks for the suggestions.  I was going to try Crunch Bang Linux, but people say it's unstable.

How do I do a minimal installation of X/Ubuntu?  The idea is to only install the bare-bones OS and use AptGet/Synaptic to get just the stuff I actually need.

That is silly; CrunchBang has been around since 7.10, has an active community, and is very stable. :)

I would recommend Puppy, SliTaz, or frankly, a new computer if you can afford it. :) The "micro distros" are going to be faster than any Ubuntu "remix" because Ubuntu is, at its core, designed for more modern computers.

---

### Post by salemboot on 2009-09-16
Most of the slow down comes from the graphics card.

You have an integrated chip.  lspci will give you more detail.

The bad thing about distributions is that most distributors release latest with latest and not latest with previous.  What I mean is you won't get the latest Xorg with the previous 2.4 kernel.  

You'll find distributions based on the old 2.4 series kernels the fastest if and only if your video card is supported by those versions' Xorg.  But I generally find them to be the fastest anyway.

Recent distributions are going to run about the same.  They all run the same kernels.  2.6.25 -> 2.6.31 will crawl, as they are still tweaking the scheduler.  It could be the case there were changes in GLibc.
In general newer kernels are optimised for multi-core processors with grotesque amounts of ram. 

Keep in mind the XBox versions of Linux distributions are based on 2.4 kernels.  XBox only has 64 Mb of ram for both the video card and system.

As far as specific distributions:
2.6 version kernels
. Ubuntu 6.06.  The kernel is old enough it should run good.
. Slackware 12.  It will test your patience, you'll need the synaptics driver if you have a touchpad.
2.4 version kernels
. Slackware 10.1. Solid distribution, ran it for 3 years, not sure how it will like your laptop.
. Slackware 10.2 Had a really polished KDE, Abiword was still there, lots of extras.  Just no Gnome.

Some things you can try with your existing distribution:
Recompile the kernel with the following configuration changes
. Configure the kernel for your processor type Pentium III 
. Disable memory past 1 Gb 
. Set 250 Mhz timer frequency
. Set Sever [ No kernel premption ]
. Disable support for mutiple cores.
. Set the scheduler to default to deadline mode: 
. Disable support for generic x86

Recompile Glibc for 686.

Manual quick steps
Setting Deadline Mode.
a. cat /sys/block/sda/queue/scheduler
b. CFQ will be set
c. sudo echo deadline > /sys/block/sda/queue/scheduler

This will be temporary.  But you can later add the echo command line to /etc/init.d/rc.local file.

sudo echo "echo deadline > /sys/block/sda/queue/scheduler" >> /etc/init.d/rc.local


Hope it helps

---

### Post by #11u-max on 2009-09-16
i don't belive it's possible to make xubuntu much lighter than it is, may i suggest**[ Spri Linux?]("http://sprilinux.com")** it is an extremely lightweight linux distro based off of an ubuntu minimal install with IceWM and only the most commonly used, and lightest applications possible.

---

### Post by anticapitalista on 2009-09-16
> **khelben1979 said:**
> [Comparison of Linux distributions]("http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions") is one of my favourites and describes quite a few Linux alternatives to choose from.

...

But the info on that page is very out of date (as well as being inaccurate).

---

### Post by raymondh on 2009-09-16
> **jhsu802701 said:**
> Thanks for the suggestions.  I was going to try Crunch Bang Linux, but people say it's unstable.

How do I do a minimal installation of X/Ubuntu?  The idea is to only install the bare-bones OS and use AptGet/Synaptic to get just the stuff I actually need.

I have never had stability problems with my crunch install.

For a true-brown ubuntu, I've used (once) the server edition and built from there.  Or, you can try the "mini iso's"  For your manager, I recommend openbox.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Good luck. Have fun :)

---

### Post by khelben1979 on 2009-09-17
> **anticapitalista said:**
> But the info on that page is very out of date (as well as being inaccurate).

I haven't found any other pages which describes the same thing which is more updated. The important thing about it is that it describes a lot of Linux distributions. Why get stuck on details? But sure, if there is a better document let me and others know about it.

---

### Post by Iksf on 2009-09-17
LXDE is really pulling ahead of XFCE in my opinion, less CPU usage, more traditional style layout, so good for Window$ converts, can't think of any of XFCe's advantages

---

### Post by benj1 on 2009-09-17
> **Iksf said:**
> LXDE is really pulling ahead of XFCE in my opinion, less CPU usage, more traditional style layout, so good for Window$ converts, can't think of any of XFCe's advantages

thunars nice and actually supports trash and a sensible desktop file system unlike pcmanfm, also better names for apps, plus its got a mouse :)

---

### Post by zeroseven0183 on 2009-09-17
> **Iksf said:**
> LXDE is really pulling ahead of XFCE in my opinion, less CPU usage, more traditional style layout, so good for Window$ converts, can't think of any of XFCe's advantages

Yup! By the way, when will they release Lubuntu?

---

### Post by BrainStorms on 2010-05-12
For those looking for a small footprint solution on machines of this size:

I have a ThinkPad i1400 = 256 MB RAM, 433 MHz Celeron, and 4.5 GB HDD.  Has a 10/100 PCMCIA card for networking and an 800x600 LCD.  I've gone through a number of minimal distros looking for a good solution...

I found three that will run well on my 1997 Toshiba Satellite Pro 435CDS (48 MB RAM, 120 MHz Pentium 1, 1.3 GB HDD -- *very* tight!):  Feather Linux (Knoppix 2.4), Damn Small Linux (Knoppix 2.4), and SliTaz 2.0.  Actually had all 3 installed at once as a multi-boot.

But of that group, only SliTaz is still being developed.  DSL runs *great*, but has a clunky look & feel.  Then I found that the main DSL developer (Robert Shingledecker) continued post-DSL to create his own minimal Linux, TinyCore Linux.  Unfortunately, that won't run on my Toshiba.  Neither will Puppy versions past 2.17...

Xubuntu 9.10 will run okay on the ThinkPad, but it takes almost all the hard drive, and it's just laggy enough to annoy.  Puppy 4.3.x runs very well, as does DSL.

What seems to work best?  SliTaz 3.0 -- an initial load takes up only about 250 MB of disk space and it runs fairly fast even on the old Celeron 433 (which is the bottleneck for this machine).  You can then customize it by downloading from their repository (> 2000 apps).  No annoying lag, and lots of disk space left.  Makes the old laptop useable...

TinyCore shows promise, but also requires a bit of work to build up a usable system.  SliTaz also requires some app downloading, but nowhere near as much.  Neither of them is Ubuntu, or Ubuntu-based.. unfortunately.

I've just downloaded the 'minimal install' version of Ubuntu 9.10 and 10.04, and will be trying them out as well.  I'll also try "Lubuntu", the LXDE version of Ubuntu (to compete with / replace Xubuntu) whenever it comes out -- perhaps with 10.10?

---

### Post by lavezarez on 2010-06-24
I have tried the final release of Lubuntu 10.04 in my 256 mb celeron but it couldn't detect my huawei usb broadband modem automatically as in other Ubuntu editions.  I also tried the Linux Mint LXDE 9 RC1, but that was worse - my computer froze during mid-install.

Then I tested Knoppix 6.2, and did the hard disk install from the live CD - it worked like a charm!  It is by far the fastest, easiest to install, offered excellent hardware detection, and painless shared Internet connection setup.

Currently testing if I can install a minimal Ubuntu 10.04 from the alternate CD.  You might want to check it out also.  Here's the link I use as reference: [ubuntu-minimal]("http://www.cs.uml.edu/%7Eaveilleu/projects/ubuntu-minimal/").

---

### Post by Sir Jasper on 2010-06-24
Hi,

Lucid Puppy 5.0.1 seems to be moving in the direction you want and it might be worth a look.

My regards

---

### Post by jerrylamos on 2010-06-24
Try Lubuntu.  Running fine on my oldest pc, a laptop.  I had a bit of learning to do with LXDE desktop & a different but similar internet browser.  Flash works fine for what I use.

Jerry

---

### Post by Flymo on 2010-07-08
Nice thread!  :popcorn:

We have set uo 7 or 8 GoBook ruggedised  laptops with a selection of distros for varii kids/grandkids/etc.  These have Pentium/Celeron 700~800 cpu  and 128 or (rarely) 256 RAM, 10 or 20 GiB  HDD.  

Agree strongly that SliTaz works well after some setting up, as does Puppy LuPu 5, and several (now 2-years old) Xubuntu LTS installations were fine - if you have 256 RAM. 

Not sure about more recent Xubuntu though - agree that it  seems to be  getting heavier with time, bit like me!;)

Puppy 'Mi-Pup' has been a popular option - good eye candy and reliable on this ancient and much-used hardware.

The redoubtable Barry Kauler of Puppy Linux has not only released Lupu (Lucid Lynx based Puppy) but also Quirky, his experimental fork that is also available (as are many fairly recent Pups) with a retro kernel - look for 'Qret' for that.  Can make a big difference on some older machines.

My current favourite for 256 RAM is Mint 8 Fluxbox CE. On most machines it boots up to around 80MB or RAM usage even with Wbar and some , which is grand for a 256MB machine.  With pseudo-transparency on the desktop menus and the Mac-alike Wbar it looks surprisingly good, and goes really well.

Lubuntu seems to be working OK, had to fix Synaptic search, and am struggling with the new-to-me configuration, but it seems basically good, although not quite as light as the Mint 8 Fluxbox.

Yes, Fluxbox is older code, but for me it just works and delivers so much bang for the RAM used.

Xubuntu was a great option for us two years ago - the kids loved the transparency effects - and I have grown to like it a lot.  But the main reason for getting used to it initially was the lightness, and it is sad to see that eroded.  But I still like it.


All the best, Ben

PS if time permits I'll pop some links in this later on.

---

### Post by axel668 on 2010-07-08
Unfortunately Xubuntu is pretty heavy on RAM, so with only 256M available you should definitely go for LXDE (there's a RC out for Mint9), Fluxbox (Mint 8 CE) or Openbox (#! based on Ubuntu 9.04). All of these distros are 100% Ubuntu compatible and all use under 100MB RAM after startup.

Surprisingly this is true for XFCE in other distros as well, was using it with Arch and Sidux and memory consumption was also around 100MB, no idea why Xubuntu is using twice as much.

---

### Post by NightwishFan on 2010-07-08
On 64-bit Debian Gnome seems to use less RAM than Debian with XFCE. So memory usage must be harder to measure than commonly thought. I have a machine with 128mb of RAM running a minimal Ubuntu and Fluxbox, it boots using only 34mb of RAM. It runs Midori just fine.

---

### Post by dzon65 on 2010-07-08
Minimal install/openbox will run on that machine.Yet,256 mb is still a bit low.Put in another 256 mb and it'll run comfortable.If you want something to look like ubuntu lxde but flies,go for slitaz.Iso<30 mb,download,burn and install will not even take 30 minutes.
Kind regards,J.

---

### Post by cruzton on 2010-08-12
I tried Xubuntu on an old, but running-XP-fine laptop that has only 256MB of ram and a 1.4ghz celeron processor. After the install, the system was useless. Xubuntu was trying to fit about 330MB of resident programs into the 256MB of RAM. The result? A swapfest as all the machine did was swap stuff around. It took 15 *minutes* to get to the desktop. 3 more to start a terminal. I couldn't even wait for it to shutdown.

Conclusion? Xubuntu doesn't work at all with only 256MB of ram. The requirements on the page should be updated to 512MB. Since I have Ubuntu Netbook running on a laptop with 512MB of RAM, I'm not sure what Xubuntu's advantage is now.

Installing the lxde pacakages produced something usable, but not fully tested desktop (ie. I still had to run nm-applet to get wifi). LXDE looked very promising though, and seems like it could be the future?

---

### Post by Samulus on 2010-08-12
You should try Slitaz linux. It's perfect for old computers. I keep it on my USB drive. [http://www.slitaz.org/en/](http://www.slitaz.org/en/)

---

### Post by admiralspark on 2010-08-12
This is an interesting subject. We have an old pc that had two 128mb memory stick in it, and I ran the full generic Ubuntu 9.04 on it with no problems. 'Course, the rest of the hardware specs were better, but memory didn't hold back Ubuntu.

Here are your options listed from easiest to hardest:

1) Linux Mint 9 LXDE edition. Even the RC's are stable, and it's clean and fast!
2) Puppy Linux (either 4.3.1 or 5.0.1 depending on which you're more comfortable with/works with your hardware).
3) SliTaz--never used it, heard great things about it
4) Spri Linux--also heard good things, very fast.
4) Debian network install--install only the things you need, I'd recommend anything from Openbox to IceWM as your window manager, with IceWM being by far the fastest.
5) last but no least--though certainly the hardest--build it from the bottom up with either Arch linux or Gentoo. Of the two, I recommend Gentoo, because it's slightly easier. Of all the *installed, full linux distro's* you can get (this does not include load-to-ram's like Puppy/DSL/Knoppix), Arch and Gentoo WILL run the fastest, sometimes by a long shot. They are customized to your specific computer with your specific hardware. Gentoo has many, many applications to choose from, however you will need an internet connection with no bandwidth usage limit (meaning no satellite internet like I have, cant wait for college in a couple weeks!).

Good luck, let us know what you decide!

---

### Post by snowpine on 2010-08-12
I have 2 old Pentium 3 laptops (500 and 600mhz) each with 256mb of RAM. They are running CrunchBang and CentOS (full Gnome desktop) just fine. :) I think CentOS is often overlooked as a distro for older hardware, however because it has older packages (like kernel 2.6.18 ) it is a great fit.

My first-ever Linux experience was Ubuntu 7.10 on one of these laptops. It ran--barely!--and it was this experience that started me down the path of lightweight distros.

---

### Post by Kixtosh on 2010-08-12
I don't know what all the fuss is about. I've found several solutions that work well with just 256MB of RAM on a PII and PIII.
 
- Ubuntu 9.10 & 10.04: both work, but a bit too sluggish to keep using.
- Xubuntu 9.10 & 10.04: both work, better than full Ubuntu, but still a bit sluggish.
- Xubuntu with LXDE desktop: even better again. Full boot in 55-60 seconds.
- Xubuntu with Chromium browser: more improvement in browsing speed.
- Puppy 431 & 501: both work, but not faster than Xubuntu & LXDE & Chromium.
- SliTaz: LiveCD would not work with my laptop (something needs fixing).
- Peppermint: works, but no speed advantage over Xubuntu & LXDE.
- Lubuntu 10.04: works, but I've had a couple of minor issues.
 
My favorite so far, and what I use (mostly) is Xubuntu and LXDE: I am able to boot up in just under one minute whereas Xubuntu _without_ LXDE (default Xfce desktop) takes about 75-85 seconds. Standard Ubuntu takes about 1.5-1.75 minutes to boot up on these machines.
 
Chromium is much better than Firefox in terms of speed. The first browsing session takes about 8 seconds to load. Subsequent sessions only require about 2 seconds. *[COLOR=DarkRed]EDIT (July 2011):[/COLOR] This may no longer be true. Firefox 4 and later are probably just as nippy as Chromium, and offer some advantages compared to Chromium (or Chrome). Firefox seems to require less space as well. In Puppy, the Firefox download is 15MB compared to 23MB for Chromium. Firefox profiles seem to require much less space in memory as well*.
 
Forget about OpenOffice. It will work, but it's just too slow when available resources are so limited. I prefer to use AbiWord and Gnumeric, or even the Google applications (which is basically what Peppermint does by providing direct launchable links to the Google applications in the standard office applications menu).
 
With just the desktop, System Monitor indicates that only 60-75MB of RAM is being used. With a browsing session open, that bumps up to 90-105MB of RAM. Even multiple tabs and browser windows have not caused noticeable issues.
 
I've used Puppy quite a bit, but it's not convenient with my Portégé, since there is no internal CD drive. I have tried it on the old DELL with both the CD and a HDD install. _It is the easiest of all to start using_ in my opinion, since you just pop in the CD and boot from there, without touching any of the original files or O.S. on the system, but it _does not offer any speed improvement_ when compared to Xubuntu with LXDE or Lubuntu. In fact, it takes longer to boot than either of those!
 
Just remember: you cannot work miracles with 256MB of RAM and a older CPU slower than 1GHz. Mostly, some web pages will slow browsing down. Probably because of flash animations and other stuff. It's far from being painful though, and I get similar results as with a much newer machine running Win XP. In fact, I use it almost every day now.

---

### Post by earthpigg on 2010-08-12
> **admiralspark said:**
> 
Here are your options listed from easiest to hardest:

...

2) Puppy Linux

...

4) Debian network install--

...

5) last but no least--though certainly the hardest--build it from the bottom up with either Arch linux or Gentoo.

i'd actually consider arch easier than debian, but more time consuming. debian's documentation is more extensive, but arch's is easier to follow. for me, at least. i shudder to think of how time consuming it would be to compile stuff on a p2 or p4 with gentoo.

puppy is certainly not difficult to set up, but *using* it seems to be a different story entirely.

puppy 4 series is easy to set up, but the limited repos mean it will likely not be long before you are compiling from source.

puppy 5 has access to ubuntu's repositories, but i found accessing them to be very counter-intuitive. the GUI method isn't as easy as synaptic was the first time i used it, and there is no command-line method that compares favorably to apt or pacman.

i do like puppy, but i'd go for arch over puppy.

---

### Post by rtlustyo on 2010-08-12
FluxBox for the win!

---

### Post by MartyBuntu on 2010-08-12
Ubuntu goes on my fastest, most up to date machines.
My Windows license is relegated to a piece of junk old clunker.

---

### Post by jeffCC on 2010-08-27
I started with something similar, an old ThinkPad 700mhz and 128 mb running xubuntu 8.04, it LIVED in swap. Sometimes the hard drive would thrash for 20 minutes.
 Increased the ram to 512mb (all it can use, eBay find) 
Upgraded to 10.04, it got faster but still not great. 
Stripped xubuntu down to xfce, better still but only because it had so much room for improvement.
Finally, installed Fluxbox, got rid of Xfce and xfwm, with conky, nm-applet and xfce-power-manager all autostarting, it boots ready to work in under 66mb.
Firefox is still a little slow, but there are other browsers.

---

### Post by wilbuzz2 on 2010-10-09
256mb ram i do recommend  lubuntu I brought ram because i wanted xubuntu because of its looks it runs like a beast bringing up google chrome takes about 2 secs i had lubuntu when i had 256mb ram thats amazing for old hardware i really do recommend it

---

### Post by Kixtosh on 2010-10-09
As I stated earlier, Xubuntu will work with a 500MHz PII or PIII CPU, and just 256MB of RAM, but with the default XFCE desktop environment it is not that much faster than regular Ubuntu.

Xubuntu with LXDE is much better, but Lubuntu (which also uses LXDE) really seems to be the lightweight choice to watch right now. My suggestion:

1) If you already have Xubuntu installed on an old machine, and want to make it faster: add the LXDE lightweight desktop environment and be done with it.

2) If you haven't installed anything yet (other than Windows), or are working with Ubuntu and find it too slow (or any other major Linux O.S. for that matter): just get Lubuntu, it's terrific for older hardware.

3) If you want to use Google developed, internet based applications for text editing, spreadsheets and e-mail (rather than a regular word processor, spreadsheet application and e-mail client), just get Peppermint - but you'll need to have an internet connection available all the time. You can still also add any application from the Ubuntu Software Center though, so you're not stuck either. Peppermint is good!

4) If you don't want to wipe your hard drive, but still want an easy to use O.S. with all the basics you're ever likely to need, Puppy on a CD or USB drive will get the job done with flying colours: switching between one O.S. on the hard drive and another (on an external CD or USB drive) has never been so easy to do. Similarly, if you're still using Windows and aren't ready to wipe it off your hard drive, Puppy is a great way to introduce safe public browsing to your environment without touching one precious little hair on your Windows installation's little head!

---

### Post by Okeefenokee on 2011-03-30
450 mhz pentium2, 384 mb sdram, 80gb-8mb hdd.

my intention is to run a few old games and nothing else. no browser, no media, no power apps. just a few old games that will run fine on the hardware. i just need a bare bones OS that will run on it as well.

---

### Post by NightwishFan on 2011-03-30
> **Okeefenokee said:**
> 450 mhz pentium2, 384 mb sdram, 80gb-8mb hdd.

my intention is to run a few old games and nothing else. no browser, no media, no power apps. just a few old games that will run fine on the hardware. i just need a bare bones OS that will run on it as well.

You should probably start a new topic. Though I recommend Debian. You can download CDs with Gnome, LXDE, XFCE, or just a minimal one to install a base command line system than build up.
[http://www.debian.org/](http://www.debian.org/)

---

