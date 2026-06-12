---
title: "Installing samba broke wireless wpa"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by carlosK on 2006-10-19
Hi,

I've just installed ubuntu today (moved from gentoo after 4 years) and what a pleasure it was!  After a little 'googling' I had ubuntu desktop installed on a Dell Latitude D600 laptop with full wpa wireless networking and all the nice power management features.

After installing various updates the wireless network stopped working; at bootup it fails with the following error:

ADDRCONF(NETDEV_UP): eth1: link is not ready

It can be (re)started successfully by running 

/etc/init.d/networking restart

after logging in, but as the laptop is for my non-techy partner, I would really like it to start automatically.

I toot the measure of reinstalling ubuntu (not so drastic after 4 years of gentoo) and noting at which point it failed. It would appear that enabling/installing SMB file sharing causes this problem.

My /etc/network/interfaces is as follows:

auto eth1
iface eth1 inet dhcp
wpa-conf managed
wpa-ssid [SSID-REMOVED]
wpa-key-mgmt WPA-PSK
wpa_psk [KEY-REMOVED]

Any help you could provide would be most welcome.

Regards,

Carlos.

---

