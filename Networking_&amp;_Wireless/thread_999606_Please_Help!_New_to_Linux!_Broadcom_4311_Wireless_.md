---
title: "Please Help! New to Linux! Broadcom 4311 Wireless Adapter driver Issues"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by brettsnowboards on 2008-12-02
I am new to Linux and don't understand much of the lingo yet, but I would really love to get my wireless going in Ubuntu 8.10!  I've tried using all these links from other forums, but nothing is going as smoothly as they say it should.  I'm sure I'll feel stupid once I am taught how it is done.  Please help!

Thank you!

---

### Post by Ayuthia on 2008-12-02
I am not for sure about what you tried so far so I will try to take a guess.  Can you try going to System->Administration->Hardware Drivers and activate the Broadcom STA driver?  Then do the following from the Terminal:```
sudo modprobe -r b43 ssb wl ndiswrapper
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```
If all goes well, it should return wireless sites.  If it does not, please post the results of:
```
lspci -nn
lshw -C network
```Please also let us know if you tried using the b43 driver from Hardware Drivers and if you tried ndiswrapper.

---

### Post by sanjaysahu on 2008-12-11
This worked for me ! I had Broadcom 4311 Wireless Adapter driver and wireless was not working. Thank You Ayuthia

> **Ayuthia said:**
> I am not for sure about what you tried so far so I will try to take a guess.  Can you try going to System->Administration->Hardware Drivers and activate the Broadcom STA driver?  Then do the following from the Terminal:```
sudo modprobe -r b43 ssb wl ndiswrapper
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```
If all goes well, it should return wireless sites.  If it does not, please post the results of:
```
lspci -nn
lshw -C network
```Please also let us know if you tried using the b43 driver from Hardware Drivers and if you tried ndiswrapper.

---

### Post by dannax on 2008-12-13
I figured I would post my questions here in this thread since it's related to the same Wireless adapter than I need help with. I've Google'd everything I can think of. First of all, I'm new to Ubuntu.

When I initially connected wirelessly, I used my WAP passphrase to connect to my router, no problem. After I installed the 162 updates, I needed to restart. After it was all booted back up, it attempted to connect to the same connection as before but this time, the password was a large string of random numbers/letters. I've tried doing everything. I'm deleted the keys, I've typed endless commands in the terminal and so on. I'm currently connected to a neighbour's WEP encrypted router and with no problems whatsoever. I read that there are several issues with WAP and Ubuntu. Can someone just tell me what I need to do. I've given up on the search for the answer. I'd really appreciate it.

---

### Post by Ayuthia on 2008-12-13
> **dannax said:**
> I figured I would post my questions here in this thread since it's related to the same Wireless adapter than I need help with. I've Google'd everything I can think of. First of all, I'm new to Ubuntu.

When I initially connected wirelessly, I used my WAP passphrase to connect to my router, no problem. After I installed the 162 updates, I needed to restart. After it was all booted back up, it attempted to connect to the same connection as before but this time, the password was a large string of random numbers/letters. I've tried doing everything. I'm deleted the keys, I've typed endless commands in the terminal and so on. I'm currently connected to a neighbour's WEP encrypted router and with no problems whatsoever. I read that there are several issues with WAP and Ubuntu. Can someone just tell me what I need to do. I've given up on the search for the answer. I'd really appreciate it.
Please let us know if you are using a 4311 card (or just post lspci -nn) and which driver you are trying to use (b43, wl, ndiswrapper).  If you have a 4311 card, you might be better off using the b43 driver because it seems to work fine with WEP/WPA.

---

### Post by dannax on 2008-12-13
4311 card, with b43 driver. still not able to connect and it's still replacing the passphrase for the WAP with a long string of characters. i've pressed connect with the long string in the box, i've replaced it with the passphrase for the router over and over and it just keeps asking for authorization over and over. i've tried the administrator password. i don't know what else i could possibly do.



> 00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

---

### Post by Ayuthia on 2008-12-13
Let's try using the wl driver then.  Please try the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```
The first two commands should not return anything.  The third should produce an [OK].  The final command should produce a list of wireless sites.  If it does, please see if you can connect.  If it does not connect, please post the results of sudo iwlist scan.

---

### Post by dannax on 2008-12-13
went through the commands, tried to connect back to my router with the passphrase set up for the router and still, it asks for the passphrase over and over. here are the results of the sudo iwlist;

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1E:C7:C6:17:21
                    ESSID:"2WIRE856"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:5/5  Signal level:-51 dBm  Noise level:-92 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:0D:72:4E:36:51
                    ESSID:"2WIRE932"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-70 dBm  Noise level:-92 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
          Cell 03 - Address: 00:1C:DF:14:C4:B0
                    ESSID:"XL33TX"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:4/5  Signal level:-61 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:11:50:D1:1A:62
                    ESSID:"Belkin_Pre_N_D15CC0"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:2/5  Signal level:-71 dBm  Noise level:-92 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s


the particular one i'm trying to connect to is XL33TX... (oh and don't take my use of "leet" serious, it's really a joke... lol) the connection i am able to connec to is the 2WIRE856...

---

### Post by Ayuthia on 2008-12-13
Can you go back to the previous kernel version and see if you can connect?  The kernel update might have caused this problem.

---

### Post by dannax on 2008-12-13
i don't know how? do you mean just reinstall a different version? i've never used other versions of ubuntu before 8.10. will i lose the things i've already transfered to the hard drive when i change the kernel version?

---

### Post by Ayuthia on 2008-12-13
> **dannax said:**
> i don't know how? do you mean just reinstall a different version? i've never used other versions of ubuntu before 8.10. will i lose the things i've already transfered to the hard drive when i change the kernel version?

When you reboot your computer, there is a screen (the GRUB menu) that might appear which will allow you to choose which version you would like to start.  If the screen does not appear, you will need to press escape and it should bring up the options screen.

---

### Post by dannax on 2008-12-13
ok, tried that and it's still not connecting and it's doing the same thing with the passphrase. it would be better if i could just access the router and change it to WEP since that seems to work fine with the other connections. i've tried accessing the router through firefox with the usual router IP address to change the settings and it can't find it. should i try to directly plug my computer into the router and access it directly instead of wireless?

---

### Post by Ayuthia on 2008-12-13
> **dannax said:**
> ok, tried that and it's still not connecting and it's doing the same thing with the passphrase. it would be better if i could just access the router and change it to WEP since that seems to work fine with the other connections. i've tried accessing the router through firefox with the usual router IP address to change the settings and it can't find it. should i try to directly plug my computer into the router and access it directly instead of wireless?

Since you are unable to access it via wireless, the wired connection would be the best choice.

---

### Post by dannax on 2008-12-13
yay, it worked! i was able to directly plug into the router and change it from WPA to WEP. everything's just fine now. thanks for the help!

---

