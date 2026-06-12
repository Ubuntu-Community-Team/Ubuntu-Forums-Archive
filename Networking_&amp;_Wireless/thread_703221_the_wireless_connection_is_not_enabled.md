---
title: "the wireless connection is not enabled"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by zigi87 on 2008-02-21
hi!
im new with ubuntu so i dont good working with the Terminal.
i installed ubuntu 7.10 on a pentium 4 2 Ghz with 2 HD's,
the first drive is 40 GB and it used for ubuntu, the other is 80 Gb and it used for Xp.
i have a wireless Pci card - Edimax ew7128g, i think its a ralink chip.

anyway, after installed ubuntu, the wireless worked with a few problems like disconnecting every 15-10 min'.
but now, a week after i installed ubuntu, the wireless isnt seen in the network screen, and the yellow/green/red light (back side of the computer) are off. 
but
when i boot to xp, the wireless working good.
i try to restart and power off the computer and also move the card to other slot, and nothing changed.
when i try to press the restricted drivers, it gives me an error that i need to have some packege (that i cannot download cos i dont have a connection)

a screenshot of the desktop, in the right side i had also wireless connection. where its gone?
and in the left its the device manager when i choose the ralink wireless card.
 
[http://img168.imageshack.us/img168/1088/screenshottl1.png](http://img168.imageshack.us/img168/1088/screenshottl1.png)

Thanks for any help!!!

---

### Post by ferdostar on 2008-02-21
Can you post the output of 
```
lspci
```
 and
```
iwconfig
```

---

### Post by zigi87 on 2008-02-21
lspci:
```

00:00.0 Host bridge: VIA Technologies, Inc. VT8753 [P4X266 AGP] (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 Network controller: RaLink RT2561/RT61 802.11g PCI
00:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX200] (rev b2)

```



iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by ferdostar on 2008-02-21
In fact you have to go to Synaptic (System->Administration->Synaptic Package Manager) and install the Ralink drivers (you have to have a wired connection). Otherwise you can download the driver from the site and install it manually. Can you post what is your situation, do you have a working wired connection, or you have to boot into windows and then to download it?

---

### Post by zigi87 on 2008-02-21
i have to boot to windows and then i can get to the net, useing wired connection is not an option right now..
is there any way i can download it in windows and install it on ubuntu? (save it on DOK?)

---

### Post by ferdostar on 2008-02-21
Two possibilities:
1) You can download the source code for you driver from the site booting in windows and compile it in ubuntu (you can check this [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73?highlight=%28WifiDocs%2FDriver%29) and this [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73?highlight=%28WifiDocs%2FDriver%29)
2) you can use ndiswrapper (using the windows driver of you card): go to [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net) download it into windows, and install it into ubuntu, then get the windows driver and istall it using ndiswrapper

---

