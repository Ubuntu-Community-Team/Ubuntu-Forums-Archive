---
title: "Network Manager not showing interfaces (WPA for Intel 2915)"
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by pix0r on 2006-09-18
I just upgraded from 5.10 to 6.06 (changed sources.lst and did dist-upgraded), and I'm trying to get my wifi card (Intel 2915) working with WPA encryption.  On 5.10, I was using wpa_supplicant and that was fine.. just had to run a script to start it up every time I connected to my home router.  That doesn't work any longer, but I read that WPA support is included in NetworkManager.  So I installed network-manager-gnome package which went fine.. now a network icon shows up in my toolbar, but it doesn't show any connections.  The tooltip says "No network connection".  When I left-click on the icon, it says "No network devices have been found".  When I right-click, the options I have are: Enable Networking (checked), Connection Information (grayed out), About, Remove.  Don't see anywhere I can add a connection.  I have eth0 (10/100/1000? NIC, dhcp automatically enabled and working) and eth1 (wireless Intel 2915 a/b/g card).

Perhaps there is some software/driver conflict I'm running into here?  Any help would be great.

Thanks!
Mike

---

### Post by sjieke on 2006-09-19
Hello,

For network manager to work you must make sure that the nics you want to be handled by network manager are commented out in /etc/network/interfaces, it should look something like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
# auto eth1

# iface eth1 inet dhcp

```

Also look at the wiki: [https://help.ubuntu.com/community/WifiDocs/NetworkManager]("https://help.ubuntu.com/community/WifiDocs/NetworkManager")

Hope this helps...

---

### Post by pix0r on 2006-09-19
Ahh, comment them out, I see.  Yep, that's where I went wrong.  Someone had told me to edit /ect/network/interfaces and I was confused because everything shows up there as I'd expected it.  I'll try this at home, thanks!

---

