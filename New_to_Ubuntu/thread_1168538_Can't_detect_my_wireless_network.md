---
title: "Can't detect my wireless network"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by Destructor on 2009-05-24
Okay, so I have just installed Ubuntu on my HP compaq nx9105, dual install with Windows. If I can iron out the bugs in Ubuntu and get it doing what I want, I will switch fulltime to Ubuntu (as I really only want to use this particular machine to browse the web and play videos). 

The first of these bugs is detecting my local wireless network. On Windows this is done automatically. When I select the network icon, Wireless Networks appears greyed out with nothing below it. I tried putting in the wireless network name and password into the detect hidden network option, but it searched and searched and found nothing. 

I did install the 'Broadcom B43 Wireless driver' in the 'System/Administration/Hardware Drivers' menu. 

There is a wireless toggle button on the machine itself- pressing this for some reason in Ubuntu seems to activate/deactive the bluetooth icon in the top right corner. However the indicator for the wireless icon on the machine itself is illuminated, so it seems as though wireless is active- it just isn't receiving any signals from my router (which is in the same room and has other devices connecting to it fine). 

I'm trying to think of more information that may be useful. Any help would be appreciated!

---

### Post by Boondoklife on 2009-05-24
Can you post the output of```
lspci
iwconfig
```

Also what kind of a setup do you have for your wifi, ex. open, hidden SSID, WEP etc.

---

### Post by mak_20789 on 2009-05-24
Hi,
   even i faced the same problem until some time back. Have you tried right-clicking the network manager in the top right-hand corner? That will give you options to connect.
Also read : 

[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

Read the  ubuntupocketguide.

---

### Post by Destructor on 2009-05-24
> **maletek said:**
> Can you post the output of```
lspci
iwconfig
```Also what kind of a setup do you have for your wifi, ex. open, hidden SSID, WEP etc.

lspci:

```
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
```

iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

I used WPA as the security for my wireless, but the network itself seems instantly detectable by my iPhone, my eee pc, and the laptop when it is using Windows. You have to enter a password, but usually detecting the network is not a problem?

I have tried right-clicking the network options icon. Wireless networking IS ticked, but I'm not sure what other options I should explore. Clicking 'edit connections' seems promising, but is a little out of m depth.

I'll check out the guide but for the moment I need problem-specific information.

Thanks.

---

### Post by tom56 on 2009-05-24
This is going to sound stupid, but try moving closer to the router. It could just be you are out of range. So far you have done everything right - it should just be a case of clicking the icon and clicking the name of the network you want to connect to. Edit connections is for changing things AFTER you have connected, so don't worry about that for now.

---

### Post by tom56 on 2009-05-24
> **Destructor said:**
> I did install the 'Broadcom B43 Wireless driver' in the 'System/Administration/Hardware Drivers' menu. 

I have the same card. Connect your laptop to the router with an ethernet cable and install any available updates (System->Administration->Update Manager). Then open up Hardware Drivers, deactivate "Broadcom B43 Wireless Driver" and activate "Broadcom STA Wireless Driver". I find it works much better.

---

### Post by Destructor on 2009-05-25
> **tom56 said:**
> I have the same card. Connect your laptop to the router with an ethernet cable and install any available updates (System->Administration->Update Manager). Then open up Hardware Drivers, deactivate "Broadcom B43 Wireless Driver" and activate "Broadcom STA Wireless Driver". I find it works much better.

I followed these steps but Broadcom STA Wireless Driver does not appear as a selectable option. Is there a way to direct Ubuntu to seek out the driver?

The router is in the same room as the PC, about six feet away, it's hard to imagine moving it closer will help. The XBox on the floor and the PC in a different room both seem to pick it up okay, as does this laptop when it's running Windows.

---

### Post by wizard10000 on 2009-05-25
> **Destructor said:**
> I followed these steps but Broadcom STA Wireless Driver does not appear as a selectable option. Is there a way to direct Ubuntu to seek out the driver?

The router is in the same room as the PC, about six feet away, it's hard to imagine moving it closer will help. The XBox on the floor and the PC in a different room both seem to pick it up okay, as does this laptop when it's running Windows.

One idea that might serve you well is to reduce an issue to its minimum configuration before trying to troubleshoot it  :)

