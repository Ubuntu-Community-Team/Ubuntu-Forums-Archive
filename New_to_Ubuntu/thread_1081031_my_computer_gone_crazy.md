---
title: "my computer gone crazy"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by mash.ky on 2009-02-26
actually i got a big problem. my brother done some software un installations and there is no network manager and when i try to reinstall it it gives some error messages "you have 835 broken packages in your system" i think i can't access internet from the machine as the network manager is un installed. so can't do anything. i'm using ubuntu 8.10. pls help!!!

---

### Post by Ms_Angel_D on 2009-02-26
In all honesty sounds like a good time to backup and re-install.

P.S. Next time log your brother on to the guest account.

---

### Post by RichardLinx on 2009-02-26
Yep. Your brother probably just deleted a bunch of dependancies from the package manager. Backup and reinstall.

---

### Post by mash.ky on 2009-02-26
how can i do that. i'm bit new to ubuntu. even i hav done some configurations with apache tomact and axis. can they be servive after the reinstallation?

---

### Post by RichardLinx on 2009-02-26
You can get access to your files through a live CD (Ubuntu lice CD will do fine). Then just save the files to an external hard drive or USB. If you reinstall Ubuntu your files will be erased because of the formatting/partitioning process unless you have your /home on a seperate partition.

---

### Post by Peter09 on 2009-02-26
You only need network manager if you have a wireless connection.

try the following commands


```
sudo dpkg --configure -a
sudo apt-get install -f
```

---

### Post by sharon.gmc on 2009-02-26
I think you need to have some re-installation done.  It will solve the errors  you're experiencing.

---

### Post by Sirron on 2009-02-26
Open Synaptic, and search for ubuntu-desktop, then mark it for installation. It's a metapackage that probably depends on a lot of the software you're missing, and may fix your problem.

If you can't find it, perhaps you're missing a repository?

---

### Post by tarps87 on 2009-02-26
Before you reinstall:
Are you connected by a wire or wireless?
Can you post the output of
```
sudo ifconfig
```

---

### Post by Orange_and_Green on 2009-02-26
Re. the missing Network manager, have you tried right-clicking the top panel, "Add applet" and add "Notification Area"?

My network manager applet was gone too after distro update and that brought it back.


Re. the broken packages, have a look at [this page]("https://help.ubuntu.com/community/SynapticHowto") under the section "How to fix broken packages".

If that doesn't do the trick, maybe you could try
```
sudo dpkg --configure -a
```.

:KSGood luck:KS

:P Oh, and remove administration privileges from your brother's account...:P

---

### Post by mash.ky on 2009-02-26
hey guys thanx for all. i reinstalled without any lose of my configuration data. now it's working pretty cool. thanx again guyz :D

ps: never let my brother to touch my computer... hik hik hik

---

