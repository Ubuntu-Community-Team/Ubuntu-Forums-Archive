---
title: "Can't unblock bluetooth on HP Pavillion dv6-6b90ec"
date: 2014-05-08
forum: Networking &amp; Wireless
---

### Post by peto1994 on 2014-05-08
I can't use bluetooth on my hp pavillion dv6-6b90ec. I have single hardware button for both wifi and bluetooth and it is turned on. When I open preinstalled bluetooth application, left panel shows "*Bluetooth is disabled*". Pressing switch in this application to *"on"* position does nothing. I have tryed also "Bluetooth manager". It says: "*Bluetooth Turned OFF. Bluetooth needs to be turned on for the device manager to function*". When I press "*Enable Bluetooth*" button, it shows the same message. 
Output of *rfkill list* is```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
```
*rfkill unblock all* doesn't change anything.
I coulnd't find any solution on google and I'm not expert on linux. Please help.

---

### Post by Hadaka on 2014-05-08
Hi,please post the output of..
```
lspci -nnk | grep -iA3 net
```
and do..
```
sudo apt-get update
sudo rfkill unblock bluetooth
sudo service restart bluetooth
```
thanks.

---

### Post by peto1994 on 2014-05-08
```
lspci -nnk | grep -iA3 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:3388]
    Kernel driver in use: r8169
0d:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008b] (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5315]
    Kernel driver in use: iwlwifi
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)

```

I updated packages, restarting service didn't help.

---

### Post by Hadaka on 2014-05-08
hi,give this a try..
```
sudo modprobe -rf iwlwifi
sudo modprobe -v iwlwifi bt_coex true
```
try that without booting...if it helps we'll write it in.
thanks.

---

### Post by peto1994 on 2014-05-08
```
$ **sudo modprobe -rf iwlwifi**
$ **sudo modprobe -v iwlwifi bt_coex true**
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko bt_coex_active=N bt_coex true
```


Still not working.

---

### Post by Hadaka on 2014-05-08
hi, please boot  and then post the output of..
```
**sudo modprobe -v iwlwifi**
```
thanks

---

### Post by peto1994 on 2014-05-09
```
**sudo modprobe -v iwlwifi**
```

Returned no output.

---

### Post by peto1994 on 2014-06-02
After long time I booted windows on same machine. I turned bluetooth on. After rebooting to ubuntu bluetooth icon appeared at top of the screen. Now I can turn it on, or off, and search for other devices, so it is probably working. I don't know why windows could enable bt and ubuntu couldn't. At least it's working now.

---

