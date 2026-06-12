---
title: "[SOLVED] Frustrated Newb: Belkin wireless USB can see networks but cannot connect!"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by Wazeem on 2007-12-05
Frustrated Newb: Belkin wireless USB can see networks but cannot connect!

To expand on the title. I am using a belkin wireless usb adapter F5D7050. The chipset I think is rt 2500 as the CD that came with the adapter has a system (the driver ???)  file with that name.

In ubuntu the surrounding connections can be seen but I cannot connect to any of them. My encryption is WPA and I know these have a problem BUT my neighbors connection which has no security applied doesn't work either.

[Ignore this as it is a rant]
The reason I am frustrated is because I did alot of research that led to nothing. IRC was a pain as most members just gave generic or unrelated asnswers or worse kept telling me to read the docs and wikis. I dont mind reading docs and wikis but they made no sense to me at all. That goes onto the non-irc frustration is that all help seems alien to me. I have never used linux before and all i see is command line instructions that scare me, heck i dont even know how to get to the command line thingy.[rant mode off]

Here is what i understand

I may need to try and connect via command line, but i dont know how to do this. I saw a tutorial from a member talking about this but like i said before i dont know where to type the commands.

It may be that i need to install the windows driver from my CD using ndiswrapper. However I dont know how to go about doing this. I looked at the CD and the only thing that resembles the driver is a "system file" but all tutorials/wikis talk about .exe files :S. Oh and I dont know where to type the commands.

I am a total newb so please help in lamen terms (and please dont tell me to read some wiki :()

Thanks Waseem

---

### Post by Threbus5 on 2007-12-05
OK,
I understand your frustration.

Several days ago I carried my laptop (running Ubuntu 7.10) into one of the "free high speed Internet" environments.
Because the laptop was configured to connect to a secure network using a fixed IP it listed the free network access points but would not connect to any of them. (Sounds similar to your experience.)

After selecting to use DHCP, removing the key and encryption from the wireless configuration, and restaring the laptop it connected to the free network. At least that demonstrated that it Could connect. (That seems your objective.) So, just to establish that the wireless card and computer work you might try those three steps. [these changes are made by selecting from the drop down main menu the system configuration for network]

Although many forum posts discuss ndiswrapper, because your wireless card detects the other networks, you may have a configuration issue and not an installation/driver problem.

After you establish that everything works to an open network, then establish the proper key and encryption method for your secure net.

Good luck

---

### Post by Wazeem on 2007-12-06
> **Threbus5 said:**
> snip

thanks but it wont connect. Any other suggestions?

---

### Post by miwaypet on 2007-12-06
I feel your pain. I had to go through hoops to get a wpn11 netgear usb antenna to work. It had to, because I have no wired connection to this desktop. Let me say upfront: this worked for me, I cannot guarentee that it will for you.

These are the instructions from the book: Hacking Ubuntu. They are what did it for me. I could not use the windows wireless driver utility. Why? You have to have an internet connection to download it through synaptic. 

Here goes:

1) Install ndiswrapper- at the command line type:

         sudo apt-get install ndiswrapper-utils

2)Insert your wireless usb disk. From the window showing the cd's contents drag and drop the contents to the desktop. The contents will be copied. Minimize the window and bring up the terminal again.

3)at the command line type:
          
         cd Desktop
 hit enter.

