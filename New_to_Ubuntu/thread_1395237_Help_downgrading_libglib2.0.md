---
title: "Help downgrading libglib2.0"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by bpowell2005 on 2010-01-31
This thread is solved...excellent directions posted in this thread that helped me downgrade libglib2.0 and it's related files without any other program removal. Computer is fixed!



Hello All,

I ran updates today, and libglib2.0 upgraded to 2.22.3...which is unstable...now when I click on my trash can, computer, or network, Nautilus segfaults.

It looks like the "fix" is to revert libglib2.0 to version 2.20. I can highlight the package and select "force version"...however, when I do that, I get a warning that to complete this task, the following programs must be removed: And in this list are basically everything needed to run Ubuntu...Brasero, Gnome, etc. (must be 50+ packages)

How can I revert my libglib2.0 version without destroying my OS?

Thanks!

---

### Post by bpowell2005 on 2010-01-31
Anybody? I'm nervious to let the package manager proceed becuase I think I'm going to lose all the packages it says it's going to remove...(no reason to think it's lying!)

How can I downgrade libglib2.0 to a stable version?

Thanks!

---

### Post by bpowell2005 on 2010-01-31
I'm starting to think from the lack of replies this might not be possible given how ingrained libglib 2.0 appears to be in the system. I really don't want to upgrade to Karmic just to see if it'll fix this...this is the first Ubuntu problem I've not been able to correct.

---

### Post by Temposs on 2010-01-31
You would lose all the packages it says. So, you don't want to do it with that method.

---

### Post by Temposs on 2010-01-31
Are you sure it's libglib2.0 that's causing the issue?

---

### Post by bpowell2005 on 2010-01-31
> **Temposs said:**
> Are you sure it's libglib2.0 that's causing the issue?

I've seen lots of posts about a similear problem...I have all the symptoms...if I click my trash icon, segfault....if I go "Places" compter, Segfault...if I go "Places" Network, segfault...all of this was working as recently as yesterday...apparently libglib2.0-2.22.3 is unstable? But it came across in my updates, and now I'm broken down.

I'm open to other suggestions though!

---

### Post by Temposs on 2010-01-31
You could try to activate the pre-release repository to get a stable version of libglib2.0 ASAP. Then once it's out, deactivate the pre-release repository.

---

### Post by bpowell2005 on 2010-01-31
> **Temposs said:**
> You could try to activate the pre-release repository to get a stable version of libglib2.0 ASAP. Then once it's out, deactivate the pre-release repository.

Thanks for the idea...I went into my package manager and see that Pre-Release (Jaunty Proposed) is already enabled? Don't remember doing that...I wonder if that's why I got this bum version? Perhaps this IS a pre-release that shouldn't go out!

I've filed a bug report as well.

---

### Post by Temposs on 2010-01-31
That could be why you have an unstable version...not sure if it can be rolled back but...

I guess what you should do is just keep the pre-release repo checked until the issue gets solved, then uncheck the pre-release repo so you don't get any more of these issues with unstable packages.

---

### Post by bpowell2005 on 2010-01-31
> **Temposs said:**
> That could be why you have an unstable version...not sure if it can be rolled back but...

I guess what you should do is just keep the pre-release repo checked until the issue gets solved, then uncheck the pre-release repo so you don't get any more of these issues with unstable packages.

That sounds like a plan...don't remember checking the pre-release though...that's not my style to go "bleeding edge"...for exactly this reason!

---

### Post by kayvortex on 2010-01-31
I've never done this, but (so says the man page) you can specify a package version to install like this:
```
sudo aptitude install *package***=*version***
```

Now, just to see what would happen, I ran this on my (Karmic) machine:
```
aptitude --simulate libglib2.0-0=2.22.2-0ubuntu1
```
and the output I got was:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following packages are BROKEN:
  libglib2.0-data libglib2.0-dev 
The following packages will be DOWNGRADED:
  libglib2.0-0 
