---
title: "Wireless with Certificates"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by zazabar on 2008-07-14
Alright, so.  My school decided it would be cool and start using advanced wireless security procedures to secure the wireless networks.  Not a problem for Windows or Mac users, but a little more difficult for us Linux users.  I've been having trouble setting it up.

Information:

    *  Security Type: IEEE 802.1X Authentication
    * Access point authentication: WPA-2
    * Data Encryption: AES
    * EAP type: PEAP or TTLS
    * Authentication Protocol: MS-CHAP-V2
    * Validate server certificate: must be checked / enabled
    * Server certificate name must match: wireless.uncg.edu
    * Check Thawte Premium Server CA in the Trusted Root Certification Authorities list.

The main part that I am having trouble with is the server certificate.  Anyone have any ideas on how to go about this?

If it helps, they have step by step instructions on how to do it in Windows XP ( [http://its.uncg.edu/Projects/Wireless_Refresh/Configure/Other_XP/](http://its.uncg.edu/Projects/Wireless_Refresh/Configure/Other_XP/) ).

---

### Post by df6269 on 2008-07-14
Please try to use wpa_supplicant.
[http://www.thinkwiki.org/wiki/Wpa_supplicant](http://www.thinkwiki.org/wiki/Wpa_supplicant)

---

