---
title: "Thinkpad X40 and 11.04"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by shepseskaf on 2011-05-10
I recently purchased an IBM Thinkpad X40 in excellent condition. The only problem was the slow, noisy 1.8" PATA hard drive, so I replaced it with a Kingspec SSD.

Intending to use the machine only for Ubuntu, I attempted to install 11.04 with a Live CD but met with very little initial success. I tried five times to install Natty on the computer, and each time a 'showstopper' error occurred, whether it had to do with disc partitions or installer failure.

Frustrated, I attempted to install both 10.04 LTS and 10,10 separately, but ran into similar problems. As a last resort, I tried 11.04 once more and it actually completed. Though I could use the computer, it was unable to display Unity and I booted to the Classic desktop view instead. However, problems soon showed up in the form of an: "error: ELF header smaller than expected" which prevented booting to the desktop GUI.

Thinking that perhaps the X40 was simply too old for current versions of the o/s, I successfully installed 7.04. The problem now, of course, is that the system is completely out of date and as a newbie, I find it difficult to add new software packages or perform any updates.

To make a long story short, I would like to re-install 11.04 on the machine and want to know if this is a feasible option. I know that because the computer is older, certain software components won't work, but is there a way to ensure stable operation with Natty through tweaks in the installation process?

---

### Post by Johanc on 2011-05-11
11.04 worked out of the box with my IBM X40. I can't access Unity though so it defaults to Gnome 2 - which is a pity..

---

### Post by Bugsy_malone 666 on 2011-05-11
Do SSD hard drives react exactly the same as normal ones?

I have one of the X61S units which is slightly newer and thats had no problems, I do have an X41 also but havent attempted to but ubuntu on that so still running XP.

With my X61 I have been going through the motions upgrade wise, eg I started with 9.04, then 9.10,10.04lts, 10.10 and finally 11.04.

I cant say I have used 7.04, although I have used 8.04 (not for a while) and I do remember that in essence the update thingy is pretty much the same throughout.

Without seeing how it reacts and how different 7.04 is compared to what I have played with its hard to fully advise, but here is the approach I would take, although its lengthy.

First up if 7.04 is running nicely and presumably the update manager is the same (as in under system>administration>upgrade Manager) There should be a settings button somewhere on the first window, click that and a new window appears with several tabs. There should be one thats called updates (I think or you may have to have a look around the first couple of tabs for it) where you can select the important updates, recommended updates and proposed ones. There are more but make sure those 3 are selected.

Once you have done that it may need to update the refresh list but might have a few more items to update, install all the updates and you should find that at the top a has a recommended new version (8.04 for example) install the new version only after all the 7.04 updates are done.

If 8.04 installs fine, do the same process of installing all the updates so its as up to date as possible, before then trying to upgrade to the next higher version. Make sure you test functionality is ok as each version is installed then repeat through 7/8/9/10 and then once 10.10 is up to date check to see if all is working, if it is try for 11.04.

The main reason for my suggestion of doing it like this is I know sometimes in order for a transition between one piece of software and a new bit to work, it needs all of the most up to date components in the previous versions, sometimes it can be a case that prior to the next release updates are made to the older version to ensure compatibility when upgrading. 

Whats the worst that can happen? if its a fresh install at worst you have to reformat and start again, at best 11.04 runs happily and it just takes longer to install :)

Hope this idea helps!

By the way where did you get your 1.8" drive from? my X41 is a bit noisy and they dont seem to be a common type of drive!

---

### Post by maszemanet on 2011-05-14
I have an X40 with a Kingspec SSD running 10.04.2 (kubuntu). Wonderful machine. What got it off the ground was avoiding kernel mode setting, e.g. like this;

In /etc/default/grub

GRUB_CMDLINE_LINUX="nomodeset"

 IIRC I had to tell the installer to boot with the nomodeset parameter as well, but that was back in 2010...

---

### Post by shepseskaf on 2011-05-22
> **Bugsy_malone 666 said:**
> Do SSD hard drives react exactly the same as normal ones?
Mine has, so far. Its performance has been virtually indistinguishable from a typical 5400rpm drive. The difference is that it's completely silent.

> Hope this idea helps!Yes, that did help. Thanks very much for your input.

> By the way where did you get your 1.8" drive from? my X41 is a bit noisy and they dont seem to be a common type of drive!I bought mine on eBay. Just search for "kingspec ssd 32gb".

Make sure that you buy only a model described as IDE PATA. Also, it helps if it specifically states that its for the X40 and X41. Don't buy a drive marked as "ZIF", which requires a converter to work.

When the new drive came, I just removed the old, 'clicky' 4200rpm drive, took off the caddy and put it on the SSD. Then I just pushed the caddy with new drive right back into the computer. The screw holes on the caddy should line up perfectly to the SSD and everything should install with no problem.

---

### Post by rasmith3530 on 2011-06-17
I just found this post and wanted to mention that I just last night installed Natty Kubuntu on my X40 Thinpad. It is a 2371-J4U running the original 40GB 4200RPM HDD and maxxed out at 1.25GB of RAM. I installed by first installing Maverick via a Canonical factory disc and then upgrading to Natty using KPackageKit. Both the install and the upgrade went without a hitch.

Additionally, I have a T61 laptop (7658-15U), and on that machine, I am dual-booting, with Windows 7 Ultimate and Ubuntu 10.04 LTS.

---

### Post by vbm on 2011-10-13
> **rasmith3530 said:**
> I just found this post ...

ditto. Installed 11.04 from a live USB and have been running it for a couple of months without any glitches. Can't run Unity 3D or Gnome 3, but Gnome 2 runs just fine.

I still have the original HW and I kept the original XP installation as well as the original recovery partition, but I rarely use XP nowadays and am about to upgrade to 11.10 this week. :)

---

