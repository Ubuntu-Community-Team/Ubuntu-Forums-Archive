---
title: "Terminal keeps coming up on login"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by dontknowhow on 2011-01-15
Hi,

Sorry for the misleading caption, it's late, and I wasn't paying attention.

I'm running Ubuntu 10.10.

I am desperately trying to forward a port.  Shouldn't be hard, right?  I am definitely paying the price for being a Linux newbie.

Well, here's what I have done so far:

* Enabled port forwarding on my router.
* Disabled the firewall.
* Attempted to switch my IP to static, and failed miserably:
** I could no longer connect to the Internet at all.  When restarting networking I was told that wlan, my wireless connection and the one I intend to use, is ignored.  I could only solve this by switching back to DHCP and rebooting.  This was after trying the graphical tool.
** Looked at the networking interfaces file but only saw the loopback interface there, even though I have other interfaces that are active.

I am stumped at this point.  I don't understand why the IP has to be static for the forwarding to work if I have not rebooted.  I don't understand how to set my IP to static, if one option disables the wireless connection and the other seems to not be relevant.

When I try with canyouseeme.org, I keep getting an error telling me the connection timed out.

Thanks,
The ever frustrated dontknowhow

---

### Post by Smart Viking on 2011-01-15
Just do it like this:
[IMG]http://www.smartviking.com/static.png[/IMG]
Where 10.0.0.6 is the static local IP i want.
10.0.0.138 is the router

Something like that.

---

### Post by dontknowhow on 2011-01-16
Oh dear, oh dear.  My gateway was wrong...after typing in 

Thanks Smart Viking!

$ route -n

I realized my mistake.

Too bad that doesn't help at all and my port is still closed according to canyouseeme.org.

I have now done all the steps:
* Forwarded port on router.
* Disabled firewall (decided to not risk configuring iptables for now).
* Set static IP on my machine.

I am not double-NATed, because if I was, I would have the same issues with my Windows box (which took about 20 seconds to configure) and my Mac box (which took about the same time).

Any ideas?

Thanks!

---

