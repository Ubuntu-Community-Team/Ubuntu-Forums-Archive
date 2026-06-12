---
title: "Firefox"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by Capitolman on 2010-03-24
Why is the update button in Firefox grayed out?.

---

### Post by chaanakya_chiraag on 2010-03-24
Firefox updates are handled by the System update manager called apt.  You can check for updates for Firefox and everything else installed on your system using System->Administration->Update Manager :)

---

### Post by The Cog on 2010-03-24
chaanakya_chiraag is right. Updating firefox from their web site would undermine the package manager.

On the other hand, if you have installed your own forefox from mozillas web site (as I have, installed in /opt) then you can update it by shutting firefox down, then running "gksu firefox" to run it as root and then using help/update. Don't go surfing as root though - that's a big security no-no.

---

