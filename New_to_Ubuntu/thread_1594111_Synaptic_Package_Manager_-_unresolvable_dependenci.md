---
title: "Synaptic Package Manager - unresolvable dependencies - Error message"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by amjjawad on 2010-10-12
I'm trying to install GParted because it's not installed by default in Ubuntu 10.04.
I've been trying to install it from** Synaptic Package Manager** but every time I try that, I get this error message:

[B]gparted:
Depends: libparted0 but it is not going to be installed
[/B]

When I try to install **libparted0, **I get this error message:
[B]
libparted0:
Depends: libparted0debian1 (=2.2-5ubuntu5) but 2.2-5ubuntu5.1 is to be installed
[/B]
And when I try to install **libparted0debian1, **I founded it already installed.

Two days ago, I was able to install GParted smoothly and without any problem at all. I had to format and Install Ubuntu 10.04 again. I've failed to install GParted since I installed Ubuntu last time.

No, I'm not trying to install anything via Synaptic nor Terminal. 

How to fix that?

Thanks a lot.

P.S.
Screen shot is attached.

---

### Post by spikoley on 2010-10-12
Try installing it from the terminal and let us know what happens.

```
sudo apt-get install gparted
```

---

### Post by amjjawad on 2010-10-12
> **spikoley said:**
> Try installing it from the terminal and let us know what happens.

