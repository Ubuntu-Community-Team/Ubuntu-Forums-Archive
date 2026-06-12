---
title: "Where does the Ubuntu Live CD store its files?"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by MontelEdwards on 2009-05-01
my just wondering. Im on my old 8.1 live CD because i got the sun ultra 24 and solaris is retarded and i lost my 9.4 cd so im downloading and then going to put the Live Cd on USB so i can install it locally.



Just a question though because im wating for it to download, where does the live cd store files that i download? RAM?

---

### Post by Zoowey on 2009-05-01
Yes, what a live CD does is it dumps as much of it's most important things in RAM, when there's not much RAM then most of it is run directly from the CD itself. It is possible for everything to be run from the CD but since it's running programs and such it stills requires RAM.

---

### Post by Xero Xenith on 2009-05-01
Unless you manually copy files to the hard drive yourself, files are stored in two places - RAM mostly, but if it gets full *AND* if there's a Linux swap partition available, it'll spill over to that partition.

---

### Post by Jimmynemo2 on 2009-05-01
yeah and we should note that anything you download you can save to the disc, but the files for ubuntu itself will be gone when you reboot.

Hope this helps.

---

