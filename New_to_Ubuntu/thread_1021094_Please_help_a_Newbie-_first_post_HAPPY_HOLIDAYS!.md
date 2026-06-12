---
title: "Please help a Newbie- first post HAPPY HOLIDAYS!"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by garpt on 2008-12-24
Hi!
 Merry xmas, Happy Holidays to all. I'm, as the forum suggests, a newbie to Linux/Ubuntu. I've used Windows since 1990, 3.1. My 4 yr old Alienware laptop bit the dust, bad HD and corrupted XP install, so being out of work,(read: broke), decided to take the plunge. I am very excited & impressed with Linux! Faster, more stable, and challenging so far.
Since I don't have a friend or buddy familiar w/ this OS, I have 2 issues I've encountered, and spent the better part of 6 days trying to learn on my own. Your assistance would be appreciated! I finally got my Canon printer, USB mouse, and Quickcam to go. I can't have any luck with my Logitech USB sound bar speakers and anything bluetooth. Most important to me is the logitech speakers. I've read that the 2.6.X.X version of Ubuntu has USB sound support, and I see it in the Alsa mixer. But when I select the USB output, it still plays the internal speakers. The USB speakers are getting power, cause the power light goes on when I plug them in to USB. If someone can help a newbie, (remember, I am learning but know little about source downloading and linux file systems)- I know how to download from Synaptics, but few commands from source. I would appreciate any help you can offer. 
I'll tackle the bluetooth issue next. THANKS!

---

### Post by kostkon on 2008-12-25
> **garpt said:**
> Hi!
 Merry xmas, Happy Holidays to all. I'm, as the forum suggests, a newbie to Linux/Ubuntu. I've used Windows since 1990, 3.1. My 4 yr old Alienware laptop bit the dust, bad HD and corrupted XP install, so being out of work,(read: broke), decided to take the plunge. I am very excited & impressed with Linux! Faster, more stable, and challenging so far.
Since I don't have a friend or buddy familiar w/ this OS, I have 2 issues I've encountered, and spent the better part of 6 days trying to learn on my own. Your assistance would be appreciated! I finally got my Canon printer, USB mouse, and Quickcam to go. I can't have any luck with my Logitech USB sound bar speakers and anything bluetooth. Most important to me is the logitech speakers. I've read that the 2.6.X.X version of Ubuntu has USB sound support, and I see it in the Alsa mixer. But when I select the USB output, it still plays the internal speakers. The USB speakers are getting power, cause the power light goes on when I plug them in to USB. If someone can help a newbie, (remember, I am learning but know little about source downloading and linux file systems)- I know how to download from Synaptics, but few commands from source. I would appreciate any help you can offer. 
I'll tackle the bluetooth issue next. THANKS!
Could you please tell which version of Ubuntu you are using?

---

### Post by garpt on 2008-12-25
Thanks for the reply kostkon. I'm using ver. 8.10.
Thanks.

---

### Post by newbee70 on 2008-12-25
> **garpt said:**
> Thanks for the reply kostkon. I'm using ver. 8.10.
Thanks.

garpt;

you can try this command "it will write a file to your desktop of everything your system has found and loaded, if you want, run it. Then open the file and look through it to make sure everything you had has been located." You can erase the file when your through with it.


terminal code: **dmesg >> ~/Desktop/dmesg.txt **

---

### Post by garpt on 2008-12-25
Hi newbie 70. That's a helpful command for diagnostics, thanx. But I don't know quite how to decipher it. This is some of what the file says:

 4.271936] Driver 'sd' needs updating - please use bus_type methods
