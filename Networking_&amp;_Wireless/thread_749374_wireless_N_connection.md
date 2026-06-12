---
title: "wireless N connection?"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by ZeroHimself on 2008-04-08
does any one know how to get a 802.11n connection to work....
or least if any cards(or drivers) support it....

have an intel 4965AGN card, and i can't connect on 2.4ghz..(to much traffic.... constant disconnects)  ... The router is set to 802.11n on the 5ghz band.....

i can't find a way to configure the card for this(or even if it supports it...)

however, i know it works under(prepare yourself for the evil word) windows.....

so does any one know if *any* driver supports this and specifically if i can make it work with ndiswrapper as an alternative to my current driver?

---

### Post by dstew on 2008-04-08
Here's an example using a Windows driver with ndiswrapper: [http://ubuntuforums.org/showthread.php?t=471794](http://ubuntuforums.org/showthread.php?t=471794)

Check your lspci output to see if it is the same card. That thread is about two years old, so maybe some better drivers are available.

---

