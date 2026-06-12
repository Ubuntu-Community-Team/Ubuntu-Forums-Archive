---
title: "Wireless Internet in Kubuntu"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by RAZRBAKK on 2009-03-19
I've installed, and I've got Kubuntu working great, except for one little thing... The wifi internet.

Back when I was trying to do this on regular Ubuntu, I was sent an email that had very good instructions. I never did get around to doing it, though.

This is what the email contained:

> Try this:
Boot into Ubuntu, and open a terminal window. Use lspci to see what your system has for a Wifi
controller. Here is what my computer displays. Now all you need is the Driver for the Atheros
AR242x (rev 01) Wireless PCI Adapter to make it functional.
The following commands can be used to check out your Wifi information.
From a Terminal Window:
lspci
larry@ubuntu:~$ lspci
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
lspci -v | less
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
larry@ubuntu:~$ lsmod | grep ath
ath_rate_sample 16128 1 
ath_pci 249016 0 
wlan 236400 4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal 305376 3 ath_rate_sample,ath_pci
larry@ubuntu:~$ lshw -C Network
larry@ubuntu:~$ dmesg | grep -e iwl -e wlan -e ath
[ 33.215950] ath_hal: module license 'Proprietary' taints kernel.
[ 33.809495] MadWifi: ath_attach: Switching rfkill capability off.
[ 33.892481] ath_pci: wifi0: Atheros 5424/2424: mem=0xd2600000, irq=20
[ 74.428240] ath0: no IPv6 routers present
larry@ubuntu:~$
larry@ubuntu:~$ lspci -nn
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
larry@ubuntu:~$ 
larry@ubuntu:~$ iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
wifi0 no wireless extensions.
ath0 IEEE 802.11g ESSID:"" Nickname:""
Mode:Managed Frequency:2.437 GHz Access Point: Not-Associated 
Bit Rate:0 kb/s Tx-Power:16 dBm Sensitivity=1/1 
Retry:off RTS thr:off Fragment thr:off
Power Management:off
Link Quality=0/70 Signal level=-96 dBm Noise level=-96 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
larry@ubuntu:~$ iwlist scanning
lo Interface doesn't support scanning.
eth0 Interface doesn't support scanning.
wifi0 Interface doesn't support scanning.
ath0 No scan results
Go here and follow the steps to install the Wifi Drivers.
[http://ubuntuforums.org/showthread.p...light=AR5007EG](http://ubuntuforums.org/showthread.p...light=AR5007EG)
If your Wifi still doesn't work try blacklisting the Restricted Hardware Drivers. 
sudo gedit /etc/modprobe.d/blacklist
#blacklist the Hardware Drivers (Restricted)
blacklist ath_hal
blacklist ath_pci
Reboot and see if your CQ50's Wifi is functional.

I gave this a try, with no results. Anyone else care to help?

The computer is a Compaq Presario CQ50. It has 2gb of ram, and a 160 gb HDD. The wireless card is an Atheros AR5007.

Thanks!

---

### Post by RAZRBAKK on 2009-03-19
Bump!

---

### Post by Chesamo on 2009-03-19
Did you try using NDISWrapper and the Windows drivers?

---

### Post by RAZRBAKK on 2009-03-19
> **Chesamo said:**
> Did you try using NDISWrapper and the Windows drivers?

I did, but I don't know which part of the driver I should use. Each one is a .exe file, so I have to run it in windows. What part of the driver do I need?

---

### Post by RAZRBAKK on 2009-03-19
bump

---

### Post by RAZRBAKK on 2009-03-19
Also, currently my network manager will not open.

I have installed NDISwrapper, and I've installed the correct driver, but still no wifi...

---

### Post by redbob on 2009-03-19
You must turn on your wireless device. Type it:
> sudo iwconfig ath0 power on

---

### Post by RAZRBAKK on 2009-03-19
This is what I get:

> skeletor@skeletor-laptop:~$ sudo iwconfig ath0 power on
[sudo] password for skeletor:
Error for wireless request "Set Power Management" (8B2D) :
    GET failed on device ath0 ; No such device.


---

### Post by RAZRBAKK on 2009-03-19
Ok, I got a recognizable driver that has the hardware present, but I don't know where to go from here...

---

### Post by RAZRBAKK on 2009-03-19
Does anyone think I would have better luck installing Ubuntu 8.10, getting the interwebz working, and THEN installing the KDE package?

---

### Post by iliya on 2009-03-19
> **RAZRBAKK said:**
> Ok, I got a recognizable driver that has the hardware present, but I don't know where to go from here...

I have the same problem! I have Dell inspiron 1525, have LAN connection, wireless button is on, but I have no Wireless connection.Give me some solutions pls!
I want to underline I`m newbie :) Thanks in advance ;)

Edit : Installed Kubuntu 8.10 and KDE 4.1

---

### Post by RAZRBAKK on 2009-03-19
Bump!

---

### Post by redbob on 2009-03-20
Hi,Razr...

I suggested you do power on ath0 because iwconfig identified your wireless as ath0, but may be you wireless device is under other identification... type > ifconfig then you tell me which devices are in the box.
Iliya: Try this:
> [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

