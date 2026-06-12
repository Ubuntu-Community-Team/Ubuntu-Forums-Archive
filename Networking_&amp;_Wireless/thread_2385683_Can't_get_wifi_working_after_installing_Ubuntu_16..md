---
title: "Can't get wifi working after installing Ubuntu 16.04 LTS"
date: 2018-02-23
forum: Networking &amp; Wireless
---

### Post by mikerichards123 on 2018-02-23
When I first installed Ubuntu I was able to access the Wifi during set-up. This worked initially, but has since dropped and now when I select the Wifi icon on the top bar there are no available networks to search for, instead a greyed out message saying 'Ethernet Network disconnected' yet I have not connected using an Ethernet cable since installing.

I have tried a number of solutions including ```
sudo systemctl restart network-manager 
```and altering false to true in NetworkManager.conf

As you can probably tell I'm very new to this. Any help would be massively appreciated.

Thanks in advance

---

### Post by kc1di on 2018-02-23
Hello mikerichards123 and Welcome to Ubuntu Forums,

could you go to a terminal and type the following commands and post the output here:
```
rfkill list
```
```
sudo lshw -C network
```

---

### Post by slickymaster on 2018-02-23
Thread moved to **Networking & Wireless** for a better fit

---

### Post by mikerichards123 on 2018-02-26
Hi kc1di, Thanks for your response!

```

rfkill list
```

returns:
```
0: tpacpi_bluetooth_sw: Bluetooth
     Soft blocked: no
     Hard blocked: no

1: hci0: Bluetooth
     Soft blocked: no
     Hard blocked: no
```


```
sudo lshw -C network
```

returns:
```

*-network UNCLAIMED     
       description: Network controller
       product: Wireless 8260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 3a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f1000000-f1001fff
  *-network
       description: Ethernet interface
       product: Ethernet Connection I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 21
       serial: c8:5b:76:c6:10:00
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:123 memory:f1200000-f121ffff
```

---

### Post by jeremy31 on 2018-02-27
What happens if you ```
sudo modprobe -v iwlwifi
```

---

### Post by mikerichards123 on 2018-02-27
Thanks Jeremy - I tried ```
[COLOR=#000000][FONT=&quot]sudo modprobe -v iwlwifi[/FONT][/COLOR]
``` but nothing was returned in the terminal

---

### Post by jeremy31 on 2018-02-27
Any results for ```
dmesg | grep iwl
```
Unclaimed usually means no module but it could be a firmware issue

---

### Post by mikerichards123 on 2018-02-27
Yes! Doesn't look great though..

```
[    4.167839] iwlwifi 0000:04:00.0: enabling device (0000 -> 0002)[    4.190611] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-8000C-33.ucode failed with error -2
[    4.190631] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-8000C-32.ucode failed with error -2
[    4.190640] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-8000C-31.ucode failed with error -2
[    4.190649] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-8000C-30.ucode failed with error -2
[    4.190656] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-8000C-29.ucode failed with error -2
[    4.190666] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-8000C-28.ucode failed with error -2
[    4.190676] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-8000C-27.ucode failed with error -2
[    4.190687] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-8000C-26.ucode failed with error -2
[    4.190694] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-8000C-25.ucode failed with error -2
[    4.190702] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-8000C-24.ucode failed with error -2
[    4.190709] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-8000C-23.ucode failed with error -2
[    4.190717] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-8000C-22.ucode failed with error -2
[    4.190718] iwlwifi 0000:04:00.0: no suitable firmware found!
[    4.190721] iwlwifi 0000:04:00.0: minimum version required: iwlwifi-8000C-22
[    4.190723] iwlwifi 0000:04:00.0: maximum version supported: iwlwifi-8000C-33
[    4.190725] iwlwifi 0000:04:00.0: check git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git



```

---

### Post by jeremy31 on 2018-02-27
Download [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-8000C-22.ucode](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-8000C-22.ucode) put it on a flash drive on copy it to the Ubuntu desktop, then in terminal do
```
cd Desktop
sudo cp iwlwifi-8000C-22.ucode /lib/firmware/
```
Reboot

---

### Post by mikerichards123 on 2018-02-27
That's worked - Thanks jeremy31!

---

### Post by jeremy31 on 2018-02-27
Now open terminal
```
sudo apt-get install linux-firmware
```
Use the thread tools menu near the top right of the page to mark as solved

---

