---
title: "Newbie question - finding folders"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by MrGollum on 2010-09-12
Hi all,

I'm not new to computers, but I'm totally new to Ubuntu.  I bumbled my way to veetle installation and now I'm trying to run the veetle sound-lag fix see here:

[http://ubuntuforums.org/showpost.php?p=9221303&postcount=12](http://ubuntuforums.org/showpost.php?p=9221303&postcount=12)

First instruction: 1) Firstly browse to the .veetle_vlc folder located in your home folder using nautilus (or your favourite file browser)

... I can't find this folder.  I search for "veetle", I search for "vlc", I can't find it.  There's nothing in my home folder except the folder with my username.

Later in the thread someone had this same problem and suggested trying 'cd ~/.veetle_vlc ; ls' to the confused user.

So I did and received 'lbclient vlc vlc_encoder'

I assume that means the folder is there? but why can't I see it??

---

### Post by migs73 on 2010-09-12
If the folder name is preceded by a '.' it is a hidden folder, just press Ctrl and H to be able to see them.

---

### Post by MrGollum on 2010-09-12
Ahhh thank you!

I knew it was something simple... I had looked for a "view hidden folders" option, but couldn't find it.  Well, now I know :)

---

### Post by Lateralis on 2010-09-12
Files and directories can be hidden in Linux (and Unix), just as they can be in Windows.  These hidden files and directories in Linux are preceeded by a dot.  Nautilus doesn't display these files by default, but as migs suggests, pressing ctrl-h will tell Nautilus to display them.  From there you can navigate to where you need to go. 

Alternatively, you can use the command line. the programme **ls** lists the contents of directories.  Going ```
ls -a
``` will tell **ls** to list all files and folders, including those which are hidden.

---

### Post by migs73 on 2010-09-12
> **MrGollum said:**
> Ahhh thank you!

I knew it was something simple... I had looked for a "view hidden folders" option, but couldn't find it.  Well, now I know :)

Not a problem. Welcome to Ubuntu and welcome to the forum.):P

---

### Post by migs73 on 2010-09-12
BTW if you have a Nautilus window open you can view hidden folders using View--> Show Hidden Files.

Now that we have covered all possible ways of allowing someone to view the folders could you please mark the thread as solved? (top of thread goto Thread Tools and click mark as solved)

Many thanks.:)

---

