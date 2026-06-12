---
title: "After upgrade from 20.04 to 22.04 wireguard-client refuses to connect."
date: 2022-12-29
forum: Networking &amp; Wireless
---

### Post by 0z0xoo on 2022-12-29
There is one server on which Wireguard is installed and works fine, friends are connected without problems. On my laptop, the Ubuntu version 20.04 was previously installed and VPN was connected regularly. After updating to version 22.04, the laptop stopped connecting to the VPN server. I tried to completely remove Wireguard and install it again. Did not help.
Here is an excerpt from the /var/log/syslog of an unsuccessful connection.

```

Dec 29 19:00:57 zubastik NetworkManager[1308]: <info>  [1672333257.1255] vpn[0x56344d518740,4a768c18-4879-4d42-b2f4-9730c6189189,"PQ"]: starting wireguard
Dec 29 19:00:57 zubastik NetworkManager[1308]: <info>  [1672333257.1260] audit: op="connection-activate" uuid="4a768c18-4879-4d42-b2f4-9730c6189189" name="PQ" pid=2717 uid=1000 result="success"
Dec 29 19:00:57 zubastik NetworkManager[36123]: [#] ip link add PQ type wireguard
Dec 29 19:00:57 zubastik NetworkManager[36123]: [#] wg setconf PQ /dev/fd/63
Dec 29 19:00:57 zubastik NetworkManager[1308]: <info>  [1672333257.1557] manager: (PQ): new WireGuard device (/org/freedesktop/NetworkManager/Devices/14)
Dec 29 19:00:57 zubastik systemd-udevd[36136]: Using default interface naming scheme 'v249'.
Dec 29 19:00:57 zubastik NetworkManager[36123]: [#] ip -4 address add 10.0.0.2/24 dev PQ
Dec 29 19:00:57 zubastik charon: 09[KNL] 10.0.0.2 appeared on PQ
Dec 29 19:00:57 zubastik NetworkManager[36123]: [#] ip link set mtu 1420 up dev PQ
Dec 29 19:00:57 zubastik charon: 13[KNL] interface PQ activated
Dec 29 19:00:57 zubastik NetworkManager[36155]: [#] resolvconf -a tun.PQ -m 0 -x
Dec 29 19:00:57 zubastik NetworkManager[1308]: <info>  [1672333257.1684] device (PQ): state change: unmanaged -> unavailable (reason 'connection-assumed', sys-iface-state: 'external')
Dec 29 19:00:57 zubastik NetworkManager[1308]: <info>  [1672333257.1687] device (PQ): state change: unavailable -> disconnected (reason 'connection-assumed', sys-iface-state: 'external')
Dec 29 19:00:57 zubastik NetworkManager[1308]: <info>  [1672333257.1690] device (PQ): Activation: starting connection 'PQ' (2afb63b4-1802-46b7-9ff9-e35f82fb1046)
Dec 29 19:00:57 zubastik NetworkManager[1308]: <info>  [1672333257.1691] device (PQ): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'external')
Dec 29 19:00:57 zubastik NetworkManager[1308]: <info>  [1672333257.1692] device (PQ): state change: prepare -> config (reason 'none', sys-iface-state: 'external')
Dec 29 19:00:57 zubastik NetworkManager[1308]: <info>  [1672333257.1693] device (PQ): state change: config -> ip-config (reason 'none', sys-iface-state: 'external')
Dec 29 19:00:57 zubastik NetworkManager[1308]: <info>  [1672333257.1693] device (PQ): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'external')
Dec 29 19:00:57 zubastik dbus-daemon[1307]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.15' (uid=0 pid>
Dec 29 19:00:57 zubastik systemd[1]: Starting Network Manager Script Dispatcher Service...
Dec 29 19:00:57 zubastik dbus-daemon[1307]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 29 19:00:57 zubastik systemd[1]: Started Network Manager Script Dispatcher Service.
Dec 29 19:00:57 zubastik NetworkManager[1308]: <info>  [1672333257.1814] device (PQ): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'external')
Dec 29 19:00:57 zubastik NetworkManager[1308]: <info>  [1672333257.1817] device (PQ): state change: secondaries -> activated (reason 'none', sys-iface-state: 'external')
Dec 29 19:00:57 zubastik NetworkManager[1308]: <info>  [1672333257.1827] device (PQ): Activation: successful, device activated.
Dec 29 19:00:57 zubastik NetworkManager[36123]: [#] wg set PQ fwmark 51820
Dec 29 19:00:57 zubastik NetworkManager[36123]: [#] ip -4 route add 0.0.0.0/0 dev PQ table 51820
Dec 29 19:00:57 zubastik NetworkManager[36123]: [#] ip -4 rule add not fwmark 51820 table 51820
Dec 29 19:00:57 zubastik NetworkManager[36123]: [#] ip -4 rule add table main suppress_prefixlength 0
Dec 29 19:00:57 zubastik NetworkManager[36123]: [#] sysctl -q net.ipv4.conf.all.src_valid_mark=1
Dec 29 19:00:57 zubastik NetworkManager[36123]: [#] nft -f /dev/fd/63
Dec 29 19:00:57 zubastik nm-wireguard-se[36120]: g_variant_builder_add_value: assertion '!GVSB(builder)->expected_type || g_variant_is_of_type (value, GVSB(builder)->expected_type)' failed
Dec 29 19:00:57 zubastik NetworkManager[1308]: <warn>  [1672333257.1975] vpn[0x56344d518740,4a768c18-4879-4d42-b2f4-9730c6189189,"PQ",if:9,dev:3:(PQ)]: config: no VPN gateway address received
Dec 29 19:00:57 zubastik NetworkManager[1308]: <warn>  [1672333257.1976] vpn[0x56344d518740,4a768c18-4879-4d42-b2f4-9730c6189189,"PQ",if:9,dev:3:(PQ)]: did not receive valid IP config information
Dec 29 19:00:57 zubastik NetworkManager[36213]: [#] ip -4 rule delete table 51820
Dec 29 19:00:57 zubastik NetworkManager[36213]: [#] ip -4 rule delete table main suppress_prefixlength 0
Dec 29 19:00:57 zubastik NetworkManager[36213]: [#] ip link delete dev PQ
Dec 29 19:00:57 zubastik charon: 08[KNL] interface PQ deactivated
Dec 29 19:00:57 zubastik charon: 05[KNL] 10.0.0.2 disappeared from PQ
Dec 29 19:00:57 zubastik charon: 10[KNL] interface PQ deleted
Dec 29 19:00:57 zubastik NetworkManager[1308]: <info>  [1672333257.2169] device (PQ): state change: activated -> unmanaged (reason 'unmanaged', sys-iface-state: 'removed')
Dec 29 19:00:57 zubastik gnome-shell[2717]: Removing a network device that was not added
Dec 29 19:00:57 zubastik NetworkManager[36213]: [#] resolvconf -d tun.PQ -f

```

How to make wireguard-clent work?

---

### Post by 0z0xoo on 2023-06-12
The gui-shell to manage the VPN still did not work. All management had to be transferred to the console scripts.

---