[    4.272208] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.272252] sd 0:0:0:0: [sda] Write Protect is off
[    4.272258] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.272335] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.272568] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.272607] sd 0:0:0:0: [sda] Write Protect is off
[    4.272612] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.272696] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.272705]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.285178]  sda1 sda2 <<6>usb 3-2: configuration #1 chosen from 1 choice
[    4.317969]  sda5 >
[    4.318259] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.325962] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.325970] Uniform CD-ROM driver Revision: 3.20
[    4.326145] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.397375] usb 1-2.1: new full speed USB device using ehci_hcd and address 5
[    4.495312] usb 1-2.1: configuration #1 chosen from 1 choice
[    4.496225] hub 1-2.1:1.0: USB hub found
[    4.497513] hub 1-2.1:1.0: 3 ports detected
[    4.784323] usb 1-2.3: new full speed USB device using ehci_hcd and address 6
[    4.878000] usb 1-2.3: configuration #1 chosen from 1 choice
[    5.052021] usb 4-1: new low speed USB device using ohci_hcd and address 2
[    5.264069] usb 4-1: configuration #1 chosen from 1 choice
[    5.344994] usb 1-2.1.3: new full speed USB device using ehci_hcd and address 7
[    5.444418] usb 1-2.1.3: configuration #1 chosen from 1 choice
[    5.447583] usbcore: registered new interface driver hiddev
[    5.453370] input: Cypress Semiconductor USB Multi Remote Controller as /devices/pci0000:00/0000:00:03.1/usb3/3-2/3-2:1.0/input/input2
[    5.473242] input,hidraw0: USB HID v1.10 Mouse [Cypress Semiconductor USB Multi Remote Controller] on usb-0000:00:03.1-2
[    5.478037] input: Cypress Semiconductor USB Multi Remote Controller as /devices/pci0000:00/0000:00:03.1/usb3/3-2/3-2:1.1/input/input3
[    5.478192] input,hidraw1: USB HID v1.10 Device [Cypress Semiconductor USB Multi Remote Controller] on usb-0000:00:03.1-2
[    5.485168] input: 2.4Ghz Wireless Mouse as /devices/pci0000:00/0000:00:03.2/usb4/4-1/4-1:1.0/input/input4
[    5.485680] input,hidraw2: USB HID v1.11 Mouse [2.4Ghz Wireless Mouse] on usb-0000:00:03.2-1
[    5.489881] input: ORTEK USB Keyboard Hub as /devices/pci0000:00/0000:00:03.3/usb1/1-2/1-2.1/1-2.1.3/1-2.1.3:1.0/input/input5
[    5.490392] input,hidraw3: USB HID v1.10 Keyboard [ORTEK USB Keyboard Hub] on usb-0000:00:03.3-2.1.3
[    5.500192] input: ORTEK USB Keyboard Hub as /devices/pci0000:00/0000:00:03.3/usb1/1-2/1-2.1/1-2.1.3/1-2.1.3:1.1/input/input6
[    5.500691] input,hidraw4: USB HID v1.10 Device [ORTEK USB Keyboard Hub] on usb-0000:00:03.3-2.1.3
[    5.500722] usbcore: registered new interface driver usbhid
[    5.500727] usbhid: v2.6:USB HID core driver
[    5.597692] PM: Starting manual resume from disk
[    5.597698] PM: Resume from partition 8:5
[    5.597701] PM: Checking hibernation image.
[    5.598009] PM: Resume from disk failed.
[    5.714686] kjournald starting.  Commit interval 5 seconds
[    5.714698] EXT3-fs: mounted filesystem with ordered data mode.
[   12.263310] udevd version 124 started
[   12.901331] Linux agpgart interface v0.103
[   12.977285] agpgart-sis 0000:00:00.0: SiS chipset [1039/0648]
[   12.994072] agpgart-sis 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   13.068117] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00

  I assume it is "seeing" all the ports and devices. However, I see that some drivers need "updating" (sr and sd.) I'm not sure if these are part of the problem.Also, it is not naming the USB speakers, but appears to detect it in the port. So I don't know where to go from here. Thanks.

---

### Post by hibajugala on 2008-12-25
Merry Christmas!
and good luck!
not much help but i just wanted to wish you the best of luck with linux <3

:)

---

### Post by crazyness003 on 2008-12-26
Actually to get a list of your usb devices try this command
```
lsusb
```

---

### Post by garpt on 2008-12-26
Hi, using lsusb, I got:

garwyn@garwyn-laptop:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 014: ID 05a4:9862 Ortek Technology, Inc. 
Bus 005 Device 013: ID 04f9:0035 Brother Industries, Ltd 
Bus 005 Device 012: ID 046d:092f Logitech, Inc. QuickCam Express Plus
Bus 005 Device 011: ID 05a4:9837 Ortek Technology, Inc. 
Bus 005 Device 010: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0d62:00a1 Darfon Electronics Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 147a:e00c Formosa Industrial Computing, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
garwyn@garwyn-laptop:~$ 

So, it is being recognized. In fact, I now got an image on xawtv and cheese. The problem now is the cam won't be recognized or found by programs and apps I want to use it with like justin.tv (no camera found.) I think it might have something to do with Adobe Flash. Any ideas?
Thanks.

---

### Post by crazyness003 on 2008-12-26
I thought you were trying to get your speakers to work?
Either way, i have no idea what justin.tv is (sounds like an URL). If so, then yes it may use the Flash api to get your webcam to wirk in the webpage. You can configure you flash-plugin if you can access it here [Adobe Flash Player Settings Manager](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html) (its should be in the tab with the "eye in the monitor with no world behind it" ... 4th tab from the left)

Also, if you wanna get more info on your device per-say, you can use the device ID (heres an example)
```
Bus 005 Device 012: **ID 046d:092f** Logitech, Inc. QuickCam Express Plus
```
and google it for moar info, possible linux drivers, or links to other forums with more information. Unfortunately, im sort of a n00b myself, but i think i know enough just to break things.

Good luck, and tell us what you find. Thanks

---

### Post by garpt on 2008-12-31
Thanks, crazyness003. Been away for the holiday. Actually, it is a compound problem, should have made that clearer. Both are USB devices. Justin.tv is a networking site type thing, see and talk to other users. So, I need webcam and speakers. Internal speakers work on the site. The camera works through xawtv and cheese. I can view webpages with flash. So, that's where I am right now. Gonna try your two ideas tonight. I'll post anything that might help others. Thanks.
Gary

---

