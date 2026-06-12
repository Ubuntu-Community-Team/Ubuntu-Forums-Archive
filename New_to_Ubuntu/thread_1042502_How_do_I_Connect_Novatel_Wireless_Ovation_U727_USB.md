---
title: "How do I: Connect Novatel Wireless Ovation U727 USB"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by TechDragon on 2009-01-17
Hello,

I have a USB Sprint Novatel Wireless Ovation U727 Cellular access device.

I am using KDE 4.2 RC1 and the network manager sees the device but asks me a lot of configuration questions which I cant answer. 

Does anyone have one of these? Could you tell me how to configure it?

Your assistance is always appreciated.

---

### Post by Morpheun on 2009-01-17
I'm not personally familiar with the device, however, Sprint has a section on their website [here]("http://www.nextel.com/en/software_downloads/mobile_broadband/novatel_ovation_u727.shtml") that covers installing this specifc unit in linux.

However, if Network Manager does detect it, figuring out the correct answers for those specifc questions is probably the best answer. Any specific one you're stuck on?

---

### Post by TechDragon on 2009-01-17
when i plug the device in it tries to connect to the net.  Kubuntu reports "unmanaged" then "Disconnected"

I have added screenshots of the two detailed config pages, Ubuntu and Kubuntu have never had a problem connecting to the device, I upgraded kde and now it is asking me config questions.

---

### Post by TechDragon on 2009-01-18
i re-installed Ubuntu and then copied the config settings from the network manager.

---

### Post by TechDragon on 2009-01-18
This did not help, Ubuntu has check marks to allow where Kubuntu has checkmarks to dissallow, suggesting that they are on by default.

Any Ideas?

---

### Post by altonbr on 2009-08-10
My Uncle uses this device for when he travels between the US and Canada.

I installed Ubuntu 9.04 on his laptop and the device was detected immediately.

A couple days later, the device started to be mounted as a USB drive with no Internet.

Can anyone help?

---

### Post by cozmicharlie on 2009-08-10
> **TechDragon said:**
> Hello,

I have a USB Sprint Novatel Wireless Ovation U727 Cellular access device.

I am using KDE 4.2 RC1 and the network manager sees the device but asks me a lot of configuration questions which I cant answer. 

Does anyone have one of these? Could you tell me how to configure it?

Your assistance is always appreciated.

Did you activate it in Windows?

I use this card and it just works when plugged in.  I use gnome but I think it is not much different on kde.  It will sometimes mount when you plug it in (you will see it mounted as a drive when you first plug it in).  This has something to do with how it is handled in Windows.  All you need to do is unmount it (right click on the icon on your desktop and "eject").  Then just wait and it will be detected.  If you have it activated then it should just work and you don't have to do any configuring.  All you probably want to do is right click on the network applet>edit connections>mobile broadband and check "connect automatically.

---

### Post by altonbr on 2009-09-05
Bump.

The 'Sprint Novatel Wireless Ovation u727' takes about 5 minutes to set itself up in Ubuntu after it was mounted as a USB drive.

Here's the 'dmesg' specifically when the USB drive is unmounted and the device is mounted as a broadband mobile device:

```
[  733.260053] usb 2-2: USB disconnect, address 3
[  733.289889] scsi 7:0:0:0: rejecting I/O to dead device
[  734.737050] usb 2-2: new full speed USB device using uhci_hcd and address 4
[  734.908379] usb 2-2: configuration #1 chosen from 1 choice
[  734.926350] scsi8 : SCSI emulation for USB Mass Storage devices
[  734.926477] usb-storage: device found at 4
[  734.926479] usb-storage: waiting for device to settle before scanning
[  734.991779] usbcore: registered new interface driver usbserial
[  734.991796] USB Serial support registered for generic
[  734.991848] usbcore: registered new interface driver usbserial_generic
[  734.991850] usbserial: USB Serial Driver core
[  735.001099] USB Serial support registered for GSM modem (1-port)
[  735.001145] option 2-2:1.0: GSM modem (1-port) converter detected
[  735.001251] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[  735.001267] option 2-2:1.1: GSM modem (1-port) converter detected
[  735.001319] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  735.001334] option 2-2:1.2: GSM modem (1-port) converter detected
[  735.001391] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  735.001406] option 2-2:1.3: GSM modem (1-port) converter detected
[  735.001455] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB3
[  735.001472] usbcore: registered new interface driver option
[  735.001475] option: v0.7.2:USB Driver for GSM modems
[  739.926036] usb-storage: device scan complete
[  739.929062] scsi 8:0:0:0: Direct-Access     Novatel  MMC Storage      2.31 PQ: 0 ANSI: 2
[  739.945106] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[  739.945220] sd 8:0:0:0: Attached scsi generic sg2 type 0
[  741.432941] PPP BSD Compression module registered
[  741.456207] PPP Deflate Compression module registered

```

---

### Post by macheted01 on 2009-10-02
Hey everyone,
New to the forum here and new to Ubuntu. I have a Novatel U727 through Sprint, that I am trying to use on a new Dell mini with Ubuntu 8.04 Hardy Heron. This U727 is active and has always been used on my other computers (windows xp).
I have found the support page on Sprint for this but does me no good, since I am clueless to alot of the terminolgy used for ubuntu. I also tried a few of the things discussed here on these forums. For those of you that have had success in using the U727 on Ubuntu and have some time to dedicate to breaking this down for me, would be greatly appreciated. Any help would be great. Thanks in advance.
Oh yeah, I am able to plug the U727 in and it seems to recognized it as I can access the folder inside, but it will not run the setup. Green light is on, on the U727.

---

### Post by scorp123 on 2009-10-02
> **altonbr said:**
>  A couple days later, the device started to be mounted as a USB drive with no Internet. Right-click on that drive icon and "Eject" it. Yes, I know. It won't jump out of the USB port :D ... But now it will be rescanned again and should now behave as modem again.

Most of those USB 3G modems do that: They come up as USB drive first. That drive part contains Windows drivers. As soon as you soft-eject that drive part, the actual modem part should become active. My Novatel MC950D does the same thing.

---

### Post by brianmck on 2009-10-07
I use this modem in Canada on the Bell network. After activating it in windows it works automatically in Jaunty. But it does take 5 minutes to switch from storage mode. To fast track this use 
sudo eject /sr1
in a terminal window.

It works this way on my laptop  but on my desktop with an asus m/b (sorry don't have the model no) it has some conflicts withe the usb or nvidia drivers and disconnects after a while - have not been able to sort it out.

brian

---

