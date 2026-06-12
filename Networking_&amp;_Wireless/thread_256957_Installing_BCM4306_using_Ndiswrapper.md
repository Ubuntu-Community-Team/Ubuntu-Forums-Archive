---
title: "Installing BCM4306 using Ndiswrapper"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by sp0nge on 2006-09-13
I'm following a how to which gives me the following:
#

Retrieve the Windows driver corresponding to your chipset. Use the information you have just found and the ndiswrapper [WWW] list to find and download the correct files for your card, or one which is very similar.
#

Unpack the Windows driver by using the unzip, cabextract and/or unshield tools (run from the Terminal), and find the INF file (.INF or .inf extension) and the SYS file (.SYS or .sys extension). You may first need to install cabextract and unshield.

I've downloaded the driver suggested on this list which is a.EXE-There is nothing to unpack and I can not locate any .INF or .SYS files. What am I missing here?

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by jcrnan on 2006-09-13
find your correct driver here: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

note that there are several types depending on your pc. (in worst case jut try several)

and here is good instructions on how to install the driver:
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

I struggled with this myself recently.

---

### Post by sp0nge on 2006-09-13
Well I'm not exactly sure what I did differently this time but Po0f, it works! Finally, I'm wireless.. now if I could just get java and flash to work properly....

\\:D/

---

### Post by wakaimono on 2006-09-14
java is tricky because there is a typo in the instructions. Read the file info carefully and compare it to the instrucitons. If I do recall it is missing an "_05"

---

