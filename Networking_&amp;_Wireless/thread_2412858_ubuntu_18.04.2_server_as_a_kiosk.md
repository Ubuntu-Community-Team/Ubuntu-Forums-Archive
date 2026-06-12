---
title: "ubuntu 18.04.2 server as a kiosk"
date: 2019-02-18
forum: Networking &amp; Wireless
---

### Post by densha2 on 2019-02-18
Hi Forum,

I have created a kiosk like device using a minimal installation of Ubuntu 18.04.2 server (ubuntu-minimal) using a preseed approach.   

When my device boots up it is not getting an IP address.  If I manually run dhclient I get an IP address assigned to the connected NIC.  So I know my netplan.io configuration file is correct.  If I look at the packages installed I see DHCP Client - isc-dhcp-client and isc-dhcp-common packages installed.

Once I run dhclient I see the DHCPDISCOVER requests sent for the other NICs that not connected or configured.

I assume I have missed installing a package, as I selected no-install-recommends to keep disk usage to a minimum

Any ideas on why dhclient is not running?  What service runs dhclient?   How is dhclient automatically run in systemd environment.

Thanks

Densha

---

### Post by cptkeys on 2019-02-28
I have been having the same issue with my server and desktop install for 18.04.2
Been trying to deploy through PXELinux and using Preseed files, neither installs come out with DHCP working correctly

---

### Post by wildmanne39 on 2019-02-28
Hello and welcome to the forum cptkeys, please start your own thread instead of posting in someone else's that way you can both get the help you need without creating confusion.

Thanks

---

