---
title: "Dongle (mobile broadband) works fine in Win 8 but unable to activate in Ubuntu 12.04"
date: 2014-02-20
forum: Networking &amp; Wireless
---

### Post by swarup on 2014-02-20
I am in India, using a new laptop Toshiba Satellite C55-A, with Micromax Dongle (mobile broadband) and a 3G simcard (Airtel). I have set up a dual boot with Win 8 and Ubuntu 12.04. The mobile broadband is working perfectly in Windows, but I cannot activate it in Ubuntu 12.04. Here below are the steps I have taken in terminal window-- my friend also has the same dongle, and these steps got it active and working on his laptop. But it has not worked on my laptop:

```
dhananjoy@dhananjoy-Satellite-C55-A:~$ lsusb

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 

Bus 001 Device 004: ID 10f1:1a52 Importek 

Bus 002 Device 003: ID 2020:0002  

dhananjoy@dhananjoy-Satellite-C55-A:~$ sudo su
[sudo] password for dhananjoy: 

root@dhananjoy-Satellite-C55-A:/home/dhananjoy# modprobe option

root@dhananjoy-Satellite-C55-A:/home/dhananjoy# echo 10F1 1A52 > /sys/bus/usb-serial/drivers/option1/new_id

root@dhananjoy-Satellite-C55-A:/home/dhananjoy# 
```

After doing the above steps and creating a mobile broadband connection in the connection wizard, the connection icon in the upper right corner of the desktop is still blank and there is no connection. My friend says an entry should have appeared in the network dropdown menu, to "enable mobile broadband", but it has not appeared.

I would very much appreciate help to get this working, as I would like to do all my work in Ubuntu rather than Windows. Thank you!

---

### Post by varunendra on 2014-02-21
Were the kernel version and the device ID (10f1:1a52) also the same in your friend's laptop?
I think you are using your WebCam's device ID instead of your modem, which looks like the **[noparse]2020:0002[/noparse]** device. This id doesn't seem to be included in usb_modeswitch package upto kernel 3.8 (not sure about later ones), and is from the state when it hasn't changed its state from a storage device to a modem device. In this state, forcing the driver 'option' to it won't work.

Please unplug the modem > wait for 10 seconds > replug > wait for 30 seconds > open terminal and post the output of -
```
lsusb
dmesg | tail -40
```

---

### Post by swarup on 2014-02-27
Sorry for the delayed reply-- I was in a rural area for the past week and could not get on line. I do not know about the kernel version of my friend's laptop, but the device ID was different. We were guessing about the device ID.

Here is the output you requested:

```
dhananjoy@dhananjoy-Satellite-C55-A:~$ lsusb 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 10f1:1a52 Importek 
Bus 002 Device 004: ID 2020:0002   
dhananjoy@dhananjoy-Satellite-C55-A:~$ dmesg | tail -40 
[   13.951714] Bluetooth: Core ver 2.16 
[   13.951736] NET: Registered protocol family 31 
[   13.951738] Bluetooth: HCI device and connection manager initialized 
[   13.951745] Bluetooth: HCI socket layer initialized 
[   13.951747] Bluetooth: L2CAP socket layer initialized 
[   13.951753] Bluetooth: SCO socket layer initialized 
[   13.961286] Bluetooth: RFCOMM TTY layer initialized 
[   13.961297] Bluetooth: RFCOMM socket layer initialized 
[   13.961299] Bluetooth: RFCOMM ver 1.11 
[   14.088049] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
[   14.088053] Bluetooth: BNEP filters: protocol multicast 
[   14.088062] Bluetooth: BNEP socket layer initialized 
[   14.322823] type=1400 audit(1393477088.096:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=918 comm="apparmor_parser" 
[   14.323273] type=1400 audit(1393477088.096:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=918 comm="apparmor_parser" 
[   14.323530] type=1400 audit(1393477088.096:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=918 comm="apparmor_parser" 
[   14.400693] type=1400 audit(1393477088.176:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=917 comm="apparmor_parser" 
[   14.401054] type=1400 audit(1393477088.176:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=917 comm="apparmor_parser" 
[   14.435679] type=1400 audit(1393477088.208:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=919 comm="apparmor_parser" 
[   14.440819] type=1400 audit(1393477088.212:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=919 comm="apparmor_parser" 
[   14.441863] type=1400 audit(1393477088.212:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=919 comm="apparmor_parser" 
[   14.442712] type=1400 audit(1393477088.212:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=919 comm="apparmor_parser" 
[   14.445800] type=1400 audit(1393477088.216:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer//launchpad_integration" pid=919 comm="apparmor_parser" 
[   16.825025] alx 0000:01:00.0: irq 44 for MSI/MSI-X 
[   16.825032] alx 0000:01:00.0: irq 45 for MSI/MSI-X 
[   16.825037] alx 0000:01:00.0: irq 46 for MSI/MSI-X 
[   16.826309] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   16.827690] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   19.207423] init: plymouth-stop pre-start process (1184) terminated with status 1 
[   86.158111] usb 2-1.1: USB disconnect, device number 3 
[  108.977672] usb 2-1.1: new high-speed USB device number 4 using ehci-pci 
[  109.071935] usb 2-1.1: New USB device found, idVendor=2020, idProduct=0002 
[  109.071946] usb 2-1.1: New USB device strings: Mfr=2, Product=3, SerialNumber=4 
[  109.071952] usb 2-1.1: Product: Modems 
[  109.071956] usb 2-1.1: Manufacturer: Micromax Informatics Ltd. 
[  109.071961] usb 2-1.1: SerialNumber: 193170548201470 
[  109.073620] scsi8 : usb-storage 2-1.1:1.0 
[  110.073918] scsi 8:0:0:0: CD-ROM            Micromax Modem            6225 PQ: 0 ANSI: 0 CCS 
[  110.077840] sr1: scsi3-mmc drive: 0x/0x caddy 
[  110.078084] sr 8:0:0:0: Attached scsi CD-ROM sr1 
[  110.078243] sr 8:0:0:0: Attached scsi generic sg2 type 5 
dhananjoy@dhananjoy-Satellite-C55-A:~$ 
```