4)at the command line type:

         sudo ndiswrapper -i ./*your usb id*.inf

note: use the exact wording of the .inf file title: example-wpn11.inf

5)at the command line type:

          sudo modprobe ndiswrapper

this loads the kernal module.

6)at command line type: ifconfig -a

you should see your driver listed in the paragraph next to wlan0.

7)at the command line: 

             sudo bash -c 'echo "ndiswrapper" >> /etc/modules'

this causes the ndiswrapper and thus your driver to load at boot.


Note: the driver does not reload when you do a resteart. You can only load it from bootup.

8) at command line: ndiswrapper -l

will show your driver and if it is working.

Note; sometimes the system will hang while working these steps. Remove your usb stick untill you finish step 5.

Hope this helps.

---

### Post by jfinkels on 2007-12-06
To determine what kind of wireless ethernet adapter, type the following in the terminal (Application > Accessories > Terminal):```
lspci -v
``` and post the output here. There should be a section that says "Network controller". We need to know exactly what kind of adapter/chipset you have, so that we can update the drivers needed for the card appropriately.

Start taking a look on this page for some info while you wait for me to respond to your next post :) 

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

(scroll down to see a list of cards)

---

### Post by jfinkels on 2007-12-06
> **miwaypet said:**
> I feel your pain. I had to go through hoops to get a wpn11 netgear usb antenna to work. It had to, because I have no wired connection to this desktop. Let me say upfront: this worked for me, I cannot guarentee that it will for you.

[...]


I would not follow this procedure quite yet! We do not know the kind of wireless chipset the OP has, so the use of ndiswrapper may not be required!

---

### Post by Wazeem on 2007-12-06
Hi sorry I took a long time to do your test but i had to switch between XP and ubuntu (and my XP takes a long time to load).

its really long. Your command was pci based but my adapter is a usb so i took the initiative to try the usb command (was a guess but it worked). I have highlighted my device in bold to help.

> 00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
        Subsystem: Dell Unknown device 0142
        Flags: bus master, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: fc000000-fdffffff
        Prefetchable memory behind bridge: f0000000-f7ffffff

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0142
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at ff80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0142
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at ff60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0142
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at ff40 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 0142
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at fe300800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fe100000-fe2fffff

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device 0142
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]
        Memory at 20000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
        Subsystem: Dell Unknown device 0142
        Flags: medium devsel, IRQ 11
        I/O ports at dc80 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Dell Unknown device 0142
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at d800 [size=256]
        I/O ports at dc40 [size=64]
        Memory at fe300400 (32-bit, non-prefetchable) [size=512]
        Memory at fe300000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3) (prog-if 00 [VGA])
        Subsystem: nVidia Corporation Unknown device 015a
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Memory at f4000000 (32-bit, prefetchable) [size=64M]
        Memory at f3f80000 (32-bit, prefetchable) [size=512K]
        Expansion ROM at f0000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:01.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02) (prog-if 00 [Generic])
        Subsystem: Dell Unknown device 0002
        Flags: bus master, fast devsel, latency 64, IRQ 16
        Memory at fe1ff000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ecf0 [size=16]
        Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
        Subsystem: Dell Unknown device 0142
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at fe1fe000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ec80 [size=64]
        Capabilities: <access denied>

waseem@waseem-desktop:~$ lsusb -v

**Bus 004 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi**
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x050d Belkin Components
  idProduct          0x7050 F5D7050 ver 1000 WiFi
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              300mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 004 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
      bInterfaceProtocol      0 Full speed hub
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
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 003 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
      bInterfaceProtocol      0 Full speed hub
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
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 002 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
      bInterfaceProtocol      0 Full speed hub
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
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
      bInterfaceProtocol      0 Full speed hub
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
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1) 


---

### Post by Vadi on 2007-12-06
Hey,

I have similar card, but mine goes into the laptop slot.

Anyway, here's what I did to get it working:

> Download this:

[ftp://202.65.194.212/cn/wlan/Driver%20%20ver.1097_Vista%20ver.1102_UI%20ver.6.rar](ftp://202.65.194.212/cn/wlan/Driver%20%20ver.1097_Vista%20ver.1102_UI%20ver.6.rar)

Unarchive it, using the terminal, navigate to the RTL8185/WINXP directory inside it, then do

sudo ndiswrapper -i net8185.inf

And then

sudo ndiswrapper -a 1799:701f net8185

And when I did ndiswrapper -l, it tells me this:

net8185 : driver installed
        device (1799:701F) present

Now reboot. There probably is some fancy command for getting the card recognized right away, but I don't know it, so rebooting is easier.

After I rebooted, the card was working for me - network manager saw it right away and all. A bit odd, I thought I'd have to do the "sudo ifconfig wlan0 up" command first, but apparently not.



If you'll get stuck on any of the steps, feel free to post, I'll explain it.

---

### Post by Wazeem on 2007-12-06
> **Vadi said:**
> Hey,

I have similar card, but mine goes into the laptop slot.

Anyway, here's what I did to get it working:



If you'll get stuck on any of the steps, feel free to post, I'll explain it.

While I was trying to solve the problem earlier i managed to install ndiswrapper but when i tried the -i command it would give me an error. Something like i don't have access to the ndiswrapper folder so it cant create the file. I used the ubuntu gui to go to the ndiswrapper folder and i really couldn't add or edit files :S.

---

### Post by jfinkels on 2007-12-06
Okay so you have a Belkin F5D7050 ver 1000 card. The instructions given here [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29) are for ver 3000, but you suggest that they use a similar chipset so we will give this a try. Follow the directions on that site and let me know if you have any trouble. The parts in the colored boxes are commands to be entered in the terminal.

At some points it may ask you to install packages or download files. If you do not have a wired connection available for your laptop, you will need to download them from some system that has an internet connection and copy the files over to your Ubuntu system. Then whenever you see ```
sudo apt-get install build-essential
``` for exmample, you will need to install it by using the command:```
sudo dpkg -i build-essential_11.3ubuntu1_i386.deb
``` or something similar, depending on the exact name of the file.

Whenever you see the command "wget", that's another thing you will have to download from an internet-connected computer and transfer to your Ubuntu system.

Some other advice: download the "checkinstall" package from [http://packages.ubuntu.com](http://packages.ubuntu.com), install it using the command:```
sudo dpkg -i checkinstall*.deb
```and replace the wores "sudo make install" with the words "sudo checkinstall" in the instructions on the Wiki page. This will give you an easy to handle .deb package which will allow you to easily uninstall and reinstall whatever program you are building from source.


EDIT: SOME NOTES ON THE TUTORIAL THAT ARE SPECIFIC TO YOUR CASE:

You may want to add```
blacklist rt2500
```in addition to the other blacklist lines. 

You may need to download a different driver than he is using. Be sure to go to the ralink website and download the appropriate one.

In the part where he does:```
#define RT73_USB_DEVICES { \
 {USB_DEVICE(0x050d,0x705a)}, /* Belkin F5D7050 ver 3000 */      \
 {USB_DEVICE(0x13b1,0x0020)}, /* Linksys WUSB54GC */             \
 {USB_DEVICE(0x2001,0x3c00)}, /* D-LINK DWL-G122 Rev: B1  */     \
 {USB_DEVICE(0x07d1,0x3c03)}, /* D-LINK DWL-G122 Rev: C1  */     \
 {USB_DEVICE(0x148f,0x2573)}, /* Ralink */      \
