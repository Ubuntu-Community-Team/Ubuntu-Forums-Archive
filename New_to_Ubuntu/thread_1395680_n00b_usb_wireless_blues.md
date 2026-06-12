---
title: "n00b usb wireless blues"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by Schiaparelli on 2010-02-01
Hi all

Total newbie to ubuntu... I've been trying to get my netgear wg111t wireless USB dongle working under Ubuntu 9.10 (which I've got totally up to date)

I've tried methods in various posts, with various degrees of nothing happening. I'm hoping someone can help me! I've figured out I need ndiswrapper for the driver. I've installed ndisgtk, and installed what I believe to be the relevant driver files. via sourceforge.net I've discovered that it's an atheros usb chipset with usbid: 1385:4250, although when I run:
```
 lsusb 

```I get: 
[FONT=Lucida Sans Unicode][FONT=Lucida Console]Bus 001 Device 002: ID 1385:4251 Netgear, Inc WG111T (no firmware[/FONT]).[/FONT]

 so the ID is slightly wrong, but I'm assuming this isn't a huge biggie and that I have the correct driver. I tried installing the drivers via command line, but being a n00b I no doubt messed this up. via ndisgtk I removed my old attempt and installed both .inf files that sourceforge told me I needed ([here]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WG111T")). These are athfmwdl.inf (plus it's .sys file) and netwg11t.inf with it's .sys file (apparently wg11tnd5.sys).

both installed fine under ndisgtk. when I use: system > Administration > Windows Wireless Drivers I initially get: "Unable to see if hardware is present" but then it shows me that both are installed. underneath the athfmwdl driver it says: hardware present: yes. under the netwg11t driver it says: hardware present: no. I presume that's bad. 

I also read that I need to disable the built in USB drivers that come with ubuntu so I used:

```
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | 
sudo tee -a /etc/modprobe.d/blacklist
```when I use either ifco[FONT=Arial]nfig [/FONT]or iwconfig, I don't see any wlan0, only the l0 and eth0 (both saying no wireless connections. similarly at the top network manager I only see eth0 - no mention of anything remotely wireless. 

as per [this]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrappe") post, I've run:
 
 ```
sudo ndiswrapper -m
```

when I run: 

```
gksudo gedit /etc/modules
```

I see that ndiswrapper is added after lp. Under the post mentioned above it mentions that there should be only one .inf installed, but under the sourceforge link it mentions I need both .inf driver files. I suspect that this might be a problem. I've tried removing the netwg11t.inf driver via ndisgtk in the hope that that might fix things, but no dice. 

I'm clearly missing something, but am unfortunately entirely at the mercy of people who have a clue as to how linux works - I'm just blindly pasting code that's sugested with little to no understanding of what it is I'm doing. Apologies for the long post (I've tried to give the best picture possible), hoping someone can help me out...

---

### Post by sailor2001 on 2010-02-01
put the inf on the desktop and then

cd Desktop
sudo apt-get install ndiswrapper -utils
sudo ndiswrapper -1 (xxx. inf)
sudo ndiswrapper -l
sudo dhclient
 (control zero saves)

---

### Post by Schiaparelli on 2010-02-01
many thanks for your reply Sailor2001 - really appreciate it
Tried what you said - but the driver is already installed it seems - as is the utils package.
When I use: sytem > administration > windows wireless drivers, it now shows me that both the drivers are 'Hardware present: yes' If I click on configure network I don't see a wireless connetion however. ndiswrapper -l gives me:

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
athfmwdl : driver installed
    device (1385:4251) present
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
netwg11t : driver installed
    device (1385:4251) present

not sure about the conf stuff, but it does seem the driver is loaded. Nothing is showing up however. the network doesn't use DHCP - uses static IPs - which I think I've managed to assign in the network manager under the wireless tab - but of course no wireless is detected. It seems I'm so close but yet so far! heh. Is this some sort of karma because the only time I've ever seen a koala it tried to bite me?

---

### Post by bkratz on 2010-02-01
Why don't we actually see if your adapter sees anything.  Go to the terminal ( Applications>>Accessories>>Terminal) and type

sudo iwlist scan
(THAT IS SUDO IWLIST SCAN IN lowercase) and copy/paste the output back here.

By the way don't worry about the warnings

---

### Post by steveneddy on 2010-02-01
I use a Mifi device for my laptop and other internet devices.

It just connects to the internet and you connect to that through the laptop's wireless connection.

It's a lot easier and no set up needed on your Linux box.

Turn it on, it's there.

It will also allow four other devices to connect at the same time along with your computer.

[Verizon]("http://www.verizonwireless.com/b2c/mobilebroadband/?page=products_mifi") and [Sprint]("http://nextelonline.nextel.com/NASApp/onlinestore/en/Action/DisplayPhones?phoneSKU=NV2200WFDO") both carry this neat little device.

---

### Post by Schiaparelli on 2010-02-02
thanks bkratz :)

basically when I type that is says: 
lo         Interface doesn't support scanning
eth0     Interface doesn't support scanning

when I use lsusb I DO see the beastie...so it's definitely attached.
when I use ndiswrapper -l it tells me both drivers are installed and the device is present...

am I close or no cigar? :)

