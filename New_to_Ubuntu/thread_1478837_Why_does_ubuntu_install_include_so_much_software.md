---
title: "Why does ubuntu install include so much software?"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by utubun on 2010-05-10
I'm in the process of discovering Ubuntu, after years of frustration with Windows. Despite some initial technical hassles, I am really loving the system.

One general issue that puzzles me is this:

A major annoyance with Windows is that it includes all sorts of programs and utilities that I don't want. I had imagined that Ubuntu would be a much leaner install, but was surprised at the number of programs that were automatically installed. For instance, I do not use or want chat services or games, but got these anyway. I appreciate that I can easily remove the unwanted stuff through the software centre, but this takes quite a bit of time.

Why is all this stuff included in the install? Would it be difficult to create a cutomisation menu for the install, via which the user could select/deselect software?

This is a genuine query, and in no way a complaint. I am massively impressed by ubuntu; just a bit puzzled that more 'stripped down' installs aren't readily available.

---

### Post by nitstorm on 2010-05-10
You could do a minimal install of Ubuntu and add whatever programs you need from there.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Here's the community documentation on that too :[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by rasmus91 on 2010-05-10
> Why is all this stuff included in the install? Would it be difficult to create a cutomisation menu for the install, via which the user could select/deselect software?

This is a genuine query, and in no way a complaint. I am massively impressed by ubuntu; just a bit puzzled that more 'stripped down' installs aren't readily available.

Well, i have wondered about the same thing. But i Guess it is because this is what most people think of when they think of a desktop OS

Also, They can put it on the disc and still have a 15 minute install time. guess thats quite acceptable.
Also, for the convenience of people used to these programs in windows, it might be nice to have something as standard.

but again, thats my guess.

---

### Post by utubun on 2010-05-10
I should have known it had been taken care of. I wish I had searched properly for this before installing my system.

Thanks.

---

### Post by Paqman on 2010-05-10
+1 for the Minimal ISO, check my sig for a script to help set it up.

You can go for the core Gnome system, which doesn't come with any additional software. I'd also install package management tools, printing, Bluetooth, etc. The script will sort all that out for you.

---

### Post by John Bean on 2010-05-10
> **utubun said:**
> I should have known it had been taken care of. I wish I had searched properly for this before installing my system.

Who knows - you may discover things on the full install that you actually like (and want to keep) but would never have dreamed of installing from a minimal base install.

---

### Post by cap10Ibraim on 2010-05-10
With 10.04 Gimp was not included I think the limit is the CD disk space 700 MB if they need more space they will take out some apps

---

### Post by 3rdalbum on 2010-05-10
It's pretty much done "because they can" fit it onto the CD, and also to help new users - let's face it, a new user is rapidly going to be confused about the wide range of music players on Linux; better to give them one to start off with and see how they like it.

You'd probably be disgusted with how most other Linux distributions looked like in 2005. They came with five text editors, four web browsers, three music players, two office suites and a partridge in a pear tree.

---

### Post by Grenage on 2010-05-10
Absolutely, if it was stable and in development - it was probably on the CD!

I think that because of kind of distro Ubuntu is (newbie-orientated), it's a good idea to have a lot of popular software bundled.

---

### Post by Sealbhach on 2010-05-10
Most Linux distros come with a selection of software that the average user would probably want. Because there are no pricing or licensing issues, the challenge is to pick a good selection of applications that people would find useful, and integrate them into the desktop environment as seamlessly as possible.

As mentioned already, you can go for the minimal install if you wish.

.

---

### Post by mörgæs on 2010-05-10
Here is more on the minimal:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

---

### Post by FinnMan on 2010-05-10
I haven't installed Ubuntu yet, only played with the LiveCD. Is there no way to choose what to install? That sounds really weird. Even if more stuff is included on the CD, why automatically install everything? :?

Personally, I don't engage in "social notworking" and all of that crap is totally unnecessary. ;) Well, I do use IRC, but I just want a simple client for that. I'm sure this won't be a big issue for me, however.

What I find surprising, is that I was told Ubuntu doesn't come with a C compiler, because most software for Linux is distributed as source. I was also told one is not available via the Software Center, so I must apt-get gcc?

PS. Regarding Gimp, I was amused, when I read the *Linux Mint* description, I think, that it comes with easy-to-use software everybody needs. Such as Gimp. Yeah. That's very easy to use! :D

---

### Post by Paqman on 2010-05-10
> **FinnMan said:**
> I haven't installed Ubuntu yet, only played with the LiveCD. Is there no way to choose what to install? That sounds really weird. Even if more stuff is included on the CD, why automatically install everything? :?


It doesn't include "everything". It includes one app in each of several main categories (eg: web browser, file browser, IM client, etc).

Gnome is designed to be a complete environment that's usable from the moment it's installed.

> 
What I find surprising, is that I was told Ubuntu doesn't come with a C compiler, because most software for Linux is distributed as source. I was also told one is not available via the Software Center, so I must apt-get gcc?

