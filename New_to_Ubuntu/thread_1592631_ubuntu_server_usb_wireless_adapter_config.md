---
title: "ubuntu server usb wireless adapter config"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by wasing on 2010-10-10
Using Ubuntu Server 10.04

I have a wireless N network adapter through usb

lsusb lists an atheros comm device but iwconfig does not have an Ath0 as a selection (lo and eth0 are the choices). do i need to install a driver even though it is recognized. thx in advance. also were can i find this driver i am currently using a windows machine as my server is not connected to the internet.

if this helps its tp-link usb wireless N adapter 
Model No. TL-WN722N

Thanks

P.S. kind of a side not when you use a command like lsusb -a how can you go back and read the rest of the output that was cutoff.

---

### Post by anewguy on 2010-10-10
For now, with the adapter plugged in, do just a lsusb and post back the results.  I'm in Windows right now or I would tell you the exact syntax, but you can also do the expanded lsusb on a specific device (I *think* it's something like d=xxxx:yyyy) - do a man lsusb or even just lsusb --help and it should tell you.  Just the regular lsusb will at least give us the manufacturer and product ids (the xxxx:yyyy).

Dave ;)

---

### Post by wasing on 2010-10-11
alright cool man ill be sure to do that after my classes get out for the day.

---

### Post by wasing on 2010-10-11
Sry im still green as grass

i can give you this though

```
Bus 001 Device 003: ID 0cf3:9271 Atheros Communications, Inc. 
```

i tried to use -v but i have no clue how to output that to a text file.

---

### Post by Hippytaff on 2010-10-11
```

lsusb

```

should output to the terminal...you can get a txt file to output to the terminal with 

```

cat /place/txtfile

```

where place is the path and txtfile is the name of the file

---

### Post by wasing on 2010-10-11
Sry Hippytaf i dont quite understand

i want to output 
```
lsusb -d 0cf3:9271 -v 
```
then take that output and write it to a text file.
then i can put it on a usb drive and paste the contents into the forum

i dont think i want to use
```
cat /place/txtfile
```
because that will just print the contents of a text file correct

from what ive been reading up on i think i have to use echo?

thx for the help so far guys

---

### Post by Hippytaff on 2010-10-11
ok so 

```

lsusb -d 0cf3-9271 -v > name.txt

```that will write it to name.txt

copy and paste name.txt to the usb efort to pste in the forum :-)

---

### Post by wasing on 2010-10-11
NVM on the copying of outputs i figured it out i will post the output in a few minutes

---

### Post by wasing on 2010-10-11
thx hippytaff lol

---

### Post by wasing on 2010-10-11
well ubuntu server does not does not automount so i will be back eventually with the lsusb output.

---

### Post by wasing on 2010-10-11
my best attempt to put it back together

```
Bus 001 Device 003: ID 0cf3:9271 Atheros Communications, Inc.

Device Descriptor:
  bLength                
18
  bDescriptorType 1
 
bcdUSB               2.00
  
bDeviceClass          255 
Vendor Specific Class
  bDeviceSubClass       255 
Vendor Specific Subclass
  
bDeviceProtocol       255 
Vendor Specific Protocol
  bMaxPacketSize0        64
  
idVendor           0x0cf3 Atheros Communications, Inc.
 
idProduct          0x9271 
  
bcdDevice            1.08
  
iManufacturer          16 
  
iProduct               32 
  
iSerial                48 
  
bNumConfigurations      1
  
Configuration Descriptor:
    
bLength  
9
    
bDescriptorType         2
  
wTotalLength           60
 
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
    
  bNumEndpoints           6
     
 bInterfaceClass       255 
Vendor Specific Class
      
bInterfaceSubClass      0 
    
  bInterfaceProtocol      0 
   
   iInterface              0 
    
  Endpoint Descriptor:
        bLength                 7
   
     bDescriptorType         5
       
 bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2

          Transfer Type  
          Bulk
   
       Synch Type   
            None
  
        Usage Type
               Data
 
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
  
      bEndpointAddress     0x83  EP 3 IN
  
      bmAttributes            3
         
 Transfer Type            Interrupt
      
    Synch Type               None
    
      Usage Type               Data
       
 wMaxPacketSize     0x0040  1x 64 bytes
     
   bInterval               1
    
  Endpoint Descriptor:
        bLength                 7
    
    bDescriptorType         5
  
      bEndpointAddress     0x04  EP 4 OUT
   
     bmAttributes            3
       
   Transfer Type           
 Interrupt
          
Synch Type               None
         
 Usage Type               Data
        
wMaxPacketSize     0x0040  1x 64 bytes
       
 bInterval               1
      
Endpoint Descriptor:
      
  bLength                 7
       
 bDescriptorType         5
       
 bEndpointAddress     0x05  EP 5 OUT
      
  bmAttributes            2
          
Transfer Type            Bulk
        
  Synch Type               None
      
    Usage Type               Data
     
   wMaxPacketSize     0x0200  1x 512 bytes
     
   bInterval               0
     
 Endpoint Descriptor:
     
   bLength                 7
     
   bDescriptorType         5
     
   bEndpointAddress     0x06  EP 6 OUT
     
   bmAttributes            2
         
 Transfer Type            Bulk
         
 Synch Type               None
         
 Usage Type               Data
        
wMaxPacketSize     0x0200  1x 512 bytes
  
      bInterval               0

```

