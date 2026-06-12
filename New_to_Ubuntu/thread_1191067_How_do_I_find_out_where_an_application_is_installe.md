---
title: "How do I find out where an application is installed? Uninstalling help."
date: 2009-06-18
forum: New to Ubuntu
---

### Post by StuM on 2009-06-18
I am a fairly recent and happy convert to Ubuntu (from Windows), and have managed to find most of the answers to my questions so far.

But I've been a bit trigger happy installing things, and I sometimes find it difficult to uninstall things afterwards, in particular those not installed through the package manager.

So as an example I want to uninstall both the Firefox 3.5 beta 4pre and Opera 10 beta browsers, but I don't know how.  I've read that if they don't exist in the package manager that I need to find where they are installed and look for an uninstall script(?).  The problem is I don't know where they are installed.  In windows I'd right click and see where the menu shortcut points to.  How can I do something similar on Ubuntu, and is there an easier way to uninstall things?

---

### Post by Tibuda on 2009-06-18
Even if you have not installed the applications from the package manager, but from a deb package, you can uninstall it using the package manager.

If you installed them from source code, you have to open the source directory and run "make uninstall".

How have you installed each of these applications?

To see where the menu shortcut points to, you can right-click the Applications menu, click "Edit menu", find your application, and see its properties. They probably are on /usr/bin or /usr/local/bin like most applications.

---

### Post by Azrael3000 on 2009-06-18
If you did install them via a .deb package you can always find them in your package manger. You can find this program at:
System -> Adminstration -> Synaptic Package Manager

Or did you compile these browsers from source?

---

### Post by kukibird1 on 2009-06-18
Check the installed local or obsolete section of Synaptic.

---

### Post by StuM on 2009-06-18
Nice one... thanks for the help.

I installed Opera from a .deb, and you are right it is in the package manager.  It was hiding from me under an unusual name.  I've just noticed you can sort by things that are already installed which made it much easier to find.

Firefox was a .tar.bz2.  I've now uninstalled that using the Installed (local or obsolete) section in Synaptic.

Cheers for the help all... much appreciated.  Knowing this will help a lot in the future too. :D

---

### Post by Sealbhach on 2009-06-18
I often have to do a similar thing, I just install tons of stuff every week. To look for where things are I use the "locate" command. e.g.

```
locate firefox
```

This requires "sudo" now in Jaunty, I don't know why they changed that, grrr...

The "which" command shows where the executable is (like the .exe file on Windows):

```
which firefox
```

This usually show up as /usr/bin/.

Lately, I've found the most expedient thing to do is to either remove things I've installed from .deb packages in Computer Janitor or Synaptic (installed locally) section. If I can't find them there then I do this:

```
sudo dpkg -l | grep *name of package*

```

this returns the name of the package that's installed.

Then to purge remove it:

```
sudo dpkg -P *name of package *

```


Sometimes though, there are other applications that I download as a tar.gz file to my /home folder, e.g. the Yo Frankie game. These run entirely from a folder in my /home folder, so to uninstall them I just delete the folder.

Hope this helps.

.

---

