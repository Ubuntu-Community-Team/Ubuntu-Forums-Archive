---
title: "re phone modem: what's needed and how to download for an offline computer"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by penguinv on 2010-01-03
I have a computer using 9.04 wubi and the only internet access right now would be dialup.

I want to download what is needed for doing that, modem drivers and program to dial and connect - and all the dependencies needed after the installation CD. I want to download it and put it on a flash card or better a CD I can keep and take it over to the needy computer.

I am sure that this was kept off for reasons of space and how many are sophisticated and connected by broadband but this is fundamental and should be provided as a easy to get module or package to download and take to the isolated computer.

Please help. And thanks so much in advance.

---

### Post by GeorgeVita on 2010-01-03
Hi ** penguinv**,
read [http://ubuntuforums.org/showthread.php?t=1368648](http://ubuntuforums.org/showthread.php?t=1368648)

(more at [http://ubuntuforums.org/showpost.php?p=8559050&postcount=132](http://ubuntuforums.org/showpost.php?p=8559050&postcount=132)
and [http://ubuntuforums.org/showpost.php?p=8559050&postcount=163](http://ubuntuforums.org/showpost.php?p=8559050&postcount=163))

which shows some 'offline' ideas, or follow my signature link to get wvdial (if it is enough for your application).

Regards,
George

---

### Post by Bartender on 2010-01-03
Saw [this]("http://ubuntuforums.org/showthread.php?t=1369558") recently, but don't know anything about it.

---

### Post by penguinv on 2010-01-20
> **GeorgeVita said:**
> Hi ** penguinv**,
read [http://ubuntuforums.org/showthread.php?t=1368648](http://ubuntuforums.org/showthread.php?t=1368648)

(more at [http://ubuntuforums.org/showpost.php?p=8559050&postcount=132](http://ubuntuforums.org/showpost.php?p=8559050&postcount=132)
and [http://ubuntuforums.org/showpost.php?p=8559050&postcount=163](http://ubuntuforums.org/showpost.php?p=8559050&postcount=163))

which shows some 'offline' ideas, or follow my signature link to get wvdial (if it is enough for your application).

Regards,
George

I'll follow up what you linked to. Thanks.

To take another tack, is there an older version of Ubuntu that comes with dialup capability?

---

### Post by Bartender on 2010-01-22
penguinv -
It doesn't matter what version of Ubuntu you install.  The biggest problem is the winmodem, the cheap, stripped-down modems in everyone's computers that rely on Windows to connect.  That's not something that's fully addressed in ANY Linux distro.

There are non-Ubuntu Linux OS'es that do a much better job than Ubuntu does at detecting winmodems, such as Puppy Linux.

But if you want to stick with Ubuntu and you want to use dial-up, you will have to make some accommodations.  Unless you have one of the very few winmodems "supported" in Linux, such as those used in the Dell Ubuntu PC's.

You live in LA?  Do you have access to a broadband-connected PC?  The best would be another Ubuntu PC that's had wget installed.  wget is a tiny program found in Synaptic.  If you had a good-sized thumb drive (at least 1GB) you could use the Package Download Script referred to in the post that GV links you to.  Living in or near LA means you should be able to find broadband (I use our library but I have a laptop) and you have access to a huge resource for used parts, like old USR external modems, etc.  Much better situation than living in Nepal or Moosehump, North Dakota.  

I've been experimenting with PDS, and found it very handy.  It's not the ultimate solution to dial-up woes, but with a little patience it goes a long way.  You're using wubi, so I don't know if this will help you any, but I'm going to post a PDS for Jaunty in the Dial-up Redux thread that lists all updates up to the present as soon as I get done here .

I just installed Jaunty clean to a PC yesterday (January 21), got online using pppconfig, asked Synaptic to Reload, waited for a freakin' hour or so, then created a PDS for all 235MB of packages that Synaptic said it needed to update.  If you had a genuine dual-boot, not wubi, all you'd have to do is set up the infrastructure at your end and run the PDS.

Does anyone know if wubi updates are in any way different than standard Ubuntu updates??

---

### Post by penguinv on 2010-01-29
Bartender,

That's a lot, and thanks! I wanted you to know that I saw it. It will take some time for me to absorb and try it. My other searches basically revealed posts saying, "I cant make it work."

I chose to get broadband (skip stories and gnashes and lies) and have learned a lot. But the money $$$ was more than I had thought. 

I still want to solve this problem though. I think it's possible to make a "liveCD" with a custom set of applications. I'd like to make one all set up for dial-up, naturally missing something else.

Meanwhile in my disguntledness I checked out Fedora and the docs that go with it have taught me a lot of the kind of things I have been strugging with in Ubuntu-land. I found more explanations of how linux works, and the meanings of terms. Some evidence of my stufggle is in my posts on Ubuntuforums.

---

### Post by Bartender on 2010-01-29
I've tried out the latest Fedora on a test PC.  It looked like a blue Ubuntu to me ;)

I've read several articles that describe Fedora as "cutting edge"...don't know what they mean by that exactly.  I kind of like the idea that Red Hat is behind the effort.

For me right now, I'm trying to tweak two dial-up PC's that are pretty much stuck at home by trotting downtown with the laptop to download discrete packages (such as Picasa for Linux or Handbrake) and/or Package Download Scripts.  It's less stressful and less of a time-suck to just keep everything in Ubuntu-land.

It's hard to grasp why remote downloads are so problematic, especially if you're used to .exe's in Windows-world.  Why can't it be like that in Linux?  Well, it *could*, but it's not.  The package managers know which dependencies you need, which is a great system when the PC you want to work on is online and the package managers can do their thing.  That same system makes it a bugger when the PC you want to work on isn't online.

The best compromise I've found so far, at least the one that isn't terribly geeky, is to use dial-up at home to at least reload your package lists, then create Package Download Scripts, then head into town with the laptop and PDS'es and notes for the heavy lifting.  The quoted threads (also linked in the bottom of my posts) have all or most of the information.  I've tried to keep it non-geeky, but they are somewhat long-winded.  George Vita, duncan, and others keep popping up with new ideas...yeah, it's *their* fault the threads are long-winded 8-[

I just re-read your first post, and there's something else I want to mention.  Windows updates are basically security-related.  There are some bug fixes, like in the Service Packs and such.  But standard programs like Windows Paint or what have you don't change.  

Open source is different.  Applications get overhauls along the way, and after the devs check them out they're placed into the repos.  The next time you go online, your package manager sees new versions of your apps and will try to get them.  That's the biggest reason why an "update" for Ubuntu can be 40, 50, or 90 MB.  This isn't a bug or a deficiency, it's the way it's supposed to be.  Of course, if you're on dial-up you might wish they'd just leave things alone!!

All you really need for a dial-up GUI is gnome-ppp and its dependencies.  There aren't many.

EDIT: I've been trying to figure out which internal modems and winmodems work in Ubuntu.  It's really hard to nail that down.  If I figure out anything new I'll be adding to the Dial-up Redux thread.

---

