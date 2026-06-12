---
title: "networkmanager does not honour a 3g connection"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by t0bias on 2008-07-03
hi,

i've got a huawei e220 which is working fine. if i choose to connect via ppp0 in the networkmanager-applet, it is connecting, but it does not show a connection. this is not too bad, but the problem is, that as soon as i get within the reach of a wireless-access-point, networkmanager tries to connect and overrides the /etc/resolv.conf-settings of the ppp0-connection.
as a consequence i always have to look up the nameservers via /var/log/messages and fill them in to /etc/resolv.conf by hand.
any ideas how to avoid this problem?

thanks,

toby

---

### Post by Fingers &amp; Thumbs on 2008-07-03
I don't use this method to connect, myself. But if you go to >Administration >Network. You should be able to switch off your wireless there.

I personally use wvdial to connect my e220 without any problems, so if you find you cannot resolve the problem with network manager, you could use [This Howto]("http://ubuntuforums.org/showthread.php?t=843973") to set your e220 by other means and with a variety of frontends.

---

### Post by Fingers &amp; Thumbs on 2008-07-03
Also, not something I've tried myself, [Network Manager 7.0]("http://ubuntuforums.org/showthread.php?p=5311013#post5311013") which apparently has much improved support for mobile broadband.

---

### Post by t0bias on 2008-07-03
Hm... just tried networkmanager 7.0, didn't help at all, except for ppp0 is now called "Auto GSM"...
Thanks

---

