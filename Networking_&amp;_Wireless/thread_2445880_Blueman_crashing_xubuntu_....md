---
title: "Blueman crashing xubuntu ..."
date: 2020-06-21
forum: Networking &amp; Wireless
---

### Post by dbee on 2020-06-21
So xubuntu on my old HP stream crashes every few hours. I examined syslog and got this ...
```

Jun 21 13:46:10 dara-HP-Stream-Laptop-11-y0XX named[676]: network unreachable resolving './DNSKEY/IN': 2001:500:200::b#53
Jun 21 13:46:10 dara-HP-Stream-Laptop-11-y0XX named[676]: network unreachable resolving './DNSKEY/IN': 2001:500:a8::e#53
Jun 21 13:46:10 dara-HP-Stream-Laptop-11-y0XX named[676]: network unreachable resolving './DNSKEY/IN': 2001:503:c27::2:30#53
Jun 21 13:46:10 dara-HP-Stream-Laptop-11-y0XX named[676]: network unreachable resolving './DNSKEY/IN': 2001:500:9f::42#53
Jun 21 13:46:10 dara-HP-Stream-Laptop-11-y0XX named[676]: network unreachable resolving './DNSKEY/IN': 2001:500:12::d0d#53
Jun 21 13:46:10 dara-HP-Stream-Laptop-11-y0XX named[676]: network unreachable resolving './DNSKEY/IN': 2001:7fe::53#53
Jun 21 13:46:10 dara-HP-Stream-Laptop-11-y0XX named[676]: network unreachable resolving './DNSKEY/IN': 2001:500:2f::f#53
Jun 21 13:46:10 dara-HP-Stream-Laptop-11-y0XX named[676]: network unreachable resolving './DNSKEY/IN': 2001:500:2::c#53
Jun 21 13:46:10 dara-HP-Stream-Laptop-11-y0XX systemd[829]: Starting Bluetooth OBEX service...
Jun 21 13:46:10 dara-HP-Stream-Laptop-11-y0XX named[676]: reloading configuration succeeded
Jun 21 13:46:10 dara-HP-Stream-Laptop-11-y0XX named[676]: scheduled loading new zones
Jun 21 13:46:10 dara-HP-Stream-Laptop-11-y0XX obexd[1682]: OBEX daemon 5.48
Jun 21 13:46:10 dara-HP-Stream-Laptop-11-y0XX dbus-daemon[876]: [session uid=1000 pid=876] Successfully activated service 'org.bluez.obex'
Jun 21 13:46:10 dara-HP-Stream-Laptop-11-y0XX systemd[829]: Started Bluetooth OBEX service.
Jun 21 13:46:10 dara-HP-Stream-Laptop-11-y0XX named[676]: any newly configured zones are now loaded
Jun 21 13:46:10 dara-HP-Stream-Laptop-11-y0XX named[676]: running
Jun 21 13:46:10 dara-HP-Stream-Laptop-11-y0XX named[676]: managed-keys-zone: Key 20326 for zone . acceptance timer complete: key now trusted
Jun 21 13:46:11 dara-HP-Stream-Laptop-11-y0XX org.blueman.Mechanism[545]: Unable to init server: Could not connect: Connection refused
Jun 21 13:46:11 dara-HP-Stream-Laptop-11-y0XX org.blueman.Mechanism[545]: Unable to init server: Could not connect: Connection refused
Jun 21 13:46:11 dara-HP-Stream-Laptop-11-y0XX blueman-mechanism: Starting blueman-mechanism
Jun 21 13:46:11 dara-HP-Stream-Laptop-11-y0XX dbus-daemon[545]: [system] Successfully activated service 'org.blueman.Mechanism'
Jun 21 13:46:11 dara-HP-Stream-Laptop-11-y0XX blueman-mechani[1665]: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
Jun 21 13:46:11 dara-HP-Stream-Laptop-11-y0XX blueman-mechanism: loading Ppp
Jun 21 13:46:11 dara-HP-Stream-Laptop-11-y0XX blueman-mechanism: loading Rfcomm
Jun 21 13:46:11 dara-HP-Stiream-Laptop-11-y0XX blueman-mechanism: loading Network
Jun 21 13:46:11 dara-HP-Stream-Laptop-11-y0XX blueman-mechanism: loading RfKill

```
I uninstalled blueman and restarted the system
```

sudo apt remove blueman
sudo shutdown -h now 

```
This should work now right ?

---

### Post by ericbradshaw on 2020-08-27
I had the same error on a Dell OptiPlex 7010 (same computer I'm using right now) with a fresh install of Xubuntu 20.04. The error popped-up again on the same machine soon after a fresh install of Xubuntu 20.04.***1***. For me the error would appear upon booting the machine - every time.

Norbert_X referenced a bug [https://pad.lv/1871336](https://pad.lv/1871336) (which I do think is it) when answering a poster's question on the Ubunutu MATE Community at [URL="https://ubuntu-mate.community/t/20-04-blueman-tray-causes-internal-error/21680"]https://ubuntu-mate.community/t/20-04-blueman-tray-causes-internal-error/21680
[/URL]
He also asked the poster to run the following commands and post the output.

```
ls -ald ~/.cache
ls -al ~/.cache/blueman-*
killall blueman-tray
rm  ~/.cache/blueman-*
blueman-tray
```

After running those commands myself, the error (on my machine anyway) disappeared permanently.

---