Please let me know what would be the next step for getting on-line...

---

### Post by varunendra on 2014-02-27
> **swarup said:**
> ```

[  108.977672] usb 2-1.1: new high-speed USB device number 4 using ehci-pci 
[  109.071935] usb 2-1.1: New USB device found,** idVendor=2020, idProduct=0002 **
[  109.071946] usb 2-1.1: New USB device strings: Mfr=2, Product=3, SerialNumber=4 
[  109.071952] usb 2-1.1: Product: Modems 
[  109.071956] usb 2-1.1: Manufacturer: Micromax Informatics Ltd. 
[  109.071961] usb 2-1.1: SerialNumber: 193170548201470 
[  109.073620] scsi8 : usb-storage 2-1.1:1.0 
[  110.073918] scsi 8:0:0:0: CD-ROM            Micromax Modem            6225 PQ: 0 ANSI: 0 CCS 
[  110.077840] sr1: scsi3-mmc drive: 0x/0x caddy 
[  110.078084] sr 8:0:0:0: **Attached scsi CD-ROM sr1 **
[  110.078243] sr 8:0:0:0: Attached scsi generic sg2 type 5 
dhananjoy@dhananjoy-Satellite-C55-A:~$ 
```

Like I suspected, it doesn't seem to be switched to modem mode, which means it is most probably not yet supported by the usb_modeswitch version you have (can't say if a newer version supports it).

However, it seems to be in CDRom mode currently, as highlighted in the last lines of the dmesg above. Can you browse to it? Usually, the real or virtual CDRoms are mounted in /cdrom or /media/cdrom directory. You can confirm it by taking a look at the output of "mount" command, or running the graphical "Disk Utility" program.

If you can open its contents, do you see any linux drivers in it? If yes, copy the whole package/folder to your desktop and post back what are its contents (might as well try to install the driver if the kernel is supported and the instructions are clear enough).

If there are no linux drivers on the drive, you may try your luck with the following command, although I'm not very optimistic with it (because it was meant for a different device from the same vendor) -
```
sudo usb_modeswitch -v 0x2020 -p 0x0002 -M "5553424312345678000000000000061b000000020000000000000000000000"
```
Then check again -
```
lsusb
dmesg | tail -20
```
Did the device change its ID?
If not, try 'Ejecting' its emulated 'CDRom' using "Disk Utility" > wait about 4-6 seconds > check lsusb again. Did it change the ID now?
If still not, unplug > replug. If the device ID in lsusb still shows up as **[noparse]"2020:0002"[/noparse]**, then we may be out of luck with this modem, at least for now.

Please try and let us know outcome. We may try to hunt for a required code to make it work, or a newer version/patch for usb_modeswitch that supports this device.

---

### Post by Eric_Atwood on 2014-02-27
This looks like it should help.
[http://www.ubuntuask.com/q/answers-micromax-usb-modem-model-mmx-352g-not-recognized-in-ubuntu-10-04-lts-146348.html](http://www.ubuntuask.com/q/answers-micromax-usb-modem-model-mmx-352g-not-recognized-in-ubuntu-10-04-lts-146348.html)

---

### Post by swarup on 2014-02-27
@ Varunendra: I am currently booted up to Windows (on the same laptop) as it is the only way I can get online. But I will go into Ubuntu and try to do what you suggest. I can tell you this much now: the package the modem came in lists the System Requirements as Widows 8/7/Vista/XP; MAC 10.6, 10.7; Ubuntu 10.04. So Ubuntu 10.04 is supported. Given that, I have hope that we should be able to get 12.04 working as well. Am I thinking in the proper direction?

(It is a bit odd that they have the very newest Windows OS listed, and yet such an old version of Ubuntu (4 years old) is listed. Anyhow, at least Ubuntu is listed...

---

### Post by swarup on 2014-02-27
@Eric_Atwood: Thanks for the great link. The last entry on that thread looks like it might be exactly what is needed. But the model I have is newer than the one the original poster listed. Our model number is Micromax MMX377G. Do you think I should try what the last poster suggested?

---

### Post by Bucky Ball on 2014-02-27
*Thread moved to **Networking & Wireless**.*

Please post in the appropriate forum section. You will improve your chances of support. Thanks.

---

### Post by varunendra on 2014-02-27
> **swarup said:**
> So Ubuntu 10.04 is supported. Given that, I have hope that we should be able to get 12.04 working as well. Am I thinking in the proper direction?
Since the device ID seems to be rather new, I hope the above means they have provided the Linux driver package on the modem itself. It most probably won't compile on the currently supported kernels, but the contents may give us significant information to derive our own solution.

@Eric_Atwood, Welcome to Ubuntu Forums ! :)

The methods on that page look okay, but the devices are different. Besides, I'm pretty sure the last post on that page is absolutely wrong/misleading. It is using the same device ID for both Default and Target IDs (which in *some* cases can be true, but certainly not in case of THAT device) which is 1c9e:9605. That is a target id for a device with default ID of **1c9e:[COLOR="#FF0000"]f000[/COLOR]**.

As a matter of fact, I am myself connected via a **1c9e:9603** device while posting this, which is almost the same device (target IDs "9000,**9603,9605**,9607" have same Default ID - 1c9e:f000). I can confirm that its IDs before and after modeswitching are different. :P

In any case, Swaroop, I wouldn't try THAT solution until all other logical approaches have failed. Because
**1)** the last post there is certainly misleading (unless I am terribly wrong),
**2)** usbserial is a relatively much slower driver than the "option" driver, which would be automatically be used once the device successfully changes its ID,
**3)** apart from the usbserial part, the rest of the solution (the applicable part) is same as what I suggested with the "usb_modeswitch" command. If that command fails, the method fails.
**4)** Adding a "sleep 10+20+10" to /etc/rc.local file is not such a good idea no matter how elegant the rest of the solution is. While not being serious, it is a very crude way of automating a task and the delay may cause other problems in the background. There are much better (correct) ways to achieve that.

---

