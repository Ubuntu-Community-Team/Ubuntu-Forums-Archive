---
title: "Dell Latitude D610 Wireless Problem"
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by issueperson on 2006-12-19
Hey All,
I'm having problems on my Dell Latitude D610 laptop.  The wireless connection, which was fine when i ran Dapper and Breezy, is having problems with Edgy.  My network card is a PRO/Wireless 2915ABG Network Card.  I turned off WPA encryption on my router until i can get the basic wireless working.  I also uninstalled Dell QuickSet power schemes in windows just to be sure that isn't messing things up.

The router name is Heroic Couplet and works fine in windows.

I've been trying a lot from all of these forums, but to no avail.  I'm back to the initial setup now.  

iwconfig gives me the following:

```
brady@sophie:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions
```

I also get:

```
brady@sophie:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
```

And I get
```
brady@sophie:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

I'm currently plugged into my router via ethernet cable and having no problems with that.

If anyone has any suggestions, i'd love to hear 'em.
issue person

---

### Post by usererror on 2006-12-19
do "a iwlist eth1 scanning" 

does it list the nearby wireless networks?

---

### Post by issueperson on 2006-12-19
```
brady@sophie:~$ iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:16:B6:30:8C:1A
                    ESSID:"Heroic Couplet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=95/100  Signal level=-32 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 960ms ago


```

---

### Post by issueperson on 2006-12-21
Still having this problem.  Anyone able to help me?

---

### Post by gb5757870 on 2006-12-27
hey issueperson,

let me first tell you that I share your frustration. It's taken me months to get my wireless working.

The person/forum that finally provided the instructions is: 
[http://ubuntuforums.org/showthread.php?t=324922]("http://ubuntuforums.org/showthread.php?t=324922")

If you are trying to use the native linux drivers from DELL or Intel's site, don't waste your time. Some people appear to have gotten it working but I went through hours of frustration until I finally found the above forum which shows a way to get it working using ndiswrapper.

I'm still somewhat of a newbie and while the instructions are excellent, they do assume a few pre-reqs.

Following the advice of many forum members, I started off with a fresh install of Ubuntu Edgy  before attempting the above.  That itself brought it's own problems as I had to do a few things before the instructions. Being a novice user, I can't remember them all, but it's things like installing:
- ndiswrapper-utils
- build-essential

**Very Important: ** When installing the driver, use *bcmwl5a* not bcmwl5. A link to download the drivers is on the above forum. Also very important is to follow the instructions in the INSTALL file after extracting the ndiswrapper zip file.

Good luck and feel free to ask for help but I can't guarantee I'll actually be able to!

g

---

### Post by fredj on 2006-12-27
It seems that you have the correct driver installed since the iwlist detects your network and
seems to show that it has WPA TKIP encryption installed. I thought you had disabled this.
Run the iwlist command again and post the output.
Go to System->Administration->Networking and post what shows up in this screen. If you have
some patience it is possible to get reliable wireless networking configured but don't follow
random suggestions from people who have still not solved the problem themselves.

---

