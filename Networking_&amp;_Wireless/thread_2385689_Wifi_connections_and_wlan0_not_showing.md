---
title: "Wifi connections and wlan0 not showing"
date: 2018-02-23
forum: Networking &amp; Wireless
---

### Post by sanjeevsiva17 on 2018-02-23
hey guys, 
wi-fi was working fine until today evening when i came back from a lecture! then i am not able to see wireless connections in the network pop down.

i tried ifconfig, there is no wlan0 in the result!
Ive tried rfkill list, 
```
0: hci0: Bluetooth
 Soft blocked: no
  Hard blocked: no

```
The output for lshw -C network is

```
  *-network               
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 07
       serial: 70:5a:0f:98:12:97
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8106e-1_0.0.1 06/29/12 ip=192.168.1.16 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:124 ioport:4000(size=256) memory:a1200000-a1200fff memory:a1000000-a1003fff
  *-network UNCLAIMED
       description: Network controller
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:a1100000-a1103fff

```

---

### Post by wildmanne39 on 2018-02-23
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by sanjeevsiva17 on 2018-02-23
[http://paste.ubuntu.com/p/jFKKdkP8TQ/](http://paste.ubuntu.com/p/jFKKdkP8TQ/)

---

### Post by wildmanne39 on 2018-02-23
Your driver is not loaded, did you compile this driver yourself and if so what commands did you use? if you did you have to go into the directory where you installed the driver and run make clean then reinstall the driver after a kernel upgrade. Please do
```
sudo modprobe -v rtl8723be
```
does the driver load? if not what error do you receive?

Thanks

---

### Post by sanjeevsiva17 on 2018-02-23
Yes, my driver is a 3rd party open source version!! i had to install it as my wifi had issues!! but that was long time ago, i don't remember which directory I installed it

---

### Post by sanjeevsiva17 on 2018-02-23
sanjeev@sanjeev-HP-Notebook:~$ sudo modprobe -v rtl8723be
insmod /lib/modules/4.4.0-116-generic/updates/dkms/rtlwifi.ko 
modprobe: ERROR: could not insert 'rtl8723be': Exec format error

---

### Post by wildmanne39 on 2018-02-23
Use the ```
locate
```command and see if you can find the driver rtl8723be then ```
cd
```into that directory and do:
```
make clean
```
then do:
```
sudo apt install --reinstall linux-headers-$(uname -r) build-essential dkms git 
git clone https://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install
sudo modprobe -r rtl8723be
sudo modprobe -v rtl8723be

```
Does it work now? Is your kernel a mainstream kernel or did you download and install it from a third party source?

---

### Post by sanjeevsiva17 on 2018-02-23
I tried doing it!! it did not work

The locate command gives!
```


/etc/modprobe.d/rtl8723be.conf
/lib/firmware/rtlwifi/rtl8723befw.bin
/lib/firmware/rtlwifi/rtl8723befw_36.bin
/lib/modules/4.4.0-101-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-101-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-101-generic/updates/dkms/rtl8723be.ko
/lib/modules/4.4.0-109-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-109-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-109-generic/updates/dkms/rtl8723be.ko
/lib/modules/4.4.0-112-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-112-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-112-generic/updates/dkms/rtl8723be.ko
/lib/modules/4.4.0-116-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-116-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-116-generic/updates/dkms/rtl8723be.ko
/lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-34-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-34-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-38-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-38-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-59-generic/updates/dkms/rtl8723be.ko
/lib/modules/4.4.0-62-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-62-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-62-generic/updates/dkms/rtl8723be.ko
/lib/modules/4.4.0-64-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-64-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-64-generic/updates/dkms/rtl8723be.ko
/lib/modules/4.4.0-71-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-71-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-71-generic/updates/dkms/rtl8723be.ko
/lib/modules/4.4.0-72-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-72-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-72-generic/updates/dkms/rtl8723be.ko
/lib/modules/4.4.0-75-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-75-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-75-generic/updates/dkms/rtl8723be.ko
/lib/modules/4.4.0-77-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-77-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-77-generic/updates/dkms/rtl8723be.ko
/lib/modules/4.4.0-78-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-78-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-78-generic/updates/dkms/rtl8723be.ko
/lib/modules/4.4.0-79-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-79-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-79-generic/updates/dkms/rtl8723be.ko
/lib/modules/4.4.0-81-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-81-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-81-generic/updates/dkms/rtl8723be.ko
/lib/modules/4.4.0-83-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-83-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-83-generic/updates/dkms/rtl8723be.ko
/lib/modules/4.4.0-87-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-87-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-87-generic/updates/dkms/rtl8723be.ko
/lib/modules/4.4.0-92-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-92-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-92-generic/updates/dkms/rtl8723be.ko
/lib/modules/4.4.0-93-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-93-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-93-generic/updates/dkms/rtl8723be.ko
/lib/modules/4.4.0-96-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-96-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-96-generic/updates/dkms/rtl8723be.ko
/lib/modules/4.4.0-97-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-97-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-97-generic/updates/dkms/rtl8723be.ko
/lib/modules/4.4.0-98-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-98-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-98-generic/updates/dkms/rtl8723be.ko
/usr/src/linux-headers-4.4.0-101/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-101/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-101-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-109/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-109/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-109-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-112/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-112/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-112-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-116/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-116/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-116-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-21/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-21/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-21-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-31/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-31/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-31-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-34/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-34/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-34-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-36/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-36/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-36-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-38/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-38/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-38-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-45/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-45/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-45-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-59/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-59/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-59-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-62/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-62/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-62-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-64/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-64/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-64-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-71/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-71/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-71-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-72/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-72/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-72-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-75/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-75/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-75-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-77/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-77/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-77-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-78/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-78/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-78-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-79/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-79/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-79-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-81/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-81/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-81-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-83/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-83/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-83-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-87/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-87/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-87-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-92/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-92/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-92-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-93/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-93/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-93-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-96/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-96/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-96-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-97/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-97/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-97-generic/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-98/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-98/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-98-generic/include/config/rtl8723be.h
/usr/src/rtlwifi-new-0.10/rtl8723be
/usr/src/rtlwifi-new-0.10/firmware/rtlwifi/rtl8723befw.bin
/usr/src/rtlwifi-new-0.10/rtl8723be/Makefile
/usr/src/rtlwifi-new-0.10/rtl8723be/def.h
/usr/src/rtlwifi-new-0.10/rtl8723be/dm.c
/usr/src/rtlwifi-new-0.10/rtl8723be/dm.h
/usr/src/rtlwifi-new-0.10/rtl8723be/fw.c
/usr/src/rtlwifi-new-0.10/rtl8723be/fw.h
/usr/src/rtlwifi-new-0.10/rtl8723be/hw.c
/usr/src/rtlwifi-new-0.10/rtl8723be/hw.h
/usr/src/rtlwifi-new-0.10/rtl8723be/led.c
/usr/src/rtlwifi-new-0.10/rtl8723be/led.h
/usr/src/rtlwifi-new-0.10/rtl8723be/modules.order
/usr/src/rtlwifi-new-0.10/rtl8723be/phy.c
/usr/src/rtlwifi-new-0.10/rtl8723be/phy.h
/usr/src/rtlwifi-new-0.10/rtl8723be/pwrseq.c
/usr/src/rtlwifi-new-0.10/rtl8723be/pwrseq.h
/usr/src/rtlwifi-new-0.10/rtl8723be/pwrseqcmd.c
/usr/src/rtlwifi-new-0.10/rtl8723be/pwrseqcmd.h
/usr/src/rtlwifi-new-0.10/rtl8723be/reg.h
/usr/src/rtlwifi-new-0.10/rtl8723be/rf.c
/usr/src/rtlwifi-new-0.10/rtl8723be/rf.h
/usr/src/rtlwifi-new-0.10/rtl8723be/sw.c
/usr/src/rtlwifi-new-0.10/rtl8723be/sw.h
/usr/src/rtlwifi-new-0.10/rtl8723be/table.c
/usr/src/rtlwifi-new-0.10/rtl8723be/table.h
/usr/src/rtlwifi-new-0.10/rtl8723be/trx.c
/usr/src/rtlwifi-new-0.10/rtl8723be/trx.h
/usr/src/rtlwifi-new-0.10/src/rtl8723be
/usr/src/rtlwifi-new-0.10/src/firmware/rtlwifi/rtl8723befw.bin
/usr/src/rtlwifi-new-0.10/src/rtl8723be/modules.order
/var/lib/dkms/rtlwifi-new/0.10/4.4.0-101-generic/x86_64/module/rtl8723be.ko
/var/lib/dkms/rtlwifi-new/0.10/4.4.0-109-generic/x86_64/module/rtl8723be.ko
/var/lib/dkms/rtlwifi-new/0.10/4.4.0-112-generic/x86_64/module/rtl8723be.ko
/var/lib/dkms/rtlwifi-new/0.10/4.4.0-116-generic/x86_64/module/rtl8723be.ko
/var/lib/dkms/rtlwifi-new/0.10/4.4.0-59-generic/x86_64/module/rtl8723be.ko
/var/lib/dkms/rtlwifi-new/0.10/4.4.0-62-generic/x86_64/module/rtl8723be.ko
/var/lib/dkms/rtlwifi-new/0.10/4.4.0-64-generic/x86_64/module/rtl8723be.ko
/var/lib/dkms/rtlwifi-new/0.10/4.4.0-71-generic/x86_64/module/rtl8723be.ko
/var/lib/dkms/rtlwifi-new/0.10/4.4.0-72-generic/x86_64/module/rtl8723be.ko
/var/lib/dkms/rtlwifi-new/0.10/4.4.0-75-generic/x86_64/module/rtl8723be.ko
/var/lib/dkms/rtlwifi-new/0.10/4.4.0-77-generic/x86_64/module/rtl8723be.ko
/var/lib/dkms/rtlwifi-new/0.10/4.4.0-78-generic/x86_64/module/rtl8723be.ko
/var/lib/dkms/rtlwifi-new/0.10/4.4.0-79-generic/x86_64/module/rtl8723be.ko
/var/lib/dkms/rtlwifi-new/0.10/4.4.0-81-generic/x86_64/module/rtl8723be.ko
/var/lib/dkms/rtlwifi-new/0.10/4.4.0-83-generic/x86_64/module/rtl8723be.ko
/var/lib/dkms/rtlwifi-new/0.10/4.4.0-87-generic/x86_64/module/rtl8723be.ko
/var/lib/dkms/rtlwifi-new/0.10/4.4.0-92-generic/x86_64/module/rtl8723be.ko
/var/lib/dkms/rtlwifi-new/0.10/4.4.0-93-generic/x86_64/module/rtl8723be.ko
/var/lib/dkms/rtlwifi-new/0.10/4.4.0-96-generic/x86_64/module/rtl8723be.ko
/var/lib/dkms/rtlwifi-new/0.10/4.4.0-97-generic/x86_64/module/rtl8723be.ko
/var/lib/dkms/rtlwifi-new/0.10/4.4.0-98-generic/x86_64/module/rtl8723be.ko
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be
/var/lib/dkms/rtlwifi-new/0.10/build/firmware/rtlwifi/rtl8723befw.bin
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/Makefile
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/def.h
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/dm.c
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/dm.h
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/fw.c
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/fw.h
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/hw.c
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/hw.h
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/led.c
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/led.h
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/phy.c
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/phy.h
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/pwrseq.c
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/pwrseq.h
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/pwrseqcmd.c
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/pwrseqcmd.h
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/reg.h
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/rf.c
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/rf.h
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/sw.c
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/sw.h
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/table.c
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/table.h
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/trx.c
/var/lib/dkms/rtlwifi-new/0.10/build/rtl8723be/trx.h
/var/lib/dkms/rtlwifi-new/0.10/build/src/rtl8723be
/var/lib/dkms/rtlwifi-new/0.10/build/src/firmware/rtlwifi/rtl8723befw.bin




```


Then i did a  cd /var/lib/dkms/rtlwifi-new/0.10/build/src/firmware/rtlwifi/

And then when i did make clean
```


make: *** No rule to make target 'clean'.  Stop.


```

Here is the ls command
```

rtl8188efw.bin  rtl8192cfwU_B.bin  rtl8192defw_12.bin  rtl8192eefw.bin      rtl8192sefw.bin      rtl8723befw.bin  rtl8723fw.bin    rtl8812aefw_wowlan.bin  rtl8821aefw_wowlan.bin
rtl8192cfw.bin  rtl8192cfwU.bin    rtl8192defw.bin     rtl8192eefw_new.bin  rtl8192sefw.old.bin  rtl8723fw_B.bin  rtl8812aefw.bin  rtl8821aefw.bin         rtlwifi_new

```

---

### Post by wildmanne39 on 2018-02-24
Go ahead and run these commands:
```
sudo apt install --reinstall linux-headers-$(uname -r) build-essential dkms git 
git clone https://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install
sudo modprobe -r rtl8723be
sudo modprobe -v rtl8723be
```
If the directory already exists then you will get a message saying so and you can go into that directory and run:
```
make clean
```
no message to that effect then run all the commands and see if it works.

---

### Post by sanjeevsiva17 on 2018-03-01
Install rtlwifi SUCCESS
sanjeev@sanjeev-HP-Notebook:/var/lib/dkms/rtlwifi-new/0.10/build/src/rtlwifi_new$ sudo modprobe -r rtl8723be
sanjeev@sanjeev-HP-Notebook:/var/lib/dkms/rtlwifi-new/0.10/build/src/rtlwifi_new$ sudo modprobe -v rtl8723be
insmod /lib/modules/4.4.0-116-generic/updates/dkms/rtlwifi.ko 
modprobe: ERROR: could not insert 'rtl8723be': Exec format error
sanjeev@sanjeev-HP-Notebook:/var/lib/dkms/rtlwifi-new/0.10/build/src/rtlwifi_new$

---

