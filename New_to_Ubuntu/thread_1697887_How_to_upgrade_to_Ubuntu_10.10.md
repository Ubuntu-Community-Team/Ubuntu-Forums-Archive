---
title: "How to upgrade to Ubuntu 10.10?"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by Fanatico on 2011-03-01
I have Ubuntu 9.04 running on my computer. How can I upgrade it to latest Ubuntu 10.10?

Should I burn CD with 10.10 Live Ubuntu image and reinstall it? Whether it will keep all my old files? Or I can upgrade to Ubuntu 10.10 via Synaptic?

Thanks

---

### Post by seawolf167 on 2011-03-01
You'll need to do a fresh install.

[*You can directly upgrade to Ubuntu 10.10 ("Maverick Meerkat") from Ubuntu 10.04 LTS ("Lucid Lynx") only*]("https://help.ubuntu.com/community/MaverickUpgrades")

---

### Post by gdonwallace on 2011-03-01
The easy way is with update-manager.

From a terminal type sudo update-manager --devel-release.  This will launch update manager with root permissions and check for any available development releases to be upgraded too.  Click the check button before doing the upgrade.  This will ensure that You have all the downloads for your current version of Ubuntu.  If there is a release to upgrade to there will be a button at the top of the update manager that You can click on to do the update.

---

### Post by Fanatico on 2011-03-02
Could you confirm that Ubuntu version upgrade through update-manager will keep all my files and documents untouched?

The Upgrade Notes ([https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)) has very scary sentence:

[B]Renewing the Installation without formating the partitons (in contrast to upgrading),
will also keep the personal data and configurations under /home but will renew all system
settings under /etc as well as the default set of installed packages. [/B]

Does it mean that upgrade format the partition?

From the point of view of terms is update of system through update-manager called upgrade or renew?

Thanks

---

### Post by andymorton on 2011-03-02
> **Fanatico said:**
> Could you confirm that Ubuntu version upgrade through update-manager will keep all my files and documents untouched?

The Upgrade Notes ([https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)) has very scary sentence:

[B]Renewing the Installation without formating the partitons (in contrast to upgrading),
will also keep the personal data and configurations under /home but will renew all system
settings under /etc as well as the default set of installed packages. [/B]

Does it mean that upgrade format the partition?

From the point of view of terms is update of system through update-manager called upgrade or renew?

Thanks

All your files, settings etc will be intact if you upgrade through the update manager. 

andy

---

### Post by Mariane on 2011-03-02
The command for that is to type in order: 

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Mariane

---

### Post by freak42 on 2011-03-02
The responses here confuse me?

As Ubuntu 9.04 is not a Long Term Support Version (LTS) of Ubuntu you can't update to 10.10 directly. This means with the commands listed above you'll get to 9.10,... then you have to upgrade again to 10.04 then again to 10.10?

That's a lot of dist upgrades to go through and I am not sure that a fresh install is the easier way.

And about your files: you should have a backup of those anyhow if you are so concerned about loosing them. Upgrades can render your system unbootable in rare cases and you'll want your files to be safe no matter what.

On another note, you can separate your files more easily by having a separate partition for your home folder, that way you can reinstall ubuntu easily without touching your files at all.

hth

---

### Post by jfla on 2011-03-02
I think the apt-get method is the best way. I think it might upgrade directly to 10.10. I have only upgraded from 10.04 to 10.10 before. Making such a big jump might not be such a good idea too, so maybe a clean install is the way to go.

---

### Post by beew on 2011-03-02
First of all even a single upgrade (from one release to the next) will take a few hours so when you have to go through several upgrades in series it will takes a loooong time, whereas a fresh install takes only 15-20 minutes.  

Secondly when the process is so complex something might go wrong, and it might go wrong without you even knowing it  and instead it will manifest as hard to diagnosed problems down the line. 

Thirdly, to upgrade successfully you have to have a very pristine system, like you have to disable all ppas. Third party softwares you install (say from .deb files or tar balls) may cause problems.

So my suggestion is simply do a fresh install. If you have already a /home partition then just don't touch it during  the new install and your data would be safe (you should have  separate / and /home partitions, when you do a fresh install, keep this configuration and the installation will only overwrite the / partition)

---

### Post by Fanatico on 2011-03-04
beew, thank you for detailed explanation

Could you just clarify a few things. I don't have separate partition for /home directory, so everything is located on one partition. I don't remember that during Ubuntu installation I had an option to create separate partition for /home.

So my question how can I make fresh install of Ubuntu 10.10 and have /home directory on separate partition? Then I assume I should move my old /home directory to this new separate /home partition?

Thanks

---

