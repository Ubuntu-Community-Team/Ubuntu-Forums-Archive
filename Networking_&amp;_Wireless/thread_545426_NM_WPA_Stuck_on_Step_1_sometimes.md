---
title: "NM WPA Stuck on Step 1 sometimes"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by drewcoll on 2007-09-07
Network manager gets stuck after illuminating the first green blob.  It cannot connect to the network and then asks for a new key which doesnt work.  I know the key is right because if I unplug my router and plug it in again it connects.  Eventually it disconnects in about an hour or two.

I thought it was the router changing the WPA encryption on a schedule, but I changed the timeout and still had the problem.

WEP works fine, the Windows laptop connects fine with the WPA.

I'm using an airlink AWLL3026.

---

### Post by spd106 on 2007-09-08
I experience this too, from time to time.

Though I have no complete fix, there are a few things you can try to help out.
1) Check the manufacturer's website for a router firmware update.
2) If you are using ndiswrapper, look for a newer version of your driver linked from the ndiswrapper website.
3) Examine the /var/log/syslog for error messages, I usually get lots of 'dhcp timed out' or 'decrypt failed: packet dropped'.
4) When it fails, reload the driver via *sudo modprobe -r <driver>*, then *sudo modprobe <driver>*.
5) Turn off roaming mode and set static addresses/encryption settings on the machine in the /etc/network/interfaces file (see the Wireless Security sticky for a guide).

I have found that I can get by without having to do (5) any more, but sometime I get frustrated and it is the most reliable method of connecting, though it's more complicated to set up and less flexible, ymmv.

---