```
sudo apt-get install gparted
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gparted: Depends: libparted0 (>= 2.2-1) but it is not going to be installed
E: Broken packages

---

### Post by spikoley on 2010-10-12
> **amjjawad said:**
> 
The following packages have unmet dependencies:
  gparted: Depends: libparted0 (>= 2.2-1) but it is not going to be installed
E: Broken packages

The error mentions it could be a broken package.  Try opening Synaptic > click Edit > Fix Broken Packages and see if it fixes your problem.

---

### Post by amjjawad on 2010-10-12
> **spikoley said:**
> The error mentions it could be a broken package.  Try opening Synaptic > click Edit > Fix Broken Packages and see if it fixes your problem.

Have done that already but nothing changed.

---

### Post by spikoley on 2010-10-12
Please post the results of the command below.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by amjjawad on 2010-10-12
> **spikoley said:**
> Please post the results of the command below.

```
gksudo gedit /etc/apt/sources.list
```


#deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

---

### Post by amjjawad on 2010-10-12
By the way, I just used Synaptic to download and install GIMP. It worked perfectly. I tried again with GParted by same error message. I thought there's something wrong with Synaptic but that's not an option.

I don't get it, why don't they include GParted with Ubuntu 10.04 just like Ubuntu 9.10?

---

### Post by amjjawad on 2010-10-12
I tried to install it from Ubuntu Software Center and I got another error message. Please check the attached screen shot.

Okay, I'll stop trying and will wait for more replies :)

---

### Post by spikoley on 2010-10-12
It looks like this is a [bug]("https://bugs.launchpad.net/ubuntu/+source/parted/+bug/535368") that has been fixed.  Run the Update Manager and try again.

---

### Post by amjjawad on 2010-10-12
> **spikoley said:**
> It looks like this is a [bug]("https://bugs.launchpad.net/ubuntu/+source/parted/+bug/535368") that has been fixed.  Run the Update Manager and try again.

As I mentioned before, I had Ubuntu installed 2 days ago. I was able to download and install GParted perfectly. I formatted, installed Ubuntu again, same version, same media (Live USB) but it seems I can't install GParted for some reason.

Anyhow, I'll do what you said, try with the Update Manger and see what will happen :)

Thanks!

---

### Post by amjjawad on 2010-10-12
> **amjjawad said:**
> Anyhow, I'll do what you said, try with the Update Manger and see what will happen :)

Thanks!

Preciously the same issue. Nothing happened.
I installed the updates, restarted and when I checked the Update Manager, it says my system is Up-To-Date.

---

### Post by QLee on 2010-10-12
[QUOTE=amjjawad]As I mentioned before, I had Ubuntu installed 2 days ago. I was able to download and install GParted perfectly. I formatted, installed Ubuntu again, same version, same media (Live USB) but it seems I can't install GParted for some reason.
[/QUOTE]
I notice a launchpad report on the 11th, which seems to put it within the time frame you're interested in. 
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2562659.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2562659.html)
It might have some relationship to what you are seeing.

However, I'm somewhat perplexed by your statements on the original post. You start out stating:
                                                                             [QUOTE=amjjawad]I'm trying to install GParted because it's not installed by default in Ubuntu 10.04.
I've been trying to install it from** Synaptic Package Manager** but every time I try that, I get this error message:[/Quote]

yet, down about the middle of your post you state:

[QUOTE=amjjawad]No, I'm not trying to install anything via Synaptic nor Terminal. [/QUOTE]

In context, I guess you mean that there isn't any other process locking the packages but it seems odd to state it that way.

In that first post you stated:
[QUOTE=amjjawad][B]libparted0:
Depends: libparted0debian1 (=2.2-5ubuntu5) but 2.2-5ubuntu5.1 is to be installed
[/B][/QUOTE]
So, it looks to me as if you are trying to install the version of gparted from lucid but you have already installed (or are at the current time installing) the libparted from lucid-updates, thus failing to have the depends.

I am not sure if you did a reload (from synaptic); check (update manager) or apt-get update (CLI) during this process but it seems your system is a tad bit confused about what packages are available.

---

### Post by amjjawad on 2010-10-12
> **QLee said:**
> I notice a launchpad report on the 11th, which seems to put it within the time frame you're interested in. 
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2562659.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2562659.html)
It might have some relationship to what you are seeing.

However, I'm somewhat perplexed by your statements on the original post. You start out stating:
                                                                             

yet, down about the middle of your post you state:



In context, I guess you mean that there isn't any other process locking the packages but it seems odd to state it that way.

In that first post you stated:

So, it looks to me as if you are trying to install the version of gparted from lucid but you have already installed (or are at the current time installing) the libparted from lucid-updates, thus failing to have the depends.

I am not sure if you did a reload (from synaptic); check (update manager) or apt-get update (CLI) during this process but it seems your system is a tad bit confused about what packages are available.

> 
**[Bug 658722] [NEW] gparted crash on Ubuntu 10.10 LiveCD**

I don't have Ubuntu 10.10, I have Ubuntu 10.04.

What I meant by my first post is:
I failed to install GParted from Synaptic and later on from Ubuntu Software Center.
While I was trying to install GParted, I had NO other process/download/installation of other program which is running at the same time. I had Synaptic's window on my desktop with that error message I already attached.

That's all.
Hope it's clear now :)

P.S.
> 
 					Originally Posted by **amjjawad** 					 				
 				[I]No, I'm not trying to install anything via Synaptic nor Terminal.

 					*I forgot to add "anything else" so only "anything" was there.*


[/I]

---

### Post by QLee on 2010-10-12
[QUOTE=amjjawad]...
Hope it's clear now :)
...[/QUOTE]
It's OK that you cleared up the confusion even though it really wasn't part of the issue, but I hope you also read the rest of what I stated, which does apply to your issue.

---

### Post by amjjawad on 2010-10-12
> **QLee said:**
> I am not sure if you did a reload (from synaptic)


[B]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://ae.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://ae.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
[/B]
This is what I got when I clicked "Reload".

> 
check (update manager) 


As I mentioned before, I updated my system but nothing changed. I downloaded the updates from Update Manager already.

> 
or apt-get update (CLI) during this process 


Do you mean type that on Terminal? because again, I've done that already.

> 
but it seems your system is a tad bit confused about what packages are available.

And what should I do to fix that?

---

### Post by amjjawad on 2010-10-12
I tried to "Reload" in Synaptic but I got the attached error message which is different than the previous one.

---

### Post by admiralspark on 2010-10-12
Well, I can see one possible cause of this issue, though I may be wrong: the ae.archive repository is experiencing problems. I'm unfortunately sitting at a windows computer right now, but if you open Synaptic --> go to file, option, whatever to get the "Sources" option, then change to the official repo (or the US or Canadian ones, since both are stable), then do a "sudo apt-get update && sudo apt-get install gparted" you should be set. 

Am I wrong in guessing the mirror is broken? His commands seem to be legitimate. I might try starting a VM of 10.04 with the ae.archive repo's tonight to see if that's the cause of the problems. That error that he's getting seems to indicate that the mirrors aren't in sync with the official repo, or that one of the packages was changed (which shouldn't happen because it's supposed to be frozen).

---

### Post by amjjawad on 2010-10-12
> **admiralspark said:**
> Well, I can see one possible cause of this issue, though I may be wrong: the ae.archive repository is experiencing problems. I'm unfortunately sitting at a windows computer right now, but if you open Synaptic --> go to file, option, whatever to get the "Sources" option, then change to the official repo (or the US or Canadian ones, since both are stable), then do a "sudo apt-get update && sudo apt-get install gparted" you should be set. 


I'm using Fedora now. I'll restart and login to Ubuntu. Hope what you said is right and will fix the issue.

---

### Post by amjjawad on 2010-10-12
> **admiralspark said:**
> I'm unfortunately sitting at a windows computer right now, but if you open Synaptic --> go to file, option, whatever to get the "Sources" option, then change to the official repo (or the US or Canadian ones, since both are stable), then do a "sudo apt-get update && sudo apt-get install gparted" you should be set. 


There is no such option. I'm on Ubuntu now and I checked Synaptic. That option does not even exist.


Is there anybody here who knows how to fix this?????

---

### Post by spikoley on 2010-10-13
It looks like he is referring to the Download From in Software Sources.

1.  Open Synaptic
2.  Settings
3.  Repositories
4.  Change the Download From location and click close
5.  Click Reload in Synaptic to update the repositories

Then try to install GParted.  I am not sure if this will work, but it is a good trouble shooting step.

---

### Post by amjjawad on 2010-10-13
> **spikoley said:**
> It looks like he is referring to the Download From in Software Sources.

1.  Open Synaptic
2.  Settings
3.  Repositories
4.  Change the Download From location and click close
5.  Click Reload in Synaptic to update the repositories

Then try to install GParted.  I am not sure if this will work, but it is a good trouble shooting step.

Thanks a lot spikoley for your reply. I know he was on Windows so he couldn't give me the exact location :)

Hmmm, same, nothing happened :(

---

### Post by QLee on 2010-10-13
[QUOTE=amjjawad]...
When I try to install **libparted0, **I get this error message:
[B]
libparted0:
Depends: libparted0debian1 (=2.2-5ubuntu5) but 2.2-5ubuntu5.1 is to be installed
[/B]
And when I try to install **libparted0debian1, **I founded it already installed.
...[/QUOTE]
As I suggested to you in my first reply, your system has a package manager conflict. Reading the error message, you can see that "depends" are not satisfied. In addition, you can see that your system thinks you should use the version from lucid-updates repository but you only have the version from lucid repository. 

As has been suggested, a possible cause of this could be an Ubuntu public mirror which is not yet in "sync" and may not have all the packages available, or some other problem with the mirror. This kind of stuff happens, especially at the time of a new release, like now. That's why people have suggested trying a different repository (mirror).

Generally speaking, if you connect to a complete mirror and update to get current packages lists, problems like yours are eliminated. Buts that's just what we can guess from what you write. You need to do this and post the results if there is still an error.

By the way, "Reload" in Synaptic, "Check" in Update Manager, and "apt-get update" from the command line, all do the same thing, refresh the packages lists on your system.

---

### Post by amjjawad on 2010-10-13
> **QLee said:**
> As I suggested to you in my first reply, your system has a package manager conflict. Reading the error message, you can see that "depends" are not satisfied. In addition, you can see that your system thinks you should use the version from lucid-updates repository but you only have the version from lucid repository. 

As has been suggested, a possible cause of this could be an Ubuntu public mirror which is not yet in "sync" and may not have all the packages available, or some other problem with the mirror. This kind of stuff happens, especially at the time of a new release, like now. That's why people have suggested trying a different repository (mirror).

Generally speaking, if you connect to a complete mirror and update to get current packages lists, problems like yours are eliminated. Buts that's just what we can guess from what you write. You need to do this and post the results if there is still an error.

By the way, "Reload" in Synaptic, "Check" in Update Manager, and "apt-get update" from the command line, all do the same thing, refresh the packages lists on your system.

Thanks for everything, I appreciate that. I'll leave it for now and will check it later. I'm going to travel for few days anyway so hopefully it will work after I'll come back.

Thanks again.

---

### Post by amjjawad on 2010-10-17
I came back home, tried to do the same old process again (download and install GParted) and it worked. I'm not sure why it did not work the first time but it's working right now and I have GParted.

Thank you!

---

### Post by daithib8 on 2010-10-28
I have the same problem and changing servers didn't help matters

---

### Post by amjjawad on 2010-10-28
> **daithib8 said:**
> I have the same problem and changing servers didn't help matters

Hi and welcome in Ubuntu's forum :)

First of all, may I ask if you read the whole thread or not? if not, I suggest to read it all :)

What version of Ubuntu do you have? what exactly are you trying to download and install?
You need to provide us with more details so that we could help you ;)

---

