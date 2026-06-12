---
title: "AVM FritzCard PCI 2.0 under Ubuntu 8.04.1 Server running Xen Kernel no device nodes"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by Ctrl+Alt+Del on 2008-08-19
Hi Folks :-)
I have a somewhat odd problem trying to get an ISDN Card working on Ubuntu Server

The Server is a Xen Dom0 and i am trying to get a "01:07.0 Network controller: AVM Audiovisuelles MKTG & Computer System GmbH Fritz!PCI v2.0 ISDN (rev 02)" started.

i installed the restricted modules, the fritz firmware and the capiutils according to [http://wiki.ubuntuusers.de/ISDN-Karten](http://wiki.ubuntuusers.de/ISDN-Karten) (german) and upon reboot i am greeted with:


```
Aug 19 11:51:41 ruby kernel: [   25.691182] capifs: Rev 1.1.2.3
Aug 19 11:51:41 ruby udevd-event[5286]: udev_node_mknod: mknod(/dev/capi/0.udev-tmp, 020660, 191, 0) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5289]: udev_node_mknod: mknod(/dev/capi/1.udev-tmp, 020660, 191, 1) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5291]: udev_node_mknod: mknod(/dev/capi/2.udev-tmp, 020660, 191, 2) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5292]: udev_node_mknod: mknod(/dev/capi/3.udev-tmp, 020660, 191, 3) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5296]: udev_node_mknod: mknod(/dev/capi/4.udev-tmp, 020660, 191, 4) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5297]: udev_node_mknod: mknod(/dev/capi/5.udev-tmp, 020660, 191, 5) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5299]: udev_node_mknod: mknod(/dev/capi/6.udev-tmp, 020660, 191, 6) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5302]: udev_node_mknod: mknod(/dev/capi/7.udev-tmp, 020660, 191, 7) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5303]: udev_node_mknod: mknod(/dev/capi/8.udev-tmp, 020660, 191, 8) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5304]: udev_node_mknod: mknod(/dev/capi/9.udev-tmp, 020660, 191, 9) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5306]: udev_node_mknod: mknod(/dev/capi/10.udev-tmp, 020660, 191, 10) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5307]: udev_node_mknod: mknod(/dev/capi/11.udev-tmp, 020660, 191, 11) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5309]: udev_node_mknod: mknod(/dev/capi/12.udev-tmp, 020660, 191, 12) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5311]: udev_node_mknod: mknod(/dev/capi/13.udev-tmp, 020660, 191, 13) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5313]: udev_node_mknod: mknod(/dev/capi/14.udev-tmp, 020660, 191, 14) failed: Operation not permitted
Aug 19 11:51:41 ruby kernel: [   25.727283] capi20: Rev 1.1.2.7: started up with major 68 (middleware+capifs)
Aug 19 11:51:41 ruby udevd-event[5315]: udev_node_mknod: mknod(/dev/capi/15.udev-tmp, 020660, 191, 15) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5317]: udev_node_mknod: mknod(/dev/capi/16.udev-tmp, 020660, 191, 16) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5319]: udev_node_mknod: mknod(/dev/capi/17.udev-tmp, 020660, 191, 17) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5321]: udev_node_mknod: mknod(/dev/capi/18.udev-tmp, 020660, 191, 18) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5323]: udev_node_mknod: mknod(/dev/capi/19.udev-tmp, 020660, 191, 19) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5325]: udev_node_mknod: mknod(/dev/capi/20.udev-tmp, 020660, 191, 20) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5327]: udev_node_mknod: mknod(/dev/capi/21.udev-tmp, 020660, 191, 21) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5329]: udev_node_mknod: mknod(/dev/capi/22.udev-tmp, 020660, 191, 22) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5330]: udev_node_mknod: mknod(/dev/capi/23.udev-tmp, 020660, 191, 23) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5331]: udev_node_mknod: mknod(/dev/capi/24.udev-tmp, 020660, 191, 24) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5332]: udev_node_mknod: mknod(/dev/capi/25.udev-tmp, 020660, 191, 25) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5333]: udev_node_mknod: mknod(/dev/capi/26.udev-tmp, 020660, 191, 26) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5335]: udev_node_mknod: mknod(/dev/capi/27.udev-tmp, 020660, 191, 27) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5336]: udev_node_mknod: mknod(/dev/capi/28.udev-tmp, 020660, 191, 28) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5338]: udev_node_mknod: mknod(/dev/capi/29.udev-tmp, 020660, 191, 29) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5340]: udev_node_mknod: mknod(/dev/capi/30.udev-tmp, 020660, 191, 30) failed: Operation not permitted
Aug 19 11:51:41 ruby udevd-event[5342]: udev_node_mknod: mknod(/dev/capi/31.udev-tmp, 020660, 191, 31) failed: Operation not permitted 
```
capiinfo says:
capi not installed - No such device or address (6)

which is not much of a suprise :)
any pointers?
thx in advance


**EDIT: turned out to be a bug that is already reported...**

---

