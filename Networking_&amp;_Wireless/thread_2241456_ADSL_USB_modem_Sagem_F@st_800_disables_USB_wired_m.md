---
title: "ADSL USB modem Sagem F@st 800 disables USB wired mouse (conflict, interference)"
date: 2014-08-26
forum: Networking &amp; Wireless
---

### Post by trusalvo on 2014-08-26
When I use my ADSL USB modem Sagem F@st 800 with Lubuntu 14.04 Trusty in  my laptop my USB wired mouse doesn't work (I have to use the touchpad).  Any idea of the reason & a solution for this, please?

---

### Post by varunendra on 2014-08-27
Welcome to the forums trusalvo!

Please open a terminal (Ctrl-Alt-T) and post back the outputs of the following Before and After connecting the modem -
```
lsusb
xinput
```

And outputs of the following immediately after the problem occurs -
```
tail -40 /var/log/syslog
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by trusalvo on 2014-09-02
Thanks

I use Lubuntu in a Live USB. Normally I plug the USB ADSL modem before I turn the laptop on. This time, as requested, I plug it after that (but later, as shown below, before turning the computer on).

The results:

**Before plugging the modem:**
```
ubuntu@ubuntu:~$ lsusb
Bus 002 Device 004: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 046d:c309 Logitech, Inc. Internet Keyboard
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse             id=10    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Logitech USB Keyboard              id=12    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=14    [slave  pointer  (2)]
&#9116;   &#8627; ALPS PS/2 Device                            id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Chicony USB 2.0 Camera                      id=9    [slave  keyboard (3)]
    &#8627; Logitech Logitech USB Keyboard              id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Toshiba input device                        id=16    [slave  keyboard (3)]
