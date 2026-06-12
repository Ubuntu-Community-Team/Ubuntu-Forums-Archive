---
title: "Configure netplan for wakeonwlan"
date: 2022-03-28
forum: Networking &amp; Wireless
---

### Post by kozimodo2 on 2022-03-28
Hi,

Can anyone help me figure out how to configure wakeonwlan using netplan?  The [reference page]("https://netplan.io/reference/") says that it takes a sequence of scalars but with no clear indication of what are reasonable values for said sequence.  It does provide a list of string values (any, disconnect, magic_pkt, gtk_rekey_failure, eap_identity_req, four_way_handshake, rfkill_release or tcp).  My sample config is:

```
network:
  version: 2
  wifis:
    wlp1s0:
      access-points:
        SSID:
          password: passphrase
      dhcp4: true
      wakeonwlan: any
```

but this does not work.  What am I doing wrong here?

---

### Post by Tadaen_Sylvermane on 2022-03-29
I've never had to do anything with Netplan for that personally. Just make sure it's properly enabled in the bios / efi. There may be multiple settings to fully enable it.

---

