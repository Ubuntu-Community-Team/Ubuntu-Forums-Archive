---
title: "How to use old version of gedit"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by beetlejuice_masterson on 2009-01-09
Hello -

I'm having an issue with gedit 2.24 - it's a bug with the sftp, so all files are read only.  I didn't have any problems with this until I upgraded to ubuntu 8.10.

I need to switch to gedit 2.22.  How do I go about doing this?  I downloaded the .tar.gz, extracted it, and ran ./configure but it gave me some weird errors....Anybody had experience with this or know how to get rid of 2.24 and revert to 2.22?

Thanks

---

### Post by thegreenblob on 2009-01-09
Hmm... not quite sure how to downgrade gedit. But if the files are read only couldn't you just chmod them to make them not read only?

```
sudo chmod 777 /location/file.txt
```

---

### Post by beetlejuice_masterson on 2009-01-09
They're all 644 but I'm logged in as root so whatever, and anyways I don't want them to be 777.

Does anyone know how to downgrade gedit?  I've got the .tar.gz file I need...just not sure how to go about it.

---

### Post by stchman on 2009-01-09
> **beetlejuice_masterson said:**
> Hello -

I'm having an issue with gedit 2.24 - it's a bug with the sftp, so all files are read only.  I didn't have any problems with this until I upgraded to ubuntu 8.10.

I need to switch to gedit 2.22.  How do I go about doing this?  I downloaded the .tar.gz, extracted it, and ran ./configure but it gave me some weird errors....Anybody had experience with this or know how to get rid of 2.24 and revert to 2.22?

Thanks

Try Geany, I have been using it and it is the best text editor I have ever used.

---

### Post by mc4man on 2009-01-09
If you don't go for the above option and or find a fix then it's
not that that hard to build, you just need the basic build tools, a few additional packages and a fair number of specific -dev packages.

What i'd suggest though, if you must, is building but not installing, just running from the build folder as needed.

If you want to try to replace 2.24.2 that would be a bit of work, if even possible.

(it seems to run fine on my 8.10 install from the build folder, only quickly tested

---

### Post by beetlejuice_masterson on 2009-01-10
mc4man -

awesome.  i'm such a nube that you may need to refresh my memory (lol) how you built it and ran it.

i downloaded the .tar.gz....put it in my home directory and extracted.

as verbose of instructions as you feel like providing would be wonderful - thanks

---

### Post by stchman on 2009-01-11
You can try this:

```
sudo apt-get autoremove gedit
```

This will completely remove gedit.

You can then download the .deb either 32 or 64 bit from the Hardy repos.

[http://packages.ubuntu.com/hardy/gedit](http://packages.ubuntu.com/hardy/gedit)

---

### Post by igknighted on 2009-01-11
Are you sure gedit is the problem?  Gedit doesn't actually have any sftp capabilities, it just borrows them from other libraries.  I suspect your issue is really in the configuration of gvfs (this is new to intrepid, yes?  Didn't hardy use gnome-vfs?).

---

### Post by mc4man on 2009-01-11
Probably you should find an editor that works with your files.

If you want to try gedit .22 in intrepid it seems it would be better to install it.  I noticed running from the build folder or even just installing a built version doesn't use all the plugins or integrate into gnome.

To install the hardy or hardy-update version

You'll need to remove rarian-compat and replace with scrollkeeper. Gedit .24 will run with scrollkeeper installed so I'd do that first in synaptic. (ck. the box to automatically close in the 'applying changes' box so you know when it's done (you'll see what I mean

Maybe try gedit .24 again. If you want to proceed then purge gedit and gedit-common.

When done go here and either install or download and install. Get both gedit and gedit-common, both the same version (hardy or hardy-updates

[http://packages.ubuntu.com/hardy-updates/gedit-common](http://packages.ubuntu.com/hardy-updates/gedit-common)

If you do individually do gedit-common first or put both in a folder, cd to that folder and run 
```
sudo dpkg -i *.deb
```

To revert basically reverse, purge gedit, gedit-commom, replace scrollkeeper with rarian-compat if desired and install the intrepid gedit, gedit-common

---

