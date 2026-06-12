---
title: "Bluetooth PAN support for w300i or w600i?"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by MarkSwanson on 2007-12-06
Hello,

I'm using Ubuntu 7.10 and have bluetooth working fine - PAN also seems to configure fine and I have a bnep0 device, but my phone still uses GPRS. It's weird that my phone supports PAN, and it configures fine, but I can't find a way to tell the phone to use the Bluetooth data comm so the phone connects to the Internet through my laptop.

My Connectivity -> Data Comm. page has a 'Close Connection' option - which is only available when I establish a PAN link. So I think the link is up. I can ping the bnep0 device fine.

I _think_ the phone is acting like the router so my laptop can access the Internet through the phone.  When my laptop connects my phone says, "your device wants to use your phone as a modem. allow? yes/no". 

What I really want is for my phone to access the Internet through my laptop. Do some phones support PAN but not in the direction I want? I suspect that may be the case as all of the howto guides state you need to config the phone to use the bluetooth network, but no option exists on my w600 or w300.

If anyone has any thoughts on this please post. I'd really like to get this working so I don't have to pay data charges to the cell phone company.

Cheers.

---

### Post by MarkSwanson on 2007-12-06
Ahhh, after much searching I think I realize what the problem is. None of the howtos explain what the prerequisite is to make this work. The w300i and w600i phones support Bluetooth NAP, which means the cell phone will only act as a router. This is not what I want at all.

Since I don't have access to any other cell phones atm I can only guess that what a cell phone really needs is the bluetooth PANU service. The LAN service looks promising but it's not mentioned in any of the HOWTOs so I don't know what it's for. Maybe wifi?


Unfortunately I could not find docs anywhere that stated what phones came with what bluetooth services. If anyone has such a link (s?) please post. I'd like to be able to know ahead of time if a phone I'm going to buy can do this or not.

Thank you.

---

### Post by MarkSwanson on 2007-12-06
Well, I did find some Symbian docs:
[http://www.symbian.com/developer/techlib/v9.2docs/doc_source/guide/Bluetooth-subsystem-guide/Bluetooth/ShortLinkServices/ShortLink/BluetoothProfiles/BluetoothPAN/BTPANProfileOverview.html#_top](http://www.symbian.com/developer/techlib/v9.2docs/doc_source/guide/Bluetooth-subsystem-guide/Bluetooth/ShortLinkServices/ShortLink/BluetoothProfiles/BluetoothPAN/BTPANProfileOverview.html#_top)

Which basically states that Symbian OS 9.2 supports PANU.
If anyone has any links for SE or other devices please post.

Cheers.

---

