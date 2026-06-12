---
title: "Computer filling up with unknown file !! wow Help"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by Ronok on 2009-12-15
Help !?
 
I had a Computer that had:

"Folders" with "Files" in them

Now within hours I have more than 600 and growing
of these 3 kinds: 

[B][SIZE="3"]Folder.ibex.index.data
Folder.ibex.index
File.cmeta[/SIZE][/B]

ok again it is doing this everywhere:

[SIZE="1"](folder)letters to pluto[/SIZE]
[B]letters to pluto.ibex.index.data
letters to pluto.ibex.index[/B]
[SIZE="1"](file) sally's Rocks[/SIZE]
**sally's Rocks.cmeta**
[SIZE="1"](folder)Beach pix from sally[/SIZE]
[B]Beach pix from sally.ibex.index.data
Beach pix from sally.ibex.index[/B]
([SIZE="1"]file) littlerocks001[/SIZE]
**littlerocks001.cmeta**


searching the net & forums get a lot of results for
"ibex" (aka ubuntu or an animal not this file) lost in the cacophony 
this is not a "hidden file" press "Ctrl+H" ineffective 
Folder.ibex.index.data  has "KEYS.000" in it
Folder.ibex.index     cant open
File.cmeta     cant open
this cant be a Virus right ?
whatever is it, its not right

How to get rid of them all,
and not have any more
Thanks

[SIZE="1"]100% Ubuntu 9.10 (karmic)
GNOME: 2.28.1
Kernel: 2.6.31-16-generic
Intel(R) Atom(TM) CPU N280 @ 1.66GHz[/SIZE]

---

### Post by audiomick on 2009-12-15
The first thing you could do is go to system> administration and start the resource manager. One of the tabs in that shows you running processes. Maybe you can identify what is doing that and stop it.

I am sorry, but I have no idea what it is.

---

### Post by wojox on 2009-12-15
Evolution. Kill evolution.

---

### Post by Ronok on 2009-12-15
Thanks: audiomick,
Thanks: wojox,

That did it !
Thanks for Your Fast Replies

I will mark as [Solved],
but maybe someone could tell or show why this happens, 
when **"Evolution (mail program)"** runs, and
how to tweek it so that it will NOT do this?

Thanks again very Much

---

### Post by wojox on 2009-12-16
It sounds like you have Evolution set up to check for new emails every so often ( 10 -30 minutes ). It maybe pulling in junk files as well. 

I run Thunderbird and have it set to only retrieve files when opened and Filter out junk mail.

---

### Post by Georgia boy on 2009-12-16
Have my system set up like Wojox. Also got rid of Evolution. Didn't like it. Decided that Thunderbird has what I need and addd the calendar for it.

Tom

---

