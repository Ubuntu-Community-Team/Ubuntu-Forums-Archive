---
title: "Non-Working Menu Shortcut for Notemeister"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by mikeTherob on 2010-03-06
Hello everyone, I'm kinda new here (as you can probably tell,) so please bear with a new guy.

I was recently looking for a Linux equivalent of OneNote, and after much searching I came upon an application which suited my needs called [Notemeister]("http://notemeister.sourceforge.net"). I downloaded it and followed the included instructions, they were as follows:
```

Installation is done using a standard Python setup.py file. Quick
instructions are:

python setup.py build
python setup.py install ( as root )
```After doing this, Notemeister appeared under Applications>Accessories; however, when I clicked on it, the program refused to open. Whenever make an attempt, it only every gets as far as showing an un-clickable icon in my bottom panel which simple says "Starting Notemeister."

I tried fixing it myself before I came to you guys, and the only thing I could attribute it to was the possibility that I don't have the proper dependencies: 
    o pygtk 2.2.0
    o Python 2.3.3
    o gnome-python 2.0.2
I tried to find these packages, with marginal success. I managed to find a tar.gz for pygtk, although I couldn't for the life of me find that version; unfortunately the installation was a bit beyond me as the usual ./configure etc. didn't cut it. When I was looking for Python itself I started on my own computer, and found that I have files by the names of Python, Python 2.6, and Python 3.0 in /usr/lib. I was unable to find gnome-python at all, although by that time I was very frustrated (as one might imagine) and I only checked Synaptic.

Anyway, that's all I've got. Any help will be much appreciated, and if there's anything I can do to make finding a solution easier, please let me know.

Thanks in advance,
mikeTherob

---

### Post by mikeTherob on 2010-03-06
Bump, any suggestions at all would be infinitely appreciated

---

### Post by Sir Jasper on 2010-03-06
Hi,

I do not know the answer to your question. However, if you are happy to use Wine then I think you would likely be well pleased the Windows program KeyNote 1.6.5 which seems to have what you want, and more.

My regards

---

### Post by mikeTherob on 2010-03-06
Thank you very much Sir, KeyNote is up and running perfectly. It's probably better that I use wine for my notes, since I already use Whitaker's WORDS for Latin translations anyway. Again, thank you much.

If anybody is looking at this and is having the same problem, I just got the solution. I tried running the program in terminal and this was what I got:
```
newuser@james-laptop:~$ notemeister
Traceback (most recent call last):
  File "/usr/local/bin/notemeister", line 19, in <module>
    import notemeister.notemeister_main as notemeister_main
  File "/usr/local/lib/python2.6/dist-packages/notemeister/__init__.py", line 24, in <module>
    import Configurator, NewNoteDlg, Note, NoteBuffer, TitleBuffer, NoteTree, NoteView, TimedStatusbar, const, notemeister_main, Stock, Dialogs, utils, sys
  File "/usr/local/lib/python2.6/dist-packages/notemeister/NoteTree.py", line 10, in <module>
    from xml.dom.ext import PrettyPrint
ImportError: No module named ext
newuser@james-laptop:~$
```

Just follow the instructions in every line coming after a <module>, and you're golden. If anybody needs more specific advice, feel free to PM me or something.

---

