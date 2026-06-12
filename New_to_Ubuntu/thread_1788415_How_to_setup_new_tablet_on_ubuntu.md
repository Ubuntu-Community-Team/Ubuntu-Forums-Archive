---
title: "How to setup new tablet on ubuntu?"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by Ellume on 2011-06-22
I'm running ubuntu 10.10 and I just bought myself a graphics drawing tablet. It is a Monoprice MP8060-H850 Graphic Drawing Tablet. I'm trying to get it to work on my system. I found one guide at [https://help.ubuntu.com/community/TabletSetup]("https://help.ubuntu.com/community/TabletSetup") but it doesn't list this tablet, and I've been searching for some drivers I could use on the net but haven't had much luck. Does this mean the tablet I got can't be used with ubuntu?

---

### Post by fballem on 2011-06-22
I'm not an expert, but at the risk of asking the most obvious of questions, what happens if you plug the tablet into your computer and reboot?

---

### Post by fballem on 2011-06-22
The reason that I am asking is that quite often, in my 3+ years of experience, ubuntu recognizes and will take the appropriate actions for new hardware.

---

### Post by Ellume on 2011-06-22
Well the tablet is on. If I try to use it then it acts like I'm clicking in the very top left of my screen. I will try restarting again just to be sure.

---

### Post by fballem on 2011-06-22
If it doesn't work right away, then this guide: [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) might be helpful.

---

### Post by Ellume on 2011-06-22
Well the restart didn't work so I'm going through that guide.

Unfortunately I'm a bit stuck on the configuration.
> Calibrate in order to find the edges of your tablet/digitizer - Run this command:

```
sudo ./wizardpen-calibrate /dev/tablet-event
```
You may find "/dev/tablet-event" missing, try this command to help find the correct value

```
ls /dev/input/by-id/
```
Example corrected "/dev/tablet-event" location. Use the value for rc.local and xorg.conf

```
/dev/input/by-id/usb-WALTOP_International_Corp._Slim_Tablet-event-if00
```
But this is what I get when I try that:
```
ellume@Shimmer:/usr/src/linux-headers-2.6.35-28-generic-pae/include/config/generic/calibrate$ sudo ./wizardpen-calibrate /dev/tablet-event
[sudo] password for ellume: 
sudo: ./wizardpen-calibrate: command not found
ellume@Shimmer:/usr/src/linux-headers-2.6.35-28-generic-pae/include/config/generic/calibrate$ ls /dev/input/by-id/
usb-5543_H850S-event-mouse  usb-Logitech_USB-PS_2_Optical_Mouse-event-mouse
usb-5543_H850S-mouse        usb-Logitech_USB-PS_2_Optical_Mouse-mouse
ellume@Shimmer:/usr/src/linux-headers-2.6.35-28-generic-pae/include/config/generic/calibrate$ 

```I'm not really sure what to try next. Any thoughts?

---

### Post by Favux on 2011-06-22
Hi Ellume,

With your Waltop tablet you can use either the WizardPen driver or the Wacom driver in Maverick.  See [HOW TO set up a Waltop tablet in Lucid & Maverick & Natty]("http://ubuntuforums.org/showthread.php?t=1595648").

---

### Post by Ellume on 2011-06-22
> **Favux said:**
> With your Waltop tablet you can use either the WizardPen driver or the Wacom driver in Maverick.  See [HOW TO set up a Waltop tablet in Lucid & Maverick & Natty]("http://ubuntuforums.org/showthread.php?t=1595648").
Umm, but I have a Monoprice tablet not a Waltop :confused:

---

### Post by Favux on 2011-06-22
It looks like Monoprice has rebranded a Waltop (the OEM) as a Monoprice MP8060-H850 Graphic Drawing Tablet.  That's common.  Your by-id shows it is a Waltop:
> /dev/input/by-id/usb-WALTOP_International_Corp._Slim_Tablet-event-if00
You can confirm by entering *lsusb* in a terminal and looking at the output line with the tablet in it or entering *xinput list*.

---

### Post by Ellume on 2011-06-22
Oh, that was me quoting the part of the guide I was stuck on. When I use *lsusb* I get:
```
Bus 002 Device 003: ID 5543:0782 UC-Logic Technology Corp. 
Bus 002 Device 002: ID 046d:c040 Logitech, Inc. Corded Tilt-Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```So I guess it is a UC-Logic rebanded. hmmm.

---

### Post by Favux on 2011-06-22
Ah, OK my mistake.  No then you do have a Wizardpen tablet.  UC_Logic's use the wizardpen driver.

Did you install the wizardpen driver from DoctorMO's wizardpen PPA?

---

### Post by Ellume on 2011-06-22
I added the ppa and installed xserver-xorg-input-wizardpen like it says. I've been trying to follow the rest of the guide. In the configuration part it asks for /dev/tablet-event which my computer doesn't have. So I just replaced it with the /dev/input/by-id/*-mouse-event. So far all that happens when I try to use the tablet is that no matter how I use it the mouse cursor jumps to the very top left corner of the screen and clicks.

I'm still trying out some minor things. It looks like the tablet has 2 different names in /dev/input/by-id/ when I plug it in. One I think only shows up when I restart with it plugged in: usb-UC-LOGIC_Tablet_WP5540U-event-mouse

Going to restart again to check.

---

### Post by Favux on 2011-06-22
Alright.  Post the result of *xinput list* in a terminal and look in /usr/share/X11/xorg.conf.d for your 70-wizardpen.conf.  Post the contents of the wizardpen.conf also.

When the pointer arrow goes up to the left upper corner like that it means the X server isn't getting any input.  That corner is 0,0.  That indicates that the match in the wizardpen.conf isn't working for your tablet and so it isn't on the WizardPen X driver.  We need to fix that match so your tablet is recognized and placed on the WizardPen driver.

---

### Post by mikewhatever on 2011-06-22
You mean, how to set up Ubuntu on the new tablet, don't you?

---

### Post by Ellume on 2011-06-22
Alright, well that makes sense. Here are the outputs:


xinput list
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; H850S                                   	id=8	[slave  pointer  (2)]
&#9116;   &#8627; H850S                                   	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
```

70-wizardpen.conf
```
Section "InputClass"
   Identifier      "wizardpen"
   MatchIsTablet   "on"
   MatchDevicePath "/dev/input/by-id/usb-5543_H850S-event-mouse"
   MatchTag        "wizardpen"
   Driver          "wizardpen"
EndSection

Section "InputClass"
   Identifier      "wizardpen ignore mouse dev"
   MatchDevicePath "/dev/input/by-id/usb-5543_H850S-event-mouse"
   MatchTag        "wizardpen"
   Driver          "mouse"
   Option          "MouseSpeed" "16"
   Option          "ignore"     "true"
EndSection
```

I couldn't find any file called just wizardpen.conf on my system. Also when I restarted my computer ended up at a text prompt login, so I restarted in failsafeX. I guess the edits I followed on the guide for the /etc/X11/xorg.conf and /etc/rc.local are causing some problems.

---

### Post by Ellume on 2011-06-22
> **mikewhatever said:**
> You mean, how to set up Ubuntu on the new tablet, don't you?

No, this is a graphics drawing tablet for a desktop computer with ubuntu installed.

---

### Post by Favux on 2011-06-22
Yes.  You should not need to edit the xorg.conf.  That's for older set ups.  So remove anything in there for the UC_LOGIC.

I'll have to hunt around for a default wizardpen.conf but I'm pretty sure the keyword match for the UC-Logic tablets is "UC_LOGIC" in the wizardpen.conf.  The PPA should have installed a wizardpen.conf so I'm a little concerned that didn't go right.

Since the output of *lsusb* in a terminal was *Bus 002 Device 003: ID 5543:0782 UC-Logic Technology Corp* I'm thinking something is wrong with your xinput list.  Let's fix the xorg.conf and make sure it is booting correctly and then repeat xinput list.

---

### Post by Ellume on 2011-06-22
Well I double checked that the ppa was correct and the xserver-xorg-input-wizardpen was the latest version according to it. Both look correct.

I undid the changes to X and the computer starts up fine now. I did the *xinput list* command and the output is:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; H850S                                   	id=8	[slave  pointer  (2)]
&#9116;   &#8627; H850S                                   	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

```
I double checked the *lsusb* too
```
Bus 002 Device 003: ID 046d:c040 Logitech, Inc. Corded Tilt-Wheel Mouse
Bus 002 Device 002: ID 5543:0782 UC-Logic Technology Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by Ellume on 2011-06-22
Also when I check ls /dev/input/by-id/ I get:
```
usb-5543_H850S-event-mouse  usb-Logitech_USB-PS_2_Optical_Mouse-event-mouse
usb-5543_H850S-mouse        usb-Logitech_USB-PS_2_Optical_Mouse-mouse

```

Which I find strange in itself because at least one time I was checking the tablet was listed as
```
usb-UC-LOGIC_Tablet_WP5540U-event-mouse
usb-UC-LOGIC_Tablet_WP5540U-mouse
```
I thought maybe it recognized it differently on restart, but that appears not to be the case.

---

### Post by Favux on 2011-06-22
Good, I didn't think that was the tablet.  And it wasn't it was the Logictech mouse.  That indicates you've lost usb communication with the tablet.  Replug it in and make sure the usb connector is seated firmly.  If you're plugging it into a hub try using a port directly on the Desktop for now until you have it working.

---

### Post by Ellume on 2011-06-22
When I unplug the tablet I get
xinput list
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

```
ls /dev/input/by-id/
```
usb-Logitech_USB-PS_2_Optical_Mouse-event-mouse
usb-Logitech_USB-PS_2_Optical_Mouse-mouse

```

Then when I plug it back in I get
xinput list
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=10	[slave  pointer  (2)]
&#9116;   &#8627; H850S                                   	id=8	[slave  pointer  (2)]
&#9116;   &#8627; H850S                                   	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

```

ls /dev/input/by-id/
```
usb-5543_H850S-event-mouse  usb-Logitech_USB-PS_2_Optical_Mouse-event-mouse
usb-5543_H850S-mouse        usb-Logitech_USB-PS_2_Optical_Mouse-mouse

```
So the H850S appears to be the tablet. But I still remember it coming up as the other way one time, as I copy and pasted it here. I'm not sure what would cause the same device to appear differently.

---

### Post by Favux on 2011-06-22
Not sure what's going on either.  But you are using a Logitech mouse, correct?  It is almost as if the tablet is being conflated with the mouse which is weird.  You didn't edit a .conf file in xorg.conf.d did you?

The problem started with your xorg.conf it seems like.  Was there one there to begin with?  Can you show me what it currently looks like?

Also let's confirm the wizardpen driver from the PPA is installed.  Search 'wizardpen' in Synaptic Package Manager.  It should be the package called something like xorg-xserver-input-wizardpen.  Make sure it is the same version number as the one for Maverick in Martin Owen's PPA.

---

### Post by Ellume on 2011-06-22
Well I got an error opening up synaptic```
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ maverick/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-i386_Packages)
```But after acknowledging that and searching wizardpen it shows up with one entry of xserver-xorg-input-wizardpen which it says I have the latest version of currently installed.

Well the xorg does seem to be the problem, and whatever happened it seemed like I ended up with a blank file at one point, I'm not sure how I managed that one. So nvidia rebuilt the file, but it looks different.
Here is the current version
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.06  (buildmeister@builder101)  Mon Sep 13 07:06:38 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

I *think* that the original looked more like the following before which I got from the xorg.conf.failsafe file.
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

---

### Post by 23dornot23d on 2011-06-22
Just out of interest do a 

[B]lsusb -v

[/B]( see if it shows up any more information ..... this was what showed you had a  UC-LOGIC earlier in the thread ...... but by doing a verbose it may give some more information - sorry for butting in - will leave you with it ...... but thought this may help ...... as you could not see why it appeared earlier .... )[B]

mine gives this if it is the UC-Logic .... it may look similar ....

> 
Bus 001 Device 008: ID 5543:0004 UC-Logic Technology Corp. Tablet WP5540U
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x5543 UC-Logic Technology Corp.
  idProduct          0x0004 Tablet WP5540U
  bcdDevice            0.00
  iManufacturer           1 UC-LOGIC
  iProduct                2 Tablet WP5540U
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              2 Tablet WP5540U
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     212
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)
root@keith-MS-7181:/home/keith# 




_*[[COLOR=Red]Link to where you quoted it before in the thread[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10969795&postcount=10")*_
[/B]

---

### Post by Favux on 2011-06-22
Good, some progress.  The Nvidia proprietary driver adds some extra uneeded stuff for recent xorg.conf's.  Let's comment them out for now.  You can remove them later.
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.06  (buildmeister@builder101)  Mon Sep 13 07:06:38 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
#    InputDevice    "Keyboard0" "CoreKeyboard"
#    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

#Section "InputDevice"
    # generated from default
#    Identifier     "Mouse0"
#    Driver         "mouse"
#    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
#EndSection

#Section "InputDevice"
#    # generated from default
#    Identifier     "Keyboard0"
#    Driver         "kbd"
#EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```
The file that runs last controls and in essence the xorg.conf runs after xorg.conf.d.

Always with any X configuration file **back it up** so you can restore your current working version from the command line if you break X.  In a terminal enter:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
To **restore** it from the command line if X is broken use:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```
To **edit** it enter in a terminal:
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Ellume on 2011-06-22
I actually thought I made a cp to xorg.conf.backup but when I checked it, it was also blank. I'm guessing I typoed the source file or something. Anyway I have a new backup file and made the comments to xorg.conf

My output for sudo lsusb -v is
```
Bus 002 Device 004: ID 5543:0782 UC-Logic Technology Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x5543 UC-Logic Technology Corp.
  idProduct          0x0782 
  bcdDevice            0.00
  iManufacturer           1 
  iProduct                2 H850S
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              300mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     254
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               5
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     139
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

Bus 002 Device 003: ID 046d:c040 Logitech, Inc. Corded Tilt-Wheel Mouse
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc040 Corded Tilt-Wheel Mouse
  bcdDevice           24.30
  iManufacturer           1 Logitech
  iProduct                2 USB-PS/2 Optical Mouse
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      59
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0005  1x 5 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.35-28-generic-pae ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:0b.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
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
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength              11
  bDescriptorType      41
  nNbrPorts            10
  wHubCharacteristic 0x0002
    No power switching (usb 1.0)
    Ganged overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x00
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0303 lowspeed power enable connect
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
   Port 7: 0000.0100 power
   Port 8: 0000.0100 power
   Port 9: 0000.0100 power
   Port 10: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.35-28-generic-pae ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:0b.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
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
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength              11
  bDescriptorType      41
  nNbrPorts            10
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x00
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
   Port 7: 0000.0100 power
   Port 8: 0000.0100 power
   Port 9: 0000.0100 power
   Port 10: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

```

---

### Post by Favux on 2011-06-22
Hah, did the xorg.conf stuff clear it up?  I assume you rebooted.  What does *xinput list* look like now?

---

### Post by Ellume on 2011-06-22
Well for the tablet I have the same problem I've had from the start, even before I tried to do anything. If I try to use it then the mouse cursor jumps to the top left and clicks. It was the tablet not working that got me looking for drivers etc in the first place.

Here is the *xinput list*```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; H850S                                   	id=8	[slave  pointer  (2)]
&#9116;   &#8627; H850S                                   	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

```

---

### Post by Favux on 2011-06-22
Bizarre.

OK let's assume that is indeed the tablet and the spurious mouse entry, after all the lsusb -v does say:
>   iProduct                2 H850S

Which would make your match keyword "H850S".  Meaning something is messed up in the kernel descriptor for your model tablet.  But OK.

Next you really haven't indicated whether you have the PPA driver installed.  I'm thinking you don't which is why there isn't a wizardpen.conf.  If I recall correctly the default Maverick wizardpen driver in the repositories doesn't work and doesn't install a wizardpen.conf.  In Synaptic Package Manager what was the version number for the wizardpen driver installed?

---

### Post by 23dornot23d on 2011-06-22
You could do a quick check of the xorg.0.log see if anything is being registered there too.

mine shows the following output .... in System - Logfile viewer .....

( was in Maverick mine used to shoot to the top left too all the time ..... but in Natty 11.04 it automatically gets picked up now .... but the fix was to add the latest wizardpen driver at the time  ....... )

> 

  1884.003] (II) config/udev: Adding input device UC-LOGIC Tablet WP5540U (/dev/input/event11)
[  1884.003] (**) UC-LOGIC Tablet WP5540U: Applying InputClass "evdev tablet catchall"
[  1884.003] (II) Using input driver 'evdev' for 'UC-LOGIC Tablet WP5540U'
[  1884.003] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1884.003] (**) UC-LOGIC Tablet WP5540U: always reports core events
[  1884.003] (**) UC-LOGIC Tablet WP5540U: Device: "/dev/input/event11"
[  1884.003] (--) UC-LOGIC Tablet WP5540U: Found absolute axes
[  1884.003] (II) evdev-grail: failed to open grail, no gesture support
[  1884.003] (--) UC-LOGIC Tablet WP5540U: Found x and y absolute axes
[  1884.003] (--) UC-LOGIC Tablet WP5540U: Found absolute tablet.
[  1884.003] (II) UC-LOGIC Tablet WP5540U: Configuring as tablet
[  1884.003] (**) UC-LOGIC Tablet WP5540U: YAxisMapping: buttons 4 and 5
[  1884.003] (**) UC-LOGIC Tablet WP5540U: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1884.003] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.4/1-2.4:1.0/input/input11/event11"
[  1884.003] (II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP5540U" (type: TABLET)
[  1884.003] (II) UC-LOGIC Tablet WP5540U: initialized for absolute axes.
[  1884.003] (**) UC-LOGIC Tablet WP5540U: (accel) keeping acceleration scheme 1
[  1884.003] (**) UC-LOGIC Tablet WP5540U: (accel) acceleration profile 0
[  1884.003] (**) UC-LOGIC Tablet WP5540U: (accel) acceleration factor: 2.000
[  1884.003] (**) UC-LOGIC Tablet WP5540U: (accel) acceleration threshold: 4
[  1884.004] (II) config/udev: Adding input device UC-LOGIC Tablet WP5540U (/dev/input/mouse1)
[  1884.004] (II) No input driver/identifier specified (ignoring)
[  1884.004] (II) config/udev: Adding input device UC-LOGIC Tablet WP5540U (/dev/input/event12)
[  1884.004] (**) UC-LOGIC Tablet WP5540U: Applying InputClass "evdev pointer catchall"
[  1884.004] (II) Using input driver 'evdev' for 'UC-LOGIC Tablet WP5540U'
[  1884.004] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1884.004] (**) UC-LOGIC Tablet WP5540U: always reports core events
[  1884.004] (**) UC-LOGIC Tablet WP5540U: Device: "/dev/input/event12"
[  1884.004] (--) UC-LOGIC Tablet WP5540U: Found 3 mouse buttons
[  1884.004] (--) UC-LOGIC Tablet WP5540U: Found scroll wheel(s)
[  1884.004] (--) UC-LOGIC Tablet WP5540U: Found relative axes
[  1884.004] (--) UC-LOGIC Tablet WP5540U: Found x and y relative axes
[  1884.004] (II) UC-LOGIC Tablet WP5540U: Configuring as mouse
[  1884.004] (II) UC-LOGIC Tablet WP5540U: Adding scrollwheel support
[  1884.004] (**) UC-LOGIC Tablet WP5540U: YAxisMapping: buttons 4 and 5
[  1884.004] (**) UC-LOGIC Tablet WP5540U: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1884.004] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.4/1-2.4:1.0/input/input12/event12"
[  1884.004] (II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP5540U" (type: MOUSE)
[  1884.004] (II) UC-LOGIC Tablet WP5540U: initialized for relative axes.
[  1884.004] (**) UC-LOGIC Tablet WP5540U: (accel) keeping acceleration scheme 1
[  1884.004] (**) UC-LOGIC Tablet WP5540U: (accel) acceleration profile 0
[  1884.004] (**) UC-LOGIC Tablet WP5540U: (accel) acceleration factor: 2.000
[  1884.004] (**) UC-LOGIC Tablet WP5540U: (accel) acceleration threshold: 4
[  1884.005] (II) config/udev: Adding input device UC-LOGIC Tablet WP5540U (/dev/input/mouse2)




There is a link here to everything I went through to try to determine the problem with mine too ..... you may want to look through this later on  ***[LINK]("https://sites.google.com/site/problems7730zg/home/wizardpen-0-7-3")***

Can be a pain in the neck to get it going but once you do it then its set for as long as you keep this version
of Ubuntu .....

---

### Post by Ellume on 2011-06-23
Alright the version of wizardpen I have installed is 0.7.4-3maverick0.

my Xorg.0.log is
```
[    18.880] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    18.880] X Protocol Version 11, Revision 0
[    18.880] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    18.880] Current Operating System: Linux Shimmer 2.6.35-28-generic-pae #50-Ubuntu SMP Fri Mar 18 20:43:15 UTC 2011 i686
[    18.880] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=80d7f48f-54e3-4112-9530-24f95f905d22 ro quiet splash
[    18.880] Build Date: 09 January 2011  12:14:58PM
[    18.880] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    18.880] Current version of pixman: 0.18.4
[    18.880] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    18.880] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.880] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun 22 20:47:51 2011
[    18.881] (==) Using config file: "/etc/X11/xorg.conf"
[    18.881] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.979] (==) ServerLayout "Layout0"
[    18.979] (**) |-->Screen "Screen0" (0)
[    18.979] (**) |   |-->Monitor "Monitor0"
[    18.979] (**) |   |-->Device "Device0"
[    18.979] (==) Automatically adding devices
[    18.979] (==) Automatically enabling devices
[    18.979] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.979] 	Entry deleted from font path.
[    18.980] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    18.980] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.980] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.980] (II) Loader magic: 0x81f9b00
[    18.980] (II) Module ABI versions:
[    18.980] 	X.Org ANSI C Emulation: 0.4
[    18.980] 	X.Org Video Driver: 8.0
[    18.980] 	X.Org XInput driver : 11.0
[    18.980] 	X.Org Server Extension : 4.0
[    18.980] (--) PCI:*(0:1:0:0) 10de:0622:19f1:0765 rev 161, Mem @ 0xcc000000/16777216, 0xb0000000/268435456, 0xca000000/33554432, I/O @ 0x00009c00/128, BIOS @ 0x????????/524288
[    18.981] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.981] (II) LoadModule: "extmod"
[    19.008] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    19.008] (II) Module extmod: vendor="X.Org Foundation"
[    19.008] 	compiled for 1.9.0, module version = 1.0.0
[    19.008] 	Module class: X.Org Server Extension
[    19.008] 	ABI class: X.Org Server Extension, version 4.0
[    19.008] (II) Loading extension MIT-SCREEN-SAVER
[    19.008] (II) Loading extension XFree86-VidModeExtension
[    19.008] (II) Loading extension XFree86-DGA
[    19.008] (II) Loading extension DPMS
[    19.008] (II) Loading extension XVideo
[    19.008] (II) Loading extension XVideo-MotionCompensation
[    19.008] (II) Loading extension X-Resource
[    19.008] (II) LoadModule: "dbe"
[    19.009] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    19.009] (II) Module dbe: vendor="X.Org Foundation"
[    19.009] 	compiled for 1.9.0, module version = 1.0.0
[    19.009] 	Module class: X.Org Server Extension
[    19.009] 	ABI class: X.Org Server Extension, version 4.0
[    19.009] (II) Loading extension DOUBLE-BUFFER
[    19.009] (II) LoadModule: "glx"
[    19.009] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    19.028] (II) Module glx: vendor="NVIDIA Corporation"
[    19.028] 	compiled for 4.0.2, module version = 1.0.0
[    19.028] 	Module class: X.Org Server Extension
[    19.028] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 07:01:31 PDT 2010
[    19.028] (II) Loading extension GLX
[    19.028] (II) LoadModule: "record"
[    19.029] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    19.029] (II) Module record: vendor="X.Org Foundation"
[    19.029] 	compiled for 1.9.0, module version = 1.13.0
[    19.029] 	Module class: X.Org Server Extension
[    19.029] 	ABI class: X.Org Server Extension, version 4.0
[    19.029] (II) Loading extension RECORD
[    19.029] (II) LoadModule: "dri"
[    19.029] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.029] (II) Module dri: vendor="X.Org Foundation"
[    19.029] 	compiled for 1.9.0, module version = 1.0.0
[    19.029] 	ABI class: X.Org Server Extension, version 4.0
[    19.029] (II) Loading extension XFree86-DRI
[    19.029] (II) LoadModule: "dri2"
[    19.030] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.030] (II) Module dri2: vendor="X.Org Foundation"
[    19.030] 	compiled for 1.9.0, module version = 1.2.0
[    19.030] 	ABI class: X.Org Server Extension, version 4.0
[    19.030] (II) Loading extension DRI2
[    19.030] (II) LoadModule: "nvidia"
[    19.030] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    19.030] (II) Module nvidia: vendor="NVIDIA Corporation"
[    19.030] 	compiled for 4.0.2, module version = 1.0.0
[    19.030] 	Module class: X.Org Video Driver
[    19.030] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 06:37:13 PDT 2010
[    19.030] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    19.030] (++) using VT number 7

[    19.031] (II) Loading sub module "fb"
[    19.031] (II) LoadModule: "fb"
[    19.032] (II) Loading /usr/lib/xorg/modules/libfb.so
[    19.032] (II) Module fb: vendor="X.Org Foundation"
[    19.032] 	compiled for 1.9.0, module version = 1.0.0
[    19.032] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    19.032] (II) Loading sub module "wfb"
[    19.032] (II) LoadModule: "wfb"
[    19.032] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    19.032] (II) Module wfb: vendor="X.Org Foundation"
[    19.032] 	compiled for 1.9.0, module version = 1.0.0
[    19.032] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    19.032] (II) Loading sub module "ramdac"
[    19.032] (II) LoadModule: "ramdac"
[    19.032] (II) Module "ramdac" already built-in
[    19.032] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    19.032] (==) NVIDIA(0): RGB weight 888
[    19.032] (==) NVIDIA(0): Default visual is TrueColor
[    19.032] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    19.032] (**) NVIDIA(0): Enabling RENDER acceleration
[    19.032] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    19.032] (II) NVIDIA(0):     enabled.
[    20.534] (II) NVIDIA(0): NVIDIA GPU GeForce 9600 GT (G94) at PCI:1:0:0 (GPU-0)
[    20.534] (--) NVIDIA(0): Memory: 524288 kBytes
[    20.534] (--) NVIDIA(0): VideoBIOS: 62.94.11.00.05
[    20.534] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    20.534] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    20.534] (--) NVIDIA(0): Connected display device(s) on GeForce 9600 GT at PCI:1:0:0
[    20.534] (--) NVIDIA(0):     WYT MNT-ANALOG (CRT-0)
[    20.534] (--) NVIDIA(0): WYT MNT-ANALOG (CRT-0): 400.0 MHz maximum pixel clock
[    20.597] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    20.597] (==) NVIDIA(0): 
[    20.597] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    20.597] (==) NVIDIA(0):     will be used as the requested mode.
[    20.597] (==) NVIDIA(0): 
[    20.597] (II) NVIDIA(0): Validated modes:
[    20.597] (II) NVIDIA(0):     "nvidia-auto-select"
[    20.597] (II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
[    20.614] (--) NVIDIA(0): DPI set to (98, 96); computed from "UseEdidDpi" X config
[    20.614] (--) NVIDIA(0):     option
[    20.614] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    20.615] (--) Depth 24 pixmap format is 32 bpp
[    20.615] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    20.615] (II) NVIDIA(0): Initialized GPU GART.
[    20.619] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    20.659] (II) Loading extension NV-GLX
[    20.673] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    20.677] (==) NVIDIA(0): Disabling shared memory pixmaps
[    20.677] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    20.677] (==) NVIDIA(0): Backing store disabled
[    20.677] (==) NVIDIA(0): Silken mouse enabled
[    20.687] (**) NVIDIA(0): DPMS enabled
[    20.687] (II) Loading extension NV-CONTROL
[    20.688] (II) Loading extension XINERAMA
[    20.688] (II) Loading sub module "dri2"
[    20.688] (II) LoadModule: "dri2"
[    20.688] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.688] (II) NVIDIA(0): [DRI2] Setup complete
[    20.688] (==) RandR enabled
[    20.688] (II) Initializing built-in extension Generic Event Extension
[    20.688] (II) Initializing built-in extension SHAPE
[    20.688] (II) Initializing built-in extension MIT-SHM
[    20.688] (II) Initializing built-in extension XInputExtension
[    20.688] (II) Initializing built-in extension XTEST
[    20.688] (II) Initializing built-in extension BIG-REQUESTS
[    20.688] (II) Initializing built-in extension SYNC
[    20.688] (II) Initializing built-in extension XKEYBOARD
[    20.688] (II) Initializing built-in extension XC-MISC
[    20.688] (II) Initializing built-in extension SECURITY
[    20.688] (II) Initializing built-in extension XINERAMA
[    20.688] (II) Initializing built-in extension XFIXES
[    20.688] (II) Initializing built-in extension RENDER
[    20.688] (II) Initializing built-in extension RANDR
[    20.688] (II) Initializing built-in extension COMPOSITE
[    20.688] (II) Initializing built-in extension DAMAGE
[    20.688] (II) Initializing built-in extension GESTURE
[    20.691] (II) Initializing extension GLX
[    20.715] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.722] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    20.722] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.722] (II) LoadModule: "evdev"
[    20.723] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.723] (II) Module evdev: vendor="X.Org Foundation"
[    20.723] 	compiled for 1.9.0, module version = 2.3.2
[    20.723] 	Module class: X.Org XInput Driver
[    20.723] 	ABI class: X.Org XInput driver, version 11.0
[    20.723] (**) Power Button: always reports core events
[    20.723] (**) Power Button: Device: "/dev/input/event1"
[    20.736] (II) Power Button: Found keys
[    20.736] (II) Power Button: Configuring as keyboard
[    20.736] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    20.736] (**) Option "xkb_rules" "evdev"
[    20.736] (**) Option "xkb_model" "pc105"
[    20.736] (**) Option "xkb_layout" "us"
[    20.738] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    20.738] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.738] (**) Power Button: always reports core events
[    20.738] (**) Power Button: Device: "/dev/input/event0"
[    20.752] (II) Power Button: Found keys
[    20.752] (II) Power Button: Configuring as keyboard
[    20.752] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    20.752] (**) Option "xkb_rules" "evdev"
[    20.752] (**) Option "xkb_model" "pc105"
[    20.752] (**) Option "xkb_layout" "us"
[    20.753] (II) config/udev: Adding input device H850S (/dev/input/event3)
[    20.753] (**) H850S: Applying InputClass "evdev pointer catchall"
[    20.753] (**) H850S: Applying InputClass "evdev tablet catchall"
[    20.753] (**) H850S: always reports core events
[    20.753] (**) H850S: Device: "/dev/input/event3"
[    20.768] (II) H850S: Found 10 mouse buttons
[    20.768] (II) H850S: Found scroll wheel(s)
[    20.768] (II) H850S: Found relative axes
[    20.768] (II) H850S: Found x and y relative axes
[    20.768] (II) H850S: Found absolute axes
[    20.768] (II) evdev-grail: failed to open grail, no gesture support
[    20.768] (II) H850S: Found x and y absolute axes
[    20.768] (II) H850S: Found absolute tablet.
[    20.768] (II) H850S: Configuring as tablet
[    20.768] (**) H850S: YAxisMapping: buttons 4 and 5
[    20.768] (**) H850S: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.768] (II) XINPUT: Adding extended input device "H850S" (type: TABLET)
[    20.768] (WW) H850S: touchpads, tablets and touchscreens ignore relative axes.
[    20.768] (II) H850S: initialized for absolute axes.
[    20.769] (II) config/udev: Adding input device H850S (/dev/input/mouse0)
[    20.769] (II) No input driver/identifier specified (ignoring)
[    20.769] (II) config/udev: Adding input device H850S (/dev/input/event4)
[    20.769] (**) H850S: Applying InputClass "evdev pointer catchall"
[    20.769] (**) H850S: Applying InputClass "evdev keyboard catchall"
[    20.769] (**) H850S: always reports core events
[    20.769] (**) H850S: Device: "/dev/input/event4"
[    20.784] (II) H850S: Found 3 mouse buttons
[    20.784] (II) H850S: Found scroll wheel(s)
[    20.784] (II) H850S: Found relative axes
[    20.784] (II) H850S: Found x and y relative axes
[    20.784] (II) H850S: Found keys
[    20.784] (II) H850S: Configuring as mouse
[    20.784] (II) H850S: Configuring as keyboard
[    20.784] (**) H850S: YAxisMapping: buttons 4 and 5
[    20.784] (**) H850S: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.784] (II) XINPUT: Adding extended input device "H850S" (type: KEYBOARD)
[    20.784] (**) Option "xkb_rules" "evdev"
[    20.784] (**) Option "xkb_model" "pc105"
[    20.784] (**) Option "xkb_layout" "us"
[    20.784] (II) H850S: initialized for relative axes.
[    20.785] (II) config/udev: Adding input device H850S (/dev/input/mouse1)
[    20.785] (II) No input driver/identifier specified (ignoring)
[    20.785] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event5)
[    20.785] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[    20.785] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[    20.785] (**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event5"
[    20.800] (II) Logitech USB-PS/2 Optical Mouse: Found 12 mouse buttons
[    20.800] (II) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[    20.800] (II) Logitech USB-PS/2 Optical Mouse: Found relative axes
[    20.800] (II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[    20.800] (II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[    20.800] (**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[    20.800] (**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.800] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[    20.800] (II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[    20.800] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse2)
[    20.800] (II) No input driver/identifier specified (ignoring)
[    20.804] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    20.804] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    20.804] (**) AT Translated Set 2 keyboard: always reports core events
[    20.804] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    20.816] (II) AT Translated Set 2 keyboard: Found keys
[    20.816] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    20.816] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    20.816] (**) Option "xkb_rules" "evdev"
[    20.816] (**) Option "xkb_model" "pc105"
[    20.816] (**) Option "xkb_layout" "us"
```

I really appreciate the help guys, thanks.

---

### Post by Favux on 2011-06-23
OK, your Xorg.0.log shows the tablet is on the evdev X driver which is to be expected and why it doesn't work:
```
[    20.753] (II) config/udev: Adding input device H850S (/dev/input/event3)
[    20.753] (**) H850S: Applying InputClass "evdev pointer catchall"
[    20.753] (**) H850S: Applying InputClass "evdev tablet catchall"
[    20.753] (**) H850S: always reports core events
[    20.753] (**) H850S: Device: "/dev/input/event3"
[    20.768] (II) H850S: Found 10 mouse buttons
[    20.768] (II) H850S: Found scroll wheel(s)
[    20.768] (II) H850S: Found relative axes
[    20.768] (II) H850S: Found x and y relative axes
[    20.768] (II) H850S: Found absolute axes
[    20.768] (II) evdev-grail: failed to open grail, no gesture support
[    20.768] (II) H850S: Found x and y absolute axes
[    20.768] (II) H850S: Found absolute tablet.
[    20.768] (II) H850S: Configuring as tablet
[    20.768] (**) H850S: YAxisMapping: buttons 4 and 5
[    20.768] (**) H850S: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.768] (II) XINPUT: Adding extended input device "H850S" (type: TABLET)
[    20.768] (WW) H850S: touchpads, tablets and touchscreens ignore relative axes.
[    20.768] (II) H850S: initialized for absolute axes.
[    20.769] (II) config/udev: Adding input device H850S (/dev/input/mouse0)
[    20.769] (II) No input driver/identifier specified (ignoring)
[    20.769] (II) config/udev: Adding input device H850S (/dev/input/event4)
[    20.769] (**) H850S: Applying InputClass "evdev pointer catchall"
[    20.769] (**) H850S: Applying InputClass "evdev keyboard catchall"
[    20.769] (**) H850S: always reports core events
[    20.769] (**) H850S: Device: "/dev/input/event4"
[    20.784] (II) H850S: Found 3 mouse buttons
[    20.784] (II) H850S: Found scroll wheel(s)
[    20.784] (II) H850S: Found relative axes
[    20.784] (II) H850S: Found x and y relative axes
[    20.784] (II) H850S: Found keys
[    20.784] (II) H850S: Configuring as mouse
[    20.784] (II) H850S: Configuring as keyboard
[    20.784] (**) H850S: YAxisMapping: buttons 4 and 5
[    20.784] (**) H850S: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.784] (II) XINPUT: Adding extended input device "H850S" (type: KEYBOARD)
[    20.784] (**) Option "xkb_rules" "evdev"
[    20.784] (**) Option "xkb_model" "pc105"
[    20.784] (**) Option "xkb_layout" "us"
[    20.784] (II) H850S: initialized for relative axes.
[    20.785] (II) config/udev: Adding input device H850S (/dev/input/mouse1)
[    20.785] (II) No input driver/identifier specified (ignoring)
```

Alright, 0.7.4-3maverick0 indicates it is the PPA driver for Maverick.  Don't understand why there isn't a wizardpen.conf file.  All you should need to do is put a working one in and the tablet should be on the wizardpen X driver and work.

It took some digging but I think I've found the current copy of it, or close to.  Something like:
```
Section "InputClass"
   Identifier      "wizardpen"
   MatchIsTablet   "on"
   MatchDevicePath "/dev/input/event*"
   MatchTag        "wizardpen"
   Driver          "wizardpen"
EndSection

Section "InputClass"
   Identifier      "wizardpen ignore mouse dev"
   MatchDevicePath "/dev/input/mouse*"
   MatchTag        "wizardpen"
   Option          "ignore"     "true"
EndSection
```
The tag is coming from udev rules that the PPA packaging puts in.  Sort of doubt that'll work for you but give it a try.  First check again that the wizardpen.conf isn't there.  Create the file with:
```
gksudo gedit /usr/share/X11/xorg.conf.d/70-wizardpen.conf
```
Copy and paste the above contents into it.  Save, Close and reboot.

If that doesn't work I'll have a modified one ready for you.

---

### Post by Favux on 2011-06-23
If that doesn't work replace the 70-wizardpen.conf contents with:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|H850S|KYE Systems|Ace Cad"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|H850S|KYE Systems|Ace Cad"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```

---

### Post by Ellume on 2011-06-23
I might have cause some confusion. When I said I didn't have a wizardpen.conf I ment that specific name. I did and do have a 70-wizardpen.conf which I had posted earlier. Anyway, I made a backup of the one I had and tried both of the suggested versions. Restarted after for each but no change :(

I'm heading to bed now, going to look at this some more tomorrow. Really appreciate the help, thanks :)

---

### Post by Favux on 2011-06-23
Right, in post #15, thanks for reminding me.

OK, try:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|H850S|KYE Systems|Ace Cad"
    MatchProduct "H850S"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|H850S|KYE Systems|Ace Cad"
    MatchProduct "H850S"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```

---

### Post by Ellume on 2011-06-23
Thought I would try this quick thing before logging off. Glad I did. The tablet is working! :D

Seems a bit funny to use, like less responsive then the mouse, but this is my first time using a tablet too. I assume I'm going to need some button configuring or other such stuff, but I will look at it tomorrow.

Many thanks! If it wasn't for the help I probably would have returned it in frustration.

---

### Post by Ellume on 2011-06-29
Well this is a bit late but after that fix everything has worked just great. Took only a couple clicks in Gimp prefs to have it working perfect with it.

Many thanks again for all the help ^_^

---

### Post by Favux on 2011-06-29
You're welcome.  Glad it's working for you now.  :D

---

