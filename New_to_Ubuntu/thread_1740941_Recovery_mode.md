---
title: "Recovery mode?"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by Visvalor on 2011-04-27
A long while ago I pressed something on boot that brought me to some form of recovery mode gui and I could select previous... setups? To boot into. 

What button did I press? I thought it was f8 but that doesn't work.

Thanks

---

### Post by Hedgehog1 on 2011-04-28
The typical way to get to recovery mode is:

When booting, hold down the Left 'Shift' key, this will force the Grub menu to be visible.

Once you get the grub menu, arrow down the your kernel of choice with the 'recovery mode' text in it's description.


***The Hedge***

:KS

---

### Post by Rubi1200 on 2011-04-28
You can also edit the current entry by pressing "e" and then navigating using the arrow keys to the line that ends with quiet splash. Remove quiet splash and type > single. Then, "Ctrl" + "x" to boot.

---

