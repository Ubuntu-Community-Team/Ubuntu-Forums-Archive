---
title: "universal config netplan without hardcoded interface name?"
date: 2019-11-20
forum: Networking &amp; Wireless
---

### Post by nozombian on 2019-11-20
Hi, I installed minimal ubuntu 18.04 from minimal.iso without GUI, selected server option and samba. Prepared this in my pc, took to another pc and I was surprised, that system did not acquire IPv4. To have ethernet, I had to connect keyboard and monitor, log in locally, edit /etc/netplan/01-netcfg.yaml, replace old enps-ifname with new enps-ifname, run sudo netplan --debug apply and then I got IPv4 again. Before I ditch netplan completely, I want to give it a chance, even if it looks like change for the worse.

Is there some universal config, that will allow me to run in any system and will configure the card it finds with dhcp as it used to be for decades?

Why netplan uses hardcoded ifname anyway?

I haven't been with ubuntu for a while (now I'm mostly on opensuse leap and tumbleweed), but I always liked ubuntu, because it was easy to use and everything worked "out of the box", so this was a big surprise to me. I just want to plug the prepared drive with installed ubuntu and forget about it, without the need to connect keyboard, monitor and manual editing. Is this still possible with ubuntu? Thank you.

---

### Post by TheFu on 2019-11-20
I don't know.  A few thoughts, complaints, and 2 options below.

You can thank the systemd project for deciding that nobody should have an eth0 or eth1 network device.  They decided that places with 6 NICs needed to have unique device names, always, and forgot about the millions of users with 1 NIC who need simplicity.

The did provide a few solutions to control network device names.  It has been a long time since I bothered to change them - like 4 yrs.  The freedesktop website, which hosts the systemd project has a page just for controlling network device names.  It can be controlled using grub. There's another method, but grub was easier in my tiny mind. Think this is it: [https://www.freedesktop.org/software/systemd/man/systemd.net-naming-scheme.html](https://www.freedesktop.org/software/systemd/man/systemd.net-naming-scheme.html)  Looks like they removed the grub method. Boooo!

The old version, which applies to older releases:
[https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)

I've mostly avoided 18.04 due to netplan not quite being there for non-trivial needs.  Installed a fresh 18.04 test server last month with a static IP and had to manually fix the netplan.yaml file, just like you.  I'm waiting for 20.04 to decide on Ubuntu server use going forward.  There is still a chance.  For desktops, I'm almost positive we'll be leaving Ubuntu over forced snap packages.

As an alternative option, have you considered using **nm-cli** for dhcp needs?  I've never used it, but we had issues with network-manager long ago and simply purge it from all our systems at this point.

---

