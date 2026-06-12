---
title: "Linksys WUSB11 Wireless?"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by Tazz92708 on 2007-02-27
[SIZE="4"]I really could use some help with this.
Am really new to Ubuntu and having a dickens of a time getting the wifi to work.
I can see the device using lsusb.
I can see the driver using lshw
Iwconfig says I have nothing.

Where do I go from here?:confused: 

Tazz92708[/SIZE]

---

### Post by n00b@linux on 2007-02-28
We need to make sure we match the correct kernel module (aka 'device driver') to the chipset used by the USB wireless adapter. If you try the verbose mode of lsusb:```
lsusb -v
```does it show you the chipset used in the WUSB11?
 
Do you know the name of the kernel module recommended for that chipset? If you do, has it been loaded into the kernel? You can check this with the following command:```
lsmod
```
 
Assuming the kernel module has been loaded, is your USB wireless adapter showing up if you run:```
ifconfig
```N.B. 'ifconfig' not 'iwconfig'. If it does show up, then you may simply need to edit your /etc/network/interfaces configuration file:```
sudo gedit /etc/network/interfaces
```by adding:```
auto wlan0
iface wlan0 inet dhcp
```to the end of the file. N.B. this assumes 'wlan0' is what shows up in ifconfig. Substitute it for the correct name if your ifconfig shows something different. Note also that in your /etc/network/interfaces configuration file 'lo' is a loopback interface (ie. not your USB wireless adapter) and 'eth0' will be your ethernet adapter (ie. not your USB wireless adapter). If you have FireWire it may show up as 'eth1'.  USB wireless adapters typically show up as 'wlan0' or 'ra0' so, just make sure you use the correct naming conventions when you edit your /etc/network/interfaces configuration file.
 
