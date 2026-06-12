---
title: "Network Manager Applet 0.6.3 Problem"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by Graham1 on 2007-01-11
Hi Guys

Please help :-?. I have a wireless connection via wpa which is working fine but having installed the network manager applet 0.6.3, connection information is greyed out. Enabled networking is enabled and checked but how do I activate connection information?

:)

---

### Post by Graham1 on 2007-01-12
Bump.

:)

---

### Post by spd106 on 2007-01-12
Are you using network manager to control you network?

If not then right-click the panel and add Network Monitor

---

### Post by Graham1 on 2007-01-12
Currently using Network Monitor but would like to use Network Manager (to keeps things standard with openSUSE and Fedora Core 6). Network Manager in openSUSE and FC6 recognizes my card (ipw2200) but Ubuntu doesn't :(. Not sure if this is a problem with Network Manager or Ubuntu? I'm hoping Network Manager will makes things easier when using WPA.

:)

---

### Post by Graham1 on 2007-01-12
Finally managed to get "Enable Wireless" to appear on Network Manager. Found the answer here:-

[http://ubuntuforums.org/showthread.php?t=282256&highlight=enable+wireless+-showing](http://ubuntuforums.org/showthread.php?t=282256&highlight=enable+wireless+-showing)

However, I haven't been able to connect to my AP yet :(. I get a green light on one of the dots but that's as far as I get. Any ideas?

:)

---

### Post by Graham1 on 2007-01-12
This is tough (for me anyway). Still no joy in connecting to my AP :(. Something I've noticed is that no IP (or other details) are being displayed in Connection Information (I'm using a static IP). Does anyone know where Network Manager stores this information? For testing, can an IP address be set from the terminal?

:)

---

### Post by spd106 on 2007-01-14
I don't think you can do static addresses with network manager. If you want wpa if think you are going to have to use wpa_supplicant and the network-admin/network monitor duo to manage the link. Also check out the /etc/network/interfaces file.

---

### Post by kilps on 2007-01-14
I have always fixed most of my nm problems by opening /etc/network/interfaces and commenting out (with a #) everything except for:

```
auto lo
iface lo inet loopback
```

It is possible that your problem is more complicated than that - but from what I understand this allows nm to control your connections 

hope that helps ...

---

### Post by Graham1 on 2007-01-15
Thanks for the replies guys :). I have already tried commenting out the lines which got Network Manager working to some extent. However, it never fully connects (only shows one green light). Not sure what else to do :???:. Network Manager works in both openSUSE 10.2 and FC6 with a static IP so maybe it is a problem with Ubuntu. Should Connection Info show my static IP?

:)

---

