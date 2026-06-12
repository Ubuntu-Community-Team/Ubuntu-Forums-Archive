---
title: "Broadcom Bluetooth dongle doesn't work"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by ectospasm on 2008-08-22
I have a Broadcom USB Bluetooth dongle which doesn't work in Kubuntu Hardy.  It shows up in lsusb but hci* does not find any HCI devices.  Here's the dmesg output when I unplug and replug the dongle:
```
ecstasy:~ # dmesg
[ 1468.394774] usb 1-2: USB disconnect, address 5
[ 1468.394779] usb 1-2.2: USB disconnect, address 6
[ 1468.435869] usb 1-2.3: USB disconnect, address 7
[ 1482.137998] usb 2-2: new full speed USB device using uhci_hcd and address 2
[ 1482.314602] usb 2-2: configuration #1 chosen from 1 choice
[ 1482.317534] hub 2-2:1.0: USB hub found
[ 1482.319495] hub 2-2:1.0: 3 ports detected
[ 1482.629594] usb 2-2.2: new full speed USB device using uhci_hcd and address 3
[ 1482.772263] usb 2-2.2: configuration #1 chosen from 1 choice
[ 1482.779284] input: Broadcom Corp BCM2045B3 ROM as /devices/pci0000:00/0000:00:1a.1/usb2/2-2/2-2.2/2-2.2:1.0/input/input8
[ 1482.832209] input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:1a.1-2.2
[ 1483.039401] usb 2-2.3: new full speed USB device using uhci_hcd and address 4
[ 1483.181073] usb 2-2.3: configuration #1 chosen from 1 choice
[ 1483.188212] input: Broadcom Corp BCM2045B3 ROM as /devices/pci0000:00/0000:00:1a.1/usb2/2-2/2-2.3/2-2.3:1.0/input/input9
[ 1483.231783] input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:1a.1-2.3
```

I know the dongle is at least somewhat recognized.  However, the HCI tools that come with the Bluetooth stack always return errors to the effect of "device not found":
```
ecstasy:~ # hcitool dev
Devices:
ecstasy:~ # hcitool scan
Device is not available: No such device
ecstasy:~ # hciconfig hci0 up
Can't get device info: No such device
``` 

Here's the output of lsub, for good measure:
```
ecstasy:~ # lsusb
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 0a5c:4503 Broadcom Corp.
Bus 002 Device 003: ID 0a5c:4502 Broadcom Corp.
Bus 002 Device 002: ID 0a5c:4500 Broadcom Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

The keyboard and mouse I primarily use this with do work, but certain functions (e.g. the scroll wheel on the mouse and the multimedia keys on the keyboard) don't work.  I know the dongle does work, because it has worked in this machine, in this OS install, with this kernel:  it was working fine during my last stretch of uptime.  But for that boot the dongle didn't work either, it "just started working," mysteriously, and I can't explain why.  All I know is it wasn't working, and while I was at work I noticed one of the hci* commands did show the hci0 device eventually, I just didn't know what had happened.  Nothing is in cron that would have made it work, nor in anacron (I just checked again for good measure).

I've been wrestling with this keyboard and mouse since I got them, and I'm beginning to think the problem is the dongle.  I will appreciate any hints on getting this working, or suggestions for other Bluetooth dongles that haven't reported as many problems.

---

### Post by styyle14 on 2008-08-22
I am having the exact same problem, any help would be greatly appreciated.
BUMP

---

### Post by Golden Blunder on 2008-08-23
see if this helps  hcitool scan, hcitool dev,name,info,inq
                   sdptool browse,search,records.Use one option at a time.
Should get info on name,mac etc.

---

### Post by ectospasm on 2008-08-23
> **Golden Blunder said:**
> see if this helps  hcitool scan, hcitool dev,name,info,inq
                   sdptool browse,search,records.Use one option at a time.
Should get info on name,mac etc.

Output is as follows:
```
ecstasy:~ # hcitool scan
Device is not available: No such device
ecstasy:~ # hcitool dev
Devices:
ecstasy:~ # hcitool name
Usage:
        name <bdaddr>
ecstasy:~ # hcitool info
Usage:
        info <bdaddr>
ecstasy:~ # hcitool inq
Inquiring ...
Inquiry failed.: No such device
ecstasy:~ # sdptool browse
Inquiring ...
Inquiry failed
ecstasy:~ # sdptool search
Usage:
        search [--bdaddr bdaddr] [--tree] [--raw] [--xml] SERVICE
SERVICE is a name (string) or UUID (0x1002)
ecstasy:~ # sdptool records
Usage:
        records [--tree] [--raw] [--xml] bdaddr

