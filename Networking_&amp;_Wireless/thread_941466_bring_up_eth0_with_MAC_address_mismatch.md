---
title: "bring up eth0 with MAC address mismatch"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by untill on 2008-10-08
Not a question, just a FYI about a problem I kinda solved today.

I had Ubuntu 7.04 running as a virtual machine, and simply copied it. However, it appears that the new system got a new virtual networking card with a new MAC address, and as a result the system did not have networking, apart from lo. 

Digging showed that /etc/iftab was obsolete, and /etc/udev/rules.d/70-persistent-net.rules produced a line containing the correct new MAC address and a mapping to eth0. dmesg showed that eth0 was correctly recognized. But then something strange must happen, because the device never shows up as eth0. The error upon ifup eth0 is

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
SIOCGMIIPHY on 'eth0' failed: No such device

After some searching, I found a [hint]("https://lists.ubuntu.com/archives/ubuntu-users/2008-January/134366.html") that this could be solved with udev, but not exactly how. Anyhow, the device name found in the registry was eth2, found with

find /sys -iname *eth*

So I then went into /etc/network/interfaces and replaced all occurances of eth0 with eth2, restarted the network

/etc/init.d/networking restart

... and it worked. ifconfig displays now eth2 beside lo. That's enough for me, even though it'd be cool to know what exactly went wrong and how to get it back to eth0.

Hope this post helps you, too.

---

### Post by untill on 2008-11-05
Just encountered the same problem with a fresh install of 8.04. I picked DHCP during the installation process and had no network after the installation process.

/etc/udev/rules.d/70-persistent-net.rules revealed a MAC address different from the real one. So, I deleted /etc/udev/rules.d/70-persistent-net.rules and /var/lib/dhcp3/dhclient.eth0.leases, and restartet the network.

/etc/init.d/networking restart

Still no dice. But then I replaced each occurence of eth0 with eth1 in /etc/network/interfaces and restarted networking. Voila!

This appears to be a bug, a conflict between eth0 and DHCP in some startup script. However, I lack the knowledge to be able to say exctly what goes wrong. :confused:

---

### Post by untill on 2008-11-21
Another update.

I upgraded to 8.10, and still encounter the same problem. Deleting /etc/udev/rules.d/70-persistent-net.rules and restarting network (err, I believe I rebooted) helps.

---

### Post by muppis on 2009-03-24
I faced up also with this problem when moving physical to virtual, removing /etc/udev/*-persistent-net.rules and rebooting helped.

---

