---
title: "Eagle-usb problems"
date: 2005-10-13
forum: Networking &amp; Wireless
---

### Post by sebastianw on 2005-10-13
When I had (K)ubntu 5.04 hoary I installed drivers for my sagem f@st 800 adsl modem with eagle-usb chipset just by typing:

sudo apt-get install eagle-usb-data 
sudo apt-get isntall eagle-usb-utils 
sudo eagleconfig 

and my internet connection works fine.

Now I download 5.10 Breezy - but when I want to do thesame after install it i have "command line 45 error" during loading drivers module (eaglectrl -d)

Cause I has no internet conection with Breezy I must back to Hoary :(

-- 
sorry about my english ;>

---

### Post by groblus on 2005-10-13
i've got a problem with sagem to, it gives me something like this:

> ~$ startadsl


Modem is not operational!
Check eaglestat result to know its state!

aem@ubuntu:~$ eaglestat
eagle-usb status display
-------------------------------------------------------------
Driver version 2.1.2 Chipset: Eagle0
Vendor ID : 0x1110 Product ID : 0x9031 Rev: 0x200b
USB Bus : 004 USB Device : 002 Dbg mask: 0x0
Ethernet Interface : none
MAC: 00:60:4c:71:23:76
Tx Rate 0 Rx Rate 0
FEC 0 Margin 0 Atten 0 dB
VID-CPE 0 VID-CO 0 HEC 0
VPI 0 VCI 0 Delin GOOD
Cells Tx 0 Cells Rx 0
Pkts Tx 0 Pkts Rx 0
OAM 0 Bad VPI 0 Bad CRC 0
Oversiz. 0

Modem waiting for driver response.
Please send DSP (eaglectrl -d)

aem@ubuntu:~$ eaglectrl -d
Unknown option on line 27
Unknown option on line 28
Unknown option on line 29
Unknown option on line 30
Unknown option on line 31
Unknown option on line 32
Unable to send options to driver: Unknown error 512

and of course no internet connection. What's wrong ?
thx for any help

---

### Post by goomior on 2005-10-14
The solution is [here](http://ubuntuforums.org/showthread.php?t=71293).

---

### Post by capitan.harlock on 2005-10-16
I tried, but I'm sorry nothing changed for me, still same error messages as above.

---

### Post by goomior on 2005-10-27
Try to reinstall eagle-usb-utils and eagle-usb-data. Also use package equivalent for your "uname -r".

---

### Post by capitan.harlock on 2005-10-27
Did it; no luck, sorry...

---

