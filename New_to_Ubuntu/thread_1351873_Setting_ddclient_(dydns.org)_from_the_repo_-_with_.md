---
title: "Setting ddclient (dydns.org) from the repo - with multi network cards (How)"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by nomnex on 2009-12-11
Configuring the ddclient, on the GUI Window, the help for the last field (see: print screen) says - it is in singular:

> Enter the name of the network interface (eth0/wlan0/ppp0/...) to use for dynamic DNS serviceI need to enter my 2 network interface. Is it possible and how?

```
eth0,wlan1
```or

```
eth0/wlan1
```Unfortunately, I have already completed the configuration GUI (with only one network card 'eth0') how do I modify the configuration file and what's its location?

Edit: What port on the NAT router (if any) do I need to forward to be reached from [www.dyndns.com?]("http://www.dydns.com?")

Thanks

---

### Post by nomnex on 2009-12-11
**Edit:**

I found how to re-edit the settings

```
dpkg-reconfigure ddclient
```I need advice regarding 2 more window settings
[B]
See: print-screen 1[/B]

What is run ddnclient on PPP connect? I have selected <YES>. Please advice/explain.

**See: print screen 2**

Run ddnclient as daemon. I have selected <YES>. I assume this is like a service runing in the background? Please advice if wrong setting.

**Next window setting (no print screen)**

The default refresh interval time was 300 s. I have left it untouched.

---

