---
title: "Ndiswrapper won't recognize wireless network."
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by GingerKid on 2008-10-13
I'm probably going to seem incredibly computer illiterate for this but here goes.  Several months ago, I installed Ubuntu on my computer (Gutsy, I believe) and installed Ndiswrapper to be able to use my linksys wireless usb adapter.  I got it to recognize the adapter, but I couldn't find the network for some reason.  After extensive searching and playing with it, I gave up.  Now, I'm ready for round two, but I have no clue where to start.  Anyone have ideas of helpful advice?  I'm fairly new to non-windows systems, so I'm still trying to learn everything.

---

### Post by cariboo on 2008-10-13
Have you been using Ubuntu since your aborted wireless attempt? Or are you starting from scratch?

Jim

---

### Post by GingerKid on 2008-10-13
No, I've been dual-booting XP, and just gave up on ubuntu entirely for a while because I use this computer mostly for the internet.

---

### Post by GingerKid on 2008-10-14
Any ideas? Anyone?

---

### Post by iponeverything on 2008-10-14
Give us the ouput from "lspci" so that we can see if there is a native driver that you should be using.

---

### Post by GingerKid on 2008-10-15
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0f.0 USB Controller: NEC Corporation USB (rev 44)
00:0f.1 USB Controller: NEC Corporation USB 2.0 (rev 05)
00:10.0 Communication controller: Agere Systems LT WinModem (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

```

---

### Post by iponeverything on 2008-10-15
:)

Sorry about that.. lspci is not going to get the info that we need with a usb stick..

What pops up in about the last 20 of /var/log/messages when you put in the stick. Also what is model number and version number printed on the stick, or the label of the box it came in.

Also post the output of "lsusb" while the stick is in the computer.

thanks -

---

### Post by GingerKid on 2008-10-15
/var/log/messages shows this ```
Oct 15 13:30:35 home kernel: [  495.899312] usb 1-2: USB disconnect, address 2

Oct 15 13:30:53 home kernel: [  514.126795] usb 1-2: new full speed USB device using ohci_hcd and address 3

Oct 15 13:30:53 home kernel: [  514.329731] usb 1-2: config 1 has an invalid interface number: 1 but max is 0

Oct 15 13:30:53 home kernel: [  514.329742] usb 1-2: config 1 has no interface number 0

Oct 15 13:30:53 home kernel: [  514.335893] usb 1-2: configuration #1 chosen from 1 choice

Oct 15 13:31:10 home kernel: [  531.357200] usb 1-2: USB disconnect, address 3

Oct 15 13:31:17 home kernel: [  537.636060] usb 1-2: new full speed USB device using ohci_hcd and address 4

Oct 15 13:31:17 home kernel: [  537.838994] usb 1-2: config 1 has an invalid interface number: 1 but max is 0

Oct 15 13:31:17 home kernel: [  537.839005] usb 1-2: config 1 has no interface number 0

Oct 15 13:31:17 home kernel: [  537.845155] usb 1-2: configuration #1 chosen from 1 choice
```

The adapter is a Linksys WUSB11 version 2.5

lsusb: ```
Bus 004 Device 002: ID 0d49:7250 Maxtor 

Bus 004 Device 001: ID 0000:0000  

Bus 003 Device 001: ID 0000:0000  

Bus 002 Device 002: ID 05dc:a430 Lexar Media, Inc. 

Bus 002 Device 003: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse

Bus 002 Device 001: ID 0000:0000  

Bus 001 Device 002: ID 066b:2212 Linksys, Inc. WUSB11v2.5 802.11b Adapter

Bus 001 Device 001: ID 0000:0000  

```

---

### Post by iponeverything on 2008-10-16
> **GingerKid said:**
> /var/log/messages shows this ```
Oct 15 13:30:35 home kernel: [  495.899312] usb 1-2: USB disconnect, address 2

Oct 15 13:30:53 home kernel: [  514.126795] usb 1-2: new full speed USB device using ohci_hcd and address 3

Oct 15 13:30:53 home kernel: [  514.329731] usb 1-2: config 1 has an invalid interface number: 1 but max is 0

Oct 15 13:30:53 home kernel: [  514.329742] usb 1-2: config 1 has no interface number 0

Oct 15 13:30:53 home kernel: [  514.335893] usb 1-2: configuration #1 chosen from 1 choice

Oct 15 13:31:10 home kernel: [  531.357200] usb 1-2: USB disconnect, address 3

Oct 15 13:31:17 home kernel: [  537.636060] usb 1-2: new full speed USB device using ohci_hcd and address 4

Oct 15 13:31:17 home kernel: [  537.838994] usb 1-2: config 1 has an invalid interface number: 1 but max is 0

Oct 15 13:31:17 home kernel: [  537.839005] usb 1-2: config 1 has no interface number 0

Oct 15 13:31:17 home kernel: [  537.845155] usb 1-2: configuration #1 chosen from 1 choice
```

The adapter is a Linksys WUSB11 version 2.5

lsusb: ```
Bus 004 Device 002: ID 0d49:7250 Maxtor 

Bus 004 Device 001: ID 0000:0000  

Bus 003 Device 001: ID 0000:0000  

Bus 002 Device 002: ID 05dc:a430 Lexar Media, Inc. 

Bus 002 Device 003: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse

Bus 002 Device 001: ID 0000:0000  

Bus 001 Device 002: ID 066b:2212 Linksys, Inc. WUSB11v2.5 802.11b Adapter

Bus 001 Device 001: ID 0000:0000  

```

This should work out of the box with the native driver:
ref: [https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)

There are two things you can do, blacklist the native driver and use the windows driver or remove the windows driver from ndiswrapper and use the native driver.

In almost every case, using the native driver is better.

The native driver is: prism2_usb

After you remove the driver from ndiswrapper, do a:

modprobe prism2_usb 

and see what shows up in the logs.

---

### Post by GingerKid on 2008-10-16
I don't believe I have that native driver, I'm running Gutsy Gibbon.  I did remove the ndiwrapper driver and type modprobe prism2_usb into the terminal, and nothing happened, and I didn't see anything new in the log either.  I'm assuming it's the same log you mentioned before? /var/log/messages?  
Is it worth trying to get this to work or should I go through the hassle of upgrading to the new version?

---

### Post by GingerKid on 2008-10-16
I don't believe I have that native driver, I'm running Gutsy Gibbon.  I did remove the ndiwrapper driver and type modprobe prism2_usb into the terminal, and nothing happened, and I didn't see anything new in the log either.  I'm assuming it's the same log you mentioned before? /var/log/messages?  
Is it worth trying to get this to work or should I go through the hassle of upgrading to the new version?

EDIT: I was just reading through that link a little more thoroughly and it said prism2_usb should work out of the box, so what did I do wrong?

---

### Post by iponeverything on 2008-10-16
strange.

```
cd /var/log

```
unplug the device -- type:

```
ls -ltr

```
The logs at the bottom will be the ones most recently modified. Take a peak at those.

With the device still plugged in:

```
sudo rmmod prism2_usb
sudo modprobe prism2_usb
ls -ltr

```
Take peak at two logs at the bottom of the list again..

Try the ndiswrapper route again --- but this time blacklist prism2_usb to make sure that it is not getting in the way.

```
sudo echo "blacklist prism2_usb" >> /etc/modprobe.d/blacklist

```

---

### Post by GingerKid on 2008-10-17
```
cd /var/log
ls-ltr
```
I didn't notice anything useful in the last three logs listed when I did this step.

```
sudo rmmod prism2_usb
sudo modprobe prism2_usb
ls -ltr
```
daemon.log had this 
```
Oct 16 22:29:47 home NetworkManager: <debug> [1224214187.496918] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_usb_device_66b_2212_01190003_if1'). 
Oct 16 22:29:49 home NetworkManager: <info>  wlan0: Device is fully-supported using driver 'prism2_usb'. 
Oct 16 22:29:49 home NetworkManager: <WARN>  nm_device_802_11_wireless_set_mode(): error setting card wlan0 to Infrastructure mode: Operation not supported 
Oct 16 22:29:49 home NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 16 22:29:49 home NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 16 22:29:49 home NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Oct 16 22:29:49 home NetworkManager: <info>  Deactivating device wlan0. 
Oct 16 22:29:49 home NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Operation not supported 
Oct 16 22:29:49 home NetworkManager: <WARN>  nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device wlan0: Operation not supported 
Oct 16 22:29:49 home NetworkManager: <WARN>  nm_device_802_11_wireless_set_mode(): error setting card wlan0 to Infrastructure mode: Operation not supported 

```
and syslog had this
```
Oct 16 22:29:47 home kernel: [  252.604902] prism2usb_init: prism2_usb.o: 0.2.8 Loaded
Oct 16 22:29:47 home kernel: [  252.604910] prism2usb_init: dev_info is: prism2_usb
Oct 16 22:29:47 home kernel: [  252.608202] usbcore: registered new interface driver prism2_usb
Oct 16 22:29:47 home NetworkManager: <debug> [1224214187.496918] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_usb_device_66b_2212_01190003_if1'). 
Oct 16 22:29:49 home NetworkManager: <info>  wlan0: Device is fully-supported using driver 'prism2_usb'. 
Oct 16 22:29:49 home NetworkManager: <WARN>  nm_device_802_11_wireless_set_mode(): error setting card wlan0 to Infrastructure mode: Operation not supported 
Oct 16 22:29:49 home NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 16 22:29:49 home NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 16 22:29:49 home NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Oct 16 22:29:49 home NetworkManager: <info>  Deactivating device wlan0. 
Oct 16 22:29:49 home NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Operation not supported 
Oct 16 22:29:49 home NetworkManager: <WARN>  nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device wlan0: Operation not supported 
Oct 16 22:29:49 home NetworkManager: <WARN>  nm_device_802_11_wireless_set_mode(): error setting card wlan0 to Infrastructure mode: Operation not supported 

```

trying to blacklist prism2_usb got me this
```
sudo echo "blacklist prism2_usb" >> /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied
```

Also, at this point, my windows got infected with some spyware that my antivirus is having trouble with, so I'm considering formatting the whole drive and installing the newest version of ubuntu.  Do you think that would fix the problem or is it likely hardware related?

---

### Post by GingerKid on 2008-10-18
Ok, so I was screwing around with it today and when I clicked the network icon on the bar at the top of the screen, my wireless network suddenly showed up.  If I click on it though, it tried to connect for about 30 seconds and then gives up.  Signal strength is about 40%, and Windows never had a problem connecting.  No encryption yet either, I want to get it to actually connect before I do that.

---

### Post by GingerKid on 2008-10-19
Does it matter if all the computers on my network are Windows?  I'm not trying to do any filesharing, just access the internet through the wireless router.  Now my wireless network isn't showing up in the network drop down menu either.:confused:

---

### Post by GingerKid on 2008-10-20
Please?

---

