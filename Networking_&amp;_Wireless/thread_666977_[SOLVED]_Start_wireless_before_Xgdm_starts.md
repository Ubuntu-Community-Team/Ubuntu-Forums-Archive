---
title: "[SOLVED] Start wireless before X/gdm starts"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by sceo on 2008-01-13
I want to get x11vnc working to the point where I could even reboot then connect to a gdm session to log in.  I actually think all that is already there.

The only problem I'm running into is that my wireless network doesn't connect until after I've logged into my session (because that's when network-manager starts).

How can I connect to my WPA wireless network BEFORE X or GDM starts?

---

### Post by sqrt2 on 2008-01-13
You can configure your wireless interface in /etc/network/interfaces. (The actual configuration depends on what kind of encryption you're using etc.) OTOH, this probably breaks network-manager, so you'll have to decide for one of those.

---

### Post by sceo on 2008-01-13
Thanks for the quick reply.  This is a desktop computer so it only ever needs one single network config.  I am more than happy to deal without network-manager.  Is there a Gutsy howto for /etc/network/interfaces + WPA?

---

### Post by sqrt2 on 2008-01-13
Run
[indent]wpa_passphrase "<your network SSID (name)>"[/indent]
in a terminal and enter your password. Assuming you get your network configuration via DHCP, add something like this to /etc/network/interfaces:
[indent]auto eth1
iface eth1 inet dhcp
wpa-ssid "<your network SSID>"
wpa-psk <paste psk string from wpa_passphrase output here>[/indent]
You may have to replace eth1 with the name of your wireless interface (could also be wifi0, ath0 or something completely different).

---

### Post by sceo on 2008-01-14
I had more luck with the wpa-passphrase directive.  However, it won't start correctly/automatically at bootup for some reason.  When I open a terminal and "sudo ifup eth0" it tells me it's already configured.  So I do a sudo ifdown eth0, THEN a sudo ifup eth0 and it works and gets a DHCP packet and everything is fine.  So why can't it do it right itself I wonder...

---

### Post by sceo on 2008-01-14
Solved using pre-up sleep 20 in /etc/network/interfaces.
[http://ubuntuforums.org/showthread.php?t=667429](http://ubuntuforums.org/showthread.php?t=667429)

---

