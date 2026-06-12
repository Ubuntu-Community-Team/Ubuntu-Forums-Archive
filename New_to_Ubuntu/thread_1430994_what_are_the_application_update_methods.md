---
title: "what are the application update methods ?"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by davexnet on 2010-03-16
Hello,
I've had Ubuntu 8.10 installed for over a year,
but it's on a dual boot PC with XP, and unfortunately,
I've spent most of my time on XP.

It's shocking how little Ubuntu I've picked up.  I just haven't reached
the hump where I feel confident enough in it to start using it more.
Bit of a catch 22 perhaps.

Here's my question.  In general, I've noticed that the versions
of applications available through Synaptic tend to be old,
(for example Avidemux version 2.4.3) and no method through synaptic
exists to update to a newer version.

It's not just Avidemux, most of the apps on there are old.

What is involved in getting a newer version?  Is it a case of uninstalling
(through Synaptic) and reinstalling using some other method?
Please advise; help me through this blind spot.

Dave

---

### Post by J V on 2010-03-16
That is an old repository, and no longer as well maintained as the rest of the world... A new version will have up to date programs, or you can install manually (same way as windows, go to their website and download it)

---

### Post by davexnet on 2010-03-16
> **J V said:**
> ... A new version will have up to date programs

What new version?  Can I point Synaptic at a different repository ?
Please explian further.

---

### Post by egalvan on 2010-03-16
> **davexnet said:**
> Hello,
I've had Ubuntu 8.10 installed for over a year,


Here's my question.  In general, I've noticed that [B]the versions
of applications available through Synaptic tend to be old[/B],
(for example Avidemux version 2.4.3) and no method through synaptic
exists to update to a newer version.

It's not just Avidemux, most of the apps on there are old.

It's not Synaptic, it's the 8.10 (Intrepid) that you are running.

Ubuntu (among many distros) is based on the "point release" paradigm of software up-dates.
Which means that the versions of the programs are "frozen' at the date of release...
for example, 8.10 was released October of 2008.
Support is gone for this version.
The latest "regular" version is 9.10 (Karmic), which many have had troubles with...
most recommend 9.04 (Jaunty), which is already pushing a year old.

(Note.. the other paradigm is the "rolling release", which is used by other types of distros,
in which software is constantly updated.)


And actually, one *can* up-date *some* software to newer versions, but this requires enabling specific repositories...
Also, be aware that this can bring up stability issues, compatibility problems, and plain old bugs...
those are some of the reasons that versions are 'frozen'.

> 
What is involved in getting a newer version?  Is it a case of uninstalling
(through Synaptic) and reinstalling using some other method?
Please advise; help me through this blind spot.
Dave

Unless you are tied to an older version of Ubuntu, the easiest way is to upgrade to a newer version of Ubuntu...
please be aware that this can bring it's own set of problems...

Make sure you need (or really want) the newer versions of whatever software you are using... 
just because it's the 'latest-greatest' doesn't mean it's the 'best'.

The Long Term Support (LTS) versions of Ubuntu have security support for 3 years Desktop, and 5 years Server.
The latest LTS was Hardy, 8.04.
The next will be Lucid, 10.04, due out at the end of April.
I will be upgrading at the end of May (wait for the problems to settle down)
(yes, 8.04 is older than the 8.10 you are using, but it has longer support)


It's a balancing act... just like in Windows Land...
many Windows admins would not upgrade to the latest, 
in order to avoid compatibility/stability issues.

---

### Post by egalvan on 2010-03-16
> **davexnet said:**
> What new version?  C**an I point Synaptic at a different repository ?**
Please explian further.

No, you need to keep the repo that the version was based on.

You can try enabling "back-ports" and "proposed"...

but as my other post stated, 8.10 has reached "end-of-life".

If you *need* newer versions, then check on an updated Ubuntu.

---

