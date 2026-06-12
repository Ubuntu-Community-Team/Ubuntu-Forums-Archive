---
title: "Ubuntu AWLH3026 Freezing woes"
date: 2007-09-26
forum: Networking &amp; Wireless
---

### Post by vergeh on 2007-09-26
I'm currently trying to get Ubuntu working on a donated computer in a non-profit organization, so my options are rather limited. First off, this office ONLY has a WEP wireless network accessible. I can;t go around connecting to a wired network to perform updates and installations, so this process has been rather arduous.

I'm running an i386 system, and the wireless card is an Airlink AWLH3026. However, it shows up as a RAlink RT2561/RT61 in lspci. Whenever I connect to the WEP using network-manager, I get an instant freeze. So, following the advice I found in other threads, I have done the following:

-Installed the new generic and i386 kernels
-Uninstalled network-manager and network-manager-gnome
-Connected via manual setup.

However, now the system seems to act sporadically. For a while, I'd get consistent running, but the wireless connection will occasionally flake out. The signal shows as connected and it's still sending and recieving packets, but there's no Internet connection. This was especially troublesome for large updates.

Then the crashes began. Now we're lucky to get 10 minutes of consistent running before the system completely locks up and needs to be hard reset. Sometimes it even locks up on boot. Removing the wireless card eliminates the freezing.

edit: I've tried to use ndiswrapper before, but for some reason the program gets testy if the hardware is already using a different driver. What would I need to do to remedy this?

Something tells me that the incorrectly-named wireless card is to blame. However, before I go on a hunt to install the new drivers (which means hooking up the card again), does anyone know if the cards are virtually interchangeable?

---

