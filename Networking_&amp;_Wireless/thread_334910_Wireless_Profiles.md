---
title: "Wireless Profiles"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by Graham1 on 2007-01-09
Hi All

First post here so please be kind :). Just installed Ubuntu and I would like to be able to switch between two networks. 

1. Static IP using WPA
2. DHCP using WEP

I have managed to connect to both but only if I edit "interfaces" within etc/network. Is there a utility that can switch between the two without having to make the manual changes each time?

:)

---

### Post by Graham1 on 2007-01-10
Bump ;). Anyone got any ideas? :-k 

:)

---

### Post by jml on 2007-01-10
The Networking Application that is loaded as a default does not handle multiple profiles well.  I would recommend that you download and install network-manager and network-manager-gnome.  These applets handle multiple profiles better than the net-app that comes standard.  Also, I recommend using Ubuntu 6.10.  It handles wireless better than earlier versions of Ubuntu.  Once installed, reboot the system.  There should be at least one network icon in the right upper corner of your screen.  You access the applet by right clicking and Left clicking on the icon.  Its not perfect, and these two applets are not very well documented, but the setup does work.  I have also heard that static IP addresses can be a problem.So if you try this and it doesn't work with the profile using a static IP address, try using a dynamic IP address (DHCP.)  Good luck.

Joe

---

### Post by Graham1 on 2007-01-10
Thanks for your reply Joe :). I'll download and install these two and see how it's goes. Unfortunately, I will need to stick with the static and dhcp ip's but who knows, I might hit lucky. I've also downloaded network selector but haven't been able to test with the static ip yet. I'll let you know how I get on later on.

:)

---

### Post by Graham1 on 2007-01-10
No joy I'm afraid :(. Installed both networkmanager packages but networkmanager applet 0.6.3 didn't want to play ball (connection info greyed out). Nevermind, I have added the required settings for both connections within "interfaces", commenting out the inactive connection.

:)

---

