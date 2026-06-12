---
title: "ASUS WiFi-AP Solo sees networks but wont associate"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by theinsomniac on 2006-09-04
Trying to get my WiFi-AP Solo integrated USB Wireless Adapter on my Asus P5B Deluxe/WiFi-AP motherboard with Dapper 6.06 LTS.

Card is recognised, can scan and recognise available networks but is unable to associate with any access points. Turned off encryption, acpi etc. Probably something silly but I've tried for 6 hours, used the trouble shooting guide etc. Anyone got any ideas? Even if it's just "time to contact the driver developer". More details below. Thanks :)


wifi radar can see networks but not connect.
iwconfig shows radio rotating though channels till ESSID is set when it then settles to the correct freq but access point will not associate with AP, this can be forced but still no DHCP or route to network if IP details are manually set.

(Some Output trimmed to relevant information only )
#lsmod | grep r8187
r8187                  49124  0
ieee80211_rtl          88360  2 r8187
usbcore               139076  5 r8187,usbhid,ehci_hcd,uhci_hcd

# lshw -C network
*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:04:03:68
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g

# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:07:40:76:DB:8F
                    ESSID:"MYWLAN"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:16  Signal level:0  Noise level:51
                    Extra: Last beacon: 1ms ago
          Cell 02 - Address: 00:14:C1:0D:A0:64
                    ESSID:"MYWLAN"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11
                    Quality:14  Signal level:0  Noise level:20
                    Extra: Last beacon: 238ms ago

# iwconfig wlan0 essid MYWLAN

# iwconfig
lo        no wireless extensions.

wlan0     802.11b/g link..  ESSID:"MYWLAN"
          Mode:Managed  Channel=11  Access Point: Not-Associated
          Bit Rate=11 Mb/s
          Retry:on   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by lupine_nickt on 2006-09-04
so  ```
sudo iwconfig wlan0 ap 00:07:40:76B:8F"
``` or ```
sudo iwconfig wlan0 ap 00:14:C1:0D:A0:64
``` doesn't work, then?

Actually, why on earth are there two cells with two different MAC addresses (eg. two different devices) on the same channel and using the same ESSID? 

That's more likely to be your problem...

xF,

...Nick

---

### Post by theinsomniac on 2006-09-04
I tried iwconfig wlan0 ap XX:XX:XX....etc

It sets the mac address to whatever I tell it.
But still #dhclient wlan0  gets nothing back as does a ping if I set static addresses.

There should be no problem with the two APs, they're just bridging the network. Works fine with several windows machines. But I've tried turning one off and also setting them to different channels and ESSIDs but with no joy.

Any other thoughts?

---

### Post by lupine_nickt on 2006-09-04
The only other thing that comes to mind is to make sure that the network is up - "sudo ifconfig wlan0 up", then scan, then set the essid and the ap. If that doesn't work, check your dmesg and syslog, and try the developers...

xF,

...Nick

---

### Post by theinsomniac on 2006-09-04
Tried that with no joy.


Bits from dmesg
rtl8187: Initializing module
rtl8187: Wireless extensions version 19
rtl8187: Initializing proc filesystem
rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
rtl8187: Card MAC address is 00:15:af:04:03:68
rtl8187: Card reports RF frontend Realtek 8225
rtl8187: WW:This driver has EXPERIMENTAL support for this chipset.
rtl8187: WW:use it with care and at your own risk and
rtl8187: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO [email]andreamrl@tiscali.it[/email]
rtl8187: This seems a new V2 radio
rtl8187: PAPE from CONFIG2: 0
rtl8187: Driver probe completed
rtl8187: Card successfully reset
ADDRCONF(NETDEV_UP): wlan0: link is not ready

Bits from syslog
Most of the above plus

localhost kernel: [17181907.820000] Linking with MYWLAN
localhost kernel: [17181910.368000] Linking with MYWLAN
localhost kernel: [17181912.916000] Linking with MYWLAN
localhost dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
localhost kernel: [17181915.464000] Linking with MYWLAN


"Linking with..." is repeated every 5 seconds or so.


Guess it might be time to ask the developers. I'm just worried that I've missed a step that eveyone but me knows.

---

### Post by amonsul on 2006-09-06
Same problem here. P5B Deluxe (wifi) Motherboard cannot connect to my Router. (With my old Ubuntucomputer all works fine...)

I dont know...

---

### Post by hearnden on 2006-09-06
I've had exactly the same problems, and I'd give up (at least for a few months).  The onboard WiFi on the P5B Deluxe is a POS.  I've tried for weeks to get it to work in Ubuntu 6.06.  I had come to the conclusion that the Realtek RTL8187 USB adapter was too recent to work completely with the r8187 driver module, but then it also just died in WinXP too, after having *just worked* for weeks. Reinstalled a few times, still broken - can't see any APs now in XP.

Moral of the story: never go for onboard WiFi.  Because now the only solution left is to get a WLAN card, meaning that the onboard one just sits there wasting space, and will no doubt cause all manner of confusion when trying to set up a new card.

---

### Post by amonsul on 2006-09-07
Ok WIFI dont works, and normal LANconnection works?  I have a lot of problems and i cannot connect me to my router!

(Asus P5B Deluxe 965 WIFI)

---

### Post by hearnden on 2006-09-09
> **amonsul said:**
> Ok WIFI dont works, and normal LANconnection works?  I have a lot of problems and i cannot connect me to my router!

(Asus P5B Deluxe 965 WIFI)

Yep, LAN connection works fine.  WiFi however has been pwned.  Same problems as theinsomniac in Ubuntu 6.06: can see AP, but can't connect to it.  Anyone else's P5B Deluxe WiFi work in Ubuntu or XP?

