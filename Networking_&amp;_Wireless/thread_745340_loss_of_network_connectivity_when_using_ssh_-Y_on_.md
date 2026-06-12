---
title: "loss of network connectivity when using ssh -Y on 7.04"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by jonnyofthedead on 2008-04-04
Hi all,

As the title says, I'm experiencing a strange, possibly ssh-related error with ubuntu 7.04. After bootup, internet connectivity is fine, I can ping various machines on my departmental network, and everything seems to be well-behaved; provided I don't use ssh, the connection seems to be indefinitely stable. If I ssh (with X forwarding) into one of the departmental servers and from there into a machine behind a firewall, everything works for a few minutes, then the remote application freezes and all useful network connectivity is lost and never properly regained, even if restarted using:

sudo /etc/init.d/networking restart

At best, this allows me to ping a few departmental servers (e.g. the DNS servers), but frequently, even that doesn't work, and either I get an error message saying it's not permitted or nothing happens. Rebooting restores network functionality.

Do any of you guys have any suggestions on how I might fix this?

---

