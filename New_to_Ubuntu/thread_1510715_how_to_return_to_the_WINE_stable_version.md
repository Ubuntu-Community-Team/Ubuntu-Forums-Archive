---
title: "how to return to the WINE stable version?"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by bilbo.san on 2010-06-15
Hello!
I had wine 1.0.1... (I think...) and wanted to use the 1.2 version, for a app I have is able to work with that version only... and it indeed work. But now that the 1.2 RC3 was released, none of the Win software I had installed works properly, and many wont even load.
I think I prefer to return to the 1.0.1 stable version.
BUT HOW?
Can anyone suggest me how to do it?... or at least, how to completely get rid of this 1.2 RC version.
I guess I am gonna have to re-install all my win applications again.
:icon_frown:

---

### Post by Chesamo on 2010-06-16
```
sudo aptitude purge wine
``` Will remove your WINE installation (but *not* your WINE programs). Then, remove the WINE PPA from your software sources (System > Administration > Synaptic Package Manager > Settings > Repositories). Now, navigate to [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) and download the latest stable version (1.1.38`).

---

