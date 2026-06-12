---
title: "l2tp error - VPN connection: failed to connect: 'invalid ipsec-gateway-id '"
date: 2018-05-23
forum: Networking &amp; Wireless
---

### Post by I-Broke-It on 2018-05-23
Hi, This used to work but it stopped when I upgraded to 18.04. 
I installed the network-manager-l2tp from library. But get the message "connection failed : activation of network connection failed" when I try to connect.

In the log I get the following. 
<info>  [1527077191.9305] settings-connection[0x55ef5221c360,015a4e3a-613d-425d-80c9-407a95a6b7a4]: write: successfully updated (keyfile: update /etc/NetworkManager/system-connections/AZvpn (015a4e3a-613d-425d-80c9-407a95a6b7a4,"AZvpn"))
<info>  [1527077191.9310] audit: op="connection-update" uuid="015a4e3a-613d-425d-80c9-407a95a6b7a4" name="AZvpn" args="vpn.data" pid=4488 uid=1000 result="success"
<info>  [1527077198.3196] vpn-connection[0x55ef523be160,015a4e3a-613d-425d-80c9-407a95a6b7a4,"AZvpn",0]: Started the VPN service, PID 7588
<info>  [1527077198.3196] vpn-connection[0x55ef523be160,015a4e3a-613d-425d-80c9-407a95a6b7a4,"AZvpn",0]: Started the VPN service, PID 7588
<info>  [1527077198.3196] vpn-connection[0x55ef523be160,015a4e3a-613d-425d-80c9-407a95a6b7a4,"AZvpn",0]: Started the VPN service, PID 7588
<warn>  [1527077198.3458] vpn-connection[0x55ef523be160,015a4e3a-613d-425d-80c9-407a95a6b7a4,"AZvpn",0]: VPN connection: failed to connect: 'invalid ipsec-gateway-id 'ipsec-gateway-id''
<info>  [1527077198.3482] vpn-connection[0x55ef523be160,015a4e3a-613d-425d-80c9-407a95a6b7a4,"AZvpn",0]: VPN plugin: state changed: stopped (6)
<info>  [1527077198.3482] vpn-connection[0x55ef523be160,015a4e3a-613d-425d-80c9-407a95a6b7a4,"AZvpn",0]: VPN plugin: state changed: stopped (6)

Please help with what is wrong and ow can I fix it. It was google and me for two days now and still no love.
Thanks.

---

### Post by dkosovic on 2018-05-24
> **I-Broke-It said:**
> 
<warn>  [1527077198.3458] vpn-connection[0x55ef523be160,015a4e3a-613d-425d-80c9-407a95a6b7a4,"AZvpn",0]: VPN connection: failed to connect: 'invalid ipsec-gateway-id 'ipsec-gateway-id''

If I'm reading that warning correctly, for the Gateway ID in the IPsec Options dialog box, you entered 'ipsec-gateway-id' ?

The Gateway ID is the peer's IP address and is primarily used when errors in regards to the peer ID occur, e.g. in some cases when it is NAT'ed.
 
Try leaving the Gateway ID blank.

---

### Post by I-Broke-It on 2018-05-24
Thanks dkosovic. I did your change it appears to connect and then fails. Please see log below. 

