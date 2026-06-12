---
title: "Very low Bit Rate on Intel Wireless Dual Band 7265-N"
date: 2017-03-27
forum: Networking &amp; Wireless
---

### Post by cesarsb on 2017-03-27
Hello, I've a laptop with Ubuntu 16.04 whose WiFi card worked just fine on Spain but now when trying to use it on Germany the Internet is very slow when I'm not right next to the router and I've seen that it has a very low Bit Rate (1 Mb actually, back on Spain it used to be over 140 Mb), here are some test outputs:

[URL="https://paste.ubuntu.com/24260227/"]https://paste.ubuntu.com/24260227/
[/URL]
Would appreciate some help as getting far from the router with this bit rate ends up on having quite much no internet at all, and the router here is working correctly as other devices can connect and work with no issues at all.

Regards, César.

---

### Post by chili555 on 2017-03-27
I am troubled by this:> wlp2s0    Scan completed :
          Cell 01 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000015b02f619f
                    Extra: Last beacon: 1224ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSKI know that the wireless script redacts the MAC address, but usually it appears something like this:> Cell 01 - Address: <[COLOR="#FF0000"]MAC 'GBR1' [AC1[/COLOR]]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001245a2e78
                    Extra: Last beacon: 168ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
When you scan, does the MAC address really show up as zeros?```
sudo iwlist scan
```I am also troubled by this:> SSID                  BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
WLAN-756149           <MAC '\00\00\00\00\00\00\00\00\00\00\00' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  80      &#9602;&#9604;&#9606;_  WPA2      yes     * 
WLAN-756149           <MAC 'WLAN-756149' [AN2]>  Infra  100   5500 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2      no        
WLAN-756149           <MAC '\00\00\00\00\00\00\00\00\00\00\00' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  WPA2      yes     * 
FRITZ!Box 6490 Cable  <MAC 'FRITZ!Box 6490 Cable' [AN4]>  Infra  1     2412 MHz  54 Mbit/s  24      &#9602;___  WPA2      no        
There are three access points with the same name; this usually causes dropping as the card attemts to roam from among them. Usually, I'd suggest binding to the preferred access point based on signal strength, but to do so requires the MAC address, which we apparently don't have! Here is an example: [http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

I am most troubled by this:> [/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
[COLOR="#FF0000"]options iwlwifi 11n_disable=8 power_save=0 power_level=5
options iwlwifi bt_coex_active=1[/COLOR]
That suggests that you've thrown every fix you can find at the problem with no success. Let's trim these down a bit, reboot and see if there is improvement:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Change the last two lines from:```
options iwlwifi 11n_disable=8 power_save=0 power_level=5
options iwlwifi bt_coex_active=1

```To:```
options iwlwifi 11n_disable=8 
```Proofread carefully, save and close the text editor. Reboot and let us see a new wireless script result.

---

### Post by cesarsb on 2017-04-03
Hello again, thank you for the reply chili.

I took longer to reply because I don't have the computer anymore, but I've been told that after some Ubuntu updates it started working correctly. Anyways I'll keep in mind to remove the fixes included in the iwlwifi.conf and see how it affects the connection.

Regards.

---

