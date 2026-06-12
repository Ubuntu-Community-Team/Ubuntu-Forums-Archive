---
title: "Wireless device &quot;disabled&quot;"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by blackholeinacan on 2007-06-10
I am a fairly new user to Ubuntu, and I have been trying for the past few weeks to get my wireless to work using the guides and forums. Unfortunately, I only have internet access through wireless, so I have to come back to Windows every time I need more information, and then restart to Ubuntu to try it out again.

I have a Compaq Presario R4000 with a Broadcom wireless card. I believe that I have set up the driver correctly using ndiswrapper so my card shows up. However, when I run "lshw", the card appears to be "disabled." Here is what I get with lshw:

*-network:0 DISABLED
                description: Wireless interface
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@03:02.0
                logical name: eth1
                version: 03
                serial: 00:90:4b:ec:b0:0e
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
                resources: iomemory:b0204000-b0205fff 

I can't figure out how to enable it. If it helps, when I run "iwconfig", I get the following:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I hope that if I can enable the card, I will be able to connect. Can anyone help me out?

Thanks in advance,
Andy

---

### Post by scrooge_74 on 2007-06-10
Was this[ thread]("http://www.ubuntuforums.org/showthread.php?t=185174") of any use for you?

Those broadcom are tricky devils

---

### Post by blackholeinacan on 2007-06-11
The problem with the Broadcom thread is that it's designed to work with computers that have internet, which I don't. Nonetheless, I did try it out. I downloaded the files for bcm43xx-fwcutter, rebooted to Ubuntu, and tried to install it. The README file says that the command "make installfw" should work when I'm in the directory, but I get the error:

if ! [ -d /lib/firmware ]; then mkdir -p /lib/firmware; fi
install -o 0 -g 0 -m 600 bcm43xx_*.fw /lib/firmware
install: cannot stat `bcm43xx_*.fw': No such file or directory
make: [installfw] Error 1 (ignored)

I don't know how the "make" or "install" command really work, or what "cannot stat" means. There isn't a file in the .tar that is bcm43xx*.fw, but there is a bcm43xx-fwcutter.l file. 

Can I install fwcutter another way, like by somehow reassigning the location in Synaptic Package Manager from the http address to my own? I'm just tossing out ideas here.

Thanks again!

---

### Post by kevdog on 2007-06-11
Please post output of:

lspci
lspci -n

I just want to make sure the bcm43xx cutter drivers will work with your card.  If not Ill walk you through how to install ndiswrapper (another way of installing wireless drivers).  Both are fairly easy.

---

### Post by blackholeinacan on 2007-06-11
With "lspci", I get:

andy@dhcp-10-86-1-143:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 10)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
03:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
03:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
03:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
03:04.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


The 03:02.0 address is my wireless card.
With "lspci -n", I get:

00:00.0 0600: 1002:5950
00:01.0 0604: 1002:5a3f
00:04.0 0604: 1002:5a36
00:13.0 0c03: 1002:4374
00:13.1 0c03: 1002:4375
00:13.2 0c03: 1002:4373
00:14.0 0c05: 1002:4372 (rev 10)
00:14.1 0101: 1002:4376
00:14.3 0601: 1002:4377
00:14.4 0604: 1002:4371
00:14.5 0401: 1002:4370 (rev 01)
00:14.6 0703: 1002:4378 (rev 01)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:05.0 0300: 1002:5955
03:00.0 0c00: 104c:8023
03:02.0 0280: 14e4:4320 (rev 03)
03:04.0 0607: 104c:8031
03:04.3 0180: 104c:8033
03:04.4 0805: 104c:8034
03:06.0 0200: 10ec:8139 (rev 10)

---

### Post by kevdog on 2007-06-11
The thread that was listed below was the exact same thread that I used to get my bcm43 drivers up and running.  I dont remember having to compile anything like you suggested.

See if by chance you already have the bcm tools installed (I doubt it by here goes):
bcm43xx-fwcutter -v

If you get an error -- you dont.

Ok next if you strike out, lets get a precompiled package for ubuntu to avoid you having to compile yourself.  You can find one here at:

[http://archive.ubuntu.com/ubuntu/pool/universe/b/bcm43xx-fwcutter/](http://archive.ubuntu.com/ubuntu/pool/universe/b/bcm43xx-fwcutter/)

You didnt tell me anything about your computer -- but if you dont have an amd64 bit processor you will probably need:
bcm43xx-fwcutter_006-1_i386.deb

Again Im guessing on this one)

Anyway once you download this on a different computer, and transfer it to the ubuntu via USB stick (or another way), you are going to need to install it.  Changing to the appropriate directory where you copied the .deb file:
sudo dpkg -i bcm43xx-xxxxx.deb
(Again type appropriate name of deb file)

See what happens with this one.  To see if it was successfully installed try:
bcm43xx-fwcutter -v

Hopefully it will give you a version number.  If this works I would proceed through the link that scrooge_74 suggested.

---