Software Centre only includes graphical desktop apps, but you can install anything in the repos using Synaptic, or the command line as you say. Almost all software for Ubuntu is distributed as binaries, compiling from source is only used as a last resort. I haven't compiled anything in years, and would be very happy if I never did again.

---

### Post by lykwydchykyn on 2010-05-10
To appreciate the way it is, you have to understand how it was.

About ten years ago, most big Linux distros came on 3-4 discs.  They booted to an installer, and you had to go through and select the software you wanted during install.  I remember installing redhat this way a few times.

When the live CD install came along with Knoppix, Mepis, Ubuntu, and others, it was a revolution:
 - You could test your computer to see if everything worked before installing.
 - You had a complete usable system-on-a-disc that you could take anywhere
 - People without broadband access, or who didn't want to juggle a bunch of discs, could have a basic, usable desktop out-of-the-box.
 - Most importantly, new users who had never laid eyes on a Linux desktop didn't have to dig through a huge list of unfamiliar packages wondering which ones were actually useful and which ones were antiquated cruft for people who wanted to wax nostaligic about NeXT or Irix;  You had a nice best-of-breed selection of software preinstalled and ready to use.


The driving ethos behind the Ubuntu installer is simplicity; ask the user the minimum number of questions required to get a working Ubuntu desktop installed.  I think that's awesome.  

Of course, when you graduate from that, it's not so awesome.  But that's why there's alternate/minimal install, other distros, etc.

---

### Post by Paddy Landau on 2010-05-10
One more thing often forgotten is the size of Ubuntu.

A standard Windows installation these days *without *the extra programs comes to over 20Gb, I think.

A standard Ubuntu installation *with* all the extra programs comes to under 5Gb, and still manages to run faster.

It's hardly a problem that those programs are included.

---

### Post by nikhilbhardwaj on 2010-05-10
a lot of people have a slow internet connection
it helps if the basic apps are installed by default

---

### Post by cascade9 on 2010-05-10
> **Paddy Landau said:**
> A standard Ubuntu installation *with* all the extra programs comes to under 5Gb, and still manages to run faster.

It's hardly a problem that those programs are included.

Run faster than vista? Yes (and maybe win7). XP can be faster than newer ubuntus though (yes, I know, its old...but still the most used OS in the world)

Its not really a 'problem', but a standard ubuntu install is slower, and heavier on RAM than distros that come without all the bloa... opps, fluff. ;)

---

### Post by Paddy Landau on 2010-05-10
> **cascade9 said:**
> Run faster than vista?
In my experience, w-a-y faster; even faster than XP.
YMMV

> **cascade9 said:**
> Its not really a 'problem', but a standard ubuntu install is slower, and heavier on RAM than distros that come without all the bloa... opps, fluff. ;)
Yes, of course you're right. However, most people want a system that "just works" -- in the same way that I want a car that "just works", even if the air conditioning does slow it down a little.

---

### Post by rasmus91 on 2010-05-13
> What I find surprising, is that I was told Ubuntu doesn't come with a C compiler, because most software for Linux is distributed as source. I was also told one is not available via the Software Center, so I must apt-get gcc?

Mine had gcc as standard

> In my experience, w-a-y faster; even faster than XP.

+1 on that

---

### Post by wojox on 2010-05-13
> 
What I find surprising, is that I was told Ubuntu doesn't come with a C compiler, because most software for Linux is distributed as source. I was also told one is not available via the Software Center, so I must apt-get gcc? 


Install:

```
sudo apt-get install build-essential
```

---

### Post by Dayofswords on 2010-05-13
> **rasmus91 said:**
> > What I find surprising, is that I was told Ubuntu doesn't come with a C compiler, because most software for Linux is distributed as source. I was also told one is not available via the Software Center, so I must apt-get gcc? Mine had gcc as standard

yep, gcc here

---

### Post by cascade9 on 2010-05-13
> **Paddy Landau said:**
> In my experience, w-a-y faster; even faster than XP.
YMMV

On newer systems, ubuntu isnt any slower (and can well be faster, if you compare a 'average users' 1-3 year old WinXP with half a million bits of useless software). On the older systems I have, newer ubuntus are slower than XP- mind you, I ran a fairly light XP with no crapware, etc. which makes a big difference. 

> **Paddy Landau said:**
> 
Yes, of course you're right. However, most people want a system that "just works" -- in the same way that I want a car that "just works", even if the air conditioning does slow it down a little.

Fair enough, and that is the reason why ubuntu does come with the amount of software it does. I' go a bit past just 'aircon' on the car analogy, its more like aircon, bullbar, snorkel, roofracks, and chains on the tires LOL. 

Yeah, I know, I'm one of these people that just dont need a lot of the stuff ubuntu comes with.

---

