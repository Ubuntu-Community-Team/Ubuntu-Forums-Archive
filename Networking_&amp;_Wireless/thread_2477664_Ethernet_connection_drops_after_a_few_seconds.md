---
title: "Ethernet connection drops after a few seconds"
date: 2022-08-02
forum: Networking &amp; Wireless
---

### Post by chopepito on 2022-08-02
Hi everyone,

I have problems with my ethernet connection. Connection drops afters a few seconds. The problem does not occur with the wireless.

Things i've tried:

* Disable IPV6
* Use static IP and fixed DNS
* Manage the interface without NetworkManager (via /etc/network/interfaces)
* Reboot router


But nothing works!!


Info about interfaces

```

*-network                 
       description: Ethernet interface
       product: Ethernet Controller I225-V
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 02
       serial: a8:xx:xx:xx:xx:f8
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igc driverversion=5.15.0-43-generic duplex=full firmware=1045:740 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:34 memory:fc600000-fc6fffff memory:fc700000-fc703fff memory:fc500000-fc5fffff
  *-network
       description: Wireless interface
       product: Wi-Fi 6 AX200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlp7s0
       version: 1a
       serial: ac:xx:xx:xx:xx:99
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.15.0-43-generic firmware=66.f1c864e0.0 cc-a0-66.ucode ip=192.168.5.42 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:32 memory:fc400000-fc403fff


```

Logs between activate wired connection and the connection drop.

