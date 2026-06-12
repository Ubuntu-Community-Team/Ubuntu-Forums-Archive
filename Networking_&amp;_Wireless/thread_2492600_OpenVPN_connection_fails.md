---
title: "OpenVPN connection fails"
date: 2023-11-16
forum: Networking &amp; Wireless
---

### Post by m-knichel on 2023-11-16
I have a wifi router that I connect to using openvpn from a windows computer just fine.  On my Ubuntu 22.04 box, I try and it fails.  Here is the syslog...
Can anyone assist?
```

Nov 16 17:09:16 GAZELLE openvpn3-service-logger[9009]: {tag:6962079989068143817} Parsed single-use configuration 'AES_OpenVPN_Config.ovpn', owner: {username}
Nov 16 17:09:16 GAZELLE dbus-daemon[791]: [system] Activating service name='net.openvpn.v3.backends' requested by ':1.264' (uid=129 pid=14417 comm="/usr/libexec/openvpn3-linux/openvpn3-service-sessi") (using servicehelper)
Nov 16 17:09:16 GAZELLE net.openvpn.v3.backends[14868]: OpenVPN3/Linux v21 (openvpn3-service-backendstart)
Nov 16 17:09:16 GAZELLE net.openvpn.v3.backends[14868]: OpenVPN core v3.8.2 linux x86_64 64-bit
Nov 16 17:09:16 GAZELLE net.openvpn.v3.backends[14868]: Copyright (C) 2012-2022 OpenVPN Inc. All rights reserved.
Nov 16 17:09:16 GAZELLE openvpn3-service-logger[9009]: Attached: {tag:9740437318184287136}  [:1.302/net.openvpn.v3.backends], pid 14868
Nov 16 17:09:16 GAZELLE dbus-daemon[791]: [system] Successfully activated service 'net.openvpn.v3.backends'
Nov 16 17:09:16 GAZELLE net.openvpn.v3.backends[14872]: Re-initiated process from pid 14872 to backend process pid 14873
Nov 16 17:09:16 GAZELLE net.openvpn.v3.backends[14873]: OpenVPN3/Linux v21 (openvpn3-service-client)
Nov 16 17:09:16 GAZELLE net.openvpn.v3.backends[14873]: OpenVPN core v3.8.2 linux x86_64 64-bit
Nov 16 17:09:16 GAZELLE net.openvpn.v3.backends[14873]: Copyright (C) 2012-2022 OpenVPN Inc. All rights reserved.
Nov 16 17:09:16 GAZELLE openvpn3-service-logger[9009]: Attached: {tag:18180910694788984475}  [:1.303/net.openvpn.v3.backends], pid 14873
Nov 16 17:09:16 GAZELLE openvpn3-service-logger[9009]: Attached: {tag:7020386408546455466}  [:1.303/net.openvpn.v3.sessions], pid 14873
Nov 16 17:09:16 GAZELLE openvpn3-service-logger[9009]: Assigned session /net/openvpn/v3/sessions/6c67dcfbs2edas45ees81b0sbf54bf4192a1 to {tag:18180910694788984475}
Nov 16 17:09:20 GAZELLE openvpn3-servic[14873]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Nov 16 17:09:22 GAZELLE openvpn3-service-logger[9009]: Detached: {tag:9740437318184287136}  [:1.302/net.openvpn.v3.backends], pid 14868
Nov 16 17:09:23 GAZELLE openvpn3-servic[14873]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Nov 16 17:09:23 GAZELLE openvpn3-service-logger[9009]: {tag:4624804669324031858} Cleaning up resources for PID 14873.
Nov 16 17:09:23 GAZELLE openvpn3-service-logger[9009]: {tag:18180910694788984475} Starting connection
Nov 16 17:09:23 GAZELLE openvpn3-service-logger[9009]: {tag:4624804669324031858} Socket protect called for socket 8, remote: '69.42.142.54', tun: '', ipv6: no
Nov 16 17:09:23 GAZELLE openvpn3-service-logger[9009]: {tag:18180910694788984475} Connecting
Nov 16 17:09:23 GAZELLE openvpn3-service-logger[9009]: {tag:4624804669324031858} Virtual device 'ca49a0abt4dcet4de6t8b26ta925b75047bb' registered on /net/openvpn/v3/netcfg/14873_ca49a0abt4dcet4de6t8b26ta925b75047bb (owner uid 129, owner pid 14873)
Nov 16 17:09:23 GAZELLE openvpn3-service-logger[9009]: {tag:4624804669324031858} Adding IP Address 10.8.0.10/30 gw 10.8.0.9 ipv6: no
Nov 16 17:09:23 GAZELLE openvpn3-service-logger[9009]: {tag:4624804669324031858} Setting remote IP address to 69.42.142.54 ipv6: no
Nov 16 17:09:23 GAZELLE openvpn3-service-logger[9009]: {tag:4624804669324031858} Adding network '192.168.1.0/24' excl: no ipv6: no
Nov 16 17:09:23 GAZELLE openvpn3-service-logger[9009]: {tag:4624804669324031858} Adding network '192.168.1.1/32' excl: no ipv6: no
Nov 16 17:09:23 GAZELLE openvpn3-service-logger[9009]: {tag:4624804669324031858} Adding network '10.8.0.1/32' excl: no ipv6: no
Nov 16 17:09:23 GAZELLE acvpnagent[842]: A new network interface has been detected.
Nov 16 17:09:23 GAZELLE acvpnagent[842]: IP addresses from active interfaces: tun0: 10.8.0.10, FE80:0:0:0:7045:DFA2:4931:7B3C wlp0s20f3: 192.168.6.251, FE80:0:0:0:740D:1517:80A9:5DF0 
Nov 16 17:09:23 GAZELLE NetworkManager[793]: <info>  [1700172563.7133] manager: (tun0): new Tun device (/org/freedesktop/NetworkManager/Devices/8)
Nov 16 17:09:23 GAZELLE systemd-udevd[14881]: Using default interface naming scheme 'v249'.
Nov 16 17:09:23 GAZELLE NetworkManager[793]: <info>  [1700172563.7231] device (tun0): state change: unmanaged -> unavailable (reason 'connection-assumed', sys-iface-state: 'external')
Nov 16 17:09:23 GAZELLE NetworkManager[793]: <info>  [1700172563.7235] device (tun0): state change: unavailable -> disconnected (reason 'connection-assumed', sys-iface-state: 'external')
Nov 16 17:09:23 GAZELLE systemd-resolved[704]: tun0: Bus client set DNS server list to: 192.168.1.1
Nov 16 17:09:23 GAZELLE NetworkManager[793]: <info>  [1700172563.7248] device (tun0): Activation: starting connection 'tun0' (da0c8392-fc01-430d-9759-5d49c36fcc79)
Nov 16 17:09:23 GAZELLE NetworkManager[793]: <info>  [1700172563.7272] device (tun0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'external')
Nov 16 17:09:23 GAZELLE NetworkManager[793]: <info>  [1700172563.7276] device (tun0): state change: prepare -> config (reason 'none', sys-iface-state: 'external')
Nov 16 17:09:23 GAZELLE NetworkManager[793]: <info>  [1700172563.7279] device (tun0): state change: config -> ip-config (reason 'none', sys-iface-state: 'external')
Nov 16 17:09:23 GAZELLE NetworkManager[793]: <info>  [1700172563.7282] device (tun0): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'external')
Nov 16 17:09:23 GAZELLE dbus-daemon[791]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.11' (uid=0 pid=793 comm="/usr/sbin/NetworkManager --no-daemon ")
Nov 16 17:09:23 GAZELLE systemd-resolved[704]: tun0: Bus client set search domain list to: ~.
Nov 16 17:09:23 GAZELLE systemd[1]: Starting Network Manager Script Dispatcher Service...
Nov 16 17:09:23 GAZELLE systemd-resolved[704]: tun0: Bus client set default route setting: yes
Nov 16 17:09:23 GAZELLE openvpn3-service-logger[9009]: {tag:18180910694788984475} Connected: *username@domainname.net*:1183 (*remote.ip.addresss*) via /UDP on tun/10.8.0.10/ gw=[10.8.0.9/] mtu=(default)
Nov 16 17:09:23 GAZELLE openvpn3-service-logger[9009]: {tag:18180910694788984475} [COMPRESS_ERROR] server pushed compression settings that are not allowed and will result in a non-working connection. 
Nov 16 17:09:23 GAZELLE openvpn3-service-logger[9009]: {tag:18180910694788984475} Disconnected
Nov 16 17:09:23 GAZELLE openvpn3-service-logger[9009]: {tag:4624804669324031858} Device 'tun0' was removed by openvpn
Nov 16 17:09:23 GAZELLE acvpnagent[842]: Function: getInterfacesInternal File: ../../vpn/Common/Utility/NetInterface_unix.cpp Line: 1725 Invoked Function: ioctl SIOCGIFNETMASK Return Code: 99 (0x00000063) Description: unknown failed to retrieve mask for interface tun0 (address 10.8.0.10): Cannot assign requested address
Nov 16 17:09:23 GAZELLE acvpnagent[842]: A network interface address has gone down.
Nov 16 17:09:23 GAZELLE acvpnagent[842]: IP addresses from active interfaces: tun0: FE80:0:0:0:7045:DFA2:4931:7B3C wlp0s20f3: 192.168.6.251, FE80:0:0:0:740D:1517:80A9:5DF0 
Nov 16 17:09:23 GAZELLE dbus-daemon[791]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Nov 16 17:09:23 GAZELLE acvpnagent[842]: A network interface has gone down.
Nov 16 17:09:23 GAZELLE acvpnagent[842]: IP addresses from active interfaces: wlp0s20f3: 192.168.6.251, FE80:0:0:0:740D:1517:80A9:5DF0 
Nov 16 17:09:23 GAZELLE systemd[1]: Started Network Manager Script Dispatcher Service.
Nov 16 17:09:23 GAZELLE NetworkManager[793]: <info>  [1700172563.7711] device (tun0): state change: ip-check -> unmanaged (reason 'connection-assumed', sys-iface-state: 'external')
Nov 16 17:09:23 GAZELLE openvpn3-service-logger[9009]: {tag:4624804669324031858} Cleaning up resources for PID 14873.
Nov 16 17:09:26 GAZELLE openvpn3-service-logger[9009]: Detached: {tag:18180910694788984475}  [:1.303/net.openvpn.v3.backends], pid 14873
Nov 16 17:09:26 GAZELLE openvpn3-service-logger[9009]: Unexpected Detach call from :1.303, pid not found for this sender
Nov 16 17:09:26 GAZELLE openvpn3-service-logger[9009]: Detached: {tag:7020386408546455466}  [:1.303/net.openvpn.v3.sessions]
Nov 16 17:09:28 GAZELLE acvpnagent[842]: Function: determinePublicAddrCandidateFromDefRoute File: ../../vpn/AgentUtilities/HostConfigMgr.cpp Line: 3057 Invoked Function: CHostConfigMgr::FindDefaultRouteInterface Return Code: -22806495 (0xFEA40021) Description: ROUTETABLE_ERROR_GETBESTROUTE_FAILED IPv6
Nov 16 17:09:28 GAZELLE acvpnagent[842]: Function: updatePotentialPublicAddresses File: ../../vpn/AgentUtilities/HostConfigMgr.cpp Line: 3190 Invoked Function: CHostConfigMgr::determinePublicAddrCandidateFromDefRoute Return Code: -22806495 (0xFEA40021) Description: ROUTETABLE_ERROR_GETBESTROUTE_FAILED IPv6
Nov 16 17:09:28 GAZELLE acvpnagent[842]: Function: logProbeFailure File: ../../vpn/Agent/NetEnvironment.cpp Line: 1599 The HTTPS probe to 151.103.1.5 resulted in a redirect.
Nov 16 17:09:28 GAZELLE acvpnagent[842]: Function: InitNSS File: ../../vpn/CommonCrypt/Certificates/NSSCertUtils.cpp Line: 343 Invoked Function: CNSSCertUtils::getCertDBPath Return Code: -31457278 (0xFE200002) Description: CERTSTORE_ERROR_BAD_PARAMETER 
Nov 16 17:09:28 GAZELLE acvpnagent[842]: Function: CNSSCertStore File: ../../vpn/CommonCrypt/Certificates/NSSCertStore.cpp Line: 52 Invoked Function: CNSSCertUtils::InitNSS Return Code: -31457278 (0xFE200002) Description: CERTSTORE_ERROR_BAD_PARAMETER 
Nov 16 17:09:28 GAZELLE acvpnagent[842]: Function: addNSSStore File: ../../vpn/CommonCrypt/Certificates/CollectiveCertStore.cpp Line: 1910 Invoked Function: CNSSCertStore::CNSSCertStore Return Code: -31457278 (0xFE200002) Description: CERTSTORE_ERROR_BAD_PARAMETER 
Nov 16 17:09:28 GAZELLE acvpnagent[842]: Function: OpenStores File: ../../vpn/CommonCrypt/Certificates/CollectiveCertStore.cpp Line: 469 Invoked Function: CCollectiveCertStore::addNSSStore Return Code: -31457278 (0xFE200002) Description: CERTSTORE_ERROR_BAD_PARAMETER 
Nov 16 17:09:28 GAZELLE acvpnagent[842]: Function: analyzeHttpResponse File: ../../vpn/Agent/NetEnvironment.cpp Line: 1813 SG (151.103.1.5) contacted
Nov 16 17:09:33 GAZELLE systemd[1]: NetworkManager-dispatcher.service: Deactivated successfully.
Nov 16 17:09:46 GAZELLE systemd[1]: systemd-hostnamed.service: Deactivated successfully.

```

---

### Post by #&amp;thj^% on 2023-11-16
Would help us and you if you ran it against a debug : [https://support.openvpn.com/hc/en-us/articles/360062146312-Collecting-logs-with-openvpn3-client-in-Linux-machine-with-debug-level-6-enabled](https://support.openvpn.com/hc/en-us/articles/360062146312-Collecting-logs-with-openvpn3-client-in-Linux-machine-with-debug-level-6-enabled)

---

