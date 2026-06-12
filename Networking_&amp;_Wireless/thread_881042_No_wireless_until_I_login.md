---
title: "No wireless until I login?"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by colskinet on 2008-08-05
Hi all

I am running Ubuntu 8.04 LTS and using only wireless for networking.

I have discovered that I have to login to the system before my network is found and connected to.

I'd have thought that it would automatically connect in the background, logged in or not?  How do I go about doing this?  I am using wlan0 and can copy up any conf files needed..

Thanks in advance!

Colin

---

### Post by wdaniels on 2008-08-05
> **colskinet said:**
> I have discovered that I have to login to the system before my network is found and connected to.

I'm assuming you mean that you have to login to the Gnome desktop, in which case your wireless is probably set up in "roaming" mode so that nm-applet (that's the little network management icon you see in the panel) would handle choosing and connecting to the network based on your profile when you start the Gnome session. If this is the case, go to System->Administration->Network and change the configuration of the wireless interface to disable roaming mode and enter the relevant details for connecting to your network directly in there.

---

### Post by colskinet on 2008-08-05
> **wdaniels said:**
> I'm assuming you mean that you have to login to the Gnome desktop, in which case your wireless is probably set up in "roaming" mode so that nm-applet (that's the little network management icon you see in the panel) would handle choosing and connecting to the network based on your profile when you start the Gnome session. If this is the case, go to System->Administration->Network and change the configuration of the wireless interface to disable roaming mode and enter the relevant details for connecting to your network directly in there.

That done the trick!  Thanks for the prompt reply.

Colin

---