Right now we know that the wireless card is working but that's all we know.  I suggest you temporarily disable security on the access point, get the Linux box to connect and then resolve the security issues.  ifconfig says your wireless card is working - get the thing to connect and *then* work on the security issues.

---

### Post by Destructor on 2009-05-25
> **wizard10000 said:**
> One idea that might serve you well is to reduce an issue to its minimum configuration before trying to troubleshoot it  :)

Right now we know that the wireless card is working but that's all we know.  I suggest you temporarily disable security on the access point, get the Linux box to connect and then resolve the security issues.  ifconfig says your wireless card is working - get the thing to connect and *then* work on the security issues.

I'm in an area where there are multiple wifi signals, some of them insecured. Nothing is displaying. I downloaded the STA driver directly from the Broadcom site but the instructions for installing it were extremely complicated and I got lost about three steps in. Is there a simple way to get this driver activated?

---

### Post by tom56 on 2009-05-25
> **Destructor said:**
> I downloaded the STA driver directly from the Broadcom site but the instructions for installing it were extremely complicated and I got lost about three steps in. Is there a simple way to get this driver activated?

Don't try installing the STA driver. The easiest way is through Hardware Drivers, so if it is not there then you probably don't need it.

Theoretically the B43 one listed there should work fine. I only mentioned the STA one because I get a better range with it but if you are that close to the router then that obviously isn't a problem. I've run out of ideas for now but I'll have a think and get back to you if I come up with anything.

EDIT:

Ok, post the output of each of these commands:
```
sudo lshw -C network
```
```
lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
```

Also try installing wifi-radar, open it from Applications->Internet and see if it can see any networks. If it does it will look like the screenshot.

---

### Post by Destructor on 2009-05-25
> **tom56 said:**
> Ok, post the output of each of these commands:
```
sudo lshw -C network
``````
lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
```Also try installing wifi-radar, open it from Applications->Internet and see if it can see any networks. If it does it will look like the screenshot.

sudo lshw -C network:

```
[sudo] password for daniel: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:6e:a7:f6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.1 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1e:07:2c:39:25:61
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper:

```
ssb                    41220  0 
```

I will try installing wifi radar now. Thank you for this help I do appreciate it.

---

### Post by Destructor on 2009-05-25
Apologies those codes were with the B43 driver deactivated. I have reactivated it, here are the correct codes:

```
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:6e:a7:f6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.1 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1e:07:2c:39:25:61
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:4f:d4:75
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

and

```
ssb                    41220  0 
```

---

### Post by Destructor on 2009-05-25
I installed wifi radar, however when I went to run it I got an error message saying: 'Could not launch wifi radar', followed by: 'Failed to execute child process "su-to-root" (No such file or directory)'. I uninstalled it and reinstalled it in case it was an install error but got the same result after a reinstall.

---

### Post by 3rdalbum on 2009-05-25
> **Destructor said:**
> I installed wifi radar, however when I went to run it I got an error message saying: 'Could not launch wifi radar', followed by: 'Failed to execute child process "su-to-root" (No such file or directory)'. I uninstalled it and reinstalled it in case it was an install error but got the same result after a reinstall.

Uninstalling and reinstalling software does not do anything on Linux.

I haven't used Wifi Radar, but I think people might be getting a little ahead of themselves. It sounds to me like your card isn't working the way it needs to.

First, shut down the computer and start it up again, to make sure that your card is in normal state. Now try this command:

```
iwlist wlan0 scanning
```

