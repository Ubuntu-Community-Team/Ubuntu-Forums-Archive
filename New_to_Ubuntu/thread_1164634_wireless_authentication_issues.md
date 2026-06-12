---
title: "wireless authentication issues"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by tomreid on 2009-05-19
Hi

I've been using Ubuntu for less than a day, really enjoying it. I've been able to resolve many problems just by searching the forums. 

There is one issue I am stuck with though.

I had the WIFI working this morning, it worked for around an hour, then cut out and I can't get the system to connect again. Works fine with an ethernet connection plugged right in from the airport.

I used the system (sorry forgot it's name) whereby I established the wifi card driver by using the windows ".inf" file. Don't think this is a drivers issue, as I can click on the top right of the screen and it shows me all the available wireless networks I'd expect to see at my house.

When I try to connect to my network, the system shows a graphic in the top right hand corner of the screen, displays two green circles with a red line going between them (I'm assuming this is the graphic for "trying to connect to network") but it does this for around 30 seconds and then reports "wifi network not connected". I know this is not true as I have three macs all working no problem off the wifi network here.

I've been in and out of "system" / "preferences" / "network connections" many times and the password type "wpa and wpa personal" is what the airport is expecting, but when I look at the password, the OS is somehow substituting it's own collection of randon letters and numbers, rather than the password for the network.

So i'm guessing some other programme is interfering with the password, but i don't know how to stop it.

thanks

Tom.

---

### Post by Miljet on 2009-05-19
Try opening a terminal (Applications -> Accessories -> Terminal) and copy/paste the following:

```
cat /etc/network/interfaces
```

If it has anything other than the following two lines,
auto lo
iface lo inet loopback
you need to edit the file.

First make a backup of the file

```
sudo cp /etc/network/interfaces /etc/network/interfaces.backup
```

Then open the file for editing

```
gksu gedit /etc/network/interfaces
```

Delete everything except the above lines. Save the file, close the terminal, and reboot your computer. Now when you select the proper network, you should be able to input the correct WPA password. If I remember right, it will then ask for your regular password (the same one you log in with.)  After the first time, it should automatically connect every time you reboot.

No guarantees, but that worked for me.

---

### Post by tomreid on 2009-05-20
Hi

It only had the two lines : auto lo
iface lo inet loopback

Not sure what to do next, I've done a lot of searching through the forums but can't find an answer. It's like the system is somehow changing or mis translating the password I input

cheers

Tom

---

### Post by Thingymebob on 2009-05-20
This may help, may not. One system i had just wouldn't play with my wireless network on the channel it was set to (similar thing just wouldn't accept the password), changed the channel in the router config and all was fine.

---

### Post by 3rdalbum on 2009-05-20
What is the wireless chipset you are using?

Please post the output of these commands:

```
lspci
```

```
lsusb
```

I don't trust ndiswrapper (the software you used to run the Windows driver in Ubuntu), and I only recommend it when there is no native Linux driver available. If there is a native Linux driver that is available and works well enough with your card, it would be preferable to use that.

---

### Post by tomreid on 2009-05-20
Hi  

The command "lspci" resulted in:

tom@tom-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev ff)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 32M/64M] (rev a1)
02:05.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)

The command "lsusb" resulted in:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I'm thinking also that there is something also in the way this system is handling passwords, as when I look in the wireless section of the "Network Preferences" app, when I click the option to make the password visible, all I see is a seemingly randoom collection of letters and numbers and not my WEP password.

The system also is displaying a number of password related error messages, the one in the attached jpeg showed up when I started the machine last.

cheers

---

### Post by Miljet on 2009-05-20
What it is actually asking for there is your regular password (the one you use to log in). It uses that to unlock your keyring.

---

### Post by tomreid on 2009-05-20
Hi all,

I have been wading through various guides I found on line, and had found that running command "lshw" gave me information about the driver and the hardware. The data that showed up in the terminal window is copied below. I think this is telling me that the driver and the hardware are OK. 

One thing I may have done when I installed the OS was I was too quick to assume that the wireless card was not supported already by the OS and I followed the route to use the ".inf" file from windows using " ndiswrapper" is it possible that both the native linux driver in the OS and the windows driver are trying to access the wireless card and that is producing the error that the card looks OK but it won't connect to my network?

I can't find any easy way to change the driver back to the native Linux driver to see if that solves the problem.



*-network:0
                description: Wireless interface
                product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
                vendor: Intel Corporation
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: wlan0
                version: 04
                serial: 00:0c:f1:2f:82:fa
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+w70n501 driverversion=1.53+Intel,08/02/2006,1.2.5.37 latency=64 link=no maxlatency=34 mingnt=2 module=ndiswrapper multicast=yes wireless=IEEE 802.11b

---

