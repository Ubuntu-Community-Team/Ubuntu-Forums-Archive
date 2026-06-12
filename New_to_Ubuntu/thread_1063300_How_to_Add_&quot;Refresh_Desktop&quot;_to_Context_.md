---
title: "How to Add &quot;Refresh Desktop&quot; to Context Menu"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by kamni on 2009-02-07
While trying to solve a different, but related problem, I ran across several posts -- both on the Ubuntu forums and on other Linux forums -- asking the same question: how do I create a context menu (right-click menu) that refreshes the desktop in Gnome?

Here are the links to the two archived posts on the Ubuntu forums:
[INDENT][**How to Add "Refresh Desktop" to Context Menu?**]("http://ubuntuforums.org/showthread.php?t=469425&highlight=refresh+desktop") 
[**What does Ctrl+r Do?**]("http://ubuntuforums.org/showthread.php?t=479900&highlight=refresh+desktop&page=1")[/INDENT]

These are both old posts, so if the problem has been solved and I missed something, please point me to the new links! :)  To my knowledge, my Intrepid and Gnome are the most recent versions available in the repository as of this post.  Here is a clunky, but doable answer to the question:

[INDENT]1) Download nautilus-actions and lineakd either by Synaptic, or via the command line:[/INDENT]

```
sudo apt-get install nautilus-actions lineakd
```

[INDENT]2) create a nautilus scripts directory.  For example:[/INDENT]

```
mkdir nautilus-scripts
```

[INDENT]3) make a file to hold your script:[/INDENT]

```
gedit nautilus-scripts/refresh_desktop
```

[INDENT]4) add the following lines of code:[/INDENT]

```
#!/bin/bash
xsendkeycode 71 1
xsendkeycode 71 0

```

This essentially sends the F5 command (the refresh command) to wherever you're clicking.  "71" is the key number on my particular computer for F5.  The "1" sends the signal that the key is being pressed, and then the "0" says that the key is no longer being pressed.

If for some reason this doesn't work, try using [xev]("http://ale.freeshell.org/articles/hotkeys/hotkeys.html") to figure out what your particular keycode is (follow steps 6-9, but mentally replace "hotkey" with "F5").

[INDENT]5) save the file and change it to be executable:[/INDENT]

```
chmod u+x nautilus-scripts/refresh_desktop
```

[INDENT]6) open up the nautilus-actions config dialog at **System -> Preferences -> Nautilus Actions Configuration**.  (If for some reason it doesn't show up in the menu yet, try logging out and logging back in.)[/INDENT]

[INDENT]7) click **Add**.

[INDENT]*In **Menu Item & Action**:*
Label: Refresh Desktop
Tooltip: Refresh the Desktop Display
Icon: (whatever you like, or blank)
Path: /home/{put your user name here}/nautilus-scripts/refresh_desktop
Parameters:

*In **Conditions**:*
Filenames: *
Match Case: [selected]
Mimetypes: */*
Appears If Selection Contains: [Both][/INDENT]
[/INDENT]

When you want to use the script, right click on any file or folder on your desktop (not the desktop background, alas!) and "Refresh Desktop" should now appear in the context menu.

---

### Post by srisharan on 2011-05-23
*When you want to use the script, right click on any file or folder on  your deskto**p (not the desktop background, alas!) *
That can be solved.In the add tab check 'display item in location context men':grin:

---

### Post by s.fox on 2011-05-23
Thread Necromancy - Thread Closed.

---

