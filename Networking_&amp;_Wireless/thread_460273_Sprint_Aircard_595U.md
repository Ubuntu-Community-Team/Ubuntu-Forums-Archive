---
title: "Sprint Aircard 595U"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by loumsmith on 2007-05-31
I am low tech when it comes to Ubuntu.  I have been running the OS for about 6 months.  I did install the aircard following the directions provided by sprint.

Here is my question:
How can I automate the commands that configure the modem?  They must be typed in, in terminal mode each time I log on to the machine.

(Here is the link to the installation manual: [http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf))

Thanks!

Lou Smith

---

### Post by Thumper723 on 2007-06-17
I have the same card, I can see it  in my devices, but Ubuntu does not know what it is.. 

I am mildly Linux competent, but drivers and such are beyond me.. 

I am running Gutsy on a Compaq Presario V6310US, AMD 64 Bit processor..

I despise vista, for it is less stable than my ex wife when she stops taking her Prozac.. My wireless LAN card, and normal networking work fine, but due to where I live, I am stuck with Cell Internet service for the next couple years.

---

### Post by Thumper723 on 2007-06-21
Ok, I used the instructions here [http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601) and apparently I have had success getting my driver up and running..

When I go to the device manangement util, I can see the card on /dev/ttyUSB1, but I could before.. Still says UNKNOWN DEVICE. 

Also, when I ran the pppd script the above link called to use.. I get a bunch of gibberish I can't CTRL-z out of, and it doesnt do anything.. 

How do I test to make sure this is where my issue is?

Is there a graphical daemon I can use to setup? I have NO internet access right now, and must download under windoze and copy to my share directory.  So I cant' use apt-get.

---

### Post by Thumper723 on 2007-06-22
Ok, this is lengthy, but this is what I get when I try to troubleshoot.. .

I'm kind of running out of ideas here..

Still no luck connecting.. 

Here is what I get when I run 
master@master-laptop:/etc/ppp/peers$ sudo pppd call cdma
Starting Sierra Wireless CDMA connect script...

Setting the abort string

Initializing modem
Connect script failed

When I checked my install I got this:
master@master-laptop:/etc/ppp/peers$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 1199:0120 Sierra Wireless, Inc. 
Bus 001 Device 001: ID 0000:0000  

master@master-laptop:/etc/ppp/peers$ lsusb -v

Bus 002 Device 001: ID 0000:0000  
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

Bus 001 Device 003: ID 1199:0120 Sierra Wireless, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1199 Sierra Wireless, Inc.
  idProduct          0x0120 
  bcdDevice            0.02
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           67
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
      bNumEndpoints           7
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval             128
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
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
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

Sorry for the long string, but trying to make sure what I am seeing is there. 

Here is my /etc/ppp/peers/cdma file

-detach^M
lcp-echo-failure 0^M
noauth^M
/dev/ttyUSB1^M
115200^M
debug^M
defaultroute^M
ipcp-accept-local^M
ipcp-accept-remote^M
usepeerdns^M
crtscts^M
lock^M
connect '/usr/sbin/chat -v -t6 -f /etc/ppp/peers/cdma_chat'^M
^

The ^M's show up as blue with vi, but are not seen using gedit. 

Here is cdma_chat

# Connection script for Sierra Wireless CDMA/EVDO modems
# Note: This demo script is setup to work on Verizon and Sprint
#       Networks.
#
SAY 'Starting Sierra Wireless CDMA connect script...\n'
SAY '\n'

#######################################
SAY 'Setting the abort string\n'
SAY '\n'
# Abort String ------------------------------
ABORT 'NO DIAL TONE' ABORT 'NO ANSWER' ABORT 'NO CARRIER' ABORT DELAYED

#######################################
SAY 'Initializing modem\n'
# Modem Initialization
'' AT
OK ATZ

#######################################
SAY '\n'
SAY     'Dialing...\n'
OK ATDT#777

---

### Post by Thumper723 on 2007-06-23
Got it to work.. Changes ttyUSB1 to USB0

Now I just need to make it auto-connect.

---

### Post by hector_g on 2007-09-09
I'm new to Ubuntu.  Could you tell me how you finally got it to work?

---

### Post by LiquidSmoke on 2007-10-22
I'm with the prevous guy, some simple instructions for how to get it work would be greatly appreciated. Thnx :)

---

### Post by Mach1US on 2007-10-25
If you guys find any way to get it connecting please post it or a link to :
[http://ubuntuforums.org/showthread.php?p=3627729#post3627729](http://ubuntuforums.org/showthread.php?p=3627729#post3627729)

---

### Post by whalebus on 2007-11-21
I downloaded a pdf instruction guide based on Ubuntu 6.10 from Sprint.  I am using Gutsy Gibbon.  A few KPPP screens were different, but I figured it all out fairly quickly.  I am using a Sierra Wireless 595U.

I went to Sprint.com/downloads.

Chose my operating system (Linux).

Downloaded the Linux installation guide.

Step by step guide to installation, followed by instructions to install startup scripts to load usbserial driver and device identification each time you start-up the system.

Should work for most currently available EVDO modems.

---

### Post by jimbarfield on 2008-05-05
Yay!  This solution FINALLY worked- after I tried about 3 or 4 other peoples' suggestions.

I am using a Sprint Aircard 595U on Ubuntu Hardy Heron 7.10 rc

The steps are kind of long but the Sprint install manual is very very good.

Here's how I did it:

(1) Register your modem on a Windows machine with the Installation CD that came with it.  (My account was pre-registered when I bought the card, but it can also be done over the phone).  If your account is pre-registered it will be considerably easier.

(2)Go to Sprint.com/downloads and choose Linux as your OS from the drop down menu.

(3)Choose your card and download the .pdf guide.  NOTE: The guide uses Ubuntu, with screenshots and everything and is very easy to use.

NOTE: On Hardy Heron some of the screenshots look a little different.

Follow the command prompt instructions EXACTLY.  For instance in one command what seemed like it should have been "Product ID# = 1111" changed to a different number, but it worked even though it seemed like a typo.

(4)Plug a regular ethernet cable to your laptop and make sure you have ethernet

(5)Download gppp from Applications> Add and Remove (it also is bundled with PPP and they will both download together.

(6)On my machine for some reason even though I followed Sprint's guide, the GPPP application froze.  I rebooted and it still froze.

(7)I downloaded all 129 suggested updates for the computer.

(8)Rebooted, got fsck errors and typed in fsck to manually check the drives, clicked "yes" to every suggested fix.

(9)Rebooted, and joila! everything works like a charm.

(10)One caveat: Firefox loads up in Offline Mode when you are using a wireless card.  My understanding is that this is not really a bug, but rather a function of the network manager looking for an ethernet connection first.

(11)Drag the GPPP icon to the dock.

(12)Now, whenever you click the icon your modem will connect to Sprint.

NOTE: You should also have a network icon on the top right that will detect traditional wireless networks- I didn't really mess with it, since this computer is going to another location, but it detected a LOT more networks than my Mac Airport and also more than programs on my Windows machine.

Good Luck- Just Glad it Works Finally- and WAY TO GO Sprint for supporting Linux with these cards!!!!!!!!!!!!!!

Jim

---

