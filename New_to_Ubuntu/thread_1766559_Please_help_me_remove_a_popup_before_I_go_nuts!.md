---
title: "Please help me remove a popup before I go nuts!"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by geekwanabe on 2011-05-24
Hey guys!  I've prided myself in never having to ask a question, as I've always found the solutions to my problems by reading the forums. But I've got an Amazon pop up that won't, go away!  Please help me get rid of it!  

It's a pop up that occurred when Amazon wanted to install a new version of its tool bar with which I had no problem.  The window wants me to confirm I want it to download or to un-install it.  

The problem is that it won't respond to my clicks on either option, won't respond to right clicks and when I close it, it just pops up again and again on every page I open.  

Does somebody have some code that I can enter into the terminal to get rid of this scourge?  I even un-installed the old tool bar, but the window still pops up.  

Any help would be appreciated, but remember, I need baby talk.  I don't even know how to show you what's on my system!  

Thanks in advance!  Oh, I'm using Natty on a Dell Studio 1555 if that helps, although the pop survived my upgrade from the last distro.

---

### Post by sandyd on 2011-05-24
> **geekwanabe said:**
> Hey guys!  I've prided myself in never having to ask a question, as I've always found the solutions to my problems by reading the forums. But I've got an Amazon pop up that won't, go away!  Please help me get rid of it!  

It's a pop up that occurred when Amazon wanted to install a new version of its tool bar with which I had no problem.  The window wants me to confirm I want it to download or to un-install it.  

The problem is that it won't respond to my clicks on either option, won't respond to right clicks and when I close it, it just pops up again and again on every page I open.  

Does somebody have some code that I can enter into the terminal to get rid of this scourge?  I even un-installed the old tool bar, but the window still pops up.  

Any help would be appreciated, but remember, I need baby talk.  I don't even know how to show you what's on my system!  

Thanks in advance!  Oh, I'm using Natty on a Dell Studio 1555 if that helps, although the pop survived my upgrade from the last distro.
The easiest way to get rid of this stuff is to regenerate your firefox profile.

[B]note: things that you do not backup will be lost forever! This means bookmarks, extensions, history, .etc .etc.

[/B]1.) Backup the things in firefox that you need
2.) ```
mv ~/.mozilla/firefox ~/.mozilla/firefox.bak
```

Open firefox.

---

### Post by 5149.5 on 2011-05-24
You could try clearing cookies for amazon.

---

### Post by webofunni on 2011-05-24
You can try clearing cache 

```

rm -rvf ~/.mozilla/firefox/*/Cache/

```

and, deleting all the amazon related files that you can find from

```

find ~/.mozilla/firefox -iname *amazon*

```

---

### Post by geekwanabe on 2011-05-24
Thanks guys!  I all those things and one of them worked!  I can't believe I didn't think about cookies and cache!  Thanks again!

---

### Post by webofunni on 2011-05-24
Please change the subject and mark it as [solved], if the issue fixed.

---

