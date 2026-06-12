---
title: "Wireless and laptop"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by bluzepher on 2008-06-29
Just installed Ubuntu on to my HP Pavilion ZV6000 laptop. Ubunto 8.04  I would like to use the wireless option.  How do I go about this to get it set up ?  How do I find out what com card I have in the laptop?  

Thanks in advance for your help

---

### Post by bluzepher on 2008-06-29
my network card is 

 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company Unknown device 3085
        Flags: bus master, medium devsel, latency 128, IRQ 20
        I/O ports at a000 [size=256]
        Memory at b020a400 (32-bit, non-prefetchable) [size=256]


Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 1355
        Flags: bus master, fast devsel, latency 64, IRQ 21
        Memory at b0204000 (32-bit, non-prefetchable) [size=8K]

Thanks for your Help

---

### Post by Wobblybob on 2008-06-29
Hi,

try [system], [Admin..], [Hardware drivers] to see if you need the restricted drivers enabled, if they are listed and need enabling you will need to connect the laptop via a cable to your internet connection to allow it to download and install them. A reboot will then be required and you should check back in hardware drivers again to make sure they are enabled and in use.

---

### Post by bluzepher on 2008-06-29
it says Broadcom B43 wireless driver in use, but the enabled box is not checked.  when I try to check it I get a message. 
While the driver itself is free software,  it relies on proprietary firmware which cannot be legally shipped with the operating system. Your hardware will not work without the firmware.   
what the heck ?

---

### Post by Wobblybob on 2008-06-29
> **bluzepher said:**
> it says Broadcom B43 wireless driver in use, but the enabled box is not checked.  when I try to check it I get a message. 
While the driver itself is free software,  it relies on proprietary firmware which cannot be legally shipped with the operating system. Your hardware will not work without the firmware.   
what the heck ?

if you want it to work then tick it and allow the system to download and all should be ok after a re boot.

---

### Post by bluzepher on 2008-06-29
I checked the box, it will not stay checked, I get the message, have rebooted and still wireless. 

 I do not have windows on this computer anymore.  Lost it when I did my Ubuntu install.  grrrr

---

### Post by Wobblybob on 2008-06-29
> **bluzepher said:**
> I checked the box, it will not stay checked, I get the message, have rebooted and still wireless. 

 I do not have windows on this computer anymore.  Lost it when I did my Ubuntu install.  grrrr

have you ticked it while connected to the net with a cable? as it sounds like it's not installed.

---

### Post by bluzepher on 2008-06-29
yes it is connected by cable for now.

when I hit the button for wireless it does not turn on.  Not sure what happened there.

It wont let me Tick it. >>

---

### Post by bluzepher on 2008-06-29
bluzepher@bluzepher-laptop:~$ sudo  lshw -C network
[sudo] password for bluzepher: 
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:79:3c:a0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.2 latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:23:13:4b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
bluzepher@bluzepher-laptop:~$




lsmod |grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
b43                   144420  0 
rfkill                  8592  16 rfkill_input,b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
ssb                    34308  1 b43

---

### Post by wabbalee on 2008-06-29
> **bluzepher said:**
> it says Broadcom B43 wireless driver in use, but the enabled box is not checked.  when I try to check it I get a message. 
While the driver itself is free software,  it relies on proprietary firmware which cannot be legally shipped with the operating system. Your hardware will not work without the firmware.   
what the heck ?
please read this post [http://ubuntuforums.org/showthread.php?t=814117](http://ubuntuforums.org/showthread.php?t=814117) #6 and #9. i have had the exact same problem but now it works every time.

---

### Post by bluzepher on 2008-07-02
> **wabbalee said:**
> please read this post [http://ubuntuforums.org/showthread.php?t=814117](http://ubuntuforums.org/showthread.php?t=814117) #6 and #9. i have had the exact same problem but now it works every time.

I did this and it is not working yet.  Not sure what is going on. :confused:  the button to turn on wireless will not come one.  
thanks

---

### Post by bluzepher on 2008-07-02
bluzepher@bluzepher-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

bluzepher@bluzepher-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

bluzepher@bluzepher-laptop:~$ 



stilbluzepher@bluzepher-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

bluzepher@bluzepher-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

bluzepher@bluzepher-laptop:~$ 

Still not working,

---

### Post by bluzepher on 2008-07-02
bluzepher@bluzepher-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 10)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 01)
00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 01)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]
03:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]
03:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
03:04.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
03:04.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
03:04.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
03:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

---

### Post by bluzepher on 2008-07-03
I went back to Ubuntu 7.10 and so far so good.

---

### Post by wabbalee on 2008-07-25
[http://vladgh.com/2008/05/31/dell-wireless-1395-card-and-ubuntu-hardy-heron/](http://vladgh.com/2008/05/31/dell-wireless-1395-card-and-ubuntu-hardy-heron/)

i followed most of these steps and it worked for me

---