ubuntu@ubuntu:~$
``` 

**After plugging the modem (I can still use my wired USB mouse but I cannot connect to the internet):**
```
ubuntu@ubuntu:~$ lsusb
Bus 002 Device 004: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 046d:c309 Logitech, Inc. Internet Keyboard
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 005 Device 004: ID 1110:9031 Analog Devices Canada, Ltd (Allied Telesyn) ADSL LAN Adapter
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse             id=10    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Logitech USB Keyboard              id=12    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=14    [slave  pointer  (2)]
&#9116;   &#8627; ALPS PS/2 Device                            id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Chicony USB 2.0 Camera                      id=9    [slave  keyboard (3)]
    &#8627; Logitech Logitech USB Keyboard              id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Toshiba input device                        id=16    [slave  keyboard (3)]
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ tail -40 /var/log/syslog
Sep  2 07:26:42 ubuntu kernel: [  215.332058] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:42 ubuntu kernel: [  215.432052] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:45 ubuntu ntpd_intres[1985]: host name not found: 0.ubuntu.pool.ntp.org
Sep  2 07:26:45 ubuntu ntpd_intres[1985]: host name not found: 1.ubuntu.pool.ntp.org
Sep  2 07:26:45 ubuntu ntpd_intres[1985]: host name not found: 2.ubuntu.pool.ntp.org
Sep  2 07:26:45 ubuntu ntpd_intres[1985]: host name not found: 3.ubuntu.pool.ntp.org
Sep  2 07:26:45 ubuntu ntpd_intres[1985]: host name not found: ntp.ubuntu.com
Sep  2 07:26:46 ubuntu kernel: [  219.732047] usbatm_submit_urb: 42 callbacks suppressed
Sep  2 07:26:46 ubuntu kernel: [  219.732070] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:46 ubuntu kernel: [  219.832063] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:47 ubuntu kernel: [  219.932041] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:47 ubuntu kernel: [  220.032041] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:47 ubuntu kernel: [  220.132048] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:47 ubuntu kernel: [  220.232053] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:47 ubuntu kernel: [  220.332072] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:47 ubuntu kernel: [  220.432075] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:47 ubuntu kernel: [  220.532052] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:47 ubuntu kernel: [  220.632057] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:52 ubuntu kernel: [  224.932040] usbatm_submit_urb: 42 callbacks suppressed
Sep  2 07:26:52 ubuntu kernel: [  224.932063] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:52 ubuntu kernel: [  225.032050] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:52 ubuntu kernel: [  225.132046] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:52 ubuntu kernel: [  225.232045] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:52 ubuntu kernel: [  225.332042] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:52 ubuntu kernel: [  225.432069] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:52 ubuntu kernel: [  225.532051] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:52 ubuntu kernel: [  225.632071] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:52 ubuntu kernel: [  225.732057] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:52 ubuntu kernel: [  225.832046] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:57 ubuntu kernel: [  230.132056] usbatm_submit_urb: 42 callbacks suppressed
Sep  2 07:26:57 ubuntu kernel: [  230.132080] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:57 ubuntu kernel: [  230.232051] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:57 ubuntu kernel: [  230.332065] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:57 ubuntu kernel: [  230.432078] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:57 ubuntu kernel: [  230.532065] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:57 ubuntu kernel: [  230.632081] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:57 ubuntu kernel: [  230.732051] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:57 ubuntu kernel: [  230.832049] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:58 ubuntu kernel: [  230.932068] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
Sep  2 07:26:58 ubuntu kernel: [  231.032049] ATM dev 0: usbatm_submit_urb: urb 0xe88bc3c0 submission failed (-28)!
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo pppd call ueagle-atm
Plugin pppoatm.so loaded.
ubuntu@ubuntu:~$
```

**After turning the computer off, and switching it on again (having the USB modem plugged -I cannot use my USB wired mouse but I can connect to the internet-) I get:**
```
ubuntu@ubuntu:~$ lsusb
Bus 002 Device 005: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 046d:c309 Logitech, Inc. Internet Keyboard
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 005 Device 002: ID 1110:9031 Analog Devices Canada, Ltd (Allied Telesyn) ADSL LAN Adapter
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Logitech USB Keyboard              id=11    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=13    [slave  pointer  (2)]
&#9116;   &#8627; ALPS PS/2 Device                            id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Chicony USB 2.0 Camera                      id=9    [slave  keyboard (3)]
    &#8627; Logitech Logitech USB Keyboard              id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Toshiba input device                        id=15    [slave  keyboard (3)]
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ tail -40 /var/log/syslog
Sep  2 07:36:32 ubuntu ntpd[2059]: proto: precision = 1.467 usec
Sep  2 07:36:32 ubuntu ntpd[2059]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Sep  2 07:36:32 ubuntu ntpd[2059]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Sep  2 07:36:32 ubuntu ntpd[2059]: Listen and drop on 1 v6wildcard :: UDP 123
Sep  2 07:36:32 ubuntu ntpd[2059]: Listen normally on 2 lo 127.0.0.1 UDP 123
Sep  2 07:36:32 ubuntu ntpd[2059]: Listen normally on 3 lo ::1 UDP 123
Sep  2 07:36:32 ubuntu ntpd[2059]: peers refreshed
Sep  2 07:36:32 ubuntu ntpd[2059]: Listening on routing socket on fd #20 for interface updates
Sep  2 07:36:32 ubuntu ntpd[2059]: Deferring DNS for 0.ubuntu.pool.ntp.org 1
Sep  2 07:36:32 ubuntu ntpd[2059]: Deferring DNS for 1.ubuntu.pool.ntp.org 1
Sep  2 07:36:32 ubuntu ntpd[2059]: Deferring DNS for 2.ubuntu.pool.ntp.org 1
Sep  2 07:36:32 ubuntu ntpd[2059]: Deferring DNS for 3.ubuntu.pool.ntp.org 1
Sep  2 07:36:32 ubuntu ntpd[2059]: Deferring DNS for ntp.ubuntu.com 1
Sep  2 07:36:32 ubuntu ntpd_intres[1735]: parent died before we finished, exiting
Sep  2 07:36:34 ubuntu ntpd_intres[2068]: host name not found: 0.ubuntu.pool.ntp.org
Sep  2 07:36:34 ubuntu ntpd_intres[2068]: host name not found: 1.ubuntu.pool.ntp.org
Sep  2 07:36:34 ubuntu ntpd_intres[2068]: host name not found: 2.ubuntu.pool.ntp.org
Sep  2 07:36:34 ubuntu ntpd_intres[2068]: host name not found: 3.ubuntu.pool.ntp.org
Sep  2 07:36:34 ubuntu ntpd_intres[2068]: host name not found: ntp.ubuntu.com
Sep  2 07:36:34 ubuntu dbus[1047]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Sep  2 07:36:34 ubuntu udisksd[2277]: udisks daemon version 2.1.3 starting
Sep  2 07:36:35 ubuntu dbus[1047]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Sep  2 07:36:35 ubuntu udisksd[2277]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Sep  2 07:36:40 ubuntu NetworkManager[1396]: <info> WiFi hardware radio set enabled
Sep  2 07:36:40 ubuntu kernel: [   42.345096] EXT4-fs (sdb2): mounting ext2 file system using the ext4 subsystem
Sep  2 07:36:40 ubuntu kernel: [   42.352969] EXT4-fs (sdb2): warning: mounting unchecked fs, running e2fsck is recommended
Sep  2 07:36:40 ubuntu kernel: [   42.355566] EXT4-fs (sdb2): mounted filesystem without journal. Opts: (null)
Sep  2 07:36:40 ubuntu udisksd[2277]: Mounted /dev/sdb2 at /media/ubuntu/edited1 on behalf of uid 999
Sep  2 07:36:40 ubuntu kernel: [   42.420228] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
Sep  2 07:36:40 ubuntu udisksd[2277]: Mounted /dev/sdb1 at /media/ubuntu/EDITED2 on behalf of uid 999
Sep  2 07:36:42 ubuntu kernel: [   44.755580] usb 5-1: [ueagle-atm] modem operational
Sep  2 07:36:45 ubuntu NetworkManager[1396]: <info> (ueagle-atm0): carrier now ON (device state 20)
Sep  2 07:36:45 ubuntu NetworkManager[1396]: <info> (ueagle-atm0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Sep  2 07:36:54 ubuntu wpa_supplicant[1702]: wlan0: CTRL-EVENT-SCAN-STARTED 
Sep  2 07:37:36 ubuntu ntpd_intres[2068]: host name not found: 0.ubuntu.pool.ntp.org
Sep  2 07:37:36 ubuntu ntpd_intres[2068]: host name not found: 1.ubuntu.pool.ntp.org
Sep  2 07:37:36 ubuntu ntpd_intres[2068]: host name not found: 2.ubuntu.pool.ntp.org
Sep  2 07:37:36 ubuntu ntpd_intres[2068]: host name not found: 3.ubuntu.pool.ntp.org
Sep  2 07:37:36 ubuntu ntpd_intres[2068]: host name not found: ntp.ubuntu.com
Sep  2 07:38:31 ubuntu udisksd[2277]: Mounted /dev/sda3 at /media/ubuntu/EDITED3 on behalf of uid 999
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo pppd call ueagle-atm
Plugin pppoatm.so loaded.
ubuntu@ubuntu:~$
```

---

### Post by varunendra on 2014-09-02
How many external USB ports do you have? Three?

It seems one of the internal USB 1.1 hubs is being shared between the mouse and the modem, while some of the available hubs are unused (which is normal, hub nos. 3,4,6 are showing since the chip has them in it, but physically they may not be connected to any ports outside or any devices inside) -

> **trusalvo said:**
> **After plugging the modem (I can still use my wired USB mouse but I cannot connect to the internet):**
```
ubuntu@ubuntu:~$ lsusb
[COLOR="#800000"]Bus 002 Device 004: ID 058f:6387 Alcor Micro Corp. Flash Drive
**Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]**
[COLOR="#006400"]Bus 007 Device 002: ID 046d:c309 Logitech, Inc. Internet Keyboard
**Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]**
***[COLOR="#808080"]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]***
[COLOR="#FF0000"]Bus 005 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 005 _Device 004_: ID 1110:9031 Analog Devices Canada, Ltd (Allied Telesyn) ADSL LAN Adapter
**Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]**
[COLOR="#0000CD"]Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
[B]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
[I][COLOR="#808080"]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR][/I][/B]
ubuntu@ubuntu:~$ 
```
As you can see, hub no. 5 (a USB 1.1 hub) is shared between the mouse and the modem. Whichever was connected first (has a lower 'device no.') kept working while the later one was probably too much an overhead to deal with for the super slow USB 1.1 hub -

> **trusalvo said:**
> **After turning the computer off, and switching it on again (having the USB modem plugged -I cannot use my USB wired mouse but I can connect to the internet-) I get:**
```
[COLOR="#FF0000"]Bus 005 _Device 003_: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 005 Device 002: ID 1110:9031 Analog Devices Canada, Ltd (Allied Telesyn) ADSL LAN Adapter
**Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub**[/COLOR]
```

One of the two available USB 2 hubs is being used for internal webcam, the other for your Live flash drive. None of these can work properly on a USB 1.1 hub (video devices need higher speeds, and the flash drive to run the OS properly).

Which port is connected to which hub internally - is usually controlled dynamically from inside the USB chip. Usually whichever of the connected devices demands higher speeds, is connected to USB 2 hub, the others to USB 1. If there are more high speed devices than available USB 2 hubs/ports, it ends up being a 'come first get first' race.

Bottom line - probably you won't face the problem if running the OS from internal hard disk, and the external USB 2 port is available for the modem, so it doesn't have to share the same hub with another device. Or, use a USB hub to connect both your external mouse and keyboard to it, so they are on one hub, the modem on the other.

At any time, to see which device is connected to which bus and at what speed, you can use the command -
```
lsusb -t
```

---

### Post by trusalvo on 2014-09-02
Thanks. I see ...
I have 4 external USB sockets:
Left: one for wired USB keyboard, one for USB flash drive.
Right: one for wired USB mouse, one for USB ADSL modem.

---

### Post by varunendra on 2014-09-03
Oh yeah, 4 ports, sorry. I had missed the keyboard while initially typing the post. All the four devices, as well as the buses/hubs they are on are highlighted in the quoted part though.

The testing/verification steps are same, please check as suggested and confirm if it indeed seems to be a hub-sharing problem.

---

### Post by trusalvo on 2014-09-03
Thanks

```
 lsusb -t
