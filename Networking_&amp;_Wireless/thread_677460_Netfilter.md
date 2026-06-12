---
title: "Netfilter"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by superbo8218 on 2008-01-24
hi,

i have ubuntu 7.10 server on my router box and it routes traffic for my internet users - 10-40mbps with 3 eth ports. my /var/log/messages is full of this thing:


Jan 25 02:19:26 dhcp kernel: [848797.883407] nf_ct_ras: decoding error: out of range
Jan 25 02:42:08 dhcp -- MARK --
Jan 25 02:48:35 dhcp kernel: [850544.302274] nf_ct_ras: decoding error: out of range
Jan 25 02:48:36 dhcp kernel: [850545.888812] nf_ct_ras: decoding error: out of range
Jan 25 02:49:35 dhcp kernel: [850604.268770] nf_ct_ras: decoding error: out of range
Jan 25 02:49:36 dhcp kernel: [850605.761698] nf_ct_ras: decoding error: out of range
Jan 25 02:57:39 dhcp kernel: [851087.883761] nf_ct_ras: decoding error: out of range
Jan 25 02:57:41 dhcp kernel: [851090.250350] nf_ct_ras: decoding error: out of range

how serious it is? any solution?

---

### Post by dschulz on 2008-01-26
I'm having the same issue here, but I think it's not serious. The only information that I could find is in polish, I can't read polish at all.

("not serious" if you don't consider "serious" some thousand spurious messages being flooded by the kernel to the log files (wasting some disk space))  :P

---

### Post by superbo8218 on 2008-01-27
> **dschulz said:**
> I'm having the same issue here, but I think it's not serious. The only information that I could find is in polish, I can't read polish at all.

("not serious" if you don't consider "serious" some thousand spurious messages being flooded by the kernel to the log files (wasting some disk space))  :P


I THINK I FOUND SOME SOLUTION:
You could try unload module nf_conntrack_h323 if you dont use it. 
Or if you cant live without this module try to contact with module developers at [http://nath323.sourceforge.net/](http://nath323.sourceforge.net/) . They's module generates that error, probably module bug. At least they can tell what tool to use to debug with error. 

This module used by netfilter nat and/or statefull firewall to work around with VoIP h323 protocol. So if you dont nat any h.323 users just unload this module. Most VoIP applications can use sip VoIP protocol too which is prefered anyway.

---

