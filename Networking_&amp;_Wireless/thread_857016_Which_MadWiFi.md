---
title: "Which MadWiFi?"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by TrikeKid on 2008-07-12
Hey, I just installed ubuntu on my Acer Aspire 5570Z, everything works out of the box except my wireless of course. In my searching I've found I need to download madwifi, but when when I search madwifi in synaptic, I end up with a ton of search results. They all seem to be variants of "restricted linux modules for x86, Xen, OpenVZ, or 386. Which one do I use for a standard install of Ubuntu Hardy?

---

### Post by kevmitch on 2008-07-12
If you type 

```
uname -r
```

in a terminal, it will give you the currently running kernel version.

You want the corresponding linux-restricted-modules package.

---

### Post by TrikeKid on 2008-07-12
Ok, I installed the correct one, now how do I get it to see the wireless network?

---

### Post by ibuclaw on 2008-07-12
To see all active wireless devices
```
iwconfig
```
To scan for all active wireless networks from within your scanning range
```
iwlist scan
```

Although the gnome-network applet in the top right hand of your menu should help to do this for you and get you connected up.

Regards
Iain

---

