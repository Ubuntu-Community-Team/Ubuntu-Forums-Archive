---
title: "Grub menu timer in dual boot."
date: 2009-01-08
forum: New to Ubuntu
---

### Post by iNeeed on 2009-01-08
Hello hello.  About one month ago I partitioned my disk and installed Vista as well as Ubuntu 8.10.  Sadly I need the vista for my iphone and netflix.
So when the grub is loading and doing its thing I have to press escape to get to the menu and load vista.  The problem is I only have about 3 seconds to do this.  I want it to load the menu automatically and stay there until I decide which OS I'd like to boot. Anybody know if this is possible and how to do it? Your help is as usual much appreciated.

---

### Post by fubbleskag on 2009-01-08
these options are controlled via the file **/boot/grub/menu.lst**

open it with your favourite editor (don't forget sudo/gksudo or you won't be able to save the file when you're done editing)

first, to get rid of the "press escape" requirement, find **hiddenmenu** and comment it out by putting a **#** in front of it

then, do the same for **timeout** and it will no longer choose after 3 seconds

---

### Post by iaculallad on 2009-01-08
On your terminal:

```
gksudo gedit /boot/grub/menu.lst
```

Locate the item below, colored blue:

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR="Blue"]**timeout		3**[/COLOR]
```

and change the value of 3 to a higher value.

Save and Close the file.

---

### Post by wolfen69 on 2009-01-08
do
```
gksudo gedit /boot/grub/menu.lst
```
find the section where it says ## timeout sec

change the 3 to whatever you want. like 3000 or so. save file.

---

