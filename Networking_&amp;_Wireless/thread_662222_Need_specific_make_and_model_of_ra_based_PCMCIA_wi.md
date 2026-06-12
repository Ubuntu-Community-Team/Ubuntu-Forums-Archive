---
title: "Need specific make and model of ra based PCMCIA wireless card"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by kevdog on 2008-01-08
In order to help all of you guys out, I was at Office Depot this morning (shopping for supplies) and wandered into the networking section.  I had a sudden inspiration that it be great if I bought an additional ra based card -- I own broadcom and atheros wireless chipsets -- to help the community troubleshoot ra based chipsets.  I asked the clerk if he had any ra chipset wireless devices, however he had no idea what I was talking about.

Can anyone give me an exact name, model, make of a wireless PCMCIA wireless card running an ra chipset (like rt2500 or rt73)?

---

### Post by kevdog on 2008-01-09
No one has an Ra wireless device?

---

### Post by rustybronco on 2008-01-09
I don't, but I will do some reseach to find out. are you looking for a new card only or will older models do such as from e-bay ect.?

---

### Post by bailout on 2008-01-09
I found this list but not sure how many are current models or how easy it would be to link model numbers to real products.

[http://ralink.rapla.net/](http://ralink.rapla.net/)

I have a belkin ralink based usb stick and IIRC they used several different chipsets in different versions of the productt but they were all sold as the same model. One of the first steps to setting it up was to find out which version I actually had and what chipset it used.

I think it may be easier to start with the list of adapters available to you in the shop and then find out what they use.

Good luck and kudos to you for doing this :D

I have just followed a howto to get my ralink dongle to work but can't get knetworkmanage to see it now. If you have any ideas or tips it would be appreciated. thread here

[http://ubuntuforums.org/showthread.php?t=588045&page=8](http://ubuntuforums.org/showthread.php?t=588045&page=8)

---

### Post by kevdog on 2008-01-09
Thanks for that list -- I saw it to -- The guy at Office Depot actually let me look up things on his computer.  The problem is that much of the actual labeling on the box does not correspond with whats stated on the ra website.  I have no idea what version the card is by looking at the box (no brand states this information).

Specifically Im looking for a PCMCIA laptop wireless card with an Ra chipset.  I think DLink offers Ra based devices -- the problem is I dont know which model.  The DLink website (or any other website for that matter) doesnt help.  I was hoping some other users here in the forums could share their make and model of card to help me out!

---

### Post by rustybronco on 2008-01-09
[http://cgi.ebay.com/NEW-Linksys-Wireless-G-card-WPC54GR-WPC54G-RangeBooster_W0QQitemZ110212732514QQihZ001QQcategoryZ45000QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/NEW-Linksys-Wireless-G-card-WPC54GR-WPC54G-RangeBooster_W0QQitemZ110212732514QQihZ001QQcategoryZ45000QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

Manufacturer Linksys (Cisco) Standard 802.11g/b 
Model Number WPC54GR Drivers Included Yes, CD-ROM 
**Chipset Ralink RT61** Cosmetic Grade NEW Retail 
OS Compatibility Win98SE/2000/ME/XP/Vista Speeds 54mbps

[http://www.officedepot.com/textSearch.do?uniqueSearchFlag=true&Ntt=WPC54GR&x=10&y=7](http://www.officedepot.com/textSearch.do?uniqueSearchFlag=true&Ntt=WPC54GR&x=10&y=7)

[http://jelnet.free.fr/jlnt_lwpc.htm](http://jelnet.free.fr/jlnt_lwpc.htm)

---

### Post by kevdog on 2008-01-09
Linksys puts out cards with ra chipsets -- Thats news to me

I should have known rustybronco would have pointed me towards a Linksys product (I miss the turkey!) :)

---

### Post by rustybronco on 2008-01-09
And I am buying one of the cards (there are two on e-bay ) to try out different things with it.
***edit*** bought
link to the 2nd one [http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&rd=1&item=110212732604&ssPageName=STRK:MEWA:IT&ih=001](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&rd=1&item=110212732604&ssPageName=STRK:MEWA:IT&ih=001)

---

### Post by rustybronco on 2008-01-12
output of the linksys wpc54gr ```
 *-network
       description: Wireless interface
       product: Ralink RT2600 802.11 MIMO
       vendor: RaLink
       physical id: 0
       bus info: pci@06:00.0
       logical name: wmaster0
       version: 00
       serial: xx:xx:xx:xx:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.2 latency=64 multicast=yes wireless=IEEE 802.11g
```

contents of iwlist scan (I am using 7.04 with the 2.6.24 kernel )
I'll try it with a fresh install of 7.04 and a fresh install of 7.10 as soon as I can.
```
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

Warning: Driver for device wlan0 has been compiled with version 22
of Wireless Extension, while this program supports up to version 20.
Some things may be broken...

wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:42:19:DE
                    ESSID:"thedogs"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=68/100  Signal level=-48 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000002eb7698a

eth0      Interface doesn't support scanning.

```
set the mac address in the router, removed my dynex card plugged the new card in, turn the laptop on, entered the essid and wep security code, changed to static mode and and yes i'm online wireless

I will reboot and see if it sticks.
***rebooted*** and working fine
***edit*** works in roaming mode also
**NOTE** dropping connections!  will try wicd...
wicd working fine so far with no speed issues, but i'll try it for 24 hours or so.
*****EDIT***** downloaded 5 gigs over two days, no speed issues, no dropped connections... If you have problems with networkmanager and this chipset, use wicd
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)
7.04 live cd 
```
*-network
       description: Wireless interface
       product: Ralink RT2600 802.11 MIMO
       vendor: RaLink
       physical id: 0
       bus info: pci@06:00.0
       logical name: ra0
       version: 00
       serial: xx:xx:xx:xx:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS ip=192.168.1.2 latency=64 multicast=yes wireless=RT61 Wireless
```
Network manager and manual configuration only! no roaming mode...

7.10 live cd
```
 *-network
       description: Wireless interface
       product: RT2600 802.11 MIMO
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 00
       serial: xx:xx:xx:xx:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.2 latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g

```
roaming mode works....

---

