---
title: "is it good or bad practice to auto update to ubuntu pre-release?"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by sallam on 2011-03-22
Greetings

In Update manager > ubuntu update, there is an option that if we tick will auto update ubuntu to the pre-release files. Do you recommend that I tick it? or is it bad to do so?
And if not ticked, will ubuntu gets auto updated when the final release is available, without having to manually download and install?

---

### Post by coffeecat on 2011-03-22
First - if you mean upgrade to the pre-release 11.04 Natty Narwhal then, unless you're willing to help with bug-testing and prepared to tolerate system instability, don't. If you only have one installation of Ubuntu - don't. Pre-releases are not stable enough for routine use. Those involved in testing pre-releases generally use a spare partition or spare machine and keep a stable installation of 10.04 or 10.10 for ordinary use.

But do you mean upgrade to 11.04? I can see nowhere in Maverick's Update Manager where you can do this. You need to use a terminal command for this in the period leading up to final release.

Or do you mean to activate the proposed and/or unsupported (backports) repositories?

---

### Post by sallam on 2011-03-22
coffeecat, thanks for your reply.
I've followed your advice and unticked the pre-release option.
Yes, I meant upgrading to 11.04 release. It cannot be done automatically then?
If I have to do this through the terminal, what commands should I use please?

---

### Post by Rex Bouwense on 2011-03-22
Under System->Administration->Software Sources->Updates you can choose to be notified when a new version is available.  To upgrade to a new version you would type:  sudo apt-get dist-upgrade.  Some people have had bad experiences upgrading to the new versions rather than using a new install.  You can read about the pros and cons on the forums, just search for upgrading to new version.

---

### Post by sallam on 2011-03-22
I just read that we should use:
sudo do-release-upgrade -d
which will tell us if a new release is available, then if there is one, we type:
sudo do-release-upgrade

But things could go wrong during this? I think I need to read more on this, thanks.

---

### Post by Rex Bouwense on 2011-03-22
Things can always go wrong.  That is why everyone will tell you back up your files that you cannot live without before you upgrade to a newer version. Chances are that nothing will go wrong, but if it does you still have your important files.

---

### Post by sallam on 2011-03-22
If I make a new install, will I have to re-install all my manually installed software, for example: Google Chrome, Google Earth, Picasa, etc..?

---

### Post by coffeecat on 2011-03-22
> **sallam said:**
> If I make a new install, will I have to re-install all my manually installed software, for example: Google Chrome, Google Earth, Picasa, etc..?

Yes. But if this to be  your only installation of Ubuntu, the advice is - don't run a pre-release version. If you have a spare partition to use, then by all means try it.

---

### Post by Rex Bouwense on 2011-03-22
> **sallam said:**
> If I make a new install, will I have to re-install all my manually installed software, for example: Google Chrome, Google Earth, Picasa, etc..?
Yes.  A new install, unless you install the new version as a dual boot OS, will over-write what you have on your disk.

---

### Post by jerome1232 on 2011-03-22
I just wanted to note when the final version does come up, I've always had great success with torrent'ing the Alternate Install CD and using that to upgrade. This also helps to take the strain off of Ubuntu's repository servers and gives you a smoother, faster upgrade process.

---

### Post by grahammechanical on 2011-03-22
Based on my experience of Ubuntu for four years, when 11.04 is released officially on 28th April Update Manager will inform us that the next release is available and will provide a button to click to upgrade. I have never needed to do anything other than wait until the official release date and click that button. I usually wait a few weeks before upgrading from one release to the next.

Last year I had some hardware problems and reinstalled with an earlier version and Update Manager informed me that the next release was available and so on until I was up to date with the latest release.

Regards.

---

### Post by sallam on 2011-03-22
jerome1232,
Why the Alternate install torrent? why not the desktop torrent?
Any advantages/differences?

---

### Post by jerome1232 on 2011-03-23
Because it supports an upgrade via cd, the regular desktop version does not. :)

---

### Post by sallam on 2011-03-23
you mean you can upgrade from within ubuntu 10.10, provided that the Alternate is on a CD or usb flash drive?
Or must you upgrade during booting?

---

### Post by jerome1232 on 2011-03-23
This is a small guide on the community documentation that has more info about upgrading via alternate cd, as well as the other methods available.

The main reason I tout torrenting and using an alternate cd, is if more people did this then Ubuntu's repository servers wouldn't get slaughtered every 6 months when everyone tries to upgrade at the same time.

[https://help.ubuntu.com/community/MaverickUpgrades#AlternateUpgrade](https://help.ubuntu.com/community/MaverickUpgrades#AlternateUpgrade)

---

### Post by wizard10000 on 2011-03-23
JMO but it's a bad idea to auto-update anything.

Sometimes stuff breaks - on my own machines I have a cron job that runs apt-get update every couple hours, but the upgrades themselves I do manually.

I've had automatic updates break stuff - so I wanna know what's being upgraded so if it breaks I know what to fix without spending a buncha time trying to figure out what broke what  ;)

---

