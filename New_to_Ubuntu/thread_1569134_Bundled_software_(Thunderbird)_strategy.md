---
title: "Bundled software (Thunderbird) strategy"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by erkswede on 2010-09-06
Dear forum members

I have been running Ubuntu for a few years now. I started out with 8.04 I think and I have upgraded a few times and I'm now running 10.04. Everything is working fine technically speaking but I cant get my head around how things are working with bundled software, in this case Thunderbird, and the upgrade of these, or rather, the absence of upgrades. Mozilla is putting out new versions of Thunderbird but there dosent seem to be an easy way to upgrade Thunderbird in my current Ubuntu installation.

My guess is that the version of Thunderbird I'm running is specially "designed" for Ubuntu 10.04? Other versions of Thunderbird, eg in Windows, have an option to "Look for upgrades" under the help menu. My Thunderbird doesn't.

I also read something on the online Ubuntu help pages that there are also different versions for different architectures, that is 32 or 64 bit.

So, how is one to decide what version of Thunderbird to run. Is there any, not very obvious, advantages to go with the "bundled" version? Any disadvantages? Or should I install a the latest Thunderbird manually? Pros and cons? Can both versions co-exist on my Ubuntu installation?

I hope you see my predicament.

Kind regards
/erkSwede

PS I'm not looking for installations instructions or technical assistance, plenty of this in the forums already. DS

---

### Post by sandyd on 2010-09-06
> **erkswede said:**
> Dear forum members

I have been running Ubuntu for a few years now. I started out with 8.04 I think and I have upgraded a few times and I'm now running 10.04. Everything is working fine technically speaking but I cant get my head around how things are working with bundled software, in this case Thunderbird, and the upgrade of these, or rather, the absence of upgrades. Mozilla is putting out new versions of Thunderbird but there dosent seem to be an easy way to upgrade Thunderbird in my current Ubuntu installation.

My guess is that the version of Thunderbird I'm running is specially "designed" for Ubuntu 10.04? Other versions of Thunderbird, eg in Windows, have an option to "Look for upgrades" under the help menu. My Thunderbird doesn't.

I also read something on the online Ubuntu help pages that there are also different versions for different architectures, that is 32 or 64 bit.

So, how is one to decide what version of Thunderbird to run. Is there any, not very obvious, advantages to go with the "bundled" version? Any disadvantages? Or should I install a the latest Thunderbird manually? Pros and cons? Can both versions co-exist on my Ubuntu installation?

I hope you see my predicament.

Kind regards
/erkSwede

PS I'm not looking for installations instructions or technical assistance, plenty of this in the forums already. DS
Ubuntu disables the thunderbird update because thunderbird can only be updated from the repos (techinically, no, but....)

