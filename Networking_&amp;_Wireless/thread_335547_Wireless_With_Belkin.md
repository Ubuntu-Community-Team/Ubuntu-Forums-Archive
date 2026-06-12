---
title: "Wireless With Belkin"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by JamieC on 2007-01-10
Hey there, I am trying to set up a _Belkin 'G' USB Wireless Adapter (F5D7050)_ on Ubuntu 6.10. I used *ndiswrapper* to install the driver, below are some commands I ran from the terminal. Does anybody have any ideas why I cannot access the internet, or more to the point, why I fail to receive a reply from the DHCP server? I've read several different methods  which detail of how to get wireless up and running but none seem to work. Any ideas would be greatly appreciated.

jamie@Ubuntu:~$ *ndiswrapper -l*
> 
Installed ndis drivers:
**rt73    driver present, hardware present** 


jamie@Ubuntu:~$ *lsusb*:
> 
**Bus 003 Device 005: ID 050d:705a Belkin Components**
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0ea0:6803 Ours Technology, Inc. OTI-6803 Flash Disk
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 005: ID 05fe:1010 Chic Technology Corp. 
Bus 001 Device 003: ID 058f:9360 Alcor Micro Corp. 
Bus 001 Device 001: ID 0000:0000
 

jamie@Ubuntu:~$ *iwconfig*:
> 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"000D0B2B0926"  
          Mode:Managed  Frequency:2.412 GHz  **Access Point: Not-Associated**   
          RTS thr:off   Fragment thr=2346 B   
          
sit0      no wireless extensions.


