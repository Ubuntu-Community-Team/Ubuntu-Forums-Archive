---
title: "Can ping URLS but not run apt-get update"
date: 2023-10-29
forum: Networking &amp; Wireless
---

### Post by abasel on 2023-10-29
I have a VM running Ubuntu 22.04.3 LTS

I can ping archive.ubuntu.com but when I try apt-get update, I get "Failed to fetch https://archive.ubuntu.com....." 

I am sure it is a networking issue as I am working from an extra NIC that I enabled in Xen Orchestra and is now part of my pFsense.

What is confusing me though is if I can ping, what network issue would prevent the update.

There is no firewall enabled on the install and pfsense is totally open on this interface.

---

### Post by MAFoElffen on 2023-10-30
What is the Virtual Host system and what is the vSwitch that you are using in it, that you are pointing to from the VM?

When you run a traceroute on it pointed to archive.ubuntu.com, does it end up at swp25.viviani.canonical.com  (185.134.181.46)?

---

### Post by abasel on 2023-11-08
It turned out to be a config  issue on xcp-ng: [https://docs.xcp-ng.org/guides/pfsense/](https://docs.xcp-ng.org/guides/pfsense/)

I needed to Disable TX Checksum Offload

---

