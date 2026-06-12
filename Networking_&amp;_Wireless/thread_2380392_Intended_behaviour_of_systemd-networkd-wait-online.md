---
title: "Intended behaviour of systemd-networkd-wait-online is... what?"
date: 2017-12-16
forum: Networking &amp; Wireless
---

### Post by Davorian on 2017-12-16
Hey all,

So I've looked over a few threads on "slow boot time due to systemd-networkd-wait-online failure" etc.   I got the problem running Ubuntu Server 17.10 in a VirtualBox VM with an additional Host-Only network adapter configured (it is always connected, and DHCP is always available on boot).

I know the problem can be solved with:

```

sudo systemctl disable systemd-networkd-wait-online.service

sudo systemctl mask systemd-networkd-wait-online.service

```

That worked for me.  However, **disabling** a service to fix this seems weird.  Why does the service fail in the first place?

Does anyone know what the **intended** behaviour of this service is, and what is the "right" way to fix the problem?

Thanks!

---

### Post by vilhelm-gray on 2018-03-14
The **systemd-networkd-wait-online** service essentially waits until all  network interfaces are finished "configuring."

You can check what state  your network interfaces are currently in by running **networkctl**. For  example, on my system I have a single physical ethernet interface, a tap interface, two bridges for Xen, and four Xen virtual interfaces:

```

# networkctl
IDX LINK             TYPE               OPERATIONAL SETUP
  1 lo               loopback           carrier     unmanaged
  2 enp4s0           ether              carrier     configured
  3 tap0             ether              no-carrier  configuring
  4 xenbr1           ether              routable    configured
  5 xenbr0           ether              routable    configured
  6 vif1.0-emu       ether              degraded    unmanaged
  7 vif1.1-emu       ether              degraded    unmanaged
  8 vif1.0           ether              no-carrier  unmanaged
  9 vif1.1           ether              no-carrier  unmanaged

9 links listed.

```

The reason **systemd-networkd-wait-online** fails on my system is because the *tap0 *interface remains in the "configuring" state so **systemd-networkd-wait-online** never considers it finished.

---

