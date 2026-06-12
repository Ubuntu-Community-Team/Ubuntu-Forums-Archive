---
title: "Intel 3945ABG wireless card and hidden SSID"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by rimvydukas on 2007-04-09
Hi,

Just installed kubuntu 7.04. I can't connect to my wireless router when ssid is hidden. I can connect to router when ssid is not hidden but right after I disable ssid broadcast - after next computer restart result is the same - cant connect whatever I do:( Right after I enable ssid broadcast I can connect again. I'm trying to connect using kde network manager. interfaces file is empty (only auto eth1 and iface eth1 inet dhcp in there) I do not have wpa_supplicant.conf in /etc. Can anyone help me? Big big thanks.

---

### Post by chili555 on 2007-04-10
It's a known bug: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/50214](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/50214)

Not sure what to suggest, except broadcast.

---

### Post by rimvydukas on 2007-04-10
No, broadcast is not solution:)

But I've found a solution. There is network manager like Wicd. I tried it instead normal network manager and knetworkmanager. I was able to connect to my wireles WAP2 router with hidden SSID without a single problem. What a relief:)

---

### Post by madsmaddad on 2007-11-04
"There is network manager like Wicd."

can you advise me what the full correct name for this application is and where I find it. I did not have any problems with my 3com usb client connecting to my router with disabled broadcast at all, but I am having problems setting up WPA.

---

### Post by ukcarl on 2008-03-03
I've foudn switching my wireless card to just support b and g works, doe sthis help anyone else?

---

### Post by jcostom on 2008-03-03
> **chili555 said:**
> It's a known bug: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/50214](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/50214)

Not sure what to suggest, except broadcast.

For what it's worth, I'm using this exact same card in my Thinkpad with a hidden SSID, every day.

I'm on Gutsy, running a customized 2.6.24 kernel, using the iwlwifi drivers (mac80211 based).  The SSID is hidden, using WPA2 with EAP-TTLS to authenticate.  Works great.

If you go this route, you'll likely also want to apply the iwl-leds patch, so your wifi led will work:

[http://bughost.org/bugzilla/show_bug.cgi?id=1209](http://bughost.org/bugzilla/show_bug.cgi?id=1209)

--j

---