### Post by trubblemaker on 2006-09-14
if you still have windows running on the box then you can use it to find out what device that you are running, go into network connections, right click on properties, click on Advanced, and then on drvier and it will tell you the type of driver, then if you look here:
```

AppleAirPort2
-------------
You can find the Apple Airport Extreme driver in your Mac OS X system at
/System/Library/Extensions/AppleAirPort2.kext/Contents/MacOS/AppleAirPort2
(Note that not all versions of the MacOSX driver are supported.)

AppleAirPortBrcm4311
--------------------
AppleAirPortBrcm4311 only seems to be available on Intel based machines.
System/Library/Extensions/IO80211Family.kext/Contents/PlugIns/AppleAirPortBrcm4311.kext/Contents/MacOS/AppleAirPortBrcm4311

bcmwl5.sys      Link
-------------   -------------------------------------------------------
3.20.23.0       http://nicolas.bonifas.free.fr/inspiron/bcmwl5.sys
                http://www.fujitsupc.com/downloads/Wireless_Broadcom_802.11g_WPA_V3.20.23.0_XP_2K.exe
                http://files.codykrieger.com/mn720drivers/bcmwl5.sys
3.30.15.0       ftp://ftp.asus.com.tw/pub/ASUS/wireless/WL-100g-03/Driver_330150.zip
                http://web.belkin.com/support/download/files/F5D7010-v2.4.4.exe
                http://www.belkin.com/support/download/downloaddetails.asp?file_id=1425
                http://communications.siemens.com/repository/1135/113557/pccard54_V11200_eng.exe
3.30.15.1       http://www.buffalo-technology.com/downloads/CBG54_30_15.zip
3.40.20.0       http://broadband.motorola.com/consumers/products/WN825g/downloads/WN-WPCI-Web-Update-v1.1.exe
                http://broadband.motorola.com/consumers/products/WPCI810g/downloads/WN-WPCI-Web-Update-v1.1.exe
3.40.25.3       http://www.silfreed.net/download/hpzt3000cto/SP23107A.tar.gz
3.40.65.0       http://ftp.us.dell.com/network/R74091jp.EXE
3.40.69.0       http://metahusky.net/~gavin/home/bcmwl5.sys
3.40.73.0       http://ftp.us.dell.com/network/R83097.EXE
                ftp://ftp.us.dell.com/network/R83097.EXE
3.40.100.0      ftp://ftp.wildpackets.com/pub/outgoing/brcmDvr340rc100a~@.zip
3.50.21.10      http://www.buffalo-technology.com/downloads/CBG54_3.50.21.10_Driver_rev.zip
3.60.7.0        ftp://ftp.asus.com.tw/pub/ASUS/wireless/WL-100g-03/Driver_3607.zip
3.60.7.5        http://www2.melcoinc.co.jp/pub/lan/wdrv_660.exe
3.70.12.0       http://files.wl500g.info/asus/wl120g/drivers/3.70.12.0.rar
                ftp://ftp.compaq.com/pub/softpaq/sp28001-28500/sp28198.exe
3.70.17.0       ftp://ftp.compaq.com/pub/softpaq/sp28501-29000/SP28538.exe
3.90.16.0       http://www.usr.com/support/5421/5421-files/5421-na.exe
3.90.41.1       http://www2.melcoinc.co.jp/pub/lan/wdrv_661.exe
3.94.41.1       http://www.buffalo-technology.com/downloads/WLI2-PCI-G54S.zip
                http://www.buffalo-technology.com/downloads/WLI-CB-G54S.3.104.64.50.zip
3.94.41.2       http://www2.melcoinc.co.jp/pub/lan/wdrv_810.exe
3.100.35.1      http://ftp.us.dell.com/network/R94826.EXE
3.100.46.0      ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip
                http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=application%2Fx-msdownload&blobheadervalue2=inline%3B+filename%3DWMP54GSv1.1_20050428.exe&blobkey=id&blobtable=MungoBlobs&blobwhere=1124848568427&ssbinary=true
                ftp://ftp.compaq.com/pub/softpaq/sp29501-30000/SP29845.exe
3.100.64.0      ftp://ftp.compaq.com/pub/softpaq/sp30501-31000/SP30676.exe
3.100.64.50     http://www2.melcoinc.co.jp/pub/lan/wdrv_661.exe
3.100.65.1      ftp://ftp.hp.com/pub/softlib/software5/COL3601/ob-31557-1/SP30379.exe
3.104.64.50     http://www.buffalo-technology.com/downloads/WLI2-PCI-G54S.zip
                http://www.buffalo-technology.com/downloads/WLI-CB-G54S.3.104.64.50.zip
3.104.64.52     http://www2.melcoinc.co.jp/pub/lan/wdrv_810.exe
3.120.27.0      ftp://ftp.us.dell.com/network/R102318.EXE
3.140.16.0      http://files.techlabs.by/getfile.php?id=1844
4.10.40.0       http://rapidshare.de/files/11458737/Broadcom_4.10.40.0_Drivers.cab.html
4.10.40.1       http://images.lunarpages.com/12002219.cab

bcmwl564.sys    Link
-------------   -------------------------------------------------------
3.70.17.5       http://ubuntuforums.org/attachment.php?attachmentid=186
3.100.64.0      ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/winxp64bit/80211g.zip

bcmwl5a.sys     Link
-------------   -------------------------------------------------------
3.90.16.0       http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=application%2Fx-msdownload&blobheadervalue2=inline%3B+filename%3DWMP54GSv1.1_20050428.exe&blobkey=id&blobtable=MungoBlobs&blobwhere=1124848568427&ssbinary=true

d11ucode.o      Link
-------------   -------------------------------------------------------
3.50.21.10      ftp://ftp.gpl-devices.org/pub/vendors/Motorola/WE800G/v4.04/WE800G_V4.04_GPL.tgz
3.60.7.0        http://files.wl500g.info/asus/wl500g/gpl/broadcom/src/wl/linux/ap_d11ucode.o
3.60.13.0       http://arch.crans.org/bernat@luffy.cx--2005-public/wrt54g--crans--0--base-0/wl/linux/sta_d11ucode.o?download
3.90.7.0        http://dune.hu/gpl_tarballs/asus/broadcom/src/wl.orig/linux/ap_d11ucode.o

wl.o            Link
-------------   -------------------------------------------------------
3.50.21.0       http://nthill.free.fr/openwrt/sources/wl/wl-2.02.7.tar.bz2
3.50.21.10      ftp://ftp.gpl-devices.org/pub/vendors/Motorola/WE800G/v4.04/WE800G_V4.04_GPL.tgz
3.60.13.0       http://nthill.free.fr/openwrt/sources/wl/wl-2.09.1.tar.bz2
                http://nthill.free.fr/openwrt/sources/wl/wl-3.37.6.tar.bz2
                http://arch.crans.org/bernat@luffy.cx--2005-public/wrt54g--crans--0--base-0/wl/linux/wl.o?download
3.90.37.0       http://openwrt.inf.fh-brs.de/~nbd/wl1.o

wl_apsta.o      Link
-------------   -------------------------------------------------------
3.31.16.0       http://puma.ttc.cz/~jaha2x/openwrt/modules/drivers/net/wl/wl_apsta/wl_apsta.o
                http://jak.kvalitne.cz/pub/puma.habrova.jarov.czf/~jaha2x/wl500/wl_apsta.o
3.130.20.0      http://openwrt.inf.fh-brs.de/~nbd/wl_apsta.o

```
you can find your driver hope this helps

---

