---
title: "WNA3100 NetGear WiFi USB Adapter 100% WORKS!!"
date: 2015-02-16
forum: Networking &amp; Wireless
---

### Post by chris216 on 2015-02-16
Hello,

My name is Chris, I am posting this for anyone having
issues with a NetGear WiFi USB Adapter, Or possibly any
WiFi connection issue.
I have done a lot of searching all over looking for a way
to get this model to work with my computer and the Ubuntu
OS. Tryed awhile ago with no success. Re-visited this issue 
recently and discoved that a lot of people have the same
issue where they try to connect and it keeps asking for a
password of network key. After Several trial and error I 
discovered that the Issue was with the Security Settings of
my modem/WiFi Router (which currently is also of NetGear).

Model No. : WNA3100
Driver       : bcmn43xx64.inf

This was loaded with ndiswrapper listed as wlan0

System Info                 : Ubuntu 14.04 LTS Desktop 64-bit AMD
Wireless Security Type : WPA
Authentication method  : Personal (Pre-Shared Key)
Data Encryption           : TKIP  <----[ This Part Is Critical ]

For some reason the way Ubuntu reads the Security of a
WiFi conflicts when it is set to AES. But when I set it to
TKIP, some how Ubuntu was able to commuicate with the
Router resulting in the WiFi connecting through the Adapter.
I hope this helps any who may still be having an issue getting
connected. I am still new to Ubuntu and trying to learn what I 
can in hopes of heling others.

---

