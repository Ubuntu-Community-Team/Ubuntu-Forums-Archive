---
title: "Ubuntu Can't Connect to Router / Wifi network"
date: 2005-09-30
forum: Networking &amp; Wireless
---

### Post by pear-i on 2005-09-30
Hey there,

I just bought a Netgear WGR614 v6 router for my home network, and for some reason my laptop can't connect to it.

My settings in System > Networking for eth1 are set up for DHCP
ESSID is filled in for my network
WEP key is setup 
and Configuration is set to DHCP

These settings worked fine at my University (DHCP w/o WEP) yet for some reason i'm unable to connect to the network. 

I believe it detects the network cause - the signal strength goes down when i turn off my router (it then goes and connects to my neighbour's unsecure network) 

I've searched for settings on the forums and tried using various things but still to no avail.

my /etc/network/interface section for eth1 is as follows:

iface eth1 inet dhcp
wireless-mode open
wireless-key ********
wireless_channel 1 

Default, this didn't have the last 3 wireless entries but it still didn't work.

If you guys could find the problem that'd be much appreciated!

Thanks!
________________________
Using Dell C640 laptop & Hoary

---

### Post by mlomker on 2005-09-30
Let me know if [this helps.]("http://www.ubuntuforums.org/showpost.php?p=374072&postcount=3")

---

### Post by pear-i on 2005-10-01
*smiles* thanks mlomker!
that worked instantaneously :)

---

