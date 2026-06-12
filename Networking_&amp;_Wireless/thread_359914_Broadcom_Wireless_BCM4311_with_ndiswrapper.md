---
title: "Broadcom Wireless BCM4311 with ndiswrapper"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by malpan on 2007-02-12
I have searched the forums and haven't been able to find a thread that helps with this particular problem, many similar, but no cigar, so:

I have edgy running on my Dell Inspiron 6400 (notebook), my wireless card is a Broadcom BCM4311 AirForce™ 54g® 802.11a/b/g PCI Express® Transceiver.
I have attempted to configure ndiswrapper by following [this]("http://www.troubleshooters.com/lpm/200612/200612.htm#_Wireless_on_My_Compaq_Presario_V6133CL") tutorial.
When I tried to
```
bcm43xx-fwcutter -w /lib/firmware bcmwl5.sys
```
i got a message:
```
Extracting firmware from this file is IMPOSSIBLE. (e.g. too old/new)
```
however, undaunted, i went ahead with the rest of the tutorial and got to
```
iwlist wlan0 scanning
```
which worked and listed a number of my campuses networks:
```
wlan0     Scan completed :
          Cell 01 - Address: 00:19:A9:55:B0:81
                    ESSID:"FSU-GUESTS"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-49 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:19:A9:55:B0:80
                    ESSID:"FSU"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-49 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:19:A9:0F:A8:41
                    ESSID:"FSU-GUESTS"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-93 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 02:13:02:00:01:AA
                    ESSID:"WIRELESS"
                    Protocol:IEEE 802.11g
                    Mode:Ad-Hoc
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-74 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:19:A9:55:B1:20
                    ESSID:"FSU"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-77 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 06 - Address: 02:13:02:00:01:A1
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Ad-Hoc
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-67 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 07 - Address: 02:13:02:00:01:AF
                    ESSID:"hpsetup"
                    Protocol:IEEE 802.11g
                    Mode:Ad-Hoc
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-84 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 08 - Address: 00:11:50:54:29:57
                    ESSID:"I <3 Bo0bs"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-85 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  

```
(FSU and FSU-GUESTS are my campus networks, the others I assume are private networks people around me have set up)

The next step, tells me to check my ifcnf-wlan0 file and I don't know where to find it.

Also, I know how to make a bash script, but I don't know what to substitute in for <hex key #> or <essid of your access point>.  I don't know very much about networking, so an explaination of these would be helpful.
(does this mean that the script would be hard-wired to use the same networks all the time, so when I, say, go to a local coffee-shop and access their wireless, I would have to modify my script?)

I have only been using linux for a couple of months, but I'm fairly good with computers and can usually pick up on something once it's been explained to me.

Thanks in advance for your time and help.
        ~jls

---

### Post by malpan on 2007-02-12
Yay!
While playing a game, thinking of something entirely different, it came to me to try changing my network settings under System>Administration>Networking

I filled in FSU-GUESTS as the ESSID and left the password blank. (there is no password for the guest connection, but it is slower than the FSU connection which uses a VPN, another day, another battle)

Lo and Behold, I am sending this with no strings (or CAT cables) attached!

But I would still like to be able to auto-connect to available wireless networks, instead of having to run ```
iwlist wlan0 scanning
``` every time and manually filling in the ESSID.

Any Ideas?

---

### Post by dekalbave on 2007-02-12
You might want to try this tutorial, and use network-manager-gnome:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by malpan on 2007-02-12
ok, since I did get my driver working with ndiswrapper, I only followed the network-manager part.
After I finished, not only could I not auto-detect wireless networks, I lost what ability to connect I did have (eg-manually entering in the ESSID) as a matter of fact, "Wireless" no longer shows up on my network settings window.
I reversed my steps by uninstalling network manager, un-commenting the lines in /etc/network/interfaces file, and rebooted.
No luck.
My wireless is not working at all now, please, any help.  Ive spent all evening getting this to work and now its gone. ](*,)

---

