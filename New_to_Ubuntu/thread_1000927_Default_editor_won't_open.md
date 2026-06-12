---
title: "Default editor won't open"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by muppetjones on 2008-12-03
I'm using eee ubuntu hardy on an EEE 1000.

Gedit was causing some problems at start up and no matter how many times I fixed it, the darn thing happened again -- a file was supposed to be type 1 but was type 2 instead.

So I'm trying out Kedit and Kate. Unfortunately (and this has been a problem, but while I was using gedit, it was okay), no other text editor will open automatically. I cannot double click on a file and have it open in my chosen editor -- it only works with 'Text Editor', which was gedit.

I've tried the following editors:
1) Bluefish
2) Kedit
4) Komodo

Here are the solutions I've tried:
1) right-clicking the file and changing the 'open with' program in properties (including removing all other options from the list)
2) right clicking the file and choosing the editor from the list
3) editing ~/.local/share/applications/defaults.list 
 and putting the following
[Default Applications]
text/plain=kedit
4) sudo update-alternatives --config editor

There are 3 alternatives which provide `editor'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/vim.tiny
*         2    /bin/ed
 +        3    /bin/nano

Press enter to keep the default[*], or type selection number: 

which never seems to change options.

All of the programs will open from the command line, and all will open individually. They also open the file from within the program.

Please help!!

---

### Post by icanfly0307 on 2008-12-03
Hi,
      Have you tried Mousepad? It's pretty stable and lightweight.

[FONT="Courier New"]sudo apt-get install mousepad[/FONT]

---

