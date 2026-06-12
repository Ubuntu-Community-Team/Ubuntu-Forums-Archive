---
title: "using one click to open apps"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-07-18
been using mint for awhile and just went to ubuntu 10.4 (used other versions for years). stupid question but where is the option to open folders and apps with one click instead of two. cant seem to find it/tks

---

### Post by howefield on 2010-07-18
Try opening Nautilus and go to Edit > Preferences > Behaviour Tab and place a check against Single click to open items.

---

### Post by rburkartjo on 2010-07-18
how, dont show an nautilus app there that is why i started this thread weird. i know i have nautilus conf tool there and one for scripts but can find what you said to look for

---

### Post by Nesaskewatch on 2010-07-18
```
sudo nautilus
```

Select edit>preferences.  Go from there.

---

### Post by Rubi1200 on 2010-07-18
> **Nesaskewatch said:**
> ```
sudo nautilus
```Select edit>preferences.  Go from there.

There is absolutely no need to run Nautilus as root for this!!!

Go to Places > Home Folder > Edit > Preferences > Behavior and change from double to single click to open files and folders.

---

### Post by gandaran on 2010-07-18
> **rburkartjo said:**
> how, dont show an nautilus app there that is why i started this thread weird. i know i have nautilus conf tool there and one for scripts but can find what you said to look for
nautilus is your file browser.

---

### Post by -kg- on 2010-07-18
> **gandaran said:**
> nautilus is your file browser.

Exactly.  On the top left panel, click "Places".  You can click on any location for this operation.  What you launch is the Nautilus file browser.  From the top menu, click "Edit," then "Preferences" at the bottom of the list.

You will then be presented with a Window with tabs at the top.  The second one from the left is "Behaviour".  On that tab, click the radio button beside "Single Click To Open Items" and it will be done.

---

### Post by rburkartjo on 2010-07-18
tks gan and kg. kg did what you said and worked like a charm

---

### Post by new__buntu on 2010-07-18
> **Rubi1200 said:**
> There is absolutely no need to run Nautilus as root for this!!!



and while we're at it let's point out the nautilus is a graphical app, and therefore gksudo should be used instead of sudo.

---

### Post by Rubi1200 on 2010-07-18
> **new__buntu said:**
> and while we're at it let's point out the nautilus is a graphical app, and therefore gksudo should be used instead of sudo.

+1

---

### Post by AlphaLexman on 2010-07-18
And,
```
xdm-open filename.ext
```
will open the file with the default application from the CLI!

A handy alias:
```
alias click='xdg-open'
```

---

