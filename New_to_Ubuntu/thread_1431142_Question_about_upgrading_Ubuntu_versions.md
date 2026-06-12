---
title: "Question about upgrading Ubuntu versions"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by LinuxFox on 2010-03-16
I have some questions about upgrading Ubuntu versions.  I plan on doing this when the next LTS is out, and I'd like some answers.

As far as I know, upgrading replaces old elements from Ubuntu, at least I was told this last time I asked.  I also installed via Wubi so I can keep Windows, would upgrading overwrite Windows or not?

Can I upgrade via CD, or do I have to do it through the update icon?

Also do the upgrades stay up or do I have a limited time to do it?

Also, my laptop is Xubuntu with the Ubuntu Desktop installed (because I prefer it), will I still keep the Ubuntu desktop or will it give me Xubuntu?

Please answer my questions and thanks in advance.

---

### Post by aeiah on 2010-03-16
it will upgrade all of the packages you have installed, so it'll upgrade all your xfce ones (which are installed as part of xubuntu) and all of your gnome ones (which you installed as part of the ubuntu desktop metapackage) in line with the current distribution version.

it shouldnt disrupt your windows partition, although things may go weird because the new ubuntu uses grub2. it certainly won't delete your windows partition though, but you may find you need to mess with grub if it does something unexpected to be able to boot into it.

to be honest, the best course of action may be to remove ubuntu and install the new version in a proper dual boot setup (using separate partitions), especially if you're planning on upgrading through more than one version (ie, you're running a version earlier than 9.10 and plan on going to 10.04)

---

### Post by 3rdalbum on 2010-03-16
Doing an upgrade will not hurt Windows. It will basically download new Ubuntu packages from the repositories (or from the Alternate CD, if provided) and install them as though you were just installing a new program.

There are two ways of doing such an in-place upgrade. Either you can run Update Manager, which will check for new versions of Ubuntu and give you a button to press to perform the upgrade. Or, you can download the Alternate CD, insert it while Ubuntu is running, and run the 'cdromupgrade' script that's on the CD. This will use the Ubuntu main packages from the Alternate CD, and download any updates to anything you have installed that is not on the CD.

The upgrades never expire until the distribution becomes End Of Life. So for example, if you were running Ubuntu 8.04 and wanted to upgrade to 8.10, you only have about a month to do it, because Ubuntu 8.10 reaches End Of Life in April. If you're on Ubuntu 9.10 and want to upgrade to 10.04, you have three years to do it.

Your system will still be Xubuntu, because it upgrades the packages you have.

A lot of people will recommend a clean install of the new version of Ubuntu. I will most likely do a clean install of 10.04 when it comes out, partially because I'm having some odd quirks occurring at the moment. But upgrading in-place should be pain-free, I've done it a fair few times without issues.

---

### Post by LinuxFox on 2010-03-16
Thanks for the answers and giving me an idea on how upgrading Ubuntu will work.

---

