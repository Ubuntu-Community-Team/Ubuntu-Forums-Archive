---
title: "Atheros driver won't discover 'hidden' SSID networks"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by hamdodger on 2007-04-15
I've discovered that unless I have my SSID set for 'broadcast discover enabled" on my wireless access point, the Atheros driver under Feisty Fawn won't properly initialize and acquire a DHCP address.  Once the SSID is broadcast, the driver works effortlessly.

---

### Post by tturrisi on 2007-04-15
It should connect even if broadcast is disabled in the AP.
/etc/network/interfaces should look like this:
# My Wlan
iface ath0 inet dhcp
wireless-essid ssid-name-here
auto ath0

---

### Post by jimbob on 2007-04-17
I had this problem some time ago and never did solve it completely.  Are you using network-manager?  You might want to remove it and install Wicd instead.  It has a special gui for setting up and detecting non-broadcast SSID's.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Drew_Blood on 2007-04-24
Having the same issue, unfortunately. Works fine with a broadcasted SSID. Non-broadcasted it will see once entered, show me the strength, but will not connect. Have seen an identical issue on this network with another user in Feisty, not sure of chipset though. He went back to Edgy and was able to connect again.

Have not tried Wicd yet, will do so once I can get a connection.

---

### Post by rexey on 2007-04-27
Likewise for me too using Atheros and Intel IPW2200
Good to know it's not just me.  It worked fine on Edgy.

-Rexey

---