### Post by swarup on 2014-02-27
> **varunendra said:**
> However, it seems to be in CDRom mode currently, as highlighted in the last lines of the dmesg above. Can you browse to it? Usually, the real or virtual CDRoms are mounted in /cdrom or /media/cdrom directory. You can confirm it by taking a look at the output of "mount" command, or running the graphical "Disk Utility" program.

If you can open its contents, do you see any linux drivers in it? If yes, copy the whole package/folder to your desktop and post back what are its contents (might as well try to install the driver if the kernel is supported and the instructions are clear enough).

I confirmed with the Disk Utility program, and it is indeed mounted as a CDRom. But I looked in nautilus, and the /cdrom and /media/cdrom directories are empty. So it does not seem possible to browse it or look for the Linux software on it.

I will try the command you have given in a few moments.

In the mean time, here is the output of the "mount" command:

```
dhananjoy@dhananjoy-Satellite-C55-A:~$ mount 
/dev/sda6 on / type ext4 (rw,errors=remount-ro) 
proc on /proc type proc (rw,noexec,nosuid,nodev) 
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) 
none on /sys/fs/fuse/connections type fusectl (rw) 
none on /sys/kernel/debug type debugfs (rw) 
none on /sys/kernel/security type securityfs (rw) 
none on /sys/firmware/efi/efivars type efivarfs (rw) 
udev on /dev type devtmpfs (rw,mode=0755) 
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) 
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) 
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) 
none on /run/shm type tmpfs (rw,nosuid,nodev) 
/dev/sda2 on /boot/efi type vfat (rw) 
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev) 
gvfs-fuse-daemon on /home/dhananjoy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dhananjoy) 
dhananjoy@dhananjoy-Satellite-C55-A:~$ 
```

---

### Post by varunendra on 2014-02-27
> **swarup said:**
> I confirmed with the Disk Utility program, and it is indeed mounted as a CDRom.
How did it confirm? Did it show its device name (e.g., /dev/sr1)? If mounted 'anywhere', it should also show its mount-point.  But from the output of "mount", it doesn't look like it was mounted. We can manually mount it though, if we know its device name for sure.

For example,
```
sudo mount /dev/sr1 /media/cdrom
```

---

### Post by swarup on 2014-02-27
It worked! That command which you gave, and said you were not very optimistic about it-- it worked! The ID changed with it. After doing so, it did not remount the device, but when as you suggested I went again into the Disk Utility and ejected it from the CDRom, then it ejected and immediately became remounted in the proper way, and appeared in the wireless device options dropdown menu as Airtel 1. When I clicked on it, it immediately went on line! Thanks so much for your help, Varun! You did a great job!

Here is the output of the terminal window for any interested:

```
dhananjoy@dhananjoy-Satellite-C55-A:~$ sudo usb_modeswitch -v 0x2020 -p 0x0002 -M "5553424312345678000000000000061b000000020000000000000000000000" 
[sudo] password for dhananjoy: 

Looking for default devices ... 
   found matching product ID 
   adding device 
 Found device in default mode, class or configuration (1) 
Accessing device 003 on bus 002 ... 
Getting the current device configuration ... 
 OK, got current device configuration (1) 
Using first interface: 0x00 
Using endpoints 0x01 (out) and 0x81 (in) 
Inquiring device details; driver will be detached ... 
Looking for active driver ... 
 OK, driver found ("usb-storage") 
 OK, driver "usb-storage" detached 

SCSI inquiry data (for identification) 
------------------------- 
  Vendor String: Micromax 
   Model String: Modem            
Revision String: 6225 
------------------------- 

USB description data (for identification) 
------------------------- 
Manufacturer: Micromax Informatics Ltd. 
     Product: Modems 
  Serial No.: 193170548201470 
------------------------- 
Setting up communication with interface 0 
Using endpoint 0x01 for message sending ... 
Trying to send message 1 to endpoint 0x01 ... 
 OK, message successfully sent 
Resetting response endpoint 0x81 
Resetting message endpoint 0x01 
-> Run lsusb to note any changes. Bye. 

dhananjoy@dhananjoy-Satellite-C55-A:~$ lsusb 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 10f1:1a52 Importek 
Bus 002 Device 004: ID 2020:4010   
dhananjoy@dhananjoy-Satellite-C55-A:~$ sudo su 
root@dhananjoy-Satellite-C55-A:/home/dhananjoy# modprobe option 
root@dhananjoy-Satellite-C55-A:/home/dhananjoy# echo 2020 4010 > /sys/bus/usb-serial/drivers/option1/new_id 
root@dhananjoy-Satellite-C55-A:/home/dhananjoy# dmesg | tail -20 
[  527.041432] option1 ttyUSB0: option_instat_callback: error -108 
[  527.041656] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0 
[  527.041672] option 2-1.1:1.2: device disconnected 
[  527.042963] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1 
[  527.042979] option 2-1.1:1.3: device disconnected 
[  527.043076] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2 
[  527.043086] option 2-1.1:1.4: device disconnected 
[  527.043158] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3 
[  527.043167] option 2-1.1:1.5: device disconnected 
[  539.537758] usb 2-1.1: new high-speed USB device number 5 using ehci-pci 
[  539.632082] usb 2-1.1: New USB device found, idVendor=2020, idProduct=0002 
[  539.632094] usb 2-1.1: New USB device strings: Mfr=2, Product=3, SerialNumber=4 
[  539.632100] usb 2-1.1: Product: Modems 
[  539.632105] usb 2-1.1: Manufacturer: Micromax Informatics Ltd. 
[  539.632109] usb 2-1.1: SerialNumber: 193170548201470 
[  539.633799] scsi9 : usb-storage 2-1.1:1.0 
[  540.634120] scsi 9:0:0:0: CD-ROM            Micromax Modem            6225 PQ: 0 ANSI: 0 CCS 
[  540.637853] sr1: scsi3-mmc drive: 0x/0x caddy 
[  540.638096] sr 9:0:0:0: Attached scsi CD-ROM sr1 
[  540.638280] sr 9:0:0:0: Attached scsi generic sg2 type 5 
root@dhananjoy-Satellite-C55-A:/home/dhananjoy# 
```

---

