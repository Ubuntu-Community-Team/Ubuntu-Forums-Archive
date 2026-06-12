---
title: "Always-on VPN via command line (pptp/pppd)"
date: 2016-03-13
forum: Networking &amp; Wireless
---

### Post by blm14 on 2016-03-13
I have successfully set up a command-line pptp VPN connection from my headless server by following the directions here:

[https://support.purevpn.com/command-line-setup-in-debian-linux](https://support.purevpn.com/command-line-setup-in-debian-linux)

And with the addition of adding "route add default dev ppp0" to the end of the /etc/ppp/ip-up.d/<route>.sh file.

The problem is that if there is an interruption, the connection drops and there doesn't seem to be a way to make it redial. Is there some way with cron or something that I can enable and disable an auto-reconnect option in the case of a loss of VPN connectivity? Thanks!

---

### Post by blm14 on 2016-03-17
FYI in case anyone wants to do this in the future - I accomplished always-on VPN by instructing pppd to reconnect after link failure. The way to do this is to edit your /etc/ppp/peers/<host> file and add the following three lines:

 persist
 holdoff 0
 maxfail 0

Persist means to redial on link failure, holdoff 0 means attempt redial immediately, and maxfail 0 means to keep trying to redial until successful. So far my VPN has been up for at least 3 days without problems.

---