0 packages upgraded, 0 newly installed, 1 downgraded, 0 to remove and 0 not upgraded.
Need to get 996kB of archives. After unpacking 4,096B will be freed.
The following packages have unmet dependencies:
  libglib2.0-data: Depends: libglib2.0-0 (>= 2.22.3-0ubuntu1) but 2.22.2-0ubuntu1 is to be installed.
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.22.3-0ubuntu1) but 2.22.2-0ubuntu1 is to be installed.
The following actions will resolve these dependencies:

Downgrade the following packages:
libglib2.0-data [2.22.3-0ubuntu1 (karmic-updates, now) -> 2.22.2-0ubuntu1
(karmic)]
libglib2.0-dev [2.22.3-0ubuntu1 (karmic-updates, now) -> 2.22.2-0ubuntu1
(karmic)]

Score is 50

Accept this solution? [Y/n/q/?]


So, aptitude seems to find this a pretty trivial ask, only asking that libglib2.0-data and libglib2.0-dev be downgraded to version 2.22.2-0ubuntu1 too.

So, to downgrade your package, just install it again with a version number appended to the package. Use aptitude **with a --simulate flag** to check what it needs to do to downgrade your libglib package without breaking your system before you actually do it!

However, don't rush into downgrading things: find out for sure which packages are at fault, and also check to see whether fixes exist.

---

### Post by bpowell2005 on 2010-02-01
> **kayvortex said:**
> I've never done this, but (so says the man page) you can specify a package version to install like this:
```
sudo aptitude install *package***=*version***
```

Now, just to see what would happen, I ran this on my (Karmic) machine:
```
aptitude --simulate libglib2.0-0=2.22.2-0ubuntu1
```
and the output I got was:


So, aptitude seems to find this a pretty trivial ask, only asking that libglib2.0-data and libglib2.0-dev be downgraded to version 2.22.2-0ubuntu1 too.

So, to downgrade your package, just install it again with a version number appended to the package. Use aptitude **with a --simulate flag** to check what it needs to do to downgrade your libglib package without breaking your system before you actually do it!

However, don't rush into downgrading things: find out for sure which packages are at fault, and also check to see whether fixes exist.

Kayvortex: Thank you for the code example...I also tried a simulation, and my computer wants to downgrade libsoup as well...I'm just headed to work, so can't investigate now, but will look into this more when I get home. However, it did NOT want to remove every package installed (as Synaptic does...) so that's a good sign!

Thank you again!

---

### Post by crh0831 on 2010-02-01
I can report that I, too, had the same problem today on my Jaunty install after yesterday's updates.  After reading the solution here to rollback to the previous version of libglib I was able to successfully open a "Network" connection again.

The command that worked for me was 

```
aptitude install libglib2.0-0=2.20.1-0ubuntu2.1
```

The computer warned me of three other programs that would be affected and offered to downgrade them as well.  I accepted the solution and everything went through fine.

Now ... how will I know when a fix has been posted so I can do updates again?

---

### Post by kayvortex on 2010-02-01
> Now ... how will I know when a fix has been posted so I can do updates again? 

Taking a more extensive read of the aptitude man page, it has an entry:
> forbid-version
           Forbid a package from being upgraded to a particular version. This
           will prevent aptitude from automatically upgrading to this version,
           but will allow automatic upgrades to future versions. By default,
           aptitude will select the version to which the package would
           normally be upgraded; you may override this selection by appending
           &#8220;=<version>&#8221; to the package name: for instance, &#8220;aptitude
           forbid-version vim=1.2.3.broken-4&#8221;.

           This command is useful for avoiding broken versions of packages
           without having to set and clear manual holds. If you decide you
           really want the forbidden version after all, the &#8220;install&#8221; command
           will remove the ban.


I don't know whether aptitude will have marked libglib2.0-0 as being on hold, so, first, enter:
```
sudo aptitude unhold libglib2.0-0
```
If aptitude comes back telling you libglib isn't on hold, then fine.

Then, I'd imagine that you'd need to enter:
```
sudo aptitude forbid-version libglib2.0-0
```
According to the man page, since you have not entered a version number aptitude will forbid the latest version which it would otherwise update to, which is the 2.22.3 version that apparently is causing problems.

