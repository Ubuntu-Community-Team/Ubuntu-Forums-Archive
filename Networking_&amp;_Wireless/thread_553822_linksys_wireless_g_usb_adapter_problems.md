---
title: "linksys wireless g usb adapter problems"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by jrmink on 2007-09-18
I am a new to linux and have no idea how to install a wireless internet device. I am running Ubuntu 7.04 Fiesty Fawn on my box. I currently have an ethernet cable hooked up to my computer but I would like very much to get it online wirelessly asap.

I have a Linksys wireless g usb network adapter 802.11g Model No. WUSB54G.  Basically I was wondering if anyone knew of a how to link to get my network adapter installed and working or if anyone has a solution.

Also the wireless network it will be connecting to has WEP security and is run on a windows OP.  I'm not sure if that makes a difference.

Thanks
jrmink

---

### Post by nzlee34 on 2007-09-18
I have the same device. To configure it i just had to set the name and encryption settings in the network dialog (under system/administration menu). what version of that model is it? (i have version 4) if that still does not solve your problem i would suggest using ndiswrapper.

EDIT: I forgot to say that it may help if you disable your ethernet connection. for some reason my wireless will not work when a wired connection is present.

---

### Post by jrmink on 2007-09-18
I believe mine is version 2 or 4 but if you could be more detailed that would be great.

Do you mean go in system > administration > then network and set it up there?  Because there is no selection for linksys usb adapter to be the network the only selections in the network menu are wired connection or modem.

---

### Post by jrmink on 2007-09-18
Still cant get it to work

---

### Post by noob12 on 2007-09-18
If you post the output of these, someone might be able to provide specific guidance:

```

lsusb

sudo lshw -C network

```

---

### Post by jrmink on 2007-09-20
Ok I will try it and post the outcome

---

### Post by jrmink on 2007-09-20
Ok here is the commands 

jrmink@jrmink-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 1915:2234  
Bus 001 Device 001: ID 0000:0000  
jrmink@jrmink-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 11
       serial: 00:04:5a:55:2e:86
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.14 ip=192.168.1.104 latency=32 maxlatency=255 mingnt=255 multicast=yes
       resources: ioport:d800-d8ff iomemory:feaffc00-feafffff irq:9
jrmink@jrmink-desktop:~$

---

### Post by noob12 on 2007-09-20
That appears to be the v1 version of WUSB54G.  It uses a Prism chipset and not the RaLink chipset used by later versions.  So be careful when applying instructions that might be based on different versions of the product.

The forum has this old thread at [http://ubuntuforums.org/showthread.php?t=418925](http://ubuntuforums.org/showthread.php?t=418925).  It provides a method using the ndiswrapper and ndisgtk from Feisty packages, but at least one participant suggests that you should use an up-to-date version of ndiswrapper from sourceforge.

I would recommend that you build your own ndiswrapper 1.47 from sourceforge.

Post back if you need more instructions.

---

### Post by jrmink on 2007-09-20
How do I "build" my own ndiswrapper?

---

### Post by jrmink on 2007-09-20
Sorry for the double post but I was couldn't install my driver for WUSB54Gv1.

I finally managed to install it but when I run lsusb nothing shows up yet.


Maybe this will help you

Oh and nothing about wireless connections shows up in network tools or the network menu in system >administration
jrmink@jrmink-desktop:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2)
02:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
02:0b.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
jrmink@jrmink-desktop:~$

---

### Post by noob12 on 2007-09-20
It was showing up in the lsusb listing.  This is the device:
```
Bus 001 Device 002: ID 1915:2234
```
I'll post instructions in a second for how to build ndiswrapper 1.48.

---

### Post by noob12 on 2007-09-20
OK.

You will also need to get the Windows XP drivers from your installation CD for your USB adapter.

First download and install packages you need to build drivers:
```

sudo aptitude update
sudo aptitude install build-essential  linux-headers-`uname -r`

```

Note that the characters are backquotes; you're best off directly cutting and pasting.

Then download and build the latest stable ndiswrapper (1.48).
```

# Make and goto the directory where we will build this
mdkir ~/ndiswrapper
cd ~/ndiswrapper

# The following downloads the package from sourceforge
wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.48.tar.gz

# Unpack the package
tar xvfz ndiswrapper-1.48

# Go into the extracted directory and build
cd ndiswrapper-1.48
make

```

Don't proceed unless you have succeeded in doing the above  Before installing the new version, we need to move/remove versions of the old version.

Disable your wireless interface if it is enabled. 
```

# This removes previous packages if you have them.
sudo aptitude remove --purge ndiswrapper-common
sudo aptitude remove --purge ndiswrapper-utils-1.9

# This removes the driver.
sudo modprobe -r ndiswrapper
sudo mv /lib/modules/`uname -r`/misc/ndiswrapper.ko  ~/ndiswrapper.ko.orig

# Go back to the build directory and install (as root)
cd ~/ndiswrapper/ndiswrapper-1.48/
sudo make install

```

