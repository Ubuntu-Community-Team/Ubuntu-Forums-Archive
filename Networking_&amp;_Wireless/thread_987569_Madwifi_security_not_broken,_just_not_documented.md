---
title: "Madwifi security not broken, just not documented"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by Chuckels550 on 2008-11-19
When I upgraded to Mythbuntu 8.10, my Atheros wireless NIC would connect, but the encryption failed to work.  I have discovered that the support for madwifi in wpasupplicant was not included in latest kernal build because wext already provided the same support.  Good reason, just not published.

If you are using madwifi drivers and cannot get the encryption to work, try using wext instead of madwifi when setting up wpasupplicant settings.  I did and my connection works as it should with WPA2 PSK (AES) encryption.  I am using wicd instead of the infamous network manager.

---

