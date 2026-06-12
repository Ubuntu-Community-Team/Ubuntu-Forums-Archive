---
title: "Changed password, now cannot get anything?"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by lugoteehalt on 2010-05-29
Installed latest version of Ubuntu 10.4 is it?  Worked alright, but had chosen a highly insecure password for my user account.  So changed it```
$ passwd myname
etc..
```Unhapilly could not then log in - it would not accept the new password, possibly I had misremembered it, or have slightly cocked up the keymap.

So booted in in recovery mode to a root shell and changed the password again using the passwd command.

It now accepts this password but just gives the background with no menus.

Research seems to say what has happened is that the encryptfs passphase needs to be changed.  So how is this done - I have the long mixture of letters and numbers that is the basic encryptfs thing, I wrote it down like it said.

This looks like a common problem that is likely to occur, why the equivocation you get when you search it up?

Any road great thanks for any simple solution??

---

### Post by lugoteehalt on 2010-05-29
Entered ecryptfs-mount-private at the CLI command prompt, $, and it asked for a passphrase.  Entered the password for my account and then things worked.  (had to do alt+F7 and then click on the desktop)

I had previously changed my password using passwd again; so I'll try changing my password back to the passphrase and hope for the best.

---

### Post by CharlesA on 2010-05-29
If the password is incorrect, can't you just boot into a root shell via recovery mode and change the password there?

---

### Post by lugoteehalt on 2010-05-29
Buggered if I know.  But thanks.

Changed the password to the same thing as the cryptographic passphrase, apparently.  And got the original problem back.

Gave up and re-installed, this time asking for just a password to log in and not also for home filesystem.

Now works alright.  I'm new to Ubuntu, the CD is very aggressive - tries to install without asking permission, overwrites grub.  Anyway hope I get used to Ubuntu.

---

### Post by bildr on 2010-05-29
if ubuntu installer hurt your feelings try freebsd from 1999, it'll make you cry.  hope you get used to ubuntu, mint is a ubuntu derivative that is simpler.

---

### Post by diablo75 on 2010-05-30
I had a similar problem once with a system that had an encrypted home folder.  I learned the hard way that telling the system to encrypt your home folder only comes with it's own set of pitfalls if you don't know what you're doing...

If encryption is what you want, you should just encrypt the entire install using the Alternate CD instead of the regular live CD.  It's a little tricky if you are wanting to install an encrypted volume next to Windows (it's kind of like creating a partition inside a partition inside another partition or something), but there are step by step tutorials out there on how to do it.

And if you are REAL serious about encryption, take a USB flash drive and dedicate it to house your /boot partition.  The reason for this is that it's possible to hack a boot partition to "record" a successfully entered password into a text file, send it over the Internet to the hacker, and cover the tracks of the hack by replacing the modified files with the originals (this is detailed in an issue of 2600 I read a few months ago).  So the way to prevent that from happening is to take that /boot partition with you.  The flash drive would basically act like a kind of key to your system.  Without it, the system can't be accessed (which would behoove most people to have a backup flash drive in case the first one is destroyed).

---

