---
title: "Knetworkmanger loading error"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by gsthakur on 2006-10-27
Today I upgraded my ubuntu to 6.10 from its previous version. Earlier the Knetworkmanager was running fine. however after the upgrade I started getting this error. 

knetworkmanager: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory

I checked the /usr/lib and found that this library is now not present in this directory which is required by the Knetworkmanager. I think during the upgrade it is removed.
Does there any solution for this? As removing and re-installing knetworkmanager is not going to help out.

---

### Post by jasil on 2006-10-27
I too did an upgrade to Edgy and I'm having the same problem, but with network-manager-gnome. I even tried to remove NetworkManager totally and install CVS version but that didn't help. Still having the same problem.
Hope somebody could help?

---

### Post by gsthakur on 2006-10-29
Does any body able to solve this issue of connecting on to the internet through wireless?

---

