---
title: "cannot see printer on peer to peer network"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by groovomata on 2007-01-20
Hi All,
I connect my kubuntu laptop to a four computer peer to peer network at work. The printer is shared from a windows xp computer. I can browse the various computers on the network however I cannot see the printer. 

When I try to configure the printer in the KDE Control Module, I can enter user name and password I have on that xp machine however whenever I try to print a test page I get the following result:
> A print error occurred. Error message received from system:

cupsdoprint -P 'tmpprinter_F8mI0dpA' -J 'KDE Print Test' -H '/var/run/cups/cups.sock:631' -U 'root' -o ' multiple-document-handling=separate-documents-uncollated-copies orientation-requested=3' '/usr/share/apps/kdeprint/testprint.ps' : execution failed with message:
client-error-not-possible 

Does anyone have any ideas?
Thanks as always,
Erik.

---