```
Before plugging the USB modem:
```
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 1: Dev 2, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 2: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/6p, 480M
    |__ Port 6: Dev 4, If 0, Class=Mass Storage, Driver=usb-storage, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M
    |__ Port 3: Dev 2, If 0, Class=Video, Driver=uvcvideo, 480M
    |__ Port 3: Dev 2, If 1, Class=Video, Driver=uvcvideo, 480M
```
After plugging the modem:
```
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 1: Dev 2, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 4, If 0, Class=Communications, Driver=ueagle-atm, 12M
    |__ Port 1: Dev 4, If 1, Class=CDC Data, Driver=ueagle-atm, 12M
    |__ Port 1: Dev 4, If 2, Class=CDC Data, Driver=ueagle-atm, 12M
    |__ Port 2: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/6p, 480M
    |__ Port 6: Dev 4, If 0, Class=Mass Storage, Driver=usb-storage, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M
    |__ Port 3: Dev 2, If 0, Class=Video, Driver=uvcvideo, 480M
    |__ Port 3: Dev 2, If 1, Class=Video, Driver=uvcvideo, 480M
```
After rebooting with the modem plugged:
```
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 1: Dev 2, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class=Communications, Driver=ueagle-atm, 12M
    |__ Port 1: Dev 2, If 1, Class=CDC Data, Driver=ueagle-atm, 12M
    |__ Port 1: Dev 2, If 2, Class=CDC Data, Driver=ueagle-atm, 12M
    |__ Port 2: Dev 3, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/6p, 480M
    |__ Port 6: Dev 5, If 0, Class=Mass Storage, Driver=usb-storage, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M
    |__ Port 3: Dev 2, If 0, Class=Video, Driver=uvcvideo, 480M
    |__ Port 3: Dev 2, If 1, Class=Video, Driver=uvcvideo, 480M
```
I don't have an (external) USB hub.

---