```

Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7264] active-connection[0x55bf5c4f12e0]: set device "enp4s0" [0x55bf5c4a8090]
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7264] device[55fd8a407ef8b8dd] (enp4s0): add_pending_action (1): 'activation-13'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7265] active-connection[0x55bf5c4f12e0]: constructed (NMActRequest, version-id 13, type managed)
Aug  3 02:20:10 hefesto NetworkManager[829]: <info>  [1659489610.7278] device (enp4s0): Activation: starting connection 'Wired connection 2' (91fb8de0-77bf-4f14-9eed-6b303a1fd362)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7278] device[55fd8a407ef8b8dd] (enp4s0): activation-stage: schedule activate_stage1_device_prepare
Aug  3 02:20:10 hefesto NetworkManager[829]: <info>  [1659489610.7278] audit: op="connection-activate" uuid="91fb8de0-77bf-4f14-9eed-6b303a1fd362" name="Wired connection 2" pid=2924 uid=1000 result="success"
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7278] device[55fd8a407ef8b8dd] (enp4s0): activation-stage: invoke activate_stage1_device_prepare
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7278] device[55fd8a407ef8b8dd] (enp4s0): ip4: set state pending (was none, reason: stage1)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7279] device[55fd8a407ef8b8dd] (enp4s0): ip6: set state pending (was none, reason: stage1)
Aug  3 02:20:10 hefesto NetworkManager[829]: <info>  [1659489610.7279] device (enp4s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7279] device[55fd8a407ef8b8dd] (enp4s0): add_pending_action (2): 'in-state-change'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7280] active-connection[0x55bf5c4f12e0]: set state activating (was unknown)
Aug  3 02:20:10 hefesto NetworkManager[829]: <info>  [1659489610.7281] manager: NetworkManager state is now CONNECTING
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7282] active-connection[0x55bf5c4f12e0]: check-master-ready: not signalling (state activating, no master)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7282] manager: ActivatingConnection now Wired connection 2
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7282] device[55fd8a407ef8b8dd] (enp4s0): remove_pending_action (1): 'in-state-change'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7282] device[55fd8a407ef8b8dd] (enp4s0): set-link: ignore link negotiation
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7282] device[55fd8a407ef8b8dd] (enp4s0): activation-stage: synchronously invoke activate_stage2_device_config
Aug  3 02:20:10 hefesto NetworkManager[829]: <info>  [1659489610.7282] device (enp4s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7282] device[55fd8a407ef8b8dd] (enp4s0): add_pending_action (2): 'in-state-change'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7283] device[55fd8a407ef8b8dd] (enp4s0): remove_pending_action (1): 'in-state-change'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7283] route-manager: sync routing-rule
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7283] device[55fd8a407ef8b8dd] (enp4s0): bringing up device 2
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7283] platform-linux: link: change 2: flags: set 0x1/0x1 ([up] / [up])
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7284] platform-linux: do-request-link: 2 
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7286] platform: (enp4s0) signal: link changed: 2: enp4s0 <UP,LOWER_UP;broadcast,multicast,up,running,lowerup> mtu 1500 arp 1 ethernet? init addr A8:A1:59:31:52:F8 permaddr A8:A1:59:31:52:F8 brd FF:FF:FF:FF:FF:FF driver igc rx:1578,1064758 tx:1343,192338
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7286] device[55fd8a407ef8b8dd] (enp4s0): queued link change for ifindex 2
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7286] platform-linux: do-change-link[2]: success changing link: success
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7286] device[55fd8a407ef8b8dd] (enp4s0): activation-stage: synchronously invoke activate_stage3_ip_config
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7286] firewalld: [412d02e221a47af2,change*:"enp4s0"]: firewall zone change enp4s0:default (not running, simulate success)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7287] firewalld: [412d02e221a47af2,change*:"enp4s0"]: complete: fake success
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7287] device[55fd8a407ef8b8dd] (enp4s0): activation-stage: synchronously invoke activate_stage3_ip_config
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7287] device[55fd8a407ef8b8dd] (enp4s0): ip4: required-timeout: disabled
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7287] device[55fd8a407ef8b8dd] (enp4s0): ip6: required-timeout: disabled
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7287] active-connection[0x55bf5c4f12e0]: set state-flags layer2-ready,lifetime-bound-to-profile-visibility (was lifetime-bound-to-profile-visibility)
Aug  3 02:20:10 hefesto NetworkManager[829]: <info>  [1659489610.7287] device (enp4s0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7287] device[55fd8a407ef8b8dd] (enp4s0): add_pending_action (2): 'in-state-change'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7288] device[55fd8a407ef8b8dd] (enp4s0): remove_pending_action (1): 'in-state-change'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7288] platform-linux: error reading /proc/sys/net/ipv6/conf/default/use_tempaddr: Failed to open file "/proc/sys/net/ipv6/conf/default/use_tempaddr": No such file or directory
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7288] device[55fd8a407ef8b8dd] (enp4s0): ip:manual4: set state pending
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7288] device[55fd8a407ef8b8dd] (enp4s0): ip:manual6: set state pending
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7288] device[55fd8a407ef8b8dd] (enp4s0): ip:dhcp4: set state pending (was none)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7288] device[55fd8a407ef8b8dd] (enp4s0): ipv4.dhcp-client-id: no explicit client-id configured
Aug  3 02:20:10 hefesto NetworkManager[829]: <info>  [1659489610.7289] dhcp4 (enp4s0): activation: beginning transaction (timeout in 45 seconds)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7289] platform-linux: sysctl: failed to open '/proc/sys/net/ipv6/conf/enp4s0/disable_ipv6': (2) No such file or directory
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7291] dhcp4 (enp4s0): send REQUEST to 255.255.255.255
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7291] dns-mgr: (device_l3cd_changed): queueing DNS updates (1)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7291] dns-mgr: (device_l3cd_changed): DNS configuration did not change
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7291] dns-mgr: (device_l3cd_changed): no DNS changes to commit (0)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7292] device[55fd8a407ef8b8dd] (enp4s0): ip:manual6: set state done
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7292] device[55fd8a407ef8b8dd] (enp4s0): ip:manual4: set state done
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7292] device[55fd8a407ef8b8dd] (enp4s0): ip: set (combined) state pending (was none, reason: check-ip-state)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7292] device[55fd8a407ef8b8dd] (enp4s0): ip6: set state done (was pending, reason: check-ip-state)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7292] active-connection[0x55bf5c4f12e0]: set state-flags layer2-ready,ip6-ready,lifetime-bound-to-profile-visibility (was layer2-ready,lifetime-bound-to-profile-visibility)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7326] dhcp4 (enp4s0): received ACK of 192.168.1.131 from 0.0.0.0
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7362] dhcp4 (enp4s0): option broadcast_address    => '192.168.1.255'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7362] dhcp4 (enp4s0): option dhcp_lease_time      => '86400'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7362] dhcp4 (enp4s0): option dhcp_server_identifier => '192.168.1.1'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7362] dhcp4 (enp4s0): option domain_name          => 'home'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7362] dhcp4 (enp4s0): option domain_name_servers  => '46.6.113.34 212.230.135.1'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7362] dhcp4 (enp4s0): option expiry               => '1659576010'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7362] dhcp4 (enp4s0): option ip_address           => '192.168.1.131'
Aug  3 02:20:10 hefesto avahi-daemon[824]: Joining mDNS multicast group on interface enp4s0.IPv4 with address 192.168.1.131.
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7363] dhcp4 (enp4s0): option requested_broadcast_address => '1'
Aug  3 02:20:10 hefesto charon: 12[KNL] 192.168.1.131 appeared on enp4s0
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7363] dhcp4 (enp4s0): option requested_domain_name => '1'
Aug  3 02:20:10 hefesto avahi-daemon[824]: New relevant interface enp4s0.IPv4 for mDNS.
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7363] dhcp4 (enp4s0): option requested_domain_name_servers => '1'
Aug  3 02:20:10 hefesto avahi-daemon[824]: Registering new address record for 192.168.1.131 on enp4s0.IPv4.
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7363] dhcp4 (enp4s0): option requested_domain_search => '1'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7363] dhcp4 (enp4s0): option requested_host_name  => '1'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7363] dhcp4 (enp4s0): option requested_interface_mtu => '1'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7363] dhcp4 (enp4s0): option requested_ms_classless_static_routes => '1'
Aug  3 02:20:10 hefesto dbus-daemon[827]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.2' (uid=0 pid=829 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7363] dhcp4 (enp4s0): option requested_nis_domain => '1'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7363] dhcp4 (enp4s0): option requested_nis_servers => '1'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7363] dhcp4 (enp4s0): option requested_ntp_servers => '1'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7363] dhcp4 (enp4s0): option requested_rfc3442_classless_static_routes => '1'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7363] dhcp4 (enp4s0): option requested_root_path  => '1'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7363] dhcp4 (enp4s0): option requested_routers    => '1'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7363] dhcp4 (enp4s0): option requested_static_routes => '1'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7363] dhcp4 (enp4s0): option requested_subnet_mask => '1'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7363] dhcp4 (enp4s0): option requested_time_offset => '1'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7363] dhcp4 (enp4s0): option requested_wpad       => '1'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7364] dhcp4 (enp4s0): option routers              => '192.168.1.1'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7364] dhcp4 (enp4s0): option subnet_mask          => '255.255.255.0'
Aug  3 02:20:10 hefesto NetworkManager[829]: <info>  [1659489610.7364] dhcp4 (enp4s0): state changed new lease, address=192.168.1.131
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7365] device[55fd8a407ef8b8dd] (enp4s0): set metered value 4
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7366] l3cfg[458b192119c76d03,ifindex=2]: obj-state: track: [e5556272563cfca6, ip4-address, 192.168.1.131/24 brd* 192.168.1.255 lft 86400sec pref 86400sec lifetime 1660-1660[86400,86400] dev 2 src dhcp force-commit]
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7366] l3cfg[458b192119c76d03,ifindex=2]: obj-state: track: [9d6ddf173aa46804, ip4-route, type unicast 0.0.0.0/0 via 192.168.1.1 dev 2 metric 20100 mss 0 rt-src dhcp force-commit]
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7366] l3cfg[458b192119c76d03,ifindex=2]: obj-state: track: [fb1dd95764140522, ip4-route, type unicast 192.168.1.0/24 dev 2 metric 100 mss 0 rt-src rt-kernel scope link pref-src 192.168.1.131 force-commit]
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7366] dns-mgr: (device_l3cd_changed): queueing DNS updates (1)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7366] dns-mgr: (device_l3cd_changed): DNS configuration did not change
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7366] dns-mgr: (device_l3cd_changed): no DNS changes to commit (0)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7367] l3cfg[458b192119c76d03,ifindex=2]: obj-state: configure-first-time: [e5556272563cfca6, ip4-address, 192.168.1.131/24 brd* 192.168.1.255 lft 86400sec pref 86400sec lifetime 1660-1660[86400,86400] dev 2 src dhcp force-commit], nm-configured
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7367] l3cfg[458b192119c76d03,ifindex=2]: obj-state: configure-first-time: [9d6ddf173aa46804, ip4-route, type unicast 0.0.0.0/0 via 192.168.1.1 dev 2 metric 20100 mss 0 rt-src dhcp force-commit], nm-configured
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7367] l3cfg[458b192119c76d03,ifindex=2]: obj-state: configure-first-time: [fb1dd95764140522, ip4-route, type unicast 192.168.1.0/24 dev 2 metric 100 mss 0 rt-src rt-kernel scope link pref-src 192.168.1.131 force-commit], nm-configured
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7368] platform: (enp4s0) address: adding or updating IPv4 address: 192.168.1.131/24 brd 192.168.1.255 lft 86400sec pref 86400sec lifetime 1660-0[86400,86400] dev 2 flags noprefixroute src unknown
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7369] platform: (enp4s0) signal: address 4   added: 192.168.1.131/24 brd 192.168.1.255 lft 86400sec pref 86400sec lifetime 1660-1660[86400,86400] dev 2 flags noprefixroute src kernel
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7369] l3cfg[458b192119c76d03,ifindex=2]: obj-state: appeared in platform: [e5556272563cfca6, ip4-address, 192.168.1.131/24 brd* 192.168.1.255 lft 86400sec pref 86400sec lifetime 1660-1660[86400,86400] dev 2 src dhcp force-commit], nm-configured, in-platform
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7370] platform: (enp4s0) signal: route   4   added: type local table 255 192.168.1.131/32 dev 2 metric 0 mss 0 rt-src rt-kernel scope host pref-src 192.168.1.131
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7370] platform-linux: do-add-ip4-address[2: 192.168.1.131/24]: success
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7370] platform: (enp4s0) route: append     IPv4 route: type unicast 192.168.1.0/24 dev 2 metric 100 mss 0 rt-src rt-kernel scope link pref-src 192.168.1.131 force-commit
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7371] platform: (enp4s0) signal: route   4   added: type unicast 192.168.1.0/24 dev 2 metric 100 mss 0 rt-src rt-kernel scope link pref-src 192.168.1.131
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7371] l3cfg[458b192119c76d03,ifindex=2]: obj-state: appeared in platform: [fb1dd95764140522, ip4-route, type unicast 192.168.1.0/24 dev 2 metric 100 mss 0 rt-src rt-kernel scope link pref-src 192.168.1.131 force-commit], nm-configured, in-platform
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7371] platform-linux: do-add-ip4-route[type unicast 192.168.1.0/24 dev 2 metric 100 mss 0 rt-src rt-kernel scope link pref-src 192.168.1.131 force-commit]: success
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7371] platform: (enp4s0) route: append     IPv4 route: type unicast 0.0.0.0/0 via 192.168.1.1 dev 2 metric 20100 mss 0 rt-src dhcp force-commit
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7372] platform: (enp4s0) signal: route   4   added: type unicast 0.0.0.0/0 via 192.168.1.1 dev 2 metric 20100 mss 0 rt-src rt-dhcp scope global
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7372] l3cfg[458b192119c76d03,ifindex=2]: obj-state: appeared in platform: [9d6ddf173aa46804, ip4-route, type unicast 0.0.0.0/0 via 192.168.1.1 dev 2 metric 20100 mss 0 rt-src dhcp force-commit], nm-configured, in-platform
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7372] platform-linux: do-add-ip4-route[type unicast 0.0.0.0/0 via 192.168.1.1 dev 2 metric 20100 mss 0 rt-src rt-dhcp scope global force-commit]: success
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7373] dhcp4 (enp4s0): accept address
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7374] device[55fd8a407ef8b8dd] (enp4s0): ip:dhcp4: set state done (was pending)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7374] dispatcher: (52) (enp4s0) dispatching action 'dhcp4-change'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7377] device[55fd8a407ef8b8dd] (enp4s0): ip4: set state done (was pending, reason: check-ip-state)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7377] active-connection[0x55bf5c4f12e0]: set state-flags layer2-ready,ip4-ready,ip6-ready,lifetime-bound-to-profile-visibility (was layer2-ready,ip6-ready,lifetime-bound-to-profile-visibility)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7378] device[55fd8a407ef8b8dd] (enp4s0): ip: set (combined) state done (was pending, reason: check-ip-state)
Aug  3 02:20:10 hefesto NetworkManager[829]: <info>  [1659489610.7378] device (enp4s0): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'managed')
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7378] device[55fd8a407ef8b8dd] (enp4s0): add_pending_action (2): 'in-state-change'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7379] manager: ActivatingConnection now (none)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7379] dispatcher: (53) (enp4s0) dispatching action 'pre-up' (with callback)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7381] device[55fd8a407ef8b8dd] (enp4s0): remove_pending_action (1): 'in-state-change'
Aug  3 02:20:10 hefesto systemd[1]: Starting Network Manager Script Dispatcher Service...
Aug  3 02:20:10 hefesto dbus-daemon[827]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug  3 02:20:10 hefesto systemd[1]: Started Network Manager Script Dispatcher Service.
Aug  3 02:20:10 hefesto nm-dispatcher: req:1 'dhcp4-change' [enp4s0]: new request (1 scripts)
Aug  3 02:20:10 hefesto nm-dispatcher: req:1 'dhcp4-change' [enp4s0]: environment: CONNECTION_DBUS_PATH=/org/freedesktop/NetworkManager/Settings/1
Aug  3 02:20:10 hefesto nm-dispatcher: req:1 'dhcp4-change' [enp4s0]: environment: CONNECTION_FILENAME=/etc/NetworkManager/system-connections/Wired connection 2.nmconnection
Aug  3 02:20:10 hefesto nm-dispatcher: req:1 'dhcp4-change' [enp4s0]: environment: CONNECTION_UUID=91fb8de0-77bf-4f14-9eed-6b303a1fd362
Aug  3 02:20:10 hefesto nm-dispatcher: req:1 'dhcp4-change' [enp4s0]: environment: CONNECTION_ID=Wired connection 2
Aug  3 02:20:10 hefesto nm-dispatcher: req:1 'dhcp4-change' [enp4s0]: environment: DEVICE_IFACE=enp4s0
Aug  3 02:20:10 hefesto nm-dispatcher: req:1 'dhcp4-change' [enp4s0]: environment: DEVICE_IP_IFACE=enp4s0
Aug  3 02:20:10 hefesto nm-dispatcher: req:1 'dhcp4-change' [enp4s0]: environment: PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin
Aug  3 02:20:10 hefesto nm-dispatcher: req:1 'dhcp4-change' [enp4s0]: environment: NM_DISPATCHER_ACTION=dhcp4-change
Aug  3 02:20:10 hefesto nm-dispatcher: req:1 'dhcp4-change' [enp4s0]: start running ordered scripts...
Aug  3 02:20:10 hefesto nm-dispatcher: req:1 'dhcp4-change' [enp4s0], "/etc/NetworkManager/dispatcher.d/01-ifupdown": run script
Aug  3 02:20:10 hefesto nm-dispatcher: req:2 'pre-up' [enp4s0]: new request (0 scripts)
Aug  3 02:20:10 hefesto nm-dispatcher: req:2 'pre-up' [enp4s0]: environment: CONNECTION_DBUS_PATH=/org/freedesktop/NetworkManager/Settings/1
Aug  3 02:20:10 hefesto nm-dispatcher: req:2 'pre-up' [enp4s0]: environment: CONNECTION_FILENAME=/etc/NetworkManager/system-connections/Wired connection 2.nmconnection
Aug  3 02:20:10 hefesto nm-dispatcher: req:2 'pre-up' [enp4s0]: environment: CONNECTION_UUID=91fb8de0-77bf-4f14-9eed-6b303a1fd362
Aug  3 02:20:10 hefesto nm-dispatcher: req:2 'pre-up' [enp4s0]: environment: CONNECTION_ID=Wired connection 2
Aug  3 02:20:10 hefesto nm-dispatcher: req:2 'pre-up' [enp4s0]: environment: DEVICE_IFACE=enp4s0
Aug  3 02:20:10 hefesto nm-dispatcher: req:2 'pre-up' [enp4s0]: environment: DEVICE_IP_IFACE=enp4s0
Aug  3 02:20:10 hefesto nm-dispatcher: req:2 'pre-up' [enp4s0]: environment: PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin
Aug  3 02:20:10 hefesto nm-dispatcher: req:2 'pre-up' [enp4s0]: environment: NM_DISPATCHER_ACTION=pre-up
Aug  3 02:20:10 hefesto nm-dispatcher: req:2 'pre-up' [enp4s0]: completed: no scripts
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7824] dispatcher: (53) succeeded but no scripts invoked
Aug  3 02:20:10 hefesto nm-dispatcher: req:1 'dhcp4-change' [enp4s0], "/etc/NetworkManager/dispatcher.d/01-ifupdown": complete
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7824] device[55fd8a407ef8b8dd] (enp4s0): add_pending_action (2): 'queued-state-change-secondaries'
Aug  3 02:20:10 hefesto nm-dispatcher: req:1 'dhcp4-change' [enp4s0]: completed (1 scripts)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7824] device[55fd8a407ef8b8dd] (enp4s0): queue-state[secondaries, reason:none, id:3809]: queue state change
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7824] dispatcher: (52) /etc/NetworkManager/dispatcher.d/01-ifupdown succeeded
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7824] device[55fd8a407ef8b8dd] (enp4s0): queue-state[secondaries, reason:none, id:3809]: change state
Aug  3 02:20:10 hefesto NetworkManager[829]: <info>  [1659489610.7824] device (enp4s0): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'managed')
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7824] device[55fd8a407ef8b8dd] (enp4s0): add_pending_action (3): 'in-state-change'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7825] device[55fd8a407ef8b8dd] (enp4s0): add_pending_action (4): 'queued-state-change-activated'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7825] device[55fd8a407ef8b8dd] (enp4s0): queue-state[activated, reason:none, id:3810]: queue state change
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7825] device[55fd8a407ef8b8dd] (enp4s0): device entered SECONDARIES state
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7825] device[55fd8a407ef8b8dd] (enp4s0): remove_pending_action (3): 'in-state-change'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7825] device[55fd8a407ef8b8dd] (enp4s0): remove_pending_action (2): 'queued-state-change-secondaries'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7825] device[55fd8a407ef8b8dd] (enp4s0): queue-state[activated, reason:none, id:3810]: change state
Aug  3 02:20:10 hefesto NetworkManager[829]: <info>  [1659489610.7826] device (enp4s0): state change: secondaries -> activated (reason 'none', sys-iface-state: 'managed')
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7826] device[55fd8a407ef8b8dd] (enp4s0): add_pending_action (3): 'in-state-change'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7826] active-connection[0x55bf5c4f12e0]: set state activated (was activating)
Aug  3 02:20:10 hefesto NetworkManager[829]: <info>  [1659489610.7827] manager: NetworkManager state is now CONNECTED_LOCAL
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7827] active-connection[0x55bf5c4f12e0]: check-master-ready: not signalling (state activated, no master)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7827] device[55fd8a407ef8b8dd] (enp4s0): remove_pending_action (2): 'activation-13'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7828] dns-mgr: (device_state_changed): queueing DNS updates (1)
Aug  3 02:20:10 hefesto NetworkManager[829]: <info>  [1659489610.7828] manager: NetworkManager state is now CONNECTED_SITE
Aug  3 02:20:10 hefesto NetworkManager[829]: <info>  [1659489610.7828] policy: set 'Wired connection 2' (enp4s0) as default for IPv4 routing and DNS
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7829] manager: PrimaryConnection now Wired connection 2
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7829] manager: new metered value: 4
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7829] dns-mgr: (device_state_changed): DNS configuration changed
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7829] dns-mgr: (device_state_changed): committing DNS changes (0)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7829] dns-mgr: update-dns: not updating resolv.conf
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7829] dns-mgr: update-dns: updating plugin systemd-resolved
Aug  3 02:20:10 hefesto NetworkManager[829]: <info>  [1659489610.7832] device (enp4s0): Activation: successful, device activated.
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7832] dispatcher: (54) (enp4s0) dispatching action 'up'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7834] connectivity: (enp4s0,IPv4,374) start request to 'http://connectivity-check.ubuntu.com./' (try resolving 'connectivity-check.ubuntu.com.' using systemd-resolved)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7834] connectivity: (enp4s0,IPv6,375) skip connectivity check due to no IP address configured
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7834] device[55fd8a407ef8b8dd] (enp4s0): remove_pending_action (1): 'in-state-change'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7834] device[55fd8a407ef8b8dd] (enp4s0): remove_pending_action (0): 'queued-state-change-activated'
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7834] connectivity: (enp4s0,IPv6,375) check completed: NONE; no IP address configured
Aug  3 02:20:10 hefesto systemd-resolved[756]: enp4s0: Bus client set search domain list to: home
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: new request (1 scripts)
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: CONNECTION_DBUS_PATH=/org/freedesktop/NetworkManager/Settings/1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: CONNECTION_FILENAME=/etc/NetworkManager/system-connections/Wired connection 2.nmconnection
Aug  3 02:20:10 hefesto systemd-resolved[756]: enp4s0: Bus client set default route setting: yes
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: CONNECTION_UUID=91fb8de0-77bf-4f14-9eed-6b303a1fd362
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: CONNECTION_ID=Wired connection 2
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DEVICE_IFACE=enp4s0
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DEVICE_IP_IFACE=enp4s0
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: IP4_ADDRESS_0=192.168.1.131/24 192.168.1.1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: IP4_NUM_ADDRESSES=1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: IP4_GATEWAY=192.168.1.1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: IP4_NAMESERVERS=8.8.8.8 46.6.113.34 212.230.135.1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: IP4_DOMAINS=home
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: IP4_ROUTE_0=192.168.1.0/24 0.0.0.0 100
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: IP4_NUM_ROUTES=1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: IP6_GATEWAY=0.0.0.0
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_BROADCAST_ADDRESS=192.168.1.255
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_DHCP_LEASE_TIME=86400
Aug  3 02:20:10 hefesto systemd-resolved[756]: enp4s0: Bus client set DNS server list to: 8.8.8.8, 46.6.113.34, 212.230.135.1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_DHCP_SERVER_IDENTIFIER=192.168.1.1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_DOMAIN_NAME=home
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_DOMAIN_NAME_SERVERS=46.6.113.34 212.230.135.1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_EXPIRY=1659576010
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_IP_ADDRESS=192.168.1.131
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_REQUESTED_BROADCAST_ADDRESS=1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_REQUESTED_DOMAIN_NAME=1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_REQUESTED_DOMAIN_NAME_SERVERS=1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_REQUESTED_DOMAIN_SEARCH=1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_REQUESTED_HOST_NAME=1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_REQUESTED_INTERFACE_MTU=1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_REQUESTED_MS_CLASSLESS_STATIC_ROUTES=1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_REQUESTED_NIS_DOMAIN=1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_REQUESTED_NIS_SERVERS=1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_REQUESTED_NTP_SERVERS=1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_REQUESTED_RFC3442_CLASSLESS_STATIC_ROUTES=1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_REQUESTED_ROOT_PATH=1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_REQUESTED_ROUTERS=1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_REQUESTED_STATIC_ROUTES=1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_REQUESTED_SUBNET_MASK=1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_REQUESTED_TIME_OFFSET=1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_REQUESTED_WPAD=1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_ROUTERS=192.168.1.1
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: DHCP4_SUBNET_MASK=255.255.255.0
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: environment: NM_DISPATCHER_ACTION=up
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: start running ordered scripts...
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0], "/etc/NetworkManager/dispatcher.d/01-ifupdown": run script
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7870] platform: (enp4s0) signal: route   4   added: type unicast 169.254.0.0/16 dev 2 metric 1000 mss 0 rt-src rt-boot scope link
Aug  3 02:20:10 hefesto nm-dispatcher[9435]: /etc/network/if-up.d/resolved: 12: mystatedir: not found
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0], "/etc/NetworkManager/dispatcher.d/01-ifupdown": complete
Aug  3 02:20:10 hefesto nm-dispatcher: req:3 'up' [enp4s0]: completed (1 scripts)
Aug  3 02:20:10 hefesto NetworkManager[829]: <debug> [1659489610.7927] dispatcher: (54) /etc/NetworkManager/dispatcher.d/01-ifupdown succeeded
Aug  3 02:20:11 hefesto goa-daemon[1190]: secret_password_lookup_sync() returned NULL
Aug  3 02:20:11 hefesto NetworkManager[829]: <debug> [1659489611.7846] connectivity: (enp4s0,IPv4,376) start request to 'http://connectivity-check.ubuntu.com./' (try resolving 'connectivity-check.ubuntu.com.' using systemd-resolved)
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0888] connectivity: (enp4s0,IPv4,376) check completed: FULL; status header found
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0889] device[55fd8a407ef8b8dd] (enp4s0): connectivity state changed from NONE to FULL
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0889] manager: connectivity checking indicates FULL
Aug  3 02:20:12 hefesto NetworkManager[829]: <info>  [1659489612.0889] manager: NetworkManager state is now CONNECTED_GLOBAL
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0890] dispatcher: (55) dispatching action 'connectivity-change'
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0891] l3cfg[458b192119c76d03,ifindex=2]: obj-state: update: [e5556272563cfca6, ip4-address, 192.168.1.131/24 brd* 192.168.1.255 lft 86399sec pref 86399sec lifetime 1661-1660[86400,86400] dev 2 src dhcp], nm-configured, in-platform
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0891] l3cfg[458b192119c76d03,ifindex=2]: obj-state: track: [ffd43bf5bc5d6643, ip4-route, type unicast 0.0.0.0/0 via 192.168.1.1 dev 2 metric 100 mss 0 rt-src dhcp]
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0891] l3cfg[458b192119c76d03,ifindex=2]: obj-state: update: [fb1dd95764140522, ip4-route, type unicast 192.168.1.0/24 dev 2 metric 100 mss 0 rt-src rt-kernel scope link pref-src 192.168.1.131], nm-configured, in-platform
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0891] l3cfg[458b192119c76d03,ifindex=2]: obj-state: now zombie: [9d6ddf173aa46804, ip4-route, type unicast 0.0.0.0/0 via 192.168.1.1 dev 2 metric 20100 mss 0 rt-src dhcp force-commit], zombie[5], nm-configured, in-platform
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0891] dns-mgr: (device_l3cd_changed): queueing DNS updates (1)
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0891] dns-mgr: (device_l3cd_changed): DNS configuration did not change
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0891] dns-mgr: (device_l3cd_changed): no DNS changes to commit (0)
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0891] l3cfg[458b192119c76d03,ifindex=2]: obj-state: configure-first-time: [ffd43bf5bc5d6643, ip4-route, type unicast 0.0.0.0/0 via 192.168.1.1 dev 2 metric 100 mss 0 rt-src dhcp], nm-configured
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0891] l3cfg[458b192119c76d03,ifindex=2]: obj-state: prune zombie: [9d6ddf173aa46804, ip4-route, type unicast 0.0.0.0/0 via 192.168.1.1 dev 2 metric 20100 mss 0 rt-src dhcp force-commit], zombie[4], nm-configured, in-platform
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0892] platform: (enp4s0) address: adding or updating IPv4 address: 192.168.1.131/24 brd 192.168.1.255 lft 86399sec pref 86399sec lifetime 1661-0[86399,86399] dev 2 flags noprefixroute src unknown
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0892] platform: (enp4s0) signal: address 4 changed: 192.168.1.131/24 brd 192.168.1.255 lft 86399sec pref 86399sec lifetime 1661-1661[86399,86399] dev 2 flags noprefixroute src kernel
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0892] l3cfg[458b192119c76d03,ifindex=2]: obj-state: appeared in platform: [e5556272563cfca6, ip4-address, 192.168.1.131/24 brd* 192.168.1.255 lft 86399sec pref 86399sec lifetime 1661-1660[86400,86400] dev 2 src dhcp], nm-configured, in-platform
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0892] platform-linux: do-add-ip4-address[2: 192.168.1.131/24]: success
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0893] platform: (enp4s0) route: append     IPv4 route: type unicast 0.0.0.0/0 via 192.168.1.1 dev 2 metric 100 mss 0 rt-src dhcp
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0893] platform: (enp4s0) signal: route   4   added: type unicast 0.0.0.0/0 via 192.168.1.1 dev 2 metric 100 mss 0 rt-src rt-dhcp scope global
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0893] l3cfg[458b192119c76d03,ifindex=2]: obj-state: appeared in platform: [ffd43bf5bc5d6643, ip4-route, type unicast 0.0.0.0/0 via 192.168.1.1 dev 2 metric 100 mss 0 rt-src dhcp], nm-configured, in-platform
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0894] platform-linux: do-add-ip4-route[type unicast 0.0.0.0/0 via 192.168.1.1 dev 2 metric 100 mss 0 rt-src rt-dhcp scope global]: success
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0894] platform: (enp4s0) ip4-route: delete type unicast 0.0.0.0/0 via 192.168.1.1 dev 2 metric 20100 mss 0 rt-src dhcp force-commit
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0894] platform: (enp4s0) signal: route   4 removed: type unicast 0.0.0.0/0 via 192.168.1.1 dev 2 metric 20100 mss 0 rt-src rt-dhcp scope global
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0894] l3cfg[458b192119c76d03,ifindex=2]: obj-state: zombie gone (untrack): [9d6ddf173aa46804, ip4-route, type unicast 0.0.0.0/0 via 192.168.1.1 dev 2 metric 20100 mss 0 rt-src dhcp force-commit], nm-configured, was-in-platform
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0894] platform-linux: do-delete-ip4-route[type unicast 0.0.0.0/0 via 192.168.1.1 dev 2 metric 20100 mss 0 rt-src dhcp force-commit]: success
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0895] connectivity: (enp4s0,IPv4,374) check completed: CANCELLED; cancelled
Aug  3 02:20:12 hefesto nm-dispatcher: req:4 'connectivity-change': new request (1 scripts)
Aug  3 02:20:12 hefesto nm-dispatcher: req:4 'connectivity-change': environment: CONNECTIVITY_STATE=FULL
Aug  3 02:20:12 hefesto nm-dispatcher: req:4 'connectivity-change': environment: PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin
Aug  3 02:20:12 hefesto nm-dispatcher: req:4 'connectivity-change': environment: NM_DISPATCHER_ACTION=connectivity-change
Aug  3 02:20:12 hefesto nm-dispatcher: req:4 'connectivity-change': start running ordered scripts...
Aug  3 02:20:12 hefesto nm-dispatcher: req:4 'connectivity-change', "/etc/NetworkManager/dispatcher.d/01-ifupdown": run script
Aug  3 02:20:12 hefesto nm-dispatcher: req:4 'connectivity-change', "/etc/NetworkManager/dispatcher.d/01-ifupdown": complete
Aug  3 02:20:12 hefesto nm-dispatcher: req:4 'connectivity-change': completed (1 scripts)
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.0916] dispatcher: (55) /etc/NetworkManager/dispatcher.d/01-ifupdown succeeded
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.7828] connectivity: (enp4s0,IPv6,377) skip connectivity check due to no IP address configured
Aug  3 02:20:12 hefesto NetworkManager[829]: <debug> [1659489612.7828] connectivity: (enp4s0,IPv6,377) check completed: NONE; no IP address configured
Aug  3 02:20:13 hefesto NetworkManager[829]: <debug> [1659489613.2876] connectivity: (wlp7s0,IPv6,378) skip connectivity check due to no carrier
Aug  3 02:20:13 hefesto NetworkManager[829]: <debug> [1659489613.2876] connectivity: (wlp7s0,IPv6,378) check completed: NONE; no carrier
Aug  3 02:20:13 hefesto goa-daemon[1190]: secret_password_lookup_sync() returned NULL
Aug  3 02:20:14 hefesto NetworkManager[829]: <debug> [1659489614.2890] connectivity: (wlp7s0,IPv4,379) skip connectivity check due to no carrier
Aug  3 02:20:14 hefesto NetworkManager[829]: <debug> [1659489614.2891] connectivity: (wlp7s0,IPv4,379) check completed: NONE; no carrier
Aug  3 02:20:14 hefesto goa-daemon[1190]: secret_password_lookup_sync() returned NULL
Aug  3 02:20:16 hefesto NetworkManager[829]: <debug> [1659489616.7835] connectivity: (enp4s0,IPv6,380) skip connectivity check due to no IP address configured
Aug  3 02:20:16 hefesto NetworkManager[829]: <debug> [1659489616.7835] connectivity: (enp4s0,IPv6,380) check completed: NONE; no IP address configured
Aug  3 02:20:22 hefesto systemd[1]: NetworkManager-dispatcher.service: Deactivated successfully.


```

Ubuntu 22.04.1 LTS

Please, help me! I'm losing faith in linux!!
Thanks

---

