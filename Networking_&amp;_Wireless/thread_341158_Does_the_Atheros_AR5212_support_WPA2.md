---
title: "Does the Atheros AR5212 support WPA2?"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by cookfromfrozen on 2007-01-18
Hi
Not so much Ubuntu related but a question for those who have the Atheros AR5212 wireless chipset as shown by this lspci :

```

06:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```

Does this model support WPA2?

Thanks.

---

### Post by spd106 on 2007-01-18
If you mean does it support WPA-PSK with AES/CCMP? Then yes it does, or at least mine does. I can't vouch for WPA-EAP since I've not connected to an enterprise network. It should work fine.

You will need wpa_supplicant and Network Manager (optional). See [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

### Post by cookfromfrozen on 2007-01-18
Thanks.  I did mean WPA-AES with PSK, yes.  The acronym soup confuses me sometimes! :lol: Thanks again.

---

