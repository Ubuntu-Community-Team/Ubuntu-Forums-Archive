---
title: "Have wifi problems? Check your Clock (possible Ubuntu Network Time Server Failure)"
date: 2017-03-27
forum: Networking &amp; Wireless
---

### Post by 6-launchpad-net-cefn-com on 2017-03-27
Sometime late last week, my automatically-synchronised clock was silently reset to some time in 2176. Turning off timeserver autosynchronization of the clock fixed my otherwise unfixable Wifi problems which had appeared out of the blue and taken many hours to diagnose.

There is a chance some others may be suffering from an ubuntu time server failure so I'm sharing here. Others may experience the same issue of network handshake failure for no obvious reason, and of course without a network, the time synchronisation will never resolve itself when the server comes back online, and instead you will spend days debugging wifi problems which are not wifi problems, unless you suddenly have a flash of insight and check your system clock.

In my case, the consequences were that my Toshiba Chromebook (which had been running Lubuntu perfectly for months) suddenly failing to connect via Wifi through any client, driver or device. The hardware was clearly functional as it could scan and identify networks. I believe this is because the time is somehow part of the Wifi auth handshake.

Of course, being a chromebook there was no way to attempt to try and resolve a regression through updating software as it has no other network device. Sourcing and attaching new wifi network hardware made no difference. Use of nmcli, wpa_supplicant and dhclient from the console ended in the same failure.

I can't tell for sure if there was a problem with the timeservers. There is also a chance there's something very screwy with my hardware, but it seems unlikely that my hardware clock would suddenly leap to 2176 owing to a local failure, so thought it worth sharing on the forum given the seriousness.

---

### Post by TheFu on 2017-03-27
Good post. Doubtful it was an ntpd issue on a remote system.  NTP migrates slowly to the current "correct time" over days.  Even migrating from being 5 minutes off will take some time. This protects systems from jumps in time that make no sense.  If you want to force a time jump, use **rdate**.

This isn't to say it is impossible to happen the way you wrote it, just that I'd look elsewhere first - like an electrical spike to the system or complete discharge of the battery. You would definitely KNOW if that happened on almost all chromebooks since the don't use CMOS batteries. Let 1 of my other chromebooks run down all the way and had to load factory chromeOS back onto it to get it booting at all again.

More sharing ... 
I have a Toshiba CB35 chromebook running a custom variant of Ubuntu (not Unity).  That doesn't really matter for this.
Correct time is extremely important for security on all Unix systems and any other systems which implement Unix-centric protocols - ssh, nfs, https.  Network authentication cares about having the correct UTC known too. On Unix systems world-wide, UTC is used for the clock and only the display time is different.  Windows has a mix of UTC and local time due to legacy reasons.

On Unix systems using NTP, there should be at least 3 time servers used.  This prevents a single bad source from overly impacting the system security.  Any NTP servers can be used. No need to use the Canonical-sponsored versions if they are unreliable in your part of the world.

Lastly, there are USB network adapters which work great with chromebooks.  I generally don't use wifi with my chromebook since a 1Gbps link will always blow away **any** wifi options available today.  Sure, sometimes, when traveling, I have no choice but to use wifi, but that is after looking for a wired alternative.
```
$ lsmod |grep ax
ax88179_178a           24576  0
usbnet                 45056  1 ax88179_178a
mii                    16384  2 usbnet,ax88179_178a

``` shows the working $22 USB3-to-GigE device I'm using from amazon.  It also provides a 3-port USB3 bus.  **iperf** shows 920 Mbps, which is respectable for any GigE adapter.  Real-word transfers are closer to 650 Mbps and the connect doesn't waiver at all. Extremely solid, unlike wifi in most places (even my home).

Wired networking is always better, if not always more convenient. ;)

---

