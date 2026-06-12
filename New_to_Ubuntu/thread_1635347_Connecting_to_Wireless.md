---
title: "Connecting to Wireless"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by Katana24 on 2010-12-01
Hello - i just got Ubuntu installed on my computer and i am trying to use a wireless USB device to connect to the internet. I need people to correct me if i am wrong here:

If the device that I have doesn't have the correct drivers then it shouldn't be-able to see any networks? 

Because it can see my wireless network and i enter the CORRECT password but it still won't connect. I am absolutely sure that the password for the wireless is correct I have tried it many times on other devices and they can all access it. 

So what is the problem with Ubuntu?

---

### Post by lkraemer on 2010-12-01
1. How do I know what Hardware my computer has, and what Drivers
(Modules) are loaded?

Open a Terminal Window (Console) and use these commands to get
more information on your hardware, wireless, Windows loaded drivers,
and Linux drivers that are currently blacklisted. Copy & Paste to
prevent errors!
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
ifconfig
iwconfig

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
If you are requesting help, post the output of each command........

Are you sure that the Wifi is ENABLED? Is there a Switch or Special
Keystrokes (maybe CNTL F2) that turns it ON/OFF?  Don't worry about
the LED Color, as it may be incorrect...........


You could try to manually configure the Wifi Interface, if it is ENABLED.

**Manual Configure:**
If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```
example......for Airlink and Wlan0
```

sudo iwconfig Wlan0 essid "Airlink"

```

You may also have some Drivers loaded that may need to be Blacklisted,
because you tried more than one way to get the Wifi functional.  Your
postings will assist us in determining those conditions.

It's not Ubuntu, but we need to know the version you are running, and
if it is 32 bit or 64 bit.  Also if you tried to use ndiswrapper, and any
Windows Drivers......You must use Windows 32 Bit Drivers for Ubuntu 32 bit
and likewise for 64 bit.  Do NOT mix and match Drivers.  And maybe how
many ways or guides you followed.............to save us some time.

You didn't mention if you have tried an Ethernet connection.

Be sure to check your browser to make sure it isn't set for OFFLINE.


Try the following commands:
```

route
route -n
route -nee
netstat -r
ping yourgatewayIPaddress

```
If you can't ping the Gateway IP address then your Login & Password
for your ISP are incorrect.

Connect via an Ethernet Cable, then make sure ENABLE NETWORKING is checked.
Then open a Terminal Window and do:
```

ping www.yahoo.com

```
CNTL C will terminate the transmission. You should see:
```

[larry@localhost ~]$ ping www.yahoo.com
PING any-fp.wa1.b.yahoo.com (72.30.2.43) 56(84) bytes of data.
64 bytes from ir1.fp.vip.sk1.yahoo.com (72.30.2.43): icmp_req=1 ttl=53 time=76.8 ms
64 bytes from ir1.fp.vip.sk1.yahoo.com (72.30.2.43): icmp_req=2 ttl=53 time=81.3 ms
64 bytes from ir1.fp.vip.sk1.yahoo.com (72.30.2.43): icmp_req=3 ttl=53 time=79.7 ms

```
If that doesn't work try:
```

ping 72.30.2.43

```
If you can't get to [www.yahoo.com](www.yahoo.com), double check your DNS Servers are
set in the DSL/Cable Modem. You might want to set the OpenDNS Servers instead.
Google OpenDNS Servers
```

208.67.222.222
208.67.220.220

