---
title: "Wireless LAN USB Adapter not working"
date: 2006-07-18
forum: Networking &amp; Wireless
---

### Post by Aurorius on 2006-07-18
Hi..

This is my second time trying to install my wireless usb and I really hope it will work. 

I've tried following ndiswrapper guide and I think I've installed the driver correctly, but it seems it can't connect to my router. I did enable mac address filter, but I've already add the MAC address into the router.

Model: SL-25111UB4 MERCURY (ETSI) by Senao

> 
mree@mree-desktop:~/Desktop/wlan$ iwconfig wlan0 mode Managed
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not permitted.

mree@mree-desktop:~/Desktop/wlan$ ndiswrapper -l
Installed ndis drivers:
wlannic         driver present, hardware present

mree@mree-desktop:~/Desktop/wlan$ lsusb
Bus 003 Device 006: ID 0930:653d Toshiba Corp.
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 004: ID 09aa:3642 Intersil Corp. Prism 2.x 802.11b Adapter
Bus 002 Device 001: ID 0000:0000

mree@mree-desktop:~/Desktop/wlan$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"xxx@yahoo.com"  Nickname:"xxx@yahoo.com"
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 02:02:00:09:59:05
          Bit Rate:2 Mb/s   Tx-Power:18 dBm
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Link Quality=0/92  Signal level=-100 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Feel free to ask any information, I'll make sure that the question is answered. Thanks in advance.

This is the driver that used with ndiswrapper. I got it using Driver Genius to extract my current driver from my Windows XP. [Click here to download]("http://aurorius.com/files/wlan_driver.zip")

---

### Post by Aurorius on 2006-07-23
Bringing thread to the front

---

### Post by Aurorius on 2006-08-09
Bringing it up again

---

### Post by Aurorius on 2006-08-09
Solution found at [https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb) .. refer to 2.2

**wireless_mode managed**
wireless_enc off

---

