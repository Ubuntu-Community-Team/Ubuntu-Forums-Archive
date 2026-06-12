---
title: "Couple of quick items after new install..."
date: 2010-07-28
forum: New to Ubuntu
---

### Post by x C0MMAND0 x on 2010-07-28
I got a new larger hard drive for my laptop.  I did a fresh install of Ubuntu 10.04 on the new hard drive.  Afterwards, I merged my old /home/user folder with my new /home/user folder, but did not overwrite any files, just merged everything.

I also merged my old /etc/ folder as I know that contains a lot of preferences and whatnot.  I am having a few minor issues so far...

1. Firefox bookmarks are missing.  I have my old hard drive and I have it mounted externally, so it should be easy to find them but I tried importing "bookmarks.html" but it did not work...

2. For some reason, all of the txt files I have copied over whenever I try to open them it asks if I want to run/display etc.  This is because for some reason all of my txt files are marked as executable.  Once I change this, I can then open them in gedit...but I shouldn't have to chmod -x ALL of my txt files...

3. I thought if I copied my /home/user folder over it would change my toolbar at the very top of the screen to be the way I used to have it in terms of icons and everything...perhaps I am missing something?

I'm not sure if there was an easier way to merge my old stuff into my new stuff but this is where I'm at so far, and any help would be greatly appreciated.  I am currently running a dpkg --set-selections command to install all of my old programs and everything right now.

---

### Post by marshmallow1304 on 2010-07-28
If you do a merge and overwrite from your backup to your /home/user, you'll get your Firefox stuff and all your settings.

---

### Post by Deiz on 2010-07-28
/etc/ is for system-wide configurations, the Firefox profile is contained in ~/.mozilla/firefox - If you want the old one, it will be in $MOUNTPATH/home/$USER/.mozilla/firefox/, $MOUNTPATH being where you have mounted your old disk. If you copy it over you'll have access to your bookmarks, saved passwords, old extensions, etc., which may be what you want.

The execute bit being set sounds like incorrect mount options. You could correct the umask, or just copy the files over and (presuming they all share the .txt extension), run:

```
find ~/ -type f -iname '*.txt' -exec chmod -x {} \;
```

I don't use GNOME, but presumably the upgrade replaces the old default theme and in turn the window manager's button location.

[This](http://lifehacker.com/5500577/move-ubuntus-window-buttons-back-to-the-right) is one solution to that issue.

---

### Post by x C0MMAND0 x on 2010-07-28
> **Deiz said:**
> /etc/ is for system-wide configurations, the Firefox profile is contained in ~/.mozilla/firefox - If you want the old one, it will be in $MOUNTPATH/home/$USER/.mozilla/firefox/, $MOUNTPATH being where you have mounted your old disk. If you copy it over you'll have access to your bookmarks, saved passwords, old extensions, etc., which may be what you want.

The execute bit being set sounds like incorrect mount options. You could correct the umask, or just copy the files over and (presuming they all share the .txt extension), run:

```
find ~/ -type f -iname '*.txt' -exec chmod -x {} \;
```

I don't use GNOME, but presumably the upgrade replaces the old default theme and in turn the window manager's button location.

[This](http://lifehacker.com/5500577/move-ubuntus-window-buttons-back-to-the-right) is one solution to that issue.

That command works for all of my files that are actually properly labeled with .txt in the filename, but I have a lot that are just the filename with out "name.txt" it's just "name" but the type is "plain text document (text/plain)"

---

### Post by x C0MMAND0 x on 2010-07-28
> **marshmallow1304 said:**
> If you do a merge and overwrite from your backup to your /home/user, you'll get your Firefox stuff and all your settings.

Thank you, overwriting it worked perfectly.

---

### Post by Deiz on 2010-07-28
> **x C0MMAND0 x said:**
> That command works for all of my files that are actually properly labeled with .txt in the filename, but I have a lot that are just the filename with out "name.txt" it's just "name" but the type is "plain text document (text/plain)"

You can act based on detected file type, as well.

For example:

```
find ~/ -type f -not -iname '*.sh' -not -iname '*.pl' -not -iname '*.py' -print0 | xargs -0 file -0 | awk -F '\0' '{ print $1 "\0" }' | tr -d '\n' | xargs -0 chmod -x
```
That will find all text files (that aren't shell/python/perl scripts) in your home directory and make them non-executable.

It's rather ugly, but it needs to be to properly handle spaces, quotes, etc. in file names.

---

### Post by x C0MMAND0 x on 2010-07-28
> **Deiz said:**
> You can act based on detected file type, as well.

For example:

```
find ~/ -type f -not -iname '*.sh' -not -iname '*.pl' -not -iname '*.py' -print0 | xargs -0 file -0 | awk -F '\0' '{ print $1 "\0" }' | tr -d '\n' | xargs -0 chmod -x
```
That will find all text files (that aren't shell/python/perl scripts) in your home directory and make them non-executable.

It's rather ugly, but it needs to be to properly handle spaces, quotes, etc., even new lines in file names.

Excellent!  Thank you that worked perfect.

The last thing I need to figure out is how to get my top menu bar back to the way it was... (Where Applications / Places / System is, etc...)  Any ideas?  I'm guessing I need to replace something instead of merge like I did, but I'm not sure what...

---

### Post by Ole Tange on 2010-07-30
> **Deiz said:**
> You can act based on detected file type, as well.

For example:

```
find ~/ -type f -not -iname '*.sh' -not -iname '*.pl' -not -iname '*.py' -print0 | xargs -0 file -0 | awk -F '\0' '{ print $1 "\0" }' | tr -d '\n' | xargs -0 chmod -x
```That will find all text files (that aren't shell/python/perl scripts) in your home directory and make them non-executable.

It's rather ugly, but it needs to be to properly handle spaces, quotes, etc., even new lines in file names.

It does not handle newlines in filenames and it also chmods files that are not textfiles. And thus it might be prettier just to write:

find . -type f -not -iname '*.sh' -not -iname '*.pl' -not -iname '*.py' | parallel -X chmod -x

which will do the same. This will only chmod the text files:

find . -type f -not -iname '*.sh' -not -iname '*.pl' -not -iname '*.py' | parallel file -0 |grep -a text | perl -pe 's/\0.*//' | parallel chmod -x

but it still does not deal correctly with filenames containing \n.

Watch the intro video to GNU Parallel at [http://www.youtube.com/watch?v=OpaiGYxkSuQ](http://www.youtube.com/watch?v=OpaiGYxkSuQ) if you have not used parallel before.

---

### Post by chaanakya_chiraag on 2010-07-30
That top menu bar is the gnome panel, whose configuration should be stored in ~/.gconf/apps/gnome-settings/gnome-panel/.  Just replace the xml in that directory with the one from the old hard drive and everything should be back to normal :)

---

