---
title: "Wireless USB WIC.  Netgear WG111v2"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by mickfromperth on 2006-12-03
Hi There.  While i'm not a total newb to linux I am a total newb to ubuntu. (And ndiswrapper for that matter).  Oh and while I'm at it I've never had wireless networking set up in linux either..  So all advise on these matter's is welcome.

I just picked up a wireless USB card (Model Netgear: WG111v2).

lsusb shows:
mick@freevo:/tmp/wg111-2$ lsusb
Bus 002 Device 003: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)

What I have established from this is that the card has a realtec chipset (WG8187).  WG8187 is supported as a native driver from realtec; of which ubunto ships with a pre-combiled kernel module for.

When I modprobe this kernel module (name: r8187) it seems to find the device?
dmesg output:
[17182277.380000] usbcore: registered new driver rtl8187

However, I am unable to configure any options for the card (such as essid..).  Or for that matter scan for a wireless network to connect to:

mick@freevo:/tmp/wg111-2$ iwlist wlan1 scan
wlan1     Failed to read scan data : Operation not permitted

mick@freevo:/tmp/wg111-2$ iwconfig wlan1 essid "athome"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan1 ; Operation not permitted.

In my eagerness at this point I figure as netgear are not realtec; that my card/device is probably one of the few devices which this driver doesn't actually support..

So I move on to try ndiswrapper for the first time.  Let me firstly say how difficult I found it to get ndiswrapper fworking.  I mean really.. Which ship a module what is not compatable with the utils version that shipped???  I almost went back to gentoo before I even posted for help..

Anyways.. back to ndiswrapper.  It took about 3 days of frustration before I realised I needed to apt-get insall ndiswrapper-utils-1.8.  So now my utils matches my module and I can at least modprobe ndiswrapper..

I've tried a number of different drivers for this card (netgear has 3 different version available for download; plus the varying operating systems each is available for..).  In any case; the best I can do with ndiswrapper is to suggesfully scan for a AP:

mick@freevo:/tmp/wg111-2/ndis_files/keeps$ iwlist wlan1 scan
wlan1     Scan completed :
          Cell 01 - Address: 00:13:A3:57:BD:C0
                    ESSID:"athome"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-74 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0


But I cant attach to it..  WTF?

mick@freevo:/tmp/wg111-2/ndis_files/keeps$ sudo iwconfig wlan1 essid "athome"

Seems to work..  But when I check it, it hasn't taken:

mick@freevo:/tmp/wg111-2/ndis_files/keeps$ iwconfig wlan1
wlan1     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2432 B   Fragment thr:2432 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ifup / ifdown doesn't attach to the AP.  And i've tried to set the essid in the /etc/network/interfaces file:

mick@freevo:/tmp/wg111-2/ndis_files/keeps$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp





iface wlan1 inet dhcp
wireless-essid "athome"
wireless-key off


Soo...  Where to I go from here?????

Please help!

Mick

---

### Post by FrodoB on 2006-12-03
Do you have the native driver blacklisted?

I have the same device and scanning does work with the native driver.

Both drivers call the device wlan?, so look at the output of lsmod and make sure that both are not loaded.  Also what is the output of ndiswrapper -l at this point?

---

### Post by mickfromperth on 2006-12-03
Hi,

Yes.  I have blatlisted r8187.  Also:

I have followed this "guide" page (searched for other modules which might be competing).  But what I found was the only dirver that work automagically is r8187.  When I blacklist this I don't get any other modules competing for the device:

[http://ubuntuforums.org/showthread.php?t=212365&page=1](http://ubuntuforums.org/showthread.php?t=212365&page=1)
(I am now using the driver [netwg111v2.inf] from this page).

Also, I followed this page:
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111)

And downloaded the latest release ndiswrapper and compiled myself a new copy.  I apt-get removed ndiswrapper-common before I did this.

I do now have a flashing light!  But.. Still.. It seems as though I can no longer scan:
mick@freevo:~$ sudo iwlist wlan1 scan
wlan1     No scan results

And it doesn't seem to keep my settings: [not essid =off/any]
mick@freevo:~$ sudo iwconfig wlan1 essid athome channel 6 key off
mick@freevo:~$ iwconfig wlan1
wlan1     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2346 B   Fragment thr:2400 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


????

Mick

---

### Post by FrodoB on 2006-12-03
The reason the command you listed for the native driver did not work was that you did not use sudo in front of each of them.  You might want to blacklist ndiswrapper and remove the native driver from the blacklist and reboot then retry, always preceding each command with sudo. It may well just work then. I have one and it does work with the native driver.

---

### Post by FrodoB on 2006-12-03
You also may want to follow this thread that is now ongoing:

[http://ubuntuforums.org/showthread.php?t=311646](http://ubuntuforums.org/showthread.php?t=311646)

---

### Post by mickfromperth on 2006-12-03
Tell me to the you have lights on the native driver?  I don't really care; but I don't get lights with the native driver; and when I use sudo (as is required, but I somtetimes do forget) it won't take my commands.

I'll try one last time.  But I can already report that using netgear downloaded drivers (v1.4) the card now works (WEP & WPA untested).  This is with the latest release of ndiswrrapper (1.30).

Oh ****.  Whatever I did didn't get my ethernet card working so now I'm locked out.  Oh Well.  Goodnight.  Thanks for the help fella's!.

---

### Post by FrodoB on 2006-12-03
The light does not work with the native driver.

Do you have it working with ndiswrapper now?

---

### Post by mickfromperth on 2006-12-03
Yep.  I left it last night working with ndiswrapper with
a) Laterst release of ndiswrapper downloaded and compiled on my own.
b) oldest version of drivers avaialble from netgear (v1.4).

I really want a "stable" wireless link though so I imagine I will be revisting this again in the next few days.

---

### Post by FrodoB on 2006-12-03
Well if it seems stable in ndiswrapper I don't see a reason to change, the native driver is great if it just works for you. Some devices are really stable on ndiswrapper.

In may case the device just worked, no issues. I have seen several posts where it does not just work, maybe there are sub-versions of the device that are not documented as such.

---

