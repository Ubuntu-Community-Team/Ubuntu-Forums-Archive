---
title: "Dynex DX-WGPUSB Dongle help"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by jderekito on 2008-05-05
Hello, 

I am somewhat new to linux, but am loving learning about it.  I have a Dynex DX-WGPUSB wireless Dongle that I have been trying to get working on my new installation of kubuntu (dapper i think).  I have tried the ndiswrapper, but am not certain I have the correct drivers.  From the driver files bcmwl5.inf is the only .inf I see.  Also, I have tried to use rt2x00.serialmonkey.com but not been able to get that to work.  Any suggestions would be greatly appreciated.

Derek

---

### Post by chili555 on 2008-05-05
> rt2x00.serialmonkey.comThat's for a Realtek chipset. You have the much beloved Broadcom.> not certain I have the correct driversAsk ndiswrapper if you have the correct ones: open a terminal and do:```
sudo ndiswrapper -l
```If you have the correct driver, it will report so; it may also report an alternate driver, in which case, we have some work to do.

So, what does it report?

---

### Post by LittleFoot on 2008-06-18
I know this post is getting a bit dated but I'm going in circles with the same problem as jderekito above.  I've tried everything that I can think of with this wireless usb and can't get it to respond.  lsusb shows it as a broadcom 

vendor: 0a5c ("Broadcom Corp."), device: d11b, device class: 02 ("Communications"), device subclass: 02 ("Abstract (modem)"), device prog-if: ff ("Vendor Specific (MSFT RNDIS?)")  

That's from [http://cateee.net/lkddb/web-lkddb/USB_NET_RNDIS_WLAN.html](http://cateee.net/lkddb/web-lkddb/USB_NET_RNDIS_WLAN.html) the linux kernal driver database.  I don't see what it mentions anywhere on my system.  And I do see usbnet rndis_host(or something to that effect the ubuntu box isn't hooked up at the moment from sheer frustration)  but I do not see rndis_wlan in the modules.  I've tried the ndiswrapper but the best I can get out of the xp drivers is invalid driver.

<<--Edit starts here-->>
The usb dongle is a DX-WGPUSB (near as I can tell from the drivers that work on the xp machine)
the dump from lsusb -v is
Bus 001 Device 003: ID 0a5c:d11b Broadcom Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0a5c Broadcom Corp.
  idProduct          0xd11b 
  bcdDevice            0.06
  iManufacturer           1 Broadcom
  iProduct                2 Remote NDIS 802.11 Wireless Adapter
  iSerial                 3 8057
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           48
    bNumInterfaces          2
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
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol    255 Vendor Specific (MSFT RNDIS?)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
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
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
can't get debug descriptor: Connection timed out
Device Status:     0x0000
  (Bus Powered)

and lsmod shows

Module                  Size  Used by
3c59x                  46376  0 
snd_rtctimer            4640  0 
binfmt_misc            12808  1 
isofs                  36388  1 
udf                    88612  0 
radeon                124192  2 
drm                    82452  3 radeon
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_ich           6288  0 
speedstep_lib           6532  1 speedstep_ich
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 speedstep_ich,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ipv6                  267780  8 
lp                     12324  0 
joydev                 13120  0 
pcmcia                 40876  0 
af_packet              23812  2 
rndis_host              8064  0 
cdc_ether               7168  1 rndis_host
usbnet                 20232  2 rndis_host,cdc_ether
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
dcdbas                  9504  0 
evdev                  13056  6 
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
video                  19856  0 
output                  4736  1 video
snd_seq_dummy           4868  0 
serio_raw               7940  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
yenta_socket           27276  2 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
battery                14212  0 
ac                      6916  0 
snd                    56996  18 snd_rtctimer,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                40336  0 
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
pcspkr                  4224  0 
shpchp                 34452  0 
intel_agp              25492  1 
pci_hotplug            30880  1 shpchp
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
agpgart                34760  2 drm,intel_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
floppy                 59588  0 
ata_piix               19588  3 
ata_generic             8324  0 
pata_acpi               8320  0 
mii                     6400  2 3c59x,usbnet
uhci_hcd               27024  0 
libata                159344  3 ata_piix,ata_generic,pata_acpi
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
usbcore               146028  5 rndis_host,cdc_ether,usbnet,uhci_hcd
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 


network manager only show's the laptops built in ethernet device and an option to configure a modem

ran all of the latest updates that popped up on me post install of ubuntu.

I've spent day's trying to figure out how to get this to work right and so far havn't even gotten the light to blink.  Any help is appreciated!

---

### Post by LittleFoot on 2008-06-19
Well the fight is continuing.  I've now tried the native ubuntu drivers, ndiswrapper with the xp drivers (though I might be missing out on earlier versions of the driver that may be stored in the cabs within the setup, not sure how to extract those further) ndiswrapper reports invalid driver, I performed compat wireless install step by step with one Warning, something about enabling multique in the kernal, not sure how to do that either.  I attempted fwcutter under each scenerio with no change in results.  compat wireless installed fine but when the usb dongle was already plugged in modprobe would have a Segmentation Fault while loading the rndis_wlan driver.  I tried to find the 2.6.25 kernel in aptitude but couldn't find it(someone told me it *may* have rndis_wlan covered with the chip.  Right now with compat wireless package once the network adapter is placed into the usb port the rndis_wlan module crashes.

the printed identifier on the chip is bcw43208kfbg.  Would love to just go buy another dongle, but funding is a bit low at the moment.  Would love to hear some idea's guys!

---

