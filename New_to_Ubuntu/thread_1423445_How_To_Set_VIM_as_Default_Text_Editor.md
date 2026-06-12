---
title: "How To Set VIM as Default Text Editor?"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by duckfeet on 2010-03-06
I know it's in here somewhere, but I'm having trouble finding it...I've got vim installed, but it still defaults to gedit, when I want to default to vim...isn't there a command I can run, that brings up the editors?

Thankyou

---

### Post by agnes on 2010-03-06
```
sudo update-alternatives --config editor
```
Choose vim, now when typing "edit /some/path/blabla.txt" it should bring up vim.

---

### Post by Rocket2DMn on 2010-03-06
If you right click on a file of a specific type, you can go to Properties and choose the Open With tab.  Here you can select the program you want to use to open that type of file.

---

### Post by agnes on 2010-03-06
Right, but setting the "normal" console vim there is impossible, so in that case (if you want to use vim when clicking in Nautilus) you have to install vim-gnome, then you can select 'gvim' in the 'Open With'-dialog.

---

### Post by Rocket2DMn on 2010-03-06
I was going off the assumption that the OP was using gnome to navigate and open files.  If you're going to use the command line, it's just as easy to type "vi" as it is "edit".  You can also run
```
export EDITOR="vi"
```
which is useful for setting the default editor when it is called implicity (e.g. if you ran "visudo").  You're suggestion also works well as it gives a list of some available editors.

---

### Post by duckfeet on 2010-03-06
Yeah, I should have been clearer: I know I can right-click, 'open with' and gvim...but I used command line vim for creating files--for java--and some other stuff, and wanted to just use vim as my default editor when just opening files.

My RC windows just expired last week, and I reinstalled ubuntu, and I'm still kind of familiarizing myself with it all again...you all are such a useful forum, and I am so glad once again to be using ubuntu.

I started out on unix in the old days, and naturally used vi as my text editor, and I'm just now learning to program in java, and wanted to use vim, and to use it in other areas so I would get *rid* of the tendency to use the mouse for everything...that's why I was trying to *not* use gvim, but stick to vim...I think I was confusing a couple of things...

This gives me the info I needed: I now have vim set as default, and tho rightclick still brings up gvim as an option, that is fine...

edit: and now, it *does* bring up vim, when I use any form of editing, from command line...thankyou!

---

