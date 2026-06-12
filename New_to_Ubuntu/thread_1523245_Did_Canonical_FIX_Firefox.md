---
title: "Did Canonical FIX Firefox ?????"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by Kellemora on 2010-07-03
Hi Gang

I Have another VERY INTERESTING download waiting in my Ubuntu Package Manager.

As a few of you may already know, the last known fully functional version of Firefox was version 3.6.3!

When Mozilla released version 3.6.4 it was inundated with BUGS...  Would not run at all on Windoze XP-Pro-MCE and on XP-PRO it would load and run, but had SERIOUS memory leak problems.  
Mozilla quickly issued version 3.6.5 which fixed a couple of bugs, but not all of them, then they issued 3.6.6 the following day with even more serious memory leaks and problems.

Over the past couple of days, these NON WORKING Firefox programs appeared in our System Package Manager auto-upgrade to install.

Today I see yet another, it's still marked Firefox 3.6.6 but NOW includes CANONICAL 1.0 with it.......

I only downloaded the newer versions on test machines.  I'm still using the last known working Firefox Linux version 3.0.19 on my main machines.

On WinDoze machines you can reinstall older working versions of Firefox no problem.  Have no idea how to do that on Ubuntu.  But would like to BLOCK the Firefox 3.6.6  from our System Package Manager's auto-upgrade so it doesn't get installed accidentally with something else.

And does anyone know why it now says Canononical 1.0?????
Did they FIX the BUGS Firefox added with version 3.6.4 and beyond?????

TTUL
Gary

---

### Post by bodhi.zazen on 2010-07-03
Canonical does not maintain Firefox

Firefox is a third party application and depending on where you installed it from (ppa ? ) the people simply re-package the firefox binary or source code into a .deb , they do not modify the source code beyond what is needed to make a .deb

If there is a bug in Firefox it would be reported "upstream" ie to mozilla.

---

### Post by -humanaut- on 2010-07-03
The Canonical package is probably the Firefox branding/theme. (ubufox or whatever its called)

---

### Post by Kellemora on 2010-07-03
Hi BZ

This is the first time I've ever seen the name Canononical associated with Firefox's auto-upgrade from Canononical, 

I was actually hoping they would have fixed the bugs in the new release, but I guess that was wishful thinking.

I've used Firefox for years now, but Mozilla really messed it up big time with the 3.6.4 release!  3.6.5 and 3.6.6 fixes only made it worse.

So I guess now I'll have to figure out how to block in somehow.  As it's in the Ubuntu auto-updates along with 25 other updates.

I want to keep version 3.0.19 until I know they fixed all the bugs they just added to Firefox.

Thanks!

TTUL
Gary

---

### Post by QIII on 2010-07-03
I don't think Canonical did anything to Firefox.

It says "Mozilla Firefox for Ubuntu canonical - 1.0", it does not say "Mozilla Firefox modified by Canonical - 1.0"

For one, I don't think anyone at Canonical would spell it "canonical" - forgetting capitalization.

This is a package that Mozilla made available for the repos.  As frustrating as it is -- and I certainly don't blame anyone for frustration -- the credit for whatever problems you are encountering goes to Mozilla.

I would like to know what testing tools you used to determine that Firefox is leaking memory.  It would be worth finding out so that it can be reported.

Using a lot of memory is one thing.  Leaking it is extremely serious.

---

