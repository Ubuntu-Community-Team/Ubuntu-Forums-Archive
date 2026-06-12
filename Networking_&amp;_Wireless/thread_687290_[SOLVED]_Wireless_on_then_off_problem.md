---
title: "[SOLVED] Wireless on then off problem??"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by timbosity on 2008-02-04
ok I know this seems to be a recurring problem and the solution may lie somewhere out there. ill keep looking. The thing is id like to understand a bit more about it hence this post. 

basically, connection to wireless happens. Web is on for about five minutes after I login then disconnects and I am unable to reestablish a connection, usually resorting to no internet or some other wired alternative (this is from my laptop and i tend to connect up through about four or five different points). The usb dongle thing that works as my wireless connector picks up the networks (most of the time) and works fine in XP. Im nearly at the stage where no internet is better than XP so Id really like to get this thing sorted out. im not sure what the specs are to the wireless usb thing but on it is written inventel UR054g. Ill be back to this post with the iwconfig and lsusb -v l less output in a little while but if anyone has any explanation as to why this happens id be extra grateful!!

Tim

---

### Post by hyperair on 2008-02-04
I think nothing much can really be done without the above outputs posted. lspci -v doesn't need |less though. You just want to copy all the output.

---

### Post by timbosity on 2008-02-04
ok,
when i log in wireless gets the full blue bars connects etc.. I was able to access synaptic download and install a couple of packages etc no bother. connection was fine and dandy. Then I launched firefox. still connection is fine and everything. I load my first page. Google works ok do a search. here things start to go downhill. Connection goes right down to about 30 % then 0 then disconnects. No way to get connection again...


so after login route gives this:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
    
default         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0


iwconfig gives me this:

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"eircom4061 0020"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:0F:CC:83:1F:DC   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=75/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beaco

lshw -C network gives this:

 *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0b:6b:9a:d9:ef
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.8 multicast=yes wireless=IEEE 802.11g

 sudo iwlist wlan0 scan gives me this:

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:CC:83:1F:DC
                    ESSID:"eircom4061 0020"
                    Mode:Master
                    Channel:7
                    Frequency:2.442 GHz
                    Signal level=37/100  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000000ee24592218

and finally the usb thing gives me this:

Bus 001 Device 003: ID 13fe:1a00  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x13fe 
  idProduct          0x1a00 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
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
    MaxPower              200mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
 wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0

Bus 001 Device 002: ID 1435:0427  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1435 
  idProduct          0x0427 
  bcdDevice           10.20
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           53
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           5
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
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
          bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1

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


whats it all about?

I cant see a driver anywhere for my wifi device or even a manufacturer or anything that resembles what kind of device it could be. Any help?

Why is it it is fine connected for synaptic and other command line download things but not internet? Why does it die when it connects to internet?

---

### Post by sneeks on 2008-02-04
hi there,i had this problem with my first full install(went like a breeze)of gutsy,usb dongle just would not hold.
after much thought and two pints of beer brain engaged and solution arrived.
open router and go to wireless settings.
set the router to the same speed as your dongle..eg b,g,n
take it from automatic channel and set it above 5,so your basically preselecting the channel,iv'e set mine to 6.
change security to wpa psk.
taadaaa
it now never drops the connection at any time.
i have used this trick on windows machines when dongles(especially belkin)play up
give it a try.

---

### Post by timbosity on 2008-02-06
Okay still havent managed to solve my problem. wireless connection appears to be very very unreliable with whatever set up I have ie I have actually had a full session where I had access to internet for about an hour (using firefox) but no access to repositories and then another session where there was no internet but access to synaptic. the outputs above are from a session where I had access to synaptic but no internet.  I have been reading around and maybe I need to install some extra driver for my usb wireless dongle?? anyone???

---

