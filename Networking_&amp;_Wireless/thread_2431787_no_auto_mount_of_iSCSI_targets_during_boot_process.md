---
title: "no auto mount of iSCSI targets during boot process"
date: 2019-11-21
forum: Networking &amp; Wireless
---

### Post by May_Masters on 2019-11-21
Hi all, I've installed a fresh VM with Ubuntu-Server 18.04.03 as a replacement for my old CentOS 7 machine. This server mounts iSCSI targets from my storage-server (CentOS 7.5).
The discovery works instantly and if you mount the targets manually, all seems fine. So I put all in the /etc/fstab and rebooted ...

The boot process got stuck for 90s, trying to mount the iSCSI target ... then fail with a timeout. Subsequently the mount of fstab also failed. But if you fire-up the dioscovery the targets are present and a (manual) mount succeeds.

I shut down the usual suspects: Firewall, Selinux, AppArmor ... no effect. Storage also has no entry about the process in its /var/log/messages

So I start digging a bit into the systemd startup scripts: A discovery/mount works perfectly using the following cmd:
```
iscsiadm -m node --login
```

But a swift examine of "/lib/systemd/system/open-iscsi.service" shows a different command:
```
ExecStart=/sbin/iscsiadm -m node --loginall=automatic
```

This is the system default, and this always fails !! Regardless if typed in manually or execute via service-script (iscsiadm version 2.0-874)
Truncating the line to a simple "--login" does the trick ...

Now, I don't have any extra security setup. So no password is needed to mount the iSCSI targets.
So is this a Bug or am I missing something here ...?

---

