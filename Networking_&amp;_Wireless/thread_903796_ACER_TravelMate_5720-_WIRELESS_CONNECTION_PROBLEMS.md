---
title: "ACER TravelMate 5720- WIRELESS CONNECTION PROBLEMS"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by alfaalbert on 2008-08-28
Hello,

I have got two Operating Systems in my notebook: WINDOWS VISTA (WV) AND UBUNTU 8.04. With WV I do not have any wireless problem, but with ubuntu... it does not detect any wireless connection. At home (I am in a foreign country studying) I used cable/wire connection with an ADSL modem.

I did most of the steps of the Ubuntu Linux Help, ubuntu recognize the hardware but I could not see wireless connections. In addition, I could not switch the wireless device on (please see the attached TERMINAL REPORTS: Terminal: 1. lspci, 2. sudo lshw -C networky and 3. iwconfig)

albert@albert-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03) 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) 00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) 00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) 00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) 00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) 00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) 00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) 00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) 00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) 00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) 00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03) 00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) 00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03) 00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03) 02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02) 04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02) 0f:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller 0f:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller 0f:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) 0f:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller albert@albert-laptop:~$


albert@albert-laptop:~$ sudo lshw -C network [sudo] password for albert: *-network description: Ethernet interface product: NetLink BCM5787M Gigabit Ethernet PCI Express vendor: Broadcom Corporation physical id: 0 bus info: pci@0000:02:00.0 logical name: eth0 version: 02 serial: 00:1d:72:32:90:be capacity: 1GB/s width: 64 bits clock: 33MHz capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.23 latency=0 link=no module=tg3 multicast=yes port=twisted pair *-network description: Wireless interface product: PRO/Wireless 3945ABG Network Connection vendor: Intel Corporation physical id: 0 bus info: pci@0000:04:00.0 logical name: wmaster0 version: 02 serial: 00:1f:3c:2f:61:04 width: 32 bits clock: 33MHz capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

albert@albert-laptop:~$ iwconfig lo no wireless extensions. eth0 no wireless extensions. irda0 no wireless extensions. wmaster0 no wireless extensions. wlan0 IEEE 802.11g ESSID:"" Nickname:"" Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated Tx-Power=27 dBm Retry min limit:7 RTS thrff Fragment thr=2346 B Power Managementff Link Quality:0 Signal level:0 Noise level:0 Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0 Tx excessive retries:0 Invalid misc:0 Missed beacon:0****

---

### Post by coffeecat on 2008-08-28
According to your lspci output, you have the...

> Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)...wireless chipset. I read on another thread that you need the linux-restricted-modules-generic installed* before the Intel 3945 chipset will work, although I cannot confirm this from personal experience. Try installing that package, if it's not installed already.

By the way, how did you manage to lose all the line breaks in your lspci output? It's almost impossible to read. Next time you post some terminal output, can I suggest you copy and paste directly from the terminal into the Firefox message field? That way the output should be readable. It's also helpful to other forum members trying to help you if you place terminal output in [noparse]```

```[/noparse] tags. That way any formatting is retained.

* **Edit:** That looks to have been a misleading post on that other thread. I've looked in all my Ubuntu installs, and they all have the linux-restricted-modules-generic package installed. It looks as though that package comes with a default install.

The only other thing I can suggest is to search the forum for threads on your wireless chipset - there have been several.

---

### Post by alfaalbert on 2008-09-13
Hi coffeecat:

I found a similar problem with the same wireless chipset in: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226411](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226411)

The important steps are:
[B]
What worked for me was the following :

- Installed the backports updates with the latets updated drivers
But after a day or so it appeared I couldn't find any networks (this error appeared random)

- Installed wicd instead of network-manager.
Again only helped temporarily

- Then I found the following sollution in BugZilla ([http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1579):](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1579):)

Creating /etc/modprobe.d/iwl3945 with the following contents :
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1
[/B]

[COLOR="Navy"]Could you explain how to do the first two steps in linux (and if it is possible how to do the same but downloading from windows and then installing in linux)?

Thank you in advance.[/COLOR]

---

