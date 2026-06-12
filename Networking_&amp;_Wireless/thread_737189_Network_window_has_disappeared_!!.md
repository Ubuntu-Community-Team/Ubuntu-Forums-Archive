---
title: "Network window has disappeared !!"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by smallzoo on 2008-03-27
I have just installed XBuntu on my tecra laptop. Everything went smoothly. I put my pen drive in and it recognised it straight away.. so I plugged my D-Link wireless car in the PCMCIA socket and it lit up..

Great I thought. went into Applications/System/Network.. after entering admin password it showed the wireless connection and I set it up as WPA. It saw my wireless network so again I was happy !

I tried Google and it still did not find a web page so I tried to go back into Applications/System/Network.

The cursor shows the timer but the networking window does NOT open !!!.. It only opens if I take the wireless card out..

HELP.. everything has worked so well so far there must be a reason 

Peter

---

### Post by adityakavoor on 2008-03-27
```
 sudo network-admin
```

---

### Post by smallzoo on 2008-03-27
Tried that but get nothing on the terminal window

e.g. when I type ls <ENTER> cat /etc/network/interfaces I get :-

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wpa-driver wext
wpa-key-mgmt wpa-psk
wpa-proto wpa2
wpa-ssid GEN-Wireless

auto wlan0

BUT
when I type  sudo network-admin <ENTER>
the cursor goes to the next row and then just sits there

---

### Post by smallzoo on 2008-03-27
I get the Network window when I remove the wireless network card.

How can I edit the interfaces file and remove the current entries

When I edit the file and try to save it I get the message 'cant open file to write' ?

---

### Post by smallzoo on 2008-03-27
Thanks for everyone's help..

I used sudo mousepad to remove all entries in the interfaces file and then added the wireless card again.

Thanks

---

