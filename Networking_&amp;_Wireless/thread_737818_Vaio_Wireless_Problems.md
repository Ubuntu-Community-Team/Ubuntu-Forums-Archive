---
title: "Vaio Wireless Problems"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by rubenlane on 2008-03-27
I have ndiswrapper installed and I have the .exe file for installing my network card drivers on a windows based computer.  However I can't find just the .inf file.  I don't know where to go from here to get my wireless card up and running and right now that's the only internet option I have on that computer.

Can anyone help me on how to proceed in getting my wireless card to work?

---

### Post by dstew on 2008-03-28
You can get the .inf file out of the .exe using the program **cabextract**. You can get it using the synaptic package manager. Enable the Universe repository first.

Once cabextract is installed, issue the command```
cabextract *driverfile.exe*
```substitute the correct name for *driverfile.exe* of course. You should get a folder with the files inside it.

---