That will update your ndiswrapper and ndiswrapper-utils.  We then need to install the Windows XP driver for your device.  You need to extract the Windows driver from your installation CD that came with the USB adapter, or download it from linksys.  Make sure you get the right one though.

When you've done that, let me know.

---

### Post by jrmink on 2007-09-20
Ok everything is done but I just wanted to let you know one error that came up during the process.

root@jrmink-desktop:~/ndiswrapper/ndiswrapper-1.48# mv /lib/modules/`uname-r`/misc/ndiswrapper.ko ~/ndiswrapper.ko.orig
bash: uname-r: command not found
mv: cannot stat `/lib/modules//misc/ndiswrapper.ko': No such file or directory
root@jrmink-desktop:~/ndiswrapper/ndiswrapper-1.48# cd ~/ndiswrapper/ndiswrapper-1.48/

---

### Post by noob12 on 2007-09-20
I missed the space.  That means the simple backup failed, but we can go back to the distribution if you have to get the original.

Did you finish building and installing successfully?

And have you got your Windows driver from the CD-ROM onto a file on your Ubuntu host?
What is the name of the file you have?

---

### Post by jrmink on 2007-09-20
Yes and guess what I can connect to my wireless network (I enabled it in network under administration and set the pass and username for my WEP encyrption) now but I notice my computer randomly freezes so I'm guessing there is more work to be done.  

Yes I downloaded the driver for wusb54gv1.inf

Tell me what I must do next to install the driver and yes, I have the driver in a folder in /home I used wine to unzip it there

:) 
Your my hero

---

### Post by noob12 on 2007-09-20
OK.  I'm not sure how you got all the way there.

Did you use the **ndiswrapper -i** command to install the driver?

Can you post the output of **ndiswrapper -l** and **ndiswrapper -v** please?  If you get errors, then **cd /** first.  (The commands can get confused if you have a local directory or file named ndiswrapper.)

We may have to blacklist some other drivers and if the 1.48 version is giving problems, we may need to go back to 1.47, which has been very stable.

ADDED:  Will be offline for about 1/2 hour.  Will respond when I get back.

---

### Post by jrmink on 2007-09-20
There you go

I installed the driver based off of what some other guides said to do before I started doing your stuff btw.

Im guessing we have to blacklist prism?

[COLOR="Red"]jrmink@jrmink-desktop:~$ ndiswrapper-l
bash: ndiswrapper-l: command not found
jrmink@jrmink-desktop:~$ ndiswrapper -l
wusb54g : driver installed
        device (1915:2234) present (alternate driver: prism54usb)
jrmink@jrmink-desktop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.48
vermagic:       2.6.20-16-generic SMP mod_unload 586 
jrmink@jrmink-desktop:~$[/COLOR]

---

### Post by noob12 on 2007-09-21
Yes.  The output of those look fine by the way.  


This blacklists it if you haven't already:
```

echo "blacklist prism54usb" | sudo tee -a /etc/modprobe.d/blacklist

```

You should also do the following if you haven't done the equivalent already.  I don't know what you've already done at this point.

This adds ndiswrapper to /etc/modules which tells it to load by default at boot
```

echo "ndiswrapper" | sudo tee -a /etc/modules

```

This sets up an alias in a file called /etc/modprobe.d/ndiswrapper
```

echo "alias wlan0 ndiswrapper" | sudo tee /etc/modprobe.d/ndiswrapper

```

ADDED:

After all of this, reboot and see if things are more stable.

After you are done, can you please post the output of these:
```

sudo lshw -C network

ifconfig -a

cat /etc/iftab

cat /etc/network/interfaces

sudo iwlist scan

iwconfig