```

Then try setting up Wifi after ETHERNET is working.


lk

---

### Post by Katana24 on 2010-12-02
Hello i tried alot of your code that you have and I have alot of output - im not sure if you want to wade through it or not?

---

### Post by Katana24 on 2010-12-02
I decided to try to ping my network and this is part of the output:


64 bytes from My IP Number: icmp_req=36 ttl=64 time=0.036 ms
64 bytes from My IP Number: icmp_req=37 ttl=64 time=0.036 ms
64 bytes from My IP Number: icmp_req=38 ttl=64 time=0.035 ms
64 bytes from My IP Number: icmp_req=39 ttl=64 time=0.035 ms
64 bytes from My IP Number: icmp_req=40 ttl=64 time=0.036 ms
64 bytes from My IP Number: icmp_req=41 ttl=64 time=0.035 ms
64 bytes from My IP Number: icmp_req=42 ttl=64 time=0.034 ms
64 bytes from My IP Number: icmp_req=43 ttl=64 time=0.035 ms
64 bytes from My IP Number: icmp_req=44 ttl=64 time=0.036 ms
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable

So this means that the username and password is correct but I just can't get on right? I also changed FireFox to online by unchecking the "OffLine" option in the file menu but it didn't make a difference. 

This is just frustrating now...>:( I don't mean to blame Ubuntu but i thought it was suppose to be user-friendly lol :D

---

### Post by TBABill on 2010-12-02
Let's just start with the easy one. Type this into a terminal and paste the output so we can know what kind of device you have and what chipset it has: ```
lshw -C network
```

---

### Post by theozzlives on 2010-12-02
Are you using SAMBA? If so, did you set your smbpasswd?
```
sudo smbpasswd -a <your username>
```

---

### Post by Katana24 on 2010-12-02
I got this output after entering lshw -C network:

andrew@andrew-HP-d530-USDT-DG010T:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5782 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: eth0
       version: 03
       serial: 00:40:ca:75:f1:4e
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.110 firmware=5782-v3.13 ip=192.168.1.6 latency=64 mingnt=64 multicast=yes
       resources: irq:20 memory:f8500000-f850ffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:02:72:8e:65:52
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g/n ...


What now? Btw what is SAMBA and why do i need it?

---

### Post by lkraemer on 2010-12-02
The only way you will get help is to copy & paste each command in a
Terminal Window, ans post the output.

Go ahead and post the info.

Don't worry about Samba.  You won't use it now.

lk

---

### Post by Katana24 on 2010-12-04
Hello - I finally got to my computer and ran all the commands. I have listed all the output as below, sorry there's so much:

andrew@andrew-HP-d530-USDT-DG010T:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
05:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet (rev 03)

--------------------------------------------------------------------------------------

andrew@andrew-HP-d530-USDT-DG010T:~$ lsusb
Bus 004 Device 002: ID 045e:0750 Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 1e3d:2092  
Bus 001 Device 003: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

--------------------------------------------------------------------------------------

andrew@andrew-HP-d530-USDT-DG010T:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5782 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: eth0
       version: 03
       serial: 00:40:ca:75:f1:4e
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.110 firmware=5782-v3.13 latency=64 mingnt=64 multicast=yes
       resources: irq:20 memory:f8500000-f850ffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:02:72:8e:65:52
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g/n ...

--------------------------------------------------------------------------------------

andrew@andrew-HP-d530-USDT-DG010T:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
usb_storage            40172  1 
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_intel8x0           25632  2 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
i915                  292683  3 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
drm_kms_helper         30168  1 i915
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
joydev                  8735  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168054  4 i915,drm_kms_helper
r8192s_usb            287340  0 
usbhid                 36882  0 
snd                    49006  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hid                    67742  1 usbhid
intel_agp              26424  2 i915
i2c_algo_bit            5168  1 i915
soundcore                880  1 snd
shpchp                 29886  0 
serio_raw               4022  0 
eeprom_93cx6            1345  1 r8192s_usb
video                  18712  1 i915
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
tg3                   123310  0 

--------------------------------------------------------------------------------------

andrew@andrew-HP-d530-USDT-DG010T:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common

--------------------------------------------------------------------------------------

andrew@andrew-HP-d530-USDT-DG010T:~$ cat /etc/modprobe.d/blacklist.conf
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

--------------------------------------------------------------------------------------

andrew@andrew-HP-d530-USDT-DG010T:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:ca:75:f1:4e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:02:72:8e:65:52  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:142 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

--------------------------------------------------------------------------------------

andrew@andrew-HP-d530-USDT-DG010T:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g/n ...  ESSID:"Home VM"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:1B:2F:56:63:DC   
          Bit Rate=130 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

--------------------------------------------------------------------------------------


And done - any suggestions or should i just rid myself of this desktop?

---

### Post by Penguin=) on 2010-12-04
Go to the USB tab and select your device!

---

### Post by Katana24 on 2010-12-05
Will that solve the problem? If so how?

---

### Post by Katana24 on 2010-12-05
Where is this 'USB Tab' located?

---

### Post by lkraemer on 2010-12-05
What Version of Ubuntu do you have installed?
What is the Manufacture & Model Number & Name of the USB Wifi Device?
Any more information you could share about it?  Website?

lk

---

### Post by anewguy on 2010-12-05
Your wireless adapter shows in the lsusb output as the Realtek RTL8188SU.  A cursory search of the web turned this up right away:

[http://ubuntuforums.org/showthread.php?p=10009171#post10009171]("http://ubuntuforums.org/showthread.php?p=10009171#post10009171")

If you need help with that, just post back.

Dave ;)

---

### Post by Katana24 on 2010-12-06
My Ubuntu version is 10.10 - the latest version.

The USB device which I have is an LM Technologies NANO USB Adapter - LM006, whose website is [http://www.lm-technologies.com/business/product_category.php?prod_cat_id=3](http://www.lm-technologies.com/business/product_category.php?prod_cat_id=3)

It has directions for downloading the appropriate Linux driver but I really don't know what to do there as its mostly using the Terminal and I'm not Linux savvy yet.

---

### Post by anewguy on 2010-12-06
Regardless of the brand, this line from the lsusb output:

Bus 001 Device 003: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter

states quite clearly it is using the RTL8188SU chipset.  The link I posted is for this device.


The driver file that I downloaded from your link must first be decompressed - just clicking on the downloaded file should open up the extract manager for you.

Once you've done that, read the readme.txt.  It is not the best written one I have seen, but read it a few times.  There is a script you run from the terminal (command line) to build the driver.  There is a script you run from the terminal (command line) if you need wpa support.  There are scripts for configuring wpa, bring the network up and bringing the network down.

I am not familiar with it since I don't own an adapter with that chipset.  However, I am more than willing to try to walk you through what is needed.  I guess one of the basic things we need to know is if the network you want to connect to uses wpa of any form, as the adapter only does wep by default.  We will need to run that script for wpa and configure it if you need wpa support.

So, post back with that info, and we'll try to go from there.  This will be a new run for me as well, so bear with me.  If anyone out there already has experience installing this driver, *please* post back!

Dave ;)

---

### Post by lkraemer on 2010-12-06
Katana24,
Dave is correct!  You need to compile the code.  As an example I created
a subdirectory named LM006.  I downloaded the file there, and extracted it
with file roller.  Then I changed to that subdirectory.

```

