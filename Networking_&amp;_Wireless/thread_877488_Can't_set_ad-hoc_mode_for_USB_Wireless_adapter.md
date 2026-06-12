---
title: "Can't set ad-hoc mode for USB Wireless adapter"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by GlenboLake on 2008-08-01
I've been having trouble switching wlan0 to ad-hoc mode, although I know my wireless adapter works just fine for normal wireless networks.  Changing the channel and essid works just fine too, it's only the mode that gives me grief.  Probably the easiest way to sum up the problem is with the ifconfig/iwconfig outputs I get:
```
# iwconfig wlan0 
wlan0     IEEE 802.11g  ESSID:"mynetwork"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

# iwconfig wlan0 mode ad-hoc 
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.

```

I thought maybe I would try shutting down wlan0 and see if that fixed anything... well, only kind of.  I don't get an error for changing the mode, but I have a new problem now:

```

# ifconfig wlan0 down
# iwconfig wlan0 mode ad-hoc 
# ifconfig wlan0 up
SIOCSIFFLAGS: Operation not supported

```

So it seems like shutting down the interface isn't solving any problems whatsoever for me.  I need to unplug the wireless adapter just to get wlan0 to reappear.  I'm using an [AZiO AWU25 Wireless Adapter]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833340004")

Thanks in advance to anybody who knows what I'm missing here...

---

### Post by pytheas22 on 2008-08-01
Not all wireless drivers support ad-hoc mode, which I think is what's going on here--when it says, "Operation not permitted," I think it's referring to ad-hoc mode.

If we know the chipset that your device is using, however, there may be a way to get it into ad-hoc mode by using a different driver or ndiswrapper.  Please post the output of:
```

lspci
lshw -C Network
```

so that we can try that.

---

### Post by GlenboLake on 2008-08-01
Okay, here is that output:
```
# lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GS] (rev a2)


~# lshw -C Network
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:e0:4d:43:91:fc
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=10.70.13.15 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:0f:bc:92:2e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

Another small update... I found a suggestion in another thread to try "dhclient -r wlan0" which didn't seem to work.  Unfortunately, I didn't record what the output was for this, but I think it included an error.  In any case, when I came back to my computer a few hours later, I found that wlan0 *was* in ad-hoc mode, but my other computer still can't see the network.  I tried to duplicate the original problem (I removed and reattached the hardware) and now I find that "ifconfig wlan0 down" is having no effect.

Thanks for the speedy reply :)

---

### Post by pytheas22 on 2008-08-02
Could you please also post the output of:

```
lsusb
```

I forgot to ask for that before--sorry--but I can't figure out which driver you need based on what you posted above.

dhclient -r just tells the system to forget the IP address that it had assigned to wlan0; I don't think it would affect the ad-hoc stuff in any way.  Also, even if iwconfig says that wlan0 is in ad-hoc mode--as you say it was after you came back to the computer--it's not necessarily true.  I know from experience: I spent a weekend in May trying to figure out why my wireless card wasn't working on my ad-hoc network, even though iwconfig reported it being in ad-hoc mode.  Eventually I did a quick Google search and realized that my driver (bcm43xx) doesn't support ad-hoc, whether iwconfig thinks it should or not.  So don't believe iwconfig until you can actually connect in ad-hoc mode.

By the way, what are you trying to do exactly?  Are you trying to use your Ubuntu machine as the access point for an ad-hoc network?

---

### Post by GlenboLake on 2008-08-02
```
$ lsusb
Bus 005 Device 008: ID 148f:2573 Ralink Technology, Corp. 
Bus 005 Device 004: ID 059b:0274 Iomega Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 413c:2010 Dell Computer Corp. 
Bus 002 Device 002: ID 413c:1003 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:08da Logitech, Inc. QuickCam Messanger
Bus 001 Device 001: ID 0000:0000  

```

Oh right, the end result I'm looking for... I probably should have mentioned that in the first place.  Oops.

When I'm at home, we have a wireless router and no way for me to get an Ethernet cable to my desktop, which is the reason I bought the wireless adapter in the first place.  I'm at a residential job right now though, and I don't have a router here, so I'm trying to create an ad-hoc network to share my desktop's wired connection with my laptop.  It's basically the only means by which I can give my laptop Internet access and still boot into Ubuntu on my desktop.

---

### Post by pytheas22 on 2008-08-02
Alright, you have an Ralink card.  The drivers that ship with Ubuntu for Ralink cards don't support ad-hoc mode (I believe they will eventually--supposedly they'll even support master mode at some point--but they're still being developed).  But there are other ones that you can install.  Follow these steps:

1. install necessary stuff:
```

