---
title: "rt2500: wpa headaches"
date: 2006-09-20
forum: Networking &amp; Wireless
---

### Post by leodp on 2006-09-20
Hi forum,

I'm completely lost, I'm trying to have my ralink wlan card working in wpa, but get nowhere; I've followed lots of HOWTOS and forum threads here, and on rt2x00 project, as well as stuff regarding other distros, but each one makes more and more  confusion in my poor mind, or maybe it's only the wlan antenna baking my brain.

I think the configuration has problems when it comes to dhclient ra0, 'cause I repeatedly get the log:
Listening on LPF/ra0/00:0d:f0:15:1f:29
Sending on   LPF/ra0/00:0d:f0:15:1f:29
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 19
No DHCPOFFERS received.
No working leases in persistent database - sleeping.



The card is a minipci one (lspci -v):
0000:00:0a.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
        Subsystem: RaLink: Unknown device 2560
        Flags: bus master, slow devsel, latency 64, IRQ 5
        Memory at dfffa000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>

I tried the rt2500 AND rt2x00 drivers (with kernel 2.6.17, no SMP, x386), both with the last release, the CVS and the dayly checkout.

I tried WPAPSK AES and TKIP (WPA1 and WPA2 are supported by the access point), but it works only with WEP, that I want to avoid (also because it's not my network and I cannot push too much)

I edited and reedited /etc/network/interfaces, that now has this stanza:
auto ra0 
iface ra0 inet dhcp
pre-up iwconfig ra0 essid "REMOVED"
pre-up iwconfig ra0 mode managed
pre-up iwpriv ra0 set Channel=2
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="REMOVED"
pre-up iwpriv ra0 set TxRate=0
I added and removed here also some lines for the gateway and the DNS, without success.


I edited and reedited /etc/Wireless/RT2500STA/RT2500STA.dat, this being the last version:
# Copy this file to /etc/Wireless/RT2500STA/RT2500STA.dat
# This file is a binary file and will be read on loading rt2500.o module.
# Use "vi -b RT2500STA.dat" to modify settings according to your need.

[Default]
CountryRegion=0
WirelessMode=0
TXBurst=0
TurboRate=0
BGProtection=0
ShortSlot=0
TxRate=0
PSMode=CAM

#SSID=OFFICEWAPG
#NetworkType=Infra
#Channel=1
#AuthMode=WPAPSK
#EncrypType=TKIP
#DefaultKeyID=1
#Key1Type=0
#Key1Str=
#Key2Type=0
#Key2Str=
#Key3Type=0
#Key3Str=
#Key4Type=0
#Key4Str=
#WPAPSK=abcdefghijklmnopqrstuvwxyz
#RTSThreshold=2312
#FragThreshold=2312
#PSMode=CAM
#RFMON=0
SSID=REMOVED
NetworkType=Infra
PreambleType=Auto
RTSThreshold=825307441
FragThreshold=2312
WPAPSK=REMOVED
Channel=0
AuthMode=WPAPSK
EncrypType=AES
BOOTPROTO='dhcp'

Radio=1
AdhocOfdm=0
ProfileID=PROF003
SSID=REMOVED
NetworkType=Infra
PreambleType=Auto
RTSThreshold=825307441
FragThreshold=2312
WPAPSK=REMOVED
Channel=0
AuthMode=WPAPSK
EncrypType=AES
BOOTPROTO='dhcp'


Anybody can tell me what's going on?

Ciao and goodnight for today, 
sad Leo

---

### Post by lupine_nickt on 2006-09-20
OK - you're sort-of there. The drivers are working fine; the only reason you're not connecting is because WPA isn't working. Once that's set up, dhclient etc. will work fine.

Since you're using the rt2x00 (legacy or new - I'd recommend you use legacy for now) drivers, you should use the rutilt GUI configuration utility. I've made this easy by setting up a repository for it - see the thread about it  [here](http://www.ubuntuforums.org/showthread.php?t=240669).

Let me know how you get on :)

xF,

...Nick

---

### Post by leodp on 2006-09-21
Hi Nick,

I already tried with rutilt, but the problem persists (also with RaConfig2500).

I see all the wlans, mine has Link quality 60%, signal level -71dBm, noise level -194dBm, there are packets in and out, no error/collisions, and I on the shell from where I launched rutilt I get the messages:

 Listening on LPF/ra0/00:0d:f0:15:1f:29
