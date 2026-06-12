---
title: "Ubuntu bash scripting for desktop settings"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by gpwil1 on 2009-03-31
I am constantly installing new versions of ubuntu, since I have found the auto-upgrades to be broken, or I am changing my hardware too quickly.

I have made all my app installs run as a batch script, but I would like to know if there is a way I can get the appearance and settings changed using a batch script.

In particular I like to have konquerer look similar to windows explorer, with folders on the left and details on the right, as well as the quick navigation address up top.

I would also like to change the layout of the desktop, to have the taskbar at the bottom, with a different wallpaper.

and with a few additional widgets like weather displayed on the taskbar.

Additionally - I would like to change the mouse behaviour to double click etc.

can anyone help?

---

### Post by asmoore82 on 2009-04-01
if you carry your entire home folder with you, all of your personal settings/layout should remain intact
it is important to grab the entire home folder so that you get all of the
hidden "dot" files in there - which would be where the settings are actually saved.

maybe on your next install you should set up a separate root / partition
and /home partition so that you can change out the OS at will
without disturbing you personal files.

---

### Post by gpwil1 on 2009-04-01
Actually I was thinking more along the lines of having a simple bash script, not having to carry around the home dir.

It kind of defeats the purpose having to back up anything.

Ultimately I want to have a bash script with conditions that can work on a clean install to customise it to how I like, so that I can distribute to my friends also.

I'll have a poke around for the hidden files you mentioned.

Alternatively, is there an App which lists all files that have been touched? That way when I make a change I can investigate.

---

### Post by llamabr on 2009-04-01
> **gpwil1 said:**
> 
It kind of defeats the purpose having to back up anything.


I would argue that there is a better reason to do backups than to make installs smoother.

You could probably write a script to do all this, but it would just be a bunch of calls to replace the dot files, since that's where all of those configurations are stored.

I've used the same /home partition for many years, and all of my stuff stays right where I like it, across different distros and versions.

To each his own, though.

---

### Post by gpwil1 on 2009-04-01
Thanks for the reply, but as I mentioned I want it to be suitable for friends to use also.

I don't exactly want to be sharing my home directory with anyone else :) 

I believe I found the daemon I need to track file changes: kfsmd

---

### Post by asmoore82 on 2009-04-01
you could create a generic user account and set it up exactly how you like it -
then tar and gzip up that entire user folder -
to use it as a "skeleton" profile for your personal accounts and your friends's acccounts.

the most proper way to tar up such a folder and in a generic manner would be to run this _from inside_ that user's home folder
```
sudo tar --owner 0 --group 0 --preserve -cvzf ../profile.tgz .
```
^^calling `tar` in such a way with ``.'' as its source will catch all files and folders -
hidden ones too - but never actually store the name of the top folder itself.

and then to expand it to another user account:
```
sudo tar xvzf /home/profile.tgz -C /home/user
sudo chown -R user:user /home/user
```
^^the key here is the less common ``-C'' option, giving `tar` a target directory to expand to;
and of course making sure to give the user ownership of his files -
tar normally does this automagically but we want to use this method
with a variety of yet-unknown user accounts.

The most bizarre thing you will encounter during your investigations will probably be the
gconf system - AKA the GNOME "registry"
it stores everything in ~/.gconf but those actual files can only be manipulated "offline"
whenever I want to mess with them(_very_ rare), I do it from a "failsafe terminal" session.

---

### Post by gpwil1 on 2009-04-08
Thanks guys, so looks like I'll have to carry around a copy of the home directory as well as my howto text doc.

:|

---

### Post by gpwil1 on 2010-11-23
Never mind, I discovered gconftool-2

now i am happy.

edit - now I'm using a live multiboot distro with a customisation script and access to my howto doc in google docs.

much bettererer.

---

