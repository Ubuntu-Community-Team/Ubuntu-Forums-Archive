---
title: "Ndiswrapper crashing on Karmic"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by Tahakki on 2010-01-18
I have a cheap Tesco wireless USB adapter - says Belkin F5D7050E on the back, but is in fact made by Accton technology and is not the same chipset as the other Belkin ones.

I loaded it with the default ndiswrapper, and it crashed the computer. I installed the latest version manually, and it still crashes. Any tips?

---

### Post by Tahakki on 2010-01-18
Here's the syslog:
```
Jan 18 18:18:14 brickmonster kernel: [  159.392124] usb 1-1: new full speed USB device using uhci_hcd and address 2
Jan 18 18:18:14 brickmonster kernel: [  159.567420] usb 1-1: configuration #1 chosen from 1 choice
Jan 18 18:18:14 brickmonster kernel: [  159.627032] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Jan 18 18:18:14 brickmonster kernel: [  159.792131] usb 1-1: reset full speed USB device using uhci_hcd and address 2
Jan 18 18:18:15 brickmonster kernel: [  159.998820] ndiswrapper: driver a4501a (,11/16/2005, 3.3.36.0) loaded
Jan 18 18:18:17 brickmonster kernel: [  162.010113] wlan0: ethernet device 00:12:bf:1e:8c:1c using NDIS driver: a4501a, version: 0x30324, NDIS version: 0x501, vendor: '802.11g Wireless USB Adapter', 083A:F503.F.conf
Jan 18 18:18:17 brickmonster kernel: [  162.010223] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Jan 18 18:18:17 brickmonster kernel: [  162.010347] usbcore: registered new interface driver ndiswrapper
Jan 18 18:18:17 brickmonster NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/net/wlan0, iface: wlan0)
Jan 18 18:18:17 brickmonster NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 18 18:18:17 brickmonster kernel: [  162.091508] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 18 18:18:17 brickmonster NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00).
Jan 18 18:18:17 brickmonster NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper')
Jan 18 18:18:17 brickmonster NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan 18 18:18:17 brickmonster NetworkManager: <info>  (wlan0): now managed
Jan 18 18:18:17 brickmonster NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Jan 18 18:18:17 brickmonster NetworkManager: <info>  (wlan0): bringing up device.
Jan 18 18:18:17 brickmonster NetworkManager: <info>  (wlan0): preparing device.
Jan 18 18:18:17 brickmonster NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Jan 18 18:18:17 brickmonster NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Jan 18 18:18:17 brickmonster NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Jan 18 18:18:18 brickmonster wpa_supplicant[750]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
```

---

### Post by Tahakki on 2010-01-18
Bump?

---

### Post by Tahakki on 2010-01-19
Bump

---

### Post by stim on 2010-01-19
what is the output of ```
lsusb
```

---

