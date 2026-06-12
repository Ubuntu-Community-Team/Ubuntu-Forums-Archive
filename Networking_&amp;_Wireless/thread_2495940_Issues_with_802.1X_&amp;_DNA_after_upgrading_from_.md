---
title: "Issues with 802.1X &amp; DNA after upgrading from 18.04 to 22.04"
date: 2024-03-09
forum: Networking &amp; Wireless
---

### Post by Rich_Stanton on 2024-03-09
Hi, I've upgraded a headless ubuntu machine from 18.04 -> 20.04 -> 22.04. There's always a few gremlins when doing this, but to add to the complication, at the same time my Uni has implemented a new network which uses 802.1X for wired. I've got a few questions about 'expected' behaviour, so I can make sure things are set up correctly.

Initially when I rebooted after the upgrade, I had a message about needing a username to authenticate the ethernet. I went to our onboarding website & ran the app, and it seemed to work fine. However at some point I noticed that I didn't have any DNS servers set & couldn't resolve anything. I found a suggestion in a forum post that I needed to change managed="false" to "true" in /etc/NetworkManager/NetworkManager.conf following an upgrade. I set that and rebooted. At this point ethernet didn't authenticate. When I checked the logs it had ''Wired Connection' has security, but secrets are required.' I then logged in through the GUI, and had a message saying that a password was required for ethernet. Putting my password in didn't help, so I turned off 802.1X, re-ran the onboarding app, and it all worked fine and I had DNS now.

Unfortunately I'm remote for the next few days, so I can't fiddle more without risking cutting myself off, but I wanted to ask a few questions in advance of more playing:

Are there other aspects of networking that need tweaking when going from 18.04->22.04, and is changing 'Managed' status something that I needed to do? When searching, I found references to Ubuntu changing from NetworkManager to NetPlan, and that I should have something like the following in /etc/network/interfaces

network:
  ethernets:
    enp0s2:
      dhcp4: true
  version: 2

Where I just have:
auto lo
iface lo inet loopback


Does that indicate a problem?

Is the failure to authenticate to 802.1X after a reboot likely connected to my changing the 'Managed' setting? Or am I likely to have the same issue when I next reboot - do I need to check that there are some stored credentials somewhere, and if so, where? I saw that 802.1X uses wpa_supplicant, but /etc/wpa_supplicant just has 3 scripts and no config file? Should there be a config file?

Thanks!

---

### Post by Rich_Stanton on 2024-03-09
OK, I've solved one confusion - I can see that network manager stores it's 802.1X config in /etc/NetworkManager/system-connections. I only have 1 ethernet connection, but I have 4 entries in that folder. I assume that have rogue entries won't cause problems, or should I delete them? If I run nmcli I can see which entry is being used. In there I have entries for:
 ca-cert
client-cert
 eap
identity
private-key
private-key-password

Presumably if if fails to authenticate I can add a password= line in there too?

---

