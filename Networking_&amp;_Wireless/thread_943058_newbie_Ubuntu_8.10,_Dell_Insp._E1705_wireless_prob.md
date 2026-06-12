---
title: "newbie: Ubuntu 8.10, Dell Insp. E1705 wireless problem"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by chromejs10 on 2008-10-09
I just installed Ubuntu 8.10 onto my Dell Inspiron E1705 computer and can't connect to wireless. i typed lshw -C network and no Wireless interface comes up. Only thing that did come up is the Network controller. the driver is: driver=b43-pci-bridge

I click the little 2 overlapping computer icon in the menu bar but nothing comes up about wireless.

I have gone into the package manager and activated that broadcom driver as well.

How do I get wireless to work?? I've googled to no avail for hours with no solution.

Please help! thanks

---

### Post by Ayuthia on 2008-10-09
Can you go into the terminal and post the results of:
```
lspci -nn
```
It looks like you have a Broadcom card since the driver is showing b43, but it will be helpful to see which model you have because some are having a hard time with the b43 driver and will work better with either wl or ndiswrapper drivers.

---

### Post by chromejs10 on 2008-10-09
> **Ayuthia said:**
> Can you go into the terminal and post the results of:
```
lspci -nn
```
It looks like you have a Broadcom card since the driver is showing b43, but it will be helpful to see which model you have because some are having a hard time with the b43 driver and will work better with either wl or ndiswrapper drivers.

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce Go 7900 GS [10de:0298] (rev a1)
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 0a)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 05)
03:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 01)

---

### Post by Ayuthia on 2008-10-09
The 4328 card is a wireless-n card so it is not supported by the b43 driver yet.  You could try the wl driver or ndiswrapper driver.

Here is a link for the wl driver:
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

If you want to try it with a test kernel:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

Here is a link for the ndiswrapper guide:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Hope that helps.

---

### Post by chromejs10 on 2008-10-09
> **Ayuthia said:**
> The 4328 card is a wireless-n card so it is not supported by the b43 driver yet.  You could try the wl driver or ndiswrapper driver.

Here is a link for the wl driver:
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

If you want to try it with a test kernel:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

Here is a link for the ndiswrapper guide:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Hope that helps.

i thought the ndiswrapper did something with windows XP. Like you have to link it to some file in windows? 

I have two questions: if i install 8.04 instead, will I have the same problem or does Hardy support my wireless card? Also, if I do switch to 8.04, will there be any problems with upgrading to 8.10 once its out of beta?

---

### Post by Ayuthia on 2008-10-09
> **chromejs10 said:**
> i thought the ndiswrapper did something with windows XP. Like you have to link it to some file in windows? 

I have two questions: if i install 8.04 instead, will I have the same problem or does Hardy support my wireless card? Also, if I do switch to 8.04, will there be any problems with upgrading to 8.10 once its out of beta?

NDISwrapper does need to use a Windows wireless driver.  The ndiswrapper link that I provided should have a link for you to get the file.

I guess I did not catch that you are using 8.10.  If you are using 8.10, you should try to use the wl driver.  It should be there for you.  Try and see if you can activate the wl driver in System->Administration->Hardware Drivers.  You will need to make sure that the b43 option is not enabled and that the wl option is enabled.

Usually when you are upgrading, most people will recommend that you do a fresh install instead of upgrading, but if you are not doing any special types of downloads that are outside of the Ubuntu repositories, usually the upgrade is ok.

---

### Post by chromejs10 on 2008-10-09
> **Ayuthia said:**
> NDISwrapper does need to use a Windows wireless driver.  The ndiswrapper link that I provided should have a link for you to get the file.

I guess I did not catch that you are using 8.10.  If you are using 8.10, you should try to use the wl driver.  It should be there for you.  Try and see if you can activate the wl driver in System->Administration->Hardware Drivers.  You will need to make sure that the b43 option is not enabled and that the wl option is enabled.

Usually when you are upgrading, most people will recommend that you do a fresh install instead of upgrading, but if you are not doing any special types of downloads that are outside of the Ubuntu repositories, usually the upgrade is ok.

OK i set the wl active and disabled the b43 option. Do I still need to follow the wl post you gave me even though the wl option appears? Also do I need to restart after doing this?

Sorry for being so newbie.

---

### Post by Ayuthia on 2008-10-09
> **chromejs10 said:**
> OK i set the wl active and disabled the b43 option. Do I still need to follow the wl post you gave me even though the wl option appears? Also do I need to restart after doing this?

