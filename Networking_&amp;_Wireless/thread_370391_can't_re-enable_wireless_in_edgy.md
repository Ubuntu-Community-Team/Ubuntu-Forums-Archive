---
title: "can't re-enable wireless in edgy"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by playmesumch00ns on 2007-02-25
I had my wireless working absolutely fine. Then I temporarily disabled it by unchecking the "Enable this connection" checkbox in the networking configuration dialog. 

However, when I tried to re-enable the connection by re-checking the box, it doesn't work. The little networking icon in the taskbar still has a warning sign on it to show that the connection isn't working, and firefox cannot connect to the internet.

Any advise would be greatly appreciated.

pmsc

---

### Post by gradedcheese on 2007-02-25
One thing that could have happened is that, somehow, the wireless interface got added back into /etc/network/interfaces -- check that file and make sure it's commented out in there (a comment starts with a '#').  I'm not 100% sure about what you have to restart in order to force NetworkManager to reload things, perhaps dbus?  As such, you could try and reboot for now.

---

### Post by playmesumch00ns on 2007-02-26
how would being in /etc/network/interfaces stop it? Is it kinda like the restricted modules list, or is something else going on?

By NetworkManager do you mean the default configuration dialogs, or the nm-applet? (as I don't have the latter installed)

---

### Post by playmesumch00ns on 2007-02-27
OK, tried taking my wireless info out pof /etc/network/interfaces. This was enough to get the 'signal strength' meter going again. But then configuring and selecting 'enable' then inputting essid and wep key still does not get me a connection. What's more 'signal strength' drops to 0 once i've done this... odd :(

---

