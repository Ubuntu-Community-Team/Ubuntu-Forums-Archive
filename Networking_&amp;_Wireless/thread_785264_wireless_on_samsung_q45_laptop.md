---
title: "wireless on samsung q45 laptop"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by jaybee99 on 2008-05-07
I am setting up a new samsung q45 laptop with Hardy and can't get wireless working, on my network which has a 64bit WEP HEX password. I tried roaming mode and manual configuration through the GUI and the manual method given [here]("http://ubuntuforums.org/showthread.php?t=684495"). The manual method ends up with:

```
Listening on LPF/wlan0/00:1c:bf:7e:72:f5
Sending on   LPF/wlan0/00:1c:bf:7e:72:f5
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Any ideas?

---

### Post by superprash2003 on 2008-05-07
have you enabled DHCP in your wifi router?

---

### Post by jaybee99 on 2008-05-07
> **superprash2003 said:**
> have you enabled DHCP in your wifi router?
Thanks for your reply. Yes, the router uses DHCP and it works fine with other boxes, including one running gutsy. The laptop driver is iwl3945, which other people seem to be using with no problem, so it's confusing. I tried turning off security and still couldn't connect with no password.

How should I start troubleshooting this?

---

### Post by jaybee99 on 2008-05-07
I am using the iwl3945 driver, but most other people with this laptop seem to be using ipw3945. That driver isn't available to me AFAIK, because modprobe ipw3945 doesn't work. How do I find it, install it, and stop using the other one?

---

### Post by superprash2003 on 2008-05-07
oh.. so you arent able to connect at all?or are you able to connect to the network but not able to do anything?

---

