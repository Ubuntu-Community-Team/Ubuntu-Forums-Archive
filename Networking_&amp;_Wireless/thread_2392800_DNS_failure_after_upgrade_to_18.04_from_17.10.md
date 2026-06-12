---
title: "DNS failure after upgrade to 18.04 from 17.10"
date: 2018-05-25
forum: Networking &amp; Wireless
---

### Post by Stronty on 2018-05-25
So i did the upgrade, which did not go smoothly for some reason.  Install complained about not being able to install menu and then hung.  I was able to manually recover by doing dpkg - - configure - a and apt - - fix-broken install. 

Yet after reboot i have no DNS.  And can't work out how to fix it.  Nothing i have read about DNS problems helps.  My OpenWRT router provides DNS in the DHCP response.  It works for every connected device and also for this pc when it was running 17.10  but not now.  Now i just get Temporary failure in name resolution.  I can ping raw ip's no problem.  Its a DNS problem, so what do i do to fix this?? 

I can't even get a temporary dns working, no idea how.  Could it BE any more opaque???

If i go to "Connection Information" on Wired connection 1 it shows my ip address, AND the Primary DNS of my router and a Secondary DNS of 8.8.8.8 yet still its unable to do DNS.  So the p. Is getting the appropriate dns settings from.the dhcp messages.

---

### Post by Stronty on 2018-05-26
This is all the data i can extract about it.  Still no idea why Network Manager knows the DNS Servers, but nothing else does.  And no idea why this only happened to me on 18.04 but 17.10 has been totally fine.

