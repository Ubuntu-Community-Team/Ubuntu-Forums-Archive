---
title: "ralink 5370 not working"
date: 2014-01-09
forum: Networking &amp; Wireless
---

### Post by mithereal on 2014-01-09
i have followed many articles regarding getting this thing to work, it shows listed , scans the wireless networks fine but cannot make it connect whatsoever.
steps ive taken
 the wireless package states the chpset is ralink 5370
lsusb
 Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter

1. download 
[RT8070 /RT3070 /RT3370 / RT3572 /RT5370 /RT5372/ RT5572 USB USB]("http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5032")
[URL="http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5016"]http://www.mediatek.com/_en/07_downl...il.php?sn=5032
[/URL]
2. make && make install
3. iwconfig
ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

5. in network manager device ra0 has a mac address of 00:00:00:00:00:00
6. i can run a iwlist scan and see my network
ra0       Scan completed :
          Cell 01 - Address: 00:12:17:CA:7F:72
                    Protocol:802.11b/g
                    ESSID:"FBI Van #6"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/100  Signal level=-74 dBm  Noise level=-69 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


added to blacklist 
blacklist rt2800usb
blacklist rt2870sta
uname -a 
3.8.0-35-generic #50-Ubuntu SMP Tue Dec 3 01:24:59 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

distro ubuntu 13.04

sudo modprobe rt5572sta
this is the only module that was compiled

x. tried 
echo 'install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "148f 3070" > /sys/bus/usb/drivers/rt2800usb/new_id' | sudo tee /etc/modprobe.d/rt2800usb.conf
sudo modprobe -v rt2800usb

any suggestions??

---

