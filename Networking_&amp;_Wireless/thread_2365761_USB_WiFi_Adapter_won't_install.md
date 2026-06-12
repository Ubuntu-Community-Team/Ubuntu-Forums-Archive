---
title: "USB WiFi Adapter won't install"
date: 2017-07-10
forum: Networking &amp; Wireless
---

### Post by dcpifhq on 2017-07-10
So I **just** bought a WNP-UA300P-01 (A Gembird usb wifi adapter), and whilst I was in the market, I quickly googled "ua300p gembird", and on their page it said 

"With this fast high power Gembird USB WiFi adapter you will have faster Internet (up to 300 Mbps) and much better reception in just two simple steps. Just plug it in and connect to your local WiFi network. It’s that simple."

Then I thought, ok, this is a plug-and-play usb wifi adapter, just what I need!

Then when I connected it with my Linux machine, the usb adapter BARELY caught up ANY connection. Every connection was on 1 line. After some keyboard smashing, I decided to calm down. And I started finding some drivers. I found this, from Gembird's official page: [http://gembird.nl/Repository/8711/WNP-UA300P-01_driver_83227E03-D4AF-47EE-9580-3C10ACBE3FDB.zip](http://gembird.nl/Repository/8711/WNP-UA300P-01_driver_83227E03-D4AF-47EE-9580-3C10ACBE3FDB.zip)
But the problem was that a bunch of errors came up, like "Compile make drive error: 127", after about an hour I solved that, but NOW I'm stuck on "Compile make drive error: 2" Here's some code if needed:

```
    /home/lamedabe/Desktop/v4.3.1.1_11320.20140505/driver/rtl8192EU_linux_v4.3.1.1_11320.20140505/core/rtw_debug.c:1221:2: note: in expansion of macro ‘DBG_871X_SEL_NL’
      DBG_871X_SEL_NL(m, "best_channel_24G = %d\n", best_channel_24G);
      ^~~~~~~~~~~~~~~
    cc1: some warnings being treated as errors
    scripts/Makefile.build:294: recipe for target '/home/lamedabe/Desktop/v4.3.1.1_11320.20140505/driver/rtl8192EU_linux_v4.3.1.1_11320.20140505/core/rtw_debug.o' failed
    make[2]: *** [/home/lamedabe/Desktop/v4.3.1.1_11320.20140505/driver/rtl8192EU_linux_v4.3.1.1_11320.20140505/core/rtw_debug.o] Error 1
    Makefile:1524: recipe for target '_module_/home/lamedabe/Desktop/v4.3.1.1_11320.20140505/driver/rtl8192EU_linux_v4.3.1.1_11320.20140505' failed
    make[1]: *** [_module_/home/lamedabe/Desktop/v4.3.1.1_11320.20140505/driver/rtl8192EU_linux_v4.3.1.1_11320.20140505] Error 2
    make[1]: Leaving directory '/usr/src/linux-headers-4.10.0-26-generic'
    Makefile:1323: recipe for target 'modules' failed
    make: *** [modules] Error 2
    ##################################################
    Compile make driver error: 2
    Please check error Mesg
    ##################################################

```
This is copied from where the error started and finished.

So, while I was doing some research about this error, I found that I need some build-essentials, git and linux-headers-generic, and I already have those installed. And some websites said that I need to install some stuff from github (half of them were dead links), and even from ubuntuforums, it said that I need to see the solution from some Spanish website...

And I found nothing (I even installed different drivers lol).

So, my problem here is that I **have** internet but it is EXTREMELY low (My integrated wifi card has better internet connection from the one I bought), and I know for a FACT that my problem is a driver issue. So can someone please help me.

**Any** kind of answer would be **EXTREMELY** appreciated!

---

### Post by johndough2 on 2017-07-10
Hi

It only has W10 drivers, therefore _ndiswrapper_ may help.

