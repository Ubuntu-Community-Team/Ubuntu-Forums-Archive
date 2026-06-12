---
title: "Connect to a wirless router"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by pk_rulz on 2008-03-05
Hi

I installed drivers for  Dell Inspiron 1520 using the restricted drivers management and it seems to detect my wireless card

My laptop is able to detect Wifi networks but when I connect to them using the WEP password(using GUI) it shows
Wireless network connection to <SSID> (0%)

What is this 0% whats the issue

Thanks 
Pradeep

---

### Post by Hightide on 2008-03-05
Hi

Just want to check if you have an ip address assigned to your device.  Please post output of

```
sudo ifconfig
```


regards

:)

---

### Post by pk_rulz on 2008-03-05
Nope I checked that ... I dont have 1

When i connect to the router using wired connection I get an IP for eth0

But wirelessly i never get anything for eth1

---

### Post by pk_rulz on 2008-03-06
Tried the sticky forum for wireless connection 

Still not  use

:(

Please help

---

### Post by rustybronco on 2008-03-06
Please post the output of
 **lshw -c network**
**iwlist scan**
**ifconfig**

have you read these?

[http://ubuntuforums.org/showthread.php?t=596797](http://ubuntuforums.org/showthread.php?t=596797)

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by pk_rulz on 2008-03-06
lshw -C network
 description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: XXXXXXXX
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-gener


iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:13:10:75:C4:75
                    ESSID:"XXXXX"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=95/100  Signal level=-50 dBm  Noise level=-69 dBm
                    Extra: Last beacon: 68ms ago

I am using WEP with 64bit Hex authentication

---

### Post by MadnessRed on 2008-03-06
have a similar problem, cant connect to router but mine is because my router is port 13 however ubuntu defaults to american range, 1 to 11, how can i change this?

---

### Post by pk_rulz on 2008-03-06
how can i check my router port ... i think u can choose ur port wen u use dhcpcd to get dynamic IP

---

### Post by MadnessRed on 2008-03-06
im guessing your in windows if you are posting this...

i have belkin so mine is different to yours. but look for where it says channel

its might be under the view all available networks

but if it is that problem i dont know how to fix it

where are you from? what contry?

and if anyone does know how to fix this please let me know

---

### Post by pk_rulz on 2008-03-06
I m from India but I m using an American Linksys router and I am on Ubuntu ... wired

---

### Post by MadnessRed on 2008-03-06
ok, your different to me, i cant even see my network because it is out of range

---

### Post by pk_rulz on 2008-03-06
After i run iwconfig I get this What does the highlightrd part mean

eth1      IEEE 802.11b/g  ESSID:"XXXX"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:13:10:75:C4:75   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          **Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0**
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by rustybronco on 2008-03-06
> **pk_rulz said:**
> After i run iwconfig I get this What does the highlightrd part mean

eth1      IEEE 802.11b/g  ESSID:"XXXX"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:13:10:75:C4:75   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          **Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0**
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
> **Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0**
RX=receive, nw=network, i.d.= indentification,  crypt=cryptography (encryption), frag= fragments

but the bigger problem is you are not associated to the access point.

> My laptop is able to detect Wifi networks but when I connect to them using the **WEP password(using GUI)**
> I am using WEP with 64bit **Hex** authentication
are you sure you have the correct key (ascII or hex) ?

> Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
also your signal levels are for all intents and purposes are ZERO.
you can try connecting from the command line in one of the links I gave you, and see if you can connect that way. if not you can try this how-to [http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963) or possibly read the various threads for your chipset "product: BCM94311MCG wlan mini-PCI"

ndiswrapper and the proper windows drivers are sometimes the preferred solution if the native drivers don't work.

let me know what I can do to help.

---

### Post by pk_rulz on 2008-03-09
Hi

Thanks every1 who helped me with this wireless issue.

I was not able to connect to Wifi from  a linksys router WRT54G v3 using Ubuntu 7.10 running from Dell Inspiron 1520 (with Broadcom chipset) even after I had installed the restricted drivers.

Aftr trying almost every sticky here n some  help from rusty n kevdog was of no avail ... 

The issue was resolved by a firmware upgrade of the Linksys router .... hehe 

Sometimes the issue is where u cant imagine it....

Seems like all Linux users should be TomRaider fans ... ( i kno it runs only on Win)

---

### Post by kevdog on 2008-03-09
Flash the router firmware for a solution?  I probably would have never thought of that!! I wonder what the problem really was??  I guess we will never know.  Good investigations and glad you got it working.

---

### Post by pk_rulz on 2008-03-10
Hi

Just thought of this 1 ... mat be it was not a simple firmware upgrade. Firmware upgrade requires me to reset the router to its factory settings before proceeding. May be there was some settting that was not allowing Linux to connect ... As u said now we will never know...

Well by the way yesterday nite I flashed it to DD - WRT n have not tested it yet ...Lets C wats in store

---