### Post by b0rt on 2008-02-06
I have the exact same trouble, also using a usb wireless dongle, mine is a Cnet  	Wireless-G USB Dongle  	CWD-854. Did you manage to fix this? plz some help, its really annoying :(

---

### Post by hyperair on 2008-02-06
Anyone tried ndiswrapper + windows drivers yet? Install ndisgtk from Synaptic, and go to System->Administration->Windows Wireless Drivers.

---

### Post by timbosity on 2008-02-07
OK. i havent had a chance to try out ndiswrapper + windows drivers etc... yet. The idea of this post was to try and understand WHY and HOW it is possible that consistantly (now for the past week three or four times a day) I log in, there is full connection (80-90%) to the wireless network, and then internet pages load really quickly and well for about 5 minutes, and then nada, nothing gone, no more wireless internet for me in Ubuntu. 

There doesnt seem to be a driver associated with the wlan0 interface (from the lshw -C network output above) and yet it connects?

Anyone?

---

### Post by timbosity on 2008-02-11
still trying at this blasted wireless thing. How do i get ndiswrapper to manage my usb dongle wifi adapter thingee? Im at a loss at exactly what im supposed to do. Im still getting the wireless connection for about five minutes after login then nothing... I just dont get how it could be connected, "get" the signal from the wireless router but not be able to stay connected... 
 In the meantime any pointers on how to get ndiswrapper to become the driver associated with wlan0 much appreciate... Maybe a step towards salvation??:confused:

---

### Post by hyperair on 2008-02-12
Install 'ndisgtk' from Synaptic. Use it to install drivers. Then type "ndiswrapper -l". Post the output here.

---

### Post by timbosity on 2008-02-12
prisma02 : driver installed
Thats the output from ndiswrapper -l

I got that driver from here [ftp://ftp.unex.com.tw/Drivers/Wireless/](ftp://ftp.unex.com.tw/Drivers/Wireless/) along with the *.sys file. Did I need the *.dll file as well? was there supposed to be other drivers to go with that one?

I blacklisted the linux drivers which could have been causing trouble but still not working... Been going commando but though I'd have a look at the ndiswrapper gui just in case id missed somehting. Its telling me that prisma02 is installed and the hardware is there too...

thanks for popping in and helping

Where to next?

I found a thread dealing with this wireless thing and pretty much followed instructions (it was a rather messy thread...). For the moment im just connecting with ethernet (4-5 different locations...) would be handier with wifi but hey, Im not complaining cause Xubuntu really breathed some new life into my 256, 6 yr old laptop!!

lovin the linux :KS

---

### Post by hyperair on 2008-02-12
Please post the full output of ndiswrapper -l. I need the extra info to tell you what to do next. 

EDIT: My bad, I didn't notice that you posted the full thing already. Notice that it says driver installed only, but not hardware present. It means that it cannot use the driver for your hardware. Could you post the contents of "lspci -nn"?

My ndiswrapper -l output is:
```
airplus : driver installed
	device (104C:8400) present (alternate driver: acx)
```

---

### Post by timbosity on 2008-02-12
allright. Sorry for the time lapse between posts. This wireless thing isnt at the top of my priorities list right now. thank you again for the help.
The reason for the lack of hardware in previous post is that it wasnt plugged in... sorry about that...
 output now says:
 prisma2: driver installed
              device (1435:0427) present (alternate driver: p54usb)

FROM lspci -nn:

00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] [11
06:0305] (rev 80)
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP] 
[1106:8305]
00:08.0 CardBus bridge [0607]: Texas Instruments PCI1420 PC card Cardbus Control
ler [104c:ac51]
00:08.1 CardBus bridge [0607]: Texas Instruments PCI1420 PC card Cardbus Control
ler [104c:ac51]
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8231 [PCI-to-ISA Bridge] [11
06:8231] (rev 10)
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT
823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Con
troller [1106:3038] (rev 1e)
00:11.4 Bridge [0680]: VIA Technologies, Inc. VT8235 ACPI [1106:8235] (rev 10)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT82C686 AC97
 Audio Controller [1106:3058] (rev 40)
00:11.6 Communication controller [0780]: VIA Technologies, Inc. AC'97 Modem Cont
roller [1106:3068] (rev 20)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [11
06:3065] (rev 51)
01:00.0 VGA compatible controller [0300]: S3 Inc. VT8636A [ProSavage KN133] AGP4
X VGA Controller (TwisterK) [5333:8d02] (rev 01)

cant see the device there... the green light is on though...

and still same thing happens when i try and connect to network. It connects (picks up that there is a network) then dies almost instantly...
should I be blacklisting the p54usb driver?
 why doesnt lshw -C network show that the wlan0 is associated with ndiswrapper and prisma02 driver?:
 *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0b:6b:9a:d9:ef
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

what is missing here???

---

### Post by hyperair on 2008-02-13
Ah I see!

I think that'll be because your ndiswrapper module was not loaded upon startup. Here's what you have to do: 
```
sudo ndiswrapper -m
```

Then try ```
sudo modprobe ndiswrapper
```

See if your wireless works now? =\

Also, if it still doesn't work, try:
```
sudo iwconfig wlan0 essid <ssid of your access point> enc s:<key (ascii)> open
```
or if you use restricted key encryption:
```
sudo iwconfig wlan0 essid <ssid> enc s:<key (ascii)> restricted
```
or if you don't use the ascii key:
```
sudo iwconfig wlan0 essid <ssid> enc <key (hex)> <open or restricted>
```

