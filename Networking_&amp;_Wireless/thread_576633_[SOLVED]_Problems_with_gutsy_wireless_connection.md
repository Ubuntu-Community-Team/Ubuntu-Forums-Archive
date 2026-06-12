---
title: "[SOLVED] Problems with gutsy wireless connection"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by Jammy4041 on 2007-10-15
**Hello**
I have just started using ubuntu (Gutsy Gibbon) just a few days ago and i dual boot my laptop, with windows XP.
I want my computer to connect to the internet via a local router, wirelessly.
I'm having the wireless problems with ubuntu (7.10), but not with XP. I try to use the Ndiswrapper but I cannot locate the .inf file. ](*,)

Windows locates the file to  


**c:\windows\system32\drivers\psched.sys**


Can anybody help me locate the .inf?


James

---

### Post by Junglizer on 2007-10-15
Please first dump your *lspci* output so we can see what type of card your using, as there may be a better solution then NDIS. Your *iwconfig* output would help also.

---

### Post by Jammy4041 on 2007-10-17
:(

---

### Post by Jammy4041 on 2007-10-17
Hello Junglizer

This is what I get when I type lspci into the terminal program in super user mode:
root@james-laptop:~# lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
 

This is what I get when I type iwconfig into the terminal program in super user mode:

root@james-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"campbell household"  Nickname:"campbell household"
          Mode:Master  Frequency=2.462 GHz  Access Point: 00:14:6C:65:29:64
          RTS thr: off   Fragment thr: off
          Encryption key:CBXX-XXXX-56   Security mode: open
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid: 0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Hope this helps! 
:KS

James

---

### Post by Junglizer on 2007-10-18
Is "campbell household" the network you are trying to connect to? (If not try running ```
iwlist eth1 scan | more
``` to scan for networks the '| more' is just if you have a long list and and 'ctrl+page up/down' in bash actually scrolls, preference really.) Then you'll want to try this:
```
iwconfig eth1 essid "campbell household"
```
```
dhclient eth1
```
I don't know the default dhcp client on Ubuntu, you may have to replace *dhclient* with *dhcpcd* or something to that effect. You can figure it out by typing "dh" and pressing tab twice. It will display a list of all commands that start with "dh." Also, these commands must be run as root.

Give that a shot, and hopefully you can associate and possibly retrive an IP from a network.

---

### Post by Jammy4041 on 2007-10-18
What if I want to connect to  campbell household? What do I do then?

---

### Post by Oraclegol on 2007-10-18
> **Jammy4041 said:**
> What if I want to connect to  campbell household? What do I do then?
you all you should have to do is 
```
dhclient eth1
```
to get an ip addres off that ap since

eth1 IEEE 802.11b/g ESSID:"campbell household" Nickname:"campbell household"
Mode:Master Frequency=2.462 GHz Access Point: 00:14:6C:65:29:64
RTS thr: off Fragment thr: off
Encryption key:CBxx-xxxx-56 Security mode: open
Link Quality=0/100 Signal level=-256 dBm Noise level=-256 dBm
Rx invalid nwid: 0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

tell's us you have a connection to ap (essid)= campbell household and the addres = 00:14:6C:65:29:64
also it tells us you connecting using a wep code of =CBxx-xxxx-56


ps you should never really post your wep code

---

### Post by Jammy4041 on 2007-10-19
Taken  on Board

Thanks for the advice.

James

---

### Post by Thragon on 2007-10-27
Good post. I had the same problem. Sorted now. Thanks.

---

### Post by Jammy4041 on 2007-12-04
This thread is now solved. I managed to do this by clean installing fiesty and using the correct firmware and stuff. Then I upgraded and now I am fine

---

