---
title: "Help with WLAN Card driver installation"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by mett demon on 2010-04-15
Hello everyone,
fairly new to ubuntu and absolutely love the look and feel. The only problem I have is that my new laptop comes with a realtek 8192xSE WLAN card. I have the correct drivers (methinks) [rtl8192se_linux_2.6.0015.0127.2010.tar.gz] but am struggling to do anything else now. Would really appreciate some step by step guides of how I go about installing this.
I am running 10.04 2.6.32-20-generic. Hardware is a Compaq 615, and when I lspci:
06:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8171 (rev 10)

Many thanks in advance     :confused:

---

### Post by anewguy on 2010-04-15
If you double-click on the file you downloaded, the system should unpack everything - it might even install it (I don't know - don't use it).  If you can point me to where you downloaded it, I can take a look inside it to see if you need to do anything special to install it.

dave ;)

---

### Post by anewguy on 2010-04-15
You may also want to see this link - even if not exactly the same the procedures will be.

[http://ubuntuforums.org/showthread.php?t=1425140]("http://ubuntuforums.org/showthread.php?t=1425140")

Dave ;)

---

### Post by mett demon on 2010-04-15
thank you very much for your replies. As I am still reading through everything now I will update once I have actually tried something. It is all a bit daunting..... but looks fun

---

### Post by anewguy on 2010-04-15
The first couple of times of seeing things like configure, make and make install can be more than a little daunting, but you soon find that most things are done via the package manager and those that are not usually follow this common format.

Good luck and let us know what happens!

Dave ;)

---

### Post by mett demon on 2010-04-16
Hi there, so I followed the thread (chili555)[QUOTE][/
cd directory/where/you/downloaded
sudo su
make clean
make
make install
modprobe r8192se_pci
exit[FONT=Verdana]][FONT=monospace]
[/FONT][/FONT]

---

