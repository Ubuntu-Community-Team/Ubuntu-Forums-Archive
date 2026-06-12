---
title: "No DHCP on unencrypted, hidden WLAN"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by aberkov on 2008-08-13
So, I've just slapped the 8.04 on Dell Latitude D610 laptop, running Intel PRO/Wireless 2915ABG WLAN card. Here's the issue I'm cracking my skull against for the last 2 days:

The WLAN I'm trying to connect to is unencrypted, with hidden SSID (no control over that side of connection). No encryption means I can't connect to it through Network Settings panel (dropdown menu offers WEP & WPA options, no unencrypted). If I add the SSID through "Wireless Networks" panel, PC finds the WAP and apparently connects to it, but receives no DHCP config from the WAP. (I don't believe this is WAP/WLAN issue, as other PCs get DHCP just fine.)

I tried the Kevdog's guide (I know it says SSID must be visible, but I thought 'what the heck'), specifically these steps:

[I]sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>[/I]

But, while it looks like all the config was accepted, upon the last step I get 4 DHCPDISCOVER attempts on the interface, followed by:

[b]No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/b]

One thing I did notice as a bit of oddity is, Ubuntu is listing my WLAN card as **eth1** interface instead of **wlan0** (Ethernet card is being listed as **eth0**.)


Advice and assistance is much appreciated :)

---

### Post by jimv on 2008-08-13
Is this an access point that you are supposed to be connecting to?  If the owner has turned MAC filtering on, or limited the number of DHCP leases, then you won't be able to get an IP.

Otherwise try WICD instead of NetworkManger.  It just works.
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by aberkov on 2008-08-13
WAP doesn't have MAC filtering or limited number of DHCP leases defined, verified with admin. Any other laptop I try to connect connects fine. I'll give WICD a shot and report back, thanks!

---

### Post by aberkov on 2008-08-13
You, sir, are a godsend - WICD made everything tick like a bomb :)

Thank you!

---

### Post by jimv on 2008-08-13
> **aberkov said:**
> You, sir, are a godsend - WICD made everything tick like a bomb :)

Thank you!

Because that's what WICD does ;)

---

### Post by tps800 on 2009-03-31
Wicd is what I have been looking for for a long time now. No other tool to compete with --- really!

Any plans to port to C/C++?

---