```
You will need to change the first so that instead of "0x705a", it says "0x7050", as you told us in the output of your lsusb command.

Since he is doing rt73, you may need to do ```
modprobe rt2500
```instead. I'm not certain all of these, though, because I am not doing them myself.

---

### Post by rustybronco on 2007-12-07
you said it was a usb device, correct?
post the output of...
lshw -C network   and   lsusb
or what I am looking for is the chipset, such as rt2500usb for your wireless device.
May i also suggest if you are having an issue with a specific device (video, wireless, ect.)
post in the main section applicable to the device in the future, you will have a better chance getting your issue resolved, speaking for myself I rarely visit more than one or two areas.

> To expand on the title. I am using a belkin wireless usb adapter F5D7050. The chipset I think is rt 2500 as the CD that came with the adapter has a system (the driver ???) file with that name.
if it is a rt2500usb this should work with 7.10 (gutsy) and possibly 7.04 (fiesty)    [http://ubuntuforums.org/showthread.php?t=588045&highlight=wusb54gv4](http://ubuntuforums.org/showthread.php?t=588045&highlight=wusb54gv4)
you also requested that we don't have you read some wiki, o.k., read kevdogs finest in my signature for additional help if needed.
Dale.

---

### Post by Vadi on 2007-12-07
Oh shoot, yes ignore my instructions - my card is version 7000.

---

### Post by Wazeem on 2007-12-07
:guitar:

Got it to work! Really pleased :D. In the end I tried various things but got it work with ndiswrapper + GUI. The command line version of ndiswrapper didn't work well (probably due to my lack of knowledge) but the GUI worked like a charm. It turned out that i didnt need to use the terminal at all for the solution :D.

So the problem is solved. Thanks to all those that helped. I learned quite a few things about command line and linux.

EDIT: For those that might have an identical problem. Get the ndiswrapper and the ndisgtk from a windows machine and transfer them to the ubuntu system (as i was dual booting i just transfered the files over to the HDD). In ubuntu install both and then use the ndisgtk gui to remove the active driver (it should show rt2500usb) and then install the rt2500usb.inf file from your CD. If you dont have the CD available PM and i'll upload the driver.

Oh BTW i couldn't connect to the neighbors open network but my WPA encrypted network worked, Nothing major but just something to think about.

---

### Post by rustybronco on 2007-12-07
> **rustybronco said:**
> you said it was a usb device, correct?
post the output of...
lshw -C network   and   lsusb
or what I am looking for is the chipset.

---

### Post by jfinkels on 2007-12-07
> **Wazeem said:**
> 
Got it to work! 

Great!! I'm sorry I gave you such complicated instructions instead of such a simple solution :P Sometimes, in life you're totally, 100% wrong. But that's okay :D

Let us know if there's anything else we can help you with.

---

### Post by Wazeem on 2007-12-07
> **jfinkels said:**
> Great!! I'm sorry I gave you such complicated instructions instead of such a simple solution :P Sometimes, in life you're totally, 100% wrong. But that's okay :D

Let us know if there's anything else we can help you with.

Yes there is :(.

After I restarted the comp the wireless feature stopped working completely. Now I cant detect any networks and if I manually input the network it wont connect or it will connect but be at 0% transfer speed.

Can someone help?

EDIT: Solved the current prob too. It seems after you install the new drivers you need to make it so that they are loaded in every time you load ubuntu. 

Here are the commands that do this for you...

sudo nano /etc/modules

add the word ndiswrapper there on it's own line so it will be loaded on reboot and then save the file

and do the following command to activate the wireless for the current session.

sudo modprobe ndiswrapper

---

