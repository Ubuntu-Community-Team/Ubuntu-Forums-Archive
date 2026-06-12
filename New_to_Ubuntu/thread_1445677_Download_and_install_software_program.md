---
title: "Download and install software program"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by harry003 on 2010-04-02
I am a newbie and I am getting frustrated by the way things just seem to "evaporate"

I thought that I had "downloaded" and "installed" Audacity software (I have used it for years under Windows) but it is nowhere to be found.

Is there anything like Windows Explorer where I can clearly see the entire directory and file structure on the screen at the same time, and root around to look for something that has gone missing?

What can I do to find the Audacity download (it does not appear to be in the "Downloads" directory, even though that is where it should be) in order to manually install it?

Thank you.

---

### Post by Revolutionary101 on 2010-04-02
If Audacity is not showing up in the "Applications>Sound and Video" section of applications, I doubt it was installed. To check open Synaptic (System>Administration>Synaptic Package Manager) and search for Audacity. When you search there should be a list of packages for you to install. Click on the box next to the one called "audacity", mark it for installation, and then hit apply on the top of the window. That will install Audacity for you.

---

### Post by humanaut on 2010-04-03
open a terminal and try the command ```
locate filenameyourlookingfor 
```

---

### Post by @rizz on 2010-04-03
If you want a windows explorer type window, i.e. a graphical representation of the files and folders

just open the terminal and type
```
$ nautilus
```

---

### Post by harry003 on 2010-04-03
Thanks guys. Every answer brings new questions.

I found that Audacity was ready to be installed, along with dozens of other things (this is a new install with Guest Additions, etc). I have accustomed myself to usually saying "yes" to most "updates" that are offered to me, but it looks like I have downloaded a bunch of them but they are not installed.

So they just continue to accumulate until you manually install them? 

I have been in Nautilus but it seems to confine me to my VirtualBox, not allowing me to see all my other drives. I am afraid that I am trapped in there, which diminishes the usefulness of this install to almost nil for me. Manipulating files and directories is what I do every day.

Trying wubi 3 or 4 times always ended in errors and frustration, so I gave up. I used different wubis from different sources, but none worked. It seems that, at least, would free me up to explore all my drives from within Ubuntu.

Last, remember the option for "Solved" when I created this thread, but I cannot find a way to edit it now.

thanks again

---