(that's a zero, by the way; not a letter O. The zero means "the first device" - don't worry, it's a mathematics thing).

This should list the networks picked up by the device. If no networks are detected here, then I don't believe "Wifi Radar" or "Wicd" or "Network Manager" will work. If no networks can be found, then you've got yourself a driver problem (or potentially a problem with the device).

Try running the command a couple of times - it seems to work very well if you run it a couple of times in quick succession. You can press the Up arrow to get the command back into your terminal and then press Enter to run it again.

---

### Post by tom56 on 2009-05-25
> **Destructor said:**
> sudo lshw -C network:

```
[sudo] password for daniel: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:6e:a7:f6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.1 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1e:07:2c:39:25:61
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper:

```
ssb                    41220  0 
```


I think we've found the problem! For whatever reason, the b43 module/driver (module is linux-speak for driver basically) isn't loading. However, that's the driver we need, as evidenced by this line "configuration: driver=b43-pci-bridge". Try this, it should work. Don't reboot, if you do it will stop working again. We will set it to work after a reboot once we've verified that this is the fix.
```
sudo modprobe b43
```

---

### Post by Tholley on 2009-05-25
This may sound silly, but are you running Firestarter firewall? I know I had a similar problem, and realized the firewall was not letting my wireless connection be detected. Plugged in the ip address and viola...
 
just a thought...

---

### Post by Destructor on 2009-05-26
> **tom56 said:**
> I think we've found the problem! For whatever reason, the b43 module/driver (module is linux-speak for driver basically) isn't loading. However, that's the driver we need, as evidenced by this line "configuration: driver=b43-pci-bridge". Try this, it should work. Don't reboot, if you do it will stop working again. We will set it to work after a reboot once we've verified that this is the fix.
```
sudo modprobe b43
```

Thanks Tom. I opened terminal and input that command, but there was no result. This is a complete C+P of my Terminal window:

```
daniel@daniel-laptop:~$ sudo modprobe b43
daniel@daniel-laptop:~$ 
```

So it didn't give me any feedback, it just went to the next line. Is this what should be happening?

I also searched for wireless networks, as below:

```
daniel@daniel-laptop:~$ iwlist wlan0 scanning
wlan0     No scan results

```

I did this a few times as instructed, no result.

---

### Post by Destructor on 2009-05-26
> **Tholley said:**
> This may sound silly, but are you running Firestarter firewall? I know I had a similar problem, and realized the firewall was not letting my wireless connection be detected. Plugged in the ip address and viola...
 
just a thought...

Is this something that is run on the computer or the router? As far as I am aware I am not running any programs on Ubuntu, it's freshly installed. As for the router, it has a password but every other wireless device in my house, Xbox, iPhone, my desktop PC, my eee PC this laptop when Windows is running, all pick it up and dial into it instantly- it's very confusing as to why Ubunutu won't cooperate.

---

### Post by tom56 on 2009-05-26
> **Destructor said:**
> Thanks Tom. I opened terminal and input that command, but there was no result. This is a complete C+P of my Terminal window:

```
daniel@daniel-laptop:~$ sudo modprobe b43
daniel@daniel-laptop:~$ 
```

So it didn't give me any feedback, it just went to the next line. Is this what should be happening?

Yes, then wait a minute and the networks should show up when you click the icon. My guess is that this won't work though. I think what happened is you either weren't connected to the internet the first time you tried to install the driver or Broadcom's website was down. Either way, Hardware Driver has to fetch some stuff from Broadcom's website because the license prevents re-distribution. Hardware Drivers seems to think it managed to do this but I think it didn't, so we'll do it manually ourselves.

If the above definitely isn't working then try this.
1) Reboot the computer
2) Connect to the internet using an ethernet cable and
sudo apt-get install --reinstall b43-fwcutter
Answer yes to any questions
4) Once it is finished remove the ethernet cable and see if it connects, if not try
sudo modprobe b43

If that works - hooray! Reboot and check if it still works, it should do.

---

### Post by Destructor on 2009-05-27
> **tom56 said:**
> If that works - hooray! Reboot and check if it still works, it should do.

I followed these steps but the problem does not seem to have been resolved. The installation process went forward, I selected yes at the appropriate times, and it seems to have successfully installed, but I still couldn't detect any networks, even after entering the modprobe code.

I did notice that the wireless icon on the front of the machine is not illuminated (this isn't always the case, it's been on in the past after installing the B43 driver). Normally I solve this problem by clicking the wireless button on the exterior of the laptop, but in Ubuntu this only activates/deactivates the bluetooth.

---

### Post by tom56 on 2009-05-27
Damn, I really thought that would work!

What is the output of the following commands? I want to check that the last thing did what it was supposed to.

```
ls -al /lib/firmware/b43
```
```
lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl
```

---

### Post by imattacus on 2009-05-27
I have a broadcom card not the same one but very similar ;) I installed drivers and everything I could do and it just wouldnt work! I plugged myself into the ethernet and I was prompted to update to 9.04 jaunty. I thought to myself what else could go wrong and just did it. Once it installed and rebooted I was litterally automatically on the internet. I dont know how but I'm guessing it  might be something to do with older ubuntus not supporting this wireless card. This worked for me so it might work for you

---

### Post by Tholley on 2009-05-27
Same sort of deal with me, but when I originally installed 9.04, it would not detect my wireless network. I ended up having some other issues where I could not boot into Ubuntu, before I started looking into the network problem. I ended up re-installing 9.04 again on the same partition, (if you need instructions on that, I can help) and then everything worked fine. It automatically saw my network. So maybe as a last resort, you might try to re-install.
 
Then on a side note, I enabled Firestarter to make use of the built in firewall, my network went away again. Realized that the firewall was now blocking it, opened a port with the IP address to my router and was back alive again.
 
Hope this helps...

---

### Post by Destructor on 2009-06-02
> **tom56 said:**
> Damn, I really thought that would work!

What is the output of the following commands? I want to check that the last thing did what it was supposed to.

```
ls -al /lib/firmware/b43
``````
lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl
```

Ladies and gentlemen, we have ignition! I rebooted the PC today (after giving up in frustration for a week) and it... just... worked! Stared up, connected immediately! I think I just needed to reboot for the changes to take effect!

As I write to you, I am sending this through my very own working wireless connection, using Ubuntu!

Tom I want to thank you for your patience and advice, you went well above and beyond and I do appreciate it.

If you feel like heading over to [this thread]("http://ubuntuforums.org/showthread.php?t=1168569") to help me out with my dual-monitor woes, that would be awesome too! Once I have that problem licked I am officially dumping Windows and switching to ubuntu!

Woohoo!

-Dan

---

### Post by Destructor on 2010-07-29
Okay, this isn't thread resurrection, this is the same issue. After updating to the new Linux version (10) I have completely lost my network connectivity.

Here are some of the results I get from various, previously recommend console commands.

lspci:

daniel@daniel-laptop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)


> daniel@daniel-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

> daniel@daniel-laptop:~$ sudo lshw -C network
[sudo] password for daniel: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:6e:a7:f6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.5 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:18 ioport:7000(size=256) memory:e8108800-e81088ff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:e8104000-e8105fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:4f:d4:75
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
daniel@daniel-laptop:~$ 

> daniel@daniel-laptop:~$ lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
b43                   163523  0 
mac80211              205146  1 b43
cfg80211              126517  2 b43,mac80211
led_class               2864  1 b43
ssb                    38671  1 b43
daniel@daniel-laptop:~$ 

> daniel@daniel-laptop:~$ iwlist wlan0 scanning
wlan0     No scan results

I have manually installed the wireless modem, it says it is functioning.

This is very frustrating and I'd appreciate any help or advice.

Thanks!

---

### Post by zagreus360 on 2010-08-02
[FONT=monospace]i'm having exactly the same problem. i looked at a few other websites before i found this thread however after doing so when i right click the icon instead of saying "wired network" and underneath it "wireless network" it only said wired network. After following what tom56 said i ran 
[/FONT]```
sudo modprobe b43
```[FONT=monospace]
in a terminal and it now displays both "wired network" and "wireless network" when right clicking the icon again. however it still doesn't display any of the available wireless networks and it reverts back to only having the "wired network" option after restarting the laptop[/FONT].

does anyone have any ideas on how to fix this?

thanks

---

