---
title: "Dynamic IP, static DNS, hosts and search domains - how?"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by Xianath on 2007-03-29
In Kubuntu, is it possible to have my IP/mask/gateway assigned dynamically but leave /etc/hosts and /etc/resolve.conf intact? I've tried profiles in the Network Connections kcontrol module but there is no way to specify a default one; tried chmod 444 /etc/hosts and /etc/resolve.conf, no dice. Tried editing the XMLs in /var/cache/setup-tool-backends/data/network/ but that yielded the same (lack of) result as network profiles did as there is no default.

The background behind this is that at work I carry my laptop around a lot, and different areas/floors/buildings are in different networks but in the same DNS domain. I know how to set this up on full manual (Slackware/FreeBSD/Gentoo style), but it just doesn't look right if I have to spend five minutes in a console while everyone else in the room is waiting for me to start my presentation.

For all its inferiority, this setup is annoyingly easy to achieve in Windows. I want to do it the Ubuntu way if possible, if only as a POC to shut up the Redmond fans around me. Maybe Network Monitor can help here - if yes, how?

Thank you for your attention,
Peter

---

### Post by lloyd_b on 2007-03-29
> In Kubuntu, is it possible to have my IP/mask/gateway assigned dynamically but leave /etc/hosts and /etc/resolve.conf intact? I've tried profiles in the Network Connections kcontrol module but there is no way to specify a default one; tried chmod 444 /etc/hosts and /etc/resolve.conf, no dice. Tried editing the XMLs in /var/cache/setup-tool-backends/data/network/ but that yielded the same (lack of) result as network profiles did as there is no default.

Take a look at the file "/etc/dhcp3/dhclient.conf".  You can control which settings are under the control of DHCP here, as well as setting manual values for some of those options.

Lloyd B.

---

### Post by Xianath on 2007-03-29
LLoyd, you nailed it! Would still be good to have it in the GUI though, minor as it may seem.

Thanks,
Peter

---

