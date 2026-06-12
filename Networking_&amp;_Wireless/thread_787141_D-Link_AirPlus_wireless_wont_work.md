---
title: "D-Link AirPlus wireless wont work"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by shortandfatloop on 2008-05-08
Please help I am 2 weeks into Ubuntu and its great on my desk top but now I have installed it on my wife's laptop but can't get the wireless connection to work.



I have a Toshiba Equium Laptop EA60-173 MODEL NO. PSA67E-007008J.

 DWL-G650+ PCMCIA wireless adaptor.

I have installed Ubuntu 8.04 with Windows XP duel boot.

The Network Manager shows my wireless network and my neighbours too.

I have Linksys WRT300N Wireless DSL Router. When I set it up about 12 months ago I typed in some words and it gave me a 26 figure passphrase consisting of letters c to d and numbers 0 to 9, is this HEX?

I have entered this as WEP 128-bit Passphrase also in WEP 64/128-bit Hex, in the formats XXXXXXXXXXXXXXXXXXXXXXXXXX and XXXX-XXXX-XXXX-XXXX-XXXX=XXXX-XX and with authentication set to both open system and shared key. I have also tried WEP 64/128-bit ASCII. The Network Manager icon spins around and then the dialogue box reappears. After a couple of attempts the Network Manager icon disappears and I have to reboot to get it back.

The D-Link card Link LED is permanently lit and the Act LED flashes when Network Manager icon is spinning around.

Windows XP connects every time no problems.

Ubuntu connects ok through a Ethernet cable.



Some info about my system.



sudo iwconfig returns



lo        no wireless extensions.



eth0      no wireless extensions.



wlan0     IEEE 802.11b+/g+  ESSID:""  Nickname:"acx v0.3.36"

          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   

          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  

          Retry min limit:7   RTS thr:off   

          Encryption key:off

          Power Management:off

          Link Quality=31/100  Signal level=4/100  Noise level=0/100

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



sudo lspci returns



00:00.0 Host bridge: ATI Technologies Inc R200 AGP Bridge [Mobility Radeon 7000 IGP] (rev 05)

00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]

00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)

00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)

00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)

00:14.0 SMBus: ATI Technologies Inc SMBus (rev 18)

00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller

00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c

00:14.4 PCI bridge: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller

00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility 7000 IGP

02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)

02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)

03:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface



sudo ifconfig returns



eth0      Link encap:Ethernet  HWaddr 00:a0:d1:b5:ea:58  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:18 Base address:0xa000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:1662 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1662 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:83100 (81.1 KB)  TX bytes:83100 (81.1 KB)



wlan0     Link encap:Ethernet  HWaddr 00:0f:3d:57:af:4a  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:160 (160.0 B)

          Interrupt:16 



I have tried lots of code listed in the Ubuntu forum and have set my router unsecured, I have tried ndiswrapper and installed my D-Link cards Windows driver, nothing seems to work? I now have a fresh install again but still no wireless.



Thank you in advance

---

### Post by chili555 on 2008-05-08
I don't know much about Network Manager, except it works great for some and grumpy for others. I don't know why you are parked in "grumpy." When I have these troubles, I call on my old pal Manual. First, turn off Roaming so NM and Manual do not fight for world wireless domination. Second, find out if you left your router in Shared Key or Auto. Make sure Key 1 is the key being transmitted.> 26 figure passphrase consisting of letters c to d and numbers 0 to 9, is this HEX?Yes, it is. WEP is the least secure encryption method, so, once we master WEP, I'd recommend you look at WPA. This guy: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539) is the forum expert on WPA. I, being an old-timer, have been helping with WEP.

Let's assume you are Shared Key. Open a terminal and do:```
sudo iwlist wlan0 scan
```Determine the exact ESSID. In Linux, myrouter is a different station than Myrouter, as is MyRouter.

Then do:```
sudo iwconfig wlan0 essid <ur_essid>
sudo iwconfig wlan0 key 01234..26-characters...567890 restricted
sudo dhclient wlan0
```Did you connect or time out? If the router's set in Auto, rather than Shared Key, simply omit *restricted.*

If this is a stationary computer that doesn't go to Starbucks, you can safely remove NM and hard-code these details in */etc/network/interfaces.*

---

