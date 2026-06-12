---
title: "Sagem F@ST 800 E3"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by Matt C on 2007-02-17
Hi, I'm having trouble getting my ADSL modem, a SAGEM F@ST 800 E3, working on a fresh install of Ubuntu 6.10.

I installed a couple of relevant packages from the Ubuntu CD: eagle-usb-utils and eagle-usb-data, and was prompted me to select my ISP (Tiscali in the UK). However, I've not had any joy in getting the driver to work. Below are bits of output from various commands which may or may not be relevant. Thanks for any help!
```
[FONT="Courier New"]
matthew@matthew-desktop:~$ eaglediag 
Diagnostic (1.21 2005/01/16) driver eagle-usb 20070216191021
# System Information
Linux matthew-desktop 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux
testing/unstable
Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5) used : 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
# module loaded ?        [ OK ]
# modem operational ?    [ KO ]
# Config vpi/vci/encapsulation/isp :  26 6 (pppoa) UK01
# pppd launched ?        [ KO ]
# ping IP ?              [ KO ]
# test DNS resolution ?  [ KO ]
--------------
matthew@matthew-desktop:~$ eaglectrl -d
Unknown option on line 27
Unknown option on line 28
Unknown option on line 29
Unknown option on line 30
Unknown option on line 31
Unknown option on line 32
Unable to send options to driver: Unknown error 512

---------------
This produces the following line in /var/log/kern.log:
Feb 16 19:10:45 matthew-desktop kernel: [17180491.680000] [EAGLE-USB] EU_IO_OPTIONS: CMVs not yet sent.

-----------------------------
matthew@matthew-desktop:~$ eaglestat 
eagle-usb status display
-------------------------------------------------------------
Driver version 2.3.2     Chipset: Eagle0
Vendor ID : 0x1110     Product ID : 0x9031   Rev: 0x200b
USB Bus : 003    USB Device : 002        Dbg mask: 0x0
Ethernet Interface : <NULL>
MAC: 00:60:4c:71:6a:fa
Tx Rate           0  Rx Rate           0
FEC               0  Margin            0  Atten             0 dB
VID-CPE           0  VID-CO            0  HEC               0
VPI               0  VCI               0  Delin          GOOD
Cells Tx          0  Cells Rx          0
Pkts Tx           0  Pkts Rx           0
OAM               0  Bad VPI           0  Bad CRC           0
Oversiz.          0

Modem waiting for driver response.
Please send DSP (eaglectrl -d)[/FONT]

```

---

### Post by chggr on 2007-02-18
I'm afraid that the drivers of the ubuntu CD won't work.
You have to install the ueagle-usb drivers.

Just follow the instructions of this topic and you should be OK:
[http://ubuntuforums.org/showthread.php?t=201127&highlight=sagem+fast](http://ubuntuforums.org/showthread.php?t=201127&highlight=sagem+fast)

PS. Normally you should follow the procedure described after the line "Both the Dapper and Edgy kernels come with eagle-usb and usbatm modules that need removing"

---

### Post by Matt C on 2007-02-19
The linked instructions worked like a charm. Cheers!

---

