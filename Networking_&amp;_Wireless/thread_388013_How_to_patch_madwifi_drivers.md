---
title: "How to patch madwifi drivers?"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by B-Con on 2007-03-19
I'm trying to apply the aircrack-ng patch to my madwifi drivers, but I don't know what to do with the .patch file in aircrack-ng's "patches" directory. How do I use it?

What confuses me is how the first line of the .patch file is:
```
diff -ur madwifi-old/ath/if_ath.c patched_madwifi-old/ath/if_ath.c
```
What's with the "patched_madwifi-old" directory that has a file being compared to the original file? Why is it trying to compare a file that doesn't exist? Is it supposed to exist? Nothing of the sort came with aircrack-ng or madwifi.

---

### Post by spd106 on 2007-03-21
I think you've got the wrong patch, that ones for madwifi-old, you want the one for madwifi-ng. 
See [http://www.aircrack-ng.org/doku.php?id=madwifi-ng](http://www.aircrack-ng.org/doku.php?id=madwifi-ng)

---

### Post by B-Con on 2007-03-21
I have the madwifi-old drivers, though, don't I want the madwif-old patch for that?

---

