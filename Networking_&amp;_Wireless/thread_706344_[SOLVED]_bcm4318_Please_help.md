---
title: "[SOLVED] bcm4318 Please help"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by Jense on 2008-02-24
Hi everybody,
I have a strange Problem here. I know there are a lot of posts about the bcm43xx, but none worked for me, so here we go again.
After a fresh install of Gutsy everything worked fine, but some update or install along the way screwed up the wireless. Sorry, can't be specific on this because I don't use it every day. So here are the problems.
1.  KNetworkmanager is not showing any wireless networks
2. After boot, I have to manually restart the wired network for it to work (in KNetworkmanager).

Some posts:

jens@jensmobil:~$ dmesg | grep ndiswrapper
[   20.272000] ndiswrapper version 1.45 loaded (smp=yes)
[   20.388000] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
[   20.396000] ndiswrapper: using IRQ 11
[   20.756000] usbcore: registered new interface driver ndiswrapper
[   20.788000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[ 2114.932000] ndiswrapper: device eth1 removed
[ 2114.936000] usbcore: deregistering interface driver ndiswrapper
[ 2125.596000] ndiswrapper version 1.45 loaded (smp=yes)
[ 2125.612000] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
[ 2125.620000] ndiswrapper: using IRQ 11
[ 2125.980000] usbcore: registered new interface driver ndiswrapper
[ 2126.328000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
jens@jensmobil:~$  

And:

jens@jensmobil:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

jens@jensmobil:~$                        


And

jens@jensmobil:~$ sudo iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:11:6B:12:7E:E2
                    ESSID:"WG-Router"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK

jens@jensmobil:~$    


Thx for any help

---

### Post by Jense on 2008-02-25
Does nobody know what this is? I am wondering, because the scan shows networks, but still KNetworkmanager does not detect any. 
Please, this is really anoying.

---

### Post by Ayuthia on 2008-02-25
Have you tried to connect to it manually?  You might try:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
kevdog has a section on how to connect for WPA

Of course, you might want to turn of KNetworkManager first so that it does not interfere with the manual connection.

You could also try to connect manually through KNetworkManager also even though it does not show any networks.

---

### Post by Jense on 2008-02-26
Thanks for your help, I will check this out. however, this is kind of a hassle to do every time you want to connect to a network. Plus I would very much like to know, why my wired network doesn't work after boot. Any  ideas?, anybody?

---

### Post by Jense on 2008-02-26
Thx for the link. It let me to the solution here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Very usefull if anybody else has problems with the bcm43xx.

Great, I am very happy now.

---

