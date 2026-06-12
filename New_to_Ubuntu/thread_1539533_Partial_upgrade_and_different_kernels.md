---
title: "Partial upgrade and different kernels"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by Alex De Duck on 2010-07-26
I installed Ubuntu 9.04 tonight from a disk I had lying around. It's a dual boot with vista, so I just chose the second option ("Install on largest available space") and let it at it. Then I had it upgrade to 9.10

Upon restart I noticed two versions of Ubuntu were installed, kernel 2.6.31-22-generic and 2.6.28-11-generic. I thought nothing of it, and started up ubuntu, and had it upgrade to 10.04. Then however my internet seemed to have given out - the indicator vanished, and I only noticed because PIdgin was showing a blank. Now it can only do a partial upgrade, it lets me know, but when I click that it prepares to upgrade, then asks me to start the upgrade, and when I click yes I got an error message:
**Could not install the upgrades**

**The upgrade is now aborted. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).**

Clicking cancel gives me this uplifting message: 

[B]Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.[/B]

 1 - how do I fix the double kernel? 
 2 - How to upgrade to 10.04?

---

### Post by uRock on 2010-07-26
[s]If you have access to burning the disk, then you should burn 10.04 to disk and run a clean install.[/s]

collinp's suggest may be the best route.

---

### Post by collinp on 2010-07-26
Kernels aren't automatically uninstalled after a upgrade - you can uninstall them, though. But unless you're strapped for space, it won't make a difference if you keep them or not.

To fix your upgrade issue, you will need to execute the following commands in a terminal session:
```
sudo apt-get install -f
sudo apt-get update
sudo apt-get dist-upgrade
```The first command will fix your current installation, which, according to the information you provided, is broken. The second command will update your package database, and the third will run a distribution upgrade from the terminal.

---

### Post by Alex De Duck on 2010-07-26
> **collinp said:**
> Kernels aren't automatically uninstalled after a upgrade - you can uninstall them, though. But unless you're strapped for space, it won't make a difference if you keep them or not.

To fix your upgrade issue, you will need to execute the following commands in a terminal session:
```
sudo apt-get install -f
sudo apt-get update
sudo apt-get dist-upgrade
```The first command will fix your current installation, which, according to the information you provided, is broken. The second command will update your package database, and the third will run a distribution upgrade from the terminal.
This first line gave me this: 

E: Internal Error, Could not perform immediate configuration (2) on mountall

Clean install sounds good but does that mean I have to remove the version of ubuntu I have right now?

---

### Post by collinp on 2010-07-26
> **Alex De Duck said:**
> This first line gave me this: 

E: Internal Error, Could not perform immediate configuration (2) on mountall


Try executing the following command, then running the commands that I listed:
```
sudo apt-get install --reinstall mountall
```

---

### Post by uRock on 2010-07-26
> **Alex De Duck said:**
> This first line gave me this: 

E: Internal Error, Could not perform immediate configuration (2) on mountall

Clean install sounds good but does that mean I have to remove the version of ubuntu I have right now?

Are you using Wubi? If not then you can just install on top of the current ubuntu.

---

### Post by Alex De Duck on 2010-07-26
@Collin: Exactly the same result. 

@uRock: No, not a wubi install, but second option, install on largest continuous space.

---

### Post by uRock on 2010-07-26
If you don't want to go through the repair process, then a clean install will go quickly. You will have to select the partition to install into, which is the one that is already EXT3 or EXT4. It will format the partition and install the newer version.

---

### Post by Alex De Duck on 2010-07-26
> **uRock said:**
> If you don't want to go through the repair process, then a clean install will go quickly. You will have to select the partition to install into, which is the one that is already EXT3 or EXT4. It will format the partition and install the newer version.
I didn't select a partition though... Ubuntu did that. Will it still work?

---

### Post by uRock on 2010-07-26
> **Alex De Duck said:**
> I didn't select a partition though... Ubuntu did that. Will it still work?

You will have to select partitions manually this time and write over the current EXT3/EXT4 partition.

---

### Post by Alex De Duck on 2010-07-27
And it won't just install another kernel?

---

