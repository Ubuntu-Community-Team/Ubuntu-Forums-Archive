---
title: "Open Office failing on startup"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by henwyn on 2008-12-28
I am having a problem starting Open Office writer under Ibex. There seems to be a problem with a file I had open last time I shut down which it wants to recover before starting. If I let it go ahead it fails and crashes. If I cancel the recovery attempt it fails and crashes as well. I'm thinking maybe remove it and reinstall. Any suggestions on what else to try first?
Thanks.

---

### Post by Skripka on 2008-12-28
Is this OpenOffice3?  Do you have the openoffice-kde package installed?  If so get rid of it, it is a none causer of crashes (possibly this one).

---

### Post by abn91c on 2008-12-28
sudo apt-get remove openoffice.org-kde

---

### Post by henwyn on 2009-01-01
> **Skripka said:**
> Is this OpenOffice3?  Do you have the openoffice-kde package installed?  If so get rid of it, it is a none causer of crashes (possibly this one).

Yes, yes, and yes it was. Thank you.

---

