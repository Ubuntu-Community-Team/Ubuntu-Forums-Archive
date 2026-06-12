---
title: "how to configure internet access"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by drtanz on 2008-11-17
Hi I have installed Ubuntu 8.04 server edition, while I was installing the DHCP settings were not detected so I skipped that part of the install, and now when I try to download a package using the cli I get errors that the address is not resolving. I guess then that internet access is not set on my Ubuntu server. How can I set this? My wireless router is set to use DHCP.

---

### Post by hictio on 2008-11-17
Try this from the CLI:

```

sudo dhclient -r (ENTER)
sudo dhclient (ENTER)

```

---

### Post by drtanz on 2008-11-18
I am getting no dhcpoffers received

wireless is working fine on my other os (vista) installed on the laptop

---

### Post by spiderbatdad on 2008-11-18
Perhaps this thread belongs in Networking & Wireless, or ABT? Is your wireless network using wpa or any security? Can you post the output of ```
sudo iwlist wlan0 scan
```substitute wlan0 for the appropriate wireless interface, if necessary...iwconfig to see interface.

---

### Post by bapoumba on 2008-11-19
Moved to Networking & Wireless.

---

### Post by drtanz on 2008-11-20
hi still no success, wlan0 is the only one available when i try iwconfig, but then when i try the command you gave me i get:

interface does not support scanning: Network is down.

any further help? thanks

---

### Post by drtanz on 2008-11-21
any further help on this? thanks

---

### Post by srilyk on 2008-11-21
try typing this:

sudo ifconfig wlan0 up
sudo iwlist wlan0 scan

then post your output

---

### Post by drtanz on 2008-11-21
wla0   Interface doesn't support scanning

---

### Post by kevdog on 2008-11-21
You need to troubleshoot your driver using the command line (which there is a link in my sig).  I would first trouleshoot the driver install using lshw -C network and lsmod to see if the wireless kernel module is loaded.  Then check dmesg to see if there was an error when the driver was loaded.

---

