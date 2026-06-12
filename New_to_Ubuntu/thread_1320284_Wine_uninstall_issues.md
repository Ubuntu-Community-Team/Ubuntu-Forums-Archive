---
title: "Wine uninstall issues"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by shoaibi on 2009-11-09
even though i have uninstalled wine and deleted ~/.wine entries in my applications menu e.g. Applications > Wine still exist. How can i get rid of it?

---

### Post by The Funkbomb on 2009-11-09
I had the same problem in 9.04.  I couldn't get rid of it either.

---

### Post by Paresh on 2009-11-09
try System->Preferences->Main Menu and either uncheck, or delete the wine settings

---

### Post by shoaibi on 2009-11-09
@paresh:
thank but i have already disabled/hidden the wine menu item, but i want it to vanish completely e.g. get deleted.

---

### Post by Paresh on 2009-11-10
I'm pretty sure there's a delete button to remove the menu item

---

### Post by shoaibi on 2009-11-10
yes but beagle's index (even after reindexing) shows these entries..

---

### Post by mrboojive on 2009-11-10
Try going to .local/share/applications and deleting the folder called "wine," if it is still there. There might also be some Wine related stuff in .local/share/desktop-directories.

---

### Post by shoaibi on 2009-11-10
jackpot.. there were such directories and file there, i have removed then and asked beagle to reindex, this time i don't think they would appear in beagle's index.

Thanks...

---

