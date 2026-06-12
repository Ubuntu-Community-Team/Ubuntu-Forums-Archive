---
title: "wireless is slow and irradic"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by deankovell on 2009-07-05
I can connect sometimes with my built in wireless, but usually it only goes at like 50 or 60 kbs. other times it'll download a file at 953.1 kbs, and then drop to zero for the next five minutes and the jump back up. Most of the time, however I don't get connected at all, or Wicd will say I'm connected, but I can never actually get to a website with Firefox. What I'm trying to do is figure out exactly what my wireless card is and find the xp driver for it, so I can try ndiswrapper with wicd and see if it goes better. I do think I have to wicd b/c that's the only way I've found to do wpa security. Any suggestions to make my connection more reliable will be greatly appreciated. Sorry if my post is rather long, but I noticed that on most of the threads I've read the first reply is one of just a few questions so, I'll try to answer those from the get go. Please be patient, I'm completely new to linux.

Jaunty 64 bit
hp pavillion a6700y 

output of lspci
```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6150SE nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80
```)

output of lsusb
```
Bus 001 Device 004: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 003: ID 15a9:0004  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"attick"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:16:01:84:D4:2F   
          Bit Rate=54 Mb/s   Tx-Power=8 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=65/100  Signal level:-90 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```sudo lshw -C network
```
*-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:5f:69:f0:32
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.11.4 multicast=yes wireless=IEEE 802.11bg
```I don't understand what I'm missing here. When I see other peoples posts of these outputs It'll say somethimg like broadcom or realtek or something, but all I'm seeing here is IEEE 802.11 bg. which if I understand right is just like network guidelines or something. Thank you if you've read all of this. If you can give me suggestion to make  my internet work better I would really appreciate it.

---

### Post by ivanvajar on 2009-07-05
There is nothing wrong with your WiFi. It's probably due to signal or number of computers using router. If your WiFi card works with kernel driver, it's good to keep it as is.

---

### Post by deankovell on 2009-07-05
Thanks for the reply. Your right It's not broken really, but it's not good either. for instance, just now, I had to reboot into vista to be able to check for replies to this thread. Like I said, I'm completely new to Linux, and I don't know if changing the driver is a good thing or not, but I'm getting really frustrated with jaunty the way things are. any other suggestions to make browsing more reliable would be appreciated. Your right also that there are sometimes issues with other computers using the router at the same time, but I don't understand why there is a dramatic performance issue between wifi in jaunty and wifi in vista. Thanks again.

---

### Post by winotree on 2009-07-06
I may be very much *out in left field* with my answer but if you're able to access your router's homepage perhaps changing the channel would help?  I nearly dumped my initial use of Xubuntu because of an unusually slow and erratic wifi -- something I didn't have on the default OS -- and found that moving it one channel up or down made all the difference.

---

### Post by deankovell on 2009-07-07
Thanks for the tip, but my roomate just told me he doesn't really feel like changing anything on his router. I did get things working however. But what I ended up doing was installing a 32 bit version of Hardy as a third OS which has support for this other adapter i have, and everything seems fine. Hardy's cool for now. It'll give me a chance to learn more about ubuntu in general before I try to do too much trouble shooting. I am keeping jaunty 64 installed so I'm still willing to take advice about the wireless issue. If you're reading this looking for help, try this thread
[http://ubuntuforums.org/showthread.php?t=1146367&highlight=wireless+jaunty+upgrade](http://ubuntuforums.org/showthread.php?t=1146367&highlight=wireless+jaunty+upgrade)

---

### Post by superprash2003 on 2009-07-07
take a look at this [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

---

### Post by deankovell on 2009-07-12
please help me sort this out. I think I'm having software conflicts .I've done some changing things around in the last week, I'm using jaunty 32bit and still having wireless problems. I have two wireless adapters. one is a built in with a ralink chipset. I think it's actually a usb dongle hard wired into a usb port and clipped onto the inside of the computer case. iwconfig shows it as wlan0. The other is a netgear wpn111 dongle that shows up as wlan1; for this one I have to use ndiswrapper. I have wicd installed. looking at the wicd screen, I'm not connected to any networks. It's set to show wlan0, and it's showing ap's in my area. I opened a terminal, and iwconfig showed that wlan0 looked normal I think, but it showed that wlan1 was connected to my neighbors unprotected network. I changed wicd to show the wlan1 device and it said that it wasn't connected to anything. I the did "sudo ifconfig wlan1 down"  that might not be exactly what the command was, I had to try several diff. times before I got the command right. iwconfig then showed that wlan1 was shut off, but I could still connect to my router via wicd. however, firefox still wouldn't load any webpages, which is apparently normal on my computer. What else information do I need to find  to figure out what's going on.

---