---

### Post by anewguy on 2010-10-12
I suspect you need either a driver or to get the correct kernel module loaded and conflicting ones unloaded.  So, please do the following:

lsmod -> post the output back here

iwconfig -> post the output back here

ifconfig -> post the output back here

copy the contents of the /etc/modprobe.d/blacklist.conf file back here as well.


BTW - the redirecting of output via the ">" may need a little more explaining, depending on what you may want to do at some point in time.  A single ">" creates the output file,  whereas ">>" appends to the output.  Handy when you want to combine more than 1 output (perhaps doing a logfile, etc.).

Dave ;)

---

### Post by Hippytaff on 2010-10-12
> 
BTW - the redirecting of output via the ">" may need a little more explaining, depending on what you may want to do at some point in time. A single ">" creates the output file, whereas ">>" appends to the output. Handy when you want to combine more than 1 output (perhaps doing a logfile, etc.).

Good point...I didn't know that...useful :-)

---

### Post by tarps87 on 2010-10-12
> **wasing said:**
> ...
P.S. kind of a side not when you use a command like lsusb -a how can you go back and read the rest of the output that was cutoff.

You can use **more** or **less**
```
lsusb | more
```
and enter to scroll down
**or**
```
lsusb | less
```
For the manual
```
man less
```

---

### Post by anewguy on 2010-10-12
+1 for "less" - you can scroll up and down with it.

dave ;)

---

### Post by wasing on 2010-10-12
wow thanks tarps87 that really made my day. also thanks for all the input everyone i will definitely bookmark this thread

```
lsmod
Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10866  1 
fat                    55062  1 vfat
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_codec_realtek   279040  1 
snd_hda_intel          25677  0 
snd_hda_codec          85663  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6778  1 snd_hda_codec
snd_pcm                87248  2 snd_hda_intel,snd_hda_codec
snd_timer              23617  1 snd_pcm
nouveau               515227  1 
snd                    70946  6 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
ttm                    60815  1 nouveau
soundcore               8052  1 snd
drm_kms_helper         30774  1 nouveau
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
i2c_piix4               9639  0 
edac_core              45423  0 
k8temp                  3912  0 
drm                   198660  3 nouveau,ttm,drm_kms_helper
edac_mce_amd            9278  0 
i2c_algo_bit            6024  1 nouveau
ppdev                   6375  0 
parport_pc             29958  1 
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
xfs                   541970  2 
exportfs                4202  1 xfs
usb_storage            49801  1 
ahci                   37870  0 
r8169                  39650  0 
mii                     5237  1 r8169
pata_atiixp             4209  4 

blacklist.conf

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
iwconfig
lo no wireless extensions.

eth0 no wireless extensions.
ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1296 (1.2 KB)  TX bytes:1296 (1.2 KB)


```

for some reason iwconfig does not like to be added to the file so i had to echo it in.

---

### Post by anewguy on 2010-10-12
Try the following (don't know if the module is there or not):

sudo modprobe ath5k


Let us know if it kicks out an error.  If not, check to see if your wireless is working.

Dave ;)

---

### Post by wasing on 2010-10-12
no cigar

iwconfig and ifconfig did not change.

is there anyway to get this module online from another machine. there is no way i can run an ethernet cable to this computer.

---

### Post by anewguy on 2010-10-12
Hum, may need the entire Atheros driver.  You might want to do some net searching on ubuntu 10.10 atheros driver and see what turns up.

Dave ;)

---

### Post by wasing on 2010-10-13
will do. but would it be a good idea to just use ndiswrapper for a dirty fix install then download the atheros ath5k driver or would this muck up my system.

---

### Post by wasing on 2010-10-13
according to
[http://wireless.kernel.org/en/users/Drivers/ath9k_htc#Supported_Devices]("http://wireless.kernel.org/en/users/Drivers/ath9k_htc#Supported_Devices")
my device uses the ath9k_htc
so i will try to configure it using this site info

---

### Post by anewguy on 2010-10-13
Sounds good!  Glad you found something to help you.  If by chance you still decide on ndiswrapper, even as a stop-gap (e.g., be able to get online in the first place to try locate drivers!), let me know and I can give you simple instructions for that.

Dave ;)

---

### Post by wasing on 2010-10-13
yeah i think i am going to go the ndiswrapper route just because it will be less messy that way. i will use the tutorial in the ubuntu help section along with the troubleshooting guide in the networking forum. so i should be good thx for all your help dave, hippytaf,and tarps87.

---

### Post by Hippytaff on 2010-10-13
Glad you sorted it :-D

mark the thread as solved so others can see how you fixed it (forum tools at the top of the page)

:-D

---

