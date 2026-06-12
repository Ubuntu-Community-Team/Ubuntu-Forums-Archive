---
title: "Wifi stops working in ~15 min after system boot. Able to reconnect only after reboot."
date: 2017-04-21
forum: Networking &amp; Wireless
---

### Post by joseph.chereshnovsky on 2017-04-21
Hi all,

I have a laptop Asus ZenBook Prime UX31L, which comes with:

 **Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)**** Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c070]**
** Kernel driver in use: ****iwlwifi**

After I boot my system, WIFI works normally for some random time, like 10-20 minutes.
Then connection stops working, but network manager still reports "Connected" status. Upon reconnecting, it will fail to connect to any Wifi hotspot.

The only way I can get Wifi connection back is to reboot the system. Then it successfully connects to any wifi hotspot, works for 10-20 minutes, hangs again and so on.

Wifi stays connected in Network Manager but there is no traffic and no DNS lookups functioning.

Attaching the output of "wireless-info" script before and after connection hangs.

The only visible difference is that I'm starting getting:
> *wlan0 Interface doesn't support **scanning :** Input/output error*

And syslog shows:
*[ 879.035752] iwlwifi 0000:02:00.0: Scan failed! ret -5*
*[ 880.054628] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd*
*[ 880.054684] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5*
*[ 880.054687] iwlwifi 0000:02:00.0: Scan failed! ret -5*
*[ 881.076756] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd*
*[ 881.076844] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5*
*[ 881.076847] iwlwifi 0000:02:00.0: Scan failed! ret -5*
*[ 882.095744] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd*
*[ 882.095822] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5*
*[ 882.095827] iwlwifi 0000:02:00.0: Scan failed! ret -5*
*[ 883.114708] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd*
*[ 883.114770] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5*
*[ 883.114773] iwlwifi 0000:02:00.0: Scan failed! ret -5*
*[ 884.133801] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd*
[I][ 884.133876] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
[/I]


I have latest **Ubuntu Desktop 17.04**, but this wifi problem was occurring in **16.04** and **16.10** before the upgrade.

---

### Post by joseph.chereshnovsky on 2017-04-24
[B]UPD:
[/B]1. Similar topic on ArchLinux forum: [https://bbs.archlinux.org/viewtopic.php?id=217628](https://bbs.archlinux.org/viewtopic.php?id=217628)
2. Unfixed bug in Fedora bugtracker that looks like exactly the same issue: [https://bugzilla.redhat.com/show_bug.cgi?id=1150593](https://bugzilla.redhat.com/show_bug.cgi?id=1150593)
3. Seems like relevant bug-report for Ubuntu [https://bugs.launchpad.net/ubuntu/+s...x/+bug/1684213](https://bugs.launchpad.net/ubuntu/+s...x/+bug/1684213)

---

### Post by slickymaster on 2017-04-24
*Thread moved to **Networking & Wireless**.*

---

### Post by webdebbyjoss on 2017-06-16
Found another relevant bug reported here:
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1673344](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1673344)

Still can't fix the problem after all this time.

---

### Post by jeremy31 on 2017-06-16
It might be power management causing the issue
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```
That will disable wifi power management

---

