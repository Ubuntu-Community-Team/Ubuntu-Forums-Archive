---
title: "Help Understanding Command"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by neu5eeCh on 2010-02-06
Hoping someone can parse this command for me. It worked. But I'm just trying to understand the finer points:

sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa

Sudo = Admin Privileges
add-apt-repository = add a given repository to my list of available repositories. Will it show up in the Ubuntu Software Center?

ppa: = what? Is PPA a particular command?

ubuntu-mozilla-daily = This is the "directory" where Mozilla posts their daily builds?

/PPA = what? Don't know what this means.  

How does one find a repository for given software? For instance, if I wanted to apt-get the latest, bleeding edge, version of Opera (or even find out if that option were available), or Chrome (which probably isn't available for Linux) how would I go about doing that?

---

### Post by mushwars on 2010-02-06
I see you are trying to get the newest firefox.

Ppa is kind of like a repository, it is an overlay for apt that allows you to get the LATEST and greatest from someones repository... more specifically... look here.

[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

---

### Post by Temposs on 2010-02-06
> add-apt-repository = add a given repository to my list of available repositories. Will it show up in the Ubuntu Software Center?

It's possible, but not necessarily the case. It depends on the package and if the packager put in the script to load it into the Software Center. It will show up in Synaptic Package Manager for sure, though.

> ppa: = what? Is PPA a particular command?

PPA stands for "Personal Package Archive". It's basically a term specific to Launchpad, which is a project hosting site run by Canonical(the company that maintains Ubuntu itself). A PPA is basically a personal repository that anyone, including you, can set up so that anyone can get your project's packages through a repository, rather than having to download it from your site manually.

> ubuntu-mozilla-daily = This is the "directory" where Mozilla posts their daily builds?

This is the name of a PPA. It probably isn't Mozilla posting their daily builds here, but rather someone working for Canonical who makes sure that Mozilla products are working well with Ubuntu. So they'll take Mozilla's daily builds, package them in this PPA with any modifications needed for running nicely on Ubuntu.

> How does one find a repository for given software?

There isn't one place to find a repository. Lots of repositories are on Launchpad, but Launchpad is used mostly by people involved with the Ubuntu community(like me, and Canonical folks, but not Opera or Google). If a project/program has a repository, they'll usually tell you somewhere on their site.

---

### Post by mac9416 on 2010-02-06
Hey, VTPoet,

You are right about 'sudo' and 'add-apt-repository'. 

'ppa:ubuntu-mozilla-daily/ppa' describes to APT the software source so that you can download software from there.

A PPA is a Personal package archive. Basically, it's an unofficial software repository maintained by one person or a small-ish group of people. Here is more info about PPAs: [https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

'ubuntu-mozilla-daily' is the PPA name and '/ppa' is the specific PPA that you will be using. If they had more than on PPA, they might name them something more specific.

You can find information about that particular PPA here: [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

Let me know if anything needs clarifying. :)

---

### Post by neu5eeCh on 2010-02-06
OK, so maybe I'm just beginning to wrap my head around this. I got the repository listing from a linux blog. I'm running the latest, bleeding edge Firefox.

But let's say I change my mind and want to run the latest stable release of 3.6.

Do I have to disable the PPA Repository in the OP, then uninstall Firefox?

Or can I just get another Firefox from a different repository and go with it?

Here's a website I found: [http://techdrivein.blogspot.com/2010/02/ubuntuzilla-repository-makes-firefox-36.html](http://techdrivein.blogspot.com/2010/02/ubuntuzilla-repository-makes-firefox-36.html)

I notice that the command is: 

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29


So... the first thing I see is that the command is completely different.

In the first repository, I didn't have to use the apt-key command? Why? I looked up apt-key and have a rough idea that it's a like a password. But if it's public, I'm not sure I understand the reason for it? Unless it's also a kind of ID tag?

echo -e "\ndeb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main" | sudo tee -a /etc/apt/sources.list > /dev/null

What's with the echo command. I looked it up but many of the options like, generate couplet from keyword, seem completely trivial. 

-e is defined as "evaluate lisp expression(s)" Huh?

Anyway, it's all Greek to me. What's going on in these commands? I find that even when I use man and --help, I have a hard time understanding what's going on.

---

### Post by mac9416 on 2010-02-06
> But let's say I change my mind and want to run the latest stable release of 3.6.

Do I have to disable the PPA Repository in the OP, then uninstall Firefox?

Or can I just get another Firefox from a different repository and go with it?

To downgrade, go to Synaptic and highlight the Firefox package. Then go to Package > Force Version, select the desired version, then apply the change.

> Here's a website I found: [http://techdrivein.blogspot.com/2010...irefox-36.html](http://techdrivein.blogspot.com/2010...irefox-36.html)

I notice that the command is:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29

So... the first thing I see is that the command is completely different.


This command imports the key that will be used to verify that the packages on this repository are not corrupted when they get to your computer.

> In the first repository, I didn't have to use the apt-key command? Why?

Because the add-apt-repository command takes care of the apt-key stuff for you.

> I looked up apt-key and have a rough idea that it's a like a password. But if it's public, I'm not sure I understand the reason for it? Unless it's also a kind of ID tag?

The idea is that the repository owners use the private key to "tag" their packages. Then when they get to you, APT uses the public key to check whether packages were signed by the repo owners' private key. This page explains it better than I can: [http://wiki.debian.org/SecureApt#Basicconcepts](http://wiki.debian.org/SecureApt#Basicconcepts)

> echo -e "\ndeb [http://downloads.sourceforge.net/pro...la/mozilla/apt](http://downloads.sourceforge.net/pro...la/mozilla/apt) all main" | sudo tee -a /etc/apt/sources.list > /dev/null

What's with the echo command. I looked it up but many of the options like, generate couplet from keyword, seem completely trivial.

That writes the software source line to the end of APT's sources file (thereby enabling it). It's like add-apt-repository, only not as smart.

I hope that clears it up some. Let me know what still needs clarification.

---

### Post by neu5eeCh on 2010-02-07
OK. So... in the spirit of experimentation and learning how to use Linux, I tried uninstalling Firefox 3.6.2pre, called Namoroka, via the Synaptic Package Manager. I then tried installing the Mozilla-Firefox-Build mentioned above using the commands described above. However, no matter what I do, I'm now stuck with 3.6.2pre. Even if I do a complete uninstall, 3.6.2pre is what is installed, rather then the "Firefox Build". Not only that, but now the Firefox logo is missing from the top left of the Firefox window and is also missing from the listed programs in the bottom panel. When I try to install the Firefox build after uninstalling 3.6.2pre, there is no force version option. So... what now? What do I need to know about Linux to fix this problem I've created for myself?

All of this must be teaching me something.

---

### Post by neu5eeCh on 2010-02-07
OK... no answers so I tried taking matters into my own hands. I opened nautilus with Sudo and deleted all debs (previous versions of Firefox I downloaded). I also deleted all files with the name firefox. I deleted just about everything I could delete.

Then reinstalled Mozilla-Build (*not* 3.6.2pre).

And 3.6.2pre reappeared, as if it had never been touched - all addons, bookmarks and extensions still in place.

The only difference? Predictably, it doesn't work. For instance, I get the following when I try to view this page:

XML Parsing Error: undefined entity
Location: jar:file:///usr/lib/firefox-3.6.2pre/chrome/toolkit.jar!/content/global/netError.xhtml
Line Number 60, Column 12:    <title>&loadError.label;</title>

So... what? Is there a Linux Registry, like a Windows Registry? I don't get why I can't get 3.6.2pre out of the system?

---

### Post by neu5eeCh on 2010-02-07
[Duplicate]

---

### Post by neu5eeCh on 2010-02-07
I give up.

I've done everything I can possibly think of. I even removed the repository from which I had downloaded 3.6.2pre. I then deleted all downloads of 3.6.2pre. Where is Linux getting it from!?! I reinstalled and uninstalled Firefox *completely* and none of it has made any any difference whatsoever.

I'm beginning to think I've found a bug.

---

### Post by neu5eeCh on 2010-02-07
I give up.

I've done everything I can possibly think of. I even removed the repository from which I had downloaded 3.6.2pre. I then deleted all downloads of 3.6.2pre. Where is Linux getting it from!?! I reinstalled and uninstalled Firefox *completely* and none of it has made any any difference whatsoever.

I'm beginning to think I've found a bug.

---

### Post by mechro on 2010-02-07
Your Firefox configuration is probably still in your home folder. Try renaming **/home/yourusername/.mozilla** to **/home/yourusername/.mozillacopy** or similar and then do your removal and installation of Firefox.

---

### Post by neu5eeCh on 2010-02-07
> **mechro said:**
> Your Firefox configuration is probably still in your home folder. Try renaming **/home/yourusername/.mozilla** to **/home/yourusername/.mozillacopy** or similar and then do your removal and installation of Firefox.

Thanks for the response. I tried that and it made no difference. Linux still installs 3.6.2pre. I'm beginning to think it might just be quicker to re install linux altogether.

---

### Post by mac9416 on 2010-02-07
Hey, VTPoet,

Sorry you're having so much trouble getting back to an official Firefox release.
Could you please post the contents of your /etc/apt/sources.list file?

---

### Post by neu5eeCh on 2010-02-07
Hey Mac, thanks for the offer. I just went ahead and reformatted and reinstalled the OS.

I looked like it was going to take longer to solve this puzzle than to simply reinstall. But all of it is a learning experience.

What was your thinking as regards the sources.list file? Maybe I can use that in the future?

---

### Post by Miljet on 2010-02-08
When you install a new package the package is stored in /var/cache/apt/archives. If you try to install the program again, apt first looks here to see if the package has already been downloaded. If it has been, apt will use that package to install instead of downloading it again.

I have experienced several cases of a package being corrupted during download. Then of course it would fail to install properly. I tried all the "fix broken packages" tricks, as well as "apt-get remove" and apt-get purge" options and nothing worked. Then I would go to /var/cache/apt/archives and delete the offending package. That will force apt to download the package again and it will install properly.

BTW, you can safely delete any packages from there once they have been installed.

---

### Post by neu5eeCh on 2010-02-08
Just checked the apt/archives folder and it's full of packages - probably all the Ubuntu updates shortly after I reinstalled. Does it make sense to regularly clear all these out?

---

### Post by nanotube on 2010-02-08
> **VTPoet said:**
> Just checked the apt/archives folder and it's full of packages - probably all the Ubuntu updates shortly after I reinstalled. Does it make sense to regularly clear all these out?

run
```
sudo apt-get autoclean
``` to clear out all the old versions.

---

### Post by mac9416 on 2010-02-08
Hey, VTPoet, sorry for the delayed response. I got in late from a Super Bowl party and went to bed right away. Since I was rooting for the Colts, I didn't have much to stay up and celebrate about. ;)

> I just went ahead and reformatted and reinstalled the OS.

I looked like it was going to take longer to solve this puzzle than to simply reinstall. But all of it is a learning experience.

Sorry you had to reinstall. I used to reinstall a lot because my experimentation would lead to breaking something. After a few of those though, I've learned a lot and I'm doing far fewer reinstalls. As you say, it's a learning experience.

> What was your thinking as regards the sources.list file? Maybe I can use that in the future?

I wanted to make sure there were absolutely no sources from which the pre-release version of Firefox could be coming. If there were none, I would have suggested you run 'apt-get update' to ensure APT actually knew which sources were enabled.

Something I should have pointed out was that even is the pre-release source was not found in the sources.list, it may be in another source file in /etc/apt/sourecs.list.d/. I think that unlikely though.

> When you install a new package the package is stored in /var/cache/apt/archives. If you try to install the program again, apt first looks here to see if the package has already been downloaded. If it has been, apt will use that package to install instead of downloading it again.

That is true, but if APT is trying to install a stable version of Firefox (pre-release sources are not enabled), APT will not even consider using the pre-release deb in the archive directory. It will always try to get the stable deb, if a newer version is not available from another source.

Nevertheless, it wouldn't hurt to clear out the cache with 'apt-get clean'. I believe this is done monthly anyway, but it may come in handy if you suspect the files are corrupted or you need to free some disk space.

I hope that clears things up a bit. Let me know if I can make anything clearer.

---

