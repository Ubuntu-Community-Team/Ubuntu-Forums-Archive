---
title: "Is it possible to launch a GUI app on PC 2 from PC 1?"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by xocekim on 2007-10-30
Hi, I have recently installed Ubuntu Gutsy on my dads and my own pc's. Is it possible to make an application appear on a remote pc from my own? I know I can run ssh with the -X option but this opens the gui on my end, not his.

For example I could load up SSH on my pc and through some command open up a file in gedit on the remote pc, my dad could then edit the file on his pc in gedit?

Thanks

---

### Post by ddrichardson on 2007-10-30
How about using VNC?

---

### Post by arpnuke on 2007-10-30
I've never done it on ubuntu to ubuntu, but my mac required that I get an xserver and have that running while I was ssh'd into the target machine with the -x argument.  xming is what I would suggest for a windows box and Apple's X server (comes with the install DVD) for a mac.  I'm afraid someone else will have to help you for ubuntu to ubuntu.

---

