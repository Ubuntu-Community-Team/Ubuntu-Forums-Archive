---
title: "Non-broadcasted ESSID - WPA issues"
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by mattalves on 2006-12-02
Heypa all,

I've been wondering if connecting to WPA networks (which is already a pain in the a**) becomes impossible if the ESSID isn't broadcasted. Tried that, and no success... seems like wpasupplicant won't work properly or something like that. Anyone having the same issues?

Cheers!

---

### Post by wieman01 on 2006-12-03
Oh, it's possible. Please try out this thread:

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

If you need help, let us know.

---

### Post by mattalves on 2006-12-03
Still no use... I'm able to connect, but no DHCP response. It works fine under Win XP Home, tho.

cheers and thanks,

mat

---

### Post by wieman01 on 2006-12-04
What script have you used ("/etc/network/interfaces")? Please also tell me more about your network device & chipset. Is ESSID broadcast turned on? What kind of encryption do you need (e.g. TKIP, AES)?

---

### Post by mattalves on 2006-12-05
Exactly /etc/network/interfaces. The network device is an Atheros AR5005G (on my Acer 3502wlci laptop), and the encryption is TKIP. I also tried meddling with the wpasupplicant configuration, but still no use.

It's actually connecting to the network, but I get no DHCP response... And everything works fine under Windows XP.

---

### Post by wieman01 on 2006-12-05
Can you post your "/etc/network/interfaces"? Let's take a look at it first. And make sure NetworkManager or Wifi-Radar are uninstalled & do not run in the background.

---

### Post by mattalves on 2006-12-11
Well, I gave up on it - too much trouble just for the sake of having a network with a hidden name at home isnt worth it...

In Dapper, everything is working just fine with NetworkManager, including WPA keys and such. 

And thanks a bunch for your help! :)

---

