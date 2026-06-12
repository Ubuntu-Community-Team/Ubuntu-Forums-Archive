---
title: "TrendNet Wireless USB adapter in and Mythbuntu"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by IceCap on 2008-05-24
I'm putting together a MythTV box using a P4 2.4GHz on a Intel motherboard.  I got a (cheap) TrendNet TEW-424UB/   A v3.1 802.11g adapter that is using a Realtek controller.  There are several (different) accounts of getting these to work with Ubuntu on the web but in my hands none of them worked (they all used versions 2.x or 3.0, not sure if that matters).  So here is a list of what I have tried (some combinations, but not all) based on what I found on the web (note I'm not a Linux expert but I can follow directions):

[LIST=1]
[*]Installed ndiswrapper and tried using the Windows drivers that came on the CD.  I also downloaded drivers from the TrendNet website as well as the Realtek website.  Drivers load fine (confirmed with 'ndiswrapper -l').  But no go.  I see my wireless network and it tries to acquire an IP address but looks like it gives up.  I'm using hexadecimal WEP for security.
[*]Blacklisted the built-in Realtek drivers.
[*]Installed wicd instead of the Network Manager.  Same thing.  Sees the network and tried to acquire a network address but looks like it fails.
[*]Tried connecting to the wireless network through the command line using 'sudo iwconfig wlan0 essid <essid> ap <xx:xx:xx:xx:xx:> key <XXX>'.  No error messages when this was run but when I then ran 'sudo dhclient wlan0' I got some errors (which I have forgotten now).
[/LIST]
  I know my network is fine, I have two laptops connecting to it that are running linux.  One is using ndiswrapper (ubuntu) the other one is using I believe built-in drivers (xubuntu).  I do remember that getting ndiswrapper was a bit of a pain but it worked using directions I found on the internet (different driver though).  I also should note that I can activate a wired connection on the MythTV box while I'm getting this to work.
  So if someone could troubleshoot this with me I would really appreciate it.

  Thanks

  IC

---

