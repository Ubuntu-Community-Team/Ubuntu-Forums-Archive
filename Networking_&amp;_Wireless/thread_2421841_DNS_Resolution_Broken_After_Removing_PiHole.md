---
title: "DNS Resolution Broken After Removing PiHole"
date: 2019-06-27
forum: Networking &amp; Wireless
---

### Post by gerowen on 2019-06-27
Ubuntu Server 18.04. I have been running PiHole on my Ubuntu server for a while now, and decided to break that service off onto a dedicated machine. After uninstalling it however, my server is unable to resolve any DNS names itself. I seem to have fixed this by adding the DNS server to the .yaml file in /etc/netplan and running netplan apply, but it doesn't stick after a reboot. I've applied a sort of duck tape fix by putting "netplan apply" in /etc/rc.local , but that doesn't really fix whatever the Pihole uninstaller broke.

I also tried:

```
sudo systemd-resolve -i enp2s0 --set-dns=10.1.1.3
```

10.1.1.3 being my local DNS server and new PiHole (it's working with every other system), and got

```
The specified interface enp2s0 is managed by systemd-networkd. Operation refused. Please configure DNS settings for systemd-networkd managed interfaces directly in their .network files.
```

Problem is, I can't seem to find anything named enp2s0.network anywhere on the system.

netplan apply with a modified .yaml file seems to be the only thing that works, but it isn't applying on reboot for some reason without me just sticking the command into my /etc/rc.local so that it runs on bootup.  As of right now, it's fine with the rc.local workaround, but I'd really like to figure why it's necessary in the first place.

I would love to just reset all of the networking configurations to their default, like I just did a clean install of the OS, but I'm not sure what that is since Ubuntu has had so many changes in recent years to how it manages network interfaces.

---

