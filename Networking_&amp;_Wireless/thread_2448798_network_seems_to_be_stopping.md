---
title: "network seems to be stopping"
date: 2020-08-13
forum: Networking &amp; Wireless
---

### Post by jgw on 2020-08-13
Every once in a while I will notice that my network goes down.  I have also noticed, almost every day, that my messages tell me the network has failed sometime during the night.  I have no idea why.  Most of the time all I have to do to get it going again is to do:
sudo nmcli networking off
and then:
sudo nmcli networking on

This time, however I had to open system setup and then stop my wifi and then start it from there and now its working.  


I went to logs and had it put the important stuff into the file below (if you need more just ask);

```
 4:48:24 PM wpa_supplicant: dbus: Failed to construct signal
 4:44:06 PM dhclient: receive_packet failed on wlx008736326fa1: Network is down
 4:43:33 PM wpa_supplicant: dbus: Failed to construct signal
Aug 11  3:45:45 PM kernel: [drm:radeon_dvi_detect [radeon]] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
Aug  5  6:53:17 AM systemd: Failed to start Process error reports when automatic reporting is enabled.
Aug  3  7:56:03 AM sudo: pam_unix(sudo:auth): auth could not identify password for [greg]
Aug  1  6:57:15 PM pulseaudio: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Aug  1  6:57:03 PM spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
Aug  1  6:56:31 PM systemd: Failed to start Service for snap application network-manager.networkmanager.
Aug  1  6:56:30 PM networkmanager: <error> [1596333390.9714] failed to start the dbus service.
Aug  1  6:56:20 PM wpa_supplicant: dbus: Failed to construct signal
Aug  1  6:55:42 PM kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.VGA.ATCS, AE_NOT_FOUND (20170831/psparse-550)
Aug  1  6:55:42 PM kernel: Couldn't get size: 0x800000000000000e
Aug  1  6:55:42 PM kernel: MODSIGN: Couldn't get UEFI db list
Aug  1  6:55:42 PM kernel: Couldn't get size: 0x800000000000000e
```

---

