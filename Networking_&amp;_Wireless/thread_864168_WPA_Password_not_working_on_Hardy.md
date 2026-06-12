---
title: "WPA Password not working on Hardy"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by cirobr on 2008-07-19
Hello,

I have a notebook HP Pavillion ze4920 equipped with WLAN card TRENDnet TEW-421PC H/W:B1. It always worked smoothly under Ubuntu Gutsy.

After a clean installation of Hardy, WLAN card driver is reinstalled with ndiswrapper. Card is recognized by the system, which in turn detects all hot spots within range. When one is chosen, it keeps asking over and over the WPA password and login to network is not completed. Other Windows and Gutsy computers are able to login to all WLANs.

Updating to latest driver from TRENDnet home page and re installation resulted on same failure.

If security on router is disabled, then the connection is done.

Any help to correct the problem is appreciated.

Regards,

Ciro.

---

### Post by tl3000 on 2008-07-19
Might be related to the following bug report:

[https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/207446](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/207446)

---

### Post by cirobr on 2008-07-19
Indeed, it seems the same issue. And it looks like there is no soluton yet, correct?

---

### Post by tl3000 on 2008-07-19
> **cirobr said:**
> Indeed, it seems the same issue. And it looks like there is no soluton yet, correct?

No solution that I'm aware of yet... the bug report remains open as of today.

Ubuntu developers have been dragging their feet on this problem and have not done anything for over 3 months since this problem surfaced when 8.04 was first introduced.  The bug report was closed at one point and then reopened with a 'confirmed' status when more reports of this problem trickled in.  I suspect this is a wider problem that affects much more users than it is being recognized since a lot of newbies don't realized what's going on with their wireless connection except that 'it does not work', and they don't know how to go about identifying and isolating the actual issue.  Thus, many cases go unrecognized and unreported.

---

### Post by robinbillings on 2008-07-19
If you execute 

tail /var/log/messages

you will see errors like the following:

Jul 19 16:48:28 rigpa dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus
.get.reason
Jul 19 16:48:30 rigpa kernel: [   47.155058] NET: Registered protocol family 17
Jul 19 16:48:31 rigpa kernel: [   47.562309] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul 19 16:48:36 rigpa dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus
.get.host_name
Jul 19 16:48:36 rigpa dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus
.get.domain_name
Jul 19 16:48:36 rigpa dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus
.get.nis_domain
Jul 19 16:48:36 rigpa dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus
.get.nis_servers
Jul 19 16:48:36 rigpa dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus
.get.interface_mtu
Jul 19 17:07:46 rigpa -- MARK --

If you connect to an unsecured server it will make the connection, but if it has to handle message to negotiate a secured connection you will not succeed as it is invoking an exchange routine.

Looks like to me that an Ubuntu developer cut and paste redhat linux code without reading it.  Hopefully, it will get the attention it deserves soon.

Robin Billings

---

### Post by tl3000 on 2008-07-22
> **robinbillings said:**
> ...

Looks like to me that an Ubuntu developer cut and paste redhat linux code without reading it.  Hopefully, it will get the attention it deserves soon.

Robin Billings

This is the first clue that anyone has shed on this problem.  I gave up after the first month since I don't have the time to be wasting to debug and fix Ubuntu's issues.  Thus, I've reluctantly been back to using WinXP SP3--and I've been a happy Ubuntu user since 6.04, but 8.04 without secured wireless is useless to me.

The one workaround that I've seen other advanced users doing is to revert back to using the 7.10 kernel--which is something I don't want to be messing around with nor do I have the time.  Ubuntu is just not quite ready for prime time yet...  Every new version of Ubuntu has required some configuration change in order to get wireless connection working--again and again.

---

### Post by nickdbliss on 2008-07-22
Do u have wpa_supplicant installeD?

---

### Post by tl3000 on 2008-07-22
> **nickdbliss said:**
> Do u have wpa_supplicant installeD?

Thanks but amateur sleuthing is not needed here...

Friendly suggestion: read the ENTIRE thread before responding would be more helpful.

---

### Post by nickdbliss on 2008-07-22
> **tl3000 said:**
> Thanks but amateur sleuthing is not needed here...

Friendly suggestion: read the ENTIRE thread before responding would be more helpful.

lol thanks for suggestion.

---

### Post by tschluter on 2008-07-22
> **tl3000 said:**
> No solution that I'm aware of yet... the bug report remains open as of today.

Ubuntu developers have been dragging their feet on this problem and have not done anything for over 3 months since this problem surfaced when 8.04 was first introduced.  The bug report was closed at one point and then reopened with a 'confirmed' status when more reports of this problem trickled in.  I suspect this is a wider problem that affects much more users than it is being recognized since a lot of newbies don't realized what's going on with their wireless connection except that 'it does not work', and they don't know how to go about identifying and isolating the actual issue.  Thus, many cases go unrecognized and unreported.

I ran into this problem after applying a batch of updates last week.  When attempting to connect the bubble on the networking icon states that it is waiting for a "key."  I'm using a Linksys 801.11g card.  Executing the command suggested by robinbillings returns similar results on my machine.

---

### Post by nickdbliss on 2008-07-22
I am having kernel 2.6.24 with ndiswrapper n windows driver installed for wireless. Use WPA-PSK security enabled on my wireless router. It connects automatically at start or when i manually start it. I had similar problem before, it would pop up as a loop asking for the password. So nevermind to explain what i did as my opinion is not required.lol. Cheers. 

As a matter of fact i have installed ubuntu on 24 laptops with wireless n WPA working...

---

