---
title: "Intermittent wireless with DHCP (OK with static IP)"
date: 2005-04-23
forum: Networking &amp; Wireless
---

### Post by emendelson on 2005-04-23
APOLOGIES TO ALL: This belongs in the Hoary forum,not here. If I could figure out how to delete it, I would...

-------------------------------------------------------------------------


Here is a baffling problem that I hope someone can help with.

I've installed 5.04 on a Thinkpad T42 with Atheros a/b/g wireless. Except for the one problem I've described here, everything works perfectly out of the box.

Here's the problem:

If I enter a static IP address (plus wep key, gateway, and netmask) in /etc/network/interfaces, then wireless networking works extremely well. The network notification applet icon on the panel at the top (near the clock) shows a steady, strong signal.

However, if I use the Gnome network settings application (Gnome menu: System/Admistration/Networking) to choose between different ESSIDs from the dropdown list in the Configure dialog, and I use DHCP, then the network notificaition icon shows a yellow caution sign ("!" in a triangle) every three seconds (more or less), and the connection is very intermittent.

I've tried using two alternative wireless managers, wicme and gtkwifi, but the same problem occurs with both. I wish I could use gtkwifi, because it is by far the best and fullest-featured network manager I've seen yet for Linux, but it seems to suffer from the same problem.

This doesn't seem to be a wicme or gtkwifi problem, because they have the same problem that the standard Gnome applet has if I use DHCP. Has anyone encountered the same problem, or can anyone suggest a solution?

Many thanks for any help.

---

