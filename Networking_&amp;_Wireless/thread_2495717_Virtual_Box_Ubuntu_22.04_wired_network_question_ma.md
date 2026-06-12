---
title: "Virtual Box Ubuntu 22.04 wired network question mark after upgraded"
date: 2024-02-28
forum: Networking &amp; Wireless
---

### Post by carlitosway on 2024-02-28
Please i have ubuntu 22.04 installed on Virtual Box 7 and it was working fine using the NAT network. I upgraded it and installed virtualmin on it which ran successfully. I am using a VPN on it for static IP. everything is all right but after rebooting when next for use, it is showing me wired network **question mark** and it is not connected to internet. Please advice on how to resolve this issue/ Thanks

this is when i ran this command ```
 sudo tail -f /var/log/syslog
Feb 28 13:00:20 smsgateway systemd[1]: NetworkManager-dispatcher.service: Deactivated successfully.
Feb 28 13:00:29 smsgateway NetworkManager[10101]: <info>  [1709121629.7050] device (enp0s3): Activation: starting connection 'Wired connection 1' (f8c2df46-eff1-3967-b0e1-4f15b8be02df)
Feb 28 13:00:29 smsgateway NetworkManager[10101]: <info>  [1709121629.7088] audit: op="connection-activate" uuid="f8c2df46-eff1-3967-b0e1-4f15b8be02df" name="Wired connection 1" pid=4442 uid=1000 result="success"
Feb 28 13:00:29 smsgateway NetworkManager[10101]: <info>  [1709121629.7097] device (enp0s3): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Feb 28 13:00:29 smsgateway NetworkManager[10101]: <info>  [1709121629.7111] manager: NetworkManager state is now CONNECTING
Feb 28 13:00:29 smsgateway NetworkManager[10101]: <info>  [1709121629.7150] device (enp0s3): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Feb 28 13:00:29 smsgateway NetworkManager[10101]: <info>  [1709121629.7580] device (enp0s3): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Feb 28 13:00:29 smsgateway NetworkManager[10101]: <info>  [1709121629.7685] dhcp4 (enp0s3): activation: beginning transaction (timeout in 45 seconds)
Feb 28 13:00:29 smsgateway NetworkManager[10101]: <info>  [1709121629.8411] dhcp4 (enp0s3): state changed new lease, address=10.0.2.15
Feb 28 13:00:29 smsgateway charon: 05[KNL] 10.0.2.15 appeared on enp0s3
Feb 28 13:00:29 smsgateway charon: 10[KNL] fe80::a64d:6629:1174:7337 appeared on enp0s3
Feb 28 13:00:29 smsgateway named[1114]: listening on IPv4 interface enp0s3, 10.0.2.15#53
Feb 28 13:00:29 smsgateway named[1114]: listening on IPv6 interface enp0s3, fe80::a64d:6629:1174:7337%2#53
Feb 28 13:00:29 smsgateway avahi-daemon[624]: Joining mDNS multicast group on interface enp0s3.IPv4 with address 10.0.2.15.
Feb 28 13:00:29 smsgateway avahi-daemon[624]: New relevant interface enp0s3.IPv4 for mDNS.
Feb 28 13:00:29 smsgateway avahi-daemon[624]: Registering new address record for 10.0.2.15 on enp0s3.IPv4.
Feb 28 13:00:29 smsgateway avahi-daemon[624]: Joining mDNS multicast group on interface enp0s3.IPv6 with address fe80::a64d:6629:1174:7337.
Feb 28 13:00:29 smsgateway avahi-daemon[624]: New relevant interface enp0s3.IPv6 for mDNS.
Feb 28 13:00:29 smsgateway avahi-daemon[624]: Registering new address record for fe80::a64d:6629:1174:7337 on enp0s3.*.
Feb 28 13:00:29 smsgateway dbus-daemon[627]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.192' (uid=0 pid=10101 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Feb 28 13:00:29 smsgateway NetworkManager[10101]: <info>  [1709121629.8682] device (enp0s3): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'managed')
Feb 28 13:00:29 smsgateway systemd[1]: Starting Network Manager Script Dispatcher Service...
Feb 28 13:00:29 smsgateway dbus-daemon[627]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb 28 13:00:29 smsgateway systemd[1]: Started Network Manager Script Dispatcher Service.
Feb 28 13:00:29 smsgateway NetworkManager[10101]: <info>  [1709121629.9036] device (enp0s3): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'managed')
Feb 28 13:00:29 smsgateway NetworkManager[10101]: <info>  [1709121629.9042] device (enp0s3): state change: secondaries -> activated (reason 'none', sys-iface-state: 'managed')
Feb 28 13:00:29 smsgateway NetworkManager[10101]: <info>  [1709121629.9081] manager: NetworkManager state is now CONNECTED_LOCAL
Feb 28 13:00:29 smsgateway NetworkManager[10101]: <info>  [1709121629.9130] manager: NetworkManager state is now CONNECTED_SITE
Feb 28 13:00:29 smsgateway NetworkManager[10101]: <info>  [1709121629.9149] policy: set 'Wired connection 1' (enp0s3) as default for IPv4 routing and DNS
Feb 28 13:00:29 smsgateway NetworkManager[10101]: <info>  [1709121629.9245] device (enp0s3): Activation: successful, device activated.
Feb 28 13:00:29 smsgateway systemd-resolved[518]: enp0s3: Bus client set default route setting: yes
Feb 28 13:00:29 smsgateway systemd-resolved[518]: enp0s3: Bus client set DNS server list to: 192.168.8.1
Feb 28 13:00:30 smsgateway systemd[1]: Reloading Postfix Mail Transport Agent (instance -)...
Feb 28 13:00:30 smsgateway postfix/postfix-script[11216]: refreshing the Postfix mail system
Feb 28 13:00:30 smsgateway postfix/master[2379]: reload -- version 3.6.4, configuration /etc/postfix
Feb 28 13:00:30 smsgateway systemd[1]: Reloaded Postfix Mail Transport Agent (instance -).
Feb 28 13:00:30 smsgateway systemd[1]: Reloading Postfix Mail Transport Agent...
Feb 28 13:00:30 smsgateway systemd[1]: Reloaded Postfix Mail Transport Agent.
Feb 28 13:00:30 smsgateway systemd[1]: Reloading Postfix Mail Transport Agent (instance -)...
Feb 28 13:00:30 smsgateway postfix/postfix-script[11243]: refreshing the Postfix mail system
Feb 28 13:00:30 smsgateway postfix/master[2379]: reload -- version 3.6.4, configuration /etc/postfix
Feb 28 13:00:30 smsgateway systemd[1]: Reloaded Postfix Mail Transport Agent (instance -).
Feb 28 13:00:30 smsgateway systemd[1]: Reloading Postfix Mail Transport Agent...
Feb 28 13:00:30 smsgateway systemd[1]: Reloaded Postfix Mail Transport Agent.
Feb 28 13:00:31 smsgateway charon: 11[KNL] flags changed for fe80::a64d:6629:1174:7337 on enp0s3
Feb 28 13:00:31 smsgateway NetworkManager[10101]: <warn>  [1709121631.7177] ndisc[0x5620324853f0,"enp0s3"]: solicit: failure sending router solicitation: Operation not permitted (1)
Feb 28 13:00:40 smsgateway systemd[1]: NetworkManager-dispatcher.service: Deactivated successfully.
Feb 28 13:00:4JUdGzvrMFDWrUUwY3toJATSeNwjn54LkCnKBPRzDuhzi5vSepH****JNxRL2gjkNrSqtCoRUrEDAgRwsQvVCjZbRyFTLRNyDmT1a1boZVunit stopped.
Feb 28 13:00:4JUdGzvrMFDWrUUwY3toJATSeNwjn54LkCnKBPRzDuhzi5vSepH****JNxRL2gjkNrSqtCoRUrEDAgRwsQvVCjZbRyFTLRNyDmT1a1boZVunit stopped.



```

---

### Post by TheFu on 2024-02-28
What does the working network look like?
What does the after reboot networking look like?
```

ip addr
ip route | column -t'
```

Make them look the same.

When posting terminal output, please, please, use code tags, not quotes.  Columns don't line up correctly.

---

### Post by carlitosway on 2024-02-29
Please i dont know how to go about this can you really guide me

---

### Post by TheFu on 2024-02-29
> **carlitosway said:**
> Please i dont know how to go about this can you really guide me

do what?

---

### Post by carlitosway on 2024-03-04
Please i still help on this issue. but let me narrow my question to: i need a complete how to on to setup l2tp on ubuntu server not desktop. Thank you.

---

