---
title: "Problems with WLAN and WDS"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by tjobbe on 2008-07-08
Hi,

I decided recently to try out Ubuntu 8.04 on my older Dell D505 with an MPCI 1300 running 4306 (rev2)and ran into the regular Broadcom WLAN issue, at least I believed so initially but the standard drivers loaded with the fwcutter on the distribution loaded worked fine form me on single AP set-up.

My set-up contains a wireless network with two routers from AVM running WDS with WPA2 and WPA2/WPA as access point security.

Due to the WDS router set-up all clients are in the same network (incl the ones connected via Ethernet) so both AP's are using the same SSID, channel and network range set up as roaming. WIth XP clients that works and with my small EEEPC and Xandros I have no issues as well with that.

When having both WDS (master and repeater) active the D505 detects the SSID (but shows only ONE access point on the NetworkMOnitor UI) and connects but only at max rate set to 2M, anything above is not getting a lease from the DHCP. Both AP are visible on the scan.

When switching off the repeater the WLAN rate can be set to max 54M and all works fine with no complaints.

Has anyone come across that problem (as most WDS only work with WEP and this is AVM does work with one vendor setup only) ? I saw threads where users discuss that WLAN gets unstable when many AP providing broadcasts.

I need to keep the Repeater on as I need to provdide WLAN downstairs for the Media Client and when working outside.

Thanks, Tjobbe

---

