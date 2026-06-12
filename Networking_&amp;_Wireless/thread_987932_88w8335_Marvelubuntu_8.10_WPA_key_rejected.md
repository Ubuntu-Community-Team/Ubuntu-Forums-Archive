---
title: "88w8335 Marvel/ubuntu 8.10 WPA key rejected"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by bunkenburg on 2008-11-20
Hello ubuntu friends!

I'm having trouble with my wireless connection. It worked fine until a couple of days after the 8.10 update, but now ubuntu keeps asking me for the WPA password and cannot connect.

My access point is Apple Extreme Base Station, with WPA/WPA2 Personal security. A MacBook, some Apple Express, and an EEE PC with Xandros can connect fine, with WPA password, so I assume the problem is in the ubuntu machine.

The ubuntu machine lists my ESSID "inspiracio" in the list of available networks. I choose it, and ubuntu tries to connect. After a while, it brings up the dialogue "Authentication required" and I type in the correct WPA passphrase. Ubuntu troes to connect again for a while, and then again brings up the dialogue, with my passphrase translated into hex, correctly. But it cannot connect!

I am using a wireless card "Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)" with ndiswrapper.

As a workaround, I have switched off security (no WPA, no WEP), and it works fine. So the problem is in the WPA security.

Any idea what is wrong?

Thanks for you help.
Alex

Here some diagnostic output:

alex@alex-linux:~$ lspci
...
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:09.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

While it is trying to connect:
alex@alex-linux:~$ iwconfig
...
wlan0     IEEE 802.11g  ESSID:"inspiracio"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:19:E3:33:70:B9   
          Bit Rate=1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Then the dialog comes up: "Authentication required by wireless network", and the output of iwconfig changes:
alex@alex-linux:~$ iwconfig
...
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

alex@alex-linux:~$ lsmod | grep ndiswrapper
ndiswrapper           196380  0 
usbcore               148848  5 ndiswrapper,usbhid,ehci_hcd,ohci_hcd

alex@alex-linux:~$ dmesg | grep ndiswrapper
[   19.337363] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   19.390620] ndiswrapper: driver mrv8335x (3Com,05/19/2005,3.1.1.10) loaded
[   19.391025] ndiswrapper 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.392721] ndiswrapper: using IRQ 17
[   19.656548] usbcore: registered new interface driver ndiswrapper

alex@alex-linux:~$ lshw
...
        *-network:1
             description: Wireless interface
             product: 88w8335 [Libertas] 802.11b/g Wireless
             vendor: Marvell Technology Group Ltd.
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: wlan0
             version: 03
             serial: 00:14:6c:2c:52:f8
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ndiswrapper+mrv8335x driverversion=1.53+3Com,05/19/2005,3.1.1.10 latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

alex@alex-linux:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:01:38:CD:3A:F6
                    ESSID:"WLAN_66"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:20/100  Signal level:-83 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:01:38:71:D6:1F
                    ESSID:"WLAN_2A"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:6/100  Signal level:-92 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:01:38:D4:C2:E7
                    ESSID:"WLAN_7F"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:19:E3:33:70:B9
                    ESSID:"inspiracio"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:28/100  Signal level:-78 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

alex@alex-linux:~$ lsb_release -d
Description:	Ubuntu 8.10

alex@alex-linux:~$ uname -r
2.6.27-7-generic

root@alex-linux:~# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                               [ OK ]

---

### Post by linuxishard on 2008-11-24
hi all... just though id say, im having this same issue using a netgear wg111v3 usb adapter with ndiswrapper, on ubuntu 8.10

i can only connect to unsecure networks.

i havent tried wep, but wpa just keeps asking for the network password.

any help would abe greatly usefull, all my work and home networks are wpa2 

thanx

---

### Post by ToOnMaN on 2008-12-03
I used WICD instead of network manager because of the same problem with the Marvell Topdog EC85 N PCIE card. It still reports the encryption is WEP but it connects to my network with a WP2 key. Hope this helps.

Ubuntu install directions:

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

G/l, these Marvell cards are a real pain...

---

### Post by stooshbunutu on 2008-12-09
> **linuxishard said:**
> hi all... just though id say, im having this same issue using a netgear wg111v3 usb adapter with ndiswrapper, on ubuntu 8.10

i can only connect to unsecure networks.

i havent tried wep, but wpa just keeps asking for the network password.

any help would abe greatly usefull, all my work and home networks are wpa2 

thanx

I've got a hidden and encrypted connection via WG111v3 on 8.10

see my tutorial to see how:
[On My Website]("http://helpbuntu.mstrutt.co.uk/wireless.html")
[On Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=732827&highlight=wg111v3")

Hope it helps you

---

