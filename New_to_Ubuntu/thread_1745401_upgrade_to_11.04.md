---
title: "upgrade to 11.04"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by expatCM on 2011-05-01
I have 10.10 64 bit installed.  I would like to upgrade.  Update manager does not show the Upgrade button.

I have had no problem in installing all updates and refreshing the repositories.

I also opened a terminal and entered sudo do-release-upgrade -d but I get the message "No new release found".   Sort of strange.

I have also changed the repository server to the Main Server and refreshed.

Which part of the plot am I missing?

---

### Post by lemmy999 on 2011-05-01
Under Software Sources have you checked the " Release Update" box for "Normal Releases"?

---

### Post by expatCM on 2011-05-01
yes, I have.

---

### Post by pwabrahams on 2011-05-01
I too have the problem that the upgrade can't be found.  Everyone tells me the same thing they told you: make sure that "normal" is selected for Software Sources.  Well, I've selected it all along and that doesn't help me.

Another normally robust way of getting upgrades is:
```
sudo apt-get update
sudo apt-get upgrade
```
but that doesn't work for me either.

---

### Post by expatCM on 2011-05-01
there is an additional command you may be interested in,  it is 

apt-get dist-upgrade

and it is designed to upgrade from one distribution to another.  This does not work for me but perhaps it helps you out ...

---

### Post by Artemis3 on 2011-05-01
Heh, actually dist-upgrade is not recommended for Ubuntu... You can do **sudo do-release-upgrade** if you want a cli (needs package update-manager-core and edit **/etc/update-manager/release-upgrades** to set **Prompt=normal**).

I say, most likely you should change your mirror.

---

### Post by Bucky Ball on 2011-05-01
> **pwabrahams said:**
> Another normally robust way of getting upgrades is:
```
sudo apt-get update
**sudo apt-get upgrade**
```

This does *not* upgrade the release, it upgrades the packages you have installed if there is a newer version of them in the repositories. ;)

---

### Post by fabricator4 on 2011-05-01
> **expatCM said:**
> I have 10.10 64 bit installed.  I would like to upgrade.  Update manager does not show the Upgrade button.

I have had no problem in installing all updates and refreshing the repositories.


Download the LiveCD, you can now upgrade from that.  When it gets to the bit where it asks if you want to use the whole disk or partition manually etc there is now a fourth option: Upgrade the existing release.  You can also run the LiveCD for a bit first to see if it's all good.

Also make sure you backup up all your data even if it's on a separate partition.  Seriously.  Then, if it falls in a heap you'll have your data and the new LiveCD to fall back on.

Chris.

---

### Post by akand074 on 2011-05-02
> **fabricator4 said:**
> Download the LiveCD, you can now upgrade from that.  When it gets to the bit where it asks if you want to use the whole disk or partition manually etc there is now a fourth option: Upgrade the existing release.  You can also run the LiveCD for a bit first to see if it's all good.

Also make sure you backup up all your data even if it's on a separate partition.  Seriously.  Then, if it falls in a heap you'll have your data and the new LiveCD to fall back on.

Chris.

I recommend this as well. Upgrades over update manager I hear takes a long, long time. I'd just download 11.04 yourself and do an upgrade from the disk nice and quick.

---

### Post by pwabrahams on 2011-05-02
I tried **do-release-upgrade** on my primary system. No upgrades found.  I actually have two other Kubuntu 10.10 systems running -- one in a different partition on the same machine as the first, and the other on a different machine altogether.  None of them got the notification, and none of them were able to upgrade via **do-release-upgrade** either.

This suggests that the problem might not lie in my environment, hard as it is to believe.  I've also tried switching download sources; that made no difference either.  One possibility is that I picked up something from a nonprimary repository that is causing the problem and that all the updates in the world wouldn't remove.

I finally gave up and did the upgrade by starting with the Alternate CD.  That worked on two of the systems; I haven't yet tried it on the third.

So although I've worked around the problem, I suspect that there's still something rotten in the state of Denmark, as Shakespeare said.  (Or maybe he didn't.)

---

### Post by beew on 2011-05-02
I suggest you back up your data and do a fresh install, it is fast (~20 min) and safest. Even an upgrade goes through smoothly it will take about 2 hours and a lot can go wrong during and after upgrade (the other day some guy reported that his cable was unplugged after about an hour and ended up with a broken system)

If you have a /home partition choose manual partition and use the same partition as /home and don't format it all your data and settings will be saved. If you don't have one you should create one: choose manual partition and create a partition of 15 -20g to be /, and then create a /home partition of whatever size you need and a swap partition about 1.5xram. Both the / partition and the /home partition should be formatted as ext4.

---

### Post by pwabrahams on 2011-05-02
My experience now says that if you don't get the notification, just walk around the problem and upgrade via the Alternate CD (see the published upgrade instructions) and then, once the process gets started, choose to continue the upgrade over the Net.  Once I chose that alternative, the process was pretty painless and took (on my hardware) a little more than an hour.  You'll need to stick around until the initial steps are completed (five minutes, maybe) and then won't need to intervene again until the process is nearly finished.

There have been times, though, when a fresh install was the way to go for me.  The choice depends on the condition of your existing system, I'd say.  If the system is in good shape, with few underlying unsolved issues, I'd recommend upgrading.  If it doesn't work, then go to a fresh install.  But if your system does have underlying difficulties and the upgrade goes badly because of them, don't waste time fighting them; do the fresh install.

As to a separate **/home**, there are two sides to that, and I've done it both ways.  A separate **/home** is much safer and more robust.  But it does have the disadvantage that you have to decide in advance how to divide up your available storage between **/home** and **/**.  If you need to conserve disk space (though these days most people don't), you might want to keep **/home** within your root partition.  But even then, there's a way out if you miscalculate the partition sizes: use **gparted** (boot it independently) to move things around.  It's time-consuming but it works.

If you're running more than one Linux system on a single machine and want to keep **/home** separate, then create **/home1** and **/home2** as separate partitions and symlink to them from **/home** in each root partition.

---

### Post by Bucky Ball on 2011-05-02
> **pwabrahams said:**
> But it does have the disadvantage that you have to decide in advance how to divide up your available storage between **/home** and **/**.

If you're running more than one Linux system on a single machine and want to keep **/home** separate, then create **/home1** and **/home2** as separate partitions and symlink to them from **/home** in each root partition.

As for you first point: Disadvantage? You need no more than 15Gb, 20Gb is plenty, for /, /home with the remainder. Where's the big decision?

Your second point is a bit wrong. You can use the same /home, and /swap for that matter, regardless of how many Ubuntu installs you have. As long as you have a separate /home partition, just don't format that when you're installing and the new install will 'automagically' use that /home (and /swap) and won't create another. Simple. No need for a bunch of '/homes' and '/swaps'. ;)

---

### Post by pwabrahams on 2011-05-03
The problem with using the same /home for two partitions is that they might not have the same dotfiles, particularly if the two partitions are configured differently.  Each partition might need its own dotfiles.

That said, it still might be possible to keep the non-dot stuff in a third partition common to both.  That approach, however, has the disadvantage that the conventional directory names within the home partition wouldn't be quite right.  But even that could be fixed, I suppose, with appropriate symlinks.

---