### Post by davexnet on 2010-04-08
I never realized that Ubuntu (and perhaps other disto's ?)
were locked in this way.  I assumed it followed the windows paradigm -
you can keep installing updates to third party software
without issue.

(whether or not the updated third party software is better than the "older" version is really besides the point)

Having to install a new version of Ubuntu just so I can get a
later release of Avidemux seems on the face of it, ridiculous.

I enjoy Ubuntu for occasional use (and this is the kind of thing that 
keeps it "occasional") but I find this limitation perplexing.

How can a simple application 'destabilize" the OS?

---

### Post by nothingspecial on 2010-04-08
> **davexnet said:**
> 

Having to install a new version of Ubuntu just so I can get a
later release of Avidemux seems on the face of it, ridiculous.



If it does, perhaps look into a rolling release distro. A distro that updates for ever and ever and doesn`t need reinstalling.

The disadvantage with that, is sometimes new versions of perfectly good software break (unintentionally), then you have to fix it.

The advantage with a distro like ubuntu, that fixes it`s packages, is that they have been tested and are known to work. (This is not foolproof btw)

I have never found upgrading  problem. Just do it through the update manager.

---

### Post by davexnet on 2010-04-08
When you say you never found upgrading a problem,
are you referring to upgrading Ubuntu to 9.04 ?

What do you have in mind when you said "rolling release distro" ?
Something other than Ubuntu ?

---

### Post by HPD2 on 2010-04-08
> **davexnet said:**
> How can a simple application 'destabilize" the OS?

That is a fairly common occurrence even in windows.  Windows updates and hardware drivers can tank your machine.  Good example of this happened to my dad, we have a western digital world book for network storage.  For some reason or another my dads machine was not in the work group that the world book was in and windows would automatically install the driver for it.  This driver also had the side effect of making his front panel usb ports to stop working.  Another example a while ago Microsoft pushed out an update for IDE or sata controllers, don't remember right off hand.  This update caused a major issue, any drive that was connected through that specific cable didn't exist any more in the machines eyes.  Many machines could no longer see their hard drives so they could not boot in to windows.  You can argue that those aren't applications in the the sense that the user launches them like Firefox but they are applications that the system still needs to work.

In linux applications have dependencies.  These need to be installed and working for the application to run.  Some of the dependencies also are needed by the operating system and other programs so changing one could make an issue for the entire system.  thats my understanding on it at least.  Its probably wrong or could be said better, I hope that kinda helps.

---

### Post by davexnet on 2010-04-08
Thanks for trying to explain it to me.
I guess as a fairly experienced Windows user, someone trying to
get to grips with Linux, but so far haven't really progressed past the
beginner stage I'm trying to get to grips with some of these
high level, philosophical differences.

I'm not talking about a system or driver update, merely a utility.
It may use system services, but it doesn't modify them.

I'm talking about a new version of Amule, Avidemux, devede, amarok,
etc,etc.

---

### Post by nothingspecial on 2010-04-08
> **davexnet said:**
> When you say you never found upgrading a problem,
are you referring to upgrading Ubuntu to 9.04 ?

Well I started by upgrading through the update manager and later made myself a /home partition and reinstalled, without formatting it.

> **davexnet said:**
> What do you have in mind when you said "rolling release distro" ?
Something other than Ubuntu ?
[URL="http://en.wikipedia.org/wiki/Rolling_release"][COLOR="Cyan"]
wikipedia[/COLOR][/URL]

---

### Post by eriktheblu on 2010-04-08
> **davexnet said:**
> were locked in this way.  I assumed it followed the windows paradigm -
you can keep installing updates to third party software
without issue.It doesn't exactly work that way with Windows either. Many bits of software will degrade as the OS updates, and many application updates will require updated libraries. Ubuntu's goal from what I can tell is to include software that it knows to work well together, and update every 6 months.

> Having to install a new version of Ubuntu just so I can get a
later release of Avidemux seems on the face of it, ridiculous. Have you tried downloading the latest version from the Avidemux website? One of the binary packages may work for you, or you may be able to compile from the source.

> ...I find this limitation perplexing.

How can a simple application 'destabilize" the OS?

It's more likely that the application simply won't run on the OS. If you start replacing libraries in order to get it to work, that may result in other applications not functioning properly. After you manage to get all that straightened out, you might as well have just upgraded to the latest release.

Upgrading Ubuntu is not a difficult or prolonged endeavor.

---

### Post by davexnet on 2010-04-11
From what I can gather, looking at the getdeb site,
(the avidemux updates) it need Ubuntu to be at 9.04
to go forward.

Thanks for assisting with this perplexing issue.

---

