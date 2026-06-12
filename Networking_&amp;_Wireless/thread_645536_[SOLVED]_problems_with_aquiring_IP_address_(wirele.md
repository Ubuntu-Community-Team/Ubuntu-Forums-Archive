---
title: "[SOLVED] problems with aquiring IP address (wireless)"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by mmbates on 2007-12-20
G'day,
I seem to be having problem's aquiring an IP address for my wireless cable connection.

I have been going through the Ubuntu help section reasonbly carefully ([https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)), and feel as though I have exhausted it.

The symptoms are:
I have a Netgear WG111v2 USB wireless adapter.  That does not have a native linux driver, but it seems to have installed ok using ndiswrapper.

I do appear to have a router connection, as when I use iwconfig the Access Point is the same as the MAC Address on the gateway (I have confirmed this by checking the gateway's configuration).

When using ifconfig, I do not manage to get an IP address assigned.  I have tried using: sudo dhclient wlan0

which spits out a bunch of stuff, but in the end, tells me there are 'no DHCPOFFERS received'

I have also tried setting a static address.  Doing this, all of the IP addresses spit out when I use the ifconfig wlan0 command, however, if I try to ping the router, or another computer on the network, it all comes back as a blank.

I currently have it set to WEP with a 128-bit hexadecimal key.  I have also (briefly, as I'm a bit worried about security) tried it with an open connection too -- but again to no avail.  I am also 100% sure that I am typing in the WEP key properly.

I have rebooted the computer and the gateway several times after trying new configurations, as well as also trying sudo invoke-rc.d network restart.

I'm pretty sure it is also not the gateway, as I also have an XP laptop connected (and am shamefully, typing this out on said laptop).  

Some other helpful info: the gateway's IP address is 192.168.0.1  I have tried setting the machine's manual IP address to 192.168.0.6, subnet mask 255.255.255.0.

Thanks for any help you might be able to give me.

cheers,
Michael

---

### Post by mmbates on 2007-12-21
Update:  I have tried Gilf's suggestion in the following thread
[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

but also to no avail.  It gets stuck at the same place, no IP address is ever aquired (using DHCP).  I also tried the unsecured network concept again, and still I have never even looked like getting an IP address.  The same symptoms appear, using iwconfig, the essid and access point appear -- however, no IP address is listed in ifconfig, and neither is an IP address aquired using dhclient.  For a little while using the unsecured network (even after a reboot), the network manager kept on asking for a WEP Key.  

I have also tried uninstalling and reinstalling network manager.  No positive results.

I did get the roaming mode working again using Gilf's method (both using the LiveCD and also on the HD version), however, even using the LiveCD an IP address was never aquired -- although, I did get Network Manager to find my network and try to connect to it, but it never aquires an IP address.

I have also tried the same using WiFi Radar....but it too doesn't get an IP address.

I have double checked, and the Gateway is definitely configured for DHCP.

I have spent many, many hours now trying to figure this out...so if anyone has any suggestions, I would be most appreciative of them.

I am half considering a clean install, but can't really think of a good reason why that would work...just clutching at straws now.

Thanks,
Michael

---

### Post by mmbates on 2007-12-22
Further update.  I have done a fresh install of gutsy, with no improvement.  

I have however, now got the computer wired to the gateway modem (and have ditched said XP laptop, for the moment at least).  So the computer has no problems using the gateway when it is wired to it...however, it still (even after the fresh install) does not want to connect wirelessly.

If anyone clever out there is listening, any further suggestions would be most appreciated....

Thanks,
Michael

---

### Post by mmbates on 2007-12-22
One more thing of interest...after the fresh install, I have tried both an unsecured mode as well as 128 bit WEP.  Neither works.  Also, I've tried rebooting the modem and computer again.

cheers,
Michael

---

### Post by kevdog on 2007-12-22
Try connecting from the command line manually as linked to in my signature.

---

### Post by mmbates on 2007-12-23
G'day Kevdog,
Thanks for the advice.  Still no success.  I am now thinking that it possibly has something to do with the driver that I'm using...?  

When using the command lshw -C network I did not get a driver listed.  So I decided to reinstall the driver.

I have a NETGEAR WG111v2 adapter, which does not have a native linux driver, and so I have installed it with wine (to run setup.exe, to get the ini file out) and then ndiswrapper.  Using [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/) it was suggested to use a Win98 driver.

After reinstallation of the drivers, still no success and all the same old story.

Pasted below is some output:
-----------------------------------------------------------------------------------------
michael@bates-ubuntu1:~$ sudo ndiswrapper -l
net111v2 : driver installed
        device (0846:6A00) present (alternate driver: rtl8187)
michael@bates-ubuntu1:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8029(AS)
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: eth0
       version: 00
       serial: 00:10:b5:0c:19:64
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=192.168.0.2 latency=0 module=ne2k_pci multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1b:2f:78:f9:7b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
-----------------------------------------------------------------------------------------
So as you can see, ndiswrapper rekons that there is a driver there and the device present, but seemingly not present in lshw...?

Anyway, proceeding on the assumption that the driver is ok, I thought I would run through your instructions again... pasted below is the output.
-----------------------------------------------------------------------------------------
michael@bates-ubuntu1:~$ sudo ifconfig eth0 down
[sudo] password for michael:
michael@bates-ubuntu1:~$ sudo ifconfig wlan0 down
michael@bates-ubuntu1:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 6489
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1b:2f:78:f9:7b
Sending on   LPF/wlan0/00:1b:2f:78:f9:7b
Sending on   Socket/fallback
michael@bates-ubuntu1:~$ sudo ifconfig wlan0 up
michael@bates-ubuntu1:~$ sudo iwconfig wlan0 essid "wantok"
michael@bates-ubuntu1:~$ sudo iwconfig wlan0 key MY_128HEX_KEY
michael@bates-ubuntu1:~$ sudo iwconfig wlan0 mode Managed
michael@bates-ubuntu1:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1b:2f:78:f9:7b
Sending on   LPF/wlan0/00:1b:2f:78:f9:7b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
-----------------------------------------------------------------------------------------
Is there anything glaringly obvious in all of that that seems wrong?  One thing that I noticed, which I am not sure about is the wmaster0 error...?

I've been reading some other posts and it seems as though some of the other outputs are important, so here is iwlist wlan0 scan, ifconfig and iwconfig outputs:
-----------------------------------------------------------------------------------------
 michael@bates-ubuntu1:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:14:A5:C5:30:F2
                    ESSID:"wantok"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz
                    Quality=57/64  Signal level=43/65  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000147a5d4b23
          Cell 02 - Address: 00:0A:95:F6:FC:BE
                    ESSID:"Evert wireless"
                    Mode:Master
                    Channel:10
                    Frequency:2.457 GHz
                    Quality=49/64  Signal level=26/65  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000156d27ce931

michael@bates-ubuntu1:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"wantok"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:A5:C5:30:F2   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

michael@bates-ubuntu1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:B5:0C:19:64  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::210:b5ff:fe0c:1964/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32278 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:31 txqueuelen:1000 
          RX bytes:46482853 (44.3 MB)  TX bytes:1393065 (1.3 MB)
          Interrupt:11 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3114 (3.0 KB)  TX bytes:3114 (3.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1B:2F:78:F9:7B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0:ava Link encap:Ethernet  HWaddr 00:1B:2F:78:F9:7B  
          inet addr:169.254.8.45  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-2F-78-F9-7B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
-----------------------------------------------------------------------------------------
iwconfig seems to suggest that the wireless device is connected to the router, however, iifconfig does not show any IP address, and dhclient does not connect either.

Please let me know if you have any suggestions...?

Your help is much appreciated.

cheers,
Michael

---

### Post by kevdog on 2007-12-23
Lets start with the driver issue, since this seems to be the problem

Please list (again)
ndiswrapper -l
lsmod | grep ndis
lshw -C network

Also try the following
sudo moprobe -r ndiswrapper
sudo modprobe ndiswrapper
dmesg | tail -n 50

If you could post the results

---

### Post by mmbates on 2007-12-23
G'day again.  Thanks for getting back to me.  

Below is the requested output:
-----------------------------------------------------------------------------------------
michael@bates-ubuntu1:~$ ndiswrapper -l
net111v2 : driver installed
        device (0846:6A00) present (alternate driver: rtl8187)
michael@bates-ubuntu1:~$ lsmod | grep ndis
michael@bates-ubuntu1:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8029(AS)
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: eth0
       version: 00
       serial: 00:10:b5:0c:19:64
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=192.168.0.2 latency=0 module=ne2k_pci multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1b:2f:78:f9:7b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
michael@bates-ubuntu1:~$ sudo moprobe -r ndiswrapper
[sudo] password for michael:
sudo: moprobe: command not found
michael@bates-ubuntu1:~$ sudo modprobe -r ndiswrapper
michael@bates-ubuntu1:~$ sudo modprobe ndiswrapper
michael@bates-ubuntu1:~$ dmesg|tail -n 50
[   18.548000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   18.644000] parport_pc: VIA parallel port: io=0x378, irq=7
[   18.932000] gameport: EMU10K1 is pci0000:00:08.1/gameport0, io 0xdc00, speed 1242kHz
[   20.044000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[   20.168000] input: PC Speaker as /class/input/input3
[   20.476000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   20.676000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[   20.676000] PCI: setting IRQ 5 as level-triggered
[   20.676000] ACPI: PCI Interrupt 0000:00:07.5[C] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[   20.676000] PCI: Setting latency timer of device 0000:00:07.5 to 64
[   22.368000] ieee80211_init: failed to initialize WME (err=-17)
[   22.384000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   22.384000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   22.384000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   22.384000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   22.392000] wmaster0: Selected rate control algorithm 'simple'
[   22.492000] phy0: hwaddr 00:1b:2f:78:f9:7b, rtl8187 V1 + rtl8225z2
[   22.492000] usbcore: registered new interface driver rtl8187
[   23.044000] lp0: using parport0 (interrupt-driven).
[   23.120000] Adding 361420k swap on /dev/hda5.  Priority:-1 extents:1 across:361420k
[   23.416000] EXT3 FS on hda1, internal journal
[   25.456000] input: Power Button (FF) as /class/input/input4
[   25.464000] ACPI: Power Button (FF) [PWRF]
[   25.536000] input: Power Button (CM) as /class/input/input5
[   25.544000] ACPI: Power Button (CM) [PWRB]
[   25.612000] input: Sleep Button (CM) as /class/input/input6
[   25.612000] ACPI: Sleep Button (CM) [SLPB]
[   25.644000] No dock devices found.
[   26.396000] powernow: No powernow capabilities detected
[   28.828000] ppdev: user-space parallel port driver
[   40.764000] audit(1198437896.407:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4609 profile="/usr/sbin/cupsd"
[   40.876000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   40.876000] apm: overridden by ACPI.
[   41.224000] Failure registering capabilities with primary security module.
[   41.536000] Bluetooth: Core ver 2.11
[   41.536000] NET: Registered protocol family 31
[   41.536000] Bluetooth: HCI device and connection manager initialized
[   41.536000] Bluetooth: HCI socket layer initialized
[   41.564000] Bluetooth: L2CAP ver 2.8
[   41.564000] Bluetooth: L2CAP socket layer initialized
[   41.692000] Bluetooth: RFCOMM socket layer initialized
[   41.692000] Bluetooth: RFCOMM TTY layer initialized
[   41.692000] Bluetooth: RFCOMM ver 1.8
[  134.748000] NET: Registered protocol family 17
[  143.556000] NET: Registered protocol family 10
[  143.556000] lo: Disabled Privacy Extensions
[  143.556000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  154.344000] eth0: no IPv6 routers present
[  392.176000] ndiswrapper version 1.45 loaded (smp=yes)
[  393.108000] usbcore: registered new interface driver ndiswrapper
michael@bates-ubuntu1:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8029(AS)
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: eth0
       version: 00
       serial: 00:10:b5:0c:19:64
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=192.168.0.2 latency=0 module=ne2k_pci multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1b:2f:78:f9:7b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
michael@bates-ubuntu1:~$ lsmod|grep ndis
ndiswrapper           185240  0 
usbcore               138632  4 ndiswrapper,rtl8187,uhci_hcd
-----------------------------------------------------------------------------------------
Once again, thanks for your help.

cheers,
Michael

---

### Post by kevdog on 2007-12-23
Can you post the following

lsmod | grep 818

lsmod | grep ndiswrapper

---

### Post by mmbates on 2007-12-23
michael@bates-ubuntu1:~$ lsmod | grep 818
rtl8187                35328  0 
mac80211              171016  2 rc80211_simple,rtl8187
eeprom_93cx6            3200  1 rtl8187
usbcore               138632  4 ndiswrapper,rtl8187,uhci_hcd
michael@bates-ubuntu1:~$ lsmod | grep ndiswrapper
ndiswrapper           185240  0 
usbcore               138632  4 ndiswrapper,rtl8187,uhci_hcd

---

### Post by kevdog on 2007-12-23
Not sure if you see the problem, however it looks like you are trying to load the rtl8187 module and ndiswrapper(with the rtl817 driver inside).  You can only use one or the other.

Can you post your /etc/modprobe.d/blacklist file??

Also if you do a lshw -C network statement -- find the wireless device section (you have a wired and wireless) and you do not see a driver= statement, then stop.  You are having a problem with the driver being loaded.

---

### Post by mmbates on 2007-12-23
contents of /etc/modprobe.d/blacklist
---------------------------------------------------------------------------------
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
---------------------------------------------------------------------------------
I had seen in lshw that the driver is not listed...most other help pages that I've follows and threads that I've seen have said that if you are getting the mac address and the essid listed in iwconfig then your drivers are working properly, however, seemingly this is not the case all the time.

So does that mean that I should blacklist the rtl817 driver...?  Then it will only load one driver and there wont be a conflict and it should work...?

I have to head out now, but I'll be back on again tonight (my time) and will have a closer look at it all.

cheers,
Michael

---

### Post by kevdog on 2007-12-23
try blaclisting the rtl8187 driver and see what happens

---

### Post by kevdog on 2007-12-23
Im guessing that somehow the old rtl driver is being used.

---

### Post by mmbates on 2007-12-24
holy dooly...you wont believe it but it works.  Blacklisting the other driver worked!  Thanks for all the advice.

I'll go away now and sort out how to get everything to load automatically at startup now, as now, I have to go through the full enchilada of commands to connect to the network :)

Again, thanks for the advice, that worked beautifully!

All the best,

MIchael

---

### Post by kalenetus on 2008-01-14
i was reading this with interest because my xubuntu (gutsy) seemed to have exactly the same:
no dhcpoffer received.

i have an utp running straight through my room, the wired connection works

when i look in the router with another machine, i see the attempt but no association/ip adress!

i use a site wl-168 wifi usb stick (actually oem version off the realtek rtl8187).

i installed ndiswrapper (1.45) with the wl168 xp driver (netrtuw), it partly works because in networkmanager it sees essid's however only those on channel 1 (???) and some indication of signal strength.


some of the above commands:

thuis@thuis-desktop:/etc/ndiswrapper/netrtuw$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8029(AS)
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: eth0
       version: 00
       serial: 00:20:18:2e:a2:a7
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=192.168.1.8 latency=0 module=ne2k_pci multicast=yes
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0c:f6:3a:31:78
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netrtuw driverversion=1.45+Realtek Semiconductor Corp. multicast=yes wireless=IEEE 802.11g
thuis@thuis-desktop:/etc/ndiswrapper/netrtuw$ 

thuis@thuis-desktop:/etc/ndiswrapper/netrtuw$ dmesg | tail -n 50
[   26.788000] input: PS/2 Logitech TrackMan as /class/input/input4
[   26.984000] usbcore: registered new interface driver xpad
[   26.984000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   27.580000] Linux video capture interface: v2.00
[   27.712000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 
[   28.092000] sd 0:0:0:0: [sda] Attached SCSI removable disk
[   28.100000] sd 0:0:0:1: [sdb] Attached SCSI removable disk
[   28.120000] sd 0:0:0:2: [sdc] Attached SCSI removable disk
[   28.128000] sd 0:0:0:3: [sdd] Attached SCSI removable disk
[   28.368000] usbcore: registered new interface driver gspca
[   28.368000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   28.392000] usbcore: registered new interface driver snd-usb-audio
[   28.432000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   28.432000] sd 0:0:0:1: Attached scsi generic sg1 type 0
[   28.432000] sd 0:0:0:2: Attached scsi generic sg2 type 0
[   28.432000] sd 0:0:0:3: Attached scsi generic sg3 type 0
[   28.708000] ACPI: PCI Interrupt 0000:00:07.5[C] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   28.708000] PCI: Setting latency timer of device 0000:00:07.5 to 64
[   30.560000] lp0: using parport0 (interrupt-driven).
[   30.680000] ndiswrapper version 1.45 loaded (smp=yes)
[   30.876000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[   31.060000] ndiswrapper: driver netrtuw (Realtek Semiconductor Corp.,01/11/2007,5.1273.0111.2007) loaded
[   36.044000] wlan0: ethernet device 00:0c:f6:3a:31:78 using NDIS driver: netrtuw, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0DF6:000D.F.conf
[   36.044000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   36.044000] usbcore: registered new interface driver ndiswrapper
[   36.168000] Adding 401552k swap on /dev/hda6.  Priority:-1 extents:1 across:401552k
[   36.644000] EXT3 FS on hda4, internal journal
[   39.000000] input: Power Button (FF) as /class/input/input5
[   39.000000] ACPI: Power Button (FF) [PWRF]
[   39.024000] input: Power Button (CM) as /class/input/input6
[   39.024000] ACPI: Power Button (CM) [PWRB]
[   39.036000] input: Sleep Button (CM) as /class/input/input7
[   39.036000] ACPI: Sleep Button (CM) [SLPB]
[   39.308000] No dock devices found.
[   40.076000] powernow: No powernow capabilities detected
[   42.560000] ppdev: user-space parallel port driver
[   43.448000] audit(1200341187.660:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4849 profile="/usr/sbin/cupsd"
[   43.604000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   43.604000] apm: overridden by ACPI.
[   43.972000] Failure registering capabilities with primary security module.
[  414.316000] NET: Registered protocol family 17
[  416.016000] NET: Registered protocol family 10
[  416.020000] lo: Disabled Privacy Extensions
[  416.020000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  426.564000] eth0: no IPv6 routers present
[  508.080000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  628.096000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  818.112000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  978.128000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1415.552000] eth0: no IPv6 routers present

thuis@thuis-desktop:/etc/ndiswrapper/netrtuw$ lsmod | grep 818

thuis@thuis-desktop:/etc/ndiswrapper/netrtuw$ lsmod | grep ndiswrapper
ndiswrapper           185240  0 
usbcore               138632  10 ndiswrapper,snd_usb_audio,snd_usb_lib,gspca,xpad,usb_storage,libusual,usbhid,uhci_hcd


anyone? plz?!

kalenetus

---

### Post by mmbates on 2008-01-15
G'day,
not sure.  It seems as though the problem that I was having is the same one as you, as your driver seems to be listed in lshw -- i.e. you do not seem to have conflicting drivers, which is the problem that I was having.

I was getting a problem more recently with channels, where my wireless router would drop -- but it was a conflicting problem with the chordless phone, which was fixed by changing to a different channel.

Sorry I can't help further.  Kevdog seems to be the guru.

---

### Post by kevdog on 2008-01-15
Ok, if you can see the networks

iwlist scan

Then try connecting from the command line to complete the connection (just for now!).  See the instructions in my signature about how to use the command line.

---

### Post by kalenetus on 2008-01-31
did the manual thing, got to this stage

thuis@thuis-desktop:/etc$ sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
Trying to associate with 00:13:d4:6e:ec:d7 (SSID='Zwart' freq=2412 MHz)
Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with 00:13:d4:6e:ec:d7 (SSID='Zwart' freq=2412 MHz)
Authentication with 00:00:00:00:00:00 timed out.
.
.
.
and so on


will try with security off, reconfigure my modem, results tonight


grtz kalenetus

---

### Post by Pulka on 2008-01-31
Hi!

I´ve been having a similar problem, but the diference is that after a few minutes, i get an ip and can connect to the internet. After a while, the connection goes down again.
Here are the results of the commands:


 **ndiswrapper -l**
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found


 **lshw -C network**
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: a0
       serial: 00:1d:60:29:b6:38
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ATL2 driverversion=1.0.40.2 firmware=L2 latency=0 module=atl2 multicast=yes
  *-network
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 00
       serial: 00:1b:11:bf:63:e1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g



**lsmod**
Module                  Size  Used by
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
i915                   25856  2 
drm                    83348  3 i915
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
ac                      6148  0 
container               5504  0 
video                  18060  0 
sbs                    19592  0 
button                  8976  0 
dock                   10656  0 
battery                11012  0 
af_packet              24840  4 
sbp2                   24072  0 
lp                     12580  0 
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         8064  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_hda_intel         263712  0 
snd_emu10k1           137248  1 snd_emu10k1_synth
snd_ac97_codec        100644  1 snd_emu10k1
snd_seq_dummy           4740  0 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
arc4                    2944  2 
snd_mixer_oss          17664  1 snd_pcm_oss
ecb                     4608  2 
blkcipher               7556  1 ecb
snd_seq_oss            33152  0 
rc80211_simple          6912  1 
snd_seq_midi            9600  0 
snd_pcm                80388  4 snd_hda_intel,snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
usblp                  15104  0 
atl2                   33304  0 
snd_rawmidi            25728  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_hwdep              10244  2 snd_emux_synth,snd_emu10k1
rt61pci                24576  0 
rt2x00pci              11520  1 rt61pci
rt2x00lib              19584  2 rt61pci,rt2x00pci
rfkill                  8208  1 rt2x00lib
mac80211              171016  4 rc80211_simple,rt61pci,rt2x00pci,rt2x00lib
cfg80211                7304  1 mac80211
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
eeprom_93cx6            3200  1 rt61pci
xpad                    9988  0 
snd_seq                53232  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9228  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                39952  0 
parport_pc             37412  1 
emu10k1_gp              4736  0 
gameport               16776  2 emu10k1_gp
iTCO_wdt               11940  0 
snd                    54660  14 snd_emux_synth,snd_seq_virmidi,snd_hda_intel,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
serio_raw               8068  0 
parport                37448  3 ppdev,lp,parport_pc
intel_agp              25620  1 
iTCO_vendor_support     4868  1 iTCO_wdt
pcspkr                  4224  0 
soundcore               8800  1 snd
snd_page_alloc         11400  3 snd_hda_intel,snd_emu10k1,snd_pcm
agpgart                35016  3 drm,intel_agp
evdev                  11136  4 
ext3                  133896  4 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  9 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
usb_storage            73024  1 
ide_core              116804  1 usb_storage
ata_piix               17540  5 
usbhid                 29536  0 
hid                    28928  1 usbhid
libusual               18448  1 usb_storage
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  6 sbp2,sg,sd_mod,sr_mod,usb_storage,libata
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
floppy                 60004  0 
uhci_hcd               26640  0 
ehci_hcd               36492  0 
usbcore               138632  8 usblp,xpad,usb_storage,usbhid,libusual,uhci_hcd,ehci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor



Can anyone find what is the problem?

---

### Post by kalenetus on 2008-02-02
same thing with security off (unencrypted etc).

so the sum up
i see the network (but only on channel 1)
get no dhcpoffer (nor automated, nor through the manual commands of kevdog)

hope kevdog has some idea?

gr kalenetus

---