```

Like I said before, all of the normal tools don't work, because the device hci0 (wherever it shows) does not exist.

---

### Post by styyle14 on 2008-08-23
same exact results when ran on my computer as well:
> 
laptop:~$ hcitool scan
Device is not available: No such device
laptop:~$ hcitool dev
Devices:
laptop:~$ hcitool name
Usage:
	name <bdaddr>
laptop:~$ hcitool info
Usage:
	info <bdaddr>
laptop:~$ hcitool inq
Inquiring ...
Inquiry failed.: No such device
laptop:~$ sdptool browse
Inquiring ...
Inquiry failed
laptop:~$ sdptool search
Usage:
	search [--bdaddr bdaddr] [--tree] [--raw] [--xml] SERVICE
SERVICE is a name (string) or UUID (0x1002)
laptop:~$ sdptool records
Usage:
	records [--tree] [--raw] [--xml] bdaddr


Here is the output of dmesg when I plug it in:
> 
[  288.910561] usb 1-1: new full speed USB device using uhci_hcd and address 8
[  288.933631] usb 1-1: configuration #1 chosen from 1 choice
[  288.936562] hub 1-1:1.0: USB hub found
[  288.938524] hub 1-1:1.0: 3 ports detected
[  289.248391] usb 1-1.2: new full speed USB device using uhci_hcd and address 9
[  289.383666] usb 1-1.2: configuration #1 chosen from 1 choice
[  289.393924] input: Broadcom Corp BCM2045B3 ROM as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input12
[  289.419185] input,hidraw1: USB HID v1.11 Keyboard [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:1d.0-1.2
[  289.626316] usb 1-1.3: new full speed USB device using uhci_hcd and address 10
[  289.772274] usb 1-1.3: configuration #1 chosen from 1 choice
[  289.782698] input: Broadcom Corp BCM2045B3 ROM as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input13
[  289.810968] input,hidraw2: USB HID v1.11 Mouse [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:1d.0-1.3


It appears that the device is detected as a keyboard and a mouse instead of a bluetooth dongle...

Information about the device itself (from the back of the device):
> 
Company: RocketFish
Item Identification: BT Adapter Fullsize
Model No.: RF-FLBTAD
FCC ID: D6xBT3038
IC IC: 3187A-BT3038B
S/N: 8E07A01133


If it helps
I am running Ubuntu Hardy on kernel 2.6.24.19-generic
Packages:
bluetooth 3.26-0ubuntu6
bluetooth-alsa 0.5cvs20070908-1
bluez-audio 3.26-0ubuntu6
bluez-btsco 1:0.50-0ubuntu2
bluez-cups 3.26-oubuntu6
bluez-gnome 0.25-0ubuntu1
bluez-hcidump 1.40-0ubuntu1
bluez-pcmcia-support 3.26-0ubuntu6
bluez-utils 3.26-0ubuntu6
gnome-bluetooth 0.11.0-0ubuntu1

Again, any help would be greatly appreciated!

---

### Post by Golden Blunder on 2008-08-23
check /etc/bluetooth/hcid.conf
did you actually put in the command hci tool scan as I gave you? Kubuntu should recognise this.

---

### Post by styyle14 on 2008-08-23
put it where?

please describe exactly how to modify this file

thanks

---

### Post by Golden Blunder on 2008-08-23
/hcid.conf  , should be like this
#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security auto;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# PIN helper
	#pin_helper /usr/bin/pinwrapper;
	#pin_helper /usr/bin/bluez-pin;
	pin_helper /usr/bin/bluepin;
	# D-Bus PIN helper
	#dbus_pin_helper;
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x3e0100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;

	# Authentication and Encryption (Security Mode 3)
	#auth enable;
	#encrypt enable;
}

---

### Post by styyle14 on 2008-08-23
I replaced my /hcid.conf file with the one you provided, yet there was no change in any of the commands or in the dmesg output. Exactly what changes where made to the file, are they device specific?

---

### Post by Golden Blunder on 2008-08-23
Oh Dear I've given you the wronge file for Hardy and it's changed somewhat.
I'll sort out the right one and post soon.Sorry!

---

### Post by Golden Blunder on 2008-08-23
Replace your backup file and post it so I can examin it

---

### Post by styyle14 on 2008-08-23
#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security user;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
	passkey "1234";
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x000100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;
	discovto 0;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}

---

### Post by Golden Blunder on 2008-08-23
Try This
#
# HCI daemon configuration file.
#

# HCId options
options {
# Automatically initialize new devices
autoinit yes;

# Security Manager mode
# none - Security manager disabled
# auto - Use local PIN for incoming connections
# user - Always ask user for a PIN
#
security user;

# Pairing mode
# none - Pairing disabled
# multi - Allow pairing with already paired devices
# once - Pair once and deny successive attempts
pairing multi;

# Default PIN code for incoming connections
passkey "1234";
}

# Default settings for HCI devices
device {
# Local device name
# %d - device id
# %h - host name
name "%h-%d";

# Local device class
class 0x000100;          change to class 0x3e0100;

# Default packet type
#pkt_type DH1,DM1,HV1;

# Inquiry and Page scan
iscan enable; pscan enable;
discovto 0;        You could remove this line

# Default link mode
# none - no specific policy
# accept - always accept incoming connections
# master - become master on incoming connections,
# deny role switch on outgoing connections
lm accept;

# Default link policy
# none - no specific policy
# rswitch - allow role switch
# hold - allow hold mode
# sniff - allow sniff mode
# park - allow park mode
lp rswitch,hold,sniff,park;
}

---

### Post by styyle14 on 2008-08-23
this still did not change anything...

thanks for all your help

---

### Post by Golden Blunder on 2008-08-23
Last Shot:- Have you checked the usb speed settings in the bios

---

### Post by styyle14 on 2008-08-24
????? I have no idea how to do that or what it means.... If you could describe how to do something like that, or link to a guide, it would be greatly appreciated.  I think, however, it is probably a detection problem of some kind because it is detected as a mouse and a keyboard (from what I've read in the dmesg), but not a bluetooth adapter.

Any help is appreciated, thanks

---

### Post by ectospasm on 2008-08-24
My /etc/bluetooth/hci.conf:
```
ecstasy:~ # grep -ve '^[[:space:]]*#' /etc/bluetooth/hcid.conf

