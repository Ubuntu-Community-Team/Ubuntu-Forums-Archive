---
title: "How can I undo rename/delete/move ?"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by BlackoutWorm on 2011-08-23
HEy. I'm new to linux, and I was wondering how I undo rename, delete or move files?

---

### Post by raja.genupula on 2011-08-23
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

this link gonna help you

---

### Post by snip3r8 on 2011-08-23
GUI or command line?

---

### Post by BlackoutWorm on 2011-08-23
> **snip3r8 said:**
> GUI or command line?
Graphic please. I don't really like the text thing.
TO be honest, it makes me feel like a nerd.
Is there a way I can add the undo function to a button or right click menu or something?

---

### Post by seawolf167 on 2011-08-23
[CTRL][Z] is the default for "undo" if available in your program(s)
[CTRL][Y] is the default for "redo" if available in your program(s)

---

### Post by Frogs Hair on 2011-08-23
Right clicking on the folder or document should open a context menu and display the options you are looking for except undo and redo .

---

### Post by raja.genupula on 2011-08-23
> **BlackoutWorm said:**
> HEy. I'm new to linux, and I was wondering how I undo rename, delete or move files?

F2 --> rename
del key --> delete
move --> cut 


all the above things you can get by rightclick

---

### Post by BlackoutWorm on 2011-08-23
I don't mean undo in a program. I mean undo rename, delete or move. You know like in Windows where you can right click and it will say "undo rename" if you just changed a file name.

---

### Post by BlackoutWorm on 2011-08-26
Bump

---

### Post by ofnuts on 2011-08-26
> **BlackoutWorm said:**
> I don't mean undo in a program. I mean undo rename, delete or move. You know like in Windows where you can right click and it will say "undo rename" if you just changed a file name.In Linux, all programs work the same way, and the file explorers are programs like the rest. :) So in a file explorer, Ctrl-Z will undo your latest action (also Edit/Undo if you have an "Edit" item in the menu bar).

---

### Post by BlackoutWorm on 2011-08-26
> **ofnuts said:**
> In Linux, all programs work the same way, and the file explorers are programs like the rest. :) So in a file explorer, Ctrl-Z will undo your latest action (also Edit/Undo if you have an "Edit" item in the menu bar).

I just tested it on my desktop.
I changed a filename and pressed CTRL+Z but nothing happened.

---

### Post by ArielSonique on 2011-11-16
I would like to know the answer to this question as well. Is there a way to undo your last action in linux (analogous to the right-click, undo method) in Windows? It would be so convenient if there were a way.

Sometimes, I accidentally move files into folders. However, I am uncertain what files I moved (because I wasn't paying attention when my stylus accidentally dragged and dropped that file into some nearby folder). So I know that something has changed in the directory but I am uncertain about what has changed. In windows, I could easily right click and undo whatever the last action was - rename/delete/move (as the OP said). But in Linux, I can't see a way to do this?

If there isn't a way, is there at least a log that logs all these events so I could check it and see what was changed?

---

### Post by Gatemaze on 2011-11-16
If you are using nautilus, the file browser of gnome, then AFAIK there is no undo for the operations you are asking. Not sure about thunar in xfce and dolphin in kde.

---

### Post by ArielSonique on 2011-11-16
Is there a log that keeps track of these actions so I can at least check what happened and undo it manually then?

---

### Post by MG&amp;TL on 2011-11-16
Best thing I can give:

Undo delete-go to recycle bin and restore the item.
Undo move-search for the file, then move it back again
Undo rename-errr...right click, rename back to what it was. Or undo, if it works in nautilus.

---

### Post by ArielSonique on 2011-11-16
> **MG&TL said:**
> Best thing I can give:
Undo delete-go to recycle bin and restore the item.
Undo rename-errr...right click, rename back to what it was. Or undo, if it works in nautilus.

These might work. Thanks.

> **MG&TL said:**
> 
Undo move-search for the file, then move it back again


However, the problem here is you can only search for a file when you know exactly which file was moved. In accidental mouse/stylus movements I don't know which file was affected or which folder it went into. But I know that some file has moved because the file list in the Nautilus window looks different.

---

### Post by tartalo on 2011-11-16
> **Gatemaze said:**
> If you are using nautilus, the file browser of gnome, then AFAIK there is no undo for the operations you are asking. Not sure about thunar in xfce and dolphin in kde.

Yes, Dolphin does undo the last action (move/rename...) with ctrl+z 

For those that don't know: Dolphin is the File Manager used in KDE, KDE is the Desktop Environment used in Kubuntu.

---

### Post by MG&amp;TL on 2011-11-16
> **tartalo said:**
> Yes, Dolphin does undo the last action (move/rename...) with ctrl+z 

For those that don't know: Dolphin is the File Manager used in KDE, KDE is the Desktop Environment used in Kubuntu.

...and thunar is the file manager used in xfce, the Desktop Environment in Xubuntu.

Also PCManFM is the manager in Lubuntu

---

### Post by ArielSonique on 2011-11-16
> **MG&TL said:**
> ...and thunar is the file manager used in xfce, the Desktop Environment in Xubuntu.

Also PCManFM is the manager in Lubuntu

Do these file managers undo last actions as well? Does only Nautilus suck in this account?? Does Nautilus have a plugin that adds this undo last action functionality perhaps?

---

### Post by MG&amp;TL on 2011-11-17
PCManFM doesn't. But it's still fairly young, and in active development, so if you want to put your oar in, now is the time.

---

### Post by Gatemaze on 2011-11-18
> **ArielSonique said:**
> Do these file managers undo last actions as well? Does only Nautilus suck in this account?? Does Nautilus have a plugin that adds this undo last action functionality perhaps?

Yup, there has been a report on their development page many years ago. I can't obviously why but it was difficult due to some implementation details. In any case, for rename and accidental delete it should be ok, but i completely feel you when you accidentally move a folder inside another without realising doing so. It's a pain to find out which one was it and where it went. AFAIK you could install thunar under gnome and use it as default, as they are both based on gtk. I am not 100% sure about this so you may want to search a bit or post a new question.

---

### Post by JBA2337 on 2012-10-04
Nautilus 3.3.5, which is in Ubuntu 12.04, has an undo feature. Undo rename, undo copy, and undo delete. Here is a link to the announcement.

[http://www.iloveubuntu.net/nautilus-335-landed-ubuntu-1204-undo-support](http://www.iloveubuntu.net/nautilus-335-landed-ubuntu-1204-undo-support)

To use Nautilus 3.3.5, will it work with any versions of Ubuntu other than 12.04?

JBA2337

---

