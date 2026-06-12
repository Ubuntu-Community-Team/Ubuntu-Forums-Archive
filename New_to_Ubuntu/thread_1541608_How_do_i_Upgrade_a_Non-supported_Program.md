---
title: "How do i Upgrade a Non-supported Program?"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by Ray716 on 2010-07-29
Ok, So i am enjoying the game FreeCol, but there is no button in the game to upgrade it, and the software center doesn't support upgrades eithor.. So my question, now that i have the  package downloaded, how to i go about upgrading that program???

Thanks!

---

### Post by LowSky on 2010-07-29
Ubuntu "locks" software between releases. The only things it upgrades are security holes.
You will just need to download the newest file from their website and install it. Make sure to uninstall the one you currently have

---

### Post by philinux on 2010-07-29
> **Ray716 said:**
> Ok, So i am enjoying the game FreeCol, but there is no button in the game to upgrade it, and the software center doesn't support upgrades eithor.. So my question, now that i have the  package downloaded, how to i go about upgrading that program???

Thanks!

Freecol is in synaptic so ubuntu will update it as and when necessary.

Make sure you have the backports repo enabled. [Backports]("https://help.ubuntu.com/community/UbuntuBackports")

Or as lowsky says get the latest and greatest from their website.

---

### Post by 3rdalbum on 2010-07-29
In Linux, to get later versions of software, you need to tell your package manager about a repository that contains the software that you want to install. Ubuntu has an extra system of "PPAs" which are repositories hosted at Launchpad.net, and anyone can start one and maintain packages in it.

There is a repository containing FreeCol, called GetDeb Games. You can find out about it here: [http://www.ubuntuupdates.org/ppas/26](http://www.ubuntuupdates.org/ppas/26)

Once the package manager has been told about this repository, run:

```
sudo apt-get update
sudo apt-get install freecol
```

or the equivilant GUI method.

I found this repository through doing a web search for "Freecol PPA". You can find PPAs this way too.

---

### Post by Ray716 on 2010-07-29
Ok.. so i went to Synaptic Package Manager... .the version i have installed is 0.8.4+dfsg-2 (lucid) the newest version availble is 0.9.2.... i tried to do the force version but it's grayed out... what's next?

---

### Post by beew on 2010-07-29
"Completely Remove" your installed version, go to the link given by 3rdalbun and enable the game repository and update as instructed there. Then go to Synaptic and reload you will find a new version.

For the reason stated by LowSky, I usually enable third party repositories for my softwares if I can find them
instead of using the outdated versions in the "official channels". I would rather take a little risk on  the all important security than to give up on new features and bug fixes.

---