Sorry for being so newbie.

You should not have to follow the post because the driver is in linux-restricted-modules (means that the driver is already installed but just needs to be activated with your permission because it is a proprietary driver).  However, you have the b44 driver for your wired card so you do need a workaround to make the wl driver work.  You will need to open up the Terminal and type(or paste):
```
echo -e '#ssb workaround, added `date`\ninstall wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl
```
This will add a script when the wl module is loaded.  What the thing does is remove the b43, b44, and ssb module, load the wl module and then load the b44 module back.  This needs to be done because the ssb module will take the wireless driver and block out the wl driver from working.  However, it will not do this if it is loaded after the wl driver and been loaded.

As for rebooting, I am not for sure if you need to or not.  Most of the time they say that you should, however the following should work also:
```
sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl
sudo ifconfig eth1 up
```I am not for sure if you need to do the last step (sudo ifconfig eth1 up) or not because network manager might do it automatically.  You might need to wait a few seconds because network manager might not catch up with it fast enough.

---

### Post by chromejs10 on 2008-10-09
> **Ayuthia said:**
> You should not have to follow the post because the driver is in linux-restricted-modules (means that the driver is already installed but just needs to be activated with your permission because it is a proprietary driver).  However, you have the b44 driver for your wired card so you do need a workaround to make the wl driver work.  You will need to open up the Terminal and type(or paste):
```
echo -e '#ssb workaround, added `date`\ninstall wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl
```
This will add a script when the wl module is loaded.  What the thing does is remove the b43, b44, and ssb module, load the wl module and then load the b44 module back.  This needs to be done because the ssb module will take the wireless driver and block out the wl driver from working.  However, it will not do this if it is loaded after the wl driver and been loaded.

As for rebooting, I am not for sure if you need to or not.  Most of the time they say that you should, however the following should work also:
```
sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl
sudo ifconfig eth1 up
```I am not for sure if you need to do the last step (sudo ifconfig eth1 up) or not because network manager might do it automatically.  You might need to wait a few seconds because network manager might not catch up with it fast enough.

It worked! thanks so much for all the time you spent with me! I REALLY appreciate it!

---

### Post by Ayuthia on 2008-10-09
> **chromejs10 said:**
> It worked! thanks so much for all the time you spent with me! I REALLY appreciate it!

Glad to see it worked!  Welcome to Ubuntu!

---

### Post by Guspaz on 2008-10-27
Another thanks from me! I'm also an Inspiron 9400 user (what we call the E1705 in Canada), and I've also got the 4328 (via the Dell 1500 wireless card). I had the exact same problem, and the workaround fixed things perfectly.

My solution under 8.04 was to use ndiswrapper and manually write scripts around wpa_supplicant (I was using Kubuntu and it was refusing to work properly with the UI network applet, I'm using regular Ubuntu this time).

Everything is just peachy now :)

---

### Post by bwitt on 2008-10-31
Let me add one more thanks! I was close to tearing my hair out over this :)

---

### Post by tephelan on 2008-11-02
I upgraded to 8.10 on Thursday and couldn't get my b43 card to working.
I searched all weekend and tried everything. I finally found this post which explained everything and why.

Thank you Ayuthia.

---

### Post by KayakJim on 2008-11-04
> **Ayuthia said:**
> You should not have to follow the post because the driver is in linux-restricted-modules (means that the driver is already installed but just needs to be activated with your permission because it is a proprietary driver).  However, you have the b44 driver for your wired card so you do need a workaround to make the wl driver work.  You will need to open up the Terminal and type(or paste):
```
echo -e '#ssb workaround, added `date`\ninstall wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl
```
This will add a script when the wl module is loaded.  What the thing does is remove the b43, b44, and ssb module, load the wl module and then load the b44 module back.  This needs to be done because the ssb module will take the wireless driver and block out the wl driver from working.  However, it will not do this if it is loaded after the wl driver and been loaded.

As for rebooting, I am not for sure if you need to or not.  Most of the time they say that you should, however the following should work also:
```
sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl
sudo ifconfig eth1 up
```I am not for sure if you need to do the last step (sudo ifconfig eth1 up) or not because network manager might do it automatically.  You might need to wait a few seconds because network manager might not catch up with it fast enough.

That got me working as well! I have been wanting to use Ubuntu since v7 but could not since I could never get my wireless working. I was *so* disappointed after installing 8.10 and wireless was still not working. I would buy you a steak and beer if I could. Thank you very much!

---

