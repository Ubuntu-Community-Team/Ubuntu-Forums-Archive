---
title: "Can't connect to wireless network, I've tried everything - help!"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by oldsmobile_mike on 2008-01-19
I'm sure you've heard it before, new Ubuntu user trying to set up wireless network connection, blah blah blah...  well, here's another one, and I just can't get it to work.

System is a Sager 5600P laptop, fresh install of Ubuntu 7.10, using an internal miniPCI wireless network card.  I've tried with an Intel 2200-series card, using the instructions found here:  [http://untitledfinale.wordpress.com/2007/10/22/update-ieee-80211-and-ipw2200-on-ubuntu-gutsy/](http://untitledfinale.wordpress.com/2007/10/22/update-ieee-80211-and-ipw2200-on-ubuntu-gutsy/)  and while the instructions were flawless, and I was able to see my network, I couldn't connect.  Each time the little icon made like it was trying to connect, but never did, and didn't give any error message.  My Network Settings are configured for "Roaming", and I tried with WEP, WPA, and no security on my router.  It would ask for the appropriate key, but would never connect.

So I tried it with a second card, an Orinoco Gold, which is listed here:  [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsProxim](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsProxim)  as "just works".  Well, sure enough, the card was detected without having to install any additional drivers or anything, and I can see my network, but again - same problem.  When you try to connect, the little wireless thing just spins around, but never connects.

I've even tried booting off the 7.10 CD, and had the identical problem.  Again, I've tried all the security settings, WEP, WPA, WPA2, no security, etc., and all my Windoze PC's in the house connect just fine.

Please help!  Thanks!  :-)



**PS - my lspci settings show this:**

mike@Sager-5600P:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:07.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
02:09.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)


**and my iwconfig shows:**

mike@Sager-5600P:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:""  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: None
          Bit Rate:11 Mb/s   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


**and ifconfig shows:**

mike@Sager-5600P:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:F5:0E:07:8B
          inet addr:192.168.1.86  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f5ff:fe0e:78b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:617 errors:0 dropped:0 overruns:0 frame:0
          TX packets:518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:670296 (654.5 KB)  TX bytes:65728 (64.1 KB)
          Interrupt:9 Base address:0x6800

eth2      Link encap:Ethernet  HWaddr 00:02:2D:34:87:97
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1296 (1.2 KB)  TX bytes:0 (0.0 b)
          Interrupt:9 Base address:0x4100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5276 (5.1 KB)  TX bytes:5276 (5.1 KB)


Note that I am currently connected via the Ethernet connection ;-)

---

### Post by Hightide on 2008-01-19
Hi

i was going to suggest that you work of the live CD but I see you already invoked that option.

Various threads suggest that various wireless drivers and Network Manager clash causing weird problems

Try WICID as an alternative instead of networkmanager. [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Code:
sudo apt-get remove network-manager;

sudo apt-get install wicd;

make sure you remove Network Manager before installing wicid

hope this helps
:)

---

### Post by oldsmobile_mike on 2008-01-20
Thanks, Hightide!

Installing wicd showed me that it was hanging at the point where it gets a DHCP address, at which point I went back to the settings on my router (a WRT54G running the latest DD-WRT), and saw that even though I had MAC filtering disabled, I remembered that sometimes DD-WRT has issues with applying settings, so on a hunch I selected "disable MAC filtering" again, and hit apply, at which point I was able to connect.  I'm still having a few issues with WPA and WEP-128 not working, but if I set it to WEP-64 it's able to connect (I think that's because this old 802.11b card doesn't support those encryption features, however).

PS - your install steps were backward - if I do "sudo apt-get remove network-manager" it removes all my network capabilities, including the wired, so I wasn't able to connect to do the wicd install...  however I was able to figure out the proper install procedure (using Synaptic Package Manager) from the link you provided.  Thanks!

---

### Post by clsgis on 2008-01-20
> **Hightide said:**
> 
Try WICID as an alternative instead of networkmanager. [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Code:
sudo apt-get remove network-manager;

sudo apt-get install wicd;

make sure you remove Network Manager before installing wicid


When you remove gnome-network-manager it turns off whatever interfaces it had turned on.  You'll probably lose your default route:oops:, so you can't see the Internet to get wicd.  Most people are on the net via DHCP.  If that's you, type

dhclient

to get back on:biggrin:.

---