### Post by varunendra on 2014-02-27
> **swarup said:**
> It worked! That command which you gave, and said you were not very optimistic about it-- it worked!

Wow! Indeed a heart-bouncing moment for me :D

**But did you need to manually bind the driver "option" to it?** As apparent here -
```
Bus 002 Device 004: **ID 2020:4010**   
dhananjoy@dhananjoy-Satellite-C55-A:~$ sudo su 
root@dhananjoy-Satellite-C55-A:/home/dhananjoy# modprobe option 
root@dhananjoy-Satellite-C55-A:/home/dhananjoy# **echo 2020 4010 > /sys/bus/usb-serial/drivers/option1/new_id**
```
I was hoping that usb_modeswitch will automatically do this job, that is, binding the id to the driver option.

In any case, you can try to automate the modeswitching by writing a configuration file in /etc/usb_modeswitch.d directory, and adding a rule in /lib/udev/rules.d/40-usb_modeswitch.rules file.

**_To create the conf file_**, open the text editor and copy-paste this into a new blank file -
```
# Micromax MMX377G

TargetVendor=  0x2020
TargetProduct= 0x4010

MessageContent="5553424312345678000000000000061b000000020000000000000000000000"
WaitBefore=2

```
(I'm not sure about the "WaitBefore" option, but it seems it is the time to wait before releasing the interface. If so, a proper value may do the trick of timely ejection/remounting)

Save this file with name **[noparse]2020:0002[/noparse]** on your desktop.

Now copy this file to the **/etc/usb_modeswitch.d** directory -
```
sudo cp [COLOR="#800000"]Desktop/2020:0002[/COLOR] [COLOR="#0000CD"]/etc/usb_modeswitch.d/[/COLOR]
```

**_To add the rule_**, open the rules file with root access -
```
gksu gedit /lib/udev/rules.d/40-usb_modeswitch.rules
```
Scroll down to the section that says "**# SpeedUp SU-8000U**" (line no. 660 in my file here). Copy these two lines -
```
# SpeedUp SU-8000U
ATTRS{idVendor}=="2020", ATTRS{idProduct}=="f00e", RUN+="usb_modeswitch '%b/%k'"
```
..and paste them right below the original lines, leaving a space to maintain the format and readability of the file. Then modify this copied line to -
```
**[COLOR="#B22222"]# Micromax MMX377G[/COLOR]**
ATTRS{idVendor}=="2020", ATTRS{idProduct}=="**[COLOR="#B22222"]0002[/COLOR]**", RUN+="usb_modeswitch '%b/%k'"
```
Proofread, save and close the file.

If you needed to manually bind the option driver, it can also be automated by slightly modifying the above rule, but I'm not sure about the need for manual ejection. I'll try to look for a solution if the above changes couldn't do it automatically.

---

### Post by swarup on 2014-02-27
> **varunendra said:**
> Wow! Indeed a heart-bouncing moment for me :D

**But did you need to manually bind the driver "option" to it?** As apparent here -
```
Bus 002 Device 004: **ID 2020:4010**   
dhananjoy@dhananjoy-Satellite-C55-A:~$ sudo su 
root@dhananjoy-Satellite-C55-A:/home/dhananjoy# modprobe option 
root@dhananjoy-Satellite-C55-A:/home/dhananjoy# **echo 2020 4010 > /sys/bus/usb-serial/drivers/option1/new_id**
```
I was hoping that usb_modeswitch will automatically do this job, that is, binding the id to the driver option.

...

If you needed to manually bind the option driver, it can also be automated by slightly modifying the above rule, but I'm not sure about the need for manual ejection. I'll try to look for a solution if the above changes couldn't do it automatically.

I have just tested it step by step-- and yes, I need to manually bind the driver "option" to it as noted in the above steps (sudo su, etc). Without those steps, it will not work. It just remains mounted as a CDRom device. And once I manually bind the driver "option" it, then it seems I also need to open disc utility and eject the device from its CDRom mount point. Once I do that, then the "Airtel 1" option appears in the network icons dropdown list, and I can click it and go on line. 

So if you could include those steps in the code you gave to make the whole process automated, that will be wonderful! I am giving this laptop to my friend (Dhananjoy) here in West Bengal, and it is his first time using any sort of computer. Everything will need to be automated for him so the "Airtel 1" option will appear every time he boots into Ubuntu and he can just click it to get online. Thank you so much Varun! You are a lifesaver.

---

### Post by swarup on 2014-02-27
I've just tested it again. Once I do your usb_modeswitch command, then it switches over from the CDRom mountpoint to the modem mount point-- although the Airtel 1 option does not appear in the network dropdown window. Once I manually bind the driver "option" using the sudo su etc 3 steps, then the Airtel 1 option appears and I can go online. So it appears that the last step I mentioned above -- that of ejecting the device from the CDRom mount point, is not needed. I could swear I had to do it the previous time, but this time it switched over to the modem mount point as soon as I did your usb_modeswitch command, and I did not need to go into disk utility to eject it.

---

### Post by varunendra on 2014-02-27
Shall post back in a few hours from now (if my internet didn't deceive me). In the meanwhile, can you test this command? -
```
sudo usb_modeswitch -v 0x2020 -p 0x0002 -M "5553424312345678000000000000061b000000020000000000000000000000" **-R**
```
..and see if it eliminates the need to do the ejection manually?

There are some other options as well that may be worth trying, take a look at the manpage for usb_modeswitch ("man usb_modeswitch"). Try them if you have the time.

I'll post back as soon as possible. The result of the above test (and similar ones) may help us a lot, if successful.

---

### Post by swarup on 2014-02-28
I just tested the new command you gave with the "-R" at the end. It worked fine; I didn't notice any difference in whether the -R was there or not though. The sudo su etc 3 steps are still needed. In the terminal window code output, I noted one new line after inputting your command with the -R:

```
Resetting usb device ...........
 Reset failed. Can be ignored if device switched OK.
-> Run lsusb to note any changes. Bye.
```

The "Reset failed" is new, but it didn't seem to affect anything. I'll pust the full output below in case you want to see it:

```
dhananjoy@dhananjoy-Satellite-C55-A:~$ sudo usb_modeswitch -v 0x2020 -p 0x0002 -M "5553424312345678000000000000061b000000020000000000000000000000" -R
[sudo] password for dhananjoy: 

Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 003 on bus 002 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x00
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: Micromax
   Model String: Modem           
Revision String: 6225
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: Micromax Informatics Ltd.
     Product: Modems
  Serial No.: 193170548201470
-------------------------
Setting up communication with interface 0
Using endpoint 0x01 for message sending ...
Trying to send message 1 to endpoint 0x01 ...
 OK, message successfully sent
Resetting response endpoint 0x81
Resetting message endpoint 0x01
Resetting usb device ...........
 Reset failed. Can be ignored if device switched OK.
-> Run lsusb to note any changes. Bye.

dhananjoy@dhananjoy-Satellite-C55-A:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 10f1:1a52 Importek 
Bus 002 Device 004: ID 2020:4010  
dhananjoy@dhananjoy-Satellite-C55-A:~$ sudo su
root@dhananjoy-Satellite-C55-A:/home/dhananjoy# modprobe option
root@dhananjoy-Satellite-C55-A:/home/dhananjoy# echo 2020 4010 > /sys/bus/usb-serial/drivers/option1/new_id
root@dhananjoy-Satellite-C55-A:/home/dhananjoy# 
```

I hope you can post the final steps needed for me to automate this process, once you are again online in a few hours. That will be really great :)

---

### Post by swarup on 2014-02-28
Here are the four steps I currently need to execute in terminal window to get on line. So these are the four steps that need to be automated:

```
sudo usb_modeswitch -v 0x2020 -p 0x0002 -M "5553424312345678000000000000061b000000020000000000000000000000"
sudo su
modprobe option
echo 2020 4010 > /sys/bus/usb-serial/drivers/option1/new_id 
```

As I mentioned, Dhananjay is new to computers and it would save him a lot of grief to not have to execute these every time he starts his computer. I tried making a script for these four steps, but when I execute the script it only does the first step; maybe it is because the first step takes a few seconds to execute. And at any rate it would be best if we can save him from opening a terminal window; best would be to just have it all be automated in the startup sequence.

---

### Post by varunendra on 2014-02-28
Hmm.. was in a hurry, didn't notice your second post mentioning that you don't need to do the manual ejection part.
That's fantastic! Because the rest of the operations are quite well documented and should work 100%.

> **swarup said:**
> Here are the four steps I currently need to execute in terminal window to get on line. So these are the four steps that need to be automated:

```
sudo usb_modeswitch -v 0x2020 -p 0x0002 -M "5553424312345678000000000000061b000000020000000000000000000000"
sudo su
modprobe option
echo 2020 4010 > /sys/bus/usb-serial/drivers/option1/new_id 
```

The modeswitching should become automatic once you create the custom file in "/etc/usb_modeswitch.d" directory, and add the new rule to the "/lib/udev/rules.d/40-usb_modeswitch.rules" file, as suggested in **post #13** above.

Once the modeswitching becomes automatic, add another rule, this time in "/etc/udev/rules.d", to make the loading and binding of the driver "option" automatic. Here's how [COLOR="#696969"]*(the notes about capital/small letters obviously don't apply to you since YOUR device id is all numbers, no letters. They are for others who may follow this post later)*[/COLOR] -

