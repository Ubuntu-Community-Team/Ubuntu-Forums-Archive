---
title: "Wireless problem in Ubuntu"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by nns2006 on 2009-04-01
Hi,
I am using windows-XP and ubuntu both on my Dell vostro 1500. Ubuntu is installed inside the windows.I have  problem in connecting to Internet through wireless in ubuntu. However in Windows there is no problem at all.
Please help.

---

### Post by nns2006 on 2009-04-01
right now i am using wired connection

---

### Post by spcwingo on 2009-04-02
Run these commands in a terminal and copy/paste the output here:

```
lspci
``` (this will list pci devices)
```
lsusb
``` (this will list usb devices)

---

### Post by cafeinoz on 2009-04-02
I had the the same problem in ubuntu but not in easy peasy linux. I think it has something to do with the madwifi driver. Go to madwifi.org for more information.

---

### Post by ivanvajar on 2009-04-02
> iwconfig

sudo iwlist scann

sudo iwconfig *xxx0* essid *ESSID*  #xxx0 - your wlan (EG wlan0)

If you use pppoe, also use this comand:

> sudo pppoeconf

---

### Post by nns2006 on 2009-04-02
> **spcwingo said:**
> Run these commands in a terminal and copy/paste the output here:

```
lspci
``` (this will list pci devices)
```
lsusb
``` (this will list usb devices)



nityanand@nityanand-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

nityanand@nityanand-laptop:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
What now?

---

### Post by nns2006 on 2009-04-02
> **ivanvajar said:**
> If you use pppoe, also use this comand:




          &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; ALL DEVICES FOUND? &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
          &#9474;                                                          &#9474; 
          &#9474; I found 2 ethernet devices:                              &#9474; 
          &#9474; eth0                                                     &#9474; 
          &#9474; wlan0                                                    &#9474; 
          &#9474;                                                          &#9474; 
          &#9474; Are all your ethernet interfaces listed above?           &#9474; 
          &#9474; (If No, modconf will be started so you can load the      &#9474; 
          &#9474; card drivers manually).                                  &#9474; 
          &#9474;                                                          &#9474; 
          &#9474; Or press ESC to abort here.                              &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;               <Yes>                  <No>                &#9474; 
          &#9474;                                                          &#9474; 
          &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
            

          &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; NOT CONNECTED &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
          &#9474;                                                          &#9474; 
          &#9474; Sorry, I scanned 2 interfaces, but the Access            &#9474; 
          &#9474; Concentrator of your provider did not respond. Please    &#9474; 
          &#9474; check your network and modem cables. Another reason      &#9474; 
          &#9474; for the scan failure may also be another running pppoe   &#9474; 
          &#9474; process which controls the modem.                        &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                          <Ok>                            &#9474; 
          &#9474;                                                          &#9474; 
          &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                                       
nityanand@nityanand-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

nityanand@nityanand-laptop:~$ sudo iwlist scann
[sudo] password for nityanand: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

nityanand@nityanand-laptop:~$ sudo iwconfig xxx0 essid ESSID #xxx0
nityanand@nityanand-laptop:~$ sudo iwconfig xxx0 essid ESSID #xxx0 IEEE 802.11g  
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device xxx0 ; No such device.
nityanand@nityanand-laptop:~$ sudo pppoeconf
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory

What to do now??

---

### Post by spcwingo on 2009-04-02
You might want to look here for instructions for ndiswrapper:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)")

If that doesn't work, you can give this a shot:

[http://ubuntuforums.org/showthread.php?t=896713&highlight=broadcom+bcm4311]("http://ubuntuforums.org/showthread.php?t=896713&highlight=broadcom+bcm4311")

Broadcom cards are notorious for awful Linux support.

---

### Post by lkraemer on 2009-04-02
OK, your Wifi is a "0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)".

From this point you have several ways to proceed.  Use ndiswrapper and the
Windows Driver for your BCM4311, OR use the Broadcom firmware and module
bcm43xx, OR the madwifi support.

To find out if the *.fw files have been previously installed you can do
this in a Terminal window:

```

cd /
cd /lib
ls
ls -alt

```
You should see a directory /firmware
If so, do a:
```

cd /firmware
ls
ls -alt

```
You will either have *.fw files or a subdirectory /b43 & maybe /b43legacy
If you have a /b43 do:
```

cd /b43
ls
ls -alt

```
You should see *.fw ........if the firmware has been installed.
If *.fw exists try this:
```

lsmod

```
If module b43 or b43xx is installed, I'd think it should work.
If they are not installed try:
```

sudo modprobe bcm43xx
iwconfig

```
If you see ath0, wlan0 or such listed for Wifi, you should be
able to get it working.

If the firmware isn't installed search for "HOWTO: & Broadcom"
or "HOWTO: & madwifi", OR go here and download it.
[http://www.omattos.com/broadcom/](http://www.omattos.com/broadcom/)
Copy the *.fw files to /lib/firmware/b43

There are several guides.  I used the one by Jamie Jackson to install my
BMC4318 on 8.04 LTS with ndiswrapper.  You might want to search for "Broadcom"
with user Jamie Jackson.....or

[http://ubuntuforums.org/showthread.php?t=197102&highlight=HOWTO+bcm43xx](http://ubuntuforums.org/showthread.php?t=197102&highlight=HOWTO+bcm43xx)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Now post the output of:
```

ndiswrapper -l
lsmod
iwconfig


```
This will tell us what has been loaded etc.

lkraemer

---

### Post by slimteufel on 2009-04-02
> **nns2006 said:**
> Hi,
I am using windows-XP and ubuntu both on my Dell vostro 1500. Ubuntu is installed inside the windows.I have  problem in connecting to Internet through wireless in ubuntu. However in Windows there is no problem at all.
Please help.


What worked for me (HP DV-series laptop) was using windows and the HP support site to determine exactly what wifi card was in my machine.  Once I discovered that otheros wifi was installed I scooped up the madwifi fixes and once I rebooted: magic.  One side effect now that I have this setup: I have to hold down the space-bar on boot when the ubuntu logo appears until the bar moves on it's own.  Little price to pay so I can smoke on my front porch and surf al gore's interwebs. ;)

---

### Post by nns2006 on 2009-05-02
sorry for long gap in my reply. I upgraded to ubuntu 9.04 and my problem disappear.:).
Thank you all for helping me out.

---

