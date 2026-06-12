---
title: "Can't find the answer - Network manager killed wireless (I think)"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by MoebusNet on 2007-04-22
I've spent 3 hours searching the forum with no luck. I'm away from home with my Ubuntu 6.10 - only D800 notebook. Wireless worked well with my open home wireless router, but after I used network manager at work (out of state) to access the company wireless router, I lost the ability to access any other network, even an open one. I am connected by wired-ethernet right now in an internet cafe. I installed wifi-radar and can see but cannot connect to the cafe wireless network. I can't connect to the open network at the motel either. Any ideas? Thanks in advance!

Edit: Atheros AR5252 wireless card as listed from "lspci" command.

---

### Post by MoebusNet on 2007-04-24
UPDATE: Like many others, I lost my wireless capability under 6.10 to the deluge of updates just prior to the 7.04. I attempted the "official" distribution upgrade in desperation to get wireless working again after all else failed. The "official" upgrade, as noted elsewhere on the forum did not work at all. So after changing my sources list from "edgy" to "feisty", I tried the tried and true:

Code:
sudo apt-get update

sudo apt-get upgrade

sudo apt-get dist-upgrade


Guess what? After a looong wait for all the downloads, the upgrade completely hosed my root files as well as /home. No choice now but to do a clean install (sigh).

On the upside, Feisty is now running on my notebook and the wireless works again (using it right now!) It's still a pain to lose everything on my HD, though.

Now I to have to go in and reinstall _everything_ while I'm on the road (J-Pilot, wine, you know _everything_.

I guess that's life on the digital frontier!

---

### Post by bigred3373 on 2007-04-24
> **MoebusNet said:**
> UPDATE: Like many others, I lost my wireless capability under 6.10 to the deluge of updates just prior to the 7.04. I attempted the "official" distribution upgrade in desperation to get wireless working again after all else failed. The "official" upgrade, as noted elsewhere on the forum did not work at all. So after changing my sources list from "edgy" to "feisty", I tried the tried and true:

Code:
sudo apt-get update

sudo apt-get upgrade

sudo apt-get dist-upgrade


Guess what? After a looong wait for all the downloads, the upgrade completely hosed my root files as well as /home. No choice now but to do a clean install (sigh).

On the upside, Feisty is now running on my notebook and the wireless works again (using it right now!) It's still a pain to lose everything on my HD, though.

Now I to have to go in and reinstall _everything_ while I'm on the road (J-Pilot, wine, you know _everything_.

I guess that's life on the digital frontier!  SO YOU DID A CLEAN INSTALL RE PUT BACK FEISTY WHAT COMMANDS DID YOU USE TO GET THE WIRELESS WORKING AGAIN THE INFORMATION ON HOW TO INSTALL I MEAN?????????????????????????

---

### Post by MoebusNet on 2007-04-25
Sorry to take so long to reply.

What I mean is that I had to repartition the hard drive, do a brand-new install Feisty from the 7.04 CD and go from there. There were no user files or configurations remaining after the install.

As you can see from my signature, I'm using an Atheros AR5252 pcmcia internal wireless card. Feisty allowed me to choose to use the proprietary driver for this card immediately after install. There was a green icon in the upper right corner of the desktop just to the left of the time/date and volume icons. Clicking it allowed me to use the driver for the wireless card. After that it all "just worked."

I hope this helps.

There are only two kinds of computer users in the world: those that have lost data, and those who will. Backups are a wonderful thing.

---

### Post by SwaroopKunduru on 2007-04-25
I had the same problem see [here]("http://ubuntuforums.org/showthread.php?t=421420")

---

