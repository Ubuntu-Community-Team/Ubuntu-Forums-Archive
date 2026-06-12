---
title: "wmp11v4 Can't get wifi networking going"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by ericwood on 2008-08-04
I am running Ubuntu 8.04 as a dual boot system with Windows XP.  So far I have been unable to get the network going in Ubuntu (I have a Linksys wmp11v4 card and a TrendNet TEW432BRP wireless router).  I have followed the Troubleshooting guide for WiFi systems and ndiswrapper seems to to be fine.  As I get to the end of the guide, I am confused by some information that I got back from some commands I inputted.  Namely, the information is different depending on whether I use ***iwlist*** or ***iwconfig***.  Also, the commands I have used at the end to set things don't work even though according to the man page the syntax is correct.  Is it possible one is the pci card and one is the router?  Also, when I try to connect with the Network option in System/Administration I get an encryption enabled required error message but I can't seem to set the encryption is iwconfig.  Any help would be appreciated. (See below:)


[B]owner@owner-desktop:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:40:F4:DD:89:E2
                    ESSID:"ericwood"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:62/100  Signal level:-56 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

owner@owner-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Ad-Hoc  Frequency:2.422 GHz  Cell: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:17 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

owner@owner-desktop:~$ sudo iwconfig wlan0 key xxxxxxxxx
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.[/B]

---

