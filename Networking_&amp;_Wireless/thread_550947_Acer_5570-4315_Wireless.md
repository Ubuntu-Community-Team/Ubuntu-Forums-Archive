---
title: "Acer 5570-4315 Wireless"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by icehammer on 2007-09-14
I recently purchased a new Acer 5570-4315.. 
Wireless works fine here, no issues whatsoever - only when its an unsecured network..

Example:
1. For my coll wireless, i have the pass key and i enter it correctly as a WEP 64/128 Hex key.
2. It asks me that the Keyring Manager is trying to access something.. I can choose between Ok/ Deny.

Either way, it shows me that i'm connected to 'wwfc' (the network), and i see the properties to verify that i have  a ip address and a dns allotted, however, i can't connect to the net..

Why is that?

If i enter the passkey in windows, it just logs in.. I tried matching the settings in Vista and Ubuntu, but ubuntu only connects me to the network and not to the net.. How can i go around this issue.?

---

### Post by noob12 on 2007-09-16
After you seem to have connected with the wireless can you please save the output of these commands, and then post them when you can connect wired or from Windows.

```

ifconfig -a

route -n

cat /etc/resolv.conf

```

---

