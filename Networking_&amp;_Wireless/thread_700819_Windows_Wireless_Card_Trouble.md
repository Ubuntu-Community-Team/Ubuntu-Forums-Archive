---
title: "Windows Wireless Card Trouble"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by CJWild8 on 2008-02-18
I'm having trouble getting a connection going using my windows wireless card, my laptop is a Toshiba A100-TA7. I've attempted installing ndiswrapper but now i'm stuck with the .inf driver portion of the task. If someone has msn and wouldn't mind walking me through this or at the least post a reply to steer me in the right direction.

any help is greatly appreciated

---

### Post by agim on 2008-02-18
Okay, so I assume you have your wireless driver. I will also assume that you know how to set up ndiswrapper (make, make install). If you have done those things, all you have to do is move to the directory where you have your .inf file, and type these commands

sudo ndiswrapper -i bcmwl5.inf
sudo modprobe ndiswrapper

then add the word ndiswrapper to /etc/modules

---

### Post by anidritesolforosa on 2008-02-18
Try installing ndisgtk, it is a graphical interface to install the .inf file make sure that after that in the System >Administration>Windows Wireless Drivers appears your driverand it says "Hardware Present:YES"

---

### Post by CJWild8 on 2008-02-18
I don't have the wireless driver yet.... where do I get it? I know it's probably a little noobish but I am trying lol

---

### Post by agim on 2008-02-18
its ok. Don't worry about being noobish. we all were.
Type lspci into the terminal and paste the output here.

---

### Post by CJWild8 on 2008-02-18
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

---

### Post by rustybronco on 2008-02-18
[http://ubuntuforums.org/showthread.php?t=700781](http://ubuntuforums.org/showthread.php?t=700781)
one thread is sufficient :)

you chipset is 05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

you can google this chipset and revision for the proper windows driver, or when I get done making dinner I will be glad to find it for you

---

### Post by rustybronco on 2008-02-18
[http://ubuntuforums.org/showthread.php?p=3389624#post3389624](http://ubuntuforums.org/showthread.php?p=3389624#post3389624)
[http://www.intel.com/](http://www.intel.com/)

b.l.t's yum!!!!!!!!!!

---

### Post by rustybronco on 2008-02-18
CJWild8,
There are a lot of threads on that wireless device, search around a little.
I don't have any experience with that chipset but a few things that come to mind are to open a terminal and type in these commands.

**uname -a** 
**lshw -C network**
**iwlist scan**
and post the output of them.

If i'm not mistaken there is support for the ipw3945 in 7.10 "gutsy" but again I don't have experience with that device.
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)

Intel linux drivers  [http://support.intel.com/support/notebook/sb/CS-006408.htm](http://support.intel.com/support/notebook/sb/CS-006408.htm)

also a ndiswrapper guide [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501) did you unzip the exe that you found and extract the .inf to use with ndiswrapper?

kind of hard following you around town.    [http://ubuntuforums.org/showthread.php?p=4358912#post4358912](http://ubuntuforums.org/showthread.php?p=4358912#post4358912)  [http://ubuntuforums.org/showthread.php?t=700781](http://ubuntuforums.org/showthread.php?t=700781)
Please feel free to ask questions, I'll help all that I can.

---

### Post by CJWild8 on 2008-02-19
cody@cody-laptop:~$ uname -a
Linux cody-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux
cody@cody-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:ae:c3:a2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 module=ipw3945 multicast=yes wireless=unassociated
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:07:08.0
       logical name: eth0
       version: 02
       serial: 00:a0:d1:60:6c:be
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A ip=192.168.0.101 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
cody@cody-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1E:52:78:17:BD
                    ESSID:"HOME2"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=43/100  Signal level=-83 dBm  Noise level=-83 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (2) : TKIP WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 24ms ago
          Cell 02 - Address: 00:13:46:F3:E3:B0
                    ESSID:"ryaneric"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=55/100  Signal level=-75 dBm  Noise level=-75 dBm
                    Extra: Last beacon: 612ms ago
          Cell 03 - Address: 00:1B:11:4F:D7:4D
                    ESSID:"Tha Boyz"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=58/100  Signal level=-73 dBm  Noise level=-73 dBm
                    Extra: Last beacon: 52ms ago
          Cell 04 - Address: 00:E0:98:53:FA:5C
                    ESSID:"Untitled"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=52/100  Signal level=-77 dBm  Noise level=-77 dBm
                    Extra: Last beacon: 680ms ago
          Cell 05 - Address: 00:13:A3:34:FA:A3
                    ESSID:"home"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=42/100  Signal level=-84 dBm  Noise level=-84 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 32ms ago

---

### Post by rustybronco on 2008-02-19
> **CJWild8 said:**
> cody@cody-laptop:~$ uname -a
Linux cody-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 **x86_64** GNU/Linux
cody@cody-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless **3945ABG** Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: **eth1**
       version: 02
       serial: 00:18:de:ae:c3:a2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **driver=ipw3945** driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 **module=ipw3945[/ b] multicast=yes [b]wireless=unassociated**
  
eth1      Scan completed :
          Cell 01 - Address: 00:1E:52:78:17:BD
                    ESSID:"HOME2"
                   
          Cell 02 - Address: 00:13:46:F3:E3:B0
                    ESSID:"ryaneric"
                   
          Cell 03 - Address: 00:1B:11:4F:D7:4D
                    ESSID:"Tha Boyz"
                  
          Cell 04 - Address: 00:E0:98:53:FA:5C
                    ESSID:"Untitled"
                   
          Cell 05 - Address: 00:13:A3:34:FA:A3
                    ESSID:"home"
                   
you can see the wireles connections but can't connect correct?
if so maybe changing the driver from ipw3945 to the iwl3945 may be the answer (see link below)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/121439/comments/120](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/121439/comments/120)
taken from this thread  [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/158045](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/158045)

*****newly found post*****  [http://ubuntuforums.org/showpost.php?p=4343525&postcount=1](http://ubuntuforums.org/showpost.php?p=4343525&postcount=1)

Again I don't know much about that device, but what I have read it can be problematic, maybe someone that has experience with it will jump in.
[https://bugs.launchpad.net/bugs/+bugs?field.searchtext=ipw3945&search=Search+Bug+Reports&field.scope=all&field.scope.target=](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=ipw3945&search=Search+Bug+Reports&field.scope=all&field.scope.target=)

I'll be looking in on this thread, I won't abandon you.
Dale

---

### Post by rustybronco on 2008-02-20
plus would you post the output of     **dmesg | grep 3945**

see this thread also  [http://ubuntuforums.org/showthread.php?t=702407](http://ubuntuforums.org/showthread.php?t=702407)

---

