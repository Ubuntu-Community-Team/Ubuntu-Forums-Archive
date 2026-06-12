---
title: "Photon plus stop working in ubuntu 12.04"
date: 2013-12-10
forum: Networking &amp; Wireless
---

### Post by ice-simx on 2013-12-10
From last few days (after Tata updated its photon network) photon+ stops working in ubuntu 12.04
Upon click on connection /var/log/syslog shows following message

Dec 10 10:23:49 hostname NetworkManager[938]: <info> Activation (ttyUSB0) starting connection 'Tata Indicom (Photon+) connection'
Dec 10 10:23:49 hostname NetworkManager[938]: <info> (ttyUSB0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 10 10:23:49 hostname NetworkManager[938]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 10 10:23:49 hostname NetworkManager[938]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Dec 10 10:23:49 hostname NetworkManager[938]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Dec 10 10:23:49 hostname modem-manager[903]: <info>  (ttyUSB0) opening serial port...
Dec 10 10:23:49 hostname modem-manager[903]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
Dec 10 10:23:50 hostname modem-manager[903]: <info>  (ttyUSB2) opening serial port...
Dec 10 10:23:50 hostname modem-manager[903]: <info>  (ttyUSB1) opening serial port...
Dec 10 10:23:50 hostname modem-manager[903]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> enabled)
Dec 10 10:23:50 hostname NetworkManager[938]: <info> WWAN now enabled by management service
Dec 10 10:24:50 hostname NetworkManager[938]: <warn> CDMA connection failed: (32) No service
Dec 10 10:24:50 hostname NetworkManager[938]: <info> (ttyUSB0): device state change: prepare -> failed (reason 'none') [40 120 0]
Dec 10 10:24:50 hostname NetworkManager[938]: <warn> Activation (ttyUSB0) failed.
Dec 10 10:24:50 hostname NetworkManager[938]: <info> (ttyUSB0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Dec 10 10:24:50 hostname NetworkManager[938]: <info> (ttyUSB0): deactivating device (reason 'none') [0]
Dec 10 10:24:50 hostname NetworkManager[938]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Dec 10 10:24:50 hostname NetworkManager[938]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed


But when tried with wvdial, it works
just install wvdial
$ sudo apt-get install wvdial
$ sudo wvdialconf > /etc/wvdial.conf
$ sudo vim /etc/wvdial.conf  (and add following lines)
Phone = #777
Password = internet
Username = internet
Stupid Mode = 1
:wq
$ sudo wvdial

and it works!!!

then why NetwrokManager fails :(

---

### Post by ice-simx on 2013-12-10
wvdial should be default included in future releases.

---

