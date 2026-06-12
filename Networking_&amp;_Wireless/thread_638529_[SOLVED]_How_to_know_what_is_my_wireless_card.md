---
title: "[SOLVED] How to know what is my wireless card?"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by Mlok on 2007-12-12
Hi,

how can I know what model is my wireless card?
There must be a command to display this information.
Another question would be : how can I know the model of everything inside my PC?

Thank you!

---

### Post by Thanoulis on 2007-12-12
Try the lshw command from terminal...with admin rights it gives you full information of anything into your PC.
Also, with the -html > <somefile.html> parameter it inserts the results into an html file. Quite handy imo!

---

### Post by d0nny2600 on 2007-12-12
There are two applications you can download- 
Hardinfo and Sysinfo

Hardinfo can be got from hardinfo.berlios.de
Sysinfo can be got from gsysinfo.sourceforge.net

One of those should display exactly what you are looking for!

---

### Post by zero-9376 on 2007-12-12
As Thanoulis indicated to list all hardware in a nice web page without installing anything
open a terminal (applications>accessories>terminal) and enter the following

sudo lshw -html > SysInfo.html

once it is finished open your home directory and open SysInfo.html which should give you relevent information which you may be able to post back here or an existing wireless thread

Alternately you can install the applications d0nny2600 suggested which are actually in the repositories so can be installed via add/remove, synaptic, or apt-get.

If this is for a PCI wireless card then the output of lspci or lspci -n may be sufficient to get you some help.

---

### Post by d0nny2600 on 2007-12-12
Correct, These applications can be added simply using the Add/Remove interface!

---

### Post by Mlok on 2007-12-12
Thank you so much to all of you.
My favourite answer goes to "sudo lshw -html > SysInfo.html" which is pretty elegant! (no install)
This makes me feel like coming back to this forum!
Again thank you to all of you!

---

### Post by d0nny2600 on 2007-12-13
You are welcome!

---

