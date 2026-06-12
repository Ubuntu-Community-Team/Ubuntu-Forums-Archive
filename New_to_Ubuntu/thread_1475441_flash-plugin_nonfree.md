---
title: "flash-plugin nonfree"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by driebel on 2010-05-06
Hi,

Just did the 10.04 upgrade from 8.04, and things went mostly smoothly.  A few errors popped up during the upgrade, namely that the flashplugin-nonfree_10.044.2ubuntu_amd64.deb package did not install correctly.  I've since gone through the rest of the upgrade and restarted, and things seem to be working.  However, I have an error message telling me there are broken dependencies, and I need to fix them using the package manager.  Alright, Synaptic recommends removing a gstreamer plugin and upgrading the flashplugin-nonfree.  However, when I press apply, I get the error message:
E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.

Sounds good, but how do I re-install without removing?  I can mark it for upgrade or removal, but not reinstallation, that option is grayed out in the drop down box.  I can't even unmark it period.

Thanks,
Dave

---

### Post by sandyd on 2010-05-06
> **driebel said:**
> Hi,

Just did the 10.04 upgrade from 8.04, and things went mostly smoothly.  A few errors popped up during the upgrade, namely that the flashplugin-nonfree_10.044.2ubuntu_amd64.deb package did not install correctly.  I've since gone through the rest of the upgrade and restarted, and things seem to be working.  However, I have an error message telling me there are broken dependencies, and I need to fix them using the package manager.  Alright, Synaptic recommends removing a gstreamer plugin and upgrading the flashplugin-nonfree.  However, when I press apply, I get the error message:
E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.

Sounds good, but how do I re-install without removing?  I can mark it for upgrade or removal, but not reinstallation, that option is grayed out in the drop down box.  I can't even unmark it period.

Thanks,
Davesee sig- press remove button

---

### Post by driebel on 2010-05-07
Wow.  Absolutely incredible.  64-bit flash has been the bane of my existence for months.  I never really had it working 100% under Hardy, and just kind of kept the faith that it would fixed in Lucid, and now it is.

THANKS!

Dave

---

### Post by driebel on 2010-05-07
Ooops, I spoke a little too soon.  Flash functions perfectly, that's great.  However, synaptic still thinks there are broken dependencies and wants to reinstall flash itself.  This process still fails, and I can't get synaptic to install anything else because it always tries to "fix" my perfectly working flash first.

The details seem to indicate that it's amazon's MP3 downloader that's having the issue.  I'm content to dump that program if that's a good fix.  Ideas?

---

### Post by driebel on 2010-05-07
Bump.

Sorry, but I've got a few other non-functional programs right now (avant window navigator especially), which I'd really like to re-install, and with synaptic nonfunctional, I've got issues.

A recap: I used carlee's brilliant flash installer, and my flash now works perfectly.  However, synaptic still thinks I have broken packages, and wants me to update flashplugin-installer and flashplugin-nonfree.  These updates are also automatically added to any synaptic list of updates I do want to do.  I can't unmark the flash programs.  I cannot remove AWN without also updating the flash programs.  This process fails every time with the message that flash is in an unstable state and I must re-install it before removing it.  Effectively, synaptic is completely non-functional.

How do I convince synaptic that everything is fine?  Thanks,

Dave

---

### Post by lykwydchykyn on 2010-05-07
I went through this, it was wicked to fix.

Lemme see if I remember how I fixed it.

I think what I had to do was edit the file /var/lib/dpkg/info/flashplugin-nonfree.prerm.

There was a line listing a bunch of apps for alternatives.  (Sorry, I should have noted this down, I'm going by memory.)  It's some variable being assigned to a list of things like iceape, mozilla, iceweasel, etc.

I removed everything from that list so that it was blank, saved it.

Then I ran apt-get -f install and all was happy.

Sorry for the vague instructions.

---

### Post by driebel on 2010-05-07
Gave the suggestion a try, no luck.  All it seemed to do was disable my desktop theme.  Flash still functioned, synaptic didn't.  :(

---

### Post by lykwydchykyn on 2010-05-07
> **driebel said:**
> Gave the suggestion a try, no luck.  All it seemed to do was disable my desktop theme.  Flash still functioned, synaptic didn't.  :(

I have no idea why that would happen.

What does it say if you run:
```

sudo apt-get -f install

```

At the terminal?

---

### Post by greenfrog on 2010-05-07
Do a search for the error message and you will find a fix.

I had the same problem with 32 bit 10.4

---

### Post by lidex on 2010-05-08
> **lykwydchykyn said:**
> I have no idea why that would happen.

What does it say if you run:
```

sudo apt-get -f install

```

At the terminal?

Or maybe

```

sudo apt-get -f install flashplugin-nonfree

```

---

### Post by utnubuuser on 2010-05-08
There is a sticky about known issues with Lucid Lynx Installs/Upgrades.
The flashplugin issue is one of them:> [http://ubuntuforums.org/showthread.php?t=1469475&highlight=can%27t+remove+flashplugin]("http://ubuntuforums.org/showthread.php?t=1469475&highlight=can%27t+remove+flashplugin")

---

### Post by Ohgordon on 2010-06-04
[lidex]("http://ubuntuforums.org/member.php?u=577099") you saved my life haha thank you

---

### Post by Lukasz Tarkowski on 2010-08-19
Thank you Idex this was really helpful

---

