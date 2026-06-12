---
title: "Atheros AR5005GS Wireless Card Problems"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by J03 on 2006-11-29
Hello, been using Linux for a while now but just decided to install Ubuntu 6.10. But I cannot seem to get my Atheros wireless card to work.. I installed Ubuntu from the iso I downloaded off of Ubuntu.com So I'm not sure if thats the Alternate CD or not.. 
This is on a Toshiba Satellite M40X Laptop (crappy I know but it gets the job done..) 
I'll post the output from the cmd that the person with the Garfield avatar always asks for once I boot back into ubuntu. 

Thanks in advance, JoeM

---

### Post by J03 on 2006-11-29
lspci:
joe@JoeMUbuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Seneca"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Hope this helps :P

---

### Post by FrodoB on 2006-11-30
For starters try this:

1) Have the install CD ready for use.

2) Open a terminal command prompt and type the following:

$ sudo apt-get install linux-restricted-modules-`uname -r`

The system should present a prompt asking you to insert the install CD, put it in the CD driver that you used for installation and then press enter. 

Apt will find the .deb archives and install them for you. A reboot should result in a system that now sees the cards that worked during the install.

---

### Post by J03 on 2006-11-30
joe@JoeMUbuntu:~$ $ sudo apt-get install linux-restricted-modules-`uname -r`
bash: $: command not found
joe@JoeMUbuntu:~$ sudo apt-get install linux-restricted-modules-`uname -r`
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-2.6.17-10-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Didn't do anything.. I did this before and got the same output..

---

### Post by FrodoB on 2006-11-30
Well, your signal level is really bad, are you far from the access point?

What is the output of:

iwlist ath0 scanning

---

### Post by J03 on 2006-11-30
joe@JoeMUbuntu:~$ iwlist ath0 scanning
ath0      Scan completed :
          Cell 01 - Address: 00:0D:28:68:57:54
                    ESSID:""
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/94  Signal level=-63 dBm  Noise level=-95 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101820003a5000027a500004254bc0062436600
          Cell 02 - Address: 00:0D:28:68:57:29
                    ESSID:""
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=7/94  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101820003a5000027a500004254bc0062436600
          Cell 03 - Address: 00:0C:85:14:5C:88
                    ESSID:"SeneNET"
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality=43/94  Signal level=-52 dBm  Noise level=-95 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101820003a5000027a500004254bc0062436600
          Cell 04 - Address: 00:0D:28:88:D0:47
                    ESSID:""
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Quality=8/94  Signal level=-87 dBm  Noise level=-95 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101820003a5000027a500004254bc0062436600
          Cell 05 - Address: 00:0D:28:68:57:33
                    ESSID:""
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Quality=18/94  Signal level=-77 dBm  Noise level=-95 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101820003a5000027a500004254bc0062436600
          Cell 06 - Address: 00:0D:28:68:57:30
                    ESSID:""
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality=6/94  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101820003a5000027a500004254bc0062436600
          Cell 07 - Address: 00:0D:28:68:57:8B
                    ESSID:""
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality=29/94  Signal level=-66 dBm  Noise level=-95 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101820003a5000027a500004254bc0062436600
          Cell 08 - Address: 00:0D:28:68:56:2D
                    ESSID:""
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Quality=15/94  Signal level=-80 dBm  Noise level=-95 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101820003a5000027a500004254bc0062436600
          Cell 09 - Address: 00:0D:28:68:57:8E
                    ESSID:""
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality=1/94  Signal level=-94 dBm  Noise level=-95 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101840003a5000027a500004254bc0062436600
          Cell 10 - Address: 00:0D:28:68:56:0A
                    ESSID:""
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Quality=8/94  Signal level=-87 dBm  Noise level=-95 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101820003a5000027a500004254bc0062436600
          Cell 11 - Address: 00:0D:28:68:56:3A
                    ESSID:""
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=11/94  Signal level=-84 dBm  Noise level=-95 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101820003a5000027a500004254bc0062436600
          Cell 12 - Address: 00:0D:28:68:57:28
                    ESSID:""
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality=13/94  Signal level=-82 dBm  Noise level=-95 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101820003a5000027a500004254bc0062436600
          Cell 13 - Address: 00:0D:28:68:57:68
                    ESSID:""
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=2/94  Signal level=-93 dBm  Noise level=-95 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101820003a5000027a500004254bc0062436600

I can connect fine in windows...

---

### Post by J03 on 2006-11-30
Thanks for your help FrodoB. I had the wrong ssid. lol. I'm writing this in Ubuntu now!

---

### Post by FrodoB on 2006-11-30
Wonderful news. Make good notes on what you did. Like me you will no doubt visit the issue again later.

---

### Post by J03 on 2006-12-03
Got another quick question. The internet works fine at school as its unencrypted (you have to login before you can use it). But at home I have WPA encrypted wireless. I have tried using Plain (ASCII) and HEXIDECIMAL and put in my network password. With no luck at all. Is it possible to get WPA to work in Ubuntu? Is there an addon I have to get? 

Thanks again, JoeM

---

### Post by FrodoB on 2006-12-03
Yes it is quite possible. You should be able to find information on this on the wpasupplicant site:

[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

The person on this forum who really seems to know about WPA  is:

wieman01

I believe. You might send him a private message and verify that I am correct about that. He seems to take his wireless security seriously.

Refer him to this thread if I got my names right and maybe he can get some others and myself on WPA as well.

---

### Post by wieman01 on 2006-12-04
> **J03 said:**
> Got another quick question. The internet works fine at school as its unencrypted (you have to login before you can use it). But at home I have WPA encrypted wireless. I have tried using Plain (ASCII) and HEXIDECIMAL and put in my network password. With no luck at all. Is it possible to get WPA to work in Ubuntu? Is there an addon I have to get? 

Thanks again, JoeM
Hello, 

You can try this guide in the first place: [http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

Please make sure you know what type of WPA you are using: WPA1 (TKIP) or WPA2 (AES). Also pay attention to the generation of the **wpa_passphrase** as indicated in the guide. It's a false friend, you cannot use the hexadecimal key that your router provides. You need to generate it... more in the guide.

Drop us a note if you troubles setting it up. Just post here or on the other thread.

---

