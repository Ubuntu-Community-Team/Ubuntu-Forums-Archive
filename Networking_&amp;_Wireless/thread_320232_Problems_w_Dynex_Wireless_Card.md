---
title: "Problems w/ Dynex Wireless Card"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by LostHusky on 2006-12-17
Hi there.  I just put Dapper on an old Dell P3, stuck in a Dynex "Enhanced G" PCI wireless card (model #: DX-WGPDTC) and am having some problems getting it to work...at all.

Out of the box, iwconfig produces this:
__________________

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
___________________

Which I'm assuming means that the system recognizes the card but doesn't know what to do with it.

The built-in networking config tool lets me activate the card, but nothing happens.  The light on the card isn't even on.,, (yeah I checked the connection)

I got ndiswrapper and stuck the Windows drivers into it.  ndisgtk says that the driver is loaded and the hardware for it has been found...but nothing changed, even in iwconfig.

Next I downloaded Network Manager, which doesn't recognize the wireless interface at all.

Any ideas?

Hope you all are enjoying your holidays!

-Kris

---

### Post by im_uptight on 2007-02-28
I've had the same problem with my DX-WGPDTC. Any help would be appreciated. Also, does anyone know if this adapter supports monitor mode or the PEEK protocol?

---