After you've edited and saved the /etc/network/interfaces file, you need to restart the networking init script:```
sudo /etc/init.d/networking restart
```The 'restart' just Then test to see the USB wireless adapter has been identified with:```
iwconfig
```
 
If any of the above steps don't work, post back.

---

### Post by Tazz92708 on 2007-03-01
[COLOR="Blue"]n00b@linux,
                      Let me start by thanking you for your reply and your willingness to assist someone very new to Linus and Ubuntu. 
I am following your instruction and posting the results from “terminal”. Some of it makes sense and the rest I will get as we go along. 
[/COLOR]
[COLOR="Red"]Running lsusb. The hardware shows up on Bus 002 Device 002[/COLOR]
oem@Merlin-II:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c50d Logitech, Inc. 
[COLOR="DarkOrchid"]Bus 002 Device 002: ID 066b:2212 Linksys, Inc. WUSB11v2.5 802.11b Adapter[/COLOR]
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

[COLOR="Red"]The results from lsusb -v again shows the hardware from bus 2, but I am unclear as to what to look for with regards to a chipset.
[/COLOR]
oem@Merlin-II:~$ lsusb -v

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
      bInterfaceProtocol      0 
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
  bDeviceProtocol         0 
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
      bInterfaceProtocol      0 
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

Bus 002 Device 003: ID 046d:c50d Logitech, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc50d 
  bcdDevice           23.02
  iManufacturer           1 
  iProduct                2 
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
    MaxPower               50mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
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
          wDescriptorLength      84
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
cannot read device status, Operation not permitted (1)

[COLOR="DarkOrchid"]Bus 002 Device 002: ID 066b:2212 Linksys, Inc. WUSB11v2.5 802.11b Adapter[/COLOR]
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x066b Linksys, Inc.
  idProduct          0x2212 WUSB11v2.5 802.11b Adapter
  bcdDevice            1.32
  iManufacturer           0 
  iProduct                0 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           3
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
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               1
cannot read device status, Operation not permitted (1)

Bus 002 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 
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
      bInterfaceProtocol      0 
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
  bDeviceProtocol         0 
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
      bInterfaceProtocol      0 
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

[COLOR="Red"]I located and installed the package “linux-wlan-ng” which contains the driver “prism2”. According to what I have read this is the correct driver for my hardware.
When I run lsmod this is the result.[/COLOR]

oem@Merlin-II:~$ lsmod
Module                  Size  Used by
ipv6                  272288  8 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
radeon                118816  3 
drm                    74644  4 radeon
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
nls_utf8                3200  2 
ntfs                  112116  2 
sbp2                   24584  0 
scsi_mod              144648  1 sbp2
lp                     12964  0 
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tsdev                   9152  0 
snd_via82xx            30360  1 
snd_ac97_codec         97696  1 snd_via82xx
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
usbhid                 45152  0 
[COLOR="DarkOrchid"]prism2_usb             79236  0 [/COLOR]
i2c_viapro              9876  0 
i2c_core               23424  2 i2c_ec,i2c_viapro
via_ircc               28948  0 
irda                  214332  1 via_ircc
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
via_agp                11264  1 
agpgart                34888  2 drm,via_agp
crc_ccitt               3200  1 irda
snd_pcm                84612  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  2 snd_seq,snd_pcm
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart        10240  1 snd_via82xx
snd_rawmidi            27264  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    58372  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              11232  1 snd
analog                 12960  0 
psmouse                41352  0 
gameport               17160  2 snd_via82xx,analog
floppy                 63044  0 
evdev                  11392  1 
serio_raw               8452  0 
via_rhine              26116  0 
mii                     6912  1 via_rhine
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
pcspkr                  4352  0 
ext3                  142728  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
[COLOR="DarkOrchid"]usbcore               134912  5 usbhid,prism2_usb,ehci_hcd,uhci_hcd[/COLOR]
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  6 
via82cxxx              10500  0 [permanent]
generic                 5764  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

[COLOR="Red"]The results from “ifconfig” do not show anything about “prism2”.  Am I correct in assuming the driver is not loaded?[/COLOR]

oem@Merlin-II:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:A6:49:E8:DD  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Base address:0xa400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3956 (3.8 KiB)  TX bytes:3956 (3.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:06:25:A6:9F:9F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

[COLOR="Blue"]Thanks again in advance for your help, Tazz92708
[/COLOR]

---

### Post by n00b@linux on 2007-03-02
Hey Tazz, look at you running commands from the terminal! You're already on your way to turning into a linux wizard!!!
 
So you've now learned the difference between 'lsusb' and 'lsusb -v'. Sometimes running 'lsusb -v' will show you the chipset used in the USB dongle. In your case it didn't. Sometimes you need to run it with root privileges, ie. 'sudo lsusb -v'. I can't remember if you need to run it as root for Ubuntu because I haven't looked at Ubuntu for about 3 months.  Anyway, you've already discovered that prism2_usb is the kernel module you need through other means.  btw, a 'kernel module' is the same thing as a 'device driver'.  So in windoze, device drivers are kernel modules for the windoze kernel - just a bit of useless information for you there ;)
 
The results of the 'lsmod' clearly show that the module 'prism2_usb' has been loaded into the kernel, ie. your kernel now supports the prism2 chipset.
 
The results of 'ifconfig' show that the name given to your USB wireless adapter interface is 'wlan0'. If you've set up your /etc/network/interfaces configuration file as I suggested in my earlier post, ie:```
auto wlan0
iface wlan0 inet dhcp
```then 'wlan0' is now ready to be associated with your access point (wireless ADSL modem/router).
 
If you run 'iwconfig' as per my previous post you'll probably see all of the above 3 interfaces listed with no associations. That's fine, except for 'wlan0' - we need to configure wlan0 to associate with an access point.
 
For now, make sure your wireless ADSL modem/router has no encryption set (WEP or otherwise). I presume you know how to do this. If you don't then encryption is probably not enabled anyway as most wireless ADSL modem/routers ship without encryption enabled by default. We'll change that later, but for now we need to make sure you can access the internet and we don't want encryption getting in the way.
 
If you run```
iwlist wlan0 scan
``` you should see a list of access points which your USB wireless adapter can see. You should see yours in that list (look for the ESSID value). If you can't see anything, move your PC closer (physically) to your access point (or vice versa) and try again. If you still get no joy, post back.
 
Assuming everything has worked, it's now time to associate wlan0 with your access point. I'll assume it's called 'tazznet' for illustration purposes, but substitute the actual name into the command I'm going to show you.
 
To associate wlan0 to tazznet run the command:```
sudo iwconfig wlan0 essid tazznet mode managed
```Now run 'iwconfig' and you should see wlan0 is now associated with tazznet. Given that your /etc/network/interfaces file has configured wlan0 to use DHCP you should now be able to access the internet. Open a web browser and try it. If it doesn't work, you may need to restart the networking init script:```
sudo /etc/init.d/networking restart
```and try your web browser again. 
 
Either way, let me know. 
 
If it has worked, I'll show you how to set things up to automatically configure wlan0 at boot so that you don't have to manually go through all of the above steps every time you reboot Ubuntu.

---

### Post by Tazz92708 on 2007-03-02
n00b@linux,
                        Yee Haw! After some minor futzing with the commands you gave me I now have internet access. To borrow a line from a beer commercial you are "Brilliant, simply Brilliant!":guitar:  

At this point I will take you up on your offer to automate the process. I feel accomplished!
Also I did turn all WEP encryption off and am getting warnings. Do I simply turn it back on or is there more to do?

Much Thanks, Tazz92708

---

### Post by n00b@linux on 2007-03-03
I'm glad to see it's working.  I know the feeling having had wireless problems myself.  Hopefully, you now understand the wireless process:

1.  the chipset is the key
2.  find out the type of chipset (using 'lspci' or 'lsusb' or other means)
3.  match/find the driver for that chipset
4.  make sure the driver is loaded into the kernel (using 'modprobe' to load it and 'lsmod' to check its loaded)
5.  check your /etc/network/interfaces configuration file is set up correctly
6. disable any encryption on your wireless ADSL modem/router
7. physically locate your equipment close together to eliminate signal strength problems
8.  restart the networking init script and check the kernel now recognises the wireless adapter (using 'ifconfig' and 'iwconfig')
9.  scan for available access points (using 'iwlist')
A.  associate the wireless adapter with an access point (using 'iwconfig')

It's really that simple, but then that's the benefit of hindsight.

OK, before we automate things for the boot process, we need to test WEP encryption (btw, I don't think your Linksys WUSB11 v2.5 supports WPA).

Re-enable the WEP encryption on your wireless ADSL modem/router and take a note of the WEP key/password you use.  For this example, I'm going to assume your key is pa55w0rd.  Then, reconfigure your /etc/network/interfaces configuration file (don't forget you will need to have root priviliges to do this, ie. use 'sudo':```
sudo gedit /etc/network/interfaces
```Change the wlan0 section of the file to look like this:```
auto wlan0
iface wlan0 inet dhcp
wireless-essid tazznet
wireless-mode managed
wireless-key s:pa55w0rd
```If your WEP key is a hexadecimal number (eg. 0123456789ABCDEF) then don't use the 's:' prefix for wireless-key, ie. instead specify wireless-key 0123456789ABCDEF (of course, substituting your key for the '0123456789ABCDEF').

Now restart the networking init script:```
sudo /etc/init.d/networking restart
```and test to see if it's worked by using your web browser.

Hopefully, everything is working fine and you no longer get the error messages you were getting when WEP was disabled.  Post back if not.

Finally, to automate the process at boot.  Well, you've already done it!  The 'init scripts' are just that - the scripts run initially (immediately) after the linux kernel has loaded.  The 'networking' init script (one of the many init scripts) looks to your /etc/network/interfaces file for configuration information and 'init'ialises your hardware based on that information.  As we've just amended the /etc/network/interfaces file, you've already set yourself up for automatic wireless configuration at boot!  Go ahead and test it: reboot your machine and check that it works.

---

### Post by Tazz92708 on 2007-03-03
[COLOR="Blue"]n00b@linux,
                      After enabling the WEP key and changing the “interfaces” file the connection is a no-go.
Take a look at the following and share what you see.[/COLOR]

[COLOR="Red"]/etc/network/interfaces file[/COLOR]

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
#auto lo
#iface lo inet loopback

[COLOR="Blue"]auto wlan0
iface wlan0 inet dhcp
wireless-essid Vella
wireless-mode managed
wireless-key s:Geoge[/COLOR]


[COLOR="Red"]]sudo /etc/init.d/networking restart[/COLOR]
oem@Merlin-II:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 4929
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:06:25:a6:9f:9f
Sending on   LPF/wlan0/00:06:25:a6:9f:9f
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:06:25:a6:9f:9f
Sending on   LPF/wlan0/00:06:25:a6:9f:9f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
[COLOR="Blue"]No DHCPOFFERS received.[/COLOR]
No working leases in persistent database – sleeping.


oem@Merlin-II:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:E0:98:FE:4B:71
                    ESSID:"05B404946975"
                    Mode:Master
                    Encryption key:off
                    Channel:6
                    Quality:19/92  Signal level:-81 dBm  Noise level:-100 dBm
         [COLOR="Blue"] Cell 02 - Address: 00:06:25:78:37:3B
                    ESSID:"Vella"
                    Mode:Master
                    Encryption key:on
                    Channel:6
                    Quality:37/92  Signal level:-63 dBm  Noise level:-100 dBm[/COLOR]
          Cell 03 - Address: 00:13:46:43:05:9A
                    ESSID:"Home"
                    Mode:Master
                    Encryption key:on
                    Channel:3
                    Quality:1/92  Signal level:-99 dBm  Noise level:-100 dBm
[COLOR="Blue"]
When I disabled the WEP Key and changed the “interfaces” file back I was able to reconnect. What can I say, so close but no cigar.
Thanks, Tazz92708 [/COLOR]

---

### Post by n00b@linux on 2007-03-04
[COLOR=black]1.  Don't comment out the loopback interface in your /etc/network/interfaces file,
2.  You'll also want your ethernet (wired) interface in it as well (assuming you want the option to connect to the internet through ethernet),
ie. your /etc/network/interfaces file should look like this:[/COLOR][COLOR=black]```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid Vella
wireless-mode manager
wireless-key s:Geoge
```Also try it with a hexadecimal key, rather than the s:Geoge.
[/COLOR]

---