---

### Post by amonsul on 2006-09-09
Hi hearnden!

Lan works fine? For me noway! What Bios-Software do you have?

---

### Post by hearnden on 2006-09-10
> **hearnden said:**
> Yep, LAN connection works fine.  WiFi however has been pwned.  Same problems as theinsomniac in Ubuntu 6.06: can see AP, but can't connect to it.  Anyone else's P5B Deluxe WiFi work in Ubuntu or XP?

I'm using BIOS 507, but it was working for all BIOS versions I tried.  I think I had 10<something> when I first got the motherboard, and upgraded to 405 and then 507.  I've got a Linksys WAG54GV2 as a router, plugged in the cables and it *just worked*.  I use NetworkManager instead of network-admin, but I think it worked with network-admin too.  Note that only the bottom LAN port works for me.  This might be something to do with the one port showing up as "Unknown device" in lspci:

```

hearnden@connie:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation P965/G965 Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation P965/G965 PCI Express Root Port (rev 02)
0000:00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
0000:00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
0000:00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
0000:00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
0000:00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
0000:00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
0000:00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4364 (rev 12)
0000:03:00.0 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
0000:05:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:05:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

```

The WLAN shows up in lsusb:

```

hearnden@connie:~$ lsusb
Bus 006 Device 002: ID 0bda:8187 Realtek Semiconductor Corp.
Bus 006 Device 001: ID 0000:0000
Bus 007 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 008: ID 046d:c703 Logitech, Inc.
Bus 003 Device 007: ID 0451:2036 Texas Instruments, Inc. TUSB2036 Hub
Bus 003 Device 001: ID 0000:0000

```

but it just doesn't work.

Does your LAN work in anything other than Ubuntu (Windows, Mac OS, other Linux..)?

---

### Post by ashram on 2006-10-13
My MoBo is m2n32 with WiFi RTL8187 chip.

Linux drivers didn't worked, so I moved to ndiswrapper and blacklisted r8187 module. Windows XP drivers gave me "linking with" problem.
The only driver that the solved problem was win98 original driver.

The only problem that it disconnecting all the time and the only sollution is reboot...

In another thread it was recommended to change "beacon interval" from 100 to 10 but it didn't helped...

[http://ubuntuforums.org/showthread.php?t=271625&page=4](http://ubuntuforums.org/showthread.php?t=271625&page=4)

Any recommendation are welcome

---

### Post by kwaanens on 2007-01-11
I'm going to build a new computer, and I'm looking at this mobo (Asus P5B Deluxe/WiFi-AP). Does it work OK otherwise? (Does the wifi work with Edgy?)

Thanks for your response!

- Ketil

---

### Post by hfdragon on 2007-01-11
I have it working !!! :-)

The problem I had was that it couldn't associate with the AP (kept having a message in dmesg showing it was trying to associate)

All I did was download the drivers from realtek :

[http://www.realtek.com.tw/]("http://www.realtek.com.tw/")

And follow the guide !

I'm quite sure network-manager doesn't work, but you still can connect 'manually' via the command line :-)

I can't give you much more informations right now since i'm typing this on my laptop... I'll need to be home to give you more details if you need.

Anyway, I have the wifi working on my ASUS P5B Deluxe wifi :-)

---

### Post by rko618 on 2007-01-31
> **hfdragon said:**
> I have it working !!! :-)

The problem I had was that it couldn't associate with the AP (kept having a message in dmesg showing it was trying to associate)

All I did was download the drivers from realtek :

[http://www.realtek.com.tw/]("http://www.realtek.com.tw/")

And follow the guide !

I'm quite sure network-manager doesn't work, but you still can connect 'manually' via the command line :-)

I can't give you much more informations right now since i'm typing this on my laptop... I'll need to be home to give you more details if you need.

Anyway, I have the wifi working on my ASUS P5B Deluxe wifi :-)


Hfdragon, can you elaborate on what you did?  A step-by-step HOWTO would be really really appreciated :).

---

### Post by edmonte on 2007-02-20
Hi,

I am using a Asus M2N32-SLI Deluxe motherboard with wifi on board.
I had the same problems on ubuntu 6.10 edgy , no connection to the router, no wifi-radar.
I solved the problem using the ndiswrapper-utils-1.8 (this was not the default when I installed ndiswrapper-utils!!!).
[LIST=1]
[*]install ndiswrapper-utils-1.8
[*]download me98se-8187(1221).zip (at opendrivers)
[*]install the driver (the instruction using ndiswrapper is easy, search the forum)
[*]then I edited the /etc/modprobe.d/blacklist , I added the lines r8187 and rtl8187 as described somewhere above, this will block the modules from being loaded
[*]edit the file /etc/modules, just add ndiswrapper and the module will be loaded during the booting of the system
[*]check if your entrie in /etc/network/interfaces include your wlan card
[*]reboot, and I was connected to the router.
[/LIST]

All right this is my first entry to the ubuntuforum.
Hope it helps

---

### Post by esquisoblogs on 2007-03-19
Ok, I'm really tired to try to do this on my own. I really need some help.

I followed that thread, and I try to do this by installing the Realtek drivers. I use the rtl8187B_linux_24.6.1021.0212.2007 drivers to do this. After do all the steps on the Read Me.txt, i get this at iwconfig wlan0

> 
wlan0 802.11b/g link.. ESSID:"Sitecom"
Mode:Managed Channel=11 Access Point: 00:04:ED:54:C7:F5
Bit Rate=11 Mb/s
Retryn Fragment thrff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


And, of course, there's no wireless.
Am I doing something wrong?

---

