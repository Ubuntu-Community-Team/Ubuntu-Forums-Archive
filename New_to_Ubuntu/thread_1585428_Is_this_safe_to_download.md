---
title: "Is this safe to download?"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by 289531.EXE on 2010-09-30
Update Manager:

gnome-terminal
gnome-terminal-data
linux-generic
**linux-headers-2.6.32-25 (New install)**
**linux-headers-2.6.32-25-generic (New install)**
linux-headers-generic
**linux-image-2.6.32-25-generic (New install)**
linux-image-generic
linux-libc-dev
python-software-properties
software-properties-gtk


This is what comes up. Now, I haven't had a problem installing from the Update Manager but this time I get a 'final warning' pop up which goes something like:

"**WARNING**

You are about to install software that [B]can't be authenticated!
[/B]Doing this could allow a malicious individual to damage or take control of your operating system"

Then it goes into detail about the packages being installed with the first on the list reading:




                                                          - NOT AUTHENTICATED
[RIGHT]


gnome-terminal
gnome-terminal-data
linux-generic
linux-headers-2.6.32-25 (New install)
linux-headers-2.6.32-25-generic (New install)
linux-headers-generic
linux-image-2.6.32-25-generic (New install)
linux-image-generic
linux-libc-dev
python-software-properties
software-properties-gtk


[LEFT]I don't know what to do-
[/LEFT]
[/RIGHT]

---

### Post by msakms on 2010-09-30
It's fine to install those updates. What's meant by those warning pops is that ubuntu doesn't maintain upgrades from some of those packages though, community members might be "or whoever made the package". I have those packages installed and everything is running like charm so, I guess it's okay.

---

### Post by jtarin on 2010-09-30
Go to Main Menu>System>Administration>Synaptic Package Manager>Settings>Repositories. Here you will see the various software sources. The ones you are concerned about come from other than (main).

---

### Post by mcduck on 2010-09-30
> **msakms said:**
> It's fine to install those updates. What's meant by those warning pops is that ubuntu doesn't maintain upgrades from some of those packages though, community members might be "or whoever made the package". I have those packages installed and everything is running like charm so, I guess it's okay.

Actually you don't even get that warning that easily, it's not related to any of Ubuntu's own repositories, not even universe & multiverse (which contain the community-maintained software). Instead it most of the times means that you are using some third-party repository but haven't installed the GPG key for that repository, so the system can't know if it's source you trust or not and can't authenticate the downloads.

(You'll see the warning any time you install or update any packages, regardless if they come from the repository with the missing key or some other source.)

Simply adding the missing GPG key will make the warning disappear.

edit: I almost forgot to add, all those updates are just fine. Actually, as long as you are only using repositories you trust yourself, you can consider any update offered through the package management to be safe. That's the whole point, really. :)

---

### Post by jtarin on 2010-09-30
[Automatically import Launchpad GPG keys in Ubuntu for all the **_PPAs _**you have added to your software sources.]("http://www.webupd8.org/2010/05/automatically-import-all-missing.html")

---

### Post by scarpent on 2010-10-01
I think something else is going on than third-party repositories not being trusted. I have the same warning (and is the first time I've ever seen this), and in my "to be installed list" there is:

linux-headers-2.6.32-25
linux-headers-2.6.32-25-generic
linux-image-2.6.32-25-generic

And these same three things show up in the "NOT AUTHENTICATED" list, along with some other things that don't look like they come from any third party repositories.  (And I don't even think I've added any third party repos on my current install.)

Others include:

python-software-properties
software-properties-gtk

Etc.

---

### Post by jtarin on 2010-10-01
Have you tried going to Menu>Systems>Administration>Software Sources>Authentication>Restore Defaults

---

### Post by scarpent on 2010-10-01
I haven't tried that.  I have four entries in that list:

Ubuntu Archive Automatic Signing Key
Ubuntu CD Image Automatic Signing Key
Medibuntu Packaging Team
Google, Inc. Linux Package Signing Key

What would "restore defaults" do?  Remove Medibuntu and Google?  I'm fine with this as the trusted list -- it still seems that the update manager is incorrectly flagging the linux headers/image as unauthenticated.

---

### Post by scarpent on 2010-10-01
From this thread:

[http://ubuntuforums.org/showthread.php?t=469280](http://ubuntuforums.org/showthread.php?t=469280)

I got the idea to try "sudo apt-get update", and that resolved the issue for me.

---

