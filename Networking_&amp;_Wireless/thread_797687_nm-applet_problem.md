---
title: "nm-applet problem"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by Beesquito on 2008-05-17
I'm having some trouble getting wireless with my Netgear wn311t, and after much trouble I think the problem is not with ndiswrapper, but with nm-applet (or something more fundamental.) lspci shows me:
```
02:08.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Unknown device [11ab:2a02] (rev 03)
```
I installed the netmw14x driver with ndiswrapper, and told it to use it for 11ab:2a02, and ndiswrapper -l gives:
```
netmw14x                driver installed, hardware present
```
My problem comes from the fact that nm-applet does not show any wireless icon, and if I go to Applications>System>Network (I'm using xubuntu, if that menu order looks a little funny) I am only shown wired connection and modem connection.  For reference,
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```
and in /etc/network/interfaces I have
```
auto lo
iface lo inet loopback
```
and that's it.  If anyone has any ideas, it would be greatly appreciated.

---