[larry@localhost rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091112.p4]$ pwd
/home/larry/LM006/60G127100-06 CD content(name_WLAN 11n USB)/Linux/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091112.p4
[larry@localhost rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091112.p4]$ ls
document  driver  readme.txt  ReleaseNotes.doc  wpa_supplicant
[larry@localhost rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091112.p4]$

```


Typically you need to install build-essential, and the headers for the
kernel you are running, if you are going to compile code.
```

uname -r

```
will tell you the kernel you are currently running.
```

sudo apt-get install build-essential linux-headers-$(uname -r)

```
will install the software needed to compile your code.


**TYPICAL COMPILE STEPS:** (from within your source directory)
```

cd /path/to/source
tar xvf packagename.tar.gz
cd /folder/of/extracted/source
./configure
make clean
make
sudo make install

```
"make clean" won't remove anything on the first compile, but will clean up
on a successive compile.

You can also use checkinstall to build a deb file.

REF:
[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)


There are three things you need to do.
1.  READ the readme.txt several times.
2.  Compile the source located in the subdirectory named driver.
3.  Extract, and compile the code in the subdirectory wpa_supplicant.

Just be sure to use cd to change to those subdirectories before running
the make.  You won't need to run ./configure for this code.

```

cd driver
ls -alt

```
then proceed with the make.....
```

make

```

At this point I need to read some more. Also there is a Power Point .ppt file that 
might be of use.  I don't have a viewer installed.  This is up to you.

Dave....THANKS.....and any Thoughts/Ideas?

lk

---

### Post by anewguy on 2010-12-06
Well, something to keep in mind is that if the wireless is not working the user may not have internet access.  No internet access = no apt-get.  So, for everyone who may not know, build-essential is delivered on the LiveCD in the /pool/main/b/build-essential folder.  That way it is current for the kernel delivered on the CD.

Dave ;)

---

### Post by Katana24 on 2010-12-07
Hello - quick update - I have read the readme.txt file and, honestly, it may as well be written in Japanese because it makes no sense to me. A step by step on this would be really quite appreciated as I'm near my wits end here!

---

### Post by Katana24 on 2010-12-11
To all who may have the same problem - I haven't managed to resolve my problem with the wireless adapter but if I do I'll post it here.

---

### Post by nickk9 on 2011-02-09
I got my LM006 working on Ubuntu 10.04! I gave up on the NDIS Wrapper method as that would show the network but never accept the password.

Compiling worked, and here's what I did:

Downloaded latest RTL8188SU driver from RealTek: [http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188SU]("http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188SU") and unzip on Desktop (or elsewhere if prefered)

Next extract the contents of the rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111.tar.gz file, which is located in the 'driver' folder (of the unzipped archive above)

Open terminal and run the following:
```
sudo apt-get install build-essential linux-headers-$(uname -r)
cd ~/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111
make
sudo insmod 8712u.ko
```

You should now see the wireless network from the NetworkManager applet (on the toolbar), and connect to your wireless network ok.

You'll loose it on a reboot though and either have to manually run insmod every time, or (from same terminal):

```
sudo mkdir /lib/modules/2.6.32.22-generic/kernel/drivers/net/wireless/rtl8712/
sudo cp 8712u.ko /lib/modules/2.6.32.22-generic/kernel/drivers/net/wireless/rtl8712/
sudo nano /etc/modules
```

and edit the file to look like below:
```

 /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

8712u
lp
```

Finally run:

```
sudo depmod –a
sudo reboot
```


Notes:
1) Downloaded driver version may differ from above, so change name accordingly.
2) Path will differ depending on your current kernel version (mine was 2.6.32.22 having not been connected to the internet for sometime!)
3) You will need to recompile every time the kernel gets updated (along with re-downloading the linux-headers pacakge i believe)
4) After doing the insmod bit above, plugging in USB memory sticks would not be recognised. Seems ok after setting it up to auto load via the depmod bit, etc.


Hope this helps.

---

