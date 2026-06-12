---
title: "How to delay autostart of Firestarter"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by fade2gray on 2008-06-18
I followed the guide [[COLOR="Blue"]_here_[/COLOR]]("http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html") to have Firestarter automatically run at startup without the need to enter a password. This works fine except that I get a warning - "Failed to start the firewall / The device wlan0 is not ready etc etc", but I can see that Firestarter is running running and working behind the warning dialog and I can just "OK" out of it without a problem.

[LIST=1]
[*]Would it be possible to delay the startup of Firestarter to give wlan0 the chance to finish firing up first?
[*]Failing that, could I have the warning dialog automatically closed?
[*]Could Firestarter be made to start minimized to the tray?
[/LIST]
I'm assuming that some of the above could be achieved by scripts - any advice in that area?

Thanks.

---

### Post by prshah on 2008-06-18
> **fade2gray said:**
> Firestarter automatically run at startup without the need to enter a password.


Just a point to note: you don't need to have firestarter running all the time; it's just a front end to a _real_ firewall called iptables. It's useful when you want to add or change port settings, but, once applied, it matters not whether it's running or not.

---

