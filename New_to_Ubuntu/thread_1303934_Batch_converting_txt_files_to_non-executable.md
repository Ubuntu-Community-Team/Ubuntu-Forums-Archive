---
title: "Batch converting txt files to non-executable"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by lavadisco on 2009-10-28
I finally ditched Windows and am Ubuntu full time now, and it's great. But I have a whole bunch of txt files that require extra button presses when I open them due to the fact that they are all currently executable by default in Ubuntu. I don't want to have to select "display" every time I open a txt file. Nor do I want to go into the properties of every single one of them and uncheck the executable option. Is there a batch command that will make all txt files in a directory non-executable?

---

### Post by diesch on 2009-10-28
On the command line use
```
chmod ugo-x  /somedir/*.txt
```

---

### Post by Barriehie on 2009-10-28
> **lavadisco said:**
> I finally ditched Windows and am Ubuntu full time now, and it's great. But I have a whole bunch of txt files that require extra button presses when I open them due to the fact that they are all currently executable by default in Ubuntu. I don't want to have to select "display" every time I open a txt file. Nor do I want to go into the properties of every single one of them and uncheck the executable option. Is there a batch command that will make all txt files in a directory non-executable?

Run nautilus and select Edit > Preferences > Behaviour and you'll be presented with an option box to Execute, View, or Ask each time.

Barrie

---

### Post by lavadisco on 2009-10-29
Great, thanks guys, worked like a charm.

---

### Post by Primefalcon on 2009-10-29
> **lavadisco said:**
> Great, thanks guys, worked like a charm.

easier way for the newbie, that doesn't require a terminal or modifying the behaviour of the OS itself......

right click the file, select the permissions tab and take the tick out of allow executing as a program.

problem solved!

---

