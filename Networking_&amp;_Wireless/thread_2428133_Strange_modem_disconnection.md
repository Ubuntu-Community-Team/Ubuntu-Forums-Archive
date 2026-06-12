---
title: "Strange modem disconnection"
date: 2019-09-30
forum: Networking &amp; Wireless
---

### Post by cpcdos on 2019-09-30
Hello!

If anyone has the solution to my problem I promise you that I call you DAD.

I have a huge problem, for 2 years and I buy a new PC + 4G modem card to fill the problem and it begin to become expensive. (I can not change hardware)

I have several hundreds of industrial mini-PC with ubuntu 14.04 LTS installed. Their goal is to establish a 4G connection with a sim card and various operators.

All PCs without exception have exactly the same hard disk image, and the same 4G card (MC7430 or MC7455 in mPCIe) and tested with French operator Bouygues Telecom (20820 operator - and apn mmsbouygtel.com)

According to the logs, all PC modem cards connect to the PPP network, I have a signal, so far it's reassuring!
But 1 PC out of 3 refuses to connect when it needs an IP for an internet connection (in Europe / US same problem)

I tried a lot of things, updating ubuntu, mmcli , networkmanager etc ... Typing AT commands by hand to the same principle as wvdial, **IT WORKS**, I have an IP and internet, but that's not what I want.

I show you my syslog:
```
Sep 25 15:00:42 router ModemManager[389]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (enabled -> registered)
Sep 25 15:00:42 router NetworkManager[1153]: <info> (ttyUSB2) modem state changed, 'enabled' --> 'registered' (reason: unknown)
Sep 25 15:00:49 router NetworkManager[1153]: <info> Activation (ttyUSB2) starting connection 'Bouygues Telecom Forfait Data'
Sep 25 15:00:49 router NetworkManager[1153]: <info> (ttyUSB2): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep 25 15:00:49 router NetworkManager[1153]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled...
Sep 25 15:00:49 router NetworkManager[1153]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started...
Sep 25 15:00:49 router NetworkManager[1153]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete.
Sep 25 15:00:49 router ModemManager[389]: <info>  Simple connect started...
Sep 25 15:00:49 router ModemManager[389]: <info>  Simple connect state (4/8): Wait to get fully enabled
Sep 25 15:00:49 router ModemManager[389]: <info>  Simple connect state (5/8): Register
Sep 25 15:00:49 router ModemManager[389]: <info>  Simple connect state (6/8): Bearer
Sep 25 15:00:49 router ModemManager[389]: <info>  Simple connect state (7/8): Connect
Sep 25 15:00:49 router ModemManager[389]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (registered -> connecting)
Sep 25 15:00:49 router NetworkManager[1153]: <info> (ttyUSB2) modem state changed, 'registered' --> 'connecting' (reason: user-requested)
Sep 25 15:00:49 router ModemManager[389]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (connecting -> connected)
Sep 25 15:00:49 router ModemManager[389]: <info>  Simple connect state (8/8): All done
Sep 25 15:00:49 router NetworkManager[1153]: <info> (ttyUSB2) modem state changed, 'connecting' --> 'connected' (reason: user-requested)
Sep 25 15:00:49 router NetworkManager[1153]: <warn> (ttyUSB2): failed to look up interface index
Sep 25 15:00:49 router NetworkManager[1153]: <info> Activation (ttyUSB2) Stage 2 of 5 (Device Configure) scheduled...
Sep 25 15:00:49 router NetworkManager[1153]: <info> Activation (ttyUSB2) Stage 2 of 5 (Device Configure) starting...
Sep 25 15:00:49 router NetworkManager[1153]: <info> (ttyUSB2): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 25 15:00:49 router NetworkManager[1153]: <info> Activation (ttyUSB2) Stage 2 of 5 (Device Configure) successful.
Sep 25 15:00:49 router NetworkManager[1153]: <info> Activation (ttyUSB2) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 25 15:00:49 router NetworkManager[1153]: <info> Activation (ttyUSB2) Stage 2 of 5 (Device Configure) complete.
Sep 25 15:00:49 router NetworkManager[1153]: <info> Activation (ttyUSB2) Stage 3 of 5 (IP Configure Start) started...
Sep 25 15:00:49 router NetworkManager[1153]: <info> (ttyUSB2): device state change: config -> ip-config (reason 'none') [50 70 0]
Sep 25 15:00:49 router NetworkManager[1153]: <info> using modem-specified IP timeout: 20 seconds
Sep 25 15:00:49 router NetworkManager[1153]: <info> starting PPP connection
Sep 25 15:00:49 router NetworkManager[1153]: <info> pppd started with pid 7638
Sep 25 15:00:49 router NetworkManager[1153]: <info> Activation (ttyUSB2) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep 25 15:00:49 router NetworkManager[1153]: <info> Activation (ttyUSB2) Stage 3 of 5 (IP Configure Start) complete.
Sep 25 15:00:49 router NetworkManager[1153]: <info> Activation (ttyUSB2) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep 25 15:00:49 router NetworkManager[1153]: <info> Activation (ttyUSB2) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Sep 25 15:00:49 router pppd[7638]: Plugin /usr/lib/x86_64-linux-gnu/pppd/2.4.5/nm-pppd-plugin.so loaded.
Sep 25 15:00:49 router pppd[7638]: pppd 2.4.5 started by root, uid 0
Sep 25 15:00:49 router pppd[7638]: Removed stale lock on ttyUSB2 (pid 5691)
Sep 25 15:00:49 router pppd[7638]: Using interface ppp0
Sep 25 15:00:49 router pppd[7638]: Connect: ppp0 <--> /dev/ttyUSB2
Sep 25 15:00:49 router pppd[7638]: CHAP authentication succeeded
Sep 25 15:00:49 router pppd[7638]: CHAP authentication succeeded
Sep 25 15:00:49 router NetworkManager[1153]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep 25 15:00:49 router NetworkManager[1153]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Sep 25 15:00:49 router NetworkManager[1153]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Sep 25 15:01:09 router NetworkManager[1153]: <warn> pppd timed out or didn't initialize our dbus module
Sep 25 15:01:09 router NetworkManager[1153]: <info> Activation (ttyUSB2) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Sep 25 15:01:09 router NetworkManager[1153]: <info> Activation (ttyUSB2) Stage 4 of 5 (IPv4 Configure Timeout) started...
Sep 25 15:01:09 router NetworkManager[1153]: <info> (ttyUSB2): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Sep 25 15:01:09 router pppd[7638]: Terminating on signal 15
Sep 25 15:01:09 router NetworkManager[1153]: <warn> Activation (ttyUSB2) failed for connection 'Bouygues Telecom Forfait Data'
Sep 25 15:01:09 router NetworkManager[1153]: <info> Activation (ttyUSB2) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Sep 25 15:01:09 router NetworkManager[1153]: <info> (ttyUSB2): device state change: failed -> disconnected (reason 'none') [120 30 0]
Sep 25 15:01:09 router NetworkManager[1153]: <info> (ttyUSB2): deactivating device (reason 'none') [0]
Sep 25 15:01:09 router ModemManager[389]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (connected -> disconnecting)
Sep 25 15:01:09 router NetworkManager[1153]: <info> (ttyUSB2) modem state changed, 'connected' --> 'disconnecting' (reason: user-requested)
Sep 25 15:01:11 router avahi-daemon[501]: Withdrawing workstation service for ppp0.
Sep 25 15:01:11 router NetworkManager[1153]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
```

