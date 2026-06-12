---
title: "Server 16.04 VLAN issues"
date: 2017-01-09
forum: Networking &amp; Wireless
---

### Post by james-jroth on 2017-01-09
I'm having issues with getting VLAN configured correctly.  

I have followed everything here [https://wiki.ubuntu.com/vlan](https://wiki.ubuntu.com/vlan)

but the only way I could get it to work was to go into my interfaces file and add it as

auto vlan5


iface vlan5 inet static
        address 192.168.5.3
        netmask 255.255.255.0
        vlan_raw_device ens3

I can then restart the networking interface and it works, but once I reboot the machine, it takes awhile to reboot and then doesn't have the vlan anymore.

When checking the networking status, I see;

&#9679; networking.service - Raise network interfaces
   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor preset: enabled)
  Drop-In: /run/systemd/generator/networking.service.d
           &#9492;&#9472;50-insserv.conf-$network.conf
   Active: failed (Result: exit-code) since Mon 2017-01-09 22:20:42 UTC; 22min ago
     Docs: man:interfaces(5)
  Process: 1340 ExecStart=/sbin/ifup -a --read-environment (code=exited, status=1/FAILURE)
  Process: 771 ExecStartPre=/bin/sh -c [ "$CONFIGURE_INTERFACES" != "no" ] && [ -n "$(ifquery --read-environment --list --exclude=lo)" ] && udevadm settle (code=exited, status=0/SUCCESS)
 Main PID: 1340 (code=exited, status=1/FAILURE)


Jan 09 22:19:12 host1 systemd[1]: Starting Raise network interfaces...
Jan 09 22:20:42 host1 ifup[1340]: Set name-type for VLAN subsystem. Should be visible in /proc/net/vlan/config
Jan 09 22:20:42 host1 ifup[1340]: ERROR: trying to add VLAN #5 to IF -:ens3:-  error: File exists
Jan 09 22:20:42 host1 ifup[1340]: Cannot find device "vlan5"
Jan 09 22:20:42 host1 ifup[1340]: Failed to bring up vlan5.
Jan 09 22:20:42 host1 systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE
Jan 09 22:20:42 host1 systemd[1]: Failed to start Raise network interfaces.
Jan 09 22:20:42 host1 systemd[1]: networking.service: Unit entered failed state.
Jan 09 22:20:42 host1 systemd[1]: networking.service: Failed with result 'exit-code'.


Has anyone else experienced this error, or know how to fix it?

Thanks,

PS - I have been searching for a couple hours now on a fix and haven't been able to find anything.

---