```
$ ping [www.google.com](www.google.com)
ping: [www.google.com:](www.google.com:) Temporary failure in name resolution

$ ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.104  netmask 255.255.255.0  broadcast 192.168.2.255
        inet6 fe80::8e89:a5ff:fe0f:cec6  prefixlen 64  scopeid 0x20<link>
        ether 8c:89:a5:0f:ce:c6  txqueuelen 1000  (Ethernet)
        RX packets 87  bytes 37036 (37.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 112  bytes 17685 (17.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 18  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 418  bytes 32294 (32.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 418  bytes 32294 (32.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255
        ether 52:54:00:5e:47:cb  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

$ systemctl status resolvconf
&#9679; resolvconf.service - Nameserver information manager
   Loaded: loaded (/lib/systemd/system/resolvconf.service; enabled; vendor preset: enabled)
   Active: active (exited) since Sat 2018-05-26 12:25:31 +08; 1min 9s ago
     Docs: man:resolvconf(8)
  Process: 3522 ExecStart=/sbin/resolvconf --enable-updates (code=exited, status=0/SUCCESS)
  Process: 3521 ExecStartPre=/bin/touch /run/resolvconf/postponed-update (code=exited, status=0/SUCCESS)
  Process: 3519 ExecStartPre=/bin/mkdir -p /run/resolvconf/interface (code=exited, status=0/SUCCESS)
 Main PID: 3522 (code=exited, status=0/SUCCESS)

$ systemd-resolve --status
Global
          DNSSEC NTA: 10.in-addr.arpa
                      16.172.in-addr.arpa
                      168.192.in-addr.arpa
                      17.172.in-addr.arpa
                      18.172.in-addr.arpa
                      19.172.in-addr.arpa
                      20.172.in-addr.arpa
                      21.172.in-addr.arpa
                      22.172.in-addr.arpa
                      23.172.in-addr.arpa
                      24.172.in-addr.arpa
                      25.172.in-addr.arpa
                      26.172.in-addr.arpa
                      27.172.in-addr.arpa
                      28.172.in-addr.arpa
                      29.172.in-addr.arpa
                      30.172.in-addr.arpa
                      31.172.in-addr.arpa
                      corp
                      d.f.ip6.arpa
                      home
                      internal
                      intranet
                      lan
                      local
                      private
                      test

Link 5 (virbr0-nic)
      Current Scopes: none
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: allow-downgrade
    DNSSEC supported: yes

Link 4 (virbr0)
      Current Scopes: none
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: allow-downgrade
    DNSSEC supported: yes

Link 3 (wlan0)
      Current Scopes: none
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: allow-downgrade
    DNSSEC supported: yes

Link 2 (eth0)
      Current Scopes: none
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: allow-downgrade
    DNSSEC supported: yes

$ nmcli connection show Wired\ connection\ 1 
connection.id:                          Wired connection 1
connection.uuid:                        995000d6-3311-3674-8649-14b6d44af2e3
connection.stable-id:                   --
connection.interface-name:              --
connection.type:                        802-3-ethernet
connection.autoconnect:                 yes
connection.autoconnect-priority:        -999
connection.autoconnect-retries:         -1 (default)
connection.timestamp:                   1527308732
connection.read-only:                   no
connection.permissions:                 --
connection.zone:                        --
connection.master:                      --
connection.slave-type:                  --
connection.autoconnect-slaves:          -1 (default)
connection.secondaries:                 --
connection.gateway-ping-timeout:        0
connection.metered:                     unknown
connection.lldp:                        -1 (default)
802-3-ethernet.port:                    --
802-3-ethernet.speed:                   0
802-3-ethernet.duplex:                  --
802-3-ethernet.auto-negotiate:          yes
802-3-ethernet.mac-address:             8C:89:A5:0F:CE:C6
802-3-ethernet.cloned-mac-address:      --
802-3-ethernet.generate-mac-address-mask:--
802-3-ethernet.mac-address-blacklist:   --
802-3-ethernet.mtu:                     auto
802-3-ethernet.s390-subchannels:        --
802-3-ethernet.s390-nettype:            --
802-3-ethernet.s390-options:            --
802-3-ethernet.wake-on-lan:             1 (default)
802-3-ethernet.wake-on-lan-password:    --
ipv4.method:                            auto
ipv4.dns:                               --
ipv4.dns-search:                        --
ipv4.dns-options:                       (default)
ipv4.dns-priority:                      0
ipv4.addresses:                         --
ipv4.gateway:                           --
ipv4.routes:                            --
ipv4.route-metric:                      -1
ipv4.ignore-auto-routes:                no
ipv4.ignore-auto-dns:                   no
ipv4.dhcp-client-id:                    --
ipv4.dhcp-timeout:                      0
ipv4.dhcp-send-hostname:                yes
ipv4.dhcp-hostname:                     --
ipv4.dhcp-fqdn:                         --
ipv4.never-default:                     no
ipv4.may-fail:                          yes
ipv4.dad-timeout:                       -1 (default)
ipv6.method:                            ignore
ipv6.dns:                               --
ipv6.dns-search:                        --
ipv6.dns-options:                       (default)
ipv6.dns-priority:                      0
ipv6.addresses:                         --
ipv6.gateway:                           --
ipv6.routes:                            --
ipv6.route-metric:                      -1
ipv6.ignore-auto-routes:                no
ipv6.ignore-auto-dns:                   no
ipv6.never-default:                     no
ipv6.may-fail:                          yes
ipv6.ip6-privacy:                       0 (disabled)
ipv6.addr-gen-mode:                     stable-privacy
ipv6.dhcp-send-hostname:                yes
ipv6.dhcp-hostname:                     --
ipv6.token:                             --
proxy.method:                           none
proxy.browser-only:                     no
proxy.pac-url:                          --
proxy.pac-script:                       --
GENERAL.NAME:                           Wired connection 1
GENERAL.UUID:                           995000d6-3311-3674-8649-14b6d44af2e3
GENERAL.DEVICES:                        eth0
GENERAL.STATE:                          activated
GENERAL.DEFAULT:                        yes
GENERAL.DEFAULT6:                       no
GENERAL.VPN:                            no
GENERAL.ZONE:                           --
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/Settings/4
GENERAL.SPEC-OBJECT:                    --
GENERAL.MASTER-PATH:                    --
IP4.ADDRESS[1]:                         192.168.2.104/24
IP4.GATEWAY:                            192.168.2.251
IP4.DNS[1]:                             192.168.2.251
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.2.251
DHCP4.OPTION[5]:                        ip_address = 192.168.2.104
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.2.251
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.2.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 37800
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.2.251
DHCP4.OPTION[16]:                       dhcp_renewal_time = 21600
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = lan
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1527351932
DHCP4.OPTION[21]:                       host_name = steven-ge40
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.2.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 192.168.2.251
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 43200
IP6.ADDRESS[1]:                         fe80::8e89:a5ff:fe0f:cec6/64
IP6.GATEWAY:                            --

$ cat /etc/systemd/resolved.conf
#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.
#
# Entries in this file show the compile time defaults.
# You can change settings by editing this file.
# Defaults can be restored by simply deleting this file.
#
# See resolved.conf(5) for details

[Resolve]
#DNS=
#FallbackDNS=
#Domains=
#LLMNR=no
#MulticastDNS=no
DNSSEC=allow-downgrade
#Cache=yes
#DNSStubListener=yes

$ cat /run/systemd/resolve/resolv.conf 
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients directly to
# all known uplink DNS servers. This file lists all configured search domains.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

# No DNS servers known.

$ cat /run/resolvconf/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
# 127.0.0.53 is the systemd-resolved stub resolver.
# run "systemd-resolve --status" to see details about the actual nameservers.

$ ls -al /etc/resolv.conf 
lrwxrwxrwx 1 root root 29 Mar 30  2015 /etc/resolv.conf -> ../run/resolvconf/resolv.conf

$ cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
# 127.0.0.53 is the systemd-resolved stub resolver.
# run "systemd-resolve --status" to see details about the actual nameservers.


```

---

### Post by wildmanne39 on 2018-05-26
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Stronty on 2018-05-26
Ok, so my answer was:
1. Accept that systemd resolve is broken.
2. Uninstall the broken software
3. Install unbound.
4. Move on with life.

---

### Post by HNmYk3h on 2018-05-26
In my case, with my router being the dns server, the resolv.conf being linked to needed to include "nameserver 192.168.1.1" (my router address) instead of "nameserver 127.0.0.53" which somehow was setup by default.  My problem was with resolving only LAN names, but perhaps this info may be helpful.

---

### Post by scubadoo on 2018-12-16
> **HNmYk3h said:**
> In my case, with my router being the dns server, the resolv.conf being linked to needed to include "nameserver 192.168.1.1" (my router address) instead of "nameserver 127.0.0.53" which somehow was setup by default.  My problem was with resolving only LAN names, but perhaps this info may be helpful.

Thanks. That's the tip I needed. Now DNS on my LAN works. I'm not sure if the latest versions of Kubuntu needed the following fix, but I also installed Samba and libnss-winbind, then appended "wins" to the host line in /etc/nsswitch.conf.

---

