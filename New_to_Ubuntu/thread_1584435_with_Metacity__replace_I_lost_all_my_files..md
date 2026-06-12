---
title: "with Metacity  replace I lost all my files."
date: 2010-09-29
forum: New to Ubuntu
---

### Post by batanda on 2010-09-29
hi.

I had renewed metacity and lost all my Home file. What can I do? I am new in Ubuntu world.
thks

batanda

---

### Post by Sef on 2010-09-30
Moved to ABT.

---

### Post by andrewthomas on 2010-09-30
> **batanda said:**
> hi.

I had renewed metacity and lost all my Home file. What can I do? I am new in Ubuntu world.
thks

batanda
You updated metacity?

---

### Post by crf on 2010-10-01
Can you see your files by going to the *Places* menu and choosing *Home Folder*? Or by opening a terminal (type [alt]+[F2] and run gnome-terminal), which should start in your home directory, running *ls* in the terminal should print the files and folders in your home directory ([more help on the command line](https://help.ubuntu.com/community/CommandlineHowto)).

I would guess that if they exist, you'll see them there.

--
Probably something about your desktop files became corrupted during an update. This has happened to me at least twice :rolleyes: . You could try creating a new user just to test this theory (System menu --> administration --> Users and groups). Once you've made a new user, log in as that user and check if that user's desktop is normal.

The following will delete all customizations you've done on your desktop: open a terminal, run ls -a (which will show all files in a directory, including configuration files), and delete (or rename, if you want to be cautious) the files .gnome2, .gconf and .gconfd. Then log out and back in.

---