### Post by mett demon on 2010-04-16
and this is the result;
benjamin@benjamin-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ sudo su
[sudo] password for benjamin: 
root@benjamin-laptop:/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010# make clean
make[1]: Entering directory `/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[2]: Entering directory `/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[2]: Leaving directory `/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s'
make[1]: Leaving directory `/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192'
make[1]: Entering directory `/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/rtllib'
rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
rm -rf .tmp_versions
rm -rf Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/rtllib'
root@benjamin-laptop:/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010# make
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-20-generic'
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_core.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_regd.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_rfkill.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_eeprom.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_wx.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_cam.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_pm.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_ps.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_dm.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_debug.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_ethtool.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_dev.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_Efuse.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_phy.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_firmware.o
/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_firmware.c: In function ‘FirmwareSetH2CCmd’:
/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_firmware.c:714: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_rtl6052.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_hwimg.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_led.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_mp.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_scan.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_rx.o
/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_rx.c: In function ‘rtllib_FlushRxTsPendingPkts’:
/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_rx.c:1122: warning: the frame size of 1056 bytes is larger than 1024 bytes
/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_rx.c: In function ‘RxReorderIndicatePacket’:
/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_rx.c:1303: warning: the frame size of 1072 bytes is larger than 1024 bytes
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_softmac.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_tx.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_wx.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_module.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_softmac_wx.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtl819x_HTProc.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtl819x_TSProc.o
/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtl819x_TSProc.c: In function ‘RxPktPendingTimeout’:
/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtl819x_TSProc.c:98: warning: the frame size of 1056 bytes is larger than 1024 bytes
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtl819x_BAProc.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/dot11d.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_crypt.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_crypt_tkip.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_crypt_ccmp.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_crypt_wep.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/wapi.o
  CC [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/wapi_interface.o
  LD [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/r8192se_pci.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/r8192se_pci.mod.o
  LD [M]  /home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/r8192se_pci.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-20-generic'
root@benjamin-laptop:/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010# make install
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-20-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-20-generic'
make[1]: Entering directory `/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192'
make -C /lib/modules/2.6.32-20-generic/build M=/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010 CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-20-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-20-generic'
install -p -m 644 r8192se_pci.ko /lib/modules/2.6.32-20-generic/kernel/drivers/net/wireless/
depmod -a
make[1]: Leaving directory `/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192'
root@benjamin-laptop:/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010# modprobe r8192se_pci
root@benjamin-laptop:/home/benjamin/Desktop/rtl8192se_linux_2.6.0015.0127.2010# exit
exit
benjamin@benjamin-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4357 (rev 10)
06:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8171 (rev 10)
benjamin@benjamin-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$

---

### Post by mett demon on 2010-04-16
I have restarted and since it will see my router but it won't connect.....
](*,)

---

### Post by anewguy on 2010-04-16
Okay, now we know the wireless is at least working with the driver now as you are able to see your router.

Connection problems can have many sources - two of the most common are:

- the router has some sort of encryption enabled

- the router has MAC filtering enabled

If you have WEP, WPA, etc., turned on in the router, you must enter the correct encryption type and the correct password/passphrase in order to connect to the router. 

If you have MAC filtering enabled, only the devices whose MAC addresses (*not* IP addresses) have been entered in the list in the router can connect.  You will either need to use another computer that has access to the router or temporarily hard-wire your PC to the router, then add the computers' MAC address to the list in the router.

The easiest way to start is to temporarily turn off encryption on the router so it is an "open" network.  After doing so, see if you can connect to the router - if so, you need to re-enable your encryption then be sure to specify the correct type and password/passphrase when connecting (remember everything is case sensitive, so Password doesn't match password, as an example).  It's also possible the driver doesn't support the encryption type you have specified - in which case I would start at WEP (easily cracked), be able to connect, then work my way up through the other encryption types.

I'm sure others have other things to try as well - these are just the 2 I have run into the most often.

Also be sure the SSID is being broadcast by the router (I assume yours is since you say you can see the router but just can't connect to it).  If the SSID is not being broadcast, you must go through network manager and manually add the connection.

Hope this helps in some small way.

Dave ;)

---

### Post by ancientrustic on 2010-05-06
This is a modified version I found on the net. It works with Lucid.

rtl driver install

cd sudo su


Took some time, but I figured out what needed to be done. Mind you, I don't know the short version of what needs to be actually done for this to work, but for reference here is what I did.

Laptop: Toshiba A505-S6980
OS: Ubuntu 9.10 32-bit Kernel 2.6.31-16
Wireless card included: Realtek 8191SE

1. Obtain the RTL8192SE Drivers (refer to post 15 of this thread) and extract the folder.
2. Either log in to the user "root" and open terminal or open terminal under user and enter root privileges by entering "sudo su".
3. Change directory to the downloaded folder.
4. Enter the commands for method 1 installation from the readme.txt file in the driver folder.
5. Follow the instructions for the method 2 installation from the readme.txt file in the driver folder.
6. Modify /etc/network/interfaces: "gedit /etc/network/interfaces" and add the following code:

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/dbus-1/system.d/wpa_supplicant.conf

7. Modify /etc/modules: "gedit /etc/modules" and add the following code:

r8192e_pci

8. Reboot

When I ran method 1 first, nothing happened. When I tried method 2, after running "./wlan0up" with root privileges, the wireless adapter worked with no issue, except it would not work until the ./wlan0up command was entered. Finally, after completing steps 6 and 7 (did not try one then the other, did both) following all the prior steps, Network Manager was able to function normally with out error.

Hope this helps others.

---

### Post by mett demon on 2010-07-17
after consigning myself to the fact that I would not be able to use wireless on this laptop, I ran throught this again:
cd directory/where/you/downloaded
sudo su
make clean
make
make install
modprobe r8192se_pci
exit[FONT=Verdana]]

as the klingons say, KAPPLAR!!
got wireless working beautifully, the only thing I had to do is to change was the security setting on my router..... 
luckily I have only old folks living around me otherwise they would be mooching off my connection as I had to change it to open
:D
[/FONT]

---

