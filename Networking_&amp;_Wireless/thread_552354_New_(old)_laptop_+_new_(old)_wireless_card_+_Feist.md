---
title: "New (old) laptop + new (old) wireless card + Feisty = trouble for me"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by JGKC9AYC on 2007-09-16
A friend gave me a non-working laptop for some pc work I did for him.  It's a Compaq Presario 700 series.  I tore it apart & got it working, although I had to install an OS.
Since i'm on a budget, I decided to just get a wireless card off of eBay.  I went to see what wireless cards worked best w/Ubuntu and, of those, which I could afford.
I got a brand new (in box) D-Link DWL-650+ off of eBay since that was one of the ones that allegedly would work.
I stuck the card in, booted up, and nothing.
I went [here]("http://www.damontimm.com/blog/how-to-configure-and-use-d-link-dwl-650-with-ubuntu-feisty-fawn-704/") and followed the instructions to the letter & still nothing.
I tried setting the connection manually (it did recognize that there were 2 wireless routers in the house...one w/a key & one without), but that didn't work either.
I know the card works because i'm dual-booting w/XP & I have no problems there.
Is the link that I posted out-dated?  Is there something i'm missing here or did wrong?
I'd like to be able to have a card that I can use (under Linux) that I won't have to set up each time I go somewhere w/my laptop & wish to use it.  Am I going to be able to do that w/this card?
I'd appreciate any help in this matter

---

### Post by kevdog on 2007-09-16
Can you post 

lshw -C network
lspci -nn

---

### Post by JGKC9AYC on 2007-09-16
> **kevdog said:**
> Can you post 

lshw -C network

  *-network               
       description: Global
       vendor: Wireless Network CardBus PC Card
       physical id: 0
       slot: Socket 0
       resources: irq:11
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@00:0b.0
       logical name: eth0
       version: 10
       serial: 00:08:02:2e:98:c4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.102 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:1400-14ff iomemory:e8010000-e80100ff irq:11
  *-network
       description: Wireless interface
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 1
       bus info: pci@02:00.0
       logical name: wlan0
       version: 00
       serial: 00:80:c8:18:b8:79
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=D-Link,09/08/2003,4.15.5.1 ip=216.240.83.156 latency=64 link=no multicast=yes wireless=IEEE 802.11b
       resources: ioport:1c00-1c1f iomemory:24010000-24010fff iomemory:24000000-2400ffff irq:11

> lspci -nn

00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] [1106:0305] (rev 80)
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP] [1106:8305]
00:07.0 ISA bridge [0601]: VIA Technologies, Inc. VT82C686 [Apollo Super South] [1106:0686] (rev 42)
00:07.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:07.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 1a)
00:07.4 Bridge [0680]: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] [1106:3057] (rev 40)
00:07.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT82C686 AC97 Audio Controller [1106:3058] (rev 50)
00:09.0 Communication controller [0780]: Conexant HSF 56k HSFi Modem [14f1:2f00] (rev 01)
00:0a.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 01)
00:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
01:00.0 VGA compatible controller [0300]: S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK) [5333:8d02] (rev 01)
02:00.0 Network controller [0280]: Texas Instruments ACX 100 22Mbps Wireless Interface [104c:8400]

---

### Post by kevdog on 2007-09-16
ok you are using a really old version of ndiswrapper but it might work.  can you list

ndiswrapper -l
iwlist scan

make sure there is no encryption on the router for now.   what's the nae of your router?

---

### Post by JGKC9AYC on 2007-09-16
> **kevdog said:**
> ok you are using a really old version of ndiswrapper but it might work.  can you list

ndiswrapper -l

airplus : driver installed
        device (104C:8400) present (alternate driver: acx)

> iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:01:38:89:29:1E
                    ESSID:"ShawneeLink-TVIN"
                    Protocol:IEEE 802.11FH
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:100/100  Signal level:89/154  Noise level:160/154
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:11:95:4D:77: D7
                    ESSID:"default"
                    Protocol:IEEE 802.11FH
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:100/100  Signal level:96/154  Noise level:160/154
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


> make sure there is no encryption on the router for now.   what's the nae of your router?

It's a Zoom ADSL X6...a combination DSL modem/wireless router

---

### Post by JGKC9AYC on 2007-09-16
Well, I don't know what happened, but all of a sudden it started working.
I don't know what I did...I didn't reboot or change any settings, but I can connect to either of my internet connections (even though I canceled my cable connection 6 months ago, they haven't disconnected it yet...I guess I should let them know?) and even asked for the WEP key for the one that requires it.
That's aggravating...I wish I knew what I did for future reference.

---

### Post by kevdog on 2007-09-16
OK everything looks ok so far -- barring perhaps the older ndiswrapper version

Ok it said alternate driver was acx

To see if you have the acx driver on your system:
modinfo acx

If something comes up, make sure within the /etc/modprobe.d/blacklist file there is a line that states:

blacklist acx

Ok now try to connect to your unencrypted router --

sudo ifconfig wlan0 down
sudo ifconfig wlan0 0.0.0.0
sudo killall dhclient dhclient3
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "default"
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

---

