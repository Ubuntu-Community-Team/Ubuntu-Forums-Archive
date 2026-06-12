---
title: "VPN Connection Failed '...because the VPN service stopped'"
date: 2017-05-20
forum: Networking &amp; Wireless
---

### Post by ubantuwannabe on 2017-05-20
Dear all,

I'm using yury@ubuntu-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:        16.04
Codename:       xenial
```

yury@ubuntu-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:        16.04
Codename:       xenial

```

with reference to [https://askubuntu.com/questions/891393/vpn-pptp-in-ubuntu-16-04-not-working](https://askubuntu.com/questions/891393/vpn-pptp-in-ubuntu-16-04-not-working)

I've have the same error messgae, and thought that the above link can helpful, but it did not help me.

I've already done what is being referenced in the above url

here's my error log

```


yury@ubuntu-desktop:~$ tail -f /var/log/syslog
May 21 01:51:59 ubuntu-desktop NetworkManager[880]: <info>  [1495302719.4945] manager: (ppp0): new Generic device (/org/freedesktop/NetworkManager/Devices/6)
May 21 01:51:59 ubuntu-desktop pptp[3182]: anon log[main:pptp.c:350]: The synchronous pptp option is NOT activated
May 21 01:51:59 ubuntu-desktop NetworkManager[880]: <info>  [1495302719.5234] devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 21 01:51:59 ubuntu-desktop NetworkManager[880]: <info>  [1495302719.5237] device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
May 21 01:51:59 ubuntu-desktop pptp[3197]: anon log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 1 'Start-Control-Connection-Request'
May 21 01:52:00 ubuntu-desktop pptp[3197]: anon log[ctrlp_disp:pptp_ctrl.c:781]: Received Start Control Connection Reply
May 21 01:52:00 ubuntu-desktop pptp[3197]: anon log[ctrlp_disp:pptp_ctrl.c:815]: Client connection established.
May 21 01:52:00 ubuntu-desktop pptp[3197]: anon log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 7 'Outgoing-Call-Request'
May 21 01:52:01 ubuntu-desktop pptp[3197]: anon log[ctrlp_disp:pptp_ctrl.c:900]: Received Outgoing Call Reply.
May 21 01:52:01 ubuntu-desktop pptp[3197]: anon log[ctrlp_disp:pptp_ctrl.c:939]: Outgoing call established (call ID 12418, peer's call ID 265).
May 21 01:52:10 ubuntu-desktop NetworkManager[880]: <info>  [1495302730.2295] audit: op="connection-activate" uuid="ab172dac-26b6-41f8-9584-9f4f40d9b672" name="jumo" pid=2027 uid=1000 result="success"
May 21 01:52:10 ubuntu-desktop NetworkManager[880]: <info>  [1495302730.2467] vpn-connection[0xa3c5f0,ab172dac-26b6-41f8-9584-9f4f40d9b672,"jumo",0]: Started the VPN service, PID 3201
May 21 01:52:10 ubuntu-desktop NetworkManager[880]: <info>  [1495302730.2755] vpn-connection[0xa3c5f0,ab172dac-26b6-41f8-9584-9f4f40d9b672,"jumo",0]: Saw the service appear; activating connection
May 21 01:52:10 ubuntu-desktop gnome-session[1789]: Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
May 21 01:52:30 ubuntu-desktop pppd[3180]: LCP: timeout sending Config-Requests
May 21 01:52:30 ubuntu-desktop pppd[3180]: Connection terminated.
May 21 01:52:30 ubuntu-desktop NetworkManager[880]: <error> [1495302750.5182] platform-linux: do-change-link[7]: failure changing link: failure 19 (No such device)
May 21 01:52:30 ubuntu-desktop NetworkManager[880]: <warn>  [1495302750.5182] device (ppp0): failed to disable userspace IPv6LL address handling
May 21 01:52:30 ubuntu-desktop systemd[1]: snapd.refresh.timer: Adding 3h 45min 10.211861s random time.
May 21 01:52:30 ubuntu-desktop pppd[3180]: Modem hangup
May 21 01:52:30 ubuntu-desktop pptp[3182]: anon warn[decaps_hdlc:pptp_gre.c:220]: short read (-1): Input/output error
May 21 01:52:30 ubuntu-desktop pptp[3182]: anon warn[decaps_hdlc:pptp_gre.c:232]: pppd may have shutdown, see pppd log
May 21 01:52:30 ubuntu-desktop pppd[3180]: Exit.
May 21 01:52:30 ubuntu-desktop pptp[3197]: anon log[callmgr_main:pptp_callmgr.c:245]: Closing connection (unhandled)
May 21 01:52:30 ubuntu-desktop pptp[3197]: anon log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 12 'Call-Clear-Request'
May 21 01:52:30 ubuntu-desktop pptp[3197]: anon log[call_callback:pptp_callmgr.c:84]: Closing connection (call state)
May 21 01:52:30 ubuntu-desktop NetworkManager[880]: <info>  [1495302750.5469] devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 21 01:52:32 ubuntu-desktop NetworkManager[880]: <info>  [1495302752.5618] keyfile: update /etc/NetworkManager/system-connections/jumo (ab172dac-26b6-41f8-9584-9f4f40d9b672,"jumo")
May 21 01:52:32 ubuntu-desktop NetworkManager[880]: <info>  [1495302752.5788] vpn-connection[0xa3c5f0,ab172dac-26b6-41f8-9584-9f4f40d9b672,"jumo",0]: VPN connection: (ConnectInteractive) reply received
May 21 01:52:32 ubuntu-desktop NetworkManager[880]: ** Message: pppd started with pid 3222
May 21 01:52:32 ubuntu-desktop NetworkManager[880]: <info>  [1495302752.6106] vpn-connection[0xa3c5f0,ab172dac-26b6-41f8-9584-9f4f40d9b672,"jumo",0]: VPN plugin: state changed: starting (3)
May 21 01:52:32 ubuntu-desktop pppd[3222]: Plugin /usr/lib/pppd/2.4.7/nm-pptp-pppd-plugin.so loaded.
May 21 01:52:32 ubuntu-desktop NetworkManager[880]: Plugin /usr/lib/pppd/2.4.7/nm-pptp-pppd-plugin.so loaded.
May 21 01:52:32 ubuntu-desktop NetworkManager[880]: ** Message: nm-pptp-ppp-plugin: (plugin_init): initializing
May 21 01:52:32 ubuntu-desktop pppd[3222]: pppd 2.4.7 started by root, uid 0
May 21 01:52:32 ubuntu-desktop NetworkManager[880]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 3 / phase 'serial connection'
May 21 01:52:32 ubuntu-desktop NetworkManager[880]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
May 21 01:52:32 ubuntu-desktop NetworkManager[880]: <info>  [1495302752.6500] manager: (ppp0): new Generic device (/org/freedesktop/NetworkManager/Devices/7)
May 21 01:52:32 ubuntu-desktop pppd[3222]: Using interface ppp0
May 21 01:52:32 ubuntu-desktop NetworkManager[880]: Using interface ppp0
May 21 01:52:32 ubuntu-desktop pppd[3222]: Connect: ppp0 <--> /dev/pts/19
May 21 01:52:32 ubuntu-desktop NetworkManager[880]: Connect: ppp0 <--> /dev/pts/19
May 21 01:52:32 ubuntu-desktop NetworkManager[880]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
May 21 01:52:32 ubuntu-desktop NetworkManager[880]: <info>  [1495302752.6722] devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 21 01:52:32 ubuntu-desktop NetworkManager[880]: <info>  [1495302752.6724] device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
May 21 01:52:32 ubuntu-desktop pptp[3238]: nm-pptp-service-3201 log[main:pptp.c:350]: The synchronous pptp option is NOT activated
May 21 01:52:32 ubuntu-desktop pptp[3244]: nm-pptp-service-3201 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 1 'Start-Control-Connection-Request'
May 21 01:52:33 ubuntu-desktop pptp[3244]: nm-pptp-service-3201 log[ctrlp_disp:pptp_ctrl.c:781]: Received Start Control Connection Reply
May 21 01:52:33 ubuntu-desktop pptp[3244]: nm-pptp-service-3201 log[ctrlp_disp:pptp_ctrl.c:815]: Client connection established.
May 21 01:52:33 ubuntu-desktop pptp[3244]: nm-pptp-service-3201 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 7 'Outgoing-Call-Request'
May 21 01:52:34 ubuntu-desktop pptp[3244]: nm-pptp-service-3201 log[ctrlp_disp:pptp_ctrl.c:900]: Received Outgoing Call Reply.
May 21 01:52:34 ubuntu-desktop pptp[3244]: nm-pptp-service-3201 log[ctrlp_disp:pptp_ctrl.c:939]: Outgoing call established (call ID 11168, peer's call ID 266).
May 21 01:53:03 ubuntu-desktop pppd[3222]: LCP: timeout sending Config-Requests
May 21 01:53:03 ubuntu-desktop NetworkManager[880]: LCP: timeout sending Config-Requests
May 21 01:53:03 ubuntu-desktop NetworkManager[880]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 11 / phase 'disconnect'
May 21 01:53:03 ubuntu-desktop NetworkManager[880]: Connection terminated.
May 21 01:53:03 ubuntu-desktop pppd[3222]: Connection terminated.
May 21 01:53:03 ubuntu-desktop NetworkManager[880]: ** Message: Terminated ppp daemon with PID 3222.
May 21 01:53:03 ubuntu-desktop NetworkManager[880]: <error> [1495302783.7113] platform-linux: do-change-link[8]: failure changing link: failure 19 (No such device)
May 21 01:53:03 ubuntu-desktop NetworkManager[880]: <warn>  [1495302783.7212] device (ppp0): failed to disable userspace IPv6LL address handling
May 21 01:53:03 ubuntu-desktop NetworkManager[880]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 1 / phase 'dead'
May 21 01:53:03 ubuntu-desktop NetworkManager[880]: <info>  [1495302783.7332] devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 21 01:53:03 ubuntu-desktop NetworkManager[880]: <info>  [1495302783.7346] vpn-connection[0xa3c5f0,ab172dac-26b6-41f8-9584-9f4f40d9b672,"jumo",0]: VPN service disappeared
May 21 01:53:03 ubuntu-desktop pppd[3222]: Terminating on signal 15
May 21 01:53:03 ubuntu-desktop NetworkManager[880]: Terminating on signal 15
May 21 01:53:03 ubuntu-desktop pppd[3222]: Child process /usr/sbin/pptp 193.24.15.230 --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-3201 (pid 3225) terminated with signal 15
May 21 01:53:03 ubuntu-desktop NetworkManager[880]: Child process /usr/sbin/pptp 193.24.15.230 --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-3201 (pid 3225) terminated with signal 15
May 21 01:53:03 ubuntu-desktop pppd[3222]: Modem hangup
May 21 01:53:03 ubuntu-desktop NetworkManager[880]: Modem hangup
May 21 01:53:03 ubuntu-desktop NetworkManager[880]: ** Message: nm-pptp-ppp-plugin: (nm_exit_notify): cleaning up
May 21 01:53:03 ubuntu-desktop pppd[3222]: Exit.
May 21 01:53:03 ubuntu-desktop pptp[3238]: nm-pptp-service-3201 warn[decaps_hdlc:pptp_gre.c:220]: short read (-1): Input/output error
May 21 01:53:03 ubuntu-desktop pptp[3238]: nm-pptp-service-3201 warn[decaps_hdlc:pptp_gre.c:232]: pppd may have shutdown, see pppd log
May 21 01:53:03 ubuntu-desktop pptp[3244]: nm-pptp-service-3201 log[callmgr_main:pptp_callmgr.c:245]: Closing connection (unhandled)
May 21 01:53:03 ubuntu-desktop pptp[3244]: nm-pptp-service-3201 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 12 'Call-Clear-Request'
May 21 01:53:03 ubuntu-desktop pptp[3244]: nm-pptp-service-3201 log[call_callback:pptp_callmgr.c:84]: Closing connection (call state)

```

would be grateful if someone could tell me what to do to establish pptp vpn connection. thanks a lota

---

