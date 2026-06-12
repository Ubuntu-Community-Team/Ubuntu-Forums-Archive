---
title: "help!"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by Asaf_Shilat on 2006-10-03
hey,
im just now finished installing ubuntu on my toshiba satellite leptop.
now, i want to install my encore ENPWI-G adapter, and i understand that i cant do it with the original cd...
can some one guide me how to do it please???

---

### Post by macabro22 on 2007-05-19
Fetch the windows drivers here:

[http://www.encore-usa.com/](http://www.encore-usa.com/)

unpack it somewhere you remember

Install the ndiswrapper package by going to the menu system -> administration -> synaptic package manager.

Type 'ndiswrapper' on the search field.

Open terminal and go to the place you unpacked the drivers by typing

> cd "path to wherever you unpacked the drivers" 

And then input, one line at a time:

> ndiswrapper -i Mrv8000c.inf
sudo modprobe ndiswrapper
ndiswrapper -m

Then read what I said here:

[http://ubuntuforums.org/showthread.php?t=449049&highlight=enpwi-g](http://ubuntuforums.org/showthread.php?t=449049&highlight=enpwi-g)

And do the same.

Cheers =]

---