May 24 21:40:00 steven-HP systemd[1]: Starting Message of the Day...
May 24 21:40:00 steven-HP systemd[1]: Started Message of the Day.
May 24 21:42:20 steven-HP dhclient[990]: DHCPREQUEST of 10.0.0.244 on wlo1 to 10.0.0.1 port 67 (xid=0x6cc8bf3a)
May 24 21:42:20 steven-HP dhclient[990]: DHCPACK of 10.0.0.244 from 10.0.0.1
May 24 21:42:20 steven-HP NetworkManager[799]: <info>  [1527190940.9068] dhcp4 (wlo1):   address 10.0.0.244
May 24 21:42:20 steven-HP NetworkManager[799]: <info>  [1527190940.9069] dhcp4 (wlo1):   plen 24 (255.255.255.0)
May 24 21:42:20 steven-HP NetworkManager[799]: <info>  [1527190940.9069] dhcp4 (wlo1):   gateway 10.0.0.1
May 24 21:42:20 steven-HP NetworkManager[799]: <info>  [1527190940.9070] dhcp4 (wlo1):   lease time 600
May 24 21:42:20 steven-HP NetworkManager[799]: <info>  [1527190940.9071] dhcp4 (wlo1):   nameserver '8.8.8.8'
May 24 21:42:20 steven-HP NetworkManager[799]: <info>  [1527190940.9072] dhcp4 (wlo1):   nameserver '8.8.4.4'
May 24 21:42:20 steven-HP NetworkManager[799]: <info>  [1527190940.9072] dhcp4 (wlo1): state changed bound -> bound
May 24 21:42:20 steven-HP dbus-daemon[752]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.11' (uid=0 pid=799 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
May 24 21:42:20 steven-HP systemd[1]: Starting Network Manager Script Dispatcher Service...
May 24 21:42:20 steven-HP dhclient[990]: bound to 10.0.0.244 -- renewal in 240 seconds.
May 24 21:42:20 steven-HP dbus-daemon[752]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 24 21:42:20 steven-HP systemd[1]: Started Network Manager Script Dispatcher Service.
May 24 21:42:20 steven-HP nm-dispatcher: req:1 'dhcp4-change' [wlo1]: new request (1 scripts)
May 24 21:42:20 steven-HP nm-dispatcher: req:1 'dhcp4-change' [wlo1]: start running ordered scripts...
May 24 21:42:34 steven-HP gnome-logs[1875]: Error creating IO channel for /proc/self/mountinfo: Permission denied (g-file-error-quark, 2)
May 24 21:42:34 steven-HP kernel: [ 2743.103930] audit: type=1400 audit(1527190954.705:78): apparmor="DENIED" operation="open" profile="snap.gnome-logs.gnome-logs" name="/proc/1875/mountinfo" pid=1875 comm="gmain" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
May 24 21:42:34 steven-HP kernel: [ 2743.104056] audit: type=1400 audit(1527190954.705:79): apparmor="DENIED" operation="open" profile="snap.gnome-logs.gnome-logs" name="/etc/fstab" pid=1875 comm="gnome-logs" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
May 24 21:42:34 steven-HP kernel: [ 2743.104099] audit: type=1400 audit(1527190954.705:80): apparmor="DENIED" operation="open" profile="snap.gnome-logs.gnome-logs" name="/proc/1875/mountinfo" pid=1875 comm="gnome-logs" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
May 24 21:42:34 steven-HP kernel: [ 2743.104144] audit: type=1400 audit(1527190954.705:81): apparmor="DENIED" operation="open" profile="snap.gnome-logs.gnome-logs" name="/proc/1875/mounts" pid=1875 comm="gnome-logs" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
May 24 21:42:34 steven-HP dbus-daemon[752]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.122' (uid=1000 pid=1875 comm="gnome-logs " label="snap.gnome-logs.gnome-logs (enforce)")
May 24 21:42:34 steven-HP kernel: [ 2743.221519] audit: type=1400 audit(1527190954.821:82): apparmor="DENIED" operation="open" profile="snap.gnome-logs.gnome-logs" name="/proc/1875/mountinfo" pid=1875 comm="gnome-logs" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
May 24 21:42:34 steven-HP kernel: [ 2743.221539] audit: type=1400 audit(1527190954.821:83): apparmor="DENIED" operation="open" profile="snap.gnome-logs.gnome-logs" name="/proc/1875/mounts" pid=1875 comm="gnome-logs" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
May 24 21:42:34 steven-HP kernel: [ 2743.224872] audit: type=1400 audit(1527190954.825:84): apparmor="DENIED" operation="open" profile="snap.gnome-logs.gnome-logs" name="/home/steven/.bash_logout" pid=1875 comm="pool" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
May 24 21:42:34 steven-HP kernel: [ 2743.224936] audit: type=1400 audit(1527190954.825:85): apparmor="DENIED" operation="open" profile="snap.gnome-logs.gnome-logs" name="/home/steven/.bashrc" pid=1875 comm="pool" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
May 24 21:42:34 steven-HP kernel: [ 2743.224978] audit: type=1400 audit(1527190954.825:86): apparmor="DENIED" operation="open" profile="snap.gnome-logs.gnome-logs" name="/home/steven/.profile" pid=1875 comm="pool" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
May 24 21:42:34 steven-HP kernel: [ 2743.225031] audit: type=1400 audit(1527190954.825:87): apparmor="DENIED" operation="open" profile="snap.gnome-logs.gnome-logs" name="/home/steven/.xsession-errors" pid=1875 comm="pool" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
May 24 21:42:34 steven-HP systemd[1]: Starting Hostname Service...
May 24 21:42:35 steven-HP dbus-daemon[752]: [system] Successfully activated service 'org.freedesktop.hostname1'
May 24 21:42:35 steven-HP systemd[1]: Started Hostname Service.
May 24 21:42:42 steven-HP kernel: [ 2751.358199] kauditd_printk_skb: 26 callbacks suppressed
May 24 21:42:42 steven-HP kernel: [ 2751.358203] audit: type=1400 audit(1527190962.957:114): apparmor="DENIED" operation="open" profile="snap.gnome-logs.gnome-logs" name="/proc/1875/mountinfo" pid=1875 comm="gnome-logs" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
May 24 21:42:42 steven-HP kernel: [ 2751.358215] audit: type=1400 audit(1527190962.957:115): apparmor="DENIED" operation="open" profile="snap.gnome-logs.gnome-logs" name="/proc/1875/mounts" pid=1875 comm="gnome-logs" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
May 24 21:46:20 steven-HP dhclient[990]: DHCPREQUEST of 10.0.0.244 on wlo1 to 10.0.0.1 port 67 (xid=0x6cc8bf3a)
May 24 21:46:20 steven-HP dhclient[990]: DHCPACK of 10.0.0.244 from 10.0.0.1
May 24 21:46:20 steven-HP NetworkManager[799]: <info>  [1527191180.8944] dhcp4 (wlo1):   address 10.0.0.244
May 24 21:46:20 steven-HP NetworkManager[799]: <info>  [1527191180.8945] dhcp4 (wlo1):   plen 24 (255.255.255.0)
May 24 21:46:20 steven-HP NetworkManager[799]: <info>  [1527191180.8945] dhcp4 (wlo1):   gateway 10.0.0.1
May 24 21:46:20 steven-HP NetworkManager[799]: <info>  [1527191180.8945] dhcp4 (wlo1):   lease time 600
May 24 21:46:20 steven-HP NetworkManager[799]: <info>  [1527191180.8946] dhcp4 (wlo1):   nameserver '8.8.8.8'
May 24 21:46:20 steven-HP NetworkManager[799]: <info>  [1527191180.8946] dhcp4 (wlo1):   nameserver '8.8.4.4'
May 24 21:46:20 steven-HP NetworkManager[799]: <info>  [1527191180.8946] dhcp4 (wlo1): state changed bound -> bound
May 24 21:46:20 steven-HP dbus-daemon[752]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.11' (uid=0 pid=799 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
May 24 21:46:20 steven-HP systemd[1]: Starting Network Manager Script Dispatcher Service...
May 24 21:46:20 steven-HP dhclient[990]: bound to 10.0.0.244 -- renewal in 283 seconds.
May 24 21:46:20 steven-HP dbus-daemon[752]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 24 21:46:20 steven-HP systemd[1]: Started Network Manager Script Dispatcher Service.
May 24 21:46:20 steven-HP nm-dispatcher: req:1 'dhcp4-change' [wlo1]: new request (1 scripts)
May 24 21:46:20 steven-HP nm-dispatcher: req:1 'dhcp4-change' [wlo1]: start running ordered scripts...
May 24 21:51:03 steven-HP dhclient[990]: DHCPREQUEST of 10.0.0.244 on wlo1 to 10.0.0.1 port 67 (xid=0x6cc8bf3a)
May 24 21:51:03 steven-HP dhclient[990]: DHCPACK of 10.0.0.244 from 10.0.0.1
May 24 21:51:03 steven-HP NetworkManager[799]: <info>  [1527191463.5147] dhcp4 (wlo1):   address 10.0.0.244
May 24 21:51:03 steven-HP NetworkManager[799]: <info>  [1527191463.5148] dhcp4 (wlo1):   plen 24 (255.255.255.0)
May 24 21:51:03 steven-HP NetworkManager[799]: <info>  [1527191463.5148] dhcp4 (wlo1):   gateway 10.0.0.1
May 24 21:51:03 steven-HP NetworkManager[799]: <info>  [1527191463.5149] dhcp4 (wlo1):   lease time 600
May 24 21:51:03 steven-HP NetworkManager[799]: <info>  [1527191463.5149] dhcp4 (wlo1):   nameserver '8.8.8.8'
May 24 21:51:03 steven-HP NetworkManager[799]: <info>  [1527191463.5149] dhcp4 (wlo1):   nameserver '8.8.4.4'
May 24 21:51:03 steven-HP NetworkManager[799]: <info>  [1527191463.5150] dhcp4 (wlo1): state changed bound -> bound
May 24 21:51:03 steven-HP dbus-daemon[752]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.11' (uid=0 pid=799 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
May 24 21:51:03 steven-HP systemd[1]: Starting Network Manager Script Dispatcher Service...
May 24 21:51:03 steven-HP dhclient[990]: bound to 10.0.0.244 -- renewal in 240 seconds.
May 24 21:51:03 steven-HP dbus-daemon[752]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 24 21:51:03 steven-HP systemd[1]: Started Network Manager Script Dispatcher Service.
May 24 21:51:03 steven-HP nm-dispatcher: req:1 'dhcp4-change' [wlo1]: new request (1 scripts)
May 24 21:51:03 steven-HP nm-dispatcher: req:1 'dhcp4-change' [wlo1]: start running ordered scripts...
May 24 21:55:03 steven-HP dhclient[990]: DHCPREQUEST of 10.0.0.244 on wlo1 to 10.0.0.1 port 67 (xid=0x6cc8bf3a)
May 24 21:55:03 steven-HP dhclient[990]: DHCPACK of 10.0.0.244 from 10.0.0.1
May 24 21:55:03 steven-HP NetworkManager[799]: <info>  [1527191703.8920] dhcp4 (wlo1):   address 10.0.0.244
May 24 21:55:03 steven-HP NetworkManager[799]: <info>  [1527191703.8921] dhcp4 (wlo1):   plen 24 (255.255.255.0)
May 24 21:55:03 steven-HP NetworkManager[799]: <info>  [1527191703.8921] dhcp4 (wlo1):   gateway 10.0.0.1
May 24 21:55:03 steven-HP NetworkManager[799]: <info>  [1527191703.8922] dhcp4 (wlo1):   lease time 600
May 24 21:55:03 steven-HP NetworkManager[799]: <info>  [1527191703.8922] dhcp4 (wlo1):   nameserver '8.8.8.8'
May 24 21:55:03 steven-HP NetworkManager[799]: <info>  [1527191703.8922] dhcp4 (wlo1):   nameserver '8.8.4.4'
May 24 21:55:03 steven-HP NetworkManager[799]: <info>  [1527191703.8922] dhcp4 (wlo1): state changed bound -> bound
May 24 21:55:03 steven-HP dbus-daemon[752]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.11' (uid=0 pid=799 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
May 24 21:55:03 steven-HP systemd[1]: Starting Network Manager Script Dispatcher Service...
May 24 21:55:03 steven-HP dhclient[990]: bound to 10.0.0.244 -- renewal in 248 seconds.
May 24 21:55:03 steven-HP dbus-daemon[752]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 24 21:55:03 steven-HP systemd[1]: Started Network Manager Script Dispatcher Service.
May 24 21:55:03 steven-HP nm-dispatcher: req:1 'dhcp4-change' [wlo1]: new request (1 scripts)
May 24 21:55:03 steven-HP nm-dispatcher: req:1 'dhcp4-change' [wlo1]: start running ordered scripts...
May 24 21:55:13 steven-HP gvfsd[1351]: mkdir failed on directory /var/cache/samba: Permission denied
May 24 21:55:14 steven-HP gvfsd[1351]: message repeated 3 times: [ mkdir failed on directory /var/cache/samba: Permission denied]
May 24 21:55:14 steven-HP gvfsd-metadata[1683]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
May 24 21:55:14 steven-HP gvfsd-metadata[1683]: message repeated 7 times: [ g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed]
May 24 21:55:15 steven-HP gvfsd[1351]: mkdir failed on directory /var/cache/samba: Permission denied

