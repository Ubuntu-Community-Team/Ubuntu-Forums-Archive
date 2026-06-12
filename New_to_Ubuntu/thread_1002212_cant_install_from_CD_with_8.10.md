---
title: "cant install from CD with 8.10"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by PaulWhipp on 2008-12-04
I uninstalled openoffice on advice in order to reinstall it. The reinstall failed with lots of broken packages in synaptics so I'm trying to use the CD...

[https://help.ubuntu.com/8.10/add-applications/C/offline.html#repository-cds](https://help.ubuntu.com/8.10/add-applications/C/offline.html#repository-cds) instructions resulted in my adding two copies of the "Cdrom with Ubuntu 8.10 "Intrepid Ibex"" entries in the Ubuntu software entry under Settings repositories. I can't see any way to get rid of them.

With one of the them checked and the CD mounted I cannot see the "Ubuntu 8.10_Intrepid_Ibex" entry listed at all if I click on "Origin" as suggested.

Now, if I select Settings | Preferences - Files tab and click on "Delete Cached Package Files", the package manager hangs and I have to use "force quit"... ("sudo apt-get clean" seems to work fine).

How do I get rid of the extra CD entries?

How do I install the packages on the CD on 8.10?

---

### Post by DBrocks on 2008-12-04
Try

```
Sudo apt-get update
sudo apt-get install openoffice.org
```

---

### Post by PaulWhipp on 2008-12-04
Thanks, I tried that and its just completed successfully. At least oo2.4 is back on my system.

Ironically the bug that lead me down this path of a lost morning's work is still there - every time I open a doc I get "Error loading BASIC of document" file:///usr/lib/openoffice/share/baskic/Gimmicks/script.xlc/script.xlb/:

The file it references is obviously incorrect but purging open office and reinstalling still causes this error on my system. Its probably something I did when adding macros but I've no idea what.

---

