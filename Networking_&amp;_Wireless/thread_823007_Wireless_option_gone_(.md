---
title: "Wireless option gone :("
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by pizlo on 2008-06-08
In a valiant effort to speed up linux on my lifebook p 2120, I used to terminal command to install xfce. I logged out, changed the session to xfce and logged in. Things were a bit faster, and all was working but the wireless. I expected to have to put in the wep key, but on opening network manager I saw only wired connection and point to point. No third option for wireless. Then I figured too bad, and switched back gnome. But now even in gnome there are only the 2 options, and no wireless option to configure:(

Any help appreciated.

---

### Post by pytheas22 on 2008-06-08
It's more of a work-around than a solution, but you could install [wicd]("http://wicd.sourceforge.net").  It's an alternative to Network Manager.

If you still can't get a wireless connection with wicd, then please post the output of:
```

iwconfig
lspci
ifconfig
```

so we can get a better idea of what's going on.

---