### Post by lovinglinux on 2010-07-04
There is no such thing as Firefox 3.6.5. Mozilla updated Firefox directly from 3.6.4 to 3.6.6 not because it was inundated with bugs, but because some users were experiencing issues with the plugin crash protection timeout. Basically, when an user was for example uploading a file through a flash based uploader, Firefox was thinking flash crashed because the timeout limit was too short. So [version 3.6.6 only increases that timeout](http://www.mozilla.com/en-US/firefox/3.6.6/releasenotes/), to avoid stopping the flash process unnecessarily.

Anyway, this is the first time Canonical pushes a major update of Firefox to a stable version of Ubuntu, since Firefox 3.0.19 (currently available in Hardy) is the last supported version of the 3.0 series. Mozilla is no longer supporting Firefox 3. So, pushing that update to Hardy is not an easy task. Some bugs are expected, but this is not Firefox fault and probably not Canonical fault, since there aren't many beta testers for that upgrade.

Anyway, I'm using Firefox 3.6.4 and above on Lucid for a long time and don't have any problems whatsoever. Some users had a few issues with the first update of Firefox 3.6.6 pushed from the repositories, but it seems these problems have already been fixed and the packages updated.

I don't have any memory leak problems with Firefox 3.6.4. It is currently using 178 Mb of memory, but I have more than 50 extensions installed. Unless your Firefox is using something like 800 Mb, then I don't think you have memory leaks. How much memory your Firefox uses?

I would advise to start Firefox in safe mode to see if the problem persists. If not, then is an extension causing the leak, which is not uncommon. I also recommend to create a new user profile, since a corrupted profile might be the source of your problems. Also update your extensions.

I haven't tested Firefox 3.6.6, but I will do today, just to see how it goes.

---

### Post by warfacegod on 2010-07-04
If you revert back to 3.6.3 you can then lock in that version using Synaptic. Under the Packages menu (top left) click "Lock Version". I don't recall off hand which package(s) need to be marked in this way.

---

### Post by lovinglinux on 2010-07-04
> **warfacegod said:**
> If you revert back to 3.6.3 you can then lock in that version using Synaptic. Under the Packages menu (top left) click "Lock Version". I don't recall off hand which package(s) need to be marked in this way.

I don't think version 3.6.3 is available to Hardy users.

---

### Post by warfacegod on 2010-07-04
> **lovinglinux said:**
> I don't think version 3.6.3 is available to Hardy users.

Okay, so I missed that in the user profile:biggrin::tongue: but I don't think Kellemora was being all that clear about which OS was involved bringing up 3.6.3, test computers, main computer, and all that.

---

### Post by philinux on 2010-07-04
[http://packages.ubuntu.com/hardy/allpackages](http://packages.ubuntu.com/hardy/allpackages)

According to this 3.6.6 is there now.

firefox  (3.6.6+nobinonly-0ubuntu0.8.04.2 [amd64, i386], 3.0~b5+nobinonly-0ubuntu3 [all]) [security]

---

### Post by lovinglinux on 2010-07-04
> **warfacegod said:**
> Okay, so I missed that in the user profile:biggrin::tongue: but I don't think Kellemora was being all that clear about which OS was involved bringing up 3.6.3, test computers, main computer, and all that.

Indeed :)

> **philinux said:**
> [http://packages.ubuntu.com/hardy/allpackages](http://packages.ubuntu.com/hardy/allpackages)

According to this 3.6.6 is there now.

firefox  (3.6.6+nobinonly-0ubuntu0.8.04.2 [amd64, i386], 3.0~b5+nobinonly-0ubuntu3 [all]) [security]

Yes. As far as I know Hardy users went from 3.0.19 to 3.6.4, then 3.6.6. At least that was the plan, so there is no 3.6.3 to downgrade to.

---

### Post by lovinglinux on 2010-07-04
I'm running Firefox 3.6.6 now. I don't see any memory leak or any other problem.

---

### Post by ulsterman on 2010-07-04
Hi!

The only problem I can see with the current auto upgrade version of firefox on Lucid is the occasional re-size problem which, although still there, is getting less frequent.

Ken

---

### Post by PPPilot on 2010-07-04
I'm running Firefox 3.6.6 on Lucid and I am having two problems. 

1. From time to time, Firefox will not close and when I kill it, it leaves the firefox.bin process running and I have to kill that in System Monitor.

2. From time to time my machine slows down and I find that the plugin-container process has run my CPU to 100%. Again I have to kill it using System Monitor.

In both cases I can restart Firefox and all is well until the next time. This happens every few days. I have not seen any memory leak problems....

---

### Post by lovinglinux on 2010-08-05
> **PPPilot said:**
> 2. From time to time my machine slows down and I find that the plugin-container process has run my CPU to 100%. Again I have to kill it using System Monitor.

That's probably flash using your CPU.

---

### Post by PPPilot on 2010-08-05
Yes, Adobe needs to do some work on the Flash Plugin. Nothing new there I guess

---

### Post by Kellemora on 2010-08-05
Well, on Hardy I now have version 3.6.8  But I can run a punch test on Linux, don't have the software for it.

And for LovingLinux, there DEFINITELY WAS a version 3.6.5 but it was only out for about 10 to 16 hours before they realized it was messed up worse.
I had updated from 3.6.4 after I found the bugs in it to 3.6.5 the next day at lunch, and after dinner 3.6.6 was out already, still with the same bugs.

Using the DOZE I can run a punch test and there are definite problems that started with version 3.6.4 with Flash.  It flat out loses cell data.
SO, my couple of DOZE machines are LOCKED IN at version 3.6.3 and I made backups of version 3.6.3 just so I could test each new release to see if they fixed the problems they introduced yet.

Again, the problems appeared with version 3.6.4 and remained in version 3.6.5, 3.6.6, 3.6.7 and now 3.6.8........

It takes quite a bit of setting up to run the tests, but once the grid is in place over the screen and you can see the cells, it will mark those cells, but not recognized they are marked.

For those who play games, this is a DISASTROUS CHANGE to Firefox!  They can't afford lost data, lost coins and lost XP points because of Firefox's BUGS.......  Many have already moved to Chrome, or did like I did, went back to version 3.6.3 which worked perfectly.

TTUL
Gary

---

### Post by lovinglinux on 2010-08-05
> **Kellemora said:**
> And for LovingLinux, there DEFINITELY WAS a version 3.6.5 but it was only out for about 10 to 16 hours before they realized it was messed up worse.
I had updated from 3.6.4 after I found the bugs in it to 3.6.5 the next day at lunch, and after dinner 3.6.6 was out already, still with the same bugs.

Perhaps you are talking about 3.6.5pre, which was automatically created in the nightly directory when version 3.6.4 was officially released. But an official final release of Firefox 3.6.5 to the public was never made. They simply renamed 3.6.5pre to 3.6.6, fixed the plugin crash delay and released it. You can find the reason [here]("http://christian.legnitto.com/blog/2010/06/09/heads-up-the-next-firefox-platform-version-is-1-9-2-6-instead-of-1-9-2-5/").  There is no such version in the FTP release directory, no release version info page, no nothing. They wouldn't simply make it disappear to cover up any mistake.

See released versions at [https://wiki.mozilla.org/Releases](https://wiki.mozilla.org/Releases)

Anyway, I'm running Firefox 4.0b3 now, so this subject is becoming old an boring. Move on.

---

### Post by Kellemora on 2010-08-06
You're absolutely right there LovingLinux!

I am moving on, from FireFox to Chrome and from Ubuntu to Debian!

TaTa

---

### Post by NightwishFan on 2010-08-06
> **Kellemora said:**
> You're absolutely right there LovingLinux!

I am moving on, from FireFox to Chrome and from Ubuntu to Debian!

TaTa

Tata *rolls eyes*

---