---

### Post by dkosovic on 2018-05-25
In your latest log output I don't see anything that has do with network-manager-l2tp, strongswan or xl2tpd.

I'm guessing you are seeing a "[FONT=lucida console]udp_xmit failed ... with err=-1:No such device"[/FONT] error with xl2tpd in the logs, as kernel 4.15 breaks xl2tpd < 1.3.12, see:
[LIST]
[*][https://github.com/nm-l2tp/network-manager-l2tp/issues/79](https://github.com/nm-l2tp/network-manager-l2tp/issues/79)
[*][https://github.com/xelerance/xl2tpd/issues/147](https://github.com/xelerance/xl2tpd/issues/147)
[*][https://bugs.launchpad.net/ubuntu/+source/xl2tpd/+bug/1760796](https://bugs.launchpad.net/ubuntu/+source/xl2tpd/+bug/1760796)
[/LIST]
I would recommend voting for the above Ubuntu 18.04 xl2tpd launchpad bug so it gets more attention and they might backport the patch and fix it.

If you can't wait, you can build a working xl2tp from source by issuing the following :
```
sudo apt install build-essential git libpcap0.8-dev
sudo systemctl stop xl2tpd
git clone https://github.com/xelerance/xl2tpd.git
cd xl2tpd
make
sudo cp xl2tpd /usr/sbin/xl2tpd
```

---

### Post by I-Broke-It on 2018-05-29
Thanks dkosovic,
I have tried the build but get the the same message. Please see log below.

11:10:00 gdm-x-session: See [https://wayland.freedesktop.org/libinput/doc/1.10.4//absolute_coordinate_ranges.html](https://wayland.freedesktop.org/libinput/doc/1.10.4//absolute_coordinate_ranges.html) for details
11:09:39 dbus-daemon: [session uid=120 pid=924] Successfully activated service 'ca.desrt.dconf'
11:09:39 NetworkManager: <warn>  [1527584979.4273] vpn-connection[0x55b2fa728220,015a4e3a-613d-425d-80c9-407a95a6b7a4,"AZvpn",0]: VPN connection: failed to connect: 'Message recipient disconnected from message bus without replying'
11:09:39 nm-l2tp-service: g_dbus_method_invocation_take_error: assertion 'error != NULL' failed
11:09:39 starter: ipsec starter stopped
11:09:39 NetworkManager: destroying IKE_SA in state CONNECTING without notification
11:09:39 starter: 

11:09:39 charon: 00[IKE] destroying IKE_SA in state CONNECTING without notification
11:09:39 NetworkManager: Stopping strongSwan IPsec...
11:09:35 gnome-shell: [AppIndicatorSupport-DEBUG] Registering StatusNotifierItem :1.67/org/ayatana/NotificationItem/software_update_available
11:09:33 charon: 12[NET] sending packet: from 172.20.199.116[500] to 41.160.224.115[500] (240 bytes)
11:09:28 starter: charon (2420) started after 20 ms
11:09:28 charon: 00[JOB] spawning 16 worker threads
11:09:28 starter: Attempting to start charon...
11:09:28 starter: Loading conn '015a4e3a-613d-425d-80c9-407a95a6b7a4'
11:09:28 NetworkManager: Loading conn '015a4e3a-613d-425d-80c9-407a95a6b7a4'
11:09:26 starter: ipsec starter stopped
11:09:26 NetworkManager: Stopping strongSwan IPsec...
11:09:26 nm-l2tp-service: Check port 1701
11:09:26 NetworkManager: <info>  [1527584966.1022] vpn-connection[0x55b2fa728220,015a4e3a-613d-425d-80c9-407a95a6b7a4,"AZvpn",0]: VPN connection: (ConnectInteractive) reply received
11:08:56 pulseaudio: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
11:08:56 dbus-daemon: [system] Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
11:08:42 packagekitd: get-details transaction /213_ebcbcaba from uid 1000 finished with success after 572ms
11:08:36 systemd: Started Firmware update daemon.
11:08:36 dbus-daemon: [system] Successfully activated service 'org.freedesktop.fwupd'
11:08:35 fwupd: Daemon ready for requests
11:08:35 systemd: Starting Firmware update daemon...
11:08:35 dbus-daemon: [system] Activating via systemd: service name='org.freedesktop.fwupd' unit='fwupd.service' requested by ':1.105' (uid=1000 pid=1959 comm="/usr/bin/gnome-software --gapplication-service " label="unconfined")
11:08:35 gnome-shell: GNOME Shell started at Tue May 29 2018 11:08:32 GMT+0200 (SAST)
11:08:35 gnome-software: disabled plugins: dpkg, repos, dummy, odrs, epiphany
11:08:34 gnome-shell: Window manager warning: Overwriting existing binding of keysym 73 with keysym 73 (keycode 27).
11:08:34 systemd: Started Virtual filesystem metadata service.
11:08:34 dbus-daemon: [session uid=1000 pid=1652] Successfully activated service 'org.gtk.vfs.Metadata'
11:08:34 systemd: Starting Virtual filesystem metadata service...
11:08:34 dbus-daemon: [session uid=1000 pid=1652] Activating via systemd: service name='org.gtk.vfs.Metadata' unit='gvfs-metadata.service' requested by ':1.48' (uid=1000 pid=1950 comm="nautilus-desktop " label="unconfined")
11:08:34 nautilus-deskto: Can not determine workarea, guessing at layout
11:08:34 systemd: Started Evolution address book service.
11:08:34 dbus-daemon: [session uid=1000 pid=1652] Successfully activated service 'org.gnome.evolution.dataserver.AddressBook9'
11:08:34 systemd: Starting Evolution address book service...
11:08:34 dbus-daemon: [session uid=1000 pid=1652] Activating via systemd: service name='org.gnome.evolution.dataserver.AddressBook9' unit='evolution-addressbook-factory.service' requested by ':1.56' (uid=1000 pid=2021 comm="/usr/lib/evolution/evolution-calendar-factory-subp" label="unconfined")
11:08:34 gsd-color: failed to set screen _ICC_PROFILE: Failed to open file &#8220;/home/steven/.local/share/icc/edid-063f6082f99a72fd8465cd75d61c95c5.icc&#8221;: Permission denied
11:08:33 gnome-shell: nma_mobile_providers_database_lookup_cdma_sid: assertion 'sid > 0' failed
11:08:33 systemd: Started Evolution calendar service.
11:08:33 dbus-daemon: [session uid=1000 pid=1652] Successfully activated service 'org.gnome.evolution.dataserver.Calendar7'
11:08:33 gnome-shell: Error looking up permission: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.impl.portal.PermissionStore was not provided by any .service files
11:08:33 dbus-daemon: [session uid=1000 pid=1652] Successfully activated service 'ca.desrt.dconf'
11:08:33 systemd: Started Locale Service.
11:08:33 dbus-daemon: [system] Successfully activated service 'org.freedesktop.locale1'
11:08:33 systemd: Starting Evolution calendar service...
11:08:33 dbus-daemon: [session uid=1000 pid=1652] Activating via systemd: service name='org.gnome.evolution.dataserver.Calendar7' unit='evolution-calendar-factory.service' requested by ':1.19' (uid=1000 pid=1809 comm="/usr/lib/gnome-shell/gnome-shell-calendar-server " label="unconfined")
11:08:33 systemd: Starting Locale Service...

---

### Post by dkosovic on 2018-05-30
Looks like strongswan (charon) is having issues and network-manager-l2tp killed it after a 10 second timeout, it didn't even get to xl2tpd's L2TP connection

Have a look at the "Issue with VPN servers only proposing IPsec IKEv1 weak legacy algorithms" section of the README.md file :

[LIST]
[*] [https://github.com/nm-l2tp/network-manager-l2tp/blob/nm-1-2/README.md](https://github.com/nm-l2tp/network-manager-l2tp/blob/nm-1-2/README.md) 
[/LIST]

Running the mentioned ike-scan.sh script indicates that the VPN server you are connecting to only has a single proposal which happen to have weak algorithms :

```

$ sudo ipsec stop
$ sudo ./ike-scan.sh 41.160.224.115 | grep SA
SA=(Enc=3DES Hash=SHA1 Auth=PSK Group=2:modp1024 LifeType=Seconds LifeDuration(4)=0x00007080)
```

See the example workaround for 3DES, SHA1 and MODP1024 broken algorithms at the end of the aforementioned README.md file for the phase 1 and 2 settings you'll need to use in the IPsec Options dialog box.

---

### Post by I-Broke-It on 2018-06-01
Hi I am now getting another error. Thanks for the help again At least we are not stuck on one spot.
 
My settings are:
Phase 1 Algorithm : 3des-sha1;modp1024
Phase 2 Algorithm : 3des-sha1

The log is as follows. 

13:12:39 gdm-x-session: See [https://wayland.freedesktop.org/libinput/doc/1.10.4//absolute_coordinate_ranges.html](https://wayland.freedesktop.org/libinput/doc/1.10.4//absolute_coordinate_ranges.html) for details
13:12:37 pulseaudio: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
13:12:37 dbus-daemon: [system] Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
13:12:27 NetworkManager: <warn>  [1527851547.3569] vpn-connection[0x557b8330c160,015a4e3a-613d-425d-80c9-407a95a6b7a4,"AZvpn",0]: VPN connection: failed to connect: 'Message recipient disconnected from message bus without replying'
13:12:27 nm-l2tp-service: g_dbus_method_invocation_take_error: assertion 'error != NULL' failed
13:12:27 starter: ipsec starter stopped
13:12:27 charon: 00[DMN] signal of type SIGINT received. Shutting down
13:12:27 NetworkManager: Stopping strongSwan IPsec...
13:12:26 charon: 09[CFG] no config named '015a4e3a-613d-425d-80c9-407a95a6b7a4'
13:12:25 starter: charon (5696) started after 20 ms
13:12:25 charon: 00[JOB] spawning 16 worker threads
13:12:25 starter: Attempting to start charon...
13:12:25 starter: Loading conn '015a4e3a-613d-425d-80c9-407a95a6b7a4'
13:12:25 NetworkManager: Loading conn '015a4e3a-613d-425d-80c9-407a95a6b7a4'
13:12:24 packagekitd: get-details transaction /253_dcadbbaa from uid 1000 finished with success after 473ms
13:12:23 starter: ipsec starter stopped
13:12:23 NetworkManager: Stopping strongSwan IPsec...
13:12:23 nm-l2tp-service: Check port 1701
13:12:23 NetworkManager: <info>  [1527851543.7750] vpn-connection[0x557b8330c160,015a4e3a-613d-425d-80c9-407a95a6b7a4,"AZvpn",0]: VPN connection: (ConnectInteractive) reply received
13:12:23 packagekitd: search-file transaction /252_adcaceca from uid 1000 finished with success after 494ms
13:12:17 systemd: Started Firmware update daemon.
13:12:17 dbus-daemon: [system] Successfully activated service 'org.freedesktop.fwupd'
13:12:17 fwupd: Daemon ready for requests
13:12:16 systemd: Starting Firmware update daemon...
13:12:16 dbus-daemon: [system] Activating via systemd: service name='org.freedesktop.fwupd' unit='fwupd.service' requested by ':1.124' (uid=1000 pid=5466 comm="/usr/bin/gnome-software --gapplication-service " label="unconfined")
13:12:16 gnome-shell: GNOME Shell started at Fri Jun 01 2018 13:12:13 GMT+0200 (SAST)
13:12:16 gnome-software: disabled plugins: dpkg, repos, dummy, odrs, epiphany
13:12:16 gnome-shell: Window manager warning: Overwriting existing binding of keysym 73 with keysym 73 (keycode 27).
13:12:16 systemd: Started Virtual filesystem metadata service.
13:12:16 dbus-daemon: [session uid=1000 pid=5161] Successfully activated service 'org.gtk.vfs.Metadata'
13:12:16 systemd: Starting Virtual filesystem metadata service...
13:12:16 dbus-daemon: [session uid=1000 pid=5161] Activating via systemd: service name='org.gtk.vfs.Metadata' unit='gvfs-metadata.service' requested by ':1.47' (uid=1000 pid=5460 comm="nautilus-desktop " label="unconfined")
13:12:15 nautilus-deskto: Can not determine workarea, guessing at layout
13:12:15 systemd: Started Evolution address book service.
13:12:15 dbus-daemon: [session uid=1000 pid=5161] Successfully activated service 'org.gnome.evolution.dataserver.AddressBook9'
13:12:15 systemd: Starting Evolution address book service...
13:12:15 dbus-daemon: [session uid=1000 pid=5161] Activating via systemd: service name='org.gnome.evolution.dataserver.AddressBook9' unit='evolution-addressbook-factory.service' requested by ':1.56' (uid=1000 pid=5526 comm="/usr/lib/evolution/evolution-calendar-factory-subp" label="unconfined")
13:12:15 gsd-color: failed to set screen _ICC_PROFILE: Failed to open file &#8220;/home/steven/.local/share/icc/edid-063f6082f99a72fd8465cd75d61c95c5.icc&#8221;: Permission denied
13:12:15 gnome-shell: Error looking up permission: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.impl.portal.PermissionStore was not provided by any .service files
13:12:14 systemd: Started Evolution calendar service.
13:12:14 dbus-daemon: [session uid=1000 pid=5161] Successfully activated service 'org.gnome.evolution.dataserver.Calendar7'
13:12:14 systemd: Started Locale Service.
13:12:14 dbus-daemon: [system] Successfully activated service 'org.freedesktop.locale1'
13:12:14 systemd: Starting Evolution calendar service...
13:12:14 dbus-daemon: [session uid=1000 pid=5161] Activating via systemd: service name='org.gnome.evolution.dataserver.Calendar7' unit='evolution-calendar-factory.service' requested by ':1.19' (uid=1000 pid=5319 comm="/usr/lib/gnome-shell/gnome-shell-calendar-server " label="unconfined")
13:12:14 systemd: Starting Locale Service...
13:12:14 dbus-daemon: [system] Activating via systemd: service name='org.freedesktop.locale1' unit='dbus-org.freedesktop.locale1.service' requested by ':1.122' (uid=1000 pid=5417 comm="/usr/lib/gnome-settings-daemon/gsd-keyboard " label="unconfined")
13:12:14 kernel: rfkill: input handler disabled
13:12:14 systemd: Started Hostname Service.
13:12:14 dbus-daemon: [system] Successfully activated service 'org.freedesktop.hostname1'
13:12:14 gnome-session-b: Entering running state

---

### Post by I-Broke-It on 2018-06-01
> **I-Broke-It said:**
> Hi I am now getting another error. Thanks for the help again At least we are not stuck on one spot.
 
My settings are:
Phase 1 Algorithm : 3des-sha1;modp1024
Phase 2 Algorithm : 3des-sha1


Found it. This is what it was supposed to be

Phase 1 Algorithm : 3des-sha1-modp1024
Phase 2 Algorithm : 3des-sha1

The docs said the first one for version 3 and up me being 5 but it needed to be the second one for versions before 3.

Thanks again for the help. It is working now.

---

### Post by dkosovic on 2018-06-03
Glad to hear you got it going.

It's not different versions, but different IPsec services, *3des-sha1;modp1024* syntax with the semicolon is for **libreswan**, while the *3des-sha1-modp1024* syntax is for **strongswan** which is what you are using.

---