[https://www.linuxquestions.org/questions/linux-newbie-8/wifi-adapter-driver-install-wnp-ua300p-4175607393/](https://www.linuxquestions.org/questions/linux-newbie-8/wifi-adapter-driver-install-wnp-ua300p-4175607393/) has some details on 

Chipset: RTL8192EU

[http://users.telenet.be/x86_64/Debian/dkms_rtl8192eu_4.3.1.1.11320.20140505_all.deb1.0k](http://users.telenet.be/x86_64/Debian/dkms_rtl8192eu_4.3.1.1.11320.20140505_all.deb1.0k)

---

### Post by chili555 on 2017-07-10
> **johndough2 said:**
> Hi

It only has W10 drivers, therefore _ndiswrapper_ may help.

[https://www.linuxquestions.org/questions/linux-newbie-8/wifi-adapter-driver-install-wnp-ua300p-4175607393/](https://www.linuxquestions.org/questions/linux-newbie-8/wifi-adapter-driver-install-wnp-ua300p-4175607393/) has some details on 

Chipset: RTL8192EU

[http://users.telenet.be/x86_64/Debian/dkms_rtl8192eu_4.3.1.1.11320.20140505_all.deb1.0k](http://users.telenet.be/x86_64/Debian/dkms_rtl8192eu_4.3.1.1.11320.20140505_all.deb1.0k)ndiswrapper is almost never helpful. As well, ndiswrapper specifically requires Windows XP drivers. From *man ndiswrapper*:> ndiswrapper - Linux kernel module and user space tool to load and run Windows XP drivers for wireless cards
I have seen many attempts to use Windows 7, 8 and 10 drivers; none succeeded.

---

### Post by jeremy31 on 2017-07-10
Ivan
Please see the wireless script link in my signature and post results

---

### Post by chili555 on 2017-07-10
> 
But the problem was that a bunch of errors came up, like "Compile make drive error: 127", after about an hour I solved that, but NOW I'm stuck on "Compile make drive error: 2" Here's some code if needed:

Is it very doubtful that installing an older, circa 2014 driver will help. Please try this instead: ```
sudo gedit /etc/NetworkManager/NetworkManager.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Append the following, exactly as shown, at the end of the file, and save.

```
[device]
wifi.scan-rand-mac-address=no
```
Finally, restart Network Manager:

```
sudo service network-manager restart
```It may take a reboot.

Any improvement?

---

### Post by vocx on 2017-07-10
> **dcpifhq said:**
> So I **just** bought a WNP-UA300P-01 (A Gembird usb wifi adapter), and whilst I was in the market, I quickly googled "ua300p gembird", and on their page it said 

"With this fast high power Gembird USB WiFi adapter you will have faster Internet (up to 300 Mbps) and much better reception in just two simple steps. Just plug it in and connect to your local WiFi network. It&#8217;s that simple."

Then I thought, ok, this is a plug-and-play usb wifi adapter, just what I need!

Then when I connected it with my Linux machine, the usb adapter BARELY caught up ANY connection. Every connection was on 1 line. After some keyboard smashing, I decided to calm down. And I started finding some drivers. I found this, from Gembird's official page: [http://gembird.nl/Repository/8711/WNP-UA300P-01_driver_83227E03-D4AF-47EE-9580-3C10ACBE3FDB.zip](http://gembird.nl/Repository/8711/WNP-UA300P-01_driver_83227E03-D4AF-47EE-9580-3C10ACBE3FDB.zip)
But the problem was that a bunch of errors came up, like "Compile make drive error: 127", after about an hour I solved that, but NOW I'm stuck on "Compile make drive error: 2" Here's some code if needed:

First of all, the drivers in Linux distributions, like Ubuntu, are mostly found in the Linux kernel package. That is, the kernel already includes many drivers for many different network cards, video cards, ethernet cards, bluetooth cards, printers, etc. It is very rare that you need to go to the manufacturer's website to get the source code for the driver, and compile it yourself. If you do this, you will mostly run into problems, and you will end up more confused and frustrated. Compiling drivers from source should be left to people who really understand Linux, and know what they are doing. By the looks of it, you are still a new user, so you should avoid going this route, so you don't end up with many errors that you don't understand.

If you go to the project page of many open source projects, you will find the source code there. The source is meant for the package maintainers of distributions. The packages in Ubuntu use the Debian format and thus end in a ".deb" extension. The package maintainers have already put the work of compiling the driver for you, so you don't have to install things from source, only the deb package. You should install deb packages as much as you can.

> 
...
So, while I was doing some research about this error, I found that I need some build-essentials, git and linux-headers-generic, and I already have those installed. And some websites said that I need to install some stuff from github (half of them were dead links), and even from ubuntuforums, it said that I need to see the solution from some Spanish website...

And I found nothing (I even installed different drivers lol).

So, my problem here is that I **have** internet but it is EXTREMELY low (My integrated wifi card has better internet connection from the one I bought), and I know for a FACT that my problem is a driver issue. So can someone please help me.

**Any** kind of answer would be **EXTREMELY** appreciated!

If you are following any guides, tutorials, forum posts, or other sources, it is extremely useful to post a link to them, so we know what you have tried before, and we can point out errors or misconceptions you may be having about those instructions. If you are ill and go to a doctor that you don't normally visit, it is useful for him to take a look at your medical history or the prescription medications that you formerly took. That way he can get a better idea of what has worked or not for you in the past. It's the same way here in Linux. It's useful for us to know what you know, or what you have tried.

You should follow the instructions of the sticky thread [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

By the way, plug and play USB Wi-Fi dongles most definitely work in Linux, but it totally depends on the internal chipset that they have. Not every USB dongle is the same. So before saying "this says it's plug and play, I'll buy it", it's better if you first research online "Wi-Fi dongle that works in Linux", then you will see which ones have a supported chipset that just works, and which have a strange chipset that is basically unsupported. In particular, many off-brand, China-made, extremely cheap cards are basically intended for the low-end Windows market, so they don't bother with compatibility. They are released one time, with exactly one driver for Windows, and that's it. Many cards like this are hard to use in Linux, so in many cases just buying a new, supported USB dongle is easier than dealing with the problems of the cheaper device.

---

### Post by praseodym on 2017-07-10
Which chipset? Please show
```

lsusb
usb-devices
```

---

### Post by dcpifhq on 2017-07-11
> **jeremy31 said:**
> Ivan
Please see the wireless script link in my signature and post results

I already saw that post which you linked, even before I posted this thread. Thx dou

---

### Post by dcpifhq on 2017-07-11
> **vocx said:**
> First of all, the drivers in Linux distributions, like Ubuntu, are mostly found in the Linux kernel package. That is, the kernel already includes many drivers for many different network cards, video cards, ethernet cards, bluetooth cards, printers, etc. It is very rare that you need to go to the manufacturer's website to get the source code for the driver, and compile it yourself. If you do this, you will mostly run into problems, and you will end up more confused and frustrated. Compiling drivers from source should be left to people who really understand Linux, and know what they are doing. By the looks of it, you are still a new user, so you should avoid going this route, so you don't end up with many errors that you don't understand.

If you go to the project page of many open source projects, you will find the source code there. The source is meant for the package maintainers of distributions. The packages in Ubuntu use the Debian format and thus end in a ".deb" extension. The package maintainers have already put the work of compiling the driver for you, so you don't have to install things from source, only the deb package. You should install deb packages as much as you can.



If you are following any guides, tutorials, forum posts, or other sources, it is extremely useful to post a link to them, so we know what you have tried before, and we can point out errors or misconceptions you may be having about those instructions. If you are ill and go to a doctor that you don't normally visit, it is useful for him to take a look at your medical history or the prescription medications that you formerly took. That way he can get a better idea of what has worked or not for you in the past. It's the same way here in Linux. It's useful for us to know what you know, or what you have tried.

You should follow the instructions of the sticky thread [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

By the way, plug and play USB Wi-Fi dongles most definitely work in Linux, but it totally depends on the internal chipset that they have. Not every USB dongle is the same. So before saying "this says it's plug and play, I'll buy it", it's better if you first research online "Wi-Fi dongle that works in Linux", then you will see which ones have a supported chipset that just works, and which have a strange chipset that is basically unsupported. In particular, many off-brand, China-made, extremely cheap cards are basically intended for the low-end Windows market, so they don't bother with compatibility. They are released one time, with exactly one driver for Windows, and that's it. Many cards like this are hard to use in Linux, so in many cases just buying a new, supported USB dongle is easier than dealing with the problems of the cheaper device.

Hi, I appreciate the time you took off your day to tell me all of this, i really do, but in the package which they gave me the usb dongle, there was also a CD, which did **not **contain any deb file, if there was one, I would obviously run that instead of running all this in the terminal. There is only some files called: android,android,android (5 of them),and no this isn't the folder for Android only, because the folder which all these other folders come from is called "linux", anyway there is a folder called documents, a folder called driver, mp_tools, WiFi_Direct_User_Interface, wireless_tools, wpa_suppliciant_hostapd, **install.sh** (which i have problems with), readme.txt (I opened the readme file and it only contained some instructions manual, and no there wasn't "necessary files" line or anything like that), and Releasenotes.pdf .
So yeah, nothing useful in the folders, except the file that I'm supposed to execute, but doesn't work.

---

### Post by dcpifhq on 2017-07-11
> **praseodym said:**
> Which chipset? Please show
```

lsusb
usb-devices
```

```
:~ $ lsusb

Bus 001 Device 053: ID 04b4:0033 Cypress Semiconductor Corp. Mouse
Bus 001 Device 054: ID 04d9:2519 Holtek Semiconductor, Inc. 
Bus 001 Device 055: ID 0bda:818b Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0424:ec00 Standard Microsystems Corp. SMSC9512/9514 Fast Ethernet Adapter
Bus 001 Device 002: ID 0424:9514 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


:~ $ usb-devices


T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 1
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.09
S:  Manufacturer=Linux 4.9.26v7-aufs dwc_otg_hcd
S:  Product=DWC OTG Controller
S:  SerialNumber=3f980000.usb
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 5
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=02 MxPS=64 #Cfgs=  1
P:  Vendor=0424 ProdID=9514 Rev=02.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=2mA
I:  If#= 0 Alt= 1 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=02 Driver=hub


T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0424 ProdID=ec00 Rev=02.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=ff Driver=smsc95xx


T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=02 Dev#= 55 Spd=480 MxCh= 0
D:  Ver= 2.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=818b Rev=02.00
S:  Manufacturer=Realtek
S:  Product=802.11n NIC
S:  SerialNumber=00e04c000001
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 5 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)


T:  Bus=01 Lev=02 Prnt=02 Port=03 Cnt=03 Dev#= 54 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=04d9 ProdID=2519 Rev=01.00
S:  Product=2.4G Wireless Touchpad Keyboard
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid


T:  Bus=01 Lev=02 Prnt=02 Port=04 Cnt=04 Dev#= 53 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=04b4 ProdID=0033 Rev=01.00
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid


:~ $ 
```

Here's what I got.

---

### Post by jeremy31 on 2017-07-11
There is source code on github that should work
```
sudo apt-get install git dkms build-essential
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
sudo dkms add ./rtl8192eu-linux-driver
sudo dkms build -m rtl8192eu -v 1.0
sudo dkms install -m rtl8192eu -v 1.0
```

Reboot

---

### Post by dcpifhq on 2017-07-11
> **chili555 said:**
> Is it very doubtful that installing an older, circa 2014 driver will help. Please try this instead: ```
sudo gedit /etc/NetworkManager/NetworkManager.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Append the following, exactly as shown, at the end of the file, and save.

```
[device]
wifi.scan-rand-mac-address=no
```
Finally, restart Network Manager:

```
sudo service network-manager restart
```It may take a reboot.

Any improvement?

Did everything you said and it didn't work...

---

### Post by chili555 on 2017-07-11
> **dcpifhq said:**
> Did everything you said and it didn't work...Meaning what? Meaning that this behavior persists?> Then when I connected it with my Linux machine, the usb adapter BARELY caught up ANY connection. Every connection was on 1 line. Or that it doesn't even scan and see networks? Or that it....what?

---

### Post by dcpifhq on 2017-07-11
> **chili555 said:**
> Meaning what? Meaning that this behavior persists?Or that it doesn't even scan and see networks? Or that it....what?

Oh, sorry for being unclear,  the problem is still here-low connection

---

### Post by chili555 on 2017-07-11
> **dcpifhq said:**
> Oh, sorry for being unclear,  the problem is still here-low connectionI recommend then, that your next step be Jeremy's proposal at post #11 above.

---

### Post by dcpifhq on 2017-07-11
> **jeremy31 said:**
> There is source code on github that should work
```
sudo apt-get install git dkms build-essential
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
sudo dkms add ./rtl8192eu-linux-driver
sudo dkms build -m rtl8192eu -v 1.0
sudo dkms install -m rtl8192eu -v 1.0
```

Reboot

Didn't work.
I tried doing these steps and it didn't work, the wifi strength didn't increase. Nothing improved.

F.Y.I. I even followed the steps on my raspberry pi 3, and it still didn't work (although my original intention was to put this dongle my raspberry pi)

---

### Post by vocx on 2017-07-11
> **dcpifhq said:**
> Hi, I appreciate the time you took off your day to tell me all of this, i really do, but in the package which they gave me the usb dongle, **there was also a CD, which did not contain any deb file,** if there was one, I would obviously run that instead of running all this in the terminal. There is only some files called: android,android,android (5 of them),and no this isn't the folder for Android only, because the folder which all these **other folders come from is called "linux", anyway there is a folder called documents, a folder called driver,** mp_tools, WiFi_Direct_User_Interface, wireless_tools, wpa_suppliciant_hostapd, **install.sh** (which i have problems with), readme.txt (I opened the readme file and it only contained some instructions manual, and no there wasn't "necessary files" line or anything like that), and Releasenotes.pdf .
So yeah, nothing useful in the folders, **except the file that I'm supposed to execute,** but doesn't work.

You are not supposed to execute the files. Installation CDs sometimes contain "drivers" and files for "Linux". As I said before, these files are relatively useless for the regular end user. You will probably not be able to make it work by compiling the driver yourself. The proper way to get it to work is to search online for the appropriate solution, until you get good information, as in post #11.

Basically, I want to discourage you from trying to install drivers and kernel modules from source if you don't really know what you are doing, because you will end up with compilation errors and confused. What you are doing right now, asking for help in the forum, is better than just trying to install files from the CD or the manufacturer's website.

---

### Post by chili555 on 2017-07-11
> **dcpifhq said:**
> Didn't work.
I tried doing these steps and it didn't work, the wifi strength didn't increase. Nothing improved.

F.Y.I. I even followed the steps on my raspberry pi 3, and it still didn't work (although my original intention was to put this dongle my raspberry pi)May we see:```
iwconfig
dmesg | grep rtl
lsmod
```

---

### Post by vocx on 2017-07-11
> **dcpifhq said:**
> Didn't work.
I tried doing these steps and it didn't work, the wifi strength didn't increase. Nothing improved.

F.Y.I. I even followed the steps on my raspberry pi 3, and it still didn't work (although my original intention was to put this dongle my raspberry pi)
If your primary intention is to use a USB dongle on a Raspberry Pi, you should search online for compatible devices before buying.

Look at these lists, for example
[http://elinux.org/RPi_USB_Wi-Fi_Adapters](http://elinux.org/RPi_USB_Wi-Fi_Adapters)
[http://www.wirelesshack.org/top-10-wifi-dongles-for-the-raspberry-pi-2016.html](http://www.wirelesshack.org/top-10-wifi-dongles-for-the-raspberry-pi-2016.html)

The Raspberry Pi 3 in particular already has a Wi-Fi capable chipset. It uses the BCM43438 chipset for both Wi-Fi and Bluetooth. So, if you only need to access one wireless network, this is enough. The Raspbian 8.0 (Jessie) image already has the drivers for it, and it just works, and you don't need an additional USB dongle. The previous versions of Raspberry Pi, 1 and 2, didn't have an integrated Wi-Fi chipset. The Raspberry Pi 3 came out in February 2016, and since then it is unnecessary to get a USB dongle. You only need an extra Wi-Fi dongle if you want to turn your Raspberry into a router or firewall, because you need one device to accept data, and another to transmit data.

---

### Post by dcpifhq on 2017-07-11
> **chili555 said:**
> May we see:```
iwconfig
dmesg | grep rtl
lsmod
```

Sure.

iwconfig (on the raspberry pi):
```
wlan0     IEEE 802.11  ESSID:"SomeName"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 90:1D:27:D4:80:2B   
          Bit Rate=13 Mb/s   Tx-Power=31 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=37/70  Signal level=-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:43  Invalid misc:0   Missed beacon:0


eth0      no wireless extensions.


lo        no wireless extensions.


```

For dmesg | grep rtl, idk if it's supposed to say something but for me it didn't say anything...

For lsmod (raspberry pi):
```
Module                  Size  Used by
ctr                     3928  0 
ccm                     8218  0 
bnep                   10438  2 
hci_uart               18312  1 
btbcm                   6228  1 hci_uart
bluetooth             331535  22 hci_uart,bnep,btbcm
i2c_dev                 5892  0 
fuse                   85666  3 
ipv6                  348261  60 
arc4                    1923  0 
ath9k_htc              56861  0 
ath9k_common           22996  1 ath9k_htc
ath9k_hw              416817  2 ath9k_htc,ath9k_common
ath                    18574  3 ath9k_htc,ath9k_hw,ath9k_common
brcmfmac              196602  0 
mac80211              568932  1 ath9k_htc
brcmutil                5788  1 brcmfmac
snd_bcm2835            20685  1 
cfg80211              456420  5 ath9k_htc,mac80211,ath,brcmfmac,ath9k_common
joydev                  9194  0 
snd_pcm                76943  1 snd_bcm2835
rfkill                 14922  4 bluetooth,cfg80211
snd_timer              19223  1 snd_pcm
snd                    52742  5 snd_timer,snd_bcm2835,snd_pcm
bcm2835_gpiomem         3257  0 
uio_pdrv_genirq         3351  0 
uio                     8151  1 uio_pdrv_genirq
fixed                   2862  0
```

iwconfig (regular pc which has linux on it of course ):
```
wlan1     IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11  ESSID:"WLAN_D4802B"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 90:1D:27:D4:80:2B   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=29/70  Signal level=-81 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:24  Invalid misc:599   Missed beacon:0
```

For dmesg | grep rtl (regular pc which has linux on it of course):
```
[  533.594675] usb 2-5: rtl8192eu_parse_efuse: dumping efuse (0x200 bytes):
[  533.595160] usb 2-5: rtl8xxxu: Loading firmware rtlwifi/rtl8192eu_nic.bin
[  533.637894] usb 2-5: firmware: direct-loading firmware rtlwifi/rtl8192eu_nic.bin
[  534.577262] usb 2-5: rtl8192eu_rx_iqk_path_a: Path A RX IQK failed!
[  534.609510] usb 2-5: rtl8192eu_rx_iqk_path_a: Path A RX IQK failed!
[  534.698382] usb 2-5: rtl8192eu_rx_iqk_path_a: Path A RX IQK failed!
[  534.730664] usb 2-5: rtl8192eu_rx_iqk_path_a: Path A RX IQK failed!
[  534.785334] usbcore: registered new interface driver rtl8xxxu
```

For lsmod (regular pc which has linux on it of course):
```
Module                  Size  Used by
rtl8xxxu               98304  0
hid_generic            16384  0
usbhid                 45056  0
hid                    94208  2 hid_generic,usbhid
ctr                    16384  4
ccm                    20480  2
binfmt_misc            20480  1
iTCO_wdt               16384  0
iTCO_vendor_support    16384  1 iTCO_wdt
arc4                   16384  4
uvcvideo               77824  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         20480  1 uvcvideo
ath5k                 135168  0
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
ath                    24576  1 ath5k
videodev              131072  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  28672  2 uvcvideo,videodev
mac80211              548864  2 ath5k,rtl8xxxu
i915                 1163264  3
lpc_ich                20480  0
evdev                  20480  15
coretemp               16384  0
mfd_core               16384  1 lpc_ich
joydev                 20480  0
eeepc_laptop           20480  0
serio_raw              16384  0
cfg80211              450560  3 mac80211,ath,ath5k
pcspkr                 16384  0
drm_kms_helper        114688  1 i915
sg                     32768  0
sparse_keymap          16384  1 eeepc_laptop
rng_core               16384  0
drm                   253952  5 i915,drm_kms_helper
i2c_algo_bit           16384  1 i915
snd_hda_codec_realtek    65536  1
snd_hda_codec_generic    65536  1 snd_hda_codec_realtek
rfkill                 20480  5 eeepc_laptop,cfg80211
snd_hda_intel          28672  3
snd_hda_codec          94208  3 snd_hda_intel,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           57344  4 snd_hda_intel,snd_hda_codec,snd_hda_codec_generic,snd_hda_codec_realtek
video                  36864  2 eeepc_laptop,i915
ac                     16384  0
battery                20480  0
snd_hwdep              16384  1 snd_hda_codec
snd_pcm                86016  3 snd_hda_intel,snd_hda_codec,snd_hda_core
snd_timer              28672  1 snd_pcm
button                 16384  1 i915
shpchp                 32768  0
snd                    57344  13 snd_hda_intel,snd_hwdep,snd_hda_codec,snd_timer,snd_hda_codec_generic,snd_hda_codec_realtek,snd_pcm
soundcore              16384  1 snd
acpi_cpufreq           20480  0
ip_tables              20480  0
x_tables               20480  1 ip_tables
autofs4                36864  2
ext4                  499712  2
crc16                  16384  1 ext4
jbd2                   77824  1 ext4
crc32c_generic         16384  0
fscrypto               24576  1 ext4
ecb                    16384  0
xts                    16384  0
lrw                    16384  0
gf128mul               20480  2 lrw,xts
ablk_helper            16384  0
cryptd                 20480  1 ablk_helper
aes_i586               20480  4
mbcache                16384  3 ext4
sd_mod                 40960  4
ata_generic            16384  0
psmouse               118784  0
ata_piix               32768  3
libata                192512  2 ata_piix,ata_generic
scsi_mod              180224  3 sd_mod,libata,sg
ehci_pci               16384  0
uhci_hcd               40960  0
ehci_hcd               65536  1 ehci_pci
usbcore               184320  6 uvcvideo,usbhid,ehci_hcd,uhci_hcd,rtl8xxxu,ehci_pci
atl1e                  32768  0
usb_common             16384  1 usbcore
thermal                20480  0
```

Omg, I just realized the pi doesn't even detect my dongle... wth

Just as vocx said though, I'm searching for drivers that aren't from source.

---

### Post by dcpifhq on 2017-07-11
> **vocx said:**
> If your primary intention is to use a USB dongle on a Raspberry Pi, you should search online for compatible devices before buying.

Look at these lists, for example
[http://elinux.org/RPi_USB_Wi-Fi_Adapters](http://elinux.org/RPi_USB_Wi-Fi_Adapters)
[http://www.wirelesshack.org/top-10-wifi-dongles-for-the-raspberry-pi-2016.html](http://www.wirelesshack.org/top-10-wifi-dongles-for-the-raspberry-pi-2016.html)

The Raspberry Pi 3 in particular already has a Wi-Fi capable chipset. It uses the BCM43438 chipset for both Wi-Fi and Bluetooth. So, if you only need to access one wireless network, this is enough. The Raspbian 8.0 (Jessie) image already has the drivers for it, and it just works, and you don't need an additional USB dongle. The previous versions of Raspberry Pi, 1 and 2, didn't have an integrated Wi-Fi chipset. The Raspberry Pi 3 came out in February 2016, and since then it is unnecessary to get a USB dongle. You only need an extra Wi-Fi dongle if you want to turn your Raspberry into a router or firewall, because you need one device to accept data, and another to transmit data.

Yes! Exactly! I need the drivers for a router! Or, at least, that's the idea.

---

### Post by vocx on 2017-07-11
> **dcpifhq said:**
> ...
Omg, I just realized the pi doesn't even detect my dongle... wth

Just as vocx said though, I'm searching for drivers that aren't from source.
The issue is not that the drivers "come from source" or not. They obviously come from somewhere. The problem is whether the device works at all in Linux. Even if there is a deb package for the driver, if it does not work, well, it does not work, and that's it.

> **dcpifhq said:**
> Yes! Exactly! I need the drivers for a router! Or, at least, that's the idea.

Personally, I would forget about the current USB dongle that you have, and just get a new one that is well supported in Linux.

It seems there is one official Raspberry Pi Wi-Fi adapter using the BCM43143 chipset which would work out of the box.
[https://www.pi-supply.com/product/official-raspberry-pi-wifi-dongle-adapter/](https://www.pi-supply.com/product/official-raspberry-pi-wifi-dongle-adapter/)

USB dongles are generally cheap, so you don't waste much money buying a new one. But I still suggest you to look online and read reviews before buying.

Or just continue trying to make it work. You say, your device works, only that the signal is not strong enough. Maybe this is not a problem with the USB dongle but with your router. In this case, check your router, increase the signal strength, or change the router, or add a signal repeater somewhere around where you want to have a strong Wi-Fi signal. There are various things to try that don't exactly relate to Ubuntu or the Raspberry Pi.

---

### Post by dcpifhq on 2017-07-11
> **vocx said:**
> The issue is not that the drivers "come from source" or not. They obviously come from somewhere. The problem is whether the device works at all in Linux. Even if there is a deb package for the driver, if it does not work, well, it does not work, and that's it.



Personally, I would forget about the current USB dongle that you have, and just get a new one that is well supported in Linux.

It seems there is one official Raspberry Pi Wi-Fi adapter using the BCM43143 chipset which would work out of the box.
[https://www.pi-supply.com/product/official-raspberry-pi-wifi-dongle-adapter/](https://www.pi-supply.com/product/official-raspberry-pi-wifi-dongle-adapter/)

USB dongles are generally cheap, so you don't waste much money buying a new one. But I still suggest you to look online and read reviews before buying.

Or just continue trying to make it work. You say, your device works, only that the signal is not strong enough. Maybe this is not a problem with the USB dongle but with your router. In this case, check your router, increase the signal strength, or change the router, or add a signal repeater somewhere around where you want to have a strong Wi-Fi signal. There are various things to try that don't exactly relate to Ubuntu or the Raspberry Pi.

Alright then, I'll buy a new one, since there is no hope for this dongle... Btw I know there isn't a problem with my router because other devices (Phones, laptops, TV etc.) are working fine,and they even get a bigger wifi range. But ok, I'll buy a new one.[B]


Thanks to everyone taking their time off to help me with this thread.[/B]

---

### Post by jeremy31 on 2017-07-11
It seems you have a USB wifi device that is supported by the kernel in the pi otherwise the ath9k-htc module wouldn't have loaded.  I suspect it might be a TP-Link WN722N like I have.  Is there a reason why you are not using the LTS Ubuntu 16.04 or 16.04.1 version as I know the instructions work perfect using Ubuntu 16.04 with kernel 4.4 on my laptop.

On the pi, plug the wifi adapter in and wait a couple minutes, then
```
dmesg | tail
```
See if there are any USB device disconnect messages

---

### Post by chili555 on 2017-07-11
Old Chili doesn't like this one bit:> wlan0     IEEE 802.11  ESSID:"WLAN_D4802B"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 90:1D:27:D4:80:2B   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          [COLOR="#FF0000"]Link Quality=29/70[/COLOR]  Signal level=-81 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:24  Invalid misc:599   Missed beacon:0
How far from the router or access point are you? 

For comparison, I am three rooms away from mine:> wlp3s0    IEEE 802.11  ESSID:"GBR5"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: xx:2B:B0:DC:45:xx
          Bit Rate=866.7 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          [COLOR="#FF0000"]Link Quality=62/70 [/COLOR] Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:690   Missed beacon:0


---

### Post by dcpifhq on 2017-07-12
> **chili555 said:**
> Old Chili doesn't like this one bit:How far from the router or access point are you? 

For comparison, I am three rooms away from mine:

I am...around 4 meters away from my router.
Basically:

_________________ ______________ _______________
|................................|.|..........................|.|........__................|
|...................|...|........|.|..........................|.|.......|__|..............|
|.router->[==].........|.|....Bathroom....|.|...... PC.............|
|................................|.|..........................|.|............................|
|................................|.|..........................|.|............................|
|________________| |_____________| |_____________ _|

---

### Post by dcpifhq on 2017-07-12
A little update guys, I switched the Gembird USB, and I put it into another PC, but that other PC had a Tenda U1 USB. And for this dongle I get the following when I ran "sudo make" on my PC:

```
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/4.10.0-26-generic/build M=/home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master  modules
make[1]: Entering directory '/usr/src/linux-headers-4.10.0-26-generic'
  CC [M]  /home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master/os_dep/linux/ioctl_linux.o
/home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master/os_dep/linux/ioctl_linux.c: In function &#8216;rtw_mp_read_reg&#8217;:
/home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master/os_dep/linux/ioctl_linux.c:11331:8: warning: this &#8216;if&#8217; clause does not guard... [-Wmisleading-indentation]
        if ( data[i] != '\0' )
        ^~
/home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master/os_dep/linux/ioctl_linux.c:11334:10: note: ...this statement, but the latter is misleadingly indented as if it is guarded by the &#8216;if&#8217;
          j++;
          ^
/home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master/os_dep/linux/ioctl_linux.c: In function &#8216;rtw_ioctl&#8217;:
/home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master/os_dep/linux/ioctl_linux.c:15736:11: error: implicit declaration of function &#8216;rtw_ioctl_wext_private&#8217; [-Werror=implicit-function-declaration]
     ret = rtw_ioctl_wext_private(dev, rq);
           ^~~~~~~~~~~~~~~~~~~~~~
cc1: some warnings being treated as errors
scripts/Makefile.build:294: recipe for target '/home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master/os_dep/linux/ioctl_linux.o' failed
make[2]: *** [/home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master/os_dep/linux/ioctl_linux.o] Error 1
Makefile:1524: recipe for target '_module_/home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master' failed
make[1]: *** [_module_/home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.10.0-26-generic'
Makefile:1685: recipe for target 'modules' failed
make: *** [modules] Error 2
lamedabe@lamedabe:~/Desktop/rtl8192eu-linux-driver-tenda-u1-master$ 
```

I'm currently not home so I'll update you what happened to the rpi when I'm back

---

### Post by vocx on 2017-07-12
> **dcpifhq said:**
> A little update guys, I switched the Gembird USB, and I put it into another PC, but that other PC had a Tenda U1 USB. And for this dongle I get the following when I ran "sudo make" on my PC:

```
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/4.10.0-26-generic/build M=/home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master  modules
make[1]: Entering directory '/usr/src/linux-headers-4.10.0-26-generic'
  CC [M]  /home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master/os_dep/linux/ioctl_linux.o
/home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master/os_dep/linux/ioctl_linux.c: In function &#8216;rtw_mp_read_reg&#8217;:
/home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master/os_dep/linux/ioctl_linux.c:11331:8: warning: this &#8216;if&#8217; clause does not guard... [-Wmisleading-indentation]
        if ( data[i] != '\0' )
        ^~
/home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master/os_dep/linux/ioctl_linux.c:11334:10: note: ...this statement, but the latter is misleadingly indented as if it is guarded by the &#8216;if&#8217;
          j++;
          ^
/home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master/os_dep/linux/ioctl_linux.c: In function &#8216;rtw_ioctl&#8217;:
/home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master/os_dep/linux/ioctl_linux.c:15736:11: error: implicit declaration of function &#8216;rtw_ioctl_wext_private&#8217; [-Werror=implicit-function-declaration]
     ret = rtw_ioctl_wext_private(dev, rq);
           ^~~~~~~~~~~~~~~~~~~~~~
cc1: some warnings being treated as errors
scripts/Makefile.build:294: recipe for target '/home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master/os_dep/linux/ioctl_linux.o' failed
make[2]: *** [/home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master/os_dep/linux/ioctl_linux.o] Error 1
Makefile:1524: recipe for target '_module_/home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master' failed
make[1]: *** [_module_/home/lamedabe/Desktop/rtl8192eu-linux-driver-tenda-u1-master] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.10.0-26-generic'
Makefile:1685: recipe for target 'modules' failed
make: *** [modules] Error 2
lamedabe@lamedabe:~/Desktop/rtl8192eu-linux-driver-tenda-u1-master$ 
```

I'm currently not home so I'll update you what happened to the rpi when I'm back
Please stop trying to compile!

---

### Post by jeremy31 on 2017-07-12
Post results for ```
modprobe -c | grep -i 818b
```

---

### Post by chili555 on 2017-07-12
Do you get very low signal strength with other devices; your internal wireless for example?

You get low signal on both your computer and the Pi. I wonder if the Gembird is defective.

---

### Post by dcpifhq on 2017-07-13
> **chili555 said:**
> Do you get very low signal strength with other devices; your internal wireless for example?

You get low signal on both your computer and the Pi. I wonder if the Gembird is defective.

I get low signal strength on my other wifi adapters that dont have drivers installed as well, but on other devices(laptop,tv, smartphone etc.) no, thr signal is fine

---

### Post by dcpifhq on 2017-07-13
> **jeremy31 said:**
> Post results for ```
modprobe -c | grep -i 818b
```

Here:

```
lamedabe@lamedabe:~$ modprobe -c | grep -i 818b
alias pci:v000010ECd0000818Bsv*sd*bc*sc*i* rtl8192ee
alias usb:v0BDAp818Bd*dc*dsc*dp*icFFiscFFipFFin* rtl8xxxu
alias usb:v0BDAp818Bd*dc*dsc*dp*icFFiscFFipFFin* 8192eu
alias usb:v10C4p818Bd*dc*dsc*dp*ic*isc*ip*in* cp210x
alias vmbus:31600b0e13523449818b38d90ced39db hv_utils
lamedabe@lamedabe:~$ 
```

BTW I have no idea why my linux is detecting 3 USBs.
Oh, and keep in mind that I changed my wifi adapter to the Tenda U1, but that doesn't make any difference cuz I have the same problem with both dongles

---

### Post by jeremy31 on 2017-07-13
Lets try ```
echo "blacklist rtl8xxxu" | sudo tee /etc/modprobe.d/rtl8xxxu.conf
```
Reboot
If the problem only exists with the Pi it could be a power issue as I think that most people use cell phone chargers as power supplies and having the internal wifi plus a USB device might be more than they can handle

The results for that command show drivers that are available for devices with 818b in their ID and only 2 of them are a perfect match for your device v0BDAp818Bd

---

### Post by alexpslab on 2017-11-30
> **vocx said:**
> If your primary intention is to use a USB dongle on a Raspberry Pi, you should search online for compatible devices before buying.

Look at these lists, for example
[http://elinux.org/RPi_USB_Wi-Fi_Adapters](http://elinux.org/RPi_USB_Wi-Fi_Adapters)
[https://scanraptor.com/kodi-iptv-stalker-addon/](https://scanraptor.com/kodi-iptv-stalker-addon/)

The Raspberry Pi 3 in particular already has a Wi-Fi capable chipset. It uses the BCM43438 chipset for both Wi-Fi and Bluetooth. So, if you only need to access one wireless network, this is enough. The Raspbian 8.0 (Jessie) image already has the drivers for it, and it just works, and you don't need an additional USB dongle. The previous versions of Raspberry Pi, 1 and 2, didn't have an integrated Wi-Fi chipset. The Raspberry Pi 3 came out in February 2016, and since then it is unnecessary to get a USB dongle. You only need an extra Wi-Fi dongle if you want to turn your Raspberry into a router or firewall, because you need one device to accept data, and another to transmit data.
Thanks mate for the tip.

---

