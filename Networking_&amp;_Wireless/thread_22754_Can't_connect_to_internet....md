---
title: "Can't connect to internet..."
date: 2005-03-29
forum: Networking &amp; Wireless
---

### Post by sx460 on 2005-03-29
Hello all,

I've got a A64 system (winchester core) with Soltek K8TPro-939 board. The board has the VIA VT6122 gigabit NIC. The install of Ubuntu was smooth as silk, the smoothest install I've seen to date of Linux. However, once in Ubuntu I cannot connect to the internet. Ubuntu sees the card in the Network Configuration application, but in the Device Manager it shows it as unknown.

When configuring the card through the Network Configuration application it appears the card is installed correctly. It's configured with DHCP. However I can't ping Google through the shell (it just times out), plus I cannot surf through Firefox (it too times out). I've tried setting the settings manually with a static IP that I know will work with my network setup.

Does Ubuntu just not support the VIA VT6122 NIC? I believe support for this device came around kernel 2.6.9. All other onboard devices work great (SATA drive is OK, as well as sound).

Thanks in advance for your help!

---

### Post by alastair on 2005-03-29
Look at the logs - for ethernet (eth) messages :

/var/log/syslog

i.e. module load/identify etc.

Also :

ifconfig -a
route -n

---

### Post by dodger on 2005-03-29
maybe the required module is not loaded?

what does lsmod say?

---

