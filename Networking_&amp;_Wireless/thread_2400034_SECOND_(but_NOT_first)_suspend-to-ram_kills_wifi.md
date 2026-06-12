---
title: "SECOND (but NOT first) suspend-to-ram kills wifi"
date: 2018-09-01
forum: Networking &amp; Wireless
---

### Post by MisterPi on 2018-09-01
On 18.04 with 4.15.0-32-generic running an Intel Wireless 7265  with the iwlwifi driver (driverversion=4.15.0-32-generic),  suspend-to-RAM followed by wakeup will kill wireless **the second time**. The first suspend/wakeup is OK, but the second time, the Networks box (from clicking the network icon on the toolbar) shows **nothing**, neither my router nor any other routers in my neighborhood.

In the past, when I've had problems like this, I sometimes could get it  to work by turning on airplane mode (in the Networks box) and turning it  off again, or trying other controls in the Networks box. But nothing  like this works anymore.

Assuming this is some kind of driver issue and I need to wait for a fix,  is there a quick workaround (short of rebooting) I can use in the  meantime? For instance, I see a process:

$ ps aux | grep wifi
root       482  0.0  0.0      0     0 ? S    11:09   0:03 [irq/131-iwlwifi]

Is there some kind of signal I can send to this process ("sudo kill  SIGwhatever 482") or some other mechanism to reset the driver so it  starts up again without having to reboot? 

NOTE: I searched around and found some pages with other suggestions. Some of  these are probably outdated (Ubuntu versions several years old), but  anyway, I tried these and none of these worked:

sudo service network-manager restart

sudo systemctl restart NetworkManager

sudo nmcli networking off
sudo nmcli networking on

sudo iwconfig wlp1s0 txpower off
sudo iwconfig wlp1s0 txpower on

nmcli radio wifi off
nmcli radio wifi on

sudo ifconfig wlp1s0 down
sudo ifconfig wlp1s0 up

For the last pair, the "up" command responded with

SIOCSIFFLAGS: Input/output error

I don't know if that means anything, but maybe it means the driver is broken at some deep level.  When the wifi is working properly, and I run the ifconfig command  pair as shown, I don't get the error.

---

### Post by MisterPi on 2018-09-15
This seems to have gone away on its own; I don't see it anymore.  I'm on kernel 0-34 now but I think maybe it was working OK *before* I upgraded from 0-33, although I also noticed the problem sometime before when I was on 0-33, so I don't think either 0-33 or 0-34 fixed the problem.

The wifi driver microcode wasn't updated either, so I'm not sure what updates, if any, fixed it.  Probably a library with a really contorted name that wouldn't stand out as obviously related to wifi or networking.

---

### Post by kurt18947 on 2018-09-15
> **MisterPi said:**
> This seems to have gone away on its own; I don't see it anymore.  I'm on kernel 0-34 now but I think maybe it was working OK *before* I upgraded from 0-33, although I also noticed the problem sometime before when I was on 0-33, so I don't think either 0-33 or 0-34 fixed the problem.

The wifi driver microcode wasn't updated either, so I'm not sure what updates, if any, fixed it.  Probably a library with a really contorted name that wouldn't stand out as obviously related to wifi or networking.

I'll have to check for updates. I have a Thinkpad that shows similar behavior. I'm also running Private Internet Access some of the time and thought that might be a contributor.  In my case turning the wifi off then on often fixed it.

---