jamie@Ubuntu:~$ *ifconfig*:
> 
eth0      Link encap:Ethernet  HWaddr 00:16:E6:1C:CC:83  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10740 (10.4 KiB)  TX bytes:10740 (10.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:C1:BD:17  
          inet6 addr: fe80::211:50ff:fec1:bd17/64 Scope:Link
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:9864 (9.6 KiB)
          Base address:0xd000 

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-C1-BD-17-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xd000


jamie@Ubuntu:~$ *sudo iwlist wlan0 scan*:
> 
wlan0     Scan completed :
          Cell 01 - Address: 00:0D:0B:2B:09:27
                    ESSID:"000D0B2B0926"
                    Mode:Master
                    Frequency:2.462 GHz
                    Encryption key:off
                    Extra:tsf=000001a9ba0c8c3c


jamie@Ubuntu:~$ *sudo dhclient wlan0*:
> 
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:50:c1:bd:17
Sending on   LPF/wlan0/00:11:50:c1:bd:17
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
**No DHCPOFFERS received.**
No working leases in persistent database - sleeping.


jamie@Ubuntu:~$ *sudo vim /etc/network/interfaces*:
> 
[...]
# Wireless adapter
auto wlan0
iface wlan0 inet dhcp
wireless_essid 000D0B2B0926


Thanks in advance, Jamie.

---

### Post by flossgeek on 2007-01-10
[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

In all honestly I doubt your going to have much luck with the USB device I'm afraid. Try and do your homework before you purchase these things, could you take it back?

---

### Post by JamieC on 2007-01-10
> **flossgeek said:**
> [http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

Hm, nothing there really helps to resolve my DHCP issues. Thanks, though.

---

### Post by flossgeek on 2007-01-10
Sorry that was a bad post, I thought it might give you some idea though, however these posts will probably fit your issue:

[http://ubuntuforums.org/showthread.php?t=323481](http://ubuntuforums.org/showthread.php?t=323481)
[http://ubuntuforums.org/showthread.php?t=252465](http://ubuntuforums.org/showthread.php?t=252465)
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=339950](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=339950)

---

### Post by JamieC on 2007-01-10
> **flossgeek said:**
> Sorry that was a bad post, I thought it might give you some idea though, however these posts will probably fit your issue:

[http://ubuntuforums.org/showthread.php?t=323481](http://ubuntuforums.org/showthread.php?t=323481)
[http://ubuntuforums.org/showthread.php?t=252465](http://ubuntuforums.org/showthread.php?t=252465)
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=339950](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=339950)

Thanks for that, I just thought of something... I'll clear the logs for my router so I know where I am - it's currently massive - I'll try and obtain a lease and then check the logs, that way I know if my settings are correct and my router is at fault. 

If the connection to the router is made and no reply is sent, that tends to suggest the router is the source of the problem, right?

---

### Post by [L2G] Slapshot on 2007-01-10
hi Jamie

check out the thread that flossgeek pointed to

[http://ubuntuforums.org/showthread.php?t=323481]("http://ubuntuforums.org/showthread.php?t=323481")

It's my thread I responded to and I'm typing this reply to you via my Belkin wireless g usb stick same version as you. The trick to note with the rt73 driver as is with most usb drivers provided by ralink is it is plug and play. You have to reboot without the usb stick in, log in and wait till all desktop activity has ceased then insert your stick and it will plug and play the device. I'm in kde and have no problems using wireless assistant to connect. You are at that stage where your config is fine the driver is loaded and the hardware is present, you are ready to rock and roll mate just unplug reboot login and wait then insert stick and wait 15 seconds for it to be recognised and then use wireless assistant to scan and connect. You can use wep with wireless assistant , I do. Although even I had a problem connecting straight away with wep, I connected without it then enabled it after without problems.

Also the bit that told me it's plug and play is in here somewhere

[ttps://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?action=show]("ttps://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?action=show")

Check out the above thread and make sure you havent missed anything then try plugging it in after you've loaded the desktop.

Let us know how you get on
Jacko

---

### Post by JamieC on 2007-01-10
> **'[L2G] Slapshot said:**
> hi Jamie

check out the thread that flossgeek pointed to

[http://ubuntuforums.org/showthread.php?t=323481]("http://ubuntuforums.org/showthread.php?t=323481")

It's my thread I responded to and I'm typing this reply to you via my Belkin wireless g usb stick same version as you. The trick to note with the rt73 driver as is with most usb drivers provided by ralink is it is plug and play. You have to reboot without the usb stick in, log in and wait till all desktop activity has ceased then insert your stick and it will plug and play the device. I'm in kde and have no problems using wireless assistant to connect. You are at that stage where your config is fine the driver is loaded and the hardware is present, you are ready to rock and roll mate just unplug reboot login and wait then insert stick and wait 15 seconds for it to be recognised and then use wireless assistant to scan and connect. You can use wep with wireless assistant , I do. Although even I had a problem connecting straight away with wep, I connected without it then enabled it after without problems.

Also the bit that told me it's plug and play is in here somewhere

[ttps://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?action=show]("ttps://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?action=show")

Check out the above thread and make sure you havent missed anything then try plugging it in after you've loaded the desktop.

Let us know how you get on
Jacko

Sorry, I'm getting so confused here, I dont suppose you could combine the steps into one document or set of instructions and post them here. I'm not sure what I have or haven't done, to be honest.

I tried the plug-and-play method, the hardware was detected by the kernel but there was no automatic setup dialog or alert of any kind:
> 
Jan 10 21:07:21 Ubuntu kernel: [17179682.924000] usb 3-4: new high speed USB device using ehci_hcd and address 5
Jan 10 21:07:21 Ubuntu kernel: [17179683.228000] usb 3-4: configuration #1 chosen from 1 choice
Jan 10 21:07:21 Ubuntu kernel: [17179683.320000] Loading module: rt73usb - CVS (N/A) by [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
Jan 10 21:07:21 Ubuntu kernel: [17179683.468000] usbcore: registered new driver rt73usb


Thanks for your help though, much appreciated.

---

### Post by hal10000 on 2007-01-10
if [L2G] Slapshot's method does'nt work, you may try this driver download: [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

choose the **rt2570 USB nightly CVS tarball** download, this is the right one for your needs.
Here you don't need ndiswrapper. Just follow the steps in the README file to compile and configure you network.

---

### Post by hal10000 on 2007-01-10
Sorry for my posting above, I just noticed that you alredy did this. But now I'm a little bit confused, because you said that you used ndiswrapper.

---

### Post by JamieC on 2007-01-11
Thanks for your help guys, I have successfully managed to get wireless up and running. I missed a step to add plug and play functionality for the device.

One problem, though...I have to remove the USB adapter and re-plug it every time I reboot to gain a connection. Any ideas how to solve this?

---

### Post by [L2G] Slapshot on 2007-01-11
Hi mate

Thanks Hal but the rt2500 driver definately doesn't work with the device id jamie has. The correct driver is rt73, also that comes with that particular product on the windows xp cd rom. A tleast people are responding to him :-).

The stage he's at is the driver is loaded and the hardware is there but because the rt73 driver is definately plug and play he needs to turn off the p.c and then remove the usb device and then completely re boot without it right up to the desktop loading. When everything has loaded he needs to plug in the usb device and then use wireless assistant to scan and connect to his network. this will work as it's exactly what I've done here on my p.c. Unfortunately I'm using KDE not Gnome as my desktop so I think ( correct me if I'm wrong ) that he can use wireless assistant with gnome also.

Jamie the usb device is plug and play started after you put it in when everything is loaded. You will not see anything at all when you put it in. As soon as you put in the usb device you should see the green light start to flash repeatedly as the device tries to connect to the router. When you then start Wireless assistant you canconfigure your device and then scan and connect. I could not connect initially with wep enabled but disable wep and then you can connect and re enable wep when it's working.

Also please can you copy your /etc/network/interfaces file and paste it here as you may have something incorrect there also.

Try to download and install wireless assistant from adept or synaptic by searching for this.

wlassistant

this will cope with wep when the device is working and connected. You are almost there as the drivers installed and the correct hardware is there for the driver, if you reboot without it and then after loging in to your desktop it starts to flash then it's just the last couple of steps and possibly the network interfaces file. I can copy and paste my wlan0 interface file here and it can be copied and pasted into yours and then later edited for your essid and wep key.

Cheers ( we'll get there )
Jacko

---

### Post by [L2G] Slapshot on 2007-01-11
Hehe I just noticed you posted while I was writing the last post to you.

Congrats on getting it to work Jamie and in answer to your post no the device is plug and play and unfortunately that is the way it works with Linux at the moment. You have to only plug it in after everything is up and running. If I can find anything I'll pm you to let you know, but at the moment it's the only way Sorry.

Jacko

---

