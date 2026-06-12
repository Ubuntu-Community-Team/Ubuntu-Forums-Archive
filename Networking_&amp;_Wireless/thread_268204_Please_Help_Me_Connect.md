---
title: "Please Help Me Connect"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by coolbian57 on 2006-09-29
Ok, so I've got a Hawking HUG1 USB Wireless Adapter.  Everything is working fine, in fact, i didn't even have to use NDISWrapper for it.  

But i have one embarresing a problem.

How do i actually connect to my internet after i have all my settings set up and everything.

It also may be possible that my connection does not reach far enough; my wireless router is about 40 feet away, and the signals are coming from a small USB adapter that is hidden behind a drawer.

---

### Post by wieman01 on 2006-09-29
There is a networking applet in Gnome (under Administration?)... You can try that to set up your network (I am using KDE, so I can tell you where it is exactly). 

Do you know your wireless adapters alias by chance (e.g. eth1, eth2, ath0)?

As for the signal strength of your network/router/card try to run this command from a terminal windows and post the output:
> sudo [COLOR="Red"]your_wireless_alias[/COLOR] scan
This command tells you more about the reception and signal quality.

---

### Post by coolbian57 on 2006-09-29
I already hve everything set up correctly.  I have the DHCP set up, and i have an automatic DNS lookup...

---

