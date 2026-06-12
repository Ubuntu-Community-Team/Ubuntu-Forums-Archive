---
title: "Wireless drivers work, but still no internet access"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by hans030390 on 2007-04-11
I have the rt2500 drivers properly installed on my computer (6.06). I've had them working before, but I had to reinstall Ubuntu.

After setting everything up, it recognizes my router and connects.

The problem is, I still get no connection (in Firefox, for example).

I checked my networking tools (or some similar tool) and it said my ra0 was running only on IPv6. I don't run on that, I use IPv4. I have no idea how to turn it on to get it properly working (the ra0 configuration button is grayed out).

Any help is greatly appreciated!

Edit: I have disabled IPv6 in Firefox already, no luck.

---

### Post by Floppyjoe on 2007-04-11
This Url may be of help to you:
[http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php)

---

### Post by josephus on 2007-04-11
can you ping your router?  if not, it might be related to dhcp: try sudo dhclient ra0

---

### Post by hans030390 on 2007-04-11
OpenDNS didn't help any.

In the network tools, it only has an IPv6 connection for ra0. I only use IPv4. I'd like to disable the IPv6 and enable IPv4.

Then again, I'm not even sure if Ubuntu is even recognizing my hardware.

It's been so long since I've had to set up my wireless card.

---

### Post by hans030390 on 2007-04-11
I checked iwconfig, and my card is working (it's getting a signal and everything).

I still think it's the IPv6 screwing me over. I really need help.

---

### Post by josephus on 2007-04-11
there are lots of post about disabling ipv6, have you tried any of them?

[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

also check dmesg for any error messages that might be related.

---

### Post by hans030390 on 2007-04-11
Yeah, I tried disabling IPv6, but then I had no sort of connection.

Strangely, I disabled ra0, took off security, and reactivated it, and now it's working.

Weird. I think this happened to me last time. Now I'm afraid that turning off the compy or enabling security will screw it up again.

---

### Post by josephus on 2007-04-11
your problem is probably unrelated to ipv6.  it seems more likely you were never connected to your access point.  maybe you didn't put in the right password.

---

