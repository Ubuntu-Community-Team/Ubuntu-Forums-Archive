---
title: "I cannot configure a SIM Card in Ubuntu 16.04.6 LTS"
date: 2019-04-12
forum: Networking &amp; Wireless
---

### Post by stevencarle93 on 2019-04-12
Hello.


I am trying to connect a device specialized to run IIoT (Industrial Internet of Things) applications using a mobile data plan active with AT&T USA. This device name is ICO120-83D of the manufacturer Axiomtek. The operating system that I installed was Ubuntu 16.04.6 LTS. Now I am using a stantard size SIM Card to connect this device to internet and get remote access using a Public Static IP Address, but I could'nt get the connection stablished from Ubuntu and BIOS neither. Please help me out to detect and configure the SIM Card.


The following are some commands outputs which I have tried:


*tazman@TazmanTurbinz:~$ sudo mmcli -i 0*
*[sudo] password for tazman:*
[I]error: couldn't find sim at '/org/freedesktop/ModemManager1/SIM/0': 'no modems found'

[/I]*tazman@TazmanTurbinz:~$ sudo mmcli -m 0 enable --timeout=120*
*[sudo] password for tazman:*
[I]error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/0'

[/I]*tazman@TazmanTurbinz:~$ lspci*
*00:00.0 Host bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Host Bridge (rev 0b)*
*00:02.0 VGA compatible controller: Intel Corporation Device 5a85 (rev 0b)*
*00:0f.0 Communication controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Trusted Execution Engine (rev 0b)*
*00:12.0 SATA controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SATA AHCI Controller (rev 0b)*
*00:13.0 PCI bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series PCI Express Port A #1 (rev fb)*
*00:13.1 PCI bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series PCI Express Port A #2 (rev fb)*
*00:13.3 PCI bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series PCI Express Port A #4 (rev fb)*
*00:15.0 USB controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series USB xHCI (rev 0b)*
*00:1f.0 ISA bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Low Pin Count Interface (rev 0b)*
*00:1f.1 SMBus: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SMBus Controller (rev 0b)*
*01:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)*
*02:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)*
[I]03:00.0 Network controller: Qualcomm Atheros AR958x 802.11abgn Wireless Network Adapter (rev 01)

[/I]*tazman@TazmanTurbinz:~$ iwconfig*
*wlp3s0    IEEE 802.11abgn  ESSID:off/any*
*          Mode:Managed  Access Point: Not-Associated   Tx-Power=3 dBm*
*          Retry short limit:7   RTS thr:off   Fragment thr:off*
*          Power Management:off*

*enp2s0    no wireless extensions.*

*lo        no wireless extensions.*

*enp1s0    no wireless extensions.*



*tazman@TazmanTurbinz:~$ rfkill list*
*0: phy0: Wireless LAN*
*        Soft blocked: no*
*        Hard blocked: no*





Thank you very much and I will be waiting for your response as soon as possible.


Best regards,


Steven Carvajal Lenis.

---

### Post by Al_Klein on 2019-05-05
A Public Static IP Address?  One not being used by any other device anywhere?  Remember, an IP address can be used by only *one* device on any network, and if you're connecting to the internet, that would have to be an address assigned by your ISP.  Otherwise it's being used by something else, you're getting an IP address conflict, and it won't work.

(Besides, why are you putting an IP address into a **SIM card**?  They're normally used for connection to a cellphone carrier.)

---

