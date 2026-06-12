---
title: "removing programs"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by zubaer on 2008-12-18
hi all! second day w/ linux went a little better. one quick question...how do you remove programs completely?  I thought I deleted a few, but they are still showing on my netbook remix desktop.
thanks!

---

### Post by hellion0 on 2008-12-18
(Disclaimer: I don't use the Netbook remix, but these methods should still work with it.)

Two ways.

First method (Easier):
1) Open Synaptic.
2) Search for the programs you want to remove.
3) Click on them and choose "Mark for Removal"
4) Apply changes once you've selected all you want to remove.

Second method (Advanced):
1) Open a Terminal.
2) Type in the following: ```
sudo apt-get remove (program1) (program2) (etc...)
```(You will be prompted for your password.) Replace (program1) and such with the names of the programs you want to get rid of.
3) Watch the text roll by. You may be prompted by apt so it can be sure you really want to remove everything issued to it.

If they're still showing up on the desktop after that, or if you already did one of these things already, you should be able to right-click on the desktop launcher and delete it by selecting the appropriate option.

---

### Post by zubaer on 2008-12-18
thanks!

---

### Post by jerome1232 on 2008-12-18
Just to add that method will remove the program but leave behind a few text files used by the programs for storing their configurations.

If you want to remove the configuration files as well then in synaptic mark for complete removal or add the --purge option when using the command line method.

```
sudo apt-get remove --purge programName
```

---

