---
title: "Switching to Monitor mode [MacBook 8.1]"
date: 2014-12-31
forum: Networking &amp; Wireless
---

### Post by mancer03 on 2014-12-31
I have read and tried as many posted tutorials as possible and still can't get this to work. Any assistance will be appreciated. I can't use "airodump-ng wlan#". 

Interface    Chipset        Driver

wlan0        Unknown     wl - [phy0]mon0: ERROR while getting interface flags: No such device

                (monitor mode enabled on mon0)

root@mancer03-MacBookPro:~# iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"--------"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 98:FC:11:D1:43:07   
          Bit Rate=54 Mb/s   Tx-Power=200 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2014-12-31
Please try:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
iwconfig
```Does the mode show as 'Monitor?' Not every device and driver combination does every mode, especially monitor.

I haven't the device, so I don't know if this works or not: [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)> HOW TO USE MONITOR MODE
-----------------------
To enable monitor mode:
$ echo 1 > /proc/brcm_monitor0

Enabling monitor mode will create a 'prism0' network interface. Wireshark and
other netwokk tools can use this new prism0 interface.

To disable monitor mode:
$ echo 0 > /proc/brcm_monitor0

DISCLAIMER: I know nothing about aircrack, airodump or aircrazzzy. I can't tell you more.

---

### Post by mancer03 on 2014-12-31
Chili555 thank you for the reponse. I have tried that but it gives me this:

Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.

I have downloaded firmware-b43 and backports as well and nothing has changed. Any other suggestions or maybe something that Im missing would help.

---

### Post by mancer03 on 2014-12-31
Here is device info:

root@mancer03-MacBookPro:~# lspci -n | grep 14e4:
02:00.0 0200: 14e4:16b4 (rev 10)
02:00.1 0805: 14e4:16bc (rev 10)
03:00.0 0280: 14e4:4331 (rev 02)

---

### Post by overdrank on 2014-12-31
Hi and welcome. Your issue is not support on the forums. Thread closed

---

