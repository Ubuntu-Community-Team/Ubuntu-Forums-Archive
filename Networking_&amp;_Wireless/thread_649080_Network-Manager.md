---
title: "Network-Manager"
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by surferkid993 on 2007-12-24
I have a hp Pavilion ze4500 and I am trying to get the wireless internet to work on it, but I am having trouble installing Network-Manager

I downloaded the tar.gz file from the site extracted it and configured it.
I'm not sure what to put for distro, ubuntu does not work so I did debian.
the configuration works but when I type sudo make into the terminal I get this error:
```
nm-vpn-properties.c:59: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
nm-vpn-properties.c:60: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
nm-vpn-properties.c: In function ‘vpn_druid_vpn_validity_changed’:
nm-vpn-properties.c:258: error: ‘druid’ undeclared (first use in this function)
nm-vpn-properties.c:258: error: (Each undeclared identifier is reported only once
nm-vpn-properties.c:258: error: for each function it appears in.)
nm-vpn-properties.c: At top level:
nm-vpn-properties.c:266: error: expected ‘)’ before ‘*’ token
nm-vpn-properties.c:304: error: expected ‘)’ before ‘*’ token
nm-vpn-properties.c:321: error: expected ‘)’ before ‘*’ token
nm-vpn-properties.c:338: error: expected ‘)’ before ‘*’ token
nm-vpn-properties.c:357: error: expected ‘)’ before ‘*’ token
nm-vpn-properties.c:378: error: expected ‘)’ before ‘*’ token
nm-vpn-properties.c: In function ‘add_cb’:
nm-vpn-properties.c:423: error: ‘druid’ undeclared (first use in this function)
nm-vpn-properties.c: In function ‘import_settings’:
nm-vpn-properties.c:477: error: ‘druid’ undeclared (first use in this function)
nm-vpn-properties.c: In function ‘init_app’:
nm-vpn-properties.c:1061: error: ‘druid’ undeclared (first use in this function)
nm-vpn-properties.c:1062: error: ‘vpn_druid_cancel’ undeclared (first use in this function)
nm-vpn-properties.c:1063: error: ‘druid_confirm_page’ undeclared (first use in this function)
nm-vpn-properties.c:1066: error: ‘vpn_druid_vpn_type_page_next’ undeclared (first use in this function)
nm-vpn-properties.c:1068: error: ‘vpn_druid_vpn_details_page_prepare’ undeclared (first use in this function)
nm-vpn-properties.c:1069: error: ‘vpn_druid_vpn_details_page_next’ undeclared (first use in this function)
nm-vpn-properties.c:1071: error: ‘vpn_druid_vpn_confirm_page_prepare’ undeclared (first use in this function)
nm-vpn-properties.c:1072: error: ‘vpn_druid_vpn_confirm_page_finish’ undeclared (first use in this function)
make[3]: *** [nm_vpn_properties-nm-vpn-properties.o] Error 1
make[3]: Leaving directory `/tmp/NetworkManager-0.6.5/gnome/vpn-properties'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/tmp/NetworkManager-0.6.5/gnome'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tmp/NetworkManager-0.6.5'
make: *** [all] Error 2

```

---

### Post by HIGHLIFE on 2007-12-24
What version of ubuntu are you using?  Version 7.10 comes with network-manager installed.

---

### Post by surferkid993 on 2007-12-24
7.10, okay thanks then I'm back to square one with wireless internet not working,sigh,

---

