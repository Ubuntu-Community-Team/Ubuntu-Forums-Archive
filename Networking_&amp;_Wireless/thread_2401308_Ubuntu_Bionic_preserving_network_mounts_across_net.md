---
title: "Ubuntu Bionic: preserving network mounts across networking changes"
date: 2018-09-16
forum: Networking &amp; Wireless
---

### Post by goatboy73 on 2018-09-16
Hi!

I'm having an interesting conundrum. I have a laptop which I move around sometimes, and thus the LAN cable gets removed and it automatically switches to Wi-Fi. I got that bit working as intended (or so I think) by way of a script in /etc/NetworkManager/dispatcher.d which uses nmcli to bring the wifi up and down as necessary. I've also created a systemd service to run a custom script that, upon resume from suspend, figures out if the LAN cable is plugged in and if it isn't, then wi-fi is brought up (if it's already up, then this script does no harm).

Sadly this is an area where I feel Linux usability lags a tiny bit behind Mac/Windows, but that's meat for another roast :)

My problem has to do with network mounts. I have a few that I'd like to have "permanently" configured for automount (via systemd's automount units). They're currently working fine on the wired network but when I unplug my wired network and switch to wi-fi, then the mounts stop working. Conversely, if I boot up using only wi-fi, then the mounts (over wi-fi) work fine, but then trouble ensues when I plug in the network cable.

This is kind of obvious since the machine's IP will have changed, and one would expect that the remote mount sessions are no longer applicable (right?).

However, I was hoping there was a mechanism by which I could configure systemd or some other part of the base o/s to somehow identify this network reconfiguration, invalidate the existing mounts, and re-establish them via the new network interface. Granted, if the mounts aren't availiable on the new network layout, then obviously the mounts would fail (this is expected and accepted behavior). I understand that file handles may be open at the time the switch happens - perhaps even preserved via suspend/resume -, and this might prove an insurmountable obstacle for my goals. I'd still like to figure out if this is ***possible*** (even if it results in the invalidation of any remote open file handles from the old mounts).

So... any ideas?

---