Then check the status of your wireless:
```
iwconfig
```

---

### Post by 1993cb7 on 2008-02-13
Wow awesome....im about to go Ubuntu in a few weeks and im using the Belkin fd58030 or something like that and i was hoping there was an answer to this.

Keep up the good work guys!!!

---

### Post by timbosity on 2008-02-14
ok after following those insructions and the ones from kevdogs tutorial on how to connect wireless commando style this is what iwconfig looks like with still no sign of ndiswrapper + prisma02 being associated driver to my wireless device, which by the way remains undetected except as    device (1435:0427)...

output of ndiswrapper -l:

prisma02 : driver installed
        device (1435:0427) present (alternate driver: p54usb)

output of sudo ndiswrapper -m:

module configuration already contains alias directive

output of iwconfig:

   IEEE 802.11g  ESSID:"eircom6530 2240"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0F:CC:D5:8B:6C   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

BY the BY, when I log in with the yoke connected its still connecting to the wireless network fine for about a minute then dying and not connecting again (through network manager applet thingee)

Im stuck in the room with the modem. I really want to go hang out in the sitting room on the buddha bag which is way more comfortable.

---

### Post by timbosity on 2008-02-14
also meant to post output from lshw -C network: 

 *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0b:6b:9a:d9:ef
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

which is what tells me theres a problem with prisma02 and ndiswrapper not being associated with this device... in kevdogs tutorial thing this is what it shoudl look like:
 
*-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: wlan0
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **driver=ndiswrapper+lsbcmnds**driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11

---

### Post by hyperair on 2008-02-14
Have you blacklisted the p54usb module?

---

### Post by timbosity on 2008-02-14
hyperair you are legend!!
blacklisting the p54usb driver has done the trick.... fantastically fantastic. My faith in the ubuntu never faltered and look see now here I am on my giant bean bag!!!

Thank you for sticking through it 8)

---

### Post by hyperair on 2008-02-14
Hahaha great to hear that it finally worked for you =) Either way I actually thought about this at first, but you did say you had blacklisted the appropriate drivers. Could you post the guide you followed? I'd like to see it.

---

### Post by timbosity on 2008-02-14
yeah. Im not sure where I got the blacklisting idea from. It was something about speeding up wireless connection... I had a quick look for it there but couldnt locate the thread. 
the p54usb one wasnt on the list. I thnk maybe it was a thread for dapper?? these are the drivers I had blacklisted...

blacklist prism54
blacklist islsm
blacklist islsm_usb
blacklist islsm_device
blacklist islsm_pc

Again, thanks a million:guitar:i

---

### Post by hyperair on 2008-02-15
The only one you had to blacklist was the one I told you about.. And that's because it was listed there. ndiswrapper always lists the alternate driver (if available) so that you can blacklist that. If the alternate driver is available, ndiswrapper disables itself and takes a back seat.

---

### Post by timbosity on 2008-02-15
Thats good to know. Thanks.

---

### Post by hyperair on 2008-02-15
No problem.

---

### Post by b0rt on 2008-03-26
I have the exact same trouble. I have an usb dongle  from Cnet. Im quite noob, so if someone could explain me how to got this  trouble fixed, it will be very appreciated.

---

### Post by lilalmond on 2008-04-01
Hi

I also have the same issue, my connection is going on and off all the time...
I have a wireless modem with a USB dongle (level one)
I tried many things to get a better connection but it just doesnt work.(from the thread slow wireless and wired internet Ubuntu 7.10)
I have disabled IPv6 in firefox
I have disabled alias net-pf-10 ipv6 in /etc/modprobe.d/aliases
I edited (~prepend) in /etc/dhcp3/dhclient.conf
Im out of options...
Any help would be welcome

---

### Post by timbosity on 2008-04-10
hey guys (b0rt and lilalmon),

assuming that the problem is driver related ie you have your ESSID and passwords and all that set up thne you have to replace the linux driver with the windows native driver for your harware (the dongle).

ndiswrapper allows you to use the windows driver so you need to install that first
(get ndisgtk from synaptic)

then you must find the windows driver for your respective dongles 
follow instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") 

example for you b0rt you cnet [dongle]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/") 

you also need to blacklist the alternate driver (instructions for that on the ndiwrapper wiki)

once you have found and installed the Windows driver you have to load ndiswrapper following what hyperair posted above ie modprobe ndiswrapper (just check to make sure)

hope that is of some help

---