```

---

### Post by jrmink on 2007-09-21
Ok now the network manager does not even show a wireless conncetion anymore after I did what you told me to do.  When I restarted it didnt start normal and I noticed something like usb 1-2: device descriptor read/64 error-110.

any ideas?


> 
jrmink@jrmink-desktop:~$ sudo lshw -C network
Password:
jrmink@jrmink-desktop:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 11
       serial: 00:04:5a:55:2e:86
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.14 ip=192.168.1.104 latency=32 maxlatency=255 mingnt=255 multicast=yes
       resources: ioport:d800-d8ff iomemory:feaffc00-feafffff irq:9
jrmink@jrmink-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:04:5A:55:2E:86  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:5aff:fe55:2e86/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:966 errors:0 dropped:0 overruns:0 frame:0
          TX packets:909 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:910243 (888.9 KiB)  TX bytes:156849 (153.1 KiB)
          Interrupt:9 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:97 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9032 (8.8 KiB)  TX bytes:9032 (8.8 KiB)

jrmink@jrmink-desktop:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:04:5a:55:2e:86 arp 1
jrmink@jrmink-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
wireless-essid minkerlan
wireless-key 361D31CCE3



iface eth0 inet dhcp





auto eth0
jrmink@jrmink-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

jrmink@jrmink-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jrmink@jrmink-desktop:~$ 


---

### Post by noob12 on 2007-09-21
Try unplugging and replugging the USB device then running **sudo modprobe ndiswrapper**

---

### Post by jrmink on 2007-09-21
Yeah I am all good now, but is that everything?

---

### Post by noob12 on 2007-09-21
Yes if you don't have stability issues, meaning freezes/crashes, you're set.

The boot-time issue may be a known issue with hotplug and this type of USB device; the workaround I've heard of is to replug it and probe the driver if necessary.  I'm not sure if there are better workarounds.  See what happens on subsequent reboots.

I'll watch the thread for awhile.  Not sure I can get you much further.

---

### Post by jrmink on 2007-09-21
Damn im sorry I lied.  It doesnt work anymore :( I kind of told you it does without testing it before.  The wireless connection comes up in network manager but now the problem is connecting it to the internet.  I have the wep security setup right....

But now it doesnt connect to the internet.

---

### Post by noob12 on 2007-09-21
If you are using NM to manage the connection, you should remove or comment out (prepend with #) the sections for wlan0 from your /etc/network/interfaces.

After doing that try ```
sudo /etc/init.d/dbus restart
```

Then Enable wireless by right-clicking on the NM icon.  Then left-click on the NM icon.  Select the network and connect.  You will be prompted for the key and the first time you enter it, you'll be prompted for a password to use to store the key in the keyring.

Describe what goes wrong where.  If you appear to be able to connect to the wireless access point, but can't get to the net, post the output of these:

```

ifconfig -a

route -n

cat /etc/resolv.conf

```

If you can't connect to the access point, then post these:

```

iwconfig

sudo iwlist scan

```

---

### Post by jrmink on 2007-09-22
When you told me to do this
> 
sudo /etc/init.d/dbus restart

Not even my wired connection showed up in network settings anymore.  So I did all of the other commands you told me to do.

BTW I am trying to connect to minkerlan connection which is WEP enabled.

> jrmink@jrmink-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:04:5A:55:2E:86  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:5aff:fe55:2e86/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1747 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1526 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1706782 (1.6 MiB)  TX bytes:228940 (223.5 KiB)
          Interrupt:9 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3470 (3.3 KiB)  TX bytes:3470 (3.3 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0C:41:D9:FA:D9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

jrmink@jrmink-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
jrmink@jrmink-desktop:~$ cat /etc/resolv.conf
# generated by NetworkManager, do not edit!

search hsd1.il.comcast.net.


nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 68.87.72.130


jrmink@jrmink-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=2 Mb/s   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jrmink@jrmink-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:70:76:FC:B2
                    ESSID:"linksys"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1
          Cell 02 - Address: 00:12:17:26:74:4F
                    ESSID:"minkerlan"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1

jrmink@jrmink-desktop:~$ 


Oh and my computer was still freezing whenever I had wireless connection enabled and I didn't know what you meant by saying

> you should remove or comment out (prepend with #) the sections for wlan0 from your /etc/network/interfaces.


---

### Post by noob12 on 2007-09-22
Until it shows up in **lsusb** nothing more can happen.  Drivers aren't going to see it either. 

It won't show up on the **lspci** ever.  That lists devices on the PCI bus.

Try unplugging the USB device.  Then reboot and plug in the device after rebooting.  Once it shows up in **lsusb** (just seeing the numbers 1915:2234 is fine) the ndiswrapper driver should see it.

---

### Post by jrmink on 2007-09-22
Ok what you said worked to get it noticed, but it still doesnt work.

> jrmink@jrmink-desktop:~$ lsusb
Bus 002 Device 002: ID 1915:2234  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
jrmink@jrmink-desktop:~$ ndiswrapper
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
jrmink@jrmink-desktop:~$ ndiswrapper -l
wusb54g : driver installed
        device (1915:2234) present (alternate driver: prism54usb)
jrmink@jrmink-desktop:~$

---

### Post by noob12 on 2007-09-22
Well, now that you've gotten to that point, can you post the output of **iwconfig** and **sudo iwlist scan** and **cat /etc/network/interfaces**?

---

### Post by jrmink on 2007-09-22
I got it working.  Finally.  The problems were that it wasnt recognizing I had the usb in before and the other problem was I had the wep key in wrong.

I guess the final thing is how to stop the freezing of my computer now?

> jrmink@jrmink-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"minkerlan"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:12:17:26:74:4F   
          Bit Rate=36 Mb/s   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:53/100  Signal level:-62 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jrmink@jrmink-desktop:~$ sudo iwlist scan
Password:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:12:17:26:74:4F
                    ESSID:"minkerlan"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:89/100  Signal level:-39 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1
          Cell 02 - Address: 00:18:39:B3:AC:97
                    ESSID:"Jewell_Network"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1

jrmink@jrmink-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface eth0 inet dhcp












iface wlan0 inet dhcp
wireless-essid minkerlan
wireless-key









auto wlan0

auto eth0
jrmink@jrmink-desktop:~$ 

---

### Post by noob12 on 2007-09-22
OK.  Some progress perhaps.  It sounds like you have the wireless working now but it is still freezing up.  Is this correct?  

Can you describe when you get the freeze?  Is it always at the same point in connecting?  Are you getting any error messages in **/var/log/kern.log** just prior to the freeze.

Does it happen if you just run the **sudo iwlist scan** repeatedly or only when you try to connect using NetworkManager?  

Also, can you confirm that you are seeing ndiswrapper as the driver when you run **sudo lshw -C network**?  Look at the configuration line.

My hope is we can get over the freezing by more blacklisting or by down-reving to ndiswrapper 1.47, but I'm not sure.

ADDED:
If you want NM to manage the wired and wireless interface, you should edit your **/etc/network/interfaces** file to look like this
```

