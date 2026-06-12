---
title: "dwl-g650 (c2) not connecting with WEP encryption"
date: 2005-06-09
forum: Networking &amp; Wireless
---

### Post by inmate on 2005-06-09
hi all,

i am trying to get my DWL-G650 (c2 - atheros) wifi card to connect to my router (DI-624) with WEP enabled, but it flat out refuses.
if i open the router (ie. switch off wep), then the connection works sterling, so the card/dhcp/etc. all definately works - its just a wep problem.

i have googled a fair bit on this and it seems that other peoples experiences vary greatly. some say that it works ["out of the box"](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards), and others suggest that i should use [madwifi](http://madwifi.sourceforge.net/dokuwiki/doku.php?id=compatibility_list) , and yet others talk of [ndiswrappers](http://madwifiwiki.thewebhost.de/wiki/DLinkDWLG650) ...

i'm really not sure which way i should go. ideally i would like to get it working as it is. tweak the configs and have it working. 
turning off the WEP is not an option.

i would appreciate any help with this.

much thanks

---

### Post by Toddy on 2005-06-09
Check to ensure that your router is set to "Open" authentication, not "Shared".  Was the only way I could get WEP to work for me using my D-Link DI-524.

---

