---
title: "DHCP Configuration Issue on Ubuntu Server: &quot;Not configured to listen on any interface"
date: 2024-10-30
forum: Networking &amp; Wireless
---

### Post by magma777dev on 2024-10-30
Hello everyone,
I'm trying to set up a DHCP server on Ubuntu Server, but I've encountered some issues. My goal is to have a virtual client receive a dynamic IP from the DHCP server, which I've configured on another virtual machine within the same network.
Here is my network setup:

[LIST]
[*]**Network**: 10.15.0.0
[*]**Netmask**: 255.0.0.0
[*]**DHCP Server IP**: 10.15.0.5
[*]**IP Range for Clients**: 10.15.0.101 - 10.15.0.200
[*]**DNS Server**: 8.8.8.8
[*]**Reserved IP for a specific client**: 10.15.0.231 (based on MAC address)

Steps I&#8217;ve Taken So Far:
[*]I installed the DHCP server on Ubuntu and configured the dhcpd.conf file with the following settings:

**subnet 10.15.0.0 netmask 255.0.0.0 {    range 10.15.0.101 10.15.0.200;    option routers 10.15.0.5;    option domain-name-servers 8.8.8.8;}**

-When I first tested it, the isc-dhcp-server service failed to start. In the log, I saw the following error message:

[B]Not configured to listen on any interfaces!

[/B]
[*]I double-checked the network interface names and confirmed that both virtual machines in VirtualBox are set to &#8220;Internal Network&#8221; mode.
[*]I&#8217;ve restarted the service several times and reviewed the configuration, but the issue persists, with the service failing with an exit-code error.
[*]I also confirmed that the mentioned interface (e.g., enp0s3) is on the same network as the DHCP configuration, but the DHCP server still won&#8217;t assign IPs to clients in the same network.

I&#8217;d really appreciate any suggestions for solving this issue, as I haven&#8217;t been able to find an effective solution.

Thank you in advance!](*,)
[/LIST]

---

### Post by Doug S on 2024-10-30
Could you please post your "/etc/default/isc-dhcp-server" file.
For example mine is:

```
doug@s15:~/config/etc/default$ [COLOR="#FF0000"]cat isc-dhcp-server[/COLOR]
# Defaults for isc-dhcp-server (sourced by /etc/init.d/isc-dhcp-server)

# Path to dhcpd's config file (default: /etc/dhcp/dhcpd.conf).
#DHCPDv4_CONF=/etc/dhcp/dhcpd.conf
#DHCPDv6_CONF=/etc/dhcp/dhcpd6.conf

# Path to dhcpd's PID file (default: /var/run/dhcpd.pid).
#DHCPDv4_PID=/var/run/dhcpd.pid
#DHCPDv6_PID=/var/run/dhcpd6.pid

# Additional options to start dhcpd with.
#       Don't use options -cf or -pf here; use DHCPD_CONF/ DHCPD_PID instead
#OPTIONS=""

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
[COLOR="#FF0000"]INTERFACESv4="br0"[/COLOR]
INTERFACESv6=""
```

---

