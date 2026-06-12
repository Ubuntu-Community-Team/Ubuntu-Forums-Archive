---
title: "Updating Installation"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by rawbertb on 2011-06-08
I guess I have Ubuntu 10.10 and would like to update to 11.04--is there a way to do this without downloading a USB?

---

### Post by jtarin on 2011-06-08
Download an .iso and burn to CD or use the Update Manager to upgrade. If the upgrade does not show you will need to enable it in software sources.Upgrading should be done cautiously. Make a back up of your /home directory at the very least. I like to back up an image of my complete installation before I do an upgrade.

---

### Post by nzjethro on 2011-06-10
If you don't want to download the actual .iso for Natty, use Update Manager. I used it when I first installed Maverick, but decided I'd get used to Linux on a tried and trusted version rather than the newest version. Open a terminal and type
```
update-manager
```

Else if you like the CL, try
```
sudo do-release-upgrade
```

---

### Post by nzjethro on 2011-06-10
And yes, as jtarin said, be sure to back up all your data, or even your entire system. I lost an entire Windows 7 installation (files and all) last time I mucked around with installation. Although it turned out to be a blessing in disguise 'cos it made me switch to Ubuntu as my primary OS.

---

### Post by jwcalla on 2011-06-10
Just for my edification... when going through the "Upgrade" process... all installed software (e.g., in /usr/local, /usr/share, etc.) and most current configuration settings (desktop, driver modules, whatever) are expected to be blown away, right?  Only /home is intended to be left untouched?

---

### Post by jtarin on 2011-06-10
Not necessarily.....only applications and dependencies that are being upgraded. Some things will be removed,yes as they are not compatible and you will have to wait to reinstall them when and if they become available.

---

### Post by jwcalla on 2011-06-10
> **jtarin said:**
> Not necessarily.....only applications and dependencies that are being upgraded. Some things will be removed,yes as they are not compatible and you will have to wait to reinstall them when and if they become available.

Thanks for the response.

Does the upgrade process give any indication of what will be kept and what will be replaced?  I guess, for example, the installed version of mplayer could be replaced (no big deal) but my personally compiled version (mplayer-mt) would remain untouched?

Also, if you know, is the gnome2 experience in 11.04 the same as 10.10 or was any functionality accidentally broken with the intro of unity?

Thanks for the help... I'm still undecided on whether I want to upgrade to 11.04 or just manually upgrade the kernel, packages, etc.

---

### Post by jtarin on 2011-06-10
> **jwcalla said:**
> Thanks for the response.

Does the upgrade process give any indication of what will be kept and what will be replaced?  I guess, for example, the installed version of mplayer could be replaced (no big deal) but my personally compiled version (mplayer-mt) would remain untouched?You might view the [_release notes_]("https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes") it might give you and idea and this [post]("http://ubuntuforums.org/showthread.php?t=1608846").

> **jwcalla said:**
> Also, if you know, is the gnome2 experience in 11.04 the same as 10.10 or was any functionality accidentally broken with the intro of unity?

Thanks for the help... I'm still undecided on whether I want to upgrade to 11.04 or just manually upgrade the kernel, packages, etc.I can't help you there as I don't use 11.04. I'm one of the dissenters.:p 10.10 is fine for me.

---

### Post by jwcalla on 2011-06-10
> **jtarin said:**
> I can't help you there as I don't use 11.04. I'm one of the dissenters.:p 10.10 is fine for me.

Ahh I didn't even notice.  I think I'll stick with 10.10 too.  ;)

Thanks.

---

### Post by jtarin on 2011-06-10
> **jwcalla said:**
> Ahh I didn't even notice.  I think I'll stick with 10.10 too.  ;)

Thanks.Don't let me sway you. ;) There's a 2 threads on the board somewhere about reactions to 11.04......for and not so for.:p

---

### Post by CVGH on 2011-06-10
Update manager told me that 11.04 was available, but I just installed 10.10 as my first foray into the Linux world. 
So I'm going to stick with it until April 2012 and see what shakes out in the Unity/Gnome3 "war" :D
I may even enable the backport repo then...
You could get the iso and run it in Virtualbox, but it won't really tell you if 11.04 will work with your hardware. 
Have to boot from the CD for that.
Good luck!

---

### Post by jwcalla on 2011-06-10
> **jtarin said:**
> Don't let me sway you. ;) There's a 2 threads on the board somewhere about reactions to 11.04......for and not so for.:p

Yeah from what I've seen of Unity and Gnome 3 so far I'm not looking to upgrade.  ;)  I'll try to keep my system fresh with manual installs of certain software instead.  (PPAs seem to support Natty and Lucid but not Maverick -- bah!)

Maybe another one or two releases of Unity / Gnome 3 and they'll be a bit more... let's say... "attractive" for my purposes.  But by then I might be on a different distro.  Soooo many options.  :)

---

### Post by jtarin on 2011-06-10
Yea Ubuntu removed some of my ppa's when I upgraded, but I found all of them again for maverick. There out there. Gotta search.

---

