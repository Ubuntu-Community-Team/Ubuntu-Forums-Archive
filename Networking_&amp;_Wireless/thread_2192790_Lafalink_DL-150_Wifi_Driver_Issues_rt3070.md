---
title: "Lafalink DL-150 Wifi Driver Issues rt3070"
date: 2013-12-09
forum: Networking &amp; Wireless
---

### Post by uno.mtkunz on 2013-12-09
I bought an Lafalink LF-D10 card from ebay for $5 because it said it had linux support and I can't for the life of me get it to work with ubuntu 12.04 x64.

I downloaded the driver from ralinks website 
[http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5032](http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5032)

I changed the WPA Supplicant lines to yes
Black listed rt2800
[http://www.linuxquestions.org/questions/linux-hardware-18/ralink-rt2870-rt3070-on-slackware-14-0-kernel-3-2-29-is-not-working-correctly-4175431191/](http://www.linuxquestions.org/questions/linux-hardware-18/ralink-rt2870-rt3070-on-slackware-14-0-kernel-3-2-29-is-not-working-correctly-4175431191/)

Did a sudo make && sudo make install and rebooted.

The card loads and can scan for networks, but it only connects if the network is encrypted with WEP or has no security. 

WPA Supplicant fails to connect from terminal with [COLOR=#000000]Association request to the driver failed[/COLOR]

[http://askubuntu.com/questions/386777/lafalink-lf-d10-wlan-driver-install](http://askubuntu.com/questions/386777/lafalink-lf-d10-wlan-driver-install)
Other people seem to have the same issue.

I tried playing with NDISWrapper and couldn't get anywhere. Can you guys help?

---

### Post by chili555 on 2013-12-09
Please run and post:```
lsb_release -d
lsusb
lsmod | grep rt2
```Thanks.

---

### Post by uno.mtkunz on 2013-12-09
I reinstalled my OS to 12.10.

Added this to the start of /etc/modprobe.d/blacklist.conf
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib

Downloaded the drivers from the website
tar xvf DPO_RT5572_LinuxSTA_2.6.1.3_20121022.tar.bz2 DPO_RT5572_LinuxSTA_2.6.1.3_20121022/
Edited the WPA_Supplicant to be Y instead of no
sudo make && sudo make install
and rebooted

Here are the results from those commands.
> taco1@taco1-desktop:~$ lsb_release -d
Description:    Ubuntu 12.10
taco1@taco1-desktop:~$ lsusb
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 004 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 003: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
taco1@taco1-desktop:~$ lsmod | grep rt
rt5572sta             806723  1 
parport_pc             32688  0 
parport                46345  3 parport_pc,ppdev,lp
taco1@taco1-desktop:~$ 



> taco1@taco1-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr bc:5f:f4:e5:b8:f4  
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::be5f:f4ff:fee5:b8f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8455 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8345272 (8.3 MB)  TX bytes:1232455 (1.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:786 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84438 (84.4 KB)  TX bytes:84438 (84.4 KB)

ra0       Link encap:Ethernet  HWaddr 00:25:22:48:fb:ab  
          inet6 addr: fe80::225:22ff:fe48:fbab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5029 errors:0 dropped:0 overruns:0 frame:0
          TX packets:774 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:951756 (951.7 KB)  TX bytes:100758 (100.7 KB)

taco1@taco1-desktop:~$ sudo iwlist ra0 scan
ra0       Scan completed :
          Cell 01 - Address: 94:44:52:93:FD:42
                    Protocol:802.11b/g/n
                    ESSID:"Wireless"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level=-38 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 04:A1:51:1D:8A:3B
                    Protocol:802.11b/g/n
                    ESSID:"NETGEAR41"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/100  Signal level=-68 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD310050F204104A00011010440001021047001088A08A9C2F5CA8013842B75DBFFEFC36103C0001031049000600372A000120

taco1@taco1-desktop:~$ wpa_passphrase Wireless MYPASSWORD > wireless.conf
taco1@taco1-desktop:~$ cat wireless.conf
network={
    ssid="Wireless"
    #psk="MYPASSWORD"
    psk=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
}
taco1@taco1-desktop:~$ sudo wpa_supplicant -B -i ra0 -c wireless.conf
taco1@taco1-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr bc:5f:f4:e5:b8:f4  
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::be5f:f4ff:fee5:b8f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8502 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8348617 (8.3 MB)  TX bytes:1234096 (1.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:786 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84438 (84.4 KB)  TX bytes:84438 (84.4 KB)

ra0       Link encap:Ethernet  HWaddr 00:25:22:48:fb:ab  
          inet6 addr: fe80::225:22ff:fe48:fbab/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5228 errors:0 dropped:1 overruns:0 frame:0
          TX packets:1134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:979440 (979.4 KB)  TX bytes:134418 (134.4 KB)

taco1@taco1-desktop:~$ 



> taco1@taco1-desktop:~$ sudo wpa_supplicant -Dwext -i ra0 -c wireless.conf
ra0: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
ra0: Trying to associate with 94:44:52:93:fd:42 (SSID='Wireless' freq=2437 MHz)
ra0: Association request to the driver failed
ra0: Associated with 94:44:52:93:fd:42
ra0: WPA: Key negotiation completed with 94:44:52:93:fd:42 [PTK=CCMP GTK=CCMP]
ra0: CTRL-EVENT-CONNECTED - Connection to 94:44:52:93:fd:42 completed (auth) [id=0 id_str=]
ra0: CTRL-EVENT-DISCONNECTED bssid=94:44:52:93:fd:42 reason=0
ra0: Trying to associate with 94:44:52:93:fd:42 (SSID='Wireless' freq=2437 MHz)
ra0: Association request to the driver failed
ra0: Associated with 94:44:52:93:fd:42
ra0: CTRL-EVENT-DISCONNECTED bssid=94:44:52:93:fd:42 reason=0
ra0: Trying to associate with 94:44:52:93:fd:42 (SSID='Wireless' freq=2437 MHz)
ra0: Association request to the driver failed
ra0: Associated with 94:44:52:93:fd:42
ra0: CTRL-EVENT-DISCONNECTED bssid=94:44:52:93:fd:42 reason=0
ra0: Trying to associate with 94:44:52:93:fd:42 (SSID='Wireless' freq=2437 MHz)
ra0: Association request to the driver failed
ra0: Associated with 94:44:52:93:fd:42
ra0: CTRL-EVENT-DISCONNECTED bssid=94:44:52:93:fd:42 reason=0
ra0: Trying to associate with 94:44:52:93:fd:42 (SSID='Wireless' freq=2437 MHz)
ra0: Association request to the driver failed
ra0: Associated with 94:44:52:93:fd:42
ra0: CTRL-EVENT-DISCONNECTED bssid=94:44:52:93:fd:42 reason=0
ra0: Trying to associate with 94:44:52:93:fd:42 (SSID='Wireless' freq=2437 MHz)
ra0: Association request to the driver failed
ra0: Associated with 94:44:52:93:fd:42
ra0: WPA: Key negotiation completed with 94:44:52:93:fd:42 [PTK=CCMP GTK=CCMP]
ra0: CTRL-EVENT-CONNECTED - Connection to 94:44:52:93:fd:42 completed (reauth) [id=0 id_str=]
ra0: CTRL-EVENT-DISCONNECTED bssid=94:44:52:93:fd:42 reason=0
ra0: Trying to associate with 94:44:52:93:fd:42 (SSID='Wireless' freq=2437 MHz)
ra0: Association request to the driver failed
ra0: Associated with 94:44:52:93:fd:42
ra0: WPA: Key negotiation completed with 94:44:52:93:fd:42 [PTK=CCMP GTK=CCMP]
ra0: CTRL-EVENT-CONNECTED - Connection to 94:44:52:93:fd:42 completed (reauth) [id=0 id_str=]
ra0: CTRL-EVENT-DISCONNECTED bssid=94:44:52:93:fd:42 reason=0
ra0: Trying to associate with 94:44:52:93:fd:42 (SSID='Wireless' freq=2437 MHz)
ra0: Association request to the driver failed
ra0: Associated with 94:44:52:93:fd:42
ra0: CTRL-EVENT-DISCONNECTED bssid=94:44:52:93:fd:42 reason=0
ra0: Trying to associate with 94:44:52:93:fd:42 (SSID='Wireless' freq=2437 MHz)
ra0: Association request to the driver failed
ra0: Associated with 94:44:52:93:fd:42
ra0: CTRL-EVENT-DISCONNECTED bssid=94:44:52:93:fd:42 reason=0
ra0: Trying to associate with 94:44:52:93:fd:42 (SSID='Wireless' freq=2437 MHz)
ra0: Association request to the driver failed
ra0: Associated with 94:44:52:93:fd:42
ra0: CTRL-EVENT-DISCONNECTED bssid=94:44:52:93:fd:42 reason=0
ra0: Trying to associate with 94:44:52:93:fd:42 (SSID='Wireless' freq=2437 MHz)
ra0: Association request to the driver failed
ra0: Associated with 94:44:52:93:fd:42
ra0: CTRL-EVENT-DISCONNECTED bssid=94:44:52:93:fd:42 reason=0
ra0: Trying to associate with 94:44:52:93:fd:42 (SSID='Wireless' freq=2437 MHz)
ra0: Association request to the driver failed
ra0: Associated with 94:44:52:93:fd:42
ra0: WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
ra0: WPA: Could not verify EAPOL-Key MIC - dropping packet
ra0: Authentication with 94:44:52:93:fd:42 timed out.
ra0: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
ra0: Trying to associate with 94:44:52:93:fd:42 (SSID='Wireless' freq=2437 MHz)
ra0: Association request to the driver failed
ra0: Associated with 94:44:52:93:fd:42
ra0: WPA: Key negotiation completed with 94:44:52:93:fd:42 [PTK=CCMP GTK=CCMP]
ra0: CTRL-EVENT-CONNECTED - Connection to 94:44:52:93:fd:42 completed (reauth) [id=0 id_str=]
^Cra0: CTRL-EVENT-TERMINATING - signal 2 received



---

### Post by chili555 on 2013-12-10
I am surprised that a driver downloaded from Realtek and compiled for 64-bit works at all, frankly. I also think the built-in rt2800usb is supposed to work with this device and I wonder what didn't work as expected. Did you explore all the troubleshooting steps before you downloaded an older (2012) driver? I might have tried several things before I tried rt5572sta.

> taco1@taco1-desktop:~$ sudo wpa_supplicant -Dwext -i ra0 -c wireless.confFinally, Network Manager will probably conflict with manual methods like calling wpa-supplicant from the command line. Is there some reason NM is not in use here?

---

### Post by uno.mtkunz on 2013-12-10
Hmm I appear to have the same problem that this guy fixed, only on gentoo. Any idea where I can find those files?

[http://www.geekamole.com/2013/rt2800usb-fix-for-ralinkmediatek-3070-gentoo-linux/](http://www.geekamole.com/2013/rt2800usb-fix-for-ralinkmediatek-3070-gentoo-linux/)

I may have solved this... I'll be back

---

### Post by uno.mtkunz on 2013-12-10
Alright I've solved it and everything is working now.

Geekamole's kernel patch is in the latest kernel image. I followed the instructions below and updated the kernel. I didn't need to install the driver off mediatek's website.

[http://ubuntuforums.org/showthread.php?t=2185682](http://ubuntuforums.org/showthread.php?t=2185682)

Currently getting 22mbps on a speed test.

Thanks for the help guys

---

### Post by chili555 on 2013-12-11
Glad it's working!

---

### Post by Matt_klimmer on 2014-02-06
I have done all the above steps using 13.10 it sees the adapter but won't connect to WPA network any help?

---

### Post by chili555 on 2014-02-06
> **Matt_klimmer said:**
> I have done all the above steps using 13.10 it sees the adapter but won't connect to WPA network any help?Which steps? Compiled a driver from Realtek? Did it actually *work* in 13.10??

Please show us:```
lsusb
iwconfig
lsmod | grep -e rt5 -e rt2
```

---

