---
title: "Amarok Issues"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by N84Christ on 2010-10-04
Hi downloaded Amarok and I am having issues with it loading and seeing my mp3 Sansa Fuze. I need to find out how to delete it and try to re install amarok.

---

### Post by gordintoronto on 2010-10-04
Did you use Synaptic?  If so, you can just ininstall it.  It's much better to use Synaptic or Software Center to install programs.

---

### Post by McTwitch on 2010-10-04
Open a terminal. ```
sudo apt-get remove amarok
``` that will get rid of it, followed by ```
sudo apt-get install amarok
``` will reinstall the bugger. If you don't know how to get the terminal, it's just Applications>Accessories>Terminal

---

### Post by sandyd on 2010-10-04
> **N84Christ said:**
> Hi downloaded Amarok and I am having issues with it loading and seeing my mp3 Sansa Fuze. I need to find out how to delete it and try to re install amarok.

try setting your fuze to MSC mode.
You can do it by following these steps
Settings -> System Settings -> USB Mode.
Set it to MSC

---

### Post by Goolie on 2010-10-05
Yes, switching to USB mode worked on my Sansa View.  I recommend attempting that first.  Although, I am using Rhythmbox.  

Should work after you switch it's mode.

---

