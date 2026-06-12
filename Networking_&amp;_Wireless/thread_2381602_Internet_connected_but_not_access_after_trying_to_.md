---
title: "Internet connected but not access after trying to set up a vpn"
date: 2018-01-02
forum: Networking &amp; Wireless
---

### Post by juanchofelipe on 2018-01-02
Hi, my internet was working fine in Ubuntu 17.10 until I tried to set up a private VPN. It didn't work in settings so after reading some forums one suggested to install the next packages:

apt install vpnc network-manager-vpnc network-manager-vpnc-gnome

After that mi internet has a question mark and I can't browse, I removed all those packages and rebooted my PC but it didn't work.

This is the information I have of nmcli device

virbr0       bridge      connected     virbr0
wlp2s0    wifi           connected     fmlia_rodriguez
enp1s0    ethernet  unavailable    --
lo              loopback unmanaged  --
virbr0-nic tun            unmanaged --

I tried with wireless and wired connection, but both show the question mark

I can ping to 8.8.8.8 and to any ip address but when I ping to google.com for example I get: Name or service not known.

I think the issue is with DNS so I did

Sudo dhclient wlp2s RTNETLINK answers: File exists

And I tried something else:

sudo dpkg-reconfigure resolvconf Package 'resolvconf' is not installed and no information is available

---

### Post by DuckHook on 2018-01-02
Welcome to the forums, juanchofelipe.

Do you have a Cisco Concentrator? If not, then those were wrong packages to install. Your attempt to remove them may have also removed essential network packages.

I'm no network guru, but for now I would try the obvious:```
sudo apt update && sudo apt install resolvconf
```

Then reboot and post back results.

---

