---
title: "Ubuntu 16.04 - VPN PPTP connection problem '...because the VPN service stopped'"
date: 2016-05-04
forum: Networking &amp; Wireless
---

### Post by arcucci on 2016-05-04
Hello,
I configured a VPN PPTP Connection, but when I try to connect to server, I receive this error message:
"The VPN connection 'myVPNConn' disconnected because the VPN service stopped"

How I can troubleshoot that?

Thank You in advance.

Tony

---

### Post by davehenson on 2016-05-04
I am by far no expert but I will say that to set up my vpn service, I installed OpenVPN. In a fresh 16.04 install, it does not appear that openvpn is installed by default.

---

### Post by mrbuga on 2016-05-05
I just had the same error and it turned out that it was just a typo in the ip address like [here]("http://askubuntu.com/questions/294120/how-to-debug-and-fix-pptp-vpn-client-connection").

To answer your question you can enter 
tail -f /var/log/syslog 
in the terminal to get more details.

@davehenson OpenVPN and PPTP VPN are different technologies, the question was about PPTP.

---

### Post by AbdRahim on 2016-05-25
I have same problem with several vpns.
$ tail -f /var/log/syslog
May 25 21:36:01 R61-R61i gnome-session[1627]: (gnome-software:2098): As-WARNING **: failed to rescan: Failed to parse /usr/share/applications/unity-info-panel.desktop file: cannot process file of type application/x-desktop
May 25 21:36:01 R61-R61i gnome-session[1627]: (gnome-software:2098): As-WARNING **: failed to rescan: Failed to parse /usr/share/applications/unity-bluetooth-panel.desktop file: cannot process file of type application/x-desktop
May 25 21:36:05 R61-R61i gnome-session[1627]: (gnome-software:2098): As-WARNING **: failed to rescan: Failed to parse /usr/share/applications/gnome-session-properties.desktop.dpkg-new file: cannot process file of type text/plain
May 25 21:36:05 R61-R61i gnome-session[1627]: (gnome-software:2098): As-WARNING **: failed to rescan: Failed to parse /usr/share/applications/gnome-session-properties.desktop.dpkg-tmp file: cannot process file of type text/plain
May 25 21:36:05 R61-R61i gnome-session[1627]: (gnome-software:2098): As-WARNING **: failed to rescan: Failed to parse /usr/share/gnome/applications/defaults.list.dpkg-new file: cannot process file of type text/plain
May 25 21:36:05 R61-R61i gnome-session[1627]: (gnome-software:2098): As-WARNING **: failed to rescan: Failed to parse /usr/share/gnome/applications/defaults.list.dpkg-tmp file: cannot process file of type text/plain
May 25 21:36:05 R61-R61i gnome-session[1627]: (gnome-software:2098): As-WARNING **: failed to rescan: Failed to parse /usr/share/applications/gnome-session-properties.desktop file: cannot process file of type application/x-desktop
May 25 21:36:05 R61-R61i gnome-session[1627]: (gnome-software:2098): As-WARNING **: failed to rescan: Failed to parse /usr/share/gnome/applications/defaults.list file: cannot process file of type text/plain
May 25 21:36:22 R61-R61i gnome-session[1627]: (gnome-software:2098): As-WARNING **: failed to rescan: Failed to parse /usr/share/applications/bamf-2.index file: cannot process file of type text/plain
May 25 21:38:44 R61-R61i org.gnome.Terminal[1458]: ** (gnome-terminal-server:10245): WARNING **: Couldn't register with accessibility bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
May 25 21:39:27 R61-R61i NetworkManager[817]: <info>  [1464226767.8362] audit: op="connection-activate" uuid="f42b41ef-08d8-4250-88df-f7bfb8a07b7d" name="GreenUS1" pid=2052 uid=1000 result="success"
May 25 21:39:27 R61-R61i NetworkManager[817]: <info>  [1464226767.8784] vpn-connection[0x15015e0,f42b41ef-08d8-4250-88df-f7bfb8a07b7d,"GreenUS1",0]: Started the VPN service, PID 10270
May 25 21:39:27 R61-R61i NetworkManager[817]: <info>  [1464226767.9386] vpn-connection[0x15015e0,f42b41ef-08d8-4250-88df-f7bfb8a07b7d,"GreenUS1",0]: Saw the service appear; activating connection
May 25 21:39:27 R61-R61i NetworkManager[817]: <info>  [1464226767.9570] vpn-connection[0x15015e0,f42b41ef-08d8-4250-88df-f7bfb8a07b7d,"GreenUS1",0]: VPN plugin: state changed: init (1)
May 25 21:39:28 R61-R61i gnome-session[1627]: ** (nm-pptp-auth-dialog:10275): WARNING **: Couldn't register with accessibility bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
May 25 21:39:28 R61-R61i NetworkManager[817]: <info>  [1464226768.3534] vpn-connection[0x15015e0,f42b41ef-08d8-4250-88df-f7bfb8a07b7d,"GreenUS1",0]: VPN connection: (ConnectInteractive) reply received
May 25 21:39:28 R61-R61i NetworkManager[817]: ** Message: pppd started with pid 10279
May 25 21:39:28 R61-R61i NetworkManager[817]: <info>  [1464226768.5821] vpn-connection[0x15015e0,f42b41ef-08d8-4250-88df-f7bfb8a07b7d,"GreenUS1",0]: VPN plugin: state changed: starting (3)
May 25 21:39:28 R61-R61i pppd[10279]: Plugin /usr/lib/pppd/2.4.7/nm-pptp-pppd-plugin.so loaded.
May 25 21:39:28 R61-R61i NetworkManager[817]: Plugin /usr/lib/pppd/2.4.7/nm-pptp-pppd-plugin.so loaded.
May 25 21:39:28 R61-R61i NetworkManager[817]: ** Message: nm-pptp-ppp-plugin: (plugin_init): initializing
May 25 21:39:28 R61-R61i pppd[10279]: pppd 2.4.7 started by root, uid 0
May 25 21:39:28 R61-R61i NetworkManager[817]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 3 / phase 'serial connection'
May 25 21:39:28 R61-R61i pppd[10279]: Using interface ppp0
May 25 21:39:28 R61-R61i NetworkManager[817]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
May 25 21:39:28 R61-R61i NetworkManager[817]: <info>  [1464226768.7457] manager: (ppp0): new Generic device (/org/freedesktop/NetworkManager/Devices/30)
May 25 21:39:28 R61-R61i NetworkManager[817]: Using interface ppp0
May 25 21:39:28 R61-R61i pppd[10279]: Connect: ppp0 <--> /dev/pts/6
May 25 21:39:28 R61-R61i NetworkManager[817]: Connect: ppp0 <--> /dev/pts/6
May 25 21:39:28 R61-R61i NetworkManager[817]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
May 25 21:39:28 R61-R61i pptp[10283]: nm-pptp-service-10270 log[main:pptp.c:350]: The synchronous pptp option is NOT activated
May 25 21:39:28 R61-R61i NetworkManager[817]: <info>  [1464226768.8197] devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 25 21:39:28 R61-R61i NetworkManager[817]: <info>  [1464226768.8197] device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
May 25 21:39:59 R61-R61i pppd[10279]: LCP: timeout sending Config-Requests
May 25 21:39:59 R61-R61i NetworkManager[817]: LCP: timeout sending Config-Requests
May 25 21:39:59 R61-R61i NetworkManager[817]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 11 / phase 'disconnect'
May 25 21:39:59 R61-R61i NetworkManager[817]: Connection terminated.
May 25 21:39:59 R61-R61i pppd[10279]: Connection terminated.
May 25 21:39:59 R61-R61i NetworkManager[817]: ** Message: Terminated ppp daemon with PID 10279.
May 25 21:39:59 R61-R61i NetworkManager[817]: <error> [1464226799.7947] platform-linux: do-change-link[31]: failure changing link: failure 19 (No such device)
May 25 21:39:59 R61-R61i NetworkManager[817]: <warn>  [1464226799.7948] device (ppp0): failed to disable userspace IPv6LL address handling
May 25 21:39:59 R61-R61i NetworkManager[817]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 1 / phase 'dead'
May 25 21:39:59 R61-R61i pppd[10279]: Terminating on signal 15
May 25 21:39:59 R61-R61i NetworkManager[817]: Terminating on signal 15
May 25 21:39:59 R61-R61i pppd[10279]: Child process /usr/sbin/pptp 136.0.16.111 --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-10270 (pid 10282) terminated with signal 15
May 25 21:39:59 R61-R61i NetworkManager[817]: Child process /usr/sbin/pptp 136.0.16.111 --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-10270 (pid 10282) terminated with signal 15
May 25 21:39:59 R61-R61i NetworkManager[817]: Modem hangup
May 25 21:39:59 R61-R61i NetworkManager[817]: ** Message: nm-pptp-ppp-plugin: (nm_exit_notify): cleaning up
May 25 21:39:59 R61-R61i pppd[10279]: Modem hangup
May 25 21:39:59 R61-R61i NetworkManager[817]: <info>  [1464226799.8146] devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 25 21:39:59 R61-R61i pppd[10279]: Exit.
May 25 21:39:59 R61-R61i NetworkManager[817]: <warn>  [1464226799.8147] vpn-connection[0x15015e0,f42b41ef-08d8-4250-88df-f7bfb8a07b7d,"GreenUS1",0]: VPN plugin: failed: connect-failed (1)
May 25 21:39:59 R61-R61i NetworkManager[817]: <info>  [1464226799.8148] vpn-connection[0x15015e0,f42b41ef-08d8-4250-88df-f7bfb8a07b7d,"GreenUS1",0]: VPN plugin: state changed: stopping (5)
May 25 21:39:59 R61-R61i NetworkManager[817]: <info>  [1464226799.8149] vpn-connection[0x15015e0,f42b41ef-08d8-4250-88df-f7bfb8a07b7d,"GreenUS1",0]: VPN service disappeared