Sending on   LPF/ra0/00:0d:f0:15:1f:29
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


I tried all the possibilities:WPAPSK with AES, TKIP and ASCII or non ASCII key (althought I don't know its meaning).

Ciao, Leo

---

### Post by DutchKid on 2006-09-21
> **lupine_nickt said:**
> OK - you're sort-of there. The drivers are working fine; the only reason you're not connecting is because WPA isn't working.

Hi Nick, I'm sorry to interrupt ;) but can you please explain: how can you tell whether the drivers are working fine? What test should be done and what should the result of this test be? Thanks very much!

---

### Post by dgrafix on 2006-09-21
I had exactly the same problem with same card, for some reason my router not giving address.
What i did to fix it was simply choose a static one:

auto ra1
iface ra1 inet static
pre-up ifconfig ra1 up
pre-up ifconfig ra1 down
pre-up ifconfig ra1 up
pre-up ifconfig ra1 down
pre-up iwconfig ra1 essid "your SSID"
pre-up iwconfig ra1 mode Managed
pre-up iwpriv ra1 set AuthMode=WPAPSK
pre-up iwpriv ra1 set EncrypType=TKIP
pre-up iwpriv ra1 set WPAPSK="your key (in hex not in text!)"
pre-up ifconfig ra1 up
address 192.168.1.4
netmask 255.255.255.0
gateway 192.168.1.1

---

### Post by leodp on 2006-09-22
Hi dgrafix,

thanks, I'll try that too.
However, yesterday also the other PC in the wlan could not connect, even if it has an OS that should do everything alone.
It was funny to see, after going through various "advanced" buttons, that pressing the one for "repairing damaged connections" a message popped up asking to contact the wlan manager, that is... the same owner of that PC.

I'll try to reboot the router and will post the results.

Thanks to all, Leo

---

### Post by leodp on 2006-09-23
Hi again,
I stop: after trying for some more hours configuring router AND Linux PC and Win PC,  I cannot track the problem further and don't have so much spare time.

I stay with WEP plus a block on MAC addresses.
Thanks to all those that helped, read you next time.

Ciao, Leo

---

### Post by Ed Lata on 2006-11-07
It sounds like you're almost there.  I recently upgrade my RaLink laptop card RT2500 to WPA-PSK (AES) on an XP system and it is working somewhat which I'll explain later.

You need to make sure that your WPA key phrase is correct if it is only not working on WPA.  This key is case sensitive.  I would venture to say that you may not have the correct SSID name entered (also case sensitive) but you state that you can get your system running using WEP.  In the RaLink utility, you set up a profile which you must activate.  Under that profile, you must enter all the pertinant information such as the WPA key, etc.

I use WPA-PSK with AES.  I upgraded my RaLink driver from [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)

My problem, if someone out there can help, is that I could not get my AVG firewall running.  It would take forever to activate, then without activation, would provide an error message that the firewall was down.

OK, someone suggested that the Windows firewall was interfering with the installation and I found that my XP Home system didn't have a Windows Firewall.  Next step - download and install the SP-2 pack.

Here's where my real problems started.  I tired to install the connection to a network, but it errored, saying that it could not install it.  It seemed that XP now wanted a complicated LAN set-up that suggested running the Wireless Zero Configuration utility.  Big problems after doing this.  My RaLink wireless card started to cycle on and off between connected and disconnected, showing the wireless signal and not.  Whereas before, I could at least get out onto the Internet, now I could not.  Back to re-loading the RT2500 drivers.  (There may be a way to fix this using the Windows Wireless Zero Configuration utility, but I don't know which settings to use.

Once that was done, my initial problem persisted - I still can't get onto my LAN - but at least I can get onto the Internet!

Anyone have the wireless Zero Configuration settings or could explain to me how to set up a LAN in XP with the SP-2 pack?  The SP2 upgrade insists that I insert a USB key which I take around to all my other computers and somehow install.  My problem is that I run different operating systems like Windows 2000.  I want to skip this part since I didn't have to do it before when prompted.

I've seen references to a RaConfig.exe utility on this bulletin board which would probably solve my problems since Windows XP support document 871122 makes reference to using the vendor's software instead of the Wireless Zero Configuration utility.  Unfortunately, I have not found a copy of it from the RaLink website.

Anyone have a copy?

Cheers,

Ed

Ed

---

