---
title: "Please help: D-Link DWL-G550"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by old_man_buddha on 2007-03-19
I am new to Linux and Ubuntu and am having trouble getting version 6.1 to recognize my D-Link DWL-G550.  This card has the Atheros chipset, so I thought it would work out of the box.

Here are the results of lshw:
-network UNCLAIMED
             description: Ethernet controller
             product: AR5212 802.11abg NIC
             vendor: Atheros Communications, Inc.
             physical id: 9
             bus info: pci@00:09.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:e2000000-e200ffff irq:11

Here are the results of ifconfig:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

Here are the results of iwconfig:
lo        no wireless extensions.

sit0      no wireless extensions.

I briefly tried ndiswrapper, but there was an error reading the windows driver so I decided I should post here for help.

Thanks in advance!

---

### Post by old_man_buddha on 2007-03-20
Can anyone help me out an give this a shot?  Clearly the configuration line is missing from the lshw results.  I don't tried manually installing the drivers from this link ([http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)), but received multiple errors.

---

### Post by old_man_buddha on 2007-03-20
Also here are the contents of the /etc/network/interfaces file:

auto lo
iface lo inet loopback

auto ath0
ifact ath0 inet dhcp
wireless-mode managed
wireless-essid MYSID
wireless-key1 XXXX-XXXX-XXX

---

### Post by old_man_buddha on 2007-03-20
I also tried installing linux-restricted-modules-2.6.17-10-generic, but I'm getting an error that it failed to fetch [http://secuirty.ubuntu.com](http://secuirty.ubuntu.com), but of course it did since I can't get the driver installed for my card!

---

### Post by old_man_buddha on 2007-03-21
So, I plugged in an ethernet card and got myself a wired connection, downloaded linux-restricted-modules-'uname -r' and it worked like a charm.  I connected and things are beautiful.

---

