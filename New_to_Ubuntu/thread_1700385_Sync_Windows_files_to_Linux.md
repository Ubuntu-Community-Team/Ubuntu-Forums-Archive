---
title: "Sync Windows files to Linux"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by DFickel on 2011-03-04
Hey guys I created virtual machine with windows 7 and ubuntu runnin on top, works pretty cool but wanted to know how to sync the files over if its possible, I've seen different software claiming to do so but thought I'd ask

---

### Post by Chronon on 2011-03-05
Is Windows 7 the host system or are they both guests running on an unmentioned host?

If Windows 7 is the host then you should be able to set up a shared folder.  If you are using VirtualBox then you can follow these instructions:
[http://forums.virtualbox.org/viewtopic.php?t=93](http://forums.virtualbox.org/viewtopic.php?t=93)
Here's another source:
[http://www.giannistsakiris.com/index.php/2008/04/09/virtualbox-access-windows-host-shared-folders-from-ubuntu-guest/](http://www.giannistsakiris.com/index.php/2008/04/09/virtualbox-access-windows-host-shared-folders-from-ubuntu-guest/)

(I'm having to make a lot of guesses.  You'll get much better help if you clearly describe your situation.)

---

### Post by DFickel on 2011-03-05
yep windows is the start up os, then i open ubuntu with virtual box, so you guessed right on the money ha, Ill try those steps and see what i can do. any other info i need to know?

---

### Post by DFickel on 2011-03-05
i know you can get your windows files brought into ubuntu if i run ubuntu boot, that way I can run ubuntu solely and have all my windows files. how would i go about this

---

### Post by jbiggs12 on 2011-03-05
You need to install the Virtualbox extensions on the Ubuntu machine, that way you can easily transfer files between the two. If that's too complicated then I'd recommend setting up dropbox on both machines ([http://www.dropbox.com](http://www.dropbox.com)) and just syncing them both over the internet.

Have fun!

---

