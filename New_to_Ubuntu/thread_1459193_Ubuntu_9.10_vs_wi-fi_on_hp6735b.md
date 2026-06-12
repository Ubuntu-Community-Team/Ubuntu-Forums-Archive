---
title: "Ubuntu 9.10 vs wi-fi on hp6735b"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by s.v.z on 2010-04-21
Good time of day everyone! Yesterday I made my first attempt to switch to Ubuntu Linux and I encountered the following problem: my wi-fi adapter seems to not have been detected by the system. The iwconfig tool says that there are no wireless devices on board. 

What`s even worse is that I don`t know how to discover its model. Is there anything similar to device manager in win?

And one more thing: there is a "wireless button" on board which is supposed to turn wi-fi and bluetooth on/off. The tooth works fine, but I don`t get any messages about wi-fi. Still, the indicator shines brightly.

---

### Post by P4man on 2010-04-21
Hi, and welcome.

To determine the exact type of wifi card, open a terminal and type

```
lspci
```

(LSPCi in lowercase). Copy paste the output here.

That time-of-day greeting made me chuckle btw :)

---

### Post by s.v.z on 2010-04-21
here`s what it says:

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
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
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0a:06.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)

---

### Post by P4man on 2010-04-21
Hmm, I see no wifi card in that list. If you toggle the wifi button of your laptop, does the output change?

---

### Post by s.v.z on 2010-04-21
No, it doesn`t change. The one I posted is when the button`s turned on.

---

### Post by P4man on 2010-04-21
And when its turned off, you get the same output, no wireless network card in the output right?

Maybe its connected internally to the USB bus, would surprise me, but easy to check. Can you post the output of

```

lsusb
```

(again check with the wifi toggle on and off, just in case)

---

### Post by s.v.z on 2010-04-21
Looks like you`re right, hehe :)

svz@svz-hp6735b:~$ lsusb
Bus 006 Device 004: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b059 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 08ff:2810 AuthenTec, Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by P4man on 2010-04-21
Also, I remember on my acer notebook I encountered a bug on a previous ubuntu where the kill switch (wifi button) would kill the wifi, but not reenable it. I had to boot windows to reenable it, then reboot in to ubuntu to have the wifi radio on. Perhaps you can test this? if you still have windows, boot windows, make sure you have a wifi signal, then reboot in ubuntu, DONT TOUCH the kill switch, and run lspci and lsusb again.

edit: posts crossed, let me check your output first

---

### Post by P4man on 2010-04-21
Bah, they obfuscate what chipset they are using.. thats not helpful HP!
Lets see if you can get some more information by entering this:

```
lsusb -vvv
```

---

### Post by s.v.z on 2010-04-21
Damn, looks like the part of the output we need gets lost high in the skies (I just can`t scroll it any higher). How do I make it write the output to some file?

---

### Post by P4man on 2010-04-21
Same as in windows :)
```
lsusb -vvv > usbinfo.txt
```

puts the output in the usbinfo.txt file in your homefolder (assuming you run it from the homefolder).

Also can you tell me what, if anything happens to both lspci and lsusb output when you hit the toggle switch, and after a fresh boot without having touched the toggle? Some links I found on google on a similar laptop as yours show the HP integrated module in lsusb as well as a broadcom wifi module in lspci, but the latter might get "killed" by the kill switch.

So here is another thing to try: hook it up to wired network, boot windows, check wifi is on, reboot, then go to system > adminstration > hardware drivers. You have to be online for that to work I think. If its a broadcom, it may ask to install restricted drivers.

---

### Post by s.v.z on 2010-04-21
Here goes the first part:

```

Bus 006 Device 004: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x03f0 Hewlett-Packard
  idProduct          0x171d Wireless (Bluetooth + WLAN) Interface [Integrated Module]
  bcdDevice            1.00
  iManufacturer           1 Broadcom Corp
  iProduct                2 HP Integrated Module
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          216
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 

```

When I turn the switch off the wireless adapter disappears from lsusb. The lspci output doesn`t change.

---

### Post by s.v.z on 2010-04-21
After rebooting I got this in lspci:

```

...
09:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
```

and unfortunately I`ve got no Windows to boot.

---

### Post by P4man on 2010-04-21
Ahh.. as i thought. The dreaded broadcom. And maybe a bug with the killswitch as well, does the card reappear when you press the killswitch twice? If not, please do file a bug report.

Anyway,  broadcom wifi is a bit of a PITA on linux,  but usually can be made to work. with the card showing up in lspci, and the laptop connected to the internet, try running "hardware drivers" from system > administation menu.

If that doesnt suggest a proprietary driver for the wifi, then follow the instructions here:
[http://ubuntuforums.org/showthread.php?t=1368699&highlight=b43-fwcutter](http://ubuntuforums.org/showthread.php?t=1368699&highlight=b43-fwcutter)

---

### Post by s.v.z on 2010-04-21
Aha, it works! But now it can`t be turned off with kill switch. It affects bluetooth only. Thanks for help! Hope someday I`ll join you in this fight against human ignorance :) 
Again, thanks a lot!

edit: Damn, guess I was too fast about it! Now it won`t connect :(

---

### Post by P4man on 2010-04-21
Well, we're getting somewhere at least. Can you be a bit more "-vvv" (verbose) :) ? What did you do first that made something work, and what isnt working now?

Also, as I understand it your killswitch is bugged, like mine was on my acer. It will kill the wifi and not turn it on again until you reboot. Thats rather annoying, but I dont have a quick fix for that, thats why you should file a bug report. In the meanwhile you should be able to toggle the wifi on and off using the gnome panel, the wifi indicator top right, if you right click it, you can turn wifi on and off (assuming its not "killed" by the killswitch).

---

### Post by s.v.z on 2010-04-21
So, lets sum up.

All I had to do was to turn the killswitch on, reboot, install the proprietary broadcom driver instead of the one that comes with Ubuntu, reboot again and enjoy. And never touch the "wireless button" again. :)

What confused me is that there was no wi-fi device listed when I tried to boot with wireless off, and turn it on after that. (Have to boot with wireless on already)
And the second thing is that the device doesn`t disappear from the list when I turn it off and the "network control" applet still shows some available networks, and behaves as if wi-fi is on, though it is not: you see some networks and you may try to connect to one, but you`ll get a "connection failed" error until next reboot. Hope it`ll help someone else.

Thanks a lot.
[SOLVED]

---

### Post by P4man on 2010-04-21
Yep, its a "lucky" coincidence I was once  bitten by the same problem with the killswitch or this could have become a very long thread indeed. Its a pretty natural thing to do, press that switch when its not working and who would guess after pressing you gotta reboot :S

Anyway, I would strongly encourage you to file a bug report, because fixing the killswitch is probably not very hard for the developers (certainly easier than convincing broadcom to opensource their stuff). This page gives a lot of info on how to report bugs:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Also, you might want to try ubuntu 10.04 which is about ot be released. If you're really lucky, they fixed that issue in that. You can download the beta now;[http://www.ubuntu.com/testing/lucid/beta2](http://www.ubuntu.com/testing/lucid/beta2)

Just running the liveCD may give a clue if the killswitch was solved. Even if it doesnt come with the broadcom drivers, using lspci and lsusb should tell you if you can turn the device on again.

Anyway, good luck with ubuntu and dont hesitate to post any other questions and problems you will surely encounter!

---