# Loopback -- don't remove it
auto lo
iface lo inet loopback

# Commented out to let NM manage this in roaming mode
#auto eth0
#iface eth0 inet dhcp

# Commented out to let NM manage this in roaming mode
#auto wlan0
#iface wlan0 inet dhcp
#wireless-essid minkerlan
#wireless-key

```

---

### Post by jrmink on 2007-09-23
My computer freezes randomly, at anytime.  Mostly when I am browsing the internet or downloading.  But if I had no internet browsers up it would still freeze.  Hopefully you have a solution?

When I run the command "sudo lshw -C network" this is the output:

> root@jrmink-desktop:/home/jrmink# lshw -C network
  *-network               
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 11
       serial: 00:04:5a:55:2e:86
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.14 latency=32 maxlatency=255 mingnt=255 multicast=yes
       resources: ioport:d800-d8ff iomemory:feaffc00-feafffff irq:9
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0c:41:d9:fa:d9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wusb54g driverversion=1.48+The Cisco-Linksys, LLC.,01/ ip=192.168.1.103 link=yes multicast=yes wireless=IEEE 802.11g
root@jrmink-desktop:/home/jrmink# 


---

### Post by noob12 on 2007-09-23
I'm assuming you are pretty sure it is due to the new device and drivers and not other things on your host.

From your last post we see that ndiswrapper has claimed the device.   If you post your **lsmod** when the only USB device you have plugged in is the network adapter, we might see something else to blacklist.

Alternatively, it might be an issue with ndiswrapper 1.48.  We may want to try 1.47.  Same directions to build that, but replace 1.47 for 1.48 where it appears.  For my part, I have been running 1.48  without any issues for several days now, but with different windows drivers for a different device on my main laptop. 

Another possibility is that there may be a more recent Windows driver than the one on the CD that might work better.

All of these are just stabs.  Without anything in the kernel logs I don't have anything to go on.  

We should try to find someone else with specific experience using this device.

---

### Post by jrmink on 2007-09-24
I reinstalled ubuntu fiesty fawn and am going to work on it again.  Ill let you know how it goes.

---

### Post by noob12 on 2007-09-24
OK.  The instructions earlier to build ndiswrapper will still apply if you want to use them, and you can also try the version of ndiswrapper 1.38 that comes pre-installed with Feisty.  Good luck.

---

### Post by jrmink on 2007-09-25
Thanks.

I reinstalled and now I have to reinstall again because I messed my username up.

Im wondering though if I run the updates will it automatically update ndiswrapper?  I dont want it to thats why Im asking.

---

### Post by noob12 on 2007-09-25
It won't generally come on its own, but whenever you update the kernel to a new version you will get a new (old) version of the ndiswrapper driver with it.  

To be sure, you have to rebuild and resinstall the driver.  For example, with the security updates today, it reverted back to 1.38.

This is one of the worst aspects of Debian/Ubuntu to me.  It ships with many old drivers, not just ndiswrapper but pretty much across the board.  I sure hope they'll get better about this.

---

### Post by jrmink on 2007-09-25
Ok I think I  understand.

Do you think there is a different distro that would be better for me or just a better distro in general?  My friend tried slack 12, fedora, dsl, and  ubuntu and he liked fedora 6 the most.  Like he really like fedora over all of them.

---

