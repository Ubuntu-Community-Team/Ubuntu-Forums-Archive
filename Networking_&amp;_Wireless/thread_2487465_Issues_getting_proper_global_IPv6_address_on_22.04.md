---
title: "Issues getting proper global IPv6 address on 22.04."
date: 2023-06-05
forum: Networking &amp; Wireless
---

### Post by crkinard on 2023-06-05
388.2_2GT-AXE11000I have been trying to get an install of Ubuntu Server 22.04 to get a proper global IPv6 from my router for a few days now.
My Windows machine seems to work with no issue getting a working address. 

I keep getting IPv6 addresses like : 
fd67:662f:a332:49cb:8261:5fff:fe10:e935/64
IPv5 is fine.

Server:
Linux dock 5.15.0-73-generic #80-Ubuntu SMP Mon May 15 15:18:26 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux

PRETTY_NAME="Ubuntu 22.04.2 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.2 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy

Netplan:
network:
  version: 2
  renderer: networkd
  ethernets:
    ens4f0:
      dhcp4: yes
      dhcp6: yes
    ens4f1:
      dhcp4: yes
      dhcp6: yes


Router:
Asus GT-AXE11000
Merlin 388.2_2

DHCP-DP: Enabled
WAN Prefix Length: 56
Statefull (or stateless dosent matter)
RA: Enabled

ISP:
FiOS

---

### Post by Dennis N on 2023-06-05
The two IP addresses:
Public IP address (WAN): Find it at [https://whatismyipaddress.com/](https://whatismyipaddress.com/)
Private IP address (LAN): use terminal command: ip address

---

### Post by crkinard on 2023-06-07
I cannot resolve any IPv6 addresses from the Ubuntu box because it does not have a real external IPv6 address.

---

### Post by crkinard on 2023-06-12
Seems like there is a DHCPv6 bug in 22.04. LTS

Installed 23.04 and I got proper DHCPv6 addresses for my interfaces. 
No idea what the issues at all.

With 22.04 LTS it just keeps asking dnsmasq for a ipv6 address, dhsmasq give sone. 22.04 does nothing with it and just keeps asking for a ipv6 over and over and over and over again according to dnsmasq logs.

---

### Post by crkinard on 2023-06-12
Ahh great. 22.04''s DHCPv6 client or whatever is broken...
23.04's works but nvidia docker is not supported.

gahhh....

---

### Post by tkubnt on 2023-06-29
Does `sudo dhclient -6 <interface>` work for you on 22.04? It might be some systemd-networkd breakage. Others are struggling with it too on Oracle OCI:
[https://community.oracle.com/customerconnect/discussion/687610/oci-ipv6-address-not-assigned-to-oci-ubuntu-instance-by-dhcp](https://community.oracle.com/customerconnect/discussion/687610/oci-ipv6-address-not-assigned-to-oci-ubuntu-instance-by-dhcp)

I filed a bug for now: [https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/2025382](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/2025382)

---

