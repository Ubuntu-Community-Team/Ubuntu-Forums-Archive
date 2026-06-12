---
title: "OpenVPN Network Manager broken (by update)"
date: 2019-01-25
forum: Networking &amp; Wireless
---

### Post by kaktux on 2019-01-25
Hi there,

i got a curious problem. I had a working openvpn connection (Kubuntu 18.04) via the network manager.
Since this week it doesn't work anymore.

The curious thing is that i can get the connection working when i use the terminal and navigate into the folder with the openvpn data (certificates and xy.ovpn) via
```
sudo openvpn --config client.ovpn
```

But using the same data - certificates and xy.ovpn with network manager as gui - or starting the existing connection via terminal using ```
nmcli con up connectionname
```
results in a "timed out" error message.

Also on my mobile (using Sailfish OS) - the same vpn works to.

Any idea what could be the reason for that behaviour?

My guess is that maybe an update cause this - since i did a bigger one this week. But i am not sure if one of the packages involved is vpn/network related.
Here is the list of updates:
> libadplug-2.2.1-0v5
libapt-inst2.0
libtiff-tools
tibtiff5
virtualbox-qt
virtualbox
apt-utils
libapt-pkg5.0
apt
virtualbox-dkms
libpoppler73
libpoppler-glib8
libpoppler-qt5-1
poppler-utils
software-properties-common
librados2
gvfs-daemons
mysql-server-core-5.7
thunderbird-locale-de
cups-ipp-utils
cups-client
libcupscgi1
cups
libcupsimage2
cups-daemons
linux-firmware
cups-core-drivers
cups-bsd
gvfs-common
libcupsppdc1
gvfs
thinderbird
bsdutils
libgs9-common
libmysqlclient20
libsmbclient
ghostscript-x
rfkill
libsmartcols1
ghostscript
libuuid1
libcupsmime1
psmisc
cups-ppdc
gvfs-libs
mysql-client-core-5.7
libblkid1
libext2fs2
samba-libs
software-properties-kde
mount
libss2
cups-common
librdmacm1
cups-server-common
util-linux
ibverbs-providers
librbd1
e2fsprogs
libmount1
libgs9
libwbclient0
libibverbs1
gvfs-bin
python3-software-properties
ligfdisk1
uuid-runtine
libcups2
libcom-err2
fdisk



Is anyone having similar problems or an idea/solution for that?

---

