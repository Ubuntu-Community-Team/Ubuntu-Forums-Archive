---
title: "NetworkManager on Hardy just doesn't flip back to automatic mode"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by amos.shapira on 2008-05-12
System: Ubuntu Hardy Heron (8.04) on Sony Vaio PCG-7K1L.

NetworkManager worked for a few months for me in three different wireless networks until a couple of days ago I tried to force it to connect to a WiFi network where the SSID was given to me in Hex.

In a few attempts to force it to accept the key I ended up with it being broken and not working at all - not even with the networks which used to work flawlessly until now.

What I see now is:
1. The icon for nm-applet shows the two terminals without any emblem on top of them, as if a wired network is connected.
2. Left-mouse click on the icon gives a menu with:
  * "Wired Network" (grayed out and unchecked)
  * "VPN Connections" sub menu
  * "Manual Configuration..."
  Choosing "Manual Configuration" brings up the "Network Settings" box where all the interfaces (Wireless, Wired, Point to Point) are marked with "-" in the box next to them and the wireless and wired interfaces are in "Enabled roaming mode". Trying to switch them between roaming and non-roaming doesn't help (and as far as I'm aware I should keep them in "Roaming" - all networks are DHCP-enabled).

3. Clicking on the right mouse button on the nm-applet icon brings up a menu with:
 * Enable Networking (checked)
 "i Connection Information" (grayed out)
 * Edit Wireless Networks which brings up the "Wireless Networks" window with the right info about the networks which used to work.

The right-mouse button menu used to list the identified wireless networks (with the right one already automatically picked up and connected to) but not any more.

How can I get back the old behavior, somehow reset network manager?

Thanks.

Amos

---

### Post by ozelot on 2008-06-16
my post might help you:
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?p=5197358#post5197358[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5197358#post5197358")

meaning = dont let this incomplete piece of software (network-admin) get you mad. write a couple of config files and some scripts to set the actual "profile" with a doubleclick.

regards,
oz

---

### Post by amos.shapira on 2008-06-16
Thanks. I ended up removing everything in /etc/network/services except for the two loopback lines and NetworkManager started working right away.

I agree that there is a huge lack of documentation for it but it also adds a lot of convenience especially on a roaming laptop.

---

### Post by ozelot on 2008-06-17
I agree for the default user it is convenient. But as soon as you want to configure something with 2 or more "profiles" it gets really annoying. Esp. for those useres who's router doesnt like to be used as a dns server (like my netgear fvs124g).
_There was some other similar software mentioned on the forum, that is working flawless:_
[[COLOR="Blue"]http://www.wicd.net/screenshot.php[/COLOR]]("http://www.wicd.net/screenshot.php")
_from this thread:_
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=763801&highlight=network-manager+alternative[/COLOR]]("http://ubuntuforums.org/showthread.php?t=763801&highlight=network-").
Havent tested it so far though.

---