options {
        autoinit yes;

        security auto;

        pairing multi;

        passkey "1234";
}

device {
        name "%h-%d";

        class 0x000100;


        iscan enable; pscan enable;
        discovto 0;

        lm accept;

        lp rswitch,hold,sniff,park;
}
```

Pretty basic, and I know for a fact that this setup did work, I just don't know how, or how to return to that state.  Unless the Kubuntu gnomes (heh) fix it when I'm sleeping...

Oh, and the BIOS settings are set for High Speed, which will drop to Full/Low speed with a low speed adapter, or so the manual (and the in-BIOS documentation) says.  I will be trying it on the Full/Low speed in just a moment.

---

### Post by ectospasm on 2008-08-24
And since this is a full/low speed dongle (USB1.1), I set the speed to Full/Low, and still no Bluetooth (same problems as before).

---

### Post by ectospasm on 2008-08-24
Good news, sorta.  My bluetooth started working.  Of course, I didn't do anything to make it work, and I could have sworn I did this, but... it appears that the hci_usb kernel module hiccuped, or somehow got reloaded, and voila! I now have hci0!  I could have sworn I tried a "modprobe -r hci_usb && modprobe hci_usb", but that didn't seem to work.  I'm guessing it didn't work when I tried it manually because the modprobe -r (remove) complained that the module was in use, and I didn't feel like tracking down all the modules involved, since I'm uber lazy, and IIRC some modules didn't have any dependent modules yet they were still in use (thus I couldn't unload them).  Whatever, this makes me pissed off since I still don't know how to fix it when I reboot again.

Oh yeah, what notified me about it working was that kbluetoothd crashed.  Probably whatever made the module HUP or reload made kbluetooth barf, and restarting it shows a nice shiny blue K icon in the systray.  

Hopefully this will give me a hint when it happens again.  Screw all y'all, it's for ***_MY_*** benefit!  :p

---

### Post by styyle14 on 2008-08-24
Once you solve the problem, could you please post the solution so that myself and others can benefit from it?

---

### Post by ectospasm on 2008-08-24
> **styyle14 said:**
> Once you solve the problem, could you please post the solution so that myself and others can benefit from it?


I don't know what the solution is presently.  My best guess is that unloading and loading hci_usb was what fixed it.  I don't really remember if I tried that or not.  The next time this happens to me (the next time I reboot), I'm going to try the following:  use "lsmod | grep hci_usb", try to remove all of the modules that depend on hci_usb (using modprobe -r <module 1> [<module 2>[ ...<module N>]]), keeping track of module names, and then try reloading hci-usb to see if I can get bluetooth to work.  Please be aware that this may not be as simple as it seems on the surface (I expect a large degree of modprobe -r "Hell"), since some modules may be listed as in use, but don't seem to have any dependent modules.  I still haven't figured out if a running program can keep a module loaded.  I sometimes consider myself a Linux guru, but not with this.  And I load and unload modules at work all day long.

---

### Post by destructar on 2008-08-24
I'm having the exact same problems described by styyle14 (hcitool scan, hcitool dev, etc. fails instantly). 
Note: I am running Ubuntu 8.04 and I'm using a bluetooth usb dongle.

lsusb shows the dongle as:
```
Bus 004 Device 004: ID 0a5c:2033 Broadcom Corp. BCM2033 Bluetooth
```

also note: I had this working perfectly fine in 7.10

Any help on this would be greatly appreciated.

---

### Post by Golden Blunder on 2008-08-24
I see bluetoothd being mentioned but hasn't that been dropped in favour of Gnome-bluetooth in 8.04 ,I'm still on 6.0.6 and bluetoothd works perfect.

---

### Post by SpankinPartier on 2008-09-22
I've been suffering with the same USB Bluetooth dongle myself. I bought a Rocketfish bluetooth keyboard/mouse combo that came with the Broadcom bcm2045b3 dongle.

The dongle starts up in HID mode and I'm able to type and use the mouse.  But for only basic functions.  The extended multimedia keys and the mouse scroll wheel are not activated when they are in HID mode.  They must be switched over to HCI mode for these to work.

When I first start up the computer and do a **lsusb** I see only 3 Broadcom devices, similar to Ectospasm.  I would try a few things then search the web some more, and then try again.  I was not getting anywhere.

While I was doing this I had a terminal open running this command: **sudo watch tail /var/log/syslog**  That allowed me to see anything I was doing would create any events.  When out of no where came a bunch of events:
```
Sep 21 23:49:47 naruto kernel: usb 3-2.1: new full speed USB device using uhci_hcd and address 5
Sep 21 23:49:47 naruto kernel: usb 3-2.1: configuration #1 chosen from 1 choice
Sep 21 23:49:47 naruto hcid[6434]: HCI dev 0 registered
Sep 21 23:49:47 naruto hcid[6434]: HCI dev 0 up
Sep 21 23:49:47 naruto hcid[6434]: Starting security manager 0
Sep 21 23:49:47 naruto hcid[6654]: Can't set scan mode on hci0: Device or resource busy (16)
Sep 21 23:49:47 naruto hcid[6654]: Can't set auth on hci0: Device or resource busy (16)
Sep 21 23:49:47 naruto hcid[6654]: Can't set encrypt on hci0: Device or resource busy (16)
```

That happened 3 minutes and 38 seconds after I did a **/etc/init.d/bluetooth restart**.  Given how long that took I don't know what up with that.  But notice all the hci0 errors "Device or resource busy".  I'll get back to that in a minute.

So now if I do a lsusb I have a new item showing up:```
Bus 001 Device 001: ID 1d6b:0002  
Bus 005 Device 002: ID 057b:0020 Y-E Data, Inc. HEXA Media Drive 6-in-1 Card Reader Writer
Bus 005 Device 001: ID 1d6b:0001  
Bus 004 Device 001: ID 1d6b:0001  
[color=red]Bus 003 Device 005: ID 0a5c:2120 Broadcom Corp. [/color]
Bus 003 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 003: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001  
Bus 002 Device 001: ID 1d6b:0001  
``` Bus 003 Device 005 just showed up.  Hmmm, this looks good.

So now if I try a few commands here's what I get:```
naruto log # hcitool dev
Devices:
	hci0	00:02:76:0D:5A:02
