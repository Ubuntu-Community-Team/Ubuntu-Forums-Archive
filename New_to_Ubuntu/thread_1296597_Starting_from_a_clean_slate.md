---
title: "Starting from a clean slate"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by eilios on 2009-10-20
I have installed a lot of programs during my Ubuntu usage, but now I find that I want to go back to the default gnome install, but I have no idea how to do so. Is there a command that does that?

---

### Post by martrn on 2009-10-20
What do you mean? Do you mean you have installed extra desktops and you want to revert to just having the gnome desktop or you have installed a great many programs and which to reduce the amount of programs you have installed on ubuntu or something else.

There is no going backwards to a fresh install and at this time there is no uninstall or rollback feature to a previous installation or snapshot unless you installed along the way a program to do that.  What is it you wanted to do ?

If you wanted to do a fresh install you could do a fresh install over the top of what you already have, but you might lose any saved files in your /home directory.

---

### Post by eilios on 2009-10-20
I want to go back to the default setup, as in remove everything(except documents) and reinstall. The problem is that I have no cds on me at the moment to install with, so I was hoping there was a command to uninstall everything except the base package.

---

### Post by Mike_IronFist on 2009-10-20
> **eilios said:**
> I have installed a lot of programs during my Ubuntu usage, but now I find that I want to go back to the default gnome install, but I have no idea how to do so. Is there a command that does that?

There's no easy way to do that right now. If you had something like BackInTime, you could system restore to a time when you didn't have all the apps you do right now. As is, you can't just get rid of all the programs in any way, other than uninstalling them manually (via something like Synaptic or Add/Remove). However, you CAN reset GNOME entirely so that it behaves as if it's a fresh install, although all your programs will still be there. If you're interested in doing that, you can have a look here:
[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/]("http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/")

Question: Why do you need to do this? There might be ways to help you do whatever you're trying to achieve without uninstalling a whole bunch of stuff. What makes you want to go back to a default install? Disk Space? Errors? Please let me know - perhaps I might be able to provide additional help.

---

### Post by eilios on 2009-10-20
The problem is that after a long time of trying new things, I have broken tiny things until it added up to no sound and no compiz, which is a major pain because my current desktop relied on compiz. It's still very usable, but having all of these tiny glitches adding up is a major headache, I would prefer to start fresh.

---

### Post by theozzlives on 2009-10-20
> **eilios said:**
> I want to go back to the default setup, as in remove everything(except documents) and reinstall. The problem is that I have no cds on me at the moment to install with, so I was hoping there was a command to uninstall everything except the base package.

Just back-up your documents to an external media and nuke the whole thing. If you don't have one, I'd recommend a separate /home partition. I nuked my laptop when I went to ext4.

---

### Post by eilios on 2009-10-20
Actually, I could probably live with this if I could fix the sound. I don't know what happened to it, but I have no sound. Is there any way to fix this?

---

### Post by Mike_IronFist on 2009-10-20
Well, theozzlives, he said he doesn't have any install media... he needs to be able to start over without usage of CDs.

> **eilios said:**
> The problem is that after a long time of trying new things, I have broken tiny things until it added up to no sound and no compiz, which is a major pain because my current desktop relied on compiz. It's still very usable, but having all of these tiny glitches adding up is a major headache, I would prefer to start fresh.

Try resetting GNOME via the instructions from that link in my previous post. If that doesn't work, you might want to consider theozzlives' suggestion of backing up all your data and reinstalling once you have the stuff needed to do so.

---

### Post by martrn on 2009-10-20
> **eilios said:**
> Actually, I could probably live with this if I could fix the sound. I don't know what happened to it, but I have no sound. Is there any way to fix this?

There is a sound trouble shooting guide for ubuntu at :
[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting").

Following it through always works for me.  I have to re-compile alsa modules for one of my computers.

---

### Post by nevets04 on 2009-10-20
Cant He just reinstall ubuntu?

---

### Post by eilios on 2009-10-21
No, I have no installation media ATM.

---

### Post by eilios on 2009-10-21
EDIT: After typing "sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2", I am getting this error: ```
E: I wasn't able to locate file for the linux-image-2.6.31-11-generic package. This might mean you need to manually fix this package.

```

EDIT: Solved itself, apparently. The sound works now, I think it was a gnome error or something, I'm not exactly sure. Sound works now, but compiz doesn't work(the window decorator is invisible).

---

