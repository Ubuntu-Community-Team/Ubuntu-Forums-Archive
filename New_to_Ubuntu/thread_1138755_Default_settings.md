---
title: "Default settings"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by projecthikari on 2009-04-26
How do I return the computer to it's default settings? I mean, like, as if it was brand new. (of course, with my folder still on the desktop.)
I just want to adjust everything from scratch.

---

### Post by NESFreak on 2009-04-26
> **projecthikari said:**
> How do I return the computer to it's default settings? I mean, like, as if it was brand new. (of course, with my folder still on the desktop.)
I just want to adjust everything from scratch.

backup important files and reinstall not an option?

If you changed some stuff that required you to give your password it might be a bit harder to restore. If you'd just want to restore your desktop you could try going to your homedir in nautilus and press control-H which shows your local files. You could remove anything that you think you could miss. They're automatically regenerated once you start the application which files you just deleted.

hell you could even make a backup of all your important files and completely clear your homedir.

Be sure this is what you want though. It might be wise to just remove the config files of the applications you'd like to reset. If you don't know which ones, there's probably a friendly dude (or gall) here to tell you.

---

### Post by snova on 2009-04-26
> **projecthikari said:**
> How do I return the computer to it's default settings? I mean, like, as if it was brand new. (of course, with my folder still on the desktop.)
I just want to adjust everything from scratch.

The system, or your desktop/application configuration?

If you just want to reset the desktop, open Nautilus to your home directory, enable hidden files, and rename/trash/delete these:

[LIST][*].config[*].gnome[*].gnome2[*].gconf[*].gconfd[/LIST]

There might be a few other places where Gnome stores configuration (.gnome2_private or something, I think). Applications may use other files and directories, as well.

Now, the system... hopefully that is only ever changed by adding and removing packages. If you removed things it's easy, just reinstall the **ubuntu-desktop** metapackage. But if you added things, I don't know of a straightforward way to remove them without doing it manually.

---

### Post by NightwishFan on 2009-04-26
Backing up all of your important data in your home directory and then deleting all of the hidden files is dramatic and effective. Only do so if you really really know everything you need to keep.

Otherwise you can try to restore all GCONF to default:

```

mv ~/.gconf ~/.gconf.old
mv ~/.gconf.d ~/.gconf.d.old

```

This should reset all the programs integrated with gconf to default. To return to your old configuration simply copy the .old files back over the regular ones.

---

### Post by projecthikari on 2009-04-26
thanks guys! :]

---

