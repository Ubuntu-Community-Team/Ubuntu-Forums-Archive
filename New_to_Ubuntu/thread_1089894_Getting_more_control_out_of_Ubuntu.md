---
title: "Getting more control out of Ubuntu"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by infernus_crusher on 2009-03-07
I've used Ubuntu for a year now and I think it's great, but I have several questions I'd like to address to improve my experience on it.
1. How do you disable the creation of "dump" files? (Files of the same name to the original files, but ending with a "~").
2. Why are those "dump files" created in the first place?
3. Is there a way to customise the shortcuts to more applications than the ones listed in System > Preferences > Keyboard Shortcuts? By modifying a text file in the File System, perhaps? For example, I'd like to customise shortcuts for Text Editor and Pidgin to execute.
4. Can you modify Ctrl+Alt+Delete to enable the option to Shut Down? Right now, mine has Log Out and Switch User only.

Note: I'm using the latest Ubuntu 8.10.

---

### Post by thtrgremlin on 2009-03-07
A program I just learned about today, ubuntu-tweak. I have been using ubuntu for several years and I am already in love with this app. Before most of what you were talking about could be configured by running 'gconf-editor', but I think you should check out ubuntu-tweak.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by Trebaruna on 2009-03-07
You may be refering to the backups gedit creates? If you save a file with gedit, it will indeed produce a file called "YourFile~".
In gedit, go to Edit -> Preferences -> Editor
deselect "Create a backup (...)"

---

### Post by thtrgremlin on 2009-03-07
I wouldn't necessarily recommend doing that. Having all your config files automatically backup every time you edit one it very useful in case you screw up. Further, anything you edit with gedit is VERY small. The only thing that you get by disabling backups is a system directory with one last file in it, and no safety net in case of problems.

Or more simply: Those are your backups, don't delete them, especially if part of the system!

It isn't often, but they have saved me on more than a few occasions.

And not to be rude Trebaruna, but while that did answer the question (and sorry I did not address it before) don't you think that it is kind of reckless to just tell someone to stop backing up (ok, not always config) files just because they don't understand what the ~ is for? This is a feature worth explaining and having some respect for.

---

### Post by infernus_crusher on 2009-03-08
Thanks for the answer guys, especially regarding the backup files. I think I'll stick to backing ups for now.

---

