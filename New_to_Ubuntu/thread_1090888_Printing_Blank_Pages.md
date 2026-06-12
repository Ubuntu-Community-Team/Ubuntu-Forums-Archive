---
title: "Printing Blank Pages"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by Erom on 2009-03-08
Alright, so I'm trying to connect to a shared printer on the network. Connecting to the printer actually works fine:

1) Pulled up printer configuration from the administration menu
2) Changed settings to "show printer shared by other systems"
3) System correctly finds the printer and installs drivers (it's a hp deskjet 5900)
4) Printer is now available for use

However, no matter what program or file format I try to print (even the test page from CUPS) all I get is a blank page. It's not an ink problem - the head doesn't even pan across the page, it just sucks the paper in and shoots it back out without a drop of ink on it, no matter what I do. Obnoxious!

Any ideas?

---

### Post by Nxion on 2009-03-09
I am having the exact same issue. I still am having the issues and have not found the fix. This is actually happing on my Epson Multifunction and a HP Deskjet. I belive that I may have narrowed it down to the version of the driver. The GutenPrinter driver is the offender on this issue, I believe updating the driver should fix it but I have not had time to sit don and install a new one. I tried about 2 months ago and I would have to compile the driver to get them to install. Once I get around to it ill let you know if it fixes it :)

---

### Post by kestrel1 on 2009-03-09
I assume that the printer is printing correctly from other machines on the network?

---

### Post by mandrill on 2009-03-09
> **Erom said:**
> Alright, so I'm trying to connect to a shared printer on the network. Connecting to the printer actually works fine:

1) Pulled up printer configuration from the administration menu
2) Changed settings to "show printer shared by other systems"
3) System correctly finds the printer and installs drivers (it's a hp deskjet 5900)
4) Printer is now available for use

However, no matter what program or file format I try to print (even the test page from CUPS) all I get is a blank page. It's not an ink problem - the head doesn't even pan across the page, it just sucks the paper in and shoots it back out without a drop of ink on it, no matter what I do. Obnoxious!

Any ideas?


Not sure if it will work, but try disabling bi-directional support on the machine the printer is connected to. (on your deskjet, properties>ports, radio button at bottom)  You should probably do that anyway....Good Luck!

---

### Post by kestrel1 on 2009-03-09
Good point mandrill.
I had a problem with a HP 1022N printer a while ago on our network, it was ages before I found that turning the bi-directional printing off resolved the problem.
Not even our network support could figure that one out. :D
It could just work.

---

### Post by Erom on 2009-03-09
Thanks for the help guys. Yes, other computers on the network print fine (Macs and PCs). Unfortunately, I've been called away from the machine in question for work so it will be a few days until I can try the bi-directional printing setting. I will dredge this thread back up when I do to confirm whether or not that helped.

Thanks again, and sorry for the delay.

---

### Post by Erom on 2009-03-20
Hey all. I'm finally back in town and ready to return to this problem. Unfortunately I can't for the life of me find a bi-directional setting, nor even a properties->ports menu either in the print queue or in the HP utility. The host machine is OS X, so perhaps I should take this question to my Mac forum?

Thanks!

---

