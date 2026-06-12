---
title: "Ethernet cards swap name assignments on every boot"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by silentcoder on 2007-09-06
Hi all,

Here is an extremely odd one.
I have servers with two onboard ethernet cards.
First card is an E1000 and the second is an E100.

These machines are meant to be LTSP servers running Kubuntu Feisty.

The cards pick up as eth2 and eth3 respectively (first oddity since it doesn't pick up anything at all on eth0 and eth1... it just seems to skip those)

Hence my /etc/network/interfaces file sets eth2 to be static on 192.168.0.254/24
Eth3 is dhcp and connects to the internet router.

All very simple. Eth2 has a static in a dhcpd range. Clients boot up, and I have internet. Now I reboot the server.
Inexplicably eth2 is now the E100 and the E1000 becomes eth3 (reversing it). So now the clients don't boot, and the internet don't work. If I now go and swap the lan cables between the two cards, then they all work again. On the next boot - they reverse AGAIN.

Obviously I cannot roll out servers that need to have the network wiring altered (how ever small the alteration) on every single boot.

I have NEVER in all my years with Linux encountered such a thing, I assume it's something (k)ubuntu is getting wrong with the mobo (as a hint, acpi doesn't work at all either).
Can anybody give me any idea where to start troubleshooting this ?

A.J.

---

### Post by kevdog on 2007-09-06
Look in your /etc/iftab file, this assigns interface names to MAC addresses.  I would first try either deleting or commenting out anything that is listed in the file.  If this doesnt work you can put each card's MAC address in the file and associate specifically with eth0, eth1.

Here is an example of the syntax:
```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

wlan0 mac 00:12:17:35:17:10 arp 1

```

---