---

### Post by Schiaparelli on 2010-02-02
steveneddy - not sure what you mean man - sorry! but this isn't a laptop though, it's a desktop...my little acer netbook connects via wifi like the clappers (under UNR) so I thought hey why not slap 9.10 on this prewar computer and give it a new life? heh...

---

### Post by steveneddy on 2010-02-02
> **Schiaparelli said:**
> steveneddy - not sure what you mean man - sorry! but this isn't a laptop though, it's a desktop...my little acer netbook connects via wifi like the clappers (under UNR) so I thought hey why not slap 9.10 on this prewar computer and give it a new life? heh...

I see - sorry.

---

### Post by bkratz on 2010-02-02
Here is a pretty good thread (just pay attention to original posters name, a lot of people jumped in) especially the second half.

[http://ubuntuforums.org/showthread.php?t=1311105&highlight=1385:4251&page=2](http://ubuntuforums.org/showthread.php?t=1311105&highlight=1385:4251&page=2)

---

### Post by Schiaparelli on 2010-02-03
many thanks bkratz - going through the commands... I'll post them here:

```

gavin@gavin-runningpc:~$ dmesg | grep -e ndis -e wlan
[   16.767904] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   17.585282] ndiswrapper: driver athfmwdl (,12/05/2003,1.00.001) loaded
[   17.612259] usbcore: registered new interface driver ndiswrapper

```

so it does seem that ndiswrapper is ok with these drivers. when I:

```

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
athfmwdl : driver installed
    device (1385:4251) present
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
netwg11t : driver installed
    device (1385:4251) present

```

so it does seem the drivers are installed - this is also confirmed by the visual front-end ndisgtk thingie...

however, I can see absolutely no reference to wlan0 no matter what command I type...

```

gavin@gavin-runningpc:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:0d:61:53:a0:96
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.5.80 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: irq:23 ioport:e400(size=256) memory:ea001000-ea0010ff

```

on the other post the guy could actually spot the wireless dongle - mine appears to be a ninja...

---

### Post by Schiaparelli on 2010-02-03
oh and:

```

ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

```

---

### Post by Schiaparelli on 2010-02-03
oh SOME info I can get: when I run lsusb -v I get:
```

Bus 001 Device 003: ID 1385:4251 Netgear, Inc WG111T (no firmware)
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1385 Netgear, Inc
  idProduct          0x4251 WG111T (no firmware)
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
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
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
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
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

```

---

### Post by Schiaparelli on 2010-02-03
also, when I run:

```

gavin@gavin-runningpc:~$ dmesg | grep -e ndis -e wlan
[   16.408594] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   17.152977] ndiswrapper: driver athfmwdl (,12/05/2003,1.00.001) loaded
[   37.276404] usbcore: registered new interface driver ndiswrapper

```

even though other sources tell me that both drivers are loaded, it appears only the athfmwdl one is showing up here. Could this be part of the problem?

---

### Post by Schiaparelli on 2010-02-03
some success! I found another doc that mentioned some updated drivers....installing those now at least gives me a blinking light from the dongle... always a good sign right?

wlan0 is now present when I run iwconfig... definitely getting there
when I run that however, it mentions an access point with what appears to be a mac address...but it's not the one for the dongle.... problem?

Wireless Networks is now finally showing up in netman at top - but says device not managed....

any clues peeps?

---

### Post by Schiaparelli on 2010-02-03
so now something is happening:
```

gavin@gavin-runningpc:~$ dmesg | grep -e ndis -e wlan
[   16.570303] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   17.343659] ndiswrapper: driver athfmwdl (,12/05/2003,1.00.001) loaded
[   17.830615] usbcore: registered new interface driver ndiswrapper
[  101.256141] ndiswrapper: driver athfmwdl (,12/05/2003,1.00.001) loaded
[  131.638058] ndiswrapper: driver netwg11t (NETGEAR,09/05/2005,1.5.0.2102) loaded
[  131.639816] ndiswrapper (ZwQueryValueKey:2329): not fully implemented (yet)
[  132.297270] wlan0: ethernet device 00:18:4d:d4:fc:0f using NDIS driver: netwg11t, version: 0x10005, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 1385:4251.F.conf
[  132.366164] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

```

If I reboot however the thing tends to disappear... but I guess that's step 2.

then:

```

gavin@gavin-runningpc:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:0d:61:53:a0:96
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.5.80 latency=32 maxlatency=8 mingnt=3 multicast=yes
       resources: irq:23 ioport:e400(size=256) memory:ea001000-ea0010ff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:4d:d4:fc:0f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netwg11t driverversion=1.55+NETGEAR,09/05/2005,1.5.0.21 multicast=yes wireless=IEEE 802.11g

```

so something is rotten in the state of wlan0....

my router DOES seem to be picking up that the device is attached though - so that's a good sign I think...

---

### Post by Schiaparelli on 2010-02-03
I've actually managed to get it connected. first connected the eth0...now suddenly the wlan0 connected. Im sure it will break as soon as I reboot etc... but at least I'm on the right track....!!

update: yup, it broke, as soon as I reboot heh....

---

