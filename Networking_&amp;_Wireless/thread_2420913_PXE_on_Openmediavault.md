---
title: "PXE on Openmediavault"
date: 2019-06-12
forum: Networking &amp; Wireless
---

### Post by tomtom447 on 2019-06-12
So I'm using Openmediavault to setup a PXE host server, but the plugin required some settings in DHCP in another plugin (Dnsmasq), that doesn't seem to be able to set anything.
The place where I get stuck is Error network: The value 'NULL' is not a string. and Failed to execute command 'export PATH=/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/bin:/usr/local/sbin; export LANG=C.UTF-8; systemctl start 'dnsmasq' 2>&1' with exit code '1': Job for dnsmasq.service failed because the control process exited with error code.
I asked the community but never got a response, so I tried entering things in manually using instructions form [https://www.ostechnix.com/how-to-install-pxe-server-on-ubuntu-16-04/](https://www.ostechnix.com/how-to-install-pxe-server-on-ubuntu-16-04/) as a guide, but had an error when sudo cp -fr install/netboot/* /var/lib/tftpboot/ that install isn't a command.
Also I'm replacing every IP with 10.0.0.228, not sure if that's correct.


Anyway, I'm a bit of a noob, in networking... so any help would be much appreciated.

---

### Post by tomtom447 on 2019-06-15
I think I need to do something with permissions.

---