(for others who may be following these steps later, please note that the **Device ID** should be in **[COLOR="#B22222"]Capital Letters[/COLOR]** in the script, and in **[COLOR="#0000CD"]Small Letters[/COLOR]** in the udev rules file. That's Very Important!)

**A. _Follow Post #13 above to Automate The Mode-Switching_**

**B. _Create a script to load and bind the driver_**

[INDENT]Open your text editor and create a new file. Type or copy-paste the following as its contents *(the **Device ID** will be in **[COLOR="#B22222"]Captial Letters[/COLOR]** here)*-
```
#!/bin/bash
modprobe option
echo **[COLOR="#B22222"]2020 4010[/COLOR]** > /sys/bus/usb-serial/drivers/option1/new_id

```
Save this file with a meaningful name, say "option_2020_4010.sh" on your Desktop. Now open a terminal and copy this file into **/usr/bin** directory, and also make it executable -
```
sudo cp [COLOR="#800000"]Desktop/option_2020_4010.sh[/COLOR] [COLOR="#0000CD"]/usr/bin[/COLOR]
sudo chmod +x /usr/bin/option_2020_4010.sh
```[/INDENT]

**C. _Create a udev rules file to automatically run this script_**

[INDENT]Create a New blank file in your text editor, and type or copy-paste the following as its contents *(the **Device ID** will be in **[COLOR="#0000CD"]Small Letters[/COLOR]** here)* -
```
ATTRS{idVendor}=="**[COLOR="#0000CD"]2020[/COLOR]**", ATTRS{idProduct}=="**[COLOR="#0000CD"]4010[/COLOR]**", RUN+=**"/usr/bin/option_2020_4010.sh"**
```
Save this file as "**option.rules**" on your Desktop, and simply copy it to your /etc/udev/rules.d directory (no need to make it executable) -
```
sudo cp [COLOR="#800000"]Desktop/option.rules[/COLOR] [COLOR="#0000CD"]/etc/udev/rules.d/[/COLOR]
```

**Additional Note :** While I was experimenting with a test script here, the script didn't start working straightaway (even if manually run), which is strange. However, after a few attempts (while analyzing it), it started working without me doing any changes. Not sure why it happened, but it did. So if initially it doesn't seem to work, simply reboot to be extra sure.[/INDENT]

**_The Summary of the Workaround_** -

[LIST=1]
[*]Create a custom usb_modeswitch configuration file and place it in **/etc/usb_modeswitch.d** directory.
[*]Add a new udev rule corresponding to the new (Default) device ID, in **/lib/udev/rules.d/40-usb_modeswitch.rules** file.
[*]Create a script to load and bind the driver "option" to the new (Switched) device ID, and place it in **/usr/bin** directory. Make it executable.
[*]Create a new udev rule file corresponding to the new (Switched) device ID, and place it in **[B]/etc/udev/rules.d**[/B] directory.
[/LIST]
The first two steps automate the mode switching, the last two automate the driver binding.

I'd be waiting for the feedback *(after several rounds of testing across multiple boots and random timings)* very curiously. :)

---

### Post by swarup on 2014-03-01
I executed the directions from  Post#13 and it went smoothly. I rebooted to test it and found that the mode switch command had been successfully automated. I then followed your instructions in your last post (#19) very carefully and confirmed everything I did. However when I rebooted to do the final test, I found to my surprise that after executing the instructions in post #19, the computer will no longer boot into Ubuntu. When I select Ubuntu from the boot menu, it tries to boot and then ultimately just gives me a screen full of code which is not intelligible to me and far to much to copy by hand onto paper and retype here. The only thing I could make out was one line about the modem manager having failed. Help! Varun, I need to undo those changes we implemented in post #19, or whatever you suggest-- we need to get Ubuntu bootable again...

I tried rebooting the computer 5 times, and each time the boot into Ubuntu failed and just yielded a page full of computer code.

---

### Post by varunendra on 2014-03-01
Was the modem plugged in when you booted? It maybe some bug in the device that maybe crashing the modem manager or the option driver.

Try booting without the modem being plugged in, and plug it in AFTER the OS is loaded and working.

The changes suggested in post #19 can not interfere with booting or ANY system process just by their existence. The only time when they can and would do ANYTHING is when not only the modem is plugged in, but also has changed its ID.

The udev rule detects the 'Changed' ID and triggers the script. The script then loads the driver "option" and binds it to the device. That's all they do, and loading/binding of the driver may be the only point that may cause some trouble - easily fixable with some variations.

So if the system is failing to boot properly even without the modem being plugged in, it is most probably something else, not what we tried in posts #13 and #19.

Please confirm -

When you boot without the modem plugged in, does the problem still occur?
When you get the text screen, is the system responsive to your actions? Like if you press "Ctrl-Alt-F1", do you get the tty1 login screen? Can you login there and work with commands?

If you doubt the changes, reverting them is as easy as moving those two files from /usr/lib and /etc/udev/rules.d to your Desktop. You can do that from either the tty1 login or from a live cd/usb.

Advantage of moving instead of deleting them is that we can analyse them to see if there is any problematic error in their contents.

---

### Post by swarup on 2014-03-01
1. When the modem is not plugged in, Ubuntu boots up normally.
2. Once Ubuntu is booted up, as soon as I plug in the modem, I get the same screen of code as I got when the computer would not boot up.
3. Once the screen of code comes, it is not responsive to my actions--  if I press "Ctrl-Alt-F1", nothing happens. No login screen.

I will try to find those two files and move them to the desktop. That way at least the manual commands will work to get the computer online. The two files should be exactly as you instructed them to be. Is there any change you want me to make in their content?

---

### Post by varunendra on 2014-03-01
> **swarup said:**
> The two files should be exactly as you instructed them to be. Is there any change you want me to make in their content?

Yup. Assuming the contents are exactly what I posted, the script contains exactly the same commands that you run manually. So what is the difference?
The only difference I can think of is timing. In manual operation, the second command ("echo...") is naturally run after a few seconds. Let's try adding those few seconds.

In the script file, try changing the contents to -
```
#!/bin/bash
/sbin/modprobe option
**sleep 2**
echo 2020 4010 > /sys/bus/usb-serial/drivers/option1/new_id
```
So we added the Full path to the modprobe command (shouldn't matter anyway), and added a two second gap between the loading and binding of the driver.

Edit the files in-place, or edit them on your desktop --> then move them back to their respective locations --> reboot. If the problem still occurs, change the time to 4 seconds. If even that does not help, we can change both files a bit, in a way that has been tested and proven many times before (yeah, running both commands with a single udev rule was my own idea, I still don't see the difference but whatever works..).

---

### Post by swarup on 2014-03-02
I changed the file as indicated in your last post, and it took 2 seconds longer, but the same thing still happened-- I got a screen full of code, and the computer was frozen. When I then remove those two files from their respective places, it again works fine (manually) the next time I boot up. I can try changing it to 4 seconds, but it does not seem that will make a difference. What about adding time delay to the modeswitch command-- could that be where the time delay is needed? I now there is a good bit of output after that command, and perhaps more time is needed there?

Do you want to try making the changes you suggested with the udev rule above and see if that fixes it?

---

### Post by varunendra on 2014-03-02
I don't think adding any delay to the modeswitch command is needed, because as you mentioned yourself, the modeswitching part is working correctly.

It also shouldn't matter how long it takes to switch the mode, because the device ID will change only when the modeswitching is complete, and the next pair of files (option.rules and the related script) will only be touched when the ID has changed (which means modeswitching has completed).

There is a possibility that the usb_modeswitch is taking a little time to release the device after its mode has been switched. So we may need more time.

Let's do a safe testing -

Please leave the 'option.rules' file as it is, and change the contents of the script file as follows -
```
#!/bin/bash
# /sbin/modprobe option
# sleep 2
# echo 2020 4010 > /sys/bus/usb-serial/drivers/option1/new_id
echo "Script Executed" > /home/dhananjoy/Desktop/Success.txt
```
*[COLOR="#FF0000"](EDIT: Removed double entry of #!/bin/bash)[/COLOR]*
This should create a file "Success.txt" on the desktop (assuming the user id is 'dhananjoy') if successfully executed.

If that happens without problems, we only need to tweak the timing in the last step - the script. Which also means the first three steps are perfect and any change to the option.rules file is possible but not necessary.

**PS:**
If this test fails, please attach (not copy-paste) the last two files - the option.rules and the script, in your next post.

---

### Post by swarup on 2014-03-02
I updated the script file as you indicated, in the version on my desktop, and then copied it to the user/bin as indicated below and again gave the order to make it executable. No file named "Success.txt" has appeared on my desktop.

```
dhananjoy@dhananjoy-Satellite-C55-A:~$ sudo cp Desktop/option_2020_4010.sh /usr/bin
[sudo] password for dhananjoy: 
dhananjoy@dhananjoy-Satellite-C55-A:~$ sudo chmod +x /usr/bin/option_2020_4010.sh
```

I am trying to attach the two files you requested and will append them in the following post in just a minute.

---

### Post by swarup on 2014-03-02
I have attached the script file. When I try to attach the option.rules file I get a message that says "invalid file". But the file opens fine and looks exactly as you indicated it to be. I am showing you the contents of it below:

> ATTRS{idVendor}=="2020", ATTRS{idProduct}=="4010", RUN+="/usr/bin/option_2020_4010.sh"

---

### Post by varunendra on 2014-03-02
I made a mistake in my post which I just corrected - "#!/bin/bash" being typed twice in the same line. Please correct that and try again. Meanwhile, I'll try to do some test myself here.

**EDIT:**
Just tested with the script ("#!/bin/bash" corrected and username changed to mine) and the line you pasted (with device ID changed with my pen drive). Works flawlessly here.

---

### Post by swarup on 2014-03-02
I updated the file as you indicated and again copied it to the indicated folder and made it executable. There is no Success.txt on the desktop.

---

### Post by varunendra on 2014-03-02
Must be some minor glitch. Please test -

After having copied the script and making it executable open a **New** terminal > type -
```
opti
```
..press 'Tab' key. Does it auto-complete to **option_2020_4010.sh** ?

If not, either the script is not in correct place, not executable or not yet recognised. Check with "ls -l" command and retry or retry after a reboot.

If it does auto-complete, press 'Enter'. Does it create the new file on the desktop?

---

### Post by swarup on 2014-03-02
It does auto-complete. When I press 'Enter' though, I do not see a new file on the desktop. 

A piece of good news though: I have just noticed there is a file named "Success.txt" on the desktop. I am not sure after which step it appeared. I must have missed it, as it appeared in a place on the desktop where I was not expecting it to appear.

---

### Post by varunendra on 2014-03-02
Delete that file and run the command (script name) from the terminal again to confirm that it is still working. Once it is confirmed that the script is working, delete the "Success.txt" file again > replug the modem. Does the file get created again?

If there are too many items on the desktop, check with "ls Desktop/Suc*" :P

Needless to say, I am also assuming that the option.rules file is also in its place - /etc/udev/rules.d

Right now I have tested with my pen drive here, but I had tested with my modem when I wrote the original post which we are following.

---

### Post by swarup on 2014-03-02
I deleted the Success.txt file and when I ran the script file, the Success.txt file again appeared on the desktop. I deleted the file, and then unplugged and replugged the modem-- and yes, the Success.txt fie *does* appear.

---

### Post by varunendra on 2014-03-02
Okay, that proves that our first three steps are good. Now the risky test -

Please modify the script to make it look like -
```
#!/bin/bash
echo "Before Modprobe" > /home/dhananjoy/Desktop/Before.txt
/sbin/modprobe option
echo "After Modprobe" > /home/dhananjoy/Desktop/After.txt
# sleep 2
# echo 2020 4010 > /sys/bus/usb-serial/drivers/option1/new_id
```

Save and test again. If this crashes the system again, check on next boot to see if any of the files ("Before.txt" or "After.txt") are found on the desktop. Also check their contents.

I believe at least the first file (Before.txt) should be created properly. It is the modprobe command that may crash the system, in which case, we won't get the second file.

Please test and confirm.

---

### Post by swarup on 2014-03-02
I made the requested change, and it did not crash the system. Both the files (Before.txt, After.txt) appeared immediately on the desktop. I then shut down the system and rebooted to Ubuntu, without the modem plugged in. When I plugged in the modem, nothing happened-- it did not go online. I had to do the three steps manually to get online.

---

### Post by varunendra on 2014-03-02
> **swarup said:**
> rebooted to Ubuntu, without the modem plugged in. When I plugged in the modem, nothing happened-- it did not go online. I had to do the three steps manually to get online.

Which means the mode-switching didn't take place. That's normal with these devices, happens sometimes no matter how well they are supported. Just unplug > wait 10 sec. > replug > check lsusb.

If you didn't alter the first two files (to do the modeswitching), there is no reason why the modeswitching would fail. If it fails, that's a problem that may happen anyway, not because we added the configuration manually.

Anyway, before rebooting, I hope the following happened when you unplugged or replugged the modem, not by manually running the script (from terminal) -
> I made the requested change, and it did not crash the system. **Both the files (Before.txt, After.txt) appeared immediately on the desktop.**

If so, then it is certainly the binding part that is crashing the OS. Leave it to manual mode for a few more test rounds.

Assuming nothing has changed in the modeswitch file/rule, Reboot or Replug the modem (after a reasonable delay in-between, which is usually about 10-12 seconds) without rebooting, and see if the "Before.txt" and "After.txt" files are created. If not, check "lsusb" and "dmesg". Do you see the initial ID of the modem in lsusb not the switched one? Are there any error messages in dmesg?

If the ID is switched as expected, the files should be created as well. After that, check -
```
lsmod | grep option
```
Is the driver loaded? To confirm, delete the files and remove the driver -
```
sudo modprobe -rv option
```
..then unplug or replug the modem. Are the files created again? Is the driver loaded again?

Once the "option" driver is confirmed to be loading automatically, manually run the last command of the required steps in terminal, that is, the binding command -
```
echo 2020 4010 > /sys/bus/usb-serial/drivers/option1/new_id
```
Is the modem active now?

I am almost 100% certain that it is the 'nearly instant' binding attempt that is causing the problem, but we are in debugging mode. It can be tiresome sometimes but it pays back. We need to make sure that it is indeed the binding step that needs sufficient delay before executed.

The only thing I'm not sure about is that how much delay can be allowed without problems in a udev event. That is something that only testing can tell us.

If all my above assumptions are true, either we just need to extend the delay between "modprobe" and "echo ...>.." commands, or split them to two different udev rules, which is the proven method with *other* devices.

---

### Post by swarup on 2014-03-02
> Anyway, before rebooting, I hope the following happened when you unplugged or replugged the modem, not by manually running the script (from terminal) -
"I made the requested change, and it did not crash the system. Both the files (Before.txt, After.txt) appeared immediately on the desktop."

Correct. It happened when I unplugged/replugged the modem.

> Assuming nothing has changed in the modeswitch file/rule, Reboot or Replug the modem (after a reasonable delay in-between, which is usually about 10-12 seconds) without rebooting, and see if the "Before.txt" and "After.txt" files are created. If not, check "lsusb" and "dmesg". Do you see the initial ID of the modem in lsusb not the switched one? Are there any error messages in dmesg?

When I unplug and replug the modem, both the "Before.txt" and "After.txt" files are created. From what you've written above ("If not, check "lsusb" and "dmesg"....") it sounds like you only needed me to do the lsusb and dmesg if the "Before.txt" and "After.txt" files were *not* created, so now Iwill move ahead from there...

---

### Post by swarup on 2014-03-02
I have just unplugged/replugged the modem on two successive occassions after booting up and manually getting online. Both times the system crashed, i.e. gave me a screen full of code and froze. Both times on reboot, the "Before.txt" and "After.txt" files were created i.e. present on the desktop on reboot. So I really do not know what is going on. I will move ahead with what you requested.

---

### Post by swarup on 2014-03-02
> If the ID is switched as expected, the files should be created as well. After that, check -
Code:

lsmod | grep option

Do you want me to execute the above, as well as the instructions following it, when I have already manually gotten online? Or upon booting the computer, before implementing the manual commands to get online?

---

### Post by swarup on 2014-03-02
> If all my above assumptions are true, either we just need to extend the delay between "modprobe" and "echo ...>.." commands, or split them to two different udev rules, which is the proven method with *other* devices. 

If that is the case, then why not we just try one or both of these ideas-- this may give us a rapid solution and allow us to skip all the testing.

---

### Post by varunendra on 2014-03-02
So may I assume the mode-switching is working as expected and the driver ("option") is loading automatically EVERY TIME (with maybe a few exceptions) when you unplug and replug? To make sure, run the "sudo modprobe -rv option" command to remove the driver (when it gets loaded) > delete the Before and After.txt files > replug > recheck "lsmod | grep option".

Assuming the above is okay, let's move to the final step - enabling the binding command again, with a bigger delay in-between.

Did you test the script with "sleep 4" ? If not, test it. This time the script should be -
```
#!/bin/bash
echo "Before Modprobe" > /home/dhananjoy/Desktop/Start.txt
/sbin/modprobe option
echo "After Modprobe" > /home/dhananjoy/Desktop/Modprobe.txt
sleep 4
echo 2020 4010 > /sys/bus/usb-serial/drivers/option1/new_id
echo "After binding" > /home/dhananjoy/Desktop/Attached.txt
```
If the system crashes again, reboot and check which files were created. At least two (Start.txt and Modprobe.txt) should be there.

If so, just increase the delay time to 10 seconds (sleep 10) and try again. With 10 second delay, any of three things may happen - 1) It'll work & we'll celebrate, 2) It won't work but won't crash either, 3) Nothing will change and system will crash again.

Depending upon which one happens, we'll decide our further (hopefully final) steps. Please try and let me know how it goes.

**[COLOR="#FF0000"]EDIT:[/COLOR]**
Just noticed your three posts in-between.
As I replied in my PM to yours, _Rapid mode is a luxury that I DO NOT HAVE_.
With a **[COLOR="#FF0000"]1 to 1.8 KB/s speed[/COLOR]**, most people in the entire world wouldn't even bother with browsing and replying posts. Like I mentioned before, my first post that we have been following was a TESTED solution, tested by myself with a similar 3G modem!

So IF it is failing at your end, we do need to test every step very thoroughly. And with you reporting that it crashed even while manually attempting to bind the driver, I am now wondering if any amount of testing or any kind of solution is going to guaranty a crash free operation.

In any case, losing patience is not going to yield anything.

---

### Post by swarup on 2014-03-02
> with you reporting that it crashed even while manually attempting to bind the driver
I must not have been clear...
The manual binding is TOTALLY dependable. It works every time. I am not having any problem getting online manually. That crash only happened because of removing and reconnecting the modem with your two files in place. If I remove those files, the manual method works flawlessly.

---

### Post by swarup on 2014-03-02
With a 4-second delay, the system crashed when I removed and reconnected the modem. Three files were created and were present on reboot: Start.txt, Modprobe.txt, Attached.txt. I have some things to take care of, but I will try the 10 second delay in a bit and see what happens.

---

### Post by swarup on 2014-04-21
Hi!

Just wanted to let you know I did get to try the 10 second delay before leaving there-- it didn't work either. So due to lack of time I had to abandon the attempt at automation and I taught Dhananjay how to get on line manually. It is pretty simple really, so I just practised it with him several times before leaving, and now that is what he does. This is the first time I think, that I could not get a technical issue like this solved in Ubuntu. It was just an issue of lack of time-- if we'd had a few more days to work on this together Varunji, I have no doubt that we would have got it. &#2310;&#2346;&#2325;&#2368; &#2360;&#2361;&#2366;&#2351;&#2340;&#2366; &#2325;&#2375; &#2354;&#2367;&#2319; &#2348;&#2361;&#2369;&#2340; &#2348;&#2361;&#2369;&#2340; &#2343;&#2344;&#2381;&#2351;&#2357;&#2366;&#2342; !

---

### Post by varunendra on 2014-04-21
No problem at all! I wish I could be of more help, but glad to know that you were able to teach him the manual steps and that he is comfortable with them now.

If you haven't already, I'd suggest to try 14.04 in live mode if and when you have time. I hope the support for that device would have been improved enough in it to not require the manual steps anymore. If not, I suggest to file a bug report and wait for a permanent fix.

---

### Post by swarup on 2014-04-22
Sure, your suggestion about 14.04 is well taken. Unfortunately, until I can get back there to Dhananjay's place (it'll probably be next February in around ten months), we won't be able to install 14.04 on his computer. I'm just glad I've got him up and running with 12.04! Thanks again. :)

---

