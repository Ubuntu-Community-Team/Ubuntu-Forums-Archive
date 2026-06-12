---
title: "Compaq multiport wireless lan"
date: 2006-12-31
forum: Networking &amp; Wireless
---

### Post by penorwood on 2006-12-31
I think that Ubuntu is very close to working with this card ... but not quite there and I am hoping I can get some help ...I have used ndisgtk to load the same inf driver that works in Windows XP and am told that the device is found ... however the terminal window tells me "FATAL" Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper.ko)".

This is the kind of card that installs to the front of the case and I have to press Fn+F2 to turn it on and off. I have confirmed this works as it alternately shows the card in device manager present or not present when I press Fn+F2.

dmesg tells me "ndiswrapper (wrapper_init:129)" loadndiswrapper failed (32512); check system log for messages from 'ndiswrapper'" and "ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed"

The card shows up in device manager as 801.11b [orinoco] if this is any help.

Thanks in advance!

Paul

Forgot to mention this is the W100 Multiport card from Compaq if it makes any difference ... I am fairly sure it uses a Prism2? chip.

---

### Post by robsonthejob on 2008-02-04
> **penorwood said:**
> I think that Ubuntu is very close to working with this card ... but not quite there and I am hoping I can get some help ...I have used ndisgtk to load the same inf driver that works in Windows XP and am told that the device is found ... however the terminal window tells me "FATAL" Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper.ko)".

This is the kind of card that installs to the front of the case and I have to press Fn+F2 to turn it on and off. I have confirmed this works as it alternately shows the card in device manager present or not present when I press Fn+F2.

dmesg tells me "ndiswrapper (wrapper_init:129)" loadndiswrapper failed (32512); check system log for messages from 'ndiswrapper'" and "ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed"

The card shows up in device manager as 801.11b [orinoco] if this is any help.

Thanks in advance!

Paul

Forgot to mention this is the W100 Multiport card from Compaq if it makes any difference ... I am fairly sure it uses a Prism2? chip.



Hi - Did you ever get this working. I have a compaq N1015v with this card and it wont play ball either. Decided to got for Ubuntu because it works a treat on my big pc and windows was trashed and wouldnt boot anymore. Ubuntu works but is slow and the wireless dosnt work. Cheers.

---

### Post by Avsfan on 2008-03-03
I have the exact same problem.  I just installed Ubuntu on my old N610C with a wireless LAN multiport.  If anyone has the fix to this problem, it would be greatly appreciated

---