naruto log # hciconfig -a
hci0:	Type: USB
	BD Address: 00:02:76:0D:5A:02 ACL MTU: 1017:8 SCO MTU: 64:0
	UP RUNNING PSCAN ISCAN 
	RX bytes:844 acl:0 sco:0 events:88 errors:0
	TX bytes:1422 acl:0 sco:0 commands:87 errors:0
	Features: 0xff 0xff 0x8d 0xfe 0x9b 0xf9 0x00 0x80
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'BlueZ (0)'
	Class: 0x3e0100
	Service Classes: Networking, Rendering, Capturing
	Device Class: Computer, Uncategorized
	HCI Ver: 2.0 (0x3) HCI Rev: 0x4116 LMP Ver: 2.0 (0x3) LMP Subver: 0x430e
	Manufacturer: Broadcom Corporation (15)

naruto log # hcitool scan
Scanning ...
naruto log # 
```*(the computer ran all last night, but last night the hciconfig command errored out at the Name line with an Input/Output error and I got a timeout error on hcitool scan command.  I'm puzzled as to why they're working -sort of- now.)*

So this brings me back to my syslog I posted earlier.  It had those "Device or resource busy" errors.  I'm wondering if the USB HID drivers are getting in the way with the HCI drivers?  Or is this a faulty bcm203x kernel module?  I wouldn't be surprised since this is a Broadcom bcm204___ dongle not a bcm203___ dongle.

I've been working on this on my Gentoo box all weekend.  But I also tried it out on my Ubuntu box and was getting the same results.  So this problem isn't prone to just one distro.  I've even gone so far as to download, compile, and install the latest kernel form kernel.org.  With no improvement.

I'm not sure where to go from here.  I do have another Bluetooth dongle somewhere.  I just don't know where it is (last seen it 2 moves ago).  If I can't find it, I may have to purchase another one and see if there's any change.

---

### Post by SpankinPartier on 2008-10-04
I ended up buying another Bluetooth USB Dongle.  This one works as I can connect to my keyboard and mouse. 

But I can't thrown my PS/2 keyboard just yet as I still need to unplug and plug back in the new dongle, press the keyboard and mouse connect buttons, and fire off a **sudo hidd --search** command to get them to work after a reboot.

In my particular application this isn't too bad as I'm using the Bluetooth k/m with my home theater, while I keep the PS/2 m/k at my desk in the office.  Now I can go and grab some :popcorn: and watch a movie, or listen to some :guitar:
8-)

---

### Post by Sir_Sid on 2008-11-01
Does anybody know how to make this work? I have the exact same problems and Im not sure how to do it.

---

### Post by PorcelainMouse on 2008-12-11
I also have exactly the same problem originally reported.  Broadcom 2045 -based Bluetooth USB adapter (Broadcom Corp BCM2045B3 ROM) shows up as three devices on USB bus, but none of these appear to be HCI devices.  I've tried in both Hardy Heron and Intrepid Ibex (8.04 & 8.10).

Some information I have seems to indicate that the bluez software works with this chipset.  But, there are several reports like this with no resolution.  Must we declare this chipset "unsupported"?  Has anyone tried the latest bluez package (4.22something+?)?  Also, I see references to the 'btusb' kernel module; but I can't find it.  Is that not in our distro for some reason?

---

### Post by b3nw on 2009-03-01
bump... any news on this? still stuck with hci0: Device or resource busy (16)

---

### Post by bildr on 2009-05-08
hello all.
My solution was to...wait for it, it's REALLY cheezy, unplug and replug in another usb port.

I am currently running BT4beta(ubuntu based) with intrepid repos enabled.  Installed bluez 2 and 3(that was a headache btw) and couldn't figure out why my bluetooth dongle wasn't appearing as an HCI device.  On an acer aspire 150 the left hand usb port is 1.1 the R 2 are 2.0.  Evidently, the broadcom chipset I am using couldn't recoginze on a 1.1 port.  hope it helps.

---

### Post by medined on 2010-03-22
I bought the RocketFish RF-FLBTAD bluetooth dongle today. When it was plugged into the front USB ports of my computer, the dongle would not be recognized as an HCI device. However, when I plugged it into one of the USB ports in the back of my computer, it registered just fine. Lots of good messages in /var/log/syslog.

---

### Post by kesten on 2012-05-15
I finally got my bluetooth working with Ubuntu 11.10 using a RF FLBTAD rocketfish adapter with a Blackberry Curve 8330m.  It was very* hit and miss on both BB and ubuntus ends.

Browse files didn't ever get working, but i was able to send pictures to and from the device.
Here's what I did.

Installed blueman.  When pairing chose my own pin in the bluetooth manager on ubuntu.  You need this for the phone when it asks for it.  I got many send failures before it finally started sending properly.

On the blackberry, some menus only show the pictures with email or mms options, neither of which work for me.  Only when i went to Camera - View Photos, did the menu offer bluetooth sending.  
The hardest part was actually finding where the files got put on my laptop.  Suggestions on the net include Downloads, Home, Pictures..  I found it by clicking the bluetooth icon top right menu bar, selecting Local Services, where you can choose what file to download to.  Mine was set to Home/Public.

I also have a samsung reality SCH-U820.  It was able to pair, but only received when it felt like it and very rarely makes a successful send.  

When switching between devices (and even when not) it seemed helpful to go to the bluetooth icon select "devices".  In the menu for the blueman manager that pops up, choose Device - Refresh Services.

Best of luck.

kesten

---

