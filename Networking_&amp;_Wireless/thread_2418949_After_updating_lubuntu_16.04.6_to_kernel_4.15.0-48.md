---
title: "After updating lubuntu 16.04.6 to kernel 4.15.0-48 3g modem is not detected properly"
date: 2019-05-14
forum: Networking &amp; Wireless
---

### Post by timomak on 2019-05-14
After updating lubuntu 16.04.6 to kernel 4.15.0-48 on a dell laptop, 3g usb modem zte k3565z model is detected as different zte model (mf627/628-636). This modem (k3565z)was working perfectly (out of the box) for years, until i updated kernel.
I tried boot with the previous kernel 4.15.0.43 but didn&#8217;t work either.

I used a friend&#8217;s lenovo laptop where the modem is detected properly with the correct qmi_wwan drivers attached. Comparison is as follows distinguished as dell - lenovo.:

 **Wrong on dell**

~lsusb 
Bus 002 Device 004: ID 19d2:2000 ZTE WCDMA Technologies MSM MF627/
MF628/MF628+/MF636+ HSDPA/HSUPA
~usb-devices
T:  Bus=02 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=2000 Rev=00.00
S:  Manufacturer=ZTE,Incorporated
S:  Product=ZTE CDMA Technologies MSM
S:  SerialNumber=P673A2VDF_MS
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none)

  
**Correct on lenovo**

~lsusb
Bus 002 Device 005: ID 19d2:0063 ZTE WCDMA Technologies MSM K3565-Z HSDPA

~usb-devices
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=0063 Rev=00.00
S:  Manufacturer=ZTE,Incorporated
S:  Product=ZTE CDMA Technologies MSM
C:  #Ifs= 6 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=qmi_wwan
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

May new kernel doesn&#8217;t support old usb modems?
What are the option i have here ? because i m a 3 years new user
Change the device name correctly and how? 
Remove last update to check if it works properly ?
Is using scanModem will help?

---

### Post by praseodym on 2019-05-14
```
 I: If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```
Is it mounted as hard drive? Right-click to unmount?!

Package "usb-modeswitch" is installed?

---

### Post by timomak on 2019-05-15
I: If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

The above code is correct functioning ok on lenovo
On dell see dell-wrong output at the beginning 
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none

it is not seen in disks/drives
usb mode-switch is installed

---

### Post by timomak on 2019-10-08
After long research i found that even when i downloaded a new lubuntu 16.4.06 iso, burned a dvd and tried live session, the problem remains with zte k 3565-z usb modem.

The same doesn’t happen with lubuntu 18.4.01 ..onwards , where specific usb modem works perfectly.
It seems that someone from lubuntu maintainers has tampered with the usb modeswitch conf file in this version 16.4.06
Apparently the feature StandatdEject=1/0 is missing from the usb_modeswitch log file so the modem never switch modes.
I don’t know how fix it but i may report a bug for this.

---

### Post by guiverc on 2019-10-12
fyi:  Lubuntu 16.04 LTS is a flavor of the main Ubuntu 16.04 LTS.  Whilst Ubuntu 16.04 LTS comes with 5 years of support (applying to packages found in the 'main' repository), flavors have packages found in 'universe' which come with only 3 years of support.  Lubuntu 16.04 LTS ([https://lubuntu.me/xenial-released/](https://lubuntu.me/xenial-released/)) is now EOL.

If you enter `ubuntu-support-status` on your actual box, you'll see what % of packages are still maintained (these will be Ubuntu packages supported by Canonical), and what % (such as all LXDE/Lubuntu flavor specific packages) are no longer supported or maintained.  I would suggest upgrading to a supported release of Lubuntu (18.04 LTS if you don't like release-upgrading every 6-9 months as required by non-LTS releases).

---

### Post by timomak on 2019-10-13
> **guiverc said:**
> fyi:  Lubuntu 16.04 LTS is a flavor of the main Ubuntu 16.04 LTS.  Whilst Ubuntu 16.04 LTS comes with 5 years of support (applying to packages found in the 'main' repository), flavors have packages found in 'universe' which come with only 3 years of support.  Lubuntu 16.04 LTS ([https://lubuntu.me/xenial-released/](https://lubuntu.me/xenial-released/)) is now EOL.

If you enter `ubuntu-support-status` on your actual box, you'll see what % of packages are still maintained (these will be Ubuntu packages supported by Canonical), and what % (such as all LXDE/Lubuntu flavor specific packages) are no longer supported or maintained.  I would suggest upgrading to a supported release of Lubuntu (18.04 LTS if you don't like release-upgrading every 6-9 months as required by non-LTS releases).


Thank  you very much for your answer.

---

