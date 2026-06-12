---
title: "Solved: Realtek 8180 WLAN configuration"
date: 2005-04-13
forum: Networking &amp; Wireless
---

### Post by g-joey on 2005-04-13
Hi,

until yesterday I couldn't get my "Digitus DN-7006" WLAN card with its Realtek 8180 chip to work: Although I had followed the several hints in this and other forums, it just didn't find my access point. I almost wanted to give up and buy another card, but then I finally discovered **the advice[tm]**:

For some unknown reason, the graphical WLAN tools seem to save the configuration somewhere where it is not read at startup. So, to provide all needed information, I had to add these lines to the file /etc/network/interfaces:

```

auto wlan0
iface wlan0 inet static
        address 192.168.1.111
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        wireless_mode managed
        wireless_essid my_access_point
        wireless_key 0123456789abcdef0123456789

```

After having done that, the WLAN connection worked. Maybe this information can help others, too, so I put it into the forum.

The only thing I still want to try is to delete the card completely and start again from scratch, but without using the graphical configuration tools...

Greetings, Joe

---

### Post by Shambler on 2005-06-05
Well, I tried that, but an "ifconfig" didn't give me the desired results. Does it need a special module to be loaded?

---

### Post by az on 2005-06-05
This is not correct.

The networking tool does just that -  write entried into /etc/networking.

To get the realtek working, you need ndiswrapper since there is no linux driver.

look up ndiswrapper.
[http://test.wiki.ubuntu.com/forum/hardware](http://test.wiki.ubuntu.com/forum/hardware)

---

