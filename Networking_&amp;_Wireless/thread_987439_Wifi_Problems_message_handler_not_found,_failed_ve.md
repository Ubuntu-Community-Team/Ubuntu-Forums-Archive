---
title: "Wifi Problems: message handler not found, failed verification."
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by erikschneider21 on 2008-11-19
Hello,

I've been having severe trouble with my wifi connection. With *extreme* frequency, I cease to be able to access the internet, though my wifi icon in the corner still reads two bars. When this happens, I have to reconnect to my wireless network and restart all connections (ie, reload every page I was trying to access). I've checked the system log, and this is what it shows:

Nov 19 14:51:24 eu kernel: [11135.855675] wifi0: FAILED verification of AR5K_PHY_WEAK_OFDM_LOW_SELFCOR default value [found=0x1 (1) expected=0x1 (1)].
Nov 19 14:51:24 eu kernel: [11135.855690]               (unknown):0x986c:0x050cb081:.....1.1 ....11.. 1.11.... 1......1:unknown
Nov 19 15:01:45 eu kernel: [11478.911456] wifi0: FAILED verification of AR5K_PHY_AGCCOARSE_LO default value [found=0xcc (-52) expected=0xcc (-52)].
Nov 19 15:01:45 eu kernel: [11478.911481]               (unknown):0x985c:0x3137665e:..11...1 ..11.111 .11..11. .1.1111.:unknown

Nothing shows up when I Googled for answers that matches this problem other than it seems to have something to do with the madwifi drivers.

Additionally, every so often I get completely booted off the network and Ubuntu automatically starts to reconnect for me, though it is extremely frustrating when, for instance, I'm playing games online. This is what the log reads when that happens:

Nov 19 15:08:12 eu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.host_name
Nov 19 15:08:12 eu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_domain
Nov 19 15:08:12 eu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_servers
Nov 19 15:08:12 eu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.interface_mtu

Now, I've searched around for solutions to this, and the closest I could come up with was this: [https://bugs.launchpad.net/ubuntu/+source/dhcdbd/+bug/93360](https://bugs.launchpad.net/ubuntu/+source/dhcdbd/+bug/93360)

I tried the partial workaround near the bottom of the page, but it made it such that only one dot in the wifi connection animation would ever light up, until I undid it and it returned to its less-broken state.

I'm running Hardy 64-bit on a Macbook Pro Santa Rosa with Madwifi drivers. I realise I shouldn't be expecting things to work well on this setup, but if someone here would be able to help even a little bit, I'd be eternally grateful.

---

