---
title: "Ubutun frozen when I try to install new software"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by carlosgui on 2010-02-23
[FONT=Calibri][SIZE=3]Hi,[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I am very new on this forum and very new to use Ubuntu 9.4 too, I just install on my computer but  I try to install some software but  I don’t have some futures of ubuntu on administration .  Can some body tell me how I can install  adobe flash player  and Oracle database on ubuntu.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Thank you for you help.[/SIZE][/FONT]
Carlos:o

---

### Post by oldos2er on 2010-02-23
To install flash, open a terminal (Applications, Accessories, Terminal) and run ```
sudo apt-get update && sudo apt-get install flashplugin-installer
```

---

### Post by no2498 on 2010-02-23
they need to do the extras first

---

### Post by Rayve on 2010-02-23
Sometimes, I think Synaptic Package Manager (System > Administration > Synaptic Package Manager) is easier for newcomers than the terminal... it was for me, at least!  That way, you can use a GUI and see descriptions of the items before you download and searching can be simpler.

If needed, you can enable different repositories by going to Settings > Repositories, once in Synaptic.

If Synaptic tends to "grey out" once you click on some software and start to download/install it, just give it time.  It works through it every time for me and comes back to itself in a few moments.

---

