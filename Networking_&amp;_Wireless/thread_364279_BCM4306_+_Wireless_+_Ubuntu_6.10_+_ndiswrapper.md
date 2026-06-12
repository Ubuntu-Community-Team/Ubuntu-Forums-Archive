---
title: "BCM4306 + Wireless + Ubuntu 6.10 + ndiswrapper"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by king0770 on 2007-02-18
Machine = HP nx9600 (laptop)
OS Ver: Ubuntu 6.10 (Edgy)
Kernel: 2.6.17-11-generic

Hello Ubuntu Guru's!

I have a HP laptop with an onboard NIC, Broadcom 4306. According to the posts I have read, I am not alone with wireless woes. I have followed the documentation using this [page]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#head-1e63934359df5734b0d85f653110de7e4ba224df") 
(very good documentation by the way). 

It appears my wireless is working, when I run the "wifi-radar" tool, it sees my wireless router. I have everything setup according to the documentation, but when I run "sudo dhclient wlan0" I can't connect to the wireless network. 

The following information as follows: 

# lspci | grep -i "Broadcom"
0b:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Converter (rev 03)

#lspci -n | tail -1 
0b:03.0 0280 14e4:4320 (rev 03)

My /etc/network/interfaces file
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid Family
wireless-key xxxxxxxxxxxxxxxx
wirelss-mode managed
auto wlan0 

# sudo iwconfig
wlan0 IEEE 802.11g ESSID:off/any Nicakname:"Family"
Mode-Managed Frequency:2.462 GHz Access Point: Not-Associated
Bit Rate=54Mb/s    Tx-Power:32 dBm
RTS thr=2347 B   Fragment  thr=2346 B
Encryption key:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

# sudo dhclient wlan0
No DHCPOFFERS received. 
No working leases in persistent database - sleeping

Maybe I need to tweak my dhcp settings?

Hopefully I am missing something obvious, if not, hopefully the next version of the Ubuntu OS will be more friendly to wireless cards. 

My best to you all! 

King0770

---

### Post by king0770 on 2007-02-19
Does anyone use a Broadcom wireless card w/ 4306 chipset using Ubuntu? 

Hello...Hello...is this thing on? <taps microphone>

---

### Post by khermans on 2007-03-03
> **king0770 said:**
> Does anyone use a Broadcom wireless card w/ 4306 chipset using Ubuntu? 

Hello...Hello...is this thing on? <taps microphone>

Yeah, but 2.6.17-11 breaks mine too!  2.6.17-10 worked.  Not even compiling ndiswrapper from source helped me!  Something is wrong...no time to check it out now :-(
--
Kristian Hermansen

---

### Post by dabone on 2007-03-03
Hey, you were going thru the same pain as me today.


try what I found.

[http://www.ubuntuforums.org/showthread.php?t=375483](http://www.ubuntuforums.org/showthread.php?t=375483)



Later,
dabone

---

### Post by splttingatms on 2007-03-11
How exactly do you install the firmware? I am brand new to Linux so specific steps would be greatly appreciated.

---

### Post by wtruong on 2007-03-17
Hey I need help with this issue too, someone please help?

---

### Post by Kobalt on 2007-03-17
If that can be of any help, here is another method for an other HP laptop with the same wifi card : 
[http://ubuntuforums.org/showpost.php?p=1189151&postcount=332](http://ubuntuforums.org/showpost.php?p=1189151&postcount=332)

---

### Post by wtruong on 2007-03-19
Nope doesn't work... I'm guessing its the new kernels

---