Now what?

---

### Post by superthin on 2016-07-17
My problem is the same:

```
tail -f /var/log/syslog
Jul 18 08:53:24 mylaptop NetworkManager[874]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 1 / phase 'dead'
Jul 18 08:53:24 mylaptop NetworkManager[874]: Child process /usr/sbin/pptp 10.1.130.33 --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-6974 (pid 6982) terminated with signal 15
Jul 18 08:53:24 mylaptop NetworkManager[874]: ** Message: nm-pptp-ppp-plugin: (nm_exit_notify): cleaning up
Jul 18 08:53:24 mylaptop pptp[6987]: nm-pptp-service-6974 warn[decaps_hdlc:pptp_gre.c:220]: short read (-1): Input/output error
Jul 18 08:53:24 mylaptop pptp[6987]: nm-pptp-service-6974 warn[decaps_hdlc:pptp_gre.c:232]: pppd may have shutdown, see pppd log
Jul 18 08:53:24 mylaptop pppd[6979]: Child process /usr/sbin/pptp 10.1.130.33 --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-6974 (pid 6982) terminated with signal 15
Jul 18 08:53:24 mylaptop pptp[7002]: nm-pptp-service-6974 log[callmgr_main:pptp_callmgr.c:245]: Closing connection (unhandled)
Jul 18 08:53:24 mylaptop pppd[6979]: Exit.
Jul 18 08:53:24 mylaptop pptp[7002]: nm-pptp-service-6974 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 12 'Call-Clear-Request'
Jul 18 08:53:24 mylaptop pptp[7002]: nm-pptp-service-6974 log[call_callback:pptp_callmgr.c:84]: Closing connection (call state)
```

In the past, everything was OK. Ubuntu 16.04. Someday I cannot connect after some times "apt-get update && apt-get upgrade". Don't know what happened.

---

### Post by diegoturcios on 2016-08-09
Did you found a work around for this?
It looks this is a bug: [https://bugs.launchpad.net/ubuntu/+source/pptp-linux/+bug/259698](https://bugs.launchpad.net/ubuntu/+source/pptp-linux/+bug/259698) :(

---