You see, thunderbird itself it installed into  /usr/bin, which you have no permission to modify. Therefore, you do not have permission to upgrade it either. To prevent issues from occuring because of that, upgrading is disabled.
However, just add the ppa -> [https://launchpad.net/~mozillateam/+archive/thunderbird-stable](https://launchpad.net/~mozillateam/+archive/thunderbird-stable)

---

### Post by erkswede on 2010-09-06
> **carlee said:**
> 
However, just add the ppa -> [https://launchpad.net/~mozillateam/+archive/thunderbird-stable](https://launchpad.net/~mozillateam/+archive/thunderbird-stable)

Thanks for your reply.

What will the above give me? As far as I understand the page the latest version I get is still 3.0.6? Latest Thunderbird version seems to be 3.1.2 asof aug?

Still don't get it, silly me :(

---

### Post by Chesamo on 2010-09-06
Repositories are usually a little bit behind the actual release, because it takes time to bugtest (a little bit) to make sure it works with the distribution, then make the .deb package.

However, what you *can* do is download the .tar.bz2 file provided on the Thunderbird web site and run the Thunderbird executable out of your Home directory. It'd be just like running the program normally, except you couldn't invoke it from the command line (and you'd have to take care of upgrading yourself, rather than through the repos). While this is possible, I don't 100% recommend it because it's a hassle to set up and (like I mentioned) updates have to be done manually.

As for using the "bundled" version, it would be no different than using the version that Mozilla provides (albeit a few releases behind). As far as I know, most programs (like Thunderbird) are packaged and the distributed; no modification is made to the programs before they ship out. Both versions can co-exist, as they would use the same configuration directory, but there'd be no actual point to do so.

The easiest thing to do would be to just run whatever's in the repos, or add the PPA. There's no strict advantage to using the executables out of a tarball, and a few disadvantages (no dependency resolution, for a start).

---

### Post by uRock on 2010-09-06
Download the newest Thunderbird from the site. Via CLI or Ubuntu Software Center, uninstall the current Thunderbird, this will not remove your thunderbird settings and such, which are in a hidden folder in /home.

When the file finishes downloading, move it to your home folder.

Right-click extract here.

Delete the .tar.gz file as you do not need it anymore.

Rename the thunderbird file to .thunderbird2

Go in the menu to Application> Accessories> Gedit and copy and paste the following text into the editor and save the file with the name .thunderbirdlauncher
```
 #this is a launcher to start Thunderbird.
cd ~/.thunderbird2
./thunderbird
```Next you will need to make the above file executable with the following command in a terminal;```
chmod +x .thunderbird
```Then you will need to create a launcher in the Main Menu.
Go to System> Preferences> Main Menu. Once the app opens, in the left pane click Internet or Office, whichever you prefer, then on the right side click +New Item, then enter ./.thunderbirdlauncher in the box beside Command and title it as you wish.
To get the icon, click on the icon and navigate throught the directory to /Home/.thunderbird2/chrome/icons/default and select whichever grade quality icon you prefer to use.

---

### Post by erkswede on 2010-09-07
Thanks for your replies, now I am a little more enlightened.

---

### Post by mcduck on 2010-09-07
The versions of packages available in each Ubuntu release are locked during the development, to allow better testing of them together and to provide stability. You only usually get updates for security reasons and to fix serious bugs, never just to provide you with new features or latest version of some program.

So the basic rule is that every package in a Ubuntu release will be the same version for the whole lifetime of that Ubuntu release. If possible, even the security updates are patched to the current version instead of upgrading the package to latest version.

Like mentioned in above posts, the update features of individual programs are disabled as normal users wouldn't have permissions to run the update anyway, and because using of Ubuntu's package management for installing/updating is preferred.

If you prefer always having the latest and greatest version of your programs you might like some Linux distribution with rolling releases instead of stable releases like Ubuntu has.

Of course if you just have a program or two that you wish to keep on the latest available version you'll usually find some PPA repository or third-party repository that gives you such updates. (And there's also the Backports repository which sometimes gives you new versions of programs, backported from the current development version of Ubuntu. But the rules for backporting stuff are pretty strict so anything that requires backporting many packages and thus might affect stability of other programs is not allowed there).

edit:
[https://wiki.ubuntu.com/StableReleaseUpdates]("https://wiki.ubuntu.com/StableReleaseUpdates")
[https://wiki.ubuntu.com/FeatureFreeze]("https://wiki.ubuntu.com/FeatureFreeze")

---

### Post by erkswede on 2010-09-07
Thanks mcduck, these "rules" was what I was looking for.

Just to be clear, I use Ubuntu because of it's stability among other attractive properties. My desire for the latest version of Thunderbird stems from the more stable (beta) version of the extension Lightning, enabling me to use our shared caldav calender server ([www.davical.org](www.davical.org)) which keeps me away from MS Exchange and Outlook.

Now I know my options and what effect they will have on new versions, updates etc. Thanks again!

---

### Post by uRock on 2010-09-07
I installed the new thunderbird for the ability to have Lightning.

---

