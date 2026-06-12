---
title: "Trusty finds wifi network -- fails to connect"
date: 2014-05-11
forum: Networking &amp; Wireless
---

### Post by r_avital on 2014-05-11
I haven't seen this in all my searches here:

Laptop using Intel Wireless-N Card, running Saucy (64Bit) -- connects ok to my encrypted wifi network, so quickly that Saucy reports it is connected by the time lightdm shows the login screen on bootup.  Really fast.

SAME laptop, same hardware, clean install of Trusty LTS (64Bit):

The network manager applet finds, recognizes, and displays the network name.
Click on it to connect, I'm prompted for a password, I enter it, it goes through some gyrations, pops-up a screen asking for the password again.  It repeats that cycle, until I click cancel, then it displays an error, fails to connect.

Tested this with the live DVD after selecting "Try Ubuntu" -- Same behavior.  *With the live DVD, in "Try Ubuntu" mode.*

Plug in an external USB wifi adapter, and I make sure it's on wlan1 (since the built-in one is by default wlan0) -- happily connects.

There seems to be a specific problem with Trusty handling connections over the built-in wlan0 (again, in this case, Intel Wireless-N Card).  Similar to what used to happen with Atheros adapters in Jaunty/Karmic.

For the sake of testing further, I created a non-encripted, open network on my access point (Netgear ProSafe WG-102).  Same behavior.

Has anyone seen this?  If not, I'll report a bug.

---

### Post by kc1di on 2014-05-11
you may find[ this thread ]("http://ubuntuforums.org/showthread.php?t=2042332&highlight=11n_disable")is helpful.

seems there is a bug in n channel connections.  The thread is for 12.04 but have seen the same thing in 14.04 . good luck.

---

### Post by r_avital on 2014-05-11
Hi kc1di

It did not resolve the problem, but it's an extremely educational thread, thank you!

I'll report the bug.

---

