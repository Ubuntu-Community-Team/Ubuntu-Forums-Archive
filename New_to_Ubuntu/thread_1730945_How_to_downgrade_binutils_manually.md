---
title: "How to downgrade binutils manually?"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by Fanatico on 2011-04-16
I need to downgrade the binutils packet due to certain reasons. How can I do that manually?

How can I see list of available binutils versions, select the one I need and install it?

I assume, I can uninstall binutils through Synaptic (or apt-get remove binutils), this is simple part.

I prefer to install binutils binaries and not to bild them from sources.

Thanks

---

### Post by Wobblybob on 2011-04-18
open the Synaptic Package Manager find binutls, highlight it then go to [Package] then [Force version] tocheck if there is a previous version that you can use, once forced you can use [Lock version] from the same menu to prevent an upgrade.

---