### Post by julio_cortez on 2010-05-13
> **cascade9 said:**
> Fair enough, and that is the reason why ubuntu does come with the amount of software it does. I' go a bit past just 'aircon' on the car analogy, its more like aircon, bullbar, snorkel, roofracks, and chains on the tires LOL.
Indeed. But it's like having chains in the trunk: they take away a little space in the trunk of your car, but they don't slow the car down until they're actually put on the tyres.
The same way, Brasero will use a small amount of your disk space once you install Ubuntu but won't affect the speed of your machine until it's launched.

Honestly, I prefer an OS that has quite everything straight out of the box (and everything else I may need just an *apt-get* far from where I am) than an OS to which I have to install everything (Microsoft, I'm looking at you).

---

### Post by cascade9 on 2010-05-14
> **julio_cortez said:**
> Indeed. But it's like having chains in the trunk: they take away a little space in the trunk of your car, but they don't slow the car down until they're actually put on the tyres.
The same way, Brasero will use a small amount of your disk space once you install Ubuntu but won't affect the speed of your machine until it's launched.

Well, actually, the extra packages ubuntu has in a standard install does slow the computer down. See these articles for some idea of how much (ys, I admit, they arent current anymore but its vaild...as far as I know newer versions of ubuntu do things the same way)- 

[http://distrowatch.com/weekly.php?issue=20090427#feature](http://distrowatch.com/weekly.php?issue=20090427#feature)

[http://distrowatch.com/weekly.php?issue=20090504#feature](http://distrowatch.com/weekly.php?issue=20090504#feature)

> **julio_cortez said:**
> 
Honestly, I prefer an OS that has quite everything straight out of the box (and everything else I may need just an *apt-get* far from where I am) than an OS to which I have to install everything (Microsoft, I'm looking at you).

I dont, but like I said, I know I like fairly minimal install. 

I'd rather have a microsoft OS with the bare minimum of installed software, I used to spend a bit of time removing unneeded junk from XP (using nLite). Most of it was stuff I really didnt need (who needs the Ali drivers these days? I sure dont) or microsoft programs that I had better versions of anyway (VLC + foobar, not WMP, firefox, not IE, etc).

---

### Post by GSF1200S on 2010-05-14
No war or animosity intended Cascade9, but ill put my year old Arch install up against a brand new XP install ;)

I think Ubuntu does it right- its aimed to help new users (while still enabling experienced users). Ubuntu (well, Xubuntu) and Arch are my two favorite distros, and they are completely different than one another. 

To the OP, there are other distros which focus on simplicity and installing nothing extra- Gentoo and Arch are examples. Other distros throw all kinds of packages, even 4 or 5 programs of the same type (i.e. music player)- take PCLos or Mepis (at least the last time I used it) for example. Others try and use one app for each purpose, like Ubuntu.

Remember, choice is a good thing ;)

---

### Post by cascade9 on 2010-05-14
> **GSF1200S said:**
> No war or animosity intended Cascade9, but ill put my year old Arch install up against a brand new XP install ;)

No animosity taken at all ;) 

In 95%+ of cases, your arch will eat a new XP alive. Even if I nLited XP to within an inch of its life, arch would still be faster. Of coruse, given the option I could skew the playing field- I would bet XP would run better on a 192MB/Pentium3 machine than Arch with KDE. Thats not really fair though. :) 


> **GSF1200S said:**
> 
I think Ubuntu does it right- its aimed to help new users (while still enabling experienced users). Ubuntu (well, Xubuntu) and Arch are my two favorite distros, and they are completely different than one another. 

To the OP, there are other distros which focus on simplicity and installing nothing extra- Gentoo and Arch are examples. Other distros throw all kinds of packages, even 4 or 5 programs of the same type (i.e. music player)- take PCLos or Mepis (at least the last time I used it) for example. Others try and use one app for each purpose, like Ubuntu.

Remember, choice is a good thing ;)

Well...IMO is in a no win situation. If they put lots of stuff into a standard ubuntu (or 'x' or 'k' ubuntu etc) then its never going to be as fast as it could be. Which will make it look worse than it should (due to speed)...but if they stripped it out to make it faster, its going to make a lot of new users mad with fustration. 

Suprising that you like Arch and Xubuntu- I admit that I'm not found of Xubuntu, as least a normal install of it. One of my favourite distros is Debian Xfce, and Xubuntu feels so.....fat....compared to Deb Xfce. 

Its not as slow as it could be- I installed PCLinuxOS (2010, Xfce version) on a machine a few days ago and its horribly slow. Its a Celeron P4, 2.0Ghz, 768MB DDR, nVidia GF4-MX440, and it is SLOWER with PCLinuxOS on it than my (I think dead now :( ) P3 866, 512MB SD RAM, Intel i810 video was with Xubuntu. BTW, with that PCLinuxOS install, there was only 1 video player (gxine) and one audio player (cant recall now). I really need to install a different distro, that I've used before, on the Celeron box to have a better comparison though.

In the end, I agree, ubuntu probably does take the right course. Its just a pity that there is no 'middle way'- not the full blown install of ubuntu, and not having to do everything from a minimal install. I've got an idea that would get around that, but I dont think that the ubuntu devs would implement it.

---

