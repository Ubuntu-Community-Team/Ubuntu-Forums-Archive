---
title: "WPC11 Network Problem?"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by thedreaming on 2007-04-23
Both previous versions of ubuntu recognized my WPC11 with no problems and I was surfing the net immediately, but Feisty Fawn doesn't seem to recognize it.  I've located a faq regarding supported wireless cards and I'll be trying out some of the things I've read there to see if I can get it working tonight.  I like ubuntu, but without internet access, it's pretty useless to me.  :confused:

---

### Post by chili555 on 2007-04-23
Linksys made several versions of WPC11, each with different chipsets. Please let us know:```
lspci -v | grep -i Network
sudo lshw -C network
```We can probably sort it out!

---

### Post by kweejibo on 2007-04-23
Please excuse my jumping in, but I have the same problem with a Linksys WPC11 v.4

I tried the latest Realtek drivers with ndiswrapper and this is what I get with the code Chili555 listed:

joshua@ubuntu:~$ lspci -v | grep -i Network
joshua@ubuntu:~$ sudo lshw -C network
  *-generic DISABLED      
       description: IRDA interface
       product: FIR Port Type-DO
       vendor: Toshiba America Info Systems
       physical id: 9
       bus info: pci@00:09.0
       logical name: irda0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list irda logical
       configuration: driver=donauboe latency=64
       resources: ioport:ff60-ff7f irq:11
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@01:00.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=64 mingnt=32
       resources: iomemory:24000000-240001ff irq:11
joshua@ubuntu:~$ 

Thanks,
Josh

---

### Post by kweejibo on 2007-04-23
Hey! Just fixed it! Woo hoo!

Downloaded the Realtek drivers [here]("http://ubuntuforums.org/attachment.php?attachmentid=3976&d=1133292079")
 and extracted them where I'd be able to find them again.
```
sudo ndiswrapper -l 
sudo ndiswrapper -r (result of above)

```

Went to System/Administration/Windows Wireless Drivers (not sure how that got there, but it's at the bottom of the list) Clicked on "Install New Driver" and pointed it to the Realtek .inf driver.

Walla!  Network Manager sprang to life. YMMV?

Josh

---

### Post by Netsui on 2007-04-24
Those drivers worked perfectly for me, kweejibo.

Thanks. This problem was driving me nutz. :)

---

### Post by swordship on 2007-04-26
I grabbed the realtek drivers, but
I can't find where to "Install Wireless Drivers"
under 7.04

????
[email]swordship@gmail.com[/email]

---

### Post by _kjus on 2007-04-27
i got the same problem. I tried to install the driver with ndiswrapper but still the same error.

*-network:1 UNCLAIMED
       description: Ethernet controller
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@00:06.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
       resources: iomemory:d4006000-d40060ff irq:255

 Any Ideas????????

---

### Post by _kjus on 2007-04-27
After ndiswrapper i did a restart. the result:

sudo /etc/init.d/networking restart

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

---

### Post by chili555 on 2007-04-27
_kjus-
Let's retrace our steps. What does *ndiswrapper -l* tell us? Driver and hardware present? If not, please go back to whatever instructions you followed and check your work. If so, then does *iwconfig* show a wireless interface? Post back, we'll get it going.

---

### Post by chili555 on 2007-04-27
swordship-
I have tried to help two different guys compile and install these drivers, I even tried to do so on my own testing laptop. Nothing ever worked. Aside from being an arduous process where there are opportunities for a mistake at every step, at the end, neither of these guys got it to work! 

I suggest taking the proven way first: ndiswrapper. [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) Be sure you get the Feisty packages, not Edgy. Otherwise the process is the same.

---

### Post by swordship on 2007-04-27
Could the problem be that it's not seeing my pcmcia wireless card?

When I do :
tpawlicki@ramblinman:~/realtek$ sudo ndiswrapper -i NET8180.INF 
driver net8180 is already installed



tpawlicki@ramblinman:~/realtek$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
02:00.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
tpawlicki@ramblinman:~/realtek$

---

### Post by chili555 on 2007-04-27
Let's look at:```
ndiswrapper -l
iwconfig
```Thanks.

---

### Post by swordship on 2007-04-27
Any thoughts?


tpawlicki@ramblinman:~$ ndiswrapper -l
net8180 : driver installed
tpawlicki@ramblinman:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

tpawlicki@ramblinman:~$

---

