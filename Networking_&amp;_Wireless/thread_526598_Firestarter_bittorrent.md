---
title: "Firestarter bittorrent"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by AnotherMuggle on 2007-08-15
I think Firestarter is limiting my bittorrent connections.

How do I set up an exception to allow its traffic through?

---

### Post by CowzRule on 2007-08-15
Open Firestarter and select the Policy tab. Next to Editing, select Inbound traffic policy. In the lower box right click and select Add Rule. In the dialog box that pops up there's an arrow next to the Name box. Click it and select BitTorrent. That will open the default port range of 6881-6889. If you use a different port range just click inside the Port box, clear out those numbers and enter your own. You can also enter your own info (like Azureus) in the Name box. When your done, click add and your rule will appear in the lower box. To finish click Apply Policy up near the top.

---

### Post by AnotherMuggle on 2007-08-16
> **CowzRule said:**
> Open Firestarter and select the Policy tab. Next to Editing, select Inbound traffic policy. In the lower box right click and select Add Rule. In the dialog box that pops up there's an arrow next to the Name box. Click it and select BitTorrent. That will open the default port range of 6881-6889. If you use a different port range just click inside the Port box, clear out those numbers and enter your own. You can also enter your own info (like Azureus) in the Name box. When your done, click add and your rule will appear in the lower box. To finish click Apply Policy up near the top.

Thanks, though it seems that the options to Add Rule etc are greyed out!?!

EDIT: All sorted now thanks :)  Was a case of me doing what I thought I was reading instead of properly reading what was said:oops:

---

