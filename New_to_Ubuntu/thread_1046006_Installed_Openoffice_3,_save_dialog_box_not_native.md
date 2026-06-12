---
title: "Installed Openoffice 3, save dialog box not native Ubuntu"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by MiniMe on 2009-01-21
Hello!

I've installed Openoffice 3 on my Ubuntu 8.04 desktop with the debs from Openoffice.org as per [http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)

The install works well but now when I select file->save as I get the openoffice dialog box rather than my ubuntu dialog box which has my "places" with my bookmarks/shortcuts which I much prefer. In openoffice, selecting tools->options>general and checking or unchecking "Use OpenOffice.org dialogs" under "Open/Save dialogs" doesn't give me back the native Ubuntu Save dialog box. 

I tried deleting Openoffice 3 and going back to 2.4 but I still don't have the native ubuntu save dialog box. I still have it for other all other applications though. Any idea about how to get it back for Openoffice?

Thanks!

---

### Post by bruce89 on 2009-01-21
The GTK+ file dialogue thing is a sort of plugin, it's in the openoffice.org-gtk package.

---

### Post by MiniMe on 2009-01-21
Many thanks! Installed openoffice.org-gtk via synaptic and it works like a charm!

---