What network manager does not handle? What is going on ?

Here is my mmcli :
```
administrator@router:~$ mmcli -m 0 

/org/freedesktop/ModemManager1/Modem/0 (device id 'c5d7407ac112435a63988cbcd7e1396bd01f27b4')
  -------------------------
  Hardware |   manufacturer: 'Sierra Wireless, Incorporated'
           |          model: 'MC7430'
           |       revision: 'SWI9X30C_02.30.03.00 r7804 CARMD-EV-FRMWR2 2018/07/25 01:10:04'
           |   H/W revision: 'unknown'
           |      supported: 'gsm-umts, lte'
           |        current: 'gsm-umts, lte'
           |   equipment id: '359074061186328'
  -------------------------
  System   |         device: '/sys/devices/pci0000:00/0000:00:14.0/usb2/2-5'
           |        drivers: 'qmi_wwan, qcserial'
           |         plugin: 'Sierra'
           |   primary port: 'ttyUSB2'
           |          ports: 'ttyUSB0 (qcdm), ttyUSB2 (at), wwan0 (net), wwan1 (net)'
  -------------------------
  Numbers  |           own : '+33661490181'
  -------------------------
  Status   |           lock: 'none'
           | unlock retries: 'sim-pin (3), sim-puk (10)'
           |          state: 'registered'
           |    power state: 'on'
           |    access tech: 'lte'
           | signal quality: '80' (cached)
  -------------------------
  Modes    |      supported: 'allowed: 2g, 3g, 4g; preferred: none'
           |        current: 'allowed: 2g, 3g, 4g; preferred: none'
  -------------------------
  Bands    |      supported: 'unknown'
           |        current: 'unknown'
  -------------------------
  IP       |      supported: 'ipv4, ipv6, ipv4v6'
  -------------------------
  3GPP     |           imei: '359074061186328'
           |  enabled locks: 'none'
           |    operator id: '20820'
           |  operator name: 'B042'
           |   subscription: 'unknown'
           |   registration: 'home'
           |    EPS UE mode: 'csps-2'
  -------------------------
  SIM      |           path: '/org/freedesktop/ModemManager1/SIM/0'

  -------------------------
  Bearers  |          paths: '/org/freedesktop/ModemManager1/Bearer/1, /org/freedesktop/ModemManager1/Bearer/0'
```

Excuse me for my bad english level

Thank you very much,
Regards, 
Sebastien FAVIER

---

### Post by cpcdos on 2019-10-03
up :(

---