### Post by anewguy on 2010-10-13
I don't know what that thread says, but I'm going to go ahead and give you simple instructions here.  First off, don't download the source and try to compile it - the posts that mention that are old.  Secondly, be sure to use ndisgtk, the GUI'd front end to ndiswrapper - it will save you a lot of headaches.

- copy you Windows XP .inf and .sys files for your adapter to your desktop

- you can install ndiswrapper and ndisgtk directly from the LiveCD -> no need for any network connection:

[LIST]
[*]After booting Ubuntu, load the LiveCD.  If a message comes up about a software source CD just cancel it.
[*]Using "Places", navigate to the /pool/main/n folder on the CD.  You will see 2 folders - 1 for ndisgtk and 1 for ndiswrapper.  These need to be installed in the following sequence:
[LIST]
[*]go to the ndiswrapper folder
[*]double click on the ndiswrapper common file to start the installation and wait for it to finish.
[*]double click on the ndiswrapper utilities file to start the installation and wait for it to finish
[*]go back to the /pool/main/n folder and then to the ndisgtk folder
[*]double click on the file for ndisgtk to start the installation and wait for it to finish
[*][/list]
[/LIST]
- After installing ndiswrapper and ndisgtk, go to System/Administration/Windows Wireless Drivers to start ndisgtk

- Use the add or new (I can't remember what it says) and point it to your desktop and the Windows XP driver .inf file and let it install

- Your driver should be loaded now

- Right-click on the network manager icon and be sure the "Enable Wireless" is checked.

- Left-click on the network manager icon and you should hopefully now see wireless networks.

- Remember that if you use MAC filtering on your router, and if this is a new PC to the network, that you will need to add the MAC address to the router list before you can connect to the router.

- If you have your router set to not broadcast the SSID ( a "hidden" network), you will need to manually set up the connection in network manager

- If you use encryption, be sure to match the type and the password/passphrase

Any problems - just post back.

Dave ;)

---

### Post by wasing on 2010-10-16
dave thx for posting that i did run into problems and eventually gave up for the past few days (i still had school work to do). anyway yeah i cant use the gtk because i am running the server version and don't have a GUI. i dont know if this is a problem but i am assuming it is.

i am just going to install the debian packages from the ubuntu archives 

[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/]("http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/")

i will still keep plugging away at it thx again for your help

---

### Post by anewguy on 2010-10-16
Sorry - didn't think that since about you on the server version.  Of course - not desktop, no GUI, and probably no ndiswrapper common or utilities on the installation CD.  When you do install ndiswrapper common and ndiswrapper utilities (hopefully the deb will have the entire package) here are some instructions:

- copy your Windows drivers to some folder in Ubuntu
- since you are using the server version, just log in since it will be a common line
- type the following:

cd xxxxxx -> what ever folder your driver files are in

sudo ndiswrapper -l -> That's a lower case "L" for list.  If anything shows up, you want to remove it first via:

sudo ndiswrapper -e xxxxxx -> Where xxxxxx is the driver/device name that shows in the list

- Now to install:

sudo ndiswrapper -i xxxxxx.inf -> Lower case "I" for install.  The xxxxxx.inf should be replaced with your .inf file name.

sudo ndiswrapper -l -> Lower case "L" again for list.  Be sure your device shows and with no errors.

sudo ndiswrapper -m -> This used to make the ndiswrapper load at boot, but for several releases it doesn't really seem to work.

sudo depmod -a

sudo modprobe ndiswrapper

That should have installed the driver and loaded the ndiswrapper kernel module.

- Now to make the loading on the ndiswrapper kernel module automatic at boot it needs to be added to the /etc/modules file.  Since this is the command line, I would think you're going to have to use vi or perhaps vim if it is installed.  Not sure if nano is installed in the server version. So:

using the command line editor of your choice, add the following line to the end of the /etc/modules file:

ndiswrapper

save the file and exit.  Try a reboot to be sure your wireless comes back up.


Let me know how things go with using wireless on your server.  I tried that a couple of years ago, and the wireless kept going dead after "x" amount of time with no activity, almost as if it went to sleep but then wouldn't wake up.  I tried a lot of things with that but still couldn't get it to work.  Also, if I remember correctly, I had to set up the connection to be a fixed IP address (maybe this is because I wasn't using the server as a router but relied on an external wireless router the rest of the network used for internet access).  This meant certain settings had to be defined for the various options to the connection as well.  If you find a way to make that all work and not go to sleep I'd sure be interested to know what you did!

Dave ;)

---

### Post by wasing on 2010-10-16
was going good until i went to check to see if the driver had installed correctly

```
netathuw : invalid driver!
```

i looked it up and people were saying that the .sys has to be in the same directory and this solved the issue but all of the files are in the directory i installed it from.

---

### Post by wasing on 2010-10-16
nvm my bad used the newest driver they had. needed to use an old one disregard

---

### Post by wasing on 2010-10-16
screwed up again need a 64 bit driver i will plug away again tomorrow

---

### Post by anewguy on 2010-10-18
Also remember with ndiswrapper, they must be the Windows XP drivers.

Dave ;)

---

