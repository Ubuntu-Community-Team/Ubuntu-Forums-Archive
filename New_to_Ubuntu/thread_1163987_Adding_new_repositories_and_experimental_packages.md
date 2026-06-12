---
title: "Adding new repositories and experimental packages"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by Rocket313 on 2009-05-19
Hi,

Just recently switched to Kubuntu from Windows. Love the new desktop and all that, got everything working without too much fuss. However, I wasn't too pleased with Amarok 2. 

Anyways, I heard that the new beta 2.1 was supposed to be better, I decided to install it. Using these instructions:

> Add the PPA [http://ppa.launchpad.net/kubuntu-experimental/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ppa/ubuntu) as a Third-Party Software source in either Adept or KPackageManager. For example, in 9.04 run KPackageKit, click Settings > Third-Party Software > Add... and enter the APT repository deb [http://ppa.launchpad.net/kubuntu-experimental/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ppa/ubuntu) jaunty main

Note: if you already have Amarok 2.0 installed, KPackageKit cannot handle updates that install new packages. Instead, after adding the software source enter in a terminal

sudo apt-get dist-upgrade


Now, in my naivety, I assumed that this would simply update the packages for Amarok. It in actual fact downloaded over 100Mb of stuff. I suspect by the "experimental" in the URL that most of this was packages designed for developers or testers. 

I'm not exactly comfortable with running a new Linux system with all these experimental packages since if it goes wrong I'm in real trouble.

So, my question is, is it enough for me to simply disable this repository and wait for the normal package releases to replace my current experimental ones? Or, is there anyway to roll back the upgrades to their current release?

Thanks in advance.

---

### Post by cariboo on 2009-05-19
You have probably updated to the next version due out in October, Karmic Koala Alpha 1 just came out last Thursday. If you disable the ppa now you won't be able to benefit from any bug fixes that come along between now and the final release. The only way to revert back to a previous version is to do a reinstall. I would suggest keeping the version you have now, and if you have any problems, post them [here]("http://ubuntuforums.org/forumdisplay.php?f=359").

---

### Post by scorp123 on 2009-05-19
> **cariboo907 said:**
> You have probably updated to the next version due out in October, Karmic Koala Alpha  How so?? The one PPA apt-source he included clearly states "jaunty" as target distro and not "karmic". I think your conclusions are in need of reconsideration, to put it mildly.

It's more likely he just pulled in a few of the newer Qt4 libraries as Amarok is a KDE program (GNOME's GUI stuff uses GTK+).

---

### Post by scorp123 on 2009-05-19
> **Rocket313 said:**
>  Now, in my naivety, I assumed that this would simply update the packages for Amarok. It in actual fact downloaded over 100Mb of stuff ....  I'm not exactly comfortable with running a new Linux system with all these experimental packages since if it goes wrong I'm in real trouble.  This page:
[https://launchpad.net/~kubuntu-experimental/+archive/ppa](https://launchpad.net/~kubuntu-experimental/+archive/ppa)

... clearly says:
> Low quality and therefore **_dangerous packages_**, which are trials of prealpha software which might be included in the Ubuntu archives at some point.

So your fears might be justified. But then again: don't panic :D .... 

Can you do this please: Open a shell (not sure where this is in Kubuntu as I use the GNOME-based Ubuntu ...) and then issue this command:

```
apt-get --simulate remove amarok
``` ... and then post the output here? I'm not around so often, so someone else hopefully will be able to give you good advice. The command above should spit out what would happen if you were to remove the experimental "amarok" package again. So the removal is just simulated and not actually done. This would also show us what all the packages are that got pulled in and if their removal is problematic (= might crash your installation) or not.

EDIT:

For good measure, could you please also add the output of this command?
```
sudo apt-cache show amarok
``` ... please post the complete output. This too should give a detailed list of the dependencies that were pulled in and that would also be removed if "amarok" is uninstalled.

---

