---
title: "boot order bluetooth &lt;-&gt; dbus"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by einalex on 2006-11-05
Hi there!
Is it just me or shouldn't bluetooth be started after dbus at boot?
Since bluetooth is reliant on dbus because of the new pin handling.

On my system bluetooth isn't started correctly the 'normal' way (bluetooth before dbus). I have to bring up hci0 per hand if I want to use it.

I just changed the start order (changing S25bluetooth to S51bluetooth in /etc/rc2.d) (dbus being S50dbus)

Now it works properly with bluetooth working without me restarting the service per hand.

---