### Post by Tahakki on 2010-01-19
```
~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 083a:f503 Accton Technology Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Odd, it's working right at this minute, I don't know how though. :P I don't think I've changed anything since the crashing apart from removing ndisgtk.

---

### Post by Tahakki on 2010-01-19
Nah, scratch that - worked fine for about five minutes and then crashed the whole computer again. :(

---

### Post by stim on 2010-01-19
the device identifier string "083a:f503" is what you are interested in. This is important, and is what you should try googling as far as getting information about drivers.  

Linux + Wireless has been a tough struggle since I started using ubuntu back in dapper drake days.  NDISwrapper is a hack *at  best* , and should be avoided if a native solution is present.  

Some quick google searches have turned up the ZD1211 driver as a possible solution. Check out this link [http://sourceforge.net/projects/zd1211/develop]("http://sourceforge.net/projects/zd1211/develop")

---

### Post by nexoncore on 2010-01-19
I have issues with ndiswrapper also, but its more of a case of the netgear wpn111 just stopping working, needing the driver to be reloaded in ndiswrapper which is becoming a pain. We need a new alternative to ndiswrapper which works better.

---

### Post by Tahakki on 2010-01-19
I downloaded and install ZD1211 as per the instructions in the README. I then did 'sudo modprobe zd1211rw', but nothing happened.

Help?

---

### Post by stim on 2010-01-19
you would want to **MAKE SURE** ndiswrapper is not loaded or running at the same time you try to use the 1211 drivers.  If NDISwrapper isnt working, either uninstall it or 

```
sudo modprobe -r ndiswrapper
```
immediately  before doing anything with the 1211 drivers to make sure the ndiswrapper module isn't loaded.  At this point, the wireless "light" on the physical device should go out, indicating it is no longer on.

Once you are sure the ndiswrapper module is not loaded,then 
```
sudo modprobe zd1211rw
```

At this point the wireless "light" should go on, indicating the device has been recognized with the new drivers.  

You can also try this thread [http://ubuntuforums.org/showthread.php?t=252465]("http://ubuntuforums.org/showthread.php?t=252465") though we would need to know the exact model of your wireless chip in order to help you further

---

### Post by Tahakki on 2010-01-19
There was no light on the device, and modprobing the zd1211rw didn't change that.

---

### Post by Tahakki on 2010-01-19
How can I find out the wireless chip's model?

---

### Post by stim on 2010-01-19
Then those are the incorrect drivers for your chipset. We need the exact model and revision so we can find a driver set that will work for you. One thing to remember in linux is newer is not always better. You may find that an old version of the windows drivers work just fine with NDISwrapper but new ones do not.

LOOK HERE:
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)



your device string : "083a:f503" is not the same as the one listed in that document , "050d:705c", so you will need to determine the EXACT REVISION of your hardware (look on the device itself) or do some googling with the device string to see what you can figure out as far as EXACT model

---

### Post by Tahakki on 2010-01-19
I had just been using the drivers off the disc.

How would I find out the chipset, model, or revision?

---

### Post by Tahakki on 2010-01-19
```
Bus 002 Device 006: ID 083a:f503 Accton Technology Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x083a Accton Technology Corp.
  idProduct          0xf503 
  bcdDevice            1.00
  iManufacturer           1 ZZ
  iProduct                2 802.11g Wireless USB Adapter
  iSerial                 3 083A-F503
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
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
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```

Some relevant lsusb information there, I hope?

The device says the following on it:

Belkin
Wireless 802.11g USB Adapter
F5D7050 E
v 1010ec.

---

### Post by stim on 2010-01-19
Not really as far as I can tell. The other posters in some of the threads I have posted, mention things like revision "4000" or revision "3000".  I tried googling the device string and some variations to no avail.  Most people say they have had success using NDISwrapper and leave it at that. 

question:
 what version of ndiswrapper are you running? It may benefit you to compile, from source, the latest ndiswrapper before you try this again.


It also may benefit you to find from belkin the NEWEST drivers from possibly their website, that support this card, and try those, instead of the drivers from the CD.

as I said before, linux wireless is a beast.  If you decide to say "Eff it" and buy a compatible card, anything with a RT73 chipset works fairly well using [these]("http://homepages.tu-darmstadt.de/~p_larbig/wlan/") drivers.

---

### Post by Tahakki on 2010-01-19
Well I saw a fairly cheap stick on Amazon with positive reviews from ubuntu users.

I am using the latest ndiswrapper (1.55 I think) from the .tar.gz from the website.

---

### Post by stim on 2010-01-19
Latest NDISwrapper is good, try the** latest **drivers for that stick before you go out and buy a new one. 

Post the link here of the chip you were thinking of, when I get home, I will check the exact model of the one I have, which also works with minimal fuss using p_larbigs drivers. 

Good Luck.

---

### Post by Tahakki on 2010-01-19
[http://www.amazon.co.uk/Technologies-802-11g-Wireless-Network-Adapter/dp/B000CC3ZFS/ref=sr_1_1?ie=UTF8&s=electronics&qid=1263937249&sr=8-1](http://www.amazon.co.uk/Technologies-802-11g-Wireless-Network-Adapter/dp/B000CC3ZFS/ref=sr_1_1?ie=UTF8&s=electronics&qid=1263937249&sr=8-1)

I'll try some driver hunting.

---

### Post by Tahakki on 2010-01-20
Found it:

[http://www.micradigital.com/product.aspx?id=25009](http://www.micradigital.com/product.aspx?id=25009)

There don't appear to be any drivers available, though.

---

### Post by stim on 2010-01-20
The drivers are inside of the .exe. Use file-roller to open the .exe as an archive, and you will find the .inf and .sys files in the driver subdirectory.  Try them with ndiswrapper.  

Important to note: (and this is what I was getting at yesterday) the version number is important! You will notice that the page has two .exe files, one for V1000 and one for V2000.  Also on belkins support page, in order to get drivers for the device, you must choose which Version.  You need to know the version to get the correct driver. I am pretty confident that if you figure out which version you have, youll get it working correctly.

---

### Post by Tahakki on 2010-01-20
Well, there's a sticker on it saying V1010 - I'll try the 1000 driver.

---

### Post by stim on 2010-01-20
Here ya go bud, this is what I've been after for the last couple of days, trying to find out exactly what youve got. 


[http://en-us-support.belkin.com/app/answers/detail/a_id/297/p/263](http://en-us-support.belkin.com/app/answers/detail/a_id/297/p/263)

That should clear the version issue up.

---

### Post by Tahakki on 2010-01-20
Don't think so - it's not a F5D7050, it's an F5D7050E, which apparently uses a different chipset?

---

### Post by Tahakki on 2010-01-20
Aargh, ndiswrapper is broken. Installing from the repos gives a segmentation fault when run, installing from source won't compile.

---

### Post by Tahakki on 2010-01-21
Help?

---

