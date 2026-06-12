---
title: "Roaming with wpa_supplicant not working"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by Haligonian on 2008-07-29
Hi folks,

I have kicked NetworkManager off my machine running Hardy, as it requires interaction with nm-applet or knetworkmanager to function, and I don't use either Gnome or KDE.  Then I went to setup roaming with wpa_supplicant, in order to automatically connect to my default networks at home and work.  Here's the weirdness.  If I run ifup -a or /etc/init.d/networking start manually from the shell, everything works like a charm.  During boot, however, the script claims to run and complete successfully, but it never starts wpa_supplicant on my wireless, and I consistently end up on my neighbor's network instead of mine (because his is open).

Next step: debugging.  I went to see what happens if I remove /etc/init.d/networking from all runlevels.  The script doesn't seem to run (at least its output is missing during boot).  However, my wireless network is still up when I login.  This begs the question: Where is the network brought up if I am not running the networking init script and no other script seems to call ifup -a or ifup eth1 (my wireless interface)?  This may be the core of the problem because ifup -a does not do anything on the wireless interface if it is already up.  (Even on the command line I have to run ifdown -a before running ifup -a to start my network properly.)

For now, I have a hack that works:  I removed auto eth1 from /etc/network/interfaces and then call ifup eth1 from /etc/rc.local.  It feels like an awful hack, though.  Any enlightenment as to how to craft a clean solution would be very much appreciated.

For reference, here are my relevant configuration files before I hacked them to bring up eth1 manually from /etc/rc.local:

*** /etc/network/interfaces ***
auto lo
iface lo inet loopback
auto eth1
iface eth1 inet manual
  wpa-driver wext
  wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
iface default inet dhcp

*** /etc/wpa_supplicant/wpa_supplicant.conf ***
ctrl_interface=/var/run/wpa_supplicant
ap_scan=1
network={
  ssid="MYSSID"
  key_mgmt=NONE
  wep_key0="MYKEY"
  wep_tx_keyidx=0
  auth_alg=SHARED
}

As a final comment probably more to the NetworkManager developers than to the Ubuntu community: NetworkManager is awesome but would be infinitely more so if it had a well-documented API that can be used to control it from other places than nm-applet (eg, from a simple Awesome (WM) widget).  The things that nm-applet does (I dug around in the source code), in order to make NetworkManager connect to a given network, are not documented in any API reference I could find online.  Once this is fixed, I may put NetworkManager back on my laptop.

---

### Post by jimv on 2008-07-30
You could give WICD a try.  It will do the WPA_Supplicant thing on it's own, and will only connect to networks that you check "Connect automatically" on.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by Haligonian on 2008-08-01
Thanks for the pointer.  I'll try it when I get a chance, even though, as I said, my current setup is working.  What I don't like is that it's a hack.  So the central question remains:  Where are my network interfaces brought up if I don't run /etc/init.d/networking?  This is the only thing that seems to prevent wpa_supplicant from working perfectly on startup.

---