sudo apt-get install build-essential rutilt
```

2. grab the source code for the driver and compile it:

```
wget http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz
tar -xzvf rt73*
cd rt73*/Module
make
sudo make install
```

3. blacklist the default Ralink drivers so they don't interfere with the one you need to use:
```

sudo -s
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
exit
```

4. now reboot and you should be in better shape.  An important thing to note is that the driver you're installing doesn't work with Network Manager; instead, you have to use Rutilt, which you can find under System>Administration, to connect.  [wicd]("http://wicd.sourceforge.net/") would also work.  Command-line tools like iwconfig will work the same; "iwconfig wlan0 mode ad-hoc" should put the card in ad-hoc mode with no problems.

Also, I've never actually successfully set up and ad-hoc network on Linux (I did try once, at a time when I didn't know so much about Linux), but I think it's more complicated than just putting your wireless card in ad-hoc mode.  I think you need to bridge the ethernet and wireless interfaces and install a dhcp server in order to serve IPs to the other devices on your network.  I know that wicd has an option to create an ad-hoc network that may do all of that stuff for you, but I'm not sure.  Just keep in mind that if it still doesn't work after installing the new driver, you may need to do other things as well.

---

### Post by GlenboLake on 2008-08-02
Thanks, that much worked, although there are still some command line issues:

```
glen@Apollo:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"AdHocApollo"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

glen@Apollo:~$ sudo iwconfig wlan0 mode ad-hoc
[sudo] password for glen: 
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.
glen@Apollo:~$ sudo ifconfig wlan0 down&&sudo iwconfig wlan0 mode ad-hoc 
glen@Apollo:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not supported

```
So I was a little disappointed, but then I went and applied the settings I wanted in RutilT (which gave me an error before I opened terminal).  This apparently did the job
```
glen@Apollo:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"AdHocApollo"  
          Mode:Ad-Hoc  Frequency:2.437 GHz  Cell: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

But you were right, my laptop still can't actually see the network I tried to create.  Do you know how I would go about doing any of the other things you mentioned?  I know that in my XP partition, all I had to do was enable Internet sharing for my Ethernet connection, which Microsoft just implements with a checkbox.

---

### Post by pytheas22 on 2008-08-02
I think that the easiest thing to try first would be to install wicd; as I said, it has an option somewhere to create a new wireless network in ad-hoc mode and I think it might be smart enough to deal with the bridging and dhcp stuff automatically.  Can your laptop at least see your ad-hoc network if you create it using wicd?

If wicd doesn't work, let me know and I'll try to find the guides that I used.  I remember searching for a long time and never finding any straight-forward how-to's explaining how to create an ad-hoc network on Ubuntu (or any kind of Linux), which I think is a glaring problem.  I know that it's really easy to do in Windows, and I think it should be simple in Linux too, if only someone would write up a good guide.  But there is some stuff out there that can be helpful.

You may also want to start a new thread; maybe someone would reply with specific instructions on what you need to do to get an ad-hoc network going, now that you know your driver will support it.

---

### Post by pytheas22 on 2008-08-02
Actually I just came across this [page]("https://help.ubuntu.com/community/Internet/ConnectionSharing#DHCP/DNS%20server") that may be of use to you.  It's not written specifically for creating an ad-hoc network, but it explains everything that you need to do: first configure iptables to forward packets appropriately between your ethernet card (connected to the Internet) and your wireless card; and second, install a dhcp server (which that guide says is "deceptively easy")--you could also use static IPs, but it would be easier to use dhcp.

As long as that guide is up-to-date and accurate, it should be pretty easy to do what you need to do; give it a shot.

---

### Post by GlenboLake on 2008-08-02
wicd did not treat me well.  Somehow, it actually killed my wired connection, and I have no idea why.  I had to download the .deb files for the network manager elsewhere and install it with dpkg.

I like the link you posted, though.  I followed the instructions for setting up a DHCP server; I'll see about trying the rest of the process when I get a chance.  Thanks for looking that up.

---