Next, run an update and full-upgrade to check that it's doing what you want to do (i.e. not updating libglib to version 2.22.3):
```

sudo aptitude update
sudo aptitude --simulate full-upgrade

```
Check to see that libglib isn't in the list of packages to upgrade, and post if it is.

---

### Post by crh0831 on 2010-02-01
> 
According to the man page, since you have not entered a version number aptitude will forbid the latest version which it would otherwise update to, which is the 2.22.3 version that apparently is causing problems.According to my apt log entry 
```

Preparing to replace libglib2.0-0 2.20.1-0ubuntu2.1 (using .../libglib2.0-0_2.22.3-0ubuntu2-ppa2~jaunty_i386.deb) ...

```libglib2.0-0_2.22.3 was indeed the culprit in my case.

Thanks for the insight!

---

### Post by bpowell2005 on 2010-02-01
> **kayvortex said:**
> Taking a more extensive read of the aptitude man page, it has an entry:


I don't know whether aptitude will have marked libglib2.0-0 as being on hold, so, first, enter:
```
sudo aptitude unhold libglib2.0-0
```
If aptitude comes back telling you libglib isn't on hold, then fine.

Then, I'd imagine that you'd need to enter:
```
sudo aptitude forbid-version libglib2.0-0
```
According to the man page, since you have not entered a version number aptitude will forbid the latest version which it would otherwise update to, which is the 2.22.3 version that apparently is causing problems.

Next, run an update and full-upgrade to check that it's doing what you want to do (i.e. not updating libglib to version 2.22.3):
```

sudo aptitude update
sudo aptitude --simulate full-upgrade

```
Check to see that libglib isn't in the list of packages to upgrade, and post if it is.

Thanks for all the tips. I was able to downgrade the libglib2.0 no problem...aptitude wanted to also downgrade some related data files, and libsoup...after all that, I'm back in business and the problem is fixed.

I've tried to forbid-version, but I'm not sure that's working...the command appears to "take" however, when I run a simulated upgrade, aptitude says it's still going to upgrade libglib...so, I've opted to lock the version in Synaptic...so for now, that's a work-around that I'll have to deal with...hopefully the developers get this problem fixed so I can clear the lock.

---

### Post by kayvortex on 2010-02-01
> 
I've tried to forbid-version, but I'm not sure that's working...the command appears to "take" however, when I run a simulated upgrade, aptitude says it's still going to upgrade libglib...so, I've opted to lock the version in Synaptic...so for now, that's a work-around that I'll have to deal with...hopefully the developers get this problem fixed so I can clear the lock.

Hmm, maybe giving the version number explicitly would help:
```
sudo aptitude forbid-version libglib2.0-0=*whatever.version.it.is*
```
Then again, it could also be a bug in that "aptitude --simulate"  would list the package as being upgradeable, but "aptitude" itself would skip it.

In any case, bpowell2005, crh0831, I'm happy to have helped.

---

### Post by bpowell2005 on 2010-02-02
> **kayvortex said:**
> Hmm, maybe giving the version number explicitly would help:
```
sudo aptitude forbid-version libglib2.0-0=*whatever.version.it.is*
```
Then again, it could also be a bug in that "aptitude --simulate"  would list the package as being upgradeable, but "aptitude" itself would skip it.

In any case, bpowell2005, crh0831, I'm happy to have helped.

I tried the explicit version number as well; no change. Perhaps this is a bug...but I didn't feel like testing it! Things are working again!

---

### Post by kayvortex on 2010-02-02
Yeah, I know that feeling! Well, at least the main problem appears to be fixed.

---

### Post by ashen on 2010-02-06
Man, you guys are absolute stars!

I had exactly the same problem as this and downgrading libglib was the solution.  I never would have figured that out without this thread!

For reference, my system is a Toshiba Tecra R10 running Ubuntu 9.04.  I have also locked the libglib version now to libglib2.0-0=2.20.1-0ubuntu2.1.

Thank you all so much!

Cheers,

Alex

---

