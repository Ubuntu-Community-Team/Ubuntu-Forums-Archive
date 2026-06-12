---
title: "HOWTO: RT73 (RT71) serialmonkey drivers"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by diepruis on 2007-04-03
[B]Please note: You can automate the process below using this thread: [http://ubuntuforums.org/showthread.php?t=757607]("http://ubuntuforums.org/showthread.php?t=757607")

Warning: The script above has not been tested extensively.[/B]

Currently, the wiki page on rt73 drivers is a tad out of date. I found that many of the instructions didn't make sense, as ralink have apparently changed things without incrementing the driver version.

A much simpler approach to getting this chipset to work is using the drivers from rt2x00.serialmonkey.com The only drivers available from this site for rt73 devices is CVS source code, so it might be slightly unstable. I haven't experienced any problems so far, however. If you do experience problems with the driver, please upload debug information to their forums. See the TESTING file (which comes with the source code) for more information on how to do this.

Okay, so here's a quick howto on setting up your rt73 / rt71 device to work in Linux by using a completely free driver.

[LIST=1]
[*] Open a terminal.
[*] Go to the directory where we'll keep the driver's source code:
```

cd /usr/src

```
[*] Download the source code. (NOTE: because /usr/src is a privileged directory, we'll need to prefix all our command with sudo from here on. Type "man sudo_root" for more information.)
```

sudo wget http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz -O /usr/src/rt73-cvs-daily.tar.gz

```
[*] If you have no internet access on the Linux install already, you will need to download [this file]("http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz") from another PC (or from Windows) and then copy it to /usr/src. Just copy the file to a flash disk or something, boot your Linux install and copy the file to your home directory. Then do the following in a terminal:
```

sudo cp ~/rt73-cvs-daily.tar.gz /usr/src
cd /usr/src

```
[*] Extract the archive you just downloaded.
```

sudo tar -xvzf rt73-cvs-daily.tar.gz

```
[*] Install needed dependencies.
```

sudo aptitude install build-essential linux-headers-`uname -r`

```
If you don't have internet access on the Linux install, refer to the section below.
[*] Compile the module.
```

cd /usr/src/rt73-cvs-yyyymmddhh/Module
sudo make

```
Note that there wont be a directory named **literally** "rt73-cvs-yyyymmddhh". The yyyymmddhh characters are placeholders which will be filled with different characters depending on the version you downloaded. To see what the actual name is, you can perform the command
```

ls -d rt73*

```
The blue entry, or the entry without the .tar.gz at the end which contains 10 numbers, is the one you want. Replace the "rt73-cvs-yyyymmddhh" above with that entry.
[*] If the module is too big, strip unnecessary stuff from it.

On some systems, the rt73 kernel module compiles to a file that is unnecessarily large. If this happens to you, you will receive a warning like this: 
```

!!! WARNING: Module file much too big (>1MB)
!!! Check your kernel settings or use 'strip'

```
If you want to make doubly sure, you can check the file's size by typing
```

ls -alh rt73.ko

```
If the file's size is in the megabytes, you are affected by this issue (it's not really a bug).

Luckily this is easily fixed, just type
```

sudo strip -S rt73.ko

```

As Abadaar points out, that -S might appear to be lower case on some displays, note that it should be upper case.

All this does is remove debugging symbols, which most users don't require. After the strip command, you can check the file size again, it should be around 240K.

[*] Install the module.
```

sudo make install 

```
[*] Make sure neither the Ubuntu, nor the RaLink modules are loaded (the former doesn't work, while the latter causes conflicts). Some other modules need to be removed as well. Don't worry if your computer complains about these modules not being found - that's a good thing.
```

sudo ifconfig wlan0 down
sudo modprobe -r rt73usb
sudo modprobe -r rt2570
sudo modprobe -r rt2500usb
sudo modprobe -r rt2x00lib

```
[*] Blacklist these modules, so that they aren't loaded on startup.
```

gksu gedit /etc/modprobe.d/blacklist (if you are using Ubuntu)
kdesu kate /etc/modprobe.d/blacklist (if you are using Kubuntu)

```
Add the following lines to the text file:
```

# Blacklist rt73usb, as it is a non-functional beta module which conflicts with the working rt73 module.
blacklist rt73usb
# Blacklist rt2570, as it causes conflicts with rt73
blacklist rt2570
# Other modules that break rt73
blacklist rt2500usb
blacklist rt2x00lib

```
[*] Load the new module.
```

sudo modprobe -v rt73

```
[*] Check whether your hardware is being detected.
```

ifconfig -a

```
This command lists all networking devices on your PC. You'll probably find several entries here, "lo" will always be present, "eth0" will be present on most modern computers. What you're looking for is an entry like "wlan0" or "wlan1". If you have a new entry that starts with "wlan", the kernel is now detecting your RT73 device and you can proceed to configure it. Note that from here on out, I assume that the interface name (that "wlan" thing) is "wlan0". If yours is "wlan1" or something similiar, you should substitute that in place of "wlan0" below.
[*] Configure the interface.
```

sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid YOUR_NETWORK_NAME_HERE
sudo iwconfig wlan0 key YOUR_WEP_KEY_HERE_OR_"off"_FOR_NO_KEY
sudo dhclient wlan0

```
Note that you must insert your network essid where it says YOUR_NETWORK_NAME_HERE and your WEP key where it says YOUR_WEP_KEY_HERE_OR_"off"_FOR_NO_KEY. Type "off" instead if you don't have a WEP key to secure your network. All this should be typed without quotation marks.
[/LIST] 

The interface should now acquire an ip address. You should now be able to browse the internet, access the network etc. If you can't then something went wrong, and you should ask for help on the forums, providing a link to this HOWTO and perhaps even posting a reply here with a link to the new topic so I can help you. Please provide any relevant output in your post, for example error messages or anything else that looks fishy to you. Note that I cannot help wth WPA related queries, as my router only supports WEP. If someone could provide instructions on getting WPA etc. to work, I would be very grateful.

If the instructions above did work for you, here's what you can do to make the interface be brought up automatically across reboots:

[LIST=1]
[*] Edit the /etc/network/interfaces file
```

gksu gedit /etc/network/interfaces (if you are using Ubuntu)
kdesu kate /etc/network/interfaces (if you are using Kubuntu)

```
[*] Look for a section containing "wlan0", if there is no such section, add the following to the bottom of the file:
```

auto wlan0
iface wlan0 inet dhcp

```
[*] Beneath those lines, add the following (*):
```

	pre-up ifconfig wlan0 up
	pre-up iwconfig wlan0 essid YOUR_ESSID
	pre-up iwconfig wlan0 key WEP_KEY_OR_"OFF"_IF_YOU_HAVE_NONE

```
[*] If you have it installed (you will if you are using dapper), remove network manager (!)
```

sudo aptitude purge network-manager

```
[/LIST]

If you have an ASCII wep key, make sure to prefix it with an "s:" (without the quotes). There should be no white space between the semicolon and the actual key. If the key is shared you need to add "restricted" (again without the quotes) directly after the "key" part. Make sure to seperate "restricted" with a space on either side of the word. Thanks to NewWithoutClue for pointing this out.

If you are using WPA security on your wireless network, then your /etc/network/interfaces file should look like this:

```

auto wlan0
iface wlan0 inet dhcp
    pre-up ifconfig wlan0 up
    pre-up iwpriv wlan0 set AuthMode=WPAPSK
    pre-up iwpriv wlan0 set EncrypType=TKIP
    pre-up iwpriv wlan0 set WPAPSK="YOUR_WPA_PSK_KEY"
    pre-up iwpriv wlan0 set SSID="YOUR_SSID"
    pre-up iwpriv wlan0 set NetworkType=Infra

```

Thanks to peterthewolf, sefs & Austin_KW for helping with this part.

If you are using a static IP address (i.e. the DHCP server on your router doesn't assign you one), use these settings (thanks to kevdog)

> Just to follow-up, one of the users I was helping posted this about getting a static IP address to work. I thought I would pass it along for the sake of completeness

```

auto wlan0
iface wlan0 inet static
address STATIC_IP_ADDRESS
netmask 255.255.255.0
network ROUTER_IP
gateway ROUTER_IP
        pre-up ifconfig wlan0 up
        pre-up iwconfig wlan0 essid YOUR_ESSID
        pre-up iwconfig wlan0 mode Managed

```


Of course, you'll need to add settings for WEP and WPA, depending on which one you're using.

NOTE: As Austin_KW rightly pointed out, if you install a new kernel (this is sometimes included in the updates), you will have to recompile the module, strip it again (if necessary) and install it over the previous one. To do this, open the terminal and go to the directory where you extracted the code originally and issue the commands listed:

```

cd /usr/src/rt73-cvs-yyyymmddhh/Module
sudo make clean
sudo make
sudo ifdown wlan0
sudo modprobe -rv rt73
sudo make install
sudo modprobe -v rt73
sudo ifup wlan0

```

Please post your results with this steps, as I need that information to make this HOWTO better. If you experience problems, please ask in a separate thread and post a link to that thread here. Please also note that I typed most of this up from memory, so there may be a few typos and glitches. If something looks fishy to you or doesn't work, please report it.

**If you have no other method of internet access on your Linux installation**
[QUOTE=kevdog]
In order to compile the serial monkey drivers from source the build-essential package is required along with the linux kernel header files. If you already have an internet connection (ie a working wired ethernet connection), please skip to step #4. Without any internet connection, please begin at step #1.

All commands typed at command prompt:
[LIST=1]
[*] After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
[*] sudo apt-cdrom add
[*] sudo aptitude update
[*] sudo aptitude install build-essential  linux-headers-`uname -r`
[/LIST]
[/QUOTE]

**Troubleshooting**

If your system hard locks after installing this driver, you should try to install a different kernel, boot into that and follow the guide again.

```

sudo aptitude install linux-server

```

TODO: Other wireless security methods (WPA etc.)

[SIZE="1"]* For the more technically minded: the reason the device is brought up before DHCP and before it's values are set is because the module requires this for some reason.

! This is because of the way network manager sets things like ESSIDs and WEPs, which is not supported by the module. The standard way network manager uses should be working with the rt73usb module, as soon as it becomes more stable.[/SIZE]

---

### Post by joeally on 2007-04-05
Thanks for the guide ive been trying for ages to get my belkin rt73 usb dongle thing to work
. I've been stuck wiith ndiswrapper for ages now, It works and detects my network, but wont connect to anything.

So I'll try this tonight

I'll tell ya if it works

Thanks Joe

---

### Post by joeally on 2007-04-05
I have installed the drivers but it wont find my belkin usb device

```
joe@joe-desktop:~$ iwconfig
lo no wireless extensions.

sit0 no wireless extensions.

rausb0 RT73 WLAN 
 Link Quality:0 Signal level:0 Noise level:113
 Rx invalid nwid:0 invalid crypt:0 invalid misc:0

```

```
joe@joe-desktop:~$ sudo iwconfig rausb0 essid Ally
Error for wireless request "Set ESSID" (8B1A) :
 SET failed on device rausb0 ; Network is down.
```

do you know why tyhis happens and how to fix it

Thanks for your help 
Joe

---

### Post by diepruis on 2007-04-05
> **joeally said:**
> do you know why tyhis happens and how to fix it

Thanks for your help 
Joe

It is being picked up, you just aren't configuring it correctly. The device needs to be brought up before you set the essid and the wep key. Sorry, this was my error, didn't notice when I was configuring the device yesterday. Please try this:

```

sudo ifconfig rausb0 down
sudo ifconfig rausb0 up
sudo ifconfig rausb0 essid ESSID
sudo ifconfig rausb0 key WEP_KEY
sudo dhclient rausb0

```

---

### Post by joeally on 2007-04-08
sorry for late reply to get it to work I just edited the etc/network/interfaces.  And I put this at the bottom:
 ```
auto rausb0
iface rausb inet dhcp
``` and then you the iwconfig and dhclinet bit worked.

I have to to this on every start up to get my internet working:
```
sudo dhclient rausb0
sudo iwconfig rausb0 essid Ally
sudo iwconfig rausb0 key a0000000000000000000000001
sudo dhclient rausb0
```


Thanks for the tutorial I was stuck for days,messing around with ndiswrapper, until I read your forum post

---

### Post by diepruis on 2007-04-08
> **joeally said:**
> ```

sudo iwconfig rausb0 essid Ally
sudo iwconfig rausb0 key a0000000000000000000000001
sudo dhclient rausb0
```


You can put all those commands in /etc/networking/interfaces as well, so it gets run automagically each boot. See the manpage for "interfaces".

> 
Thanks for the tutorial I was stuck for days,messing around with ndiswrapper, until I read your forum post


Sure thing. Glad I could help.

---

### Post by Austin_KW on 2007-04-08
You should be able to put all the config commands into etc/network/interfaces. If it does not work on boot then cycle the interface with ifdown ra0; ifup ra0. 

The ifup & down commands can be added to /etc/rc.local (as indeed can the ifconfig,iwconfig and iwpriv commands) to automatically configure ra0 at the end of the boot sequence.

I notice this howto removes the old driver from the running system with sudo modprobe -r rt73usb but this does not prevent it from reloading on boot. The rt73usb should be blacklisted in /etc/modprobe.d/blacklist

---

### Post by diepruis on 2007-04-09
> **Austin_KW said:**
> You should be able to put all the config commands into etc/network/interfaces. If it does not work on boot then cycle the interface with ifdown ra0; ifup ra0. 

The ifup & down commands can be added to /etc/rc.local (as indeed can the ifconfig,iwconfig and iwpriv commands) to automatically configure ra0 at the end of the boot sequence.


I was only waiting until I had tested this before adding it. I'll edit my original post now. Isn't ifup and ifdown already run by default? I didn't have to add anything to make them run by default...

> **Austin_KW said:**
> I notice this howto removes the old driver from the running system with sudo modprobe -r rt73usb but this does not prevent it from reloading on boot. The rt73usb should be blacklisted in /etc/modprobe.d/blacklist

Indeed you are correct. Thanks for your comments.

---

### Post by Austin_KW on 2007-04-09
Yes the ifup is done by default, However I had to add an additional ifdown, ifup sequence as it did not always succeed the dhcp request the first time. My comment (badly worded) was that any additional configuration (ifup/ifconfig/iwconfig/iwpriv) could be done automatically at the end of the boot sequence by adding the commands to /etc/rc.local.

---

### Post by joeally on 2007-04-10
thanks diepruis. Nice tip now i dont have to type in console every reboot

---

### Post by Austin_KW on 2007-04-10
For WPA-PSK; replace MyEssid & myWpaPsk, It might be a good idea to put both in "quotes" if you have any special characters (/,<space> etc)
```

auto rausb0
iface rausb0 inet dhcp
    pre-up ifconfig rausb0 up
    pre-up iwconfig rausb0 mode managed
    pre-up iwpriv rausb0 set EncrypType=TKIP
    pre-up iwpriv rausb0 set AuthMode=WPAPSK
    pre-up iwconfig rausb0 essid MyEssid
    pre-up iwpriv rausb0 set WPAPSK="myWpaPsk"
    pre-up iwconfig rausb0 essid MyEssid

```

---

### Post by alecut on 2007-04-10
Hello, 

I messed too much in the past few days to carry on by myself. I need to ask for some help on this one.

I have a system AMD Athlon 64 X2 Dual Core.
I have installed Ubuntu Festy Fawn 7.04 (Beta) for 64bit (64-bit PC (AMD64) desktop CD) to be found at [http://releases.ubuntu.com/7.04/ubuntu-7.04-beta-desktop-amd64.iso](http://releases.ubuntu.com/7.04/ubuntu-7.04-beta-desktop-amd64.iso).

I want to connect to my wireless router and use WPA encryption.
I have a USB Wireless adaptor ASUS WL-167g.

On install, I managed to make it work with an open wireless connection as well as with a WEP connection using Network Manager, but for WPA I had to go advanced.

After a lot of trouble and 3 fresh reinstallations of the whole operating system , reading one too many web pages I got to the conclusion that installing the legacy driver rt73 is the best option, disabling also the wpa_supplicant  and network_manager (which i hope i did correctly, wpa_supplicant i removed it with aptitude remove and network manager, I unticked it from System->Preferences->Sessions ).

So I followed the instructions and I think i installed rt73 correctly, I also added the ASUS device id when compiling the module as adviced, using the output from lsusb.
> BUS 002 Device 002: ID 0b05:1706.

My rt73sta.dat which is located in /etc/Wireless/RT73STA/ is reading :
> [Default]
SSID=<myssid>
NetworkType=Infra
AuthMode=WPAPSK
EncryType=TKIP
WPAPSK=<mykey>


I have some avahi business going on and I am not sure what to do with it. I do not need it so I would be happy to disable it. Which i tried with  :
sudo /etc/init.d/avahi-daemon stop

My device list using command lshw shows :> 
  *-usb
                description: Generic USB device
                product: 802.11g WLAN Drive
                vendor: ASUS
                physical id: 4
                bus info: usb@2:4
                version: 0.01
                capabilities: usb-2.00
                configuration: driver=rt73 maxpower=300mA speed=480.0MB/s

 *-network
       description: Wireless interface
       physical id: 1
       logical name: rausb0
       serial: 00:11:2f:4e:78:91
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT73 WLAN


My list of active modules for the usb adaptor using 
> lsmod |grep rt
is> 
rt73                  317440  0 
parport_pc             40104  1 
parport                43404  3 ppdev,lp,parport_pc
usbcore               154416  4 rt73,ehci_hcd,ohci_hcd

ifconfig :> 

eth0      Link encap:Ethernet  HWaddr 00:19:21:4F:3F:D3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xc000 

eth0:avah Link encap:Ethernet  HWaddr 00:19:21:4F:3F:D3  
          inet addr:169.254.6.100  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51533 (50.3 KiB)  TX bytes:51533 (50.3 KiB)

rausb0    Link encap:Ethernet  HWaddr 00:11:2F:4E:78:91  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

rausb0:av Link encap:Ethernet  HWaddr 00:11:2F:4E:78:91  
          inet addr:169.254.6.15  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

iwconfig:
> 
lo        no wireless extensions.

eth0      no wireless extensions.

rausb0    RT73 WLAN  ESSID:"ateam"  Nickname:""
          Mode:Managed  Frequency=2.437 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


This is the worrying bit :
iwlist scan:
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

rausb0    No scan results



sudo dhclient rausb0
> There is already a pid file /var/run/dhclient.pid with pid 11755
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/rausb0/00:11:2f:4e:78:91
Sending on   LPF/rausb0/00:11:2f:4e:78:91
Sending on   Socket/fallback
DHCPREQUEST on rausb0 to 255.255.255.255 port 67
DHCPREQUEST on rausb0 to 255.255.255.255 port 67
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
Trying recorded lease 192.168.1.103
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.



dmesg
> [ 2934.401126] rt73 driver version - 1.0.3.6 CVS
[ 2934.590772] ***rt73***: net_device supplies MAC, activating this one
[ 2934.590776] ***rt73***: Active MAC is: 00:11:2f:4e:78:91.
[ 3315.223437] eth0: no link during initialization.
[ 4209.045791] rt73 driver version - 1.0.3.6 CVS
[ 4209.234772] ***rt73***: net_device supplies MAC, activating this one
[ 4209.234777] ***rt73***: Active MAC is: 00:11:2f:4e:78:91.



/var/log/syslog

> Apr 10 23:34:11 alecut dhclient: No working leases in persistent database - sleeping.
Apr 10 23:34:12 alecut dhclient: DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 8
Apr 10 23:34:20 alecut dhclient: No DHCPOFFERS received.
Apr 10 23:34:20 alecut dhclient: No working leases in persistent database - sleeping.
Apr 10 23:39:57 alecut dhclient: DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 5
Apr 10 23:40:02 alecut dhclient: DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 12
Apr 10 23:40:06 alecut dhclient: There is already a pid file /var/run/dhclient.pid with pid 11755
Apr 10 23:40:06 alecut dhclient: killed old client process, removed PID file
Apr 10 23:40:06 alecut dhclient: Internet Systems Consortium DHCP Client V3.0.4
Apr 10 23:40:06 alecut dhclient: Copyright 2004-2006 Internet Systems Consortium.
Apr 10 23:40:06 alecut dhclient: All rights reserved.
Apr 10 23:40:06 alecut dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Apr 10 23:40:06 alecut dhclient: 
Apr 10 23:40:06 alecut avahi-autoipd(rausb0)[11741]: Got SIGTERM, quitting.
Apr 10 23:40:06 alecut avahi-autoipd(rausb0)[11741]: Callout STOP, address 169.254.6.15 on interface rausb0
Apr 10 23:40:06 alecut avahi-autoipd(rausb0)[11742]: client: RTNETLINK answers: No such process
Apr 10 23:40:07 alecut dhclient: Listening on LPF/rausb0/00:11:2f:4e:78:91
Apr 10 23:40:07 alecut dhclient: Sending on   LPF/rausb0/00:11:2f:4e:78:91
Apr 10 23:40:07 alecut dhclient: Sending on   Socket/fallback
Apr 10 23:40:10 alecut dhclient: DHCPREQUEST on rausb0 to 255.255.255.255 port 67
Apr 10 23:40:14 alecut dhclient: DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 10
Apr 10 23:40:17 alecut dhclient: DHCPREQUEST on rausb0 to 255.255.255.255 port 67
Apr 10 23:40:24 alecut dhclient: DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 4
Apr 10 23:40:28 alecut dhclient: No DHCPOFFERS received.
Apr 10 23:40:28 alecut dhclient: DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 3
Apr 10 23:40:28 alecut dhclient: No working leases in persistent database - sleeping.
Apr 10 23:40:28 alecut avahi-autoipd(rausb0)[11966]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 108).
Apr 10 23:40:28 alecut avahi-autoipd(rausb0)[11966]: Successfully called chroot().
Apr 10 23:40:28 alecut avahi-autoipd(rausb0)[11966]: Successfully dropped root privileges.
Apr 10 23:40:28 alecut avahi-autoipd(rausb0)[11966]: fopen() failed: Permission denied
Apr 10 23:40:28 alecut avahi-autoipd(rausb0)[11966]: Starting with address 169.254.6.15
Apr 10 23:40:31 alecut dhclient: DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 3
Apr 10 23:40:33 alecut avahi-autoipd(rausb0)[11966]: Callout BIND, address 169.254.6.15 on interface rausb0
Apr 10 23:40:33 alecut avahi-autoipd(rausb0)[11967]: client: RTNETLINK answers: File exists
Apr 10 23:40:34 alecut dhclient: DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 6
Apr 10 23:40:37 alecut avahi-autoipd(rausb0)[11966]: Successfully claimed IP address 169.254.6.15
Apr 10 23:40:37 alecut avahi-autoipd(rausb0)[11966]: fopen() failed: Permission denied
Apr 10 23:40:40 alecut dhclient: DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 12
Apr 10 23:40:52 alecut dhclient: DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 7
Apr 10 23:40:59 alecut dhclient: No DHCPOFFERS received.
Apr 10 23:40:59 alecut dhclient: Trying recorded lease 192.168.1.103
Apr 10 23:40:59 alecut avahi-autoipd(rausb0)[11966]: A routable address has been configured.
Apr 10 23:40:59 alecut avahi-autoipd(rausb0)[11966]: Callout UNBIND, address 169.254.6.15 on interface rausb0
Apr 10 23:40:59 alecut avahi-autoipd(rausb0)[11967]: client: RTNETLINK answers: No such process
Apr 10 23:41:02 alecut avahi-autoipd(rausb0)[11966]: No longer a routable address configured, restarting probe process.
Apr 10 23:41:02 alecut dhclient: No working leases in persistent database - sleeping.
Apr 10 23:41:07 alecut avahi-autoipd(rausb0)[11966]: Callout BIND, address 169.254.6.15 on interface rausb0
Apr 10 23:41:07 alecut avahi-autoipd(rausb0)[11967]: client: RTNETLINK answers: File exists
Apr 10 23:41:11 alecut avahi-autoipd(rausb0)[11966]: Successfully claimed IP address 169.254.6.15
Apr 10 23:41:11 alecut avahi-autoipd(rausb0)[11966]: fopen() failed: Permission denied



What else can I check?!  
Please help!!

Many thanks,
Alexandra

---

### Post by Austin_KW on 2007-04-10
Alexcut, Not sure how much help I can be, but I remember that the legacy drivers had problems with 64 bit and dual core. I am running one on a pentium D but in 32 bit. 

I dont know about the avahi interfaces, (rausb0:av) where is this brought up, is it in your /etc/network/interfaces.

Also I aways configure with the command line and interfaces file and not with the sta.dat file as they can conflict.

---

### Post by alecut on 2007-04-11
Hello,

Thank you for your advice Austin.

I am now writing off this machine I was complaining about :-) so I guess it is not all bad in the world.

I restarted it and of course (since i am not very good at making my drivers permanent) the rt2500usb started being used by the rausb0 interface again.

I used a script as follows to set the properties of the interface 
The essential bit in this is the static IP Address.

> sudo iwpriv rausb0 enc 3
sleep 1
sudo iwpriv rausb0 auth 3
sudo iwpriv rausb0 essid ateam
sudo iwconfig rausb0 essid "myconnection"
sudo iwpriv rausb0 wpapsk "mywpakey"
sudo iwconfig rausb0 essid "myconnection"
sleep 1
sudo ifconfig rausb0 up
sudo ifconfig rausb0 192.168.1.103
sleep 10
sudo iwpriv rausb0 enc 3
sudo iwpriv rausb0 auth 3
sudo iwconfig rausb0 essid "myconnection"


I will try the RT73 sometime in the future but for the moment I am enjoying my WPA internet  :)

Thanks again for the help.

Alexandra

---

### Post by diepruis on 2007-04-12
> **Austin_KW said:**
> For WPA-PSK; replace MyEssid & myWpaPsk, It might be a good idea to put both in "quotes" if you have any special characters (/,<space> etc)


Incorporated into the HOWTO, hope you don't mind.

---

### Post by 01ago on 2007-04-12
Thank you so much!!! The HOWTO is so useful to rookie ubuntu users (using rt73 wireless card)!
I hadn't get my rt73 to work before, untill I read this post.
I noticed that I'd missed one line before:
   sudo aptitude install build-essential linux-headers-`uname -r`
Now everything on Ubuntu seems fine. LOL!

---

### Post by alecut on 2007-04-12
Just an update and maybe this should be mentioned in the HOWTO for RT73. RT73 does not support SMP and PREEMT.

Even though it is the adviced way to go and it works very nicely for most of the latest wireless USB adaptors, the RT73 adaptor does not support multi processors. So it won't be working for my dual core machine.

I was just trying to come back to it since my RT2500USB is so unstable but now after a bit more reading I realize i need to try and setup my rt2x00.

Regards,
Alexandra.

---

### Post by diepruis on 2007-04-13
> **01ago said:**
> Now everything on Ubuntu seems fine. LOL!

It's usually something silly like that. Glad I could help.

[QUOTE=alecut]Just an update and maybe this should be mentioned in the HOWTO for RT73. RT73 does not support SMP and PREEMT.[/QUOTE]

I didn't realise this was the case for RT73 as well. I know RT61 has problems with it. I'll add the information to the HOWTO, thanks.

---

### Post by ceaseoleo on 2007-04-16
Im currently using Feisty Fawn beta, and the rt73 wireless drivers were working up until the last update on friday the 13th possibly  ( Around this time) .  Ive tried just about everything and can't seem to make any sense out of it.  Any ideas??

---

### Post by diepruis on 2007-04-17
> **ceaseoleo said:**
> Im currently using Feisty Fawn beta, and the rt73 wireless drivers were working up until the last update on friday the 13th possibly  ( Around this time) .  Ive tried just about everything and can't seem to make any sense out of it.  Any ideas??

I'm not following the development of Feisty, but if a new kernel was released in that update, you will have to recompile the driver. Please try this:

```

cd /usr/src/rt73-cvs-yyyymmddhh/Module
sudo make clean
sudo make
sudo make install

```

(Replacing the yyyymmddhh as appropriate.)

Reboot and it *should* work.

---

### Post by ceaseoleo on 2007-04-20
thanks diepruis for the help ..
i waited till the final release of feisty to retry, but still no luck.  
I also refereneced [http://ubuntuforums.org/showthread.php?t=402472&highlight=rt73](http://ubuntuforums.org/showthread.php?t=402472&highlight=rt73)

whats the difference between the rt73 drivers and rt2x00 drivers ? should I attempt to use those drivers.

---

### Post by diepruis on 2007-04-20
> **ceaseoleo said:**
> whats the difference between the rt73 drivers and rt2x00 drivers ? should I attempt to use those drivers.

rt2x00 is an attempt to create a unified driver for all the rt chipsets. It's still very much in beta however (at least for rt61 and rt73) so I doubt it'll work.

Could you please attach /var/log/dmesg ?

---

### Post by dgel on 2007-04-20
Hey

I just installed feisty, in the hope it would get my linksys wusb54gc working, but no deal (haven't had it working under linux ever). So i want to give this a try, however, do i need to uninstall the network manager feisty comes with in order to safely do this? and if so, what is the best way to uninstall it completely?

it would be great if you could help.

---

### Post by lemmyc on 2007-04-20
Hi,
I'm having Feisty problems too.
I had my Belkin USB wireless gadget working on Edgy using these instructions: 
[LINK]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29")

I tried the same thing under Feisty and it didn't work. So I tried the method in this thread. I get to stage 10, type  sudo ifconfig rausb0 up
and get the following message: rausb0: ERROR while getting interface flags: No such device

The compile seemed to go without any problems. I think the problem with the previous method was the same - device couldn't be found.

Any ideas? I'm fairly new to Linux, maybe it's something simple in this case...

---

### Post by diepruis on 2007-04-20
> **Na-Fiann said:**
> Hey

I just installed feisty, in the hope it would get my linksys wusb54gc working, but no deal (haven't had it working under linux ever). So i want to give this a try, however, do i need to uninstall the network manager feisty comes with in order to safely do this? and if so, what is the best way to uninstall it completely?

it would be great if you could help.

Yes you do. The steps to do this are outlined in the HOWTO, along with the motivation.

---

### Post by diepruis on 2007-04-20
> **lemmyc said:**
> Any ideas? I'm fairly new to Linux, maybe it's something simple in this case...

Mmm... could you please attach the output of 
```

lsusb
iwconfig
ifconfig

```

---

### Post by lemmyc on 2007-04-20
Sure - 
lsusb:

```
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 050d:705a Belkin Components 
Bus 001 Device 001: ID 0000:0000  

```

iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

```

ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:C1:26:05:47:76  
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2c1:26ff:fe05:4776/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6850392 (6.5 MiB)  TX bytes:1470572 (1.4 MiB)
          Interrupt:9 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:149 errors:0 dropped:0 overruns:0 frame:0
          TX packets:149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11495 (11.2 KiB)  TX bytes:11495 (11.2 KiB)

```

---

### Post by diepruis on 2007-04-20
In reply to lemmyc:

It seems that the driver isn't creating a device. Could you please copy the output of "lsmod" to a file and attach (not post) that. Could you also please attach /var/log/dmesg?

---

### Post by lemmyc on 2007-04-20
OK, here's lsmod. I'm having problems attaching the other dmesg file -  will keep trying.
Thanks for your help!

---

### Post by lemmyc on 2007-04-20
Here's dmesg...

---

### Post by Austin_KW on 2007-04-20
lemmyc,
you have 2 ralink drivers installed, rt2570 and rt73
Remove & blacklist the 2570 driver
"sudo modprobe -r rt2570"
then edit /etc/modprobe.d/blacklist and add "blacklist rt2570"

This should be added to the howto?

---

### Post by dgel on 2007-04-20
Hey

thanks for the howto and the help :) I almost have the network up and running now. i followed your steps and used the directions for wpa-psk, which worked fine. I could unplug the network cable and still use google, which i found proof enough that it worked. i then edited the interfaces file and rebooted to see if it worked, but it didnt. somehow my usb adapter isnt even active.
Iwconfig gives the right essid but it doesnt seem to do anything..

here's the result from iwconfig, hope that helps.

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

rausb0    RT73 WLAN  ESSID:"censored"  Nickname:""
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:14:7F:82:BA:83   
          Bit Rate=18 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=46/100  Signal level:-78 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ifconfig only lists my ethernet currently.

---

### Post by diepruis on 2007-04-20
> **Austin_KW said:**
> lemmyc,
you have 2 ralink drivers installed, rt2570 and rt73
Remove & blacklist the 2570 driver
"sudo modprobe -r rt2570"
then edit /etc/modprobe.d/blacklist and add "blacklist rt2570"

This should be added to the howto?

This does seem to be what's happening. I noticed that the kernel is trying to load rt73usb as well, but that it doesn't appear in the loaded modules list. Please check that "blacklist rt73usb" also appears in /etc/modprobe.d/blacklist. Please also issue the following command again:

```

sudo modprobe -v rt73

```

just to make sure rt73 is being loaded.

I will add information on blacklisting and removing rt2570 to the howto.

---

### Post by diepruis on 2007-04-20
> **Na-Fiann said:**
> Hey

thanks for the howto and the help :) I almost have the network up and running now. i followed your steps and used the directions for wpa-psk, which worked fine. I could unplug the network cable and still use google, which i found proof enough that it worked. i then edited the interfaces file and rebooted to see if it worked, but it didnt. somehow my usb adapter isnt even active.
Iwconfig gives the right essid but it doesnt seem to do anything.

No problem.

I'm not sure what could be the problem here. If you could attach your /etc/network/interfaces file, I could have a look at that. Please also attach /var/log/dmesg and the output from lsusb.

This problem can also be caused by network-manager under Feisty. Are you sure you uninstalled it completely?

Lastly, please check whether this works:
```

sudo ifdown rausb0
sudo ifup rausb0

```

If it doesn't, please also attach the output from those commands.

---

### Post by lemmyc on 2007-04-20
Hm, well I'm pretty sure both RT73usb and RT2570 are blacklisted, that was part of the procedure that worked with Edgy, which I also tried on Feisty.
I don't have access to that machine right now, will check later and give it another try.

---

### Post by dgel on 2007-04-20
Hey

yeah ifdown ifup seems to work, i'm now writing this on the wireless  connection.
i'm quite sure the network manager is uninstalled, if you want to make sure, here is the output if i try again:

$ sudo aptitude purge network-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done



The dmesg file was a bit too large, so i had to split it up :p
thanks for the help:)

---

### Post by Bad_Byte on 2007-04-20
Thanks diepruis, your post fixed my wusb54gc upgrade problems :) . Now I only need a voodoo priest to put a curse the guy(s) who made rt73usb which out of the box detected my network but wouldn't let me connect to it ](*,).

---

### Post by diepruis on 2007-04-20
> **Na-Fiann said:**
> Hey

yeah ifdown ifup seems to work, i'm now writing this on the wireless  connection.
i'm quite sure the network manager is uninstalled...

Since the command line tools work, I'm guessing that something is overriding them. I seem to remember removing another program in addition to network-manager when I was configuring the device, but I can't seem to remember what it was. I think the program was the GNOME graphical network management application. Could you please try to remove that? If that works, could you please post which package you had to remove? I think the software is somewhere under System, sorry I can't be more specific.

---

### Post by diepruis on 2007-04-20
> **Bad_Byte said:**
> Thanks diepruis, your post fixed my wusb54gc upgrade problems :) . Now I only need a voodoo priest to put a curse the guy(s) who made rt73usb which out of the box detected my network but wouldn't let me connect to it ](*,).

No problem :) glad to hear it worked for you.

---

### Post by dgel on 2007-04-20
Hi

yeah i think the program you mean is under system->Administration->Network
Problem is, i don't have a clue how to remove it (and i probably don't even want to:p)
sure there is no other way?

EDIT> I found network manager under system->preferences->sessions but unchecking it so it won't start doesn't solve the problem, so i think uninstalling that program wil do very little
(it's nm-applet btw)
EDIT EDIT> well it wouldn't do anything anyway, seems like nm-applet isn't even installed :/ i'm really stuck here

---

### Post by diepruis on 2007-04-20
> **Na-Fiann said:**
> Hi

yeah i think the program you mean is under system->Administration->Network
Problem is, i don't have a clue how to remove it (and i probably don't even want to:p)
sure there is no other way?

EDIT> I found network manager under system->preferences->sessions but unchecking it so it won't start doesn't solve the problem, so i think uninstalling that program wil do very little
(it's nm-applet btw)
EDIT EDIT> well it wouldn't do anything anyway, seems like nm-applet isn't even installed :/ i'm really stuck here

Hmmm.... I believe the culprit **was** under System->Administration->Network. You can try to set up your connection from there, or try to get it to not configure your network. I just can't remember the exact solution. I do remember that there was some GNOME application other than NetworkManager that was overriding the standard tools.

If anyone has more experience with GNOME than I do, now's the time to jump in. There must be a simple way to get this application to not override iwconfig.

---

### Post by dgel on 2007-04-20
Can't anyone help? this is a really odd problem, which should not exist at all.
For the record, I reinstalled ubuntu following the instructions earlier to the letter, but the same problem remains. So anyone know what other program might be interfering and how to get rid of it?

---

### Post by lemmyc on 2007-04-20
Hey, 
I seem to have got things working here. I removed rt73, as I think the old version was still being used (not the one compiled by the serialmonkey code), then went through the steps again.
Everything seemed to work this time, but then iwconfig showed the wrong essid. But I had my network interfaces file set up with the right essid and key, so I rebooted, and here we are..!

Thanks for the howto and the help!

---

### Post by peterthewolf on 2007-04-20
A simpler howto is at 

If you follow this wiki then the dwl-g122 H/W ver C1 F/W ver 3.00 will work using WPA
[http://wiki.ubuntu-it.org/RalinkRT73](http://wiki.ubuntu-it.org/RalinkRT73)

---

### Post by sefs on 2007-04-20
At sudo make i get this.

```

sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/genksyms/lex.o
  HOSTLD  scripts/genksyms/genksyms
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost
make[2]: *** No rule to make target `arch/i386/kernel/msr.c', needed by `arch/i386/kernel/msr.o'.  Stop.
make[1]: *** [arch/i386/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
rt73.ko failed to build!
make: *** [module] Error 1

```

anyideas what i did wrong?

Thanks.

---

### Post by diepruis on 2007-04-21
> **sefs said:**
> anyideas what i did wrong?

Thanks.

What's the output of ```
sudo aptitude search ^linux-headers
```

---

### Post by diepruis on 2007-04-21
> **lemmyc said:**
> Thanks for the howto and the help!

No problem :)

---

### Post by dgel on 2007-04-21
Thanks peter, it now works:)

ive changed the code in interfaces to the following 

```


auto rausb0
iface rausb0 inet dhcp
    pre-up ifconfig rausb0 up
    pre-up iwconfig rausb0 essid "censored"
    pre-up iwconfig rausb0 mode managed
    pre-up iwpriv rausb0 set AuthMode=WPAPSK
    pre-up iwpriv rausb0 set EncrypType=AES
    pre-up iwpriv rausb0 set WPAPSK="censored"
    pre-up iwpriv rausb0 set SSID="censored"


```

This works just fine, maybe an idea to change in the original post?

Thanks for all the help btw

---

### Post by diepruis on 2007-04-21
> **Na-Fiann said:**
> This works just fine, maybe an idea to change in the original post?

Thanks for all the help btw

Sure ;) Changed the original post, as the previous information looked a bit strange. Guess I was wrong about the other program that was interfering. Memory's not what it used to be, you know :)

So for everyone else, removing network-manager should be enough, there's no need to randomly go purging other programs.

---

### Post by ceaseoleo on 2007-04-21
Thanks diepruis for all the help on this subject.  I finally got it working.

For others you do have to remove Network Manager.  
and 
#wireless drivers that break rt73
blacklist rt2500usb
blacklist rt2x00lib
blacklist rt73usb

blacklist all of these in /etc/modprobe.d/blacklist file .. just add is

---

### Post by diepruis on 2007-04-21
> **ceaseoleo said:**
> Thanks diepruis for all the help on this subject.  I finally got it working.

For others you do have to remove Network Manager.  
and 
#wireless drivers that break rt73
blacklist rt2500usb
blacklist rt2x00lib
blacklist rt73usb

blacklist all of these in /etc/modprobe.d/blacklist file .. just add is

You're welcome :) I'll add those modules to the HOWTO. However, some people DO need to remove network-manager. I cite personal experience in support of this, along with this blog entry: [http://loktarogar.blogspot.com/2007/04/take-that-network-manager.html](http://loktarogar.blogspot.com/2007/04/take-that-network-manager.html)

If you didn't need to remove it, then good for you. But if you notice that your device isn't being brought up properly on restart, but works properly with ifup / ifdown then you should give it a try.

---

### Post by Gaute65 on 2007-04-21
Thank you diepruis, have some :popcorn: 

I finally got my wireless working again.

---

### Post by sefs on 2007-04-21
Hi again thanks for your response.

The output of that command gives me
```

fshlinux@fshlinux:~$ sudo aptitude search ^linux-headers
v   linux-headers                                          -                                                                 
v   linux-headers-2.6                                      -                                                                 
i   linux-headers-2.6.20-15                                - Header files related to Linux kernel version 2.6.20             
p   linux-headers-2.6.20-15-386                            - Linux kernel headers for version 2.6.20 on i386                 
i   linux-headers-2.6.20-15-generic                        - Linux kernel headers for version 2.6.20 on x86/x86_64           
p   linux-headers-2.6.20-15-lowlatency                     - Linux kernel headers for version 2.6.20 on x86/x86_64           
p   linux-headers-2.6.20-15-server                         - Linux kernel headers for version 2.6.20 on x86/x86_64           
p   linux-headers-2.6.20-15-server-bigiron                 - Linux kernel headers for version 2.6.20 on BigIron Server Equipm
p   linux-headers-386                                      - Linux kernel headers on 386                                     
p   linux-headers-686                                      - Obsoleted by: linux-headers-generic                             
i   linux-headers-generic                                  - Generic Linux kernel headers                                    
p   linux-headers-k7                                       - Obsoleted by: linux-headers-generic                             
p   linux-headers-lowlatency                               - Low latency Linux kernel headers                                
p   linux-headers-server                                   - Linux kernel headers on Server Equipment.                       
p   linux-headers-server-bigiron                           - Linux kernel headers on BigIron Server Equipment.               

```

> **diepruis said:**
> What's the output of ```
sudo aptitude search ^linux-headers
```

---

### Post by Mituness on 2007-04-21
Thanks so much for this guide! I've been struggling with getting my wireless working since I installed Feisty, and this helped right away. Thank you! :KS

---

### Post by dcapurro on 2007-04-21
Hi, Im new to Ubuntu 7.0.4 I just installed it on my Laptop. I cannot connect to the internet with it yet so I downloaded the rt73 USB nightly CVS tarball with another computer to pass it to the laptop with a pendrive. The thing is that I don`t know where to put the compressed folder so that tha instructions that you give will work.

Thank you

---

### Post by Austin_KW on 2007-04-21
> **dcapurro said:**
> Hi, Im new to Ubuntu 7.0.4 I just installed it on my Laptop. I cannot connect to the internet with it yet so I downloaded the rt73 USB nightly CVS tarball with another computer to pass it to the laptop with a pendrive. The thing is that I don`t know where to put the compressed folder so that tha instructions that you give will work.

Thank you

It does not matter where you put it, just follow the instructions and the "sudo make install" will automatically copy the driver to the correct location. The most convient location will be in your home folder as this is where the terminal will be at initially

---

### Post by diepruis on 2007-04-22
> **sefs said:**
> 
anyideas what i did wrong?

Thanks.

Mmm... this is a tough one. I checked the Makefile and the source files and none of them reference arch/i386/kernel/msr.c I'm guessing that there's something wrong with the configuration of your system. What is the output of:
```

file /usr/src/linux

```

You might also want to try downloading the daily CVS again. The driver is still under development, so it's possible they already fixed an error you might've run into.

What seems strange to me is that your build output is completely different from mine. Might be that you have a different version of make, but please just check that you have the right driver and that you are following the directions closely.

Wish I could be more help.

---

### Post by sefs on 2007-04-22
Hi again, from that output I get...
/usr/src/linux: symbolic link to `/usr/src/linux-source-2.6.20'

Hope that makes some sense.

> **diepruis said:**
> What is the output of:
```

file /usr/src/linux

```

You might also want to try downloading the daily CVS again. The driver is still under development, so it's possible they already fixed an error you might've run into.

What seems strange to me is that your build output is completely different from mine. Might be that you have a different version of make, but please just check that you have the right driver and that you are following the directions closely.

Wish I could be more help.

---

### Post by diepruis on 2007-04-22
> **sefs said:**
> Hi again, from that output I get...
/usr/src/linux: symbolic link to `/usr/src/linux-source-2.6.20'

Hope that makes some sense.

Hmmm... that's odd. This may be different in Edgy, but on my system that symlink points to a linux-headers-* directory.

Could you please try the following?

```

sudo rm /usr/src/linux
sudo ln -s /usr/src/linux-headers-`uname -r` /usr/src/linux

```

Then change to the directory where you extracted the source and try the make install thing again.

If that doesn't work, please try downloading the source from the rt2x00 website again and try again.

---

### Post by sefs on 2007-04-22
Hi again .  I did that and got this...

```

make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[2]: *** No rule to make target `arch/i386/kernel/msr.c', needed by `arch/i386/kernel/msr.o'.  Stop.
make[1]: *** [arch/i386/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
rt73.ko failed to build!
make: *** [module] Error 1

```

I am on feisty btw.

Thanks.

---

### Post by sefs on 2007-04-22
Hi again...

and Feisty even acts more weird...

I can get the module compiled by issuing the command 

make

but if i use 

sudo make

it bombs with the error I described.

---

### Post by diepruis on 2007-04-23
> **sefs said:**
> Hi again...

and Feisty even acts more weird...

I can get the module compiled by issuing the command 

make

but if i use 

sudo make

it bombs with the error I described.

The reason for that is actually pretty good. You extracted the source to /usr/src (if you followed my instructions). Since users do not have write permission here, you have to use sudo make, as make needs those permissions to create the compiled machine code files.

I've been doing some research and looking at the driver source, and I'm really stumped as to your original problem. I suggest you drop in over at rt2x00.serialmonkey.com and look for the rt73 legacy driver forum. Post your problems there and someone with more knowledge of the source will try and help you. Please post a link to this HOWTO on that thread, and a link to the thread on this one.

---

### Post by dgel on 2007-04-23
Well twas fun while it lasted, but my network connection once again doesnt work and your solution suddenly doesn't work anymore :S it's weird really, this morning it worked, when i came back this afternoon it was broken.
Though it might be because i booted it up with a usb stick plugged in as well as my usb wifi adapter.
Tried to fix it with  new install of the drivers, using a static ip and even a full new install of feisty, but nothing worked.
All i get now when i try to connect to the wireless network are varying
"DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval X " messages after which it goes into sleep mode or something, i'm not sure what it is.
 I honestly don't have a clue and if you don't either i'm thinking about waiting for the next release of ubuntu again to get it working, such a shame because for a day or so it worked flawlessly.

---

### Post by Austin_KW on 2007-04-23
If it did not work after you reboot it might be a conflicting driver that was not blacklisted;
What is the output from "lsusb | grep rt"

One other thing, I have a race condition somewhere in the boot sequence. I am too lazy to find it, but unplugging and reinserting the usb dongle usually sorts it.

---

### Post by diepruis on 2007-04-23
> **Na-Fiann said:**
> Well twas fun while it lasted, but my network connection once again doesnt work and your solution suddenly doesn't work anymore :S it's weird really, this morning it worked, when i came back this afternoon it was broken.

I don't know what could cause that. All advice I can offer you is to reboot your router. I know it sounds silly, but sometimes it works.

---

### Post by joramdam on 2007-04-23
I am uncredible happy for the guide, it worked for me.
But how do i actiwate nomade modus. Will it detect other open networks  than my own ?

---

### Post by diepruis on 2007-04-24
> **joramdam said:**
> I am uncredible happy for the guide, it worked for me.
But how do i actiwate nomade modus. Will it detect other open networks  than my own ?

Sure, I'm happy to help :)

The device *should* pick up other open networks. I believe you can use a graphical tool (as long as it doesn't overwrite things or conflict in some other way) to scan for open networks. You can also use the terminal:

```

sudo iwlist rausb0 scan

```

As to "nomad modus", I've never heard of that. Do you mean "roaming mode"? Unfortunately I don't know much about that either, so you'll have to ask someone else ;)

---

### Post by joramdam on 2007-04-24
> **diepruis said:**
> Sure, I'm happy to help :)

The device *should* pick up other open networks. I believe you can use a graphical tool (as long as it doesn't overwrite things or conflict in some other way) to scan for open networks. You can also use the terminal:

```

sudo iwlist rausb0 scan

```

As to "nomad modus", I've never heard of that. Do you mean "roaming mode"? Unfortunately I don't know much about that either, so you'll have to ask someone else ;)

Well, nomade modus means exactly what you are telling me. So i  just have to search for a GUI. I like it a litle gprapical even if its linux :)

---

### Post by dannyboy79 on 2007-04-24
i can't even seem to get ndiswrapper to work with this. any suggestions? this is everywhere within dmesg

[17361823.436000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17361823.556000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17361823.616000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'


and then when I try to look at the syslog, it merely states the same thing and there is no log for ndiswrapper. any help would be appreciated as I thought I could at least get this working with ndiswrapper. i just bought because I am looking for a usb wireless adapter to plug into computers that I work on in my house. i do that on the side and this person I am trying to convert to linux. if I can't get wireless working I may have to try another distro which i don't want to do, ever since march of last yearm i've been ubuntu all the way!

i suppose I'll try this guide. i am trying to get his computer to use edgy xubuntu and the default rt73usb isn't working, i keep getting:

wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:17:3f:85:01:72
Sending on   LPF/wlan0/00:17:3f:85:01:72
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
 and it just sits there.

the belkin box has a little sticker on it that has version 3002 on it and dmesg shows me this when I plug it in:

 0000:01:0d.0: tulip_stop_rxtx() failed (CSR5 0xfc06c012 CSR6 0xff970111)
[17357688.792000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17357689.120000] usb 1-1: configuration #1 chosen from 1 choice
[17357689.756000] Loading module: rt73usb - CVS (N/A) by [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[17357690.016000] wmaster0: Selected rate control algorithm 'simple'
[17357690.100000] usbcore: registered new driver rt73usb
[17358098.272000] 0000:01:0d.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[17358098.272000] eth0: Setting full-duplex based on MII#1 link partner capability of c5e1.
[17358105.984000] eth0: no IPv6 routers present
[17358117.440000] wlan0: no IPv6 routers present
[17358180.252000] 0000:01:0d.0: tulip_stop_rxtx() failed (CSR5 0xfc06c012 CSR6 0xff970111)
[17359135.196000] wlan0: no IPv6 routers present
[17359253.536000] 0000:01:0d.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)

---

### Post by jetpig on 2007-04-25
this works with the WUA-1340 in feisty  thanks!

---

### Post by diepruis on 2007-04-25
> **dannyboy79 said:**
> i can't even seem to get ndiswrapper to work with this

You shouldn't use ndiswrapper when native drivers are available. They really are preferable. Besides, AFAIK ndiswrapper only bothers with support for cards that have no native drivers.

---

### Post by dannyboy79 on 2007-04-25
well I can see that for this computer I am currently working on but I sure wouldn't want to use a driver if I can't take advantage of my processor merely to get wireless to work. I'd rather figure out how to get ndiswrapper to work so I can utilize my cpu.

my question it, how do I determine which belkin version I have?? i typed in lsusb but it doesn't list any version?? the box has a sticker on the side labeled version 3002. i just just bought this adapter from tigerdirect.com so maybe there is even a new chipset?

---

### Post by Austin_KW on 2007-04-25
V3xxx should be rt73. Have you tried the rt73 driver? 
It works for me (for a v3000) on smp. Sometimes I have to re-insert the dongle on boot (don't know if this is a firmware load failure or what, & too lazy to debug it). But it works and I have seen no crashes, hangs or high cpu usage on a pentium-d with 6.10 generic kernel.

---

### Post by dannyboy79 on 2007-04-26
I assumed that's the driver I should use since edgy trys to use that module that was included from the install but as the originator of this thread stated, that one doesn't work. So I have not yet tried it but I will now. Thanks for you info. Is there any tips you can provide other than the guide?

---

### Post by Austin_KW on 2007-04-26
I notice the the WPA example in the first post now sets the encryption to AES, and not TKIP. I thought that AES was WPA2 not WPA. Anyhow the example for the howto should show what is most frequently available on routers/APs

---

### Post by babysteps on 2007-04-26
".....If you have such a system, you need to do the following:
[LIST=1]
[*] Install a non SMP kernel.
```

sudo aptitude install linux-386

```
[*] Reboot.
[*] While your PC is booting, you should see a prompt with something about GRUB. When this appears press ESC repeatedly.
[*] A list of kernels will come up, choose the one that contains 386.
[/LIST]....."

Its very good of you to post this How To.  I think I'm ready to give this one a shot, too, now, since I've been down rt2500, and rt2570 already (I know rt doesn't stand for route, for seems appropriate here) , only to find out that my Belkin's ID is 050d: 5070, a version 1000, and has either a Rt73 chip, or a Prism/ a GW3887 chip.
Since at this point I don't understand the freemac/softmac world, I will attempt the rt73 first.

Just one question first, if I'm running verion 2.6.12-9-386 does that mean I can just let it boot up naturally instead of trying to ESC between GRUB and Ubuntu?

Thanks!

Babysteps

---

### Post by diepruis on 2007-04-28
> **dannyboy79 said:**
> my question it, how do I determine which belkin version I have?? i typed in lsusb but it doesn't list any version?? the box has a sticker on the side labeled version 3002. i just just bought this adapter from tigerdirect.com so maybe there is even a new chipset?

lsusb should give you a hexadecimal number in the form XXXX:XXXX which uniquely identifies the chipset on the device. You can search the web for that number in order to identify it.

---

### Post by diepruis on 2007-04-28
> **Austin_KW said:**
> I notice the the WPA example in the first post now sets the encryption to AES, and not TKIP. I thought that AES was WPA2 not WPA. Anyhow the example for the howto should show what is most frequently available on routers/APs

What do you suggest? Should I just change the EncrypType line to TKIP with a note for users of AES? I know nothing about wireless security, so I'm completely dependent on your suggestion.

---

### Post by diepruis on 2007-04-28
> **babysteps said:**
> Just one question first, if I'm running verion 2.6.12-9-386 does that mean I can just let it boot up naturally instead of trying to ESC between GRUB and Ubuntu?

Yes, that should work. The instructions were only for edgy and feisty users, since those versions install kernels with SMP enabled by default. You're using an older version of Ubuntu (judging by the version of that kernel), so you shouldn't have any problems with this driver.

---

### Post by NoTiG on 2007-04-28
i installed and everything seemed to go correctly. i then manually did the iwconfig...


and at the part of the guide where it said the internet should start working.... i opened firefox... and there is no connection and additionally... the computer hard locks... i cannot even get to a terminal or out of gdm. i have to cut the power.

---

### Post by NoTiG on 2007-04-29
when i do /etc/init.d/networking restart i get this:

* Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.rausb0.pid with pid 5157
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/rausb0/00:17:3f:49:11:ff
Sending on   LPF/rausb0/00:17:3f:49:11:ff
Sending on   Socket/fallback
DHCPRELEASE on rausb0 to 192.168.1.1 port 67
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device rausb0 ; Network is down.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device rausb0 ; Network is down.
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
There is already a pid file /var/run/dhclient.rausb0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/rausb0/00:17:3f:49:11:ff
Sending on   LPF/rausb0/00:17:3f:49:11:ff
Sending on   Socket/fallback
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on rausb0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.104 -- renewal in 41970 seconds.
                                                                         [ OK ]

---

### Post by Austin_KW on 2007-04-29
That looks like it is working? You are getting a dhcp address from you AP.

---

### Post by NoTiG on 2007-04-29
well i just figured out the problem. i assumed that i was ok since i didn't have an SMP processor.

i was using the generic kernel.

i went back and installed the 386 kernel and now the stuff is working . Phew

---

### Post by NoTiG on 2007-04-29
can anyone be more specific as to what their /etc/network/interfaces file looks like? My wireless thing works but i have to type this in every time to get it to work:


  168  sudo ifconfig rausb0 up
  169  sudo iwconfig rausb0 essid linksys
  170  sudo iwconfig rausb0 key xxxxxxxxxx
  171  sudo dhclient rausb0

i tried adding the lines to my interfaces file but it didn't change anything. here is my current file:
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface rausb0 inet dhcp
wireless-essid linksys
wireless-key B034A29868

 auto rausb0
               
sudo iwconfig rausb0 essid linksys
sudo iwconfig rausb0 key XXXXXXXXXX
sudo dhclient rausb0

                                               


```

---

### Post by Austin_KW on 2007-04-29
You dont use sudo, you should use pre-up 
eg  "pre-up iwconfig rausb0 essid linksys"

You dont need to use dhclient to bring the interface up the "iface rausb0 inet dhcp" and "auto rausb0" will do this for you.
There are more example in the first post


And I assume that "wireless-key B034A29868" and "pre-up iwconfig rausb0 key XXXXXXXXXX" are the same key. or XXXX will be overwritten with B034A29868

---

### Post by NoTiG on 2007-04-29
ok here is my new interfaces and it still doesn't work ```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface rausb0 inet dhcp
wireless-essid linksys
wireless-key B034A29868













auto rausb0

pre-up iwconfig rausb0 essid linksys
pre-up iwconfig rausb0 key B034A29868
```

and yes i just broadcast my wireless key across the net. lol. time to change it i guess.

i still have to type 

  196  sudo ifconfig rausb0 up
  197  sudo iwconfig rausb0 essid linksys
  198  sudo iwconfig rausb0 key B034A29868
  199  sudo dhclient rausb0

before i can use the connection

---

### Post by Austin_KW on 2007-04-29
Some ralink drivers need to have the interface have come up at least once before it will accept some commands.
Try adding "pre-up ifconfig rausb0 up" before the "pre-up iwconfig" commands

---

### Post by NoTiG on 2007-04-29
nope... i tried it. still not working

---

### Post by Austin_KW on 2007-04-29
Rather than running the commands, try removing and re-inserting the usb dongle. I have an issue where it does not come up on some boots. Re-inserting usually fixes it. I dont know exactly what it is & I have been too lazy to debug it. 

Failing that add the commands to /etc/rc.local. This is for local configuration commands that are run at the end of the boot sequence. Just add the commands before the exit, you don't need sudo  as it is run in the root context.

---

### Post by diepruis on 2007-04-29
> **NoTiG said:**
> nope... i tried it. still not working

You need "auto rausb0 up" before the line "iface rausb0 inet dhcp". This line tells ifup to bring this interface up whenever the command "ifup -a" is executed. Since this is the command run at boot time to bring up all your networking interfaces, if you don't have that line you won't have any connectivity when you boot.

---

### Post by sefs on 2007-04-29
Whats the correct procedure to complete purge this driver and everything it installs on your system?

Thanks.

---

### Post by sefs on 2007-04-29
Are you saying that this dosnt work with the generic kernel in feisty?

> **NoTiG said:**
> well i just figured out the problem. i assumed that i was ok since i didn't have an SMP processor.

i was using the generic kernel.

i went back and installed the 386 kernel and now the stuff is working . Phew

---

### Post by diepruis on 2007-04-29
> **sefs said:**
> Whats the correct procedure to complete purge this driver and everything it installs on your system?

Thanks.

```

sudo ifconfig rausb0 down
sudo modprobe -r rt73
sudo rm /lib/modules/`uname -r`/extra/rt73.ko
sudo depmod -a

```

And then remove the line saying "alias ra0 rt73" from /etc/modprobe.conf

NOTE: This is what I'm guessing from the makefile. Use at your own risk.

---

### Post by diepruis on 2007-04-29
> **sefs said:**
> Are you saying that this dosnt work with the generic kernel in feisty?

It's not supposed to... but on some setups it does work. I don't have the faintest idea why this could be. It's probably some race condition in the driver that happens to be highly erratic.

At any rate, it's safer to just install the 386 kernel.

If you've tried this with the generic kernel and experienced lockups and such it might be a good idea to try the safer option. Please note that you'll have to recompile the driver and install it again in this case.

---

### Post by NoTiG on 2007-04-29
> **diepruis said:**
> You need "auto rausb0 up" before the line "iface rausb0 inet dhcp". This line tells ifup to bring this interface up whenever the command "ifup -a" is executed. Since this is the command run at boot time to bring up all your networking interfaces, if you don't have that line you won't have any connectivity when you boot.

thanks for the suggestion, i tried it but it still does not work. here is my interfaces now:

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto rausb0 up
iface rausb0 inet dhcp
wireless-essid linksys
wireless-key B034A29868













auto rausb0
pre-up ifconfig rausb0 up
pre-up iwconfig rausb0 essid linksys
pre-up iwconfig rausb0 key B034A29868
```

still doesn't work. should i just create some kind of script to run at boot up ? Any suggestions?

and btw... yes it appears that going from generic to 386 kernel stopped the lockups for me.

---

### Post by diepruis on 2007-04-30
> **NoTiG said:**
> still doesn't work. should i just create some kind of script to run at boot up ? Any suggestions?

and btw... yes it appears that going from generic to 386 kernel stopped the lockups for me.

That won't work for reasons I posted in the original howto. Have you tried setting up your /etc/network/interfaces like I posted in the howto? If you haven't please do, reboot and then post the file again if it doesn't work. And please note that the rausb0 section has to match my example nearly exactly, the only things you should change are the essid and WEP keys.

---

### Post by Fraser67 on 2007-05-02
Thanks for this HOW TO. I have been struggling for days to connect to the internet. I am new to Linux and Ubuntu and am using Xubuntu 7.04 since I have an old machine. I have tried various methods before this and finally followed this HOW TO exactly for DHCP with WPAPSK. However it still does not work until I try "sudo dhclient rausb0", this then returns an IP address for my Dell Latitude CPt laptop. Then I can get see the internet. How do I added this to my setup so it happens automatically?

Incidently, if I type "sudo ifup rausb0" it returns 
Invalid command : SSID=OscarBelkin54g
Failed to bring up rausb0

and the internet connection is broken. Again to reconnect I need to re-entre sudo dhclient rausb0.

Also what is the difference between an ESSID and a SSID. I am using the same identifier.

I am using a Belkin F5D7050 version 3000 usb 54g stick with an Belkin ADSL Modem with Wireless G Router F5D7632-4 version 2000uk.

Also after machine has booted and I have logged in I get a warning box saying "Could not look up internet address for home1. This will prevent Xfe from operating correctly. It may be possible to correct the problem by adding home1 to the file /etc/hosts on your system. Continue Anyway or Try Again." Any ideas what this is about?

---

### Post by Austin_KW on 2007-05-02
ESSID and SSID are the same thing. ESSIS is the SSID in infrastructure/managed mode (when you have an AP, router with an AP etc).

Looks like a typo in your /etc/network/interfaces, Post it

---

### Post by Austin_KW on 2007-05-02
Assuming that home1 is your hostname you should add an entry to the hosts file for a loopback address.
127.0.1.1   home1

---

### Post by Fraser67 on 2007-05-03
I will check this tonight. Does the loopback address have to match the IP address I will end up being allocated from my wirless router. Because they will be totally different? Thanks

---

### Post by Austin_KW on 2007-05-03
Your loopback address is always 127.0.0.1/8 (ie only the 127 matters, the rest can be any valid adddress)

---

### Post by dannyboy79 on 2007-05-03
> **Austin_KW said:**
> ESSID and SSID are the same thing. ESSIS is the SSID in infrastructure/managed mode (when you have an AP, router with an AP etc).

Looks like a typo in your /etc/network/interfaces, Post it

I though the E meant that it was an SSID for an **E**ncrypted Access Point. huh, are you saying that because you think that's the case or are you sure that's why. i'd like to know my sources before I pass on information to others.

---

### Post by diepruis on 2007-05-03
> **dannyboy79 said:**
> I though the E meant that it was an SSID for an **E**ncrypted Access Point. huh, are you saying that because you think that's the case or are you sure that's why. i'd like to know my sources before I pass on information to others.

According to [Wikipedia](http://en.wikipedia.org/wiki/ESSID), the E stands for "extended". ESSID is indeed used in secured networks. As far as I know, however, they work exactly the same from the viewpoint of the desktop user.

---

### Post by Austin_KW on 2007-05-03
the E is extended not encrypted
The SSID is the network name, the ESSID is the network name in the context of an infrastruct network.
Try "man iwconfig" and the wikipedia source given in above post.

edit: (actually strike that, the man page for iwconfig is a bit confused. iwconfig uses essid for ssid even when mode is adhoc, this is not technically correct)

---

### Post by dannyboy79 on 2007-05-03
> **Austin_KW said:**
> the E is extended not encrypted
The SSID is the network name, the ESSID is the network name in the context of an infrastruct network.
Try "man iwconfig" and the wikipedia source given in above post.

edit: (actually strike that, the man page for iwconfig is a bit confused. iwconfig uses essid for ssid even when mode is adhoc, this is not technically correct)

ok, thank you for clarifying this for me, now I know and as the Gi Joe cartoon always used to say, "Knowing is half the battle" i used to love Gi Joe and I still have some, Snake Eyes, Gung Ho, and some of the others from the 70's. sorry off topic, I always do that.

---

### Post by Fraser67 on 2007-05-03
Spot on. I put 127.0.1.1 home1 as loop back and this removed the error. Thanks again

---

### Post by Fraser67 on 2007-05-03
Thanks again. It was a typo. The price you pay for doing this late at night. I can now connect automatically to the net.

---

### Post by marinedalek on 2007-05-05
Hi, I'm using 7.04 Server with an F5D7050B and I followed this guide through. It seemed to work (seemed to connect to the router - signal at 63/100) but the DHCP discover wouldn't work so I tried giving it a static IP - that didn't seem to work, and when I rebooted the signal strength was 0/100. I can't ping the router (which I can on other wireless machines - it doesn't block the ping) and I have had this adapter working before on 6.10 Server, though I can't for the life of me remember how.
Is there anything you can think of that could cause this?

---

### Post by diepruis on 2007-05-05
> **marinedalek said:**
> Hi, I'm using 7.04 Server with an F5D7050B and I followed this guide through. It seemed to work (seemed to connect to the router - signal at 63/100) but the DHCP discover wouldn't work so I tried giving it a static IP - that didn't seem to work, and when I rebooted the signal strength was 0/100. I can't ping the router (which I can on other wireless machines - it doesn't block the ping) and I have had this adapter working before on 6.10 Server, though I can't for the life of me remember how.
Is there anything you can think of that could cause this?

Nothing specific. Usually when the DHCP Discover fails it's a problem with authentication - you might want to double check WEP keys and the like. I don't understand why the signal strength would drop suddenly, except if there is some configuration error in your startup scripts. I'd specifically check that only the rt73 module is being loaded for the card.

---

### Post by marinedalek on 2007-05-05
You were quite right, it was the authentication - I had to set the Access Point's WEP mode to "open" and then it worked fine - thanks!

---

### Post by retox on 2007-05-05
I have just installed Ubuntu 7.04 and it actually sees the r73 card and performs the site survey ok too but I cant validate my WEP key?? WHy is that?

---

### Post by port on 2007-05-05
I get to the iwconfig part of the HOW-TO and insert my card and my whole system freezes and forces me to restart, i already installed the 386 kernel and i am booting to that kernel. Also if i leave my card in while booting it freezes during boot also. I have belkin f57050b v5. I am able to use the card fine with ndiswrapper, any ideas why this isn't working properly ?

---

### Post by diepruis on 2007-05-06
> **marinedalek said:**
> You were quite right, it was the authentication - I had to set the Access Point's WEP mode to "open" and then it worked fine - thanks!

That's great, but you shouldn't run in open mode, anyone can then access your network and browse the Internet from it. I would recommend switching WEP back on and making sure you copied the key correctly to your interfaces file. Still, at least now we know that the card and the driver do work.

---

### Post by diepruis on 2007-05-06
> **retox said:**
> I have just installed Ubuntu 7.04 and it actually sees the r73 card and performs the site survey ok too but I cant validate my WEP key?? WHy is that?

I'm not understanding exactly. Did you follow this HOWTO, or not? The driver that comes with Ubuntu 7.04 by default can indeed scan for networks, but it can't authenticate. If you haven't yet, you should follow the instructions here to get your card working.

---

### Post by diepruis on 2007-05-06
> **port said:**
> I get to the iwconfig part of the HOW-TO and insert my card and my whole system freezes and forces me to restart, i already installed the 386 kernel and i am booting to that kernel. Also if i leave my card in while booting it freezes during boot also. I have belkin f57050b v5. I am able to use the card fine with ndiswrapper, any ideas why this isn't working properly ?

According to [the serialmonkey hardware page](http://rt2x00.serialmonkey.com/wiki/index.php/Hardware) the Belkin F5D7050 **Ver 3** uses an rt73 chip set. Are you sure that yours also uses that chip? Wireless card vendors usually switch around a lot between versions. It sounds like a very new card, since I can't find anything about it on google, so ndiswrapper might be your only hope.

Just for interest's sake, what is the output from ```
lsusb
``` Sometimes you can derive the chip set from that...

---

### Post by port on 2007-05-06
I actually have a bunch of these belkin cards. I went back to 2.6.20.15-generic kernel and plugged in another card and it was automatically detected and i was able to configure it. iwconfig shows it as eth1.  It works fine. The lsusb output of it is 

BUS 005 Device 003:  ID 050d:705c Belkin Components

The other card was 050d:705a, but even now if i even plug that card in it will freeze I am not sure why, so i cant use ndiswrapper with it either. I must have messed something up. Oh well the other card 705c works fine.

---

### Post by diepruis on 2007-05-06
> **port said:**
> The other card was 050d:705a, but even now if i even plug that card in it will freeze I am not sure why, so i cant use ndiswrapper with it either. I must have messed something up. Oh well the other card 705c works fine.

My guess is that you've got the wrong driver loaded for that card, but since you've got wireless working I won't pursue it any further ;)

---

### Post by babysteps on 2007-05-07
My uname -r gets me: 2.6.12-9-386. It seems that i'm the only one who's having this problem after I get to the "sudo make" stage: I get the error message of either 

make [1] : Makefile: No such file or directory
make [1] : *** No rule to make target 'Makefile'. Stop.

          OR 

I get, as with trying to install rt2570 earl ier, some message about not being able to find" gcc-3.4 .....sh  line 11" and line 12.  It doesn't like having gcc-4.0 and so i don't get a rt73.ko build.  If I build-essential, gcc-4.0 is installed. I don't know why it's always looking for 3.4 instead.

Any tips on how to get around this?  

I'm not sure exactly what drivers I should be using at this point anymore.  my lsusb gets me 

050d:7050 Belkin Component

Should i be using rt2570 or rt73?

I  opened the casing to my Belkin and found the chip on it says rt2571F.  It seems logical that I should use the rt2570 driver, but after so much difficulties, I'm no sure any more.  

Any help will be appreciated.

Babysteps

---

### Post by diepruis on 2007-05-07
> **babysteps said:**
> My uname -r gets me: 2.6.12-9-386. It seems that i'm the only one who's having this problem after I get to the "sudo make" stage: I get the error message of either 

make [1] : Makefile: No such file or directory
make [1] : *** No rule to make target 'Makefile'. Stop.

That's usually because you're not in the "Module" directory. Make doubly sure that there is a file named "Makefile" in the directory where you type "make". Also, make sure you type "sudo make" with no other arguments.

Your kernel also seems a little on the old side. I've never tried to compile this driver on a kernel that old. None of the documentation states any dependency on a newer kernel, but you never know.

If you absolutely cannot get this driver to work, check the wiki. It has instructions on an older driver that no longer works with the newer kernels, but might work with yours.

> **babysteps said:**
> I get, as with trying to install rt2570 earl ier, some message about not being able to find" gcc-3.4 .....sh  line 11" and line 12.  It doesn't like having gcc-4.0 and so i don't get a rt73.ko build.  If I build-essential, gcc-4.0 is installed. I don't know why it's always looking for 3.4 instead.

Any tips on how to get around this?  

You might try the following:

```

sudo aptitude install gcc-3.4

```

Then try again. Not sure if that will work, but it might to the trick.

> **babysteps said:**
> 
I'm not sure exactly what drivers I should be using at this point anymore.  my lsusb gets me 

050d:7050 Belkin Component

Should i be using rt2570 or rt73?

I  opened the casing to my Belkin and found the chip on it says rt2571F.  It seems logical that I should use the rt2570 driver, but after so much difficulties, I'm no sure any more.  

Any help will be appreciated.

Babysteps

From the version number on the chip, I would infer that rt71 is the right driver. I think it's rather a problem with your build system than with this being the wrong driver, let's try and sort that out first.

---

### Post by babysteps on 2007-05-08
[QUOTE=diepruis;2609893]That's usually because you're not in the "Module" directory. Make doubly sure that there is a file named "Makefile" in the directory where you type "make". Also, make sure you type "sudo make" with no other arguments...."

A little aid I picked up from a phrase book is to use: ls -l  to see what's in a directory.  I used it, and did see the "Makefile".  I subsequently got a different error about not being able to find "modules".  Both times when I looked there were "Makefile" and "modules" but they were blue in color, while the others were just plain white text on black.  Does that mean something?  I notice that the tar.gz files are usually light green in color.


"...Your kernel also seems a little on the old side. I've never tried to compile this driver on a kernel that old. None of the documentation states any dependency on a newer kernel, but you never know...."

  I don't know if there are anyone out there using what i'm using (breezy linux 2.6.12-9-386) and have similar situations for using what I'm using, but I got the book + CD written by Keir Thomas: Beginning Ubuntu Linux.  I got the 1st edition because it came with a CD rom instead of a DVD rom. The newer version was available, but I wasn't sure my older computer could read the DVD rom.  That's the reason for the older version.  The inability to upgrade after that is of course, due to the fact that it couldn't get online, sort of a catch 22 situation. 



"...If you absolutely cannot get this driver to work, check the wiki. It has instructions on an older driver that no longer works with the newer kernels, but might work with yours..." 

I tried to go to Ralink's site for the drivers, but it's not available.  Some of the links from sites such as Arch Linux have links that are also no longer available.  I'm also frustrated about how SerialMonkey's site doesn't really give me info as to exactly WHICH driver to download. With all the work they apparently have put into the projects, it's too bad it's a bit beyond the uninitiated to take advantage of.   For example, your title says " RT73 (RT71) serialmonkey drivers", which I would not have thought would be for my USB because I've been looking for something along the line of rt2500.  Then when i finally opened the USB dongle, and saw RT2571F, my thought is that I should be using the rt2570 driver.  The result is that I've been exercising and learning a lot by starting with the ndiswrapper with the rt2500usb.inf file from window's installation CD, then to the serial monkey's rt2570, and now finally the rt73. Each is a different process. My head is spinning from it all...



"...You might try the following:

```

sudo aptitude install gcc-3.4

```

Then try again. Not sure if that will work, but it might to the trick...."

I tried that, but I don't have gcc-3.4 available, only gcc-4.0, gcc-4.0-base, and gcc, and gcc-3.3-base that came with the installation CD.  When I look online with my other laptop to get the gcc-3.4 package, I can never get a complete one.  It gets really confusing.  Even when I go separately to download what the errors complains about missing, I cannot get the exact .x.x.x numbers to satisfy the requirement. 



"....From the version number on the chip, I would infer that rt71 is the right driver. I think it's rather a problem with your build system than with this being the wrong driver, let's try and sort that out first...."

I will try again.

Thanks for your help.

Babysteps

---

### Post by dannyboy79 on 2007-05-08
> **babysteps said:**
> [QUOTE=diepruis;2609893]That's usually because you're not in the "Module" directory. Make doubly sure that there is a file named "Makefile" in the directory where you type "make". Also, make sure you type "sudo make" with no other arguments...."

A little aid I picked up from a phrase book is to use: ls -l  to see what's in a directory.  I used it, and did see the "Makefile".  I subsequently got a different error about not being able to find "modules".  Both times when I looked there were "Makefile" and "modules" but they were blue in color, while the others were just plain white text on black.  Does that mean something?  I notice that the tar.gz files are usually light green in color.


"...Your kernel also seems a little on the old side. I've never tried to compile this driver on a kernel that old. None of the documentation states any dependency on a newer kernel, but you never know...."

  I don't know if there are anyone out there using what i'm using (breezy linux 2.6.12-9-386) and have similar situations for using what I'm using, but I got the book + CD written by Keir Thomas: Beginning Ubuntu Linux.  I got the 1st edition because it came with a CD rom instead of a DVD rom. The newer version was available, but I wasn't sure my older computer could read the DVD rom.  That's the reason for the older version.  The inability to upgrade after that is of course, due to the fact that it couldn't get online, sort of a catch 22 situation. 



"...If you absolutely cannot get this driver to work, check the wiki. It has instructions on an older driver that no longer works with the newer kernels, but might work with yours..." 

I tried to go to Ralink's site for the drivers, but it's not available.  Some of the links from sites such as Arch Linux have links that are also no longer available.  I'm also frustrated about how SerialMonkey's site doesn't really give me info as to exactly WHICH driver to download. With all the work they apparently have put into the projects, it's too bad it's a bit beyond the uninitiated to take advantage of.   For example, your title says " RT73 (RT71) serialmonkey drivers", which I would not have thought would be for my USB because I've been looking for something along the line of rt2500.  Then when i finally opened the USB dongle, and saw RT2571F, my thought is that I should be using the rt2570 driver.  The result is that I've been exercising and learning a lot by starting with the ndiswrapper with the rt2500usb.inf file from window's installation CD, then to the serial monkey's rt2570, and now finally the rt73. Each is a different process. My head is spinning from it all...



"...You might try the following:

```

sudo aptitude install gcc-3.4

```

Then try again. Not sure if that will work, but it might to the trick...."

I tried that, but I don't have gcc-3.4 available, only gcc-4.0, gcc-4.0-base, and gcc, and gcc-3.3-base that came with the installation CD.  When I look online with my other laptop to get the gcc-3.4 package, I can never get a complete one.  It gets really confusing.  Even when I go separately to download what the errors complains about missing, I cannot get the exact .x.x.x numbers to satisfy the requirement. 



"....From the version number on the chip, I would infer that rt71 is the right driver. I think it's rather a problem with your build system than with this being the wrong driver, let's try and sort that out first...."

I will try again.

Thanks for your help.

Babysteps


sounds to me like you need to get dapper, edgy, or even fiesty as you're still using breezy which is way outdated now. you're "old" hardware will be fine on feisty. I just installed xubuntu feisty on my Hitachi 266mhz MMX which only has 128mb ram, 4mb video ram, and a 24X CDROM, the pcmcia NETGEAR WG511T (AR5212 is the pci chipset) I am pretty sure. 

My point is that you didn't need to get breezy due to your hardware being old. this would stop some of the errors you're getting due to dependencies which aren't available for breezy.

---

### Post by ex625 on 2007-05-09
diepruis - another kudos to you - this got my ubuntu system up and running finally (linksys wusb54gc on a dell dimension). thanks for helping everyone out.   

-ed

btw, why remove networkmanager? and is there a preferred replacement (e.g. something that shows connection status/strength in the toolbar)

---

### Post by diepruis on 2007-05-09
> **babysteps said:**
> A little aid I picked up from a phrase book is to use: ls -l  to see what's in a directory.  I used it, and did see the "Makefile".  I subsequently got a different error about not being able to find "modules".  Both times when I looked there were "Makefile" and "modules" but they were blue in color, while the others were just plain white text on black.  Does that mean something?  I notice that the tar.gz files are usually light green in color.

Yes the colours do mean something. I *think* the light green indicates archives, while blue indicates directories. The Makefile is definitely not supposed to be blue. I'm not entirely sure what that indicates though. Perhaps something is corrupted somehow, and you need to re download and try again - still, that won't solve your gcc problems.

The "modules" error is my fault, sorry, the directory's name should be "Module".

> **babysteps said:**
> I don't know if there are anyone out there using what i'm using (breezy linux 2.6.12-9-386) and have similar situations for using what I'm using, but I got the book + CD written by Keir Thomas: Beginning Ubuntu Linux.  I got the 1st edition because it came with a CD rom instead of a DVD rom. The newer version was available, but I wasn't sure my older computer could read the DVD rom.  That's the reason for the older version.  The inability to upgrade after that is of course, due to the fact that it couldn't get online, sort of a catch 22 situation.

You can upgrade from the any CD of the version after your current one. You can also do a fresh install of Feisty. If you can't get on line, check to see if your LoCo team could provide you with a CD. That said, I'm not sure that upgrading will solve your problem.

> **babysteps said:**
> I tried to go to Ralink's site for the drivers, but it's not available.  Some of the links from sites such as Arch Linux have links that are also no longer available.  I'm also frustrated about how SerialMonkey's site doesn't really give me info as to exactly WHICH driver to download. With all the work they apparently have put into the projects, it's too bad it's a bit beyond the uninitiated to take advantage of.   For example, your title says " RT73 (RT71) serialmonkey drivers", which I would not have thought would be for my USB because I've been looking for something along the line of rt2500.  Then when i finally opened the USB dongle, and saw RT2571F, my thought is that I should be using the rt2570 driver.  The result is that I've been exercising and learning a lot by starting with the ndiswrapper with the rt2500usb.inf file from window's installation CD, then to the serial monkey's rt2570, and now finally the rt73. Each is a different process. My head is spinning from it all...

It's incredibly frustrating, I know. I struggled for about a week to get my rt61 card to work because I was barking up all sorts of wrong trees. If you keep at it, it'll work eventually.

> **babysteps said:**
> I tried that, but I don't have gcc-3.4 available, only gcc-4.0, gcc-4.0-base, and gcc, and gcc-3.3-base that came with the installation CD.  When I look online with my other laptop to get the gcc-3.4 package, I can never get a complete one.  It gets really confusing.  Even when I go separately to download what the errors complains about missing, I cannot get the exact .x.x.x numbers to satisfy the requirement.

I have a feeling this might be because of your old version of Ubuntu, since mine (Feisty) has gcc-3.4 available. You might need to upgrade just to get this package.


I'm sorry I can't be more help, but I never even had Breezy installed, nor did I try to run this driver on it. I'm tempted to agree with dannyboy and tell you to upgrade to a newer version of Ubuntu, but like I said, I don't know *for sure* that that'll work - still it's something to try.

---

### Post by diepruis on 2007-05-09
> **ex625 said:**
> diepruis - another kudos to you - this got my ubuntu system up and running finally (linksys wusb54gc on a dell dimension). thanks for helping everyone out.   

-ed


It really is my pleasure :)

> **ex625 said:**
> btw, why remove networkmanager? and is there a preferred replacement (e.g. something that shows connection status/strength in the toolbar)

I stated why that should be removed in the original HOWTO, check the second footnote.

Unfortunately, there is no replacement, as far as I know. If you want to check those variables you can always run "iwconfig rausb0" from a console. Not ideal, but it's better than nothing.

---

### Post by marinedalek on 2007-05-12
> **diepruis said:**
> That's great, but you shouldn't run in open mode, anyone can then access your network and browse the Internet from it. I would recommend switching WEP back on and making sure you copied the key correctly to your interfaces file. Still, at least now we know that the card and the driver do work.

Ah no, you misunderstand. WEP is still on, but the authentication type is set to "Open" - this protects against a text attack that exploits the "shared" option, in fact Cisco Systems state that the "Open" mode of WEP is more secure: [http://www.cisco.com/warp/public/779/smbiz/prodconfig/help/eag/air/ap3xx/SetWEP_Keys.shm.htm](http://www.cisco.com/warp/public/779/smbiz/prodconfig/help/eag/air/ap3xx/SetWEP_Keys.shm.htm)

---

### Post by diepruis on 2007-05-13
> **marinedalek said:**
> Ah no, you misunderstand. WEP is still on, but the authentication type is set to "Open" - this protects against a text attack that exploits the "shared" option, in fact Cisco Systems state that the "Open" mode of WEP is more secure: [http://www.cisco.com/warp/public/779/smbiz/prodconfig/help/eag/air/ap3xx/SetWEP_Keys.shm.htm](http://www.cisco.com/warp/public/779/smbiz/prodconfig/help/eag/air/ap3xx/SetWEP_Keys.shm.htm)

Mmmmm.... interesting, I didn't know that. Thanks for the link ;)

---

### Post by microsoft92sucks on 2007-05-17
I used this how to to get my belkin wireless addepter to work on Ubuntu and it work great thank u for the very good how to but now im checking out Kubuntu and im having trouble on step 10 i cant get it to cofig write how do i do this on Kubuntu please help

---

### Post by diepruis on 2007-05-17
> **microsoft92sucks said:**
> I used this how to to get my belkin wireless addepter to work on Ubuntu and it work great thank u for the very good how to but now im checking out Kubuntu and im having trouble on step 10 i cant get it to cofig write how do i do this on Kubuntu please help

I'm not sure I understand. What are you trying to do? What commands did you type? What error messages did you receive? What is going wrong?

---

### Post by epee on 2007-05-17
> **diepruis said:**
> If you want to check those variables you can always run "iwconfig rausb0" from a console.Note - the driver as of now uses device names 'wlan0' etc...

---

### Post by microsoft92sucks on 2007-05-17
> **diepruis said:**
> I'm not sure I understand. What are you trying to do? What commands did you type? What error messages did you receive? What is going wrong?

Well when i did it in Ubuntu I used a network tool not the terminal and I dont know how to do this stuff throw the terminal very good. If i put in iwconfig i get
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"home wireless"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 10:17:3F:44:FA:AA
          Bit Rate=11 Mb/s
          Link Quality=100/100  Signal level=44/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

You can see that its getting a signal i just dont know how to set it to use that signal.

 and u can see here it cant find the device when i name it rausb0 
justin@EggHead:~$ sudo ifconfig rausb0
rausb0: error fetching interface information: Device not found
justin@EggHead:~$ sudo ifconfig rausb0 down
rausb0: ERROR while getting interface flags: No such device
justin@EggHead:~$ sudo iwconfig rausb0
rausb0    No such device

what is the devices name. Please help srry for very little info on last post (i was very tired) And thank for any help u can give me.

---

### Post by diepruis on 2007-05-17
> **microsoft92sucks said:**
> what is the devices name. Please help srry for very little info on last post (i was very tired) And thank for any help u can give me.

This seems to tie in with epee's post. I'll have to investigate further... In the meantime, just replace all the instances of rausb0 with eth1 and it should work for you.

---

### Post by epee on 2007-05-17
> **diepruis said:**
> This seems to tie in with epee's post. I'll have to investigate further... 
See [here]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3800&highlight=wlan0") for info.

---

### Post by diepruis on 2007-05-17
> **epee said:**
> See [here]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3800&highlight=wlan0") for info.

Thanks for the link, I had searched for this earlier but didn't have a lot of time. I'll update the HOWTO.

This doesn't explain why microsoft92sucks's device was being shown as eth1, however. That's not important, though. As long as it works, right?

---

### Post by microsoft92sucks on 2007-05-17
> **diepruis said:**
> This seems to tie in with epee's post. I'll have to investigate further... In the meantime, just replace all the instances of rausb0 with eth1 and it should work for you.

thx man i hope that works i think it will. im in school right now so ill see if it works when i get home

---

### Post by barksten on 2007-05-17
Thank you!
Got it up and running thanks to your work. I had to sacrifice WPA but what the hell.. WEP have worked before we had WPA :)

---

### Post by diepruis on 2007-05-17
> **barksten said:**
> Thank you!
Got it up and running thanks to your work. I had to sacrifice WPA but what the hell.. WEP have worked before we had WPA :)

It truly is a pleasure.

WPA **should** work with this module, though, but if you're fine with WEP it should protect you reasonably well enough.

---

### Post by lowebb on 2007-05-17
Guys, this seems to be the place to post issues with the rt73 driver. 

I installed it yesterday with minimal hassle but it seems now my dwl-g122 needs to be removed and re-inserted every time I boot my computer to get the wlan going. Only then does the computer recognize it. 

In dmesg I get get the error "rt73: probe of 3-3:1.0 failed with error -71"

Its trying to load the usb device at startup but failing

When installing it I went through few iterations due to the recent update in the rt73 install process, so I'm thinking I have redundancies within its setup.

If anyone can shed light on this I would be most appreicative

thanks

---

### Post by microsoft92sucks on 2007-05-17
thanks agian diepruis I now have the driver working on Ubuntu and Kubuntu im still not sure what one i like the most they both have there strong and week points. But i now can see more of Kubuntus point with Inernet thanks man

---

### Post by gorka on 2007-05-17
It works!!!
Thank you very very much!!!
I did not have a problem following your commands.

Many many Thanks

---

### Post by diepruis on 2007-05-18
> **microsoft92sucks said:**
> thanks agian diepruis I now have the driver working on Ubuntu and Kubuntu im still not sure what one i like the most they both have there strong and week points. But i now can see more of Kubuntus point with Inernet thanks man

It's a pleasure. I had some difficulty deciding as well and I tend to switch between the two every few months or so, but I use Kubuntu most of the time :)

---

### Post by diepruis on 2007-05-18
> **gorka said:**
> It works!!!
Thank you very very much!!!
I did not have a problem following your commands.

Many many Thanks

Sure thing. Glad it worked so well for you :)

---

### Post by diepruis on 2007-05-18
> **lowebb said:**
> Guys, this seems to be the place to post issues with the rt73 driver. 

I installed it yesterday with minimal hassle but it seems now my dwl-g122 needs to be removed and re-inserted every time I boot my computer to get the wlan going. Only then does the computer recognize it. 

In dmesg I get get the error "rt73: probe of 3-3:1.0 failed with error -71"

Its trying to load the usb device at startup but failing

When installing it I went through few iterations due to the recent update in the rt73 install process, so I'm thinking I have redundancies within its setup.

If anyone can shed light on this I would be most appreicative

thanks

That's a little out of my depth, unfortunately. If I had to venture a guess I would say that it's trying to load the thing at the wrong stage of the boot process. Check which modules are being loaded as well. Other than that I'm really stumped. You can always head over to the [serialmonkey website](rt2x00.serialmonkey.com) and ask on their forums.

---

### Post by joramdam on 2007-05-20
I cant install the modules ??

joramdam@dreamer:/usr/src/rt73-cvs-2007051917/Module$ sudo make install
Password:
*** Install module in /lib/modules/2.6.20-15-386/extra ...
make -C /lib/modules/2.6.20-15-386/build SUBDIRS=/usr/src/rt73-cvs-2007051917/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-386'
  INSTALL /usr/src/rt73-cvs-2007051917/Module/rt73.ko
  DEPMOD  2.6.20-15-386
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-386'
/sbin/depmod -a
*** Update /etc/modprobe.conf alias for wlan*
*** Install firmware in /lib/firmware ...
*** Check config ...

---

### Post by joramdam on 2007-05-20
And  this


joramdam@dreamer:/usr/src/rt73-cvs-2007051917/Module$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-386'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-386'
!!! WARNING: Module file much too big (>1MB)
!!! Check your GCC settings or ask for support
*** Module rt73.ko built successfully
joramdam@dreamer:/usr/src/rt73-cvs-2007051917/Module$

---

### Post by dannyboy79 on 2007-05-21
hi there, I know this is off topic but it deals with the  exact same thing. Compiling a wireless driver from source. It's for the at76c503a driver provided from berlios ( [http://at76c503a.berlios.de/support.html#get](http://at76c503a.berlios.de/support.html#get) )because the fiesty version is NOT working just like the fiesty version of the RT73 driver doesn't work. 

I don't even need this driver, I am only trying to help out another user. i was going to build a deb using checkinstall and then host it on my ftp site for him and other's if they want it. Anyway, I first got a bunch of errors when I tried to compile it using the generic kernel and unforunately I didn't write them down (this is another thing, I tried checking out ~/.bash_history and even root's history but I couldn't find the errors, what do I have to do to .bash_profile or whatever file so that it logs everything not just hte input but output as well). FYI, I am doing this thru ssh from work, he he he. So when I installed the 386 kernel, and issued sudo shutdown -r now, then made sure with uname -r that I booted with the -386 kernel instead of the -generic kernel, I downloaded the source from berlios AGAIN, into a folder within /usr/local/src/ and when I issue the make command, I get this error:

/usr/local/src/at76_usb-0.14beta1# make
Makefile:24: *** Kernel in /lib/modules/2.6.20-15-386/build is not configured.  Stop.

So what does this mean? I checked out /lib/modules/2.6.20-15-386/ and there is no folder/file called build? Do I need to create a symlink  pointing to the kernel? There does appear to be a symlink within /lib/modules/2.6.20-15-generic/ called build that points to /usr/src/linux-headers-2.6.20-15-generic. I have never compiled from source and when I have, it just did it with no errors so any help would be much appreciated. If I should start a new thread I will. I am not trying to hijack, just trying to get help and if I just started a new thread to begin with, I doubt you would see it and realize that you could potentially help due to the similar nature of the situations with the drivers. Thank yiou if you can help.

---

### Post by barksten on 2007-05-21
> **barksten said:**
> Thank you!
Got it up and running thanks to your work. I had to sacrifice WPA but what the hell.. WEP have worked before we had WPA :)

Actually I have the interface up but not automagically. I'm not sure the if-upscripts are running. How do I tell??

---

### Post by Austin_KW on 2007-05-21
> /usr/local/src/at76_usb-0.14beta1# make
Makefile:24: *** Kernel in /lib/modules/2.6.20-15-386/build is not configured. Stop.
Often building from source needs a "./configure"  or something similar in the build directory

---

### Post by diepruis on 2007-05-21
> **dannyboy79 said:**
> So what does this mean? I checked out /lib/modules/2.6.20-15-386/ and there is no folder/file called build? Do I need to create a symlink  pointing to the kernel?

I think so, yes.

But in all honesty, I don't think these drivers are similiar enough to be discussed under one thread. You'd be better served by making a new thread and perhaps PMing me a link.

---

### Post by diepruis on 2007-05-21
> **barksten said:**
> Actually I have the interface up but not automagically. I'm not sure the if-upscripts are running. How do I tell??

I'm not sure if there's is a way to tell...

You could try running ifup -a. If that works then it's a fair bet that it's configured correctly, but that ifup isn't running. If ifup <interface name> works, then you should add the "auto" bit to the config file. If neither of those work, then you probably need to look at /etc/network/interfaces again.

---

### Post by diepruis on 2007-05-21
> **joramdam said:**
> I cant install the modules ??

joramdam@dreamer:/usr/src/rt73-cvs-2007051917/Module$ sudo make install
Password:
*** Install module in /lib/modules/2.6.20-15-386/extra ...
make -C /lib/modules/2.6.20-15-386/build SUBDIRS=/usr/src/rt73-cvs-2007051917/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-386'
  INSTALL /usr/src/rt73-cvs-2007051917/Module/rt73.ko
  DEPMOD  2.6.20-15-386
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-386'
/sbin/depmod -a
*** Update /etc/modprobe.conf alias for wlan*
*** Install firmware in /lib/firmware ...
*** Check config ...

That looks fine, actually. What happens when you try ```
sudo modprobe rt73
```?

---

### Post by dannyboy79 on 2007-05-21
> **Austin_KW said:**
> Often building from source needs a "./configure"  or something similar in the build directory

there is no configure script with the berlios source files for this driver but thanks anyway. I am guessing I just need to add the symlink just like the -generic kernel has one under /lib/modules/2.6.20-15-generic/build. so I'll try that. thanks for the responses though.

to the author of the thread, I wasn't trying to say that these drivers are the same, I was merely pointing out the fiesty comes with both the RT71 (RT73) drivers as well as the at76c503a driver (which is for Atmel AT76c503/AT76c505/AT76c505a based WLAN (802.11b) usb adapter) but they both DON'T work so you have to compile new ones from source.

---

### Post by Austin_KW on 2007-05-21
> **diepruis said:**
> I'm not sure if there's is a way to tell...

You could try running ifup -a. If that works then it's a fair bet that it's configured correctly, but that ifup isn't running. If ifup <interface name> works, then you should add the "auto" bit to the config file. If neither of those work, then you probably need to look at /etc/network/interfaces again.

I have noticed that when your remove the dongle in feisty, the ifdown is not called. /var/run/network/ifstate still reflects the state as configured, so when you re-insert the usb dongle it does not come up. You may need to manually run 'ifdown rausb0' or 'ifdown wlan0' & then re-insert the dongle.

---

### Post by Austin_KW on 2007-05-21
Did anyone have the rt73 driver come up as wlan1. It happened when I was testing 64 bit feisty. I don't know why, as iftab was set to wlan0 for the MAC addr, and I could not find anything else reserving wlan0. It was also a pain trying to get the rt73 to work on boot in 64 bit on a pentium D. It worked well once the network came up but often took 2/3 'ifdown wlan1' remove & re-insert dongle.
 
I have now gone back to feisty 32 bit (generic) and it seems much better behaved, but I am curious if anyone else if seeing wlan1 in place of wlan0.

---

### Post by diepruis on 2007-05-21
> **Austin_KW said:**
> Did anyone have the rt73 driver come up as wlan1. It happened when I was testing 64 bit feisty. I don't know why, as iftab was set to wlan0 for the MAC addr, and I could not find anything else reserving wlan0. It was also a pain trying to get the rt73 to work on boot in 64 bit on a pentium D. It worked well once the network came up but often took 2/3 'ifdown wlan1' remove & re-insert dongle.
 
I have now gone back to feisty 32 bit (generic) and it seems much better behaved, but I am curious if anyone else if seeing wlan1 in place of wlan0.

One time I installed this on a 32 bit Beta of Feisty. After a few false starts and the like, I finally got the device to play along. It came up as rausb0, but after a bit of fiddling it inexplicably changed to rausb1. I still have no idea why and like you, I couldn't find anything reserving the previous name. I checked /etc/modprobe.conf and modprobe.d as well.

---

### Post by joramdam on 2007-05-21
> **diepruis said:**
> That looks fine, actually. What happens when you try ```
sudo modprobe rt73
```?

I am sorry for my late respons when i ask for help... It works fine, i was experimenting with a belkin F5D8010 pre N as well at the same time. So i had both wlan0 and wlan1. Bye the way i got the Belkin PCMCIA MIMO  Airgo Networks Inc AGN100 card working, and i can see that it is many who have had trouble with that. So i am wery happy :-)  Thanks for the help !!!!!!!!!!

---

### Post by diepruis on 2007-05-21
> **joramdam said:**
> I am sorry for my late respons when i ask for help... It works fine, i was experimenting with a belkin F5D8010 pre N as well at the same time. So i had both wlan0 and wlan1. Bye the way i got the Belkin PCMCIA MIMO  Airgo Networks Inc AGN100 card working, and i can see that it is many who have had trouble with that. So i am wery happy :-)  Thanks for the help !!!!!!!!!!

No problem, you're welcome.

---

### Post by scorptig on 2007-05-23
Tried it with no luck, I have Linksys WUSB54GC
I will try to document my problems.
Removing network-applet did not help.
Latest CVS RT-73 didn't help

So Again I'll be back on this topic, next time I install I have to remember to back up before I create changes.

---

### Post by Alex74447 on 2007-05-27
Worked perfectly for the D-Link WUA-1340.

Note for future users, maybe you should include this in the original post:

If you can't access the internet to aptitude build-essential, simply insert the Feisty disc, go to the area where you add the repositories, hit add CD, and add everything. Then reload repositories and mark Build-essential for installation and continue with the instructions.

---

### Post by TotallyConfused on 2007-05-27
You are a lifesaver! I FINALLY got my rt73 Edimax USB dongle to work! I am writing this using the wireless now. I hope it stays this way though.

Can I ask if it's safe to apply the updates that Adept Updater has (I'm using Kubuntu 7.04)? Will it screw up my hard work if I update stuff?

---

### Post by Austin_KW on 2007-05-28
> **TotallyConfused said:**
> You are a lifesaver! I FINALLY got my rt73 Edimax USB dongle to work! I am writing this using the wireless now. I hope it stays this way though.

Can I ask if it's safe to apply the updates that Adept Updater has (I'm using Kubuntu 7.04)? Will it screw up my hard work if I update stuff?

There is a new kernel (linux-image) so you have to rebuild and install the driver under the new kernel /lib/modules. You have to do this for kernel updates.

go to the modules directory
make clean
make 
sudo make install

---

### Post by TotallyConfused on 2007-05-28
Hi Austin,

I'm newbie to Linux so I'll like a little clarification to your reply. When you say modules directory, do you mean that it's the /module/ directory under the directory where the driver was unzipped according to the instructions in this how-to and then run the commands that you recommended?

---

### Post by durfff on 2007-05-28
Hey all

I'm new to ubuntu and I've been trying to get a connection to the net for the last 3 days and this is now hurting my brain...

I have a D-LINK G122 rev C1, and I've folloed this (brilliant) how-to to the letter to get the dongle working but no success. Well, kind of...

I'm using Edgy Eft (graphics card reason - the good ol' Radeon 9200SE). I've followed the step-by-step and I've now done that 3 times on new installs of edgy, to no avail. 

The closest I can get to a connection is in the part of the how-to that mentions "now you should be connected", I am indeed connected and achieving far better speeds than in windows (probably due to the signal being around 89% compared to 24% in XP), but it only lasts for about 5 minutes... After that the connection is lost and nothing can bring it back up... I've tried rebooting, removing then reinserting the dongle, booting with, without, ifdown-ifup, nothing works. 

Now you're probably going to laugh at me, but I've noticed the only thing I haven't done is changing the kernel... At the moment it's using the generic kernel, thing is, I have no idea how to change it... I've tried sudo aptitude linux-386, but that outputs no package installed, no package removed... How do I install the 386 kernel??? Bearing in mind at the moment when booting in ubuntu I have absolutely no internet connection (you could probably use ethernet I hear you say, well, I could, but that would mean using about 40m of ethernet cable and I don't have that cable nor the money to get it...).

I really want to get it to work to explore the world of ubuntu properly (and to properly install the rest of my hardware without having to reboot between XP and buntu all the time!)

I can post outputs from various commands if you need me to, let me know.

Thanks for any help!!!

---

### Post by Austin_KW on 2007-05-28
> **TotallyConfused said:**
> Hi Austin,

I'm newbie to Linux so I'll like a little clarification to your reply. When you say modules directory, do you mean that it's the /module/ directory under the directory where the driver was unzipped according to the instructions in this how-to and then run the commands that you recommended?

Yes, You need to go back to rt73-cvs-yyyymmddhh/Module directory, and do the "sudo make" and "sudo make install" again.
You will need to do this every time you boot a newly installed  kernel

---

### Post by Austin_KW on 2007-05-28
durfff,
If you a loosing the connection after 5 mins ensure that you have blacklisted all conflicting drivers.
check the output of "lsmod | grep rt" and "lsmod | grep usbcore" to see what ralink drivers are loaded or using the usb.

What HW are you running on, is it dual core, 64 bit

---

### Post by durfff on 2007-05-28
Hey Austin, cheers for the quick reply

All conflicting drivers have been blacklisted (follownig the how-to at the beginning of the thread, and double-checked the blacklist file and they're all there). 

For the output of "lsmod | grep rt" and "lsmod | grep usbcore" I don't think there's anything wrong, lsmod | grep rt only shows rt73 and a few other drivers with "rt" in the name (I doubt they have anything to do with that) and grep usbcore shows rt73... No mention of any blacklisted driver there. I could post the output here but it might take a while (cut long story short: the only hard drive that will share files between windows is Mac-formatted cos I had a mac that got stolen therefore read-and-write in windows with MacDrive but read-only in Ubuntu... So can't copy files over :() If you do want the output I'm sure I'll find a way to resize the main partition on this external and post here. Let me know, but then again I don't see anything fishy...

My comp is an AMD 2600 XP+ on MSI KM4M-L mobo, 512MB RAM and system is installed as dual-boot with XP on a 40GB Maxtor... AGP ATI Radeon 9200SE (there's some weird stuff going on with that in Ubuntu, could it be linked? Bit crazy...), dunno what else to say...

if only I could get on the net I'm sure I'd love Ubuntu :(

---

### Post by diepruis on 2007-05-28
> **durfff said:**
> Hey Austin, cheers for the quick reply

All conflicting drivers have been blacklisted (follownig the how-to at the beginning of the thread, and double-checked the blacklist file and they're all there). 

For the output of "lsmod | grep rt" and "lsmod | grep usbcore" I don't think there's anything wrong, lsmod | grep rt only shows rt73 and a few other drivers with "rt" in the name (I doubt they have anything to do with that) and grep usbcore shows rt73... No mention of any blacklisted driver there. I could post the output here but it might take a while (cut long story short: the only hard drive that will share files between windows is Mac-formatted cos I had a mac that got stolen therefore read-and-write in windows with MacDrive but read-only in Ubuntu... So can't copy files over :() If you do want the output I'm sure I'll find a way to resize the main partition on this external and post here. Let me know, but then again I don't see anything fishy...

My comp is an AMD 2600 XP+ on MSI KM4M-L mobo, 512MB RAM and system is installed as dual-boot with XP on a 40GB Maxtor... AGP ATI Radeon 9200SE (there's some weird stuff going on with that in Ubuntu, could it be linked? Bit crazy...), dunno what else to say...

if only I could get on the net I'm sure I'd love Ubuntu :(

Mmmmm... since you're losing connectivity after about 5 minutes, I'm guessing that it's indeed the kernel. What you need to do is to insert the ubuntu CD then go to the console and type

```

sudo apt-cdrom add

```

Add the cdrom as a repository and then try 

```

sudo apt-get install linux-386

```

If that doesn't work, it means the Ubuntu CD doesn't have that kernel on it, in which case you will probably have to go the ethernet route. Borrow a cable from a friend, or move your PC and use a shorter one. Don't invest a lot of money in it, though, as I'm not sure this is the solution.

---

### Post by diepruis on 2007-05-28
> **Alex74447 said:**
> Worked perfectly for the D-Link WUA-1340.

Note for future users, maybe you should include this in the original post:

If you can't access the internet to aptitude build-essential, simply insert the Feisty disc, go to the area where you add the repositories, hit add CD, and add everything. Then reload repositories and mark Build-essential for installation and continue with the instructions.

Good tip, I'm adding this to the HOWTO (assuming you don't mind).

---

### Post by durfff on 2007-05-28
Mmmh... Thanks diepruis, I'll try that but I remember trying the kernel update with the CD in (using the sudo aptitude install linux-386 command) and that didn't work... How do I add repositories though? Or is that what that command is for? I'm that new to Linux!

Thanks muchos

---

### Post by TotallyConfused on 2007-05-29
> **Austin_KW said:**
> Yes, You need to go back to rt73-cvs-yyyymmddhh/Module directory, and do the "sudo make" and "sudo make install" again.
You will need to do this every time you boot a newly installed  kernel

Thanks alot! I'm much clearer on how to resolve a kernel upgrade now. :D

---

### Post by psavva on 2007-05-29
Thanks dude.  Works perfectly

---

### Post by diepruis on 2007-05-29
> **durfff said:**
> Mmmh... Thanks diepruis, I'll try that but I remember trying the kernel update with the CD in (using the sudo aptitude install linux-386 command) and that didn't work... How do I add repositories though? Or is that what that command is for? I'm that new to Linux!

Thanks muchos

You can add new repositories in Synaptic (or Adept for Kubuntu) or by editing /etc/apt/sources.list. In addition, the command ```
sudo apt-cdrom add
``` adds a CDROM with packages on it to your repositories. If you can't get on the internet with that computer at all, then you'll need to manually download the packages you need, and that really is a major drag. I really do recommend you find some way to get that PC hooked up to the Interpages.

---

### Post by diepruis on 2007-05-29
> **psavva said:**
> Thanks dude.  Works perfectly

Glad I could help.

---

### Post by ceaseoleo on 2007-05-30
"I have now gone back to feisty 32 bit (generic) and it seems much better behaved, but I am curious if anyone else if seeing wlan1 in place of wlan0.
One time I installed this on a 32 bit Beta of Feisty. After a few false starts and the like, I finally got the device to play along. It came up as rausb0, but after a bit of fiddling it inexplicably changed to rausb1. I still have no idea why and like you, I couldn't find anything reserving the previous name. I checked /etc/modprobe.conf and modprobe.d as well."

Hi Dieprus

After new kernel update, i went through the instructions again.  It used to work on rausb0 , but now I see it is working on wlan1 when i scan and run iwconfig up.  any ideas on why this might be.. or how did you remove it from rausb1 back to rausb0.  I can get wlan1 to work wirelessly only when I manually enter in everything manually.  

rt73                  213888  0 
rtc                    13232  0 
snd                    51716  14 snd_via82xx,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
agpgart                34096  2 via_agp,amd64_agp
usbcore               131480  4 rt73,ehci_hcd,uhci_hcd

from lsmod | grep rt73 .. its listed twice in the list ??????????

also in the /etc/sysconfig/network-scripts theres a file called ifcfg-rausb0 .. 
thanks

---

### Post by diepruis on 2007-05-30
> **ceaseoleo said:**
> Hi Dieprus

After new kernel update, i went through the instructions again.  It used to work on rausb0 , but now I see it is working on wlan1 when i scan and run iwconfig up.  any ideas on why this might be.. or how did you remove it from rausb1 back to rausb0.  I can get wlan1 to work wirelessly only when I manually enter in everything manually.  

rt73                  213888  0 
rtc                    13232  0 
snd                    51716  14 snd_via82xx,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
agpgart                34096  2 via_agp,amd64_agp
usbcore               131480  4 rt73,ehci_hcd,uhci_hcd

from lsmod | grep rt73 .. its listed twice in the list ??????????

also in the /etc/sysconfig/network-scripts theres a file called ifcfg-rausb0 .. 
thanks

If you look closely, you'll see that the second rt73 in the list is on the right hand side. That means it's dependent on the module on the left hand side (i.e. usbcore).

As for changing the interface name, I didn't manage to do that. For some reason it didn't want to change back. However, your interface should be wlan* because the driver was changed by the serialmonkey guys. If I was you, I wouldn't worry about it, since it really doesn't have any practical implications. All you need to do is change the occurrences of rausb0 in the /etc/network/interfaces file to wlan1.

---

### Post by lowebb on 2007-05-30
I have a D-Link G122 rev c1, and Ive managed to get it up and runnign with feisty, but it seems random whether it will come up at boot time or not. I've been postingo n the serial monkey forum about this and am still at a deadlock on it.

See here for further info:

[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3828](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3828)

anyway basically I (sometimes 50% of the time) get the output from DMES

 40.198009] rtusb init ====>
[ 40.289147] usb 3-3: USB disconnect, address 4
[ 40.289158] rt73: probe of 3-3:1.0 failed with error -71

If I reinsert it and restart my network it comes up just fine.

I was wondering if anyone else seen this behaviour. I think it may be something to do with my freecom dvb usb dongle because when I remove it, the wireless dongle comes up 100% of the time.

Can anyone suggest a hacked fix, the best I've come up with is a script which will I can run on start-up after reinserting the dongle (which is ideal)

Thanks

---

### Post by Austin_KW on 2007-05-30
> If I reinsert it and restart my network it comes up just fine.
I have regular problems with this device at boot. I have always suspected that it is a firmware load issue as it will be working and stable at boot until I install something which will change the boot timing. 

It should be noted that I refuse to go back to the 386 kernel which most people report is much more stable but I don't want to cripple my smp system just to use this £10 network card. 


It was a little better in edgy, I could just reinsert the card an usually the wlan would come up. In feisty, I have to ifdown, remove the dongle then reinsert and manually ifup. I suppose that I could add commands to my /etc/rc.local but I am not sure how to force a firmare reload (I dont think unloading/reloading the driver will do it) and I am not even 100% sure that that is the problem.

---

### Post by Mars73 on 2007-05-30
Diepruis, you're a life safer.
I've almost given up on my Belkin USB Mimo (rt73) adapter but you're instructions we're very helpful.
Up and running on kernel 2.6.20-16 with wpa aes, even on my hyperthreading and without the 386 version.
Great!

---

### Post by diepruis on 2007-05-31
> **lowebb said:**
> I have a D-Link G122 rev c1, and Ive managed to get it up and runnign with feisty, but it seems random whether it will come up at boot time or not. I've been postingo n the serial monkey forum about this and am still at a deadlock on it.

See here for further info:

[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3828](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3828)


I read through that post and you're most probably correct, I won't be able to offer as much support as the serialmonkey guys. I did have an idea while reading through the thread though. Isn't there some way you can use Upstart to delay the device being brought up till everything else is on line? As you may know, Upstart is event based, so you can make it wait for any arbitrary condition to become true, e.g. your other devices must be functional before it attempts to load the firmware for the rt73 device. I don't know to what extent it's been included in Feisty, however, or how to configure, so you're pretty much on your own.

I feel I must raise an obvious question here, what if the USB dongle is just pure crap? Austin_KW seems to be having problems with it as well, and I've had several USB devices that didn't work properly even using native drivers in Windows. It might be worth it to invest in a quality PCI card that's well supported.

---

### Post by diepruis on 2007-05-31
> **Mars73 said:**
> Diepruis, you're a life safer.
I've almost given up on my Belkin USB Mimo (rt73) adapter but you're instructions we're very helpful.
Up and running on kernel 2.6.20-16 with wpa aes, even on my hyperthreading and without the 386 version.
Great!

Happy to help, friend.

The kernel issues seem to only affect certain setups / devices. It seems you're one of the lucky ones :)

---

### Post by epee on 2007-05-31
Just out of interest - how come this excellent thread containing such a wealth of crucial information is not a sticky?

---

### Post by durfff on 2007-05-31
RIght, as I said I can access the tinterweb from the windows installation on my machine, so I looked around a bit for the right kernel and I'm a little tad confused... I've downloaded 2 different ones so far, linux-386_2.6.20-7.1_i386.deb and linux-386_2.6.17.11_i386.deb.

Is any of them right for my install? And provided one of them is what I want (or provided I find the one that's actually for my machine), how do I go about installing it? I've found a few threads about it but it's all a bit confusing, the kernel file isn't a .deb or something slightly different like that...

Thanks for any help :D

---

### Post by durfff on 2007-05-31
I've just checked on startup the kernel I'm using at the moment is 2.6.17.10-generic. Can I download any kernel version, as in, the latest one? Or does it have to be 2.6.17.10-i386? 

The Master Kernel thread ([http://ubuntuforums.org/showthread.php?t=311158]("http://ubuntuforums.org/showthread.php?t=311158")) also says about downloading .bz2 files and then uncompress... But will downloading them from a mirror give me the generic kernel? God I'm confused about kernels!!! Kernels!!! KERNELS!!!!! lol

Cheers peeps

---

### Post by dannyboy79 on 2007-05-31
> **durfff said:**
> I've just checked on startup the kernel I'm using at the moment is 2.6.17.10-generic. Can I download any kernel version, as in, the latest one? Or does it have to be 2.6.17.10-i386? 

The Master Kernel thread ([http://ubuntuforums.org/showthread.php?t=311158]("http://ubuntuforums.org/showthread.php?t=311158")) also says about downloading .bz2 files and then uncompress... But will downloading them from a mirror give me the generic kernel? God I'm confused about kernels!!! Kernels!!! KERNELS!!!!! lol

Cheers peeps
if when you issue the command, uname -r
and it returns 2.6.17.10-generic
than you need to use those kernel header files. You find them here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
chose edgy, then chose Development then chose to download them 
OR
just use this wget command I made by copying the link and pasting it for ya.

wget [http://packages.ubuntu.com/edgy/devel/linux-headers-2.6.17-10-generic](http://packages.ubuntu.com/edgy/devel/linux-headers-2.6.17-10-generic)

---

### Post by diepruis on 2007-05-31
> **durfff said:**
> I've just checked on startup the kernel I'm using at the moment is 2.6.17.10-generic. Can I download any kernel version, as in, the latest one? Or does it have to be 2.6.17.10-i386? 

The Master Kernel thread ([http://ubuntuforums.org/showthread.php?t=311158]("http://ubuntuforums.org/showthread.php?t=311158")) also says about downloading .bz2 files and then uncompress... But will downloading them from a mirror give me the generic kernel? God I'm confused about kernels!!! Kernels!!! KERNELS!!!!! lol

Cheers peeps

Ignore the master kernel thread, that concerns compiling your own kernel - which I really do not recommend. You need the 2.6.17.10-i386 deb and also the file that dannyboy79 linked to. Then you need to install both of those using
```

sudo dpkg -i linux-386_2.6.17.11_i386.deb
sudo dpkg -i linux-headers-386_2.6.17.11_i386.deb

```

Then you will have to reboot, choose the new kernel from GRUB's boot menu and only then can you compile the driver for this card. A big hassle, I know, but it can't really be helped.

---

### Post by diepruis on 2007-05-31
> **epee said:**
> Just out of interest - how come this excellent thread containing such a wealth of crucial information is not a sticky?

I'm not sure, but I believe the motivation is to encourage contribution to the wiki instead. However, I don't feel that this driver is stable and bug-free enough to warrant a place on the wiki. Besides, the discussion based nature of the forums is better suited to ironing out the sort of kinks people are encountering.

---

### Post by dannyboy79 on 2007-05-31
> **diepruis said:**
> Ignore the master kernel thread, that concerns compiling your own kernel - which I really do not recommend. You need the 2.6.17.10-i386 deb and also the file that dannyboy79 linked to. Then you need to install both of those using
```

sudo dpkg -i linux-386_2.6.17.11_i386.deb
sudo dpkg -i linux-headers-386_2.6.17.11_i386.deb

```

Then you will have to reboot, choose the new kernel from GRUB's boot menu and only then can you compile the driver for this card. A big hassle, I know, but it can't really be helped.

well I only recommended the -generic headers because a few posts back a person said that it's working with SMP. he should need both headers does he?

---

### Post by Austin_KW on 2007-05-31
> **diepruis said:**
> I read through that post and you're most probably correct, I won't be able to offer as much support as the serialmonkey guys. I did have an idea while reading through the thread though. Isn't there some way you can use Upstart to delay the device being brought up till everything else is on line? As you may know, Upstart is event based, so you can make it wait for any arbitrary condition to become true, e.g. your other devices must be functional before it attempts to load the firmware for the rt73 device. I don't know to what extent it's been included in Feisty, however, or how to configure, so you're pretty much on your own.

I feel I must raise an obvious question here, what if the USB dongle is just pure crap? Austin_KW seems to be having problems with it as well, and I've had several USB devices that didn't work properly even using native drivers in Windows. It might be worth it to invest in a quality PCI card that's well supported.

It might well be pure crap, but I would be happy if it was as stable as the windows driver (which only works 100% for me with static addresses).
I still think it is a driver issue. My sysV startup and Upstart knowledge is too out of date to go tinkering with startup sequence. But being the adventurous type I decided to modify my copy of the driver to do an extra firmware load on ifup. This was a lot more stable for me but that is just as likely due to the fact that I have modified the timings with my debug messages. 

But what I have discovered is that on my dual boot system; If I restart from windows into ubuntu the rt73 will not work. The warm start is not clearing the device state and the rt73 is not clearing it either. The only way to fix it is ifdown-remove-reinsert-ifup. A warm start ubuntu 2 ubuntu seems OK. Obviously this could be a combination of my bios, usb chipsets and drivers.


EDIT:
No you are right, it is crap, I put it in my laptop to compare against a pcmcia card and it is unstable junk.

---

### Post by Mars73 on 2007-06-01
> **dannyboy79 said:**
> well I only recommended the -generic headers because a few posts back a person said that it's working with SMP. he should need both headers does he?

So far no problems with the rt73.
I'm not at my home pc right now but I use a HP DC7600 2.8GHz with Hyperthreading and using the generic linux image (2.6-20.16).
I downloaded the rt73 driver from the ralink site, copied the firmware file (bin) to a Wireless folder, followed most of what was in the readme file of ralink and then following Diepruis's instructions, then I was able to get it perfectly running.
I could give you more info (if it's needed) when I get back home from work.
I'm not sure if I have 2 headers, I certainly didn't install an extra header for it to work, just the generic ones.

---

### Post by diepruis on 2007-06-01
> **Mars73 said:**
> So far no problems with the rt73.
I'm not at my home pc right now but I use a HP DC7600 2.8GHz with Hyperthreading and using the generic linux image (2.6-20.16).
I downloaded the rt73 driver from the ralink site, copied the firmware file (bin) to a Wireless folder, followed most of what was in the readme file of ralink and then following Diepruis's instructions, then I was able to get it perfectly running.
I could give you more info (if it's needed) when I get back home from work.
I'm not sure if I have 2 headers, I certainly didn't install an extra header for it to work, just the generic ones.

Like I said earlier, the 386 kernel is only needed by very few people. Also note that the RaLink driver is **not** the same as this one. The serialmonkey driver is worked on by volunteers and is more up-to-date and bug free than the RaLink one - at least as far as I know.

They are, however, similar (serialmonkey forked the RaLink driver), which is why my instructions partially worked for you.

If everything is working, though, good for you. If it ain't broke don't fix it, eh?

---

### Post by diepruis on 2007-06-01
> **dannyboy79 said:**
> well I only recommended the -generic headers because a few posts back a person said that it's working with SMP. he should need both headers does he?

He's having problems with the generic kernel, so I advised he try the 386 kernel, in which case he needs the kernel deb and also the headers for that kernel.

---

### Post by diepruis on 2007-06-01
> **Austin_KW said:**
> No you are right, it is crap, I put it in my laptop to compare against a pcmcia card and it is unstable junk.

Heh. That's the D-Link G122 rev c1, right? I should remember to scare people away from it ;)

---

### Post by Mars73 on 2007-06-01
> **diepruis said:**
> They are, however, similar (serialmonkey forked the RaLink driver), which is why my instructions partially worked for you.

Of which I'm very grateful. :)
> 
If everything is working, though, good for you. If it ain't broke don't fix it, eh?
I'm looking for a good backup/image method right now so that I always have a working image that I can restore in case I mess up things. Looks like ghost 4 linux is nice (but this is for another thread).

---

### Post by dannyboy79 on 2007-06-01
> **diepruis said:**
> He's having problems with the generic kernel, so I advised he try the 386 kernel, in which case he needs the kernel deb and also the headers for that kernel.

ok, since he has to download on another machine etc etc why didn't you tell him that he didn't need to download the -generic headers then, that's all I am pointing out? 

Plus, I didn't know he was having problems with the -generic kernel and headers, I didn't think he had any headers since he doesn't have an internet connection to begin with, which is why I suggested downloading the -generic first so that he can get the most out of his cpu.

I have a guy that's very p.o.'d about feisty freezing on hiim so much, someone stated that it's becase of the Ralink rt61 drivers that ubuntu provides, they told him to blacklist them and then build from serialmonkey's. He can follow your guide correct? ANd now that I ahve read what  mars person has to say, I even more confident since I think he's talking about the same driver, the rt61 I hope. 
So what does the new ralink driver get named because wouldn't the fact that he has to blacklist both rt61 and rt61pc make it so that modules with those name won't get loaded? I am kind of new at the custom module compiling thingy.

DISREGARD, I saw that mars.. isn't using the RT61.

---

### Post by Abadaar on 2007-06-01
I just wanted to report that I have successfully downloaded latest rt73-cvs, compiled and installed it on my SMP system.

The steps I took:
-Downloaded [rt73-cvs-daily.tar.gz]("http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz")
-Unpacked (tar -xvzf rt73-cvs-daily.tar.gz)
-Read the Readme
-Compiled (make), stripped (strip -S rt73.ko) and installed (sudo make install)
-Blacklist and modprobe -r the "bad" drivers, modprobe rt73
-Configured /etc/network/interfaces, according to the instructions in the Readme, for my WPAPSK-TKIP network
```

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 mode managed
pre-up iwconfig wlan0 essid <ESSID>
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set WPAPSK=<KEY>
pre-up iwpriv wlan0 set EncrypType=TKIP

```
-Added "alias wlan0 rt73" in /etc/modprobe.d/aliases
-Plugged in the Sweex LW053 USB dongle (rt2571wf)
-Ran "sudo /etc/init.d/networking restart" and up it goes! :)

I have a stable connection even through 2 walls. :)

---

### Post by diepruis on 2007-06-02
> **Abadaar said:**
> I just wanted to report that I have successfully downloaded latest rt73-cvs, compiled and installed it on my SMP system.

-Compiled (make), stripped (strip -S rt73.ko) and installed (sudo make install)

I have a stable connection even through 2 walls. :)

Sweet! Which version of the CVS is this though? I can't remember having to strip the kernel module, if that's a recent addition I should add it to the instructions here.

---

### Post by durfff on 2007-06-02
Thank you so much everyone or all the help and prompt replies! The Ubuntu community rocks! (and it will rock even more when I get that damn thing to work :-P )

Right, before I proceed installing the new kernel, a couple of quick and stupid questions...

- Diepruis, you said:
> **diepruis said:**
> You need the 2.6.17.10-i386 deb and also the file that dannyboy79 linked to. Then you need to install both of those using
```

sudo dpkg -i linux-386_2.6.17.11_i386.deb
sudo dpkg -i linux-headers-386_2.6.17.11_i386.deb

```

Doesn't that code need to say 2.6.17.**10** instead of 11?

- Where do I put the files before executing that command?

Cheers! durf is da noobnoobnoob!

---

### Post by diepruis on 2007-06-02
> **durfff said:**
> Doesn't that code need to say 2.6.17.**10** instead of 11?

Err.... yes, it should be .10 :oops:

> **durfff said:**
> Where do I put the files before executing that command?

You can really put them anywhere you want to. AFAIK they will be added to apt's cache in /var/cache/apt regardless of where they are installed from, so feel free to just dump them in your home directory and delete them once you're sure the kernel is properly installed.

Oh, and BTW, good luck ;)

---

### Post by Abadaar on 2007-06-02
> **diepruis said:**
> Sweet! Which version of the CVS is this though? I can't remember having to strip the kernel module, if that's a recent addition I should add it to the instructions here.

20070528 was the first I tried and the later ones have worked as well... I made me a little script which automatically downloads, compiles, installs the latest cvs and also keep rolling backups of the 4 latest ones ^^

When I had compiled, the rt73.ko was about 2.7MiB and I got a warning about it being too big. So I stripped it of the unnecessary stuff with "strip -S". After the strip it's down to 243KiB :)

---

### Post by diepruis on 2007-06-02
> **Abadaar said:**
> 20070528 was the first I tried and the later ones have worked as well... I made me a little script which automatically downloads, compiles, installs the latest cvs and also keep rolling backups of the 4 latest ones ^^

I'm impressed, I bow to your superior geekiness =D.

> **Abadaar said:**
> When I had compiled, the rt73.ko was about 2.7MiB and I got a warning about it being too big. So I stripped it of the unnecessary stuff with "strip -S". After the strip it's down to 243KiB :)

Thanks, I'll add that to the HOWTO as well.

---

### Post by Abadaar on 2007-06-02
> **diepruis said:**
> 
Just one caveat: RT73 doesn't support SMP or PREEMPT. These are options that can be set when your kernel is being compiled. If that doesn't make any sense, don't worry, it's all been taken care of by the Ubuntu developers. What it boils down to is you can't use hyper threading or dual-core capabilities alongside this driver. The guys at rt2x00.serialmonkey.com are aware of this and are working on support for SMP platforms, once the rt2x00 driver is finished, you can use your PC to it's optimum capacity.

If you have such a system, you need to do the following:
[LIST=1]
[*] Install a non SMP kernel.
```

sudo aptitude install linux-386 (see below if this fails, or if you don't have internet access)

```
[*] Reboot.
[*] While your PC is booting, you should see a prompt with something about GRUB. When this appears press ESC repeatedly.
[*] A list of kernels will come up, choose the one that contains 386.
[/LIST]

You can set up GRUB to automatically load this kernel instead of another, but that is beyond the scope of this howto. For more information, see [this webpage](http://www.gnu.org/software/grub/manual/grub.html) on editing /boot/grub/menu.lst.

Also note that, should you do this, you may need to recompile some other kernel modules, such as fglrx and possibly the nvidia drivers.


I think that you can remove or move this part since the driver works on SMP/PREEMPT systems now and has for a few weeks according to their forums, the changelog and since it works on both of my SMP systems. :)

> **diepruis said:**
> 
If the module is too big, strip unnecessary stuff from it.

On some systems, the rt73 kernel module compiles to a file that is unnecessarily large. If this happens to you, you will receive a warning like this: 
```

!!! WARNING: Module file much too big (>1MB)
!!! Check your kernel settings or use 'strip'

```
If you want to make doubly sure, you can check the file's size by typing
```

ls -alh rt73.ko

```
If the file's size is in the megabytes, you are affected by this issue (it's not really a bug).

Luckily this is easily fixed, just type
```

sudo strip -S rt73.ko

```

All this does is remove debugging symbols, which most users don't require. After the strip command, you can check the file size again, it should be around 240K.


On my screen that looks like a small s in "-S", and if you use a small s you will get an error when you try to modprobe it later, which is not good :) I suggest making a note that it must be a big S.

---

### Post by diepruis on 2007-06-02
> **Abadaar said:**
> I think that you can remove or move this part since the driver works on SMP/PREEMPT systems now and has for a few weeks according to their forums, the changelog and since it works on both of my SMP systems. :)

Indeed you are correct sir. I'll remove it at once.

> **Abadaar said:**
> On my screen that looks like a small s in "-S", and if you use a small s you will get an error when you try to modprobe it later, which is not good :) I suggest making a note that it must be a big S.

That might be a bit paranoid, but I'll add it anyway.

---

### Post by Austin_KW on 2007-06-02
diepruis,
Just looking again at your updated instructions;

As the hourly tarball is always in the same place, you could add the download command to the howto, 
sudo wget [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) -o /usr/src/rt73-cvs-daily.tar.gz

You might also mention that it will be necessary to redo the make and install after booting a kernel upgrade.

The WPA instructions give EncrypType=AES, This should be EncrypType=TKIP. AES is WPA2 and may not be supported on older access point hardware that only support the wep encryption algorithm

---

### Post by diepruis on 2007-06-03
> **Austin_KW said:**
> As the hourly tarball is always in the same place, you could add the download command to the howto, 
sudo wget [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) -o /usr/src/rt73-cvs-daily.tar.gz

Good point, changed.

> **Austin_KW said:**
> You might also mention that it will be necessary to redo the make and install after booting a kernel upgrade.

Added.

> **Austin_KW said:**
> The WPA instructions give EncrypType=AES, This should be EncrypType=TKIP. AES is WPA2 and may not be supported on older access point hardware that only support the wep encryption algorithm

I have no idea what's going on there, so I just blindly followed your suggestion ;)

---

### Post by Austin_KW on 2007-06-03
Sorry, idiot typo/

The wget should have '-O' not '-o', The lowercase just redirects the standard output logging

---

### Post by Abadaar on 2007-06-03
Actually, you don't have to put the source in /usr/src/ at all, that will just make it more complicated. No need for sudo up until "make install" if you just put it in your home dir. Don't use your superpowers when you don't need to! :)

---

### Post by Austin_KW on 2007-06-03
> **Abadaar said:**
> Actually, you don't have to put the source in /usr/src/ at all, that will just make it more complicated. No need for sudo up until "make install" if you just put it in your home dir. Don't use your superpowers when you don't need to! :)

Except, you want to encourage users to keep the sources, as they will lose the network connection when they upgrade the kernel and need to rebuild. Users are less likely to delete (without thinking) from under the /usr/src tree.

---

### Post by diepruis on 2007-06-03
> **Austin_KW said:**
> Sorry, idiot typo/

The wget should have '-O' not '-o', The lowercase just redirects the standard output logging

Changed ;)

---

### Post by diepruis on 2007-06-03
> **Austin_KW said:**
> Except, you want to encourage users to keep the sources, as they will lose the network connection when they upgrade the kernel and need to rebuild. Users are less likely to delete (without thinking) from under the /usr/src tree.

Exactly, plus, it makes logical sense putting it there, since that's what the directory's for (I think). It also emphasizes the idea of having source code for all the software on your computer.

---

### Post by alexrb on 2007-06-03
hi, diepruis

thanx for great howto. actually that's the only howto that made my g122 working.
but I'm having one problem.

After I edit /etc/network/interfaces as you wrote in the first post I can't connect to my wireless network after reboot. 

Here what I have: 
```

auto lo
iface lo inet loopback

auto eth1
iface  eth1 inet dhcp

auto rausb0
iface rausb0 inet dhcp
       pre-up ifconfig rausb0 up
       pre-up iwconfig rausb0 essid RALSTUDIO
       pre-up iwconfig rausb0 key "off"

```

hope you could help to solve my problem. thanx in advance!

best wishes from Ukraine,
Alex

---

### Post by pfwd.tech on 2007-06-03
Ok, just trying this out.  I'm getting this after i try and install the modules

```
pete@pfwd:/usr/src/rt73-cvs-2007060313/Module$ sudo make install
*** Install module in /lib/modules/2.6.20-16-generic/extra ...
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/usr/src/rt73-cvs-2007060313/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  INSTALL /usr/src/rt73-cvs-2007060313/Module/rt73.ko
  DEPMOD  2.6.20-16-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
/sbin/depmod -a
*** Update /etc/modprobe.conf alias for wlan*
*** Install firmware in /lib/firmware ...
*** Check config ...
!!!
!!! WARNING: DEPRECATED CONFIG FOUND !
!!!
!!! -> Update your config and remove /etc/Wireless/RT73STA
!!! -> rt73sta.dat file is deprecated: use iwconfig/iwpriv instead
!!! -> rt73.bin firmware has moved to /lib/firmware
!!! -> ra0 interface name is deprecated: remove old /etc/modprobe.conf alias

```

I haven't been using Ubuntu long (Linux for that matter) so I'm not sure what the first course of action is.  I take it that these are conflicting settings in a config file or something.
What should i do?

---

### Post by diepruis on 2007-06-03
> **alexrb said:**
> 
```

auto rausb0
iface rausb0 inet dhcp
       pre-up ifconfig rausb0 up
       pre-up iwconfig rausb0 essid RALSTUDIO
       pre-up iwconfig rausb0 key "off"

```

hope you could help to solve my problem. thanx in advance!

best wishes from Ukraine,
Alex

Hey Alex, that rausb0 thingy is the name of the network interface (i.e. the wireless USB adapter). That name was recently changed to wlan0, so you might want to try changing all the occurences of "rausb0" to "wlan0" in /etc/network/interfaces

If that doesn't solve your problem, please post the output of these commands:
```

iwconfig
sudo ifdown -a
sudo ifup -a

```

Good luck!

---

### Post by diepruis on 2007-06-03
> **pfwd.tech said:**
> 
```

!!! WARNING: DEPRECATED CONFIG FOUND !
!!!
!!! -> Update your config and remove /etc/Wireless/RT73STA
!!! -> rt73sta.dat file is deprecated: use iwconfig/iwpriv instead
!!! -> rt73.bin firmware has moved to /lib/firmware
!!! -> ra0 interface name is deprecated: remove old /etc/modprobe.conf alias

```

I haven't been using Ubuntu long (Linux for that matter) so I'm not sure what the first course of action is.  I take it that these are conflicting settings in a config file or something.
What should i do?

The warnings may be completely innocuous, if the USB adapter is working regardless, just ignore them. My advice would be to follow the rest of the HOWTO and if that doesn't work, then follow the instructions below:

I think this is detecting the remnants of an old installation of the driver that still required the STA files to be placed in that location. It **should** be safe to delete it ```
sudo rm -R /etc/Wireless/RT73STA
``` but I can't be 100% sure.

The last line seems to involve a deprecated driver for an rt61 card. Odd that the rt73 scripts would be complaining about that... might be a bug, regardless that warning is also easy to get rid of. Just do ```
gksu gedit /etc/modprobe.conf
``` remove the line that says "alias ra0 rt61" and save the file. If there's a line like "alias rausb0 rt73" you should remove that too.

However, **do not** remove the rt**61** line if you also have a working rt61 driver installed, because that would break it.

Good luck ;)

---

### Post by alexrb on 2007-06-03
thanx for reply

maybe i'm using not the latest drivers? but at least when I'm using rausb0 name it works (sometimes).

here we go with some code
```

lo        no wireless extensions.

eth0      no wireless extensions.

rausb0    RT73 WLAN  ESSID:off/any  
          Mode:Auto  Channel=1  Bit Rate:54 Mb/s   
          RTS thr:off   Fragment thr:off

```

sudo ifdown -a gave no results

```

eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/rausb0/00:17:9a:bd:da:f9
Sending on   LPF/rausb0/00:17:9a:bd:da:f9
Sending on   Socket/fallback
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by diepruis on 2007-06-03
> **alexrb said:**
> 
```

lo        no wireless extensions.

eth0      no wireless extensions.

rausb0    RT73 WLAN  ESSID:off/any  
          Mode:Auto  Channel=1  Bit Rate:54 Mb/s   
          RTS thr:off   Fragment thr:off

```


Mmmm... looks like the device isn't setting the ESSID correctly. Make sure that it is brought up with "sudo ifconfig rausb0 up" before trying to set that. Could you try the following commands and attach the output in a text file?

```

sudo ifdown rausb0
sudo ifconfig rausb0 up
sudo ifconfig rausb0 essid RALSTUDIO
sudo ifconfig rausb0 key off
sudo dhclient rausb0

```

Also, could you include the output from this?

```

sudo ifconfig rausb0 up
sudo iwlist rausb0 scan

```

---

### Post by alexrb on 2007-06-03
scan says it doesn't supported

other commands coming soon

---

### Post by diepruis on 2007-06-03
> **alexrb said:**
> scan says it doesn't supported

other commands coming soon

That doesn't sound right. I remember doing scans with this device before. Could you paste the exact output?

---

### Post by alexrb on 2007-06-03
> **diepruis said:**
> Mmmm... looks like the device isn't setting the ESSID correctly. Make sure that it is brought up with "sudo ifconfig rausb0 up" before trying to set that. Could you try the following commands and attach the output in a text file?
I guess so too
> 
```

sudo ifdown rausb0
sudo ifconfig rausb0 up
[COLOR="Red"]sudo ifconfig rausb0 essid RALSTUDIO
sudo ifconfig rausb0 key off
[/COLOR]sudo dhclient rausb0

```

iwconfig i guess ;)
still "NO DHCPOFFERS received" error

hope this helps.

I've got online from that machine 2 times. 
First, before I edited /etc/netowrk/interfaces
Second, when I deleted everything about rausb0 from *interfaces*
But that's not solution... ;)

---

### Post by alexrb on 2007-06-03
> **diepruis said:**
> That doesn't sound right. I remember doing scans with this device before. Could you paste the exact output?

```

rausb0 Interface doesn't support scanning.

```

---

### Post by Austin_KW on 2007-06-03
> **alexrb said:**
> ```

rausb0 Interface doesn't support scanning.

```

The interface has to come up at least once before it will scan etc. As suggested above did you "sudo ifconfig rausb0 up" before the scan

---

### Post by alexrb on 2007-06-03
> **Austin_KW said:**
> The interface has to come up at least once before it will scan etc. As suggested above did you "sudo ifconfig rausb0 up" before the scan

yes, I did

---

### Post by diepruis on 2007-06-03
> **alexrb said:**
> I guess so too

iwconfig i guess ;)
still "NO DHCPOFFERS received" error


Hah, my bad :oops:

> **alexrb said:**
> 
hope this helps.

I've got online from that machine 2 times. 
First, before I edited /etc/netowrk/interfaces
Second, when I deleted everything about rausb0 from *interfaces*
But that's not solution... ;)

This is strange and it's hard to debug this kind of thing over the internet. Mmmm... all I can think of is to try a more recent CVS of the driver, i.e. just follow the guide again. The reason I say that is because of the fact that the device can't scan, while I'm 90% sure it should be able to. This makes me think there's something wrong with the driver.

Are you sure it's the right driver for the device? What does
```

lsusb

```
give you? (You can ignore the lines with "ID 0000:0000")

---

### Post by alexrb on 2007-06-03
lsusb gives 
```

Bus 002  Device 002: ID 07d1:3c03 D-Link System 

```

if i plug in usb flash drive it shows too

---

### Post by alexrb on 2007-06-03
> **diepruis said:**
> 
This is strange and it's hard to debug this kind of thing over the internet. 
I'm here and it's not easier. ha-ha :)

> 
Mmmm... all I can think of is to try a more recent CVS of the driver, i.e. just follow the guide again. The reason I say that is because of the fact that the device can't scan, while I'm 90% sure it should be able to. This makes me think there's something wrong with the driver.


yep, I think something wrong went with driver but why I was able to got online? really bizarre...

---

### Post by diepruis on 2007-06-03
> **alexrb said:**
> lsusb gives 
```

Bus 002  Device 002: ID 07d1:3c03 D-Link System 

```

if i plug in usb flash drive it shows too

Did some quick searches, you're trying the right driver.

---

### Post by diepruis on 2007-06-03
> **alexrb said:**
> I'm here and it's not easier. ha-ha :)

;)

> **alexrb said:**
> yep, I think something wrong went with driver but why I was able to got online? really bizarre...

I can honestly not say... you probably accidentally broke something (it happens). You could try doing this:

```

sudo ifdown rausb0
sudo modprobe -rv rt73
sudo modprobe -v rt73
sudo ifup rausb0
dmesg | tail

```

And try to find any error messages, that might be illuminating.

---

### Post by pfwd.tech on 2007-06-03
Thanks for the reply, I removed the old drivers like you said and its working to a point.
The scan is picking up my network
iwlist scan
```
 
pete@pfwd:/usr/src/rt73-cvs-2007060313/Module$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:11:50:93:34:8E
                    ESSID:"blackbox"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Bit Rates:0 kb/s

```
after i put in the following:
udo ifconfig wlan1 up
sudo iwconfig wlan1 essid blackbox
sudo iwconfig wlan1 key xxxx.....
sudo dhclient wlan1
i get the following:
```
pete@pfwd:/usr/src/rt73-cvs-2007060313/Module$ sudo dhclient wlan1There is already a pid file /var/run/dhclient.pid with pid 10653
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:0e:2e:c6:c3:80
Sending on   LPF/wlan1/00:0e:2e:c6:c3:80
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Should my interfaces be this empty?
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto rausb0
iface rausb0 inet dhcp

auto wlan1
iface wlan1 inet dhcp
```

---

### Post by diepruis on 2007-06-03
> **pfwd.tech said:**
> Thanks for the reply, I removed the old drivers like you said and its working to a point.
The scan is picking up my network
iwlist scan
```
 
pete@pfwd:/usr/src/rt73-cvs-2007060313/Module$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:11:50:93:34:8E
                    ESSID:"blackbox"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Bit Rates:0 kb/s

```
after i put in the following:
udo ifconfig wlan1 up
sudo iwconfig wlan1 essid blackbox
sudo iwconfig wlan1 key xxxx.....
sudo dhclient wlan1
i get the following:
```
pete@pfwd:/usr/src/rt73-cvs-2007060313/Module$ sudo dhclient wlan1There is already a pid file /var/run/dhclient.pid with pid 10653
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:0e:2e:c6:c3:80
Sending on   LPF/wlan1/00:0e:2e:c6:c3:80
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```


Mmm... check the output of 
```

sudo iwconfig

```

Are the values for your ESSID and KEY set properly? Also, are you getting a reasonable signal strength?

> **pfwd.tech said:**
> 
Should my interfaces be this empty?


No, but we should get the device working before sorting that out.

---

### Post by alexrb on 2007-06-03
okay, here we go
sudo ifdown rausb0 gave
```

ifdown: interface rausb0 not configured

```

sudo modprobe -rv rt73 run smoothly (no output)
sudo modprobe -v rt73 gave 
```

insmod /lib/modules/2.6.20-15-generic/kernel/net/rt73.ko

```
sudo ifup rausb0 raised an error
```

ifup: interface rausb0 already configured

```

---

### Post by diepruis on 2007-06-03
> **alexrb said:**
> okay, here we go
sudo ifdown rausb0 gave
```

ifdown: interface rausb0 not configured

```

sudo modprobe -rv rt73 run smoothly (no output)
sudo modprobe -v rt73 gave 
```

insmod /lib/modules/2.6.20-15-generic/kernel/net/rt73.ko

```
sudo ifup rausb0 raised an error
```

ifup: interface rausb0 already configured

```

And the output from dmesg | tail?

---

### Post by alexrb on 2007-06-03
dmesg | tail output
```

[ 1390.721885 ] rt73 driver version - 1.0.4.0
[ 1401/845921 ] rausb0: no IPv6 routers present
[ 3348.39793 ] usbcore: deregestering interface driver rt73
[ 3348.397520 ] unregister_netdev()
[ 3348.436619 ] <==== rtusb exit
[ 3353.745627 ] rtusbinit ===>
[ 3353.835522 ] idVendor = 0x7d1, idProduct = 0x3c03
[ 3353.836564 ] usbcore: registered new interface driver rt73
[ 3353.843564 ] rt73 driver version - 1.0.4.0
[ 3364.594741 ] rausb0: no IPv6 routers present

```

---

### Post by pfwd.tech on 2007-06-03
yeah this looks fine to me
```
pete@pfwd:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     RT73 WLAN  ESSID:"blackbox"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:1C5D-B0EC-4F26-5773-C134-9C0D-4D
          Link Quality=0/100  Signal level:-48 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```Just pulled my cable out to test the wireless but everything dropped.
Ive cross checked the encryption key too.

The led on the Edimax usb stick is flickering like crazy

---

### Post by diepruis on 2007-06-03
> **alexrb said:**
> dmesg | tail output
```

[ 1390.721885 ] rt73 driver version - 1.0.4.0
[ 1401/845921 ] rausb0: no IPv6 routers present
[ 3348.39793 ] usbcore: deregestering interface driver rt73
[ 3348.397520 ] unregister_netdev()
[ 3348.436619 ] <==== rtusb exit
[ 3353.745627 ] rtusbinit ===>
[ 3353.835522 ] idVendor = 0x7d1, idProduct = 0x3c03
[ 3353.836564 ] usbcore: registered new interface driver rt73
[ 3353.843564 ] rt73 driver version - 1.0.4.0
[ 3364.594741 ] rausb0: no IPv6 routers present

```

That's normal too. What signal strength are you getting? You can check using iwconfig, see Link Quality, Signal Level and Noise Level.

---

### Post by diepruis on 2007-06-03
> **pfwd.tech said:**
> yeah this looks fine to me
```
pete@pfwd:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     RT73 WLAN  ESSID:"blackbox"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:1C5D-B0EC-4F26-5773-C134-9C0D-4D
          Link Quality=0/100  Signal level:-48 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```Just pulled my cable out to test the wireless but everything dropped.
Ive cross checked the encryption key too.

The led on the Edimax usb stick is flickering like crazy

I might be completely off here, but shouldn't the Link Quality be > 0. I know you don't get a connection, but my PCI card shows 88/100 even when the link is down. Does this card work in Windows / has it worked in the past? Perhaps you should try to increase the link quality?

---

### Post by alexrb on 2007-06-03
i guess i should get this when I'm connected. but i'm not :(
 iwconfig rausb0 gives
```

rausb0          RT73 WLAN  ESSID:off/any
                       Mode:Auto   Channel=1    Bit Rate:54 Mb/s
                       RTS thr: off   Fragment thr: off

```

---

### Post by diepruis on 2007-06-03
> **alexrb said:**
> i guess i should get this when I'm connected. but i'm not :(
 iwconfig rausb0 gives
```

rausb0          RT73 WLAN  ESSID:off/any
                       Mode:Auto   Channel=1    Bit Rate:54 Mb/s
                       RTS thr: off   Fragment thr: off

```

It's still not setting your ESSID... I'll get back to you tomorrow, though, need to get some sleep ;)

---

### Post by pfwd.tech on 2007-06-03
I bought the usb wireless adapter from The Linux Emporium its an EDIMAX ralink usb stick.  I haven't tested it on windows as i don't have a windows machine at hand. but i bought it specially for this.
Its like im so close lol.
How would i increase the link quality?

---

### Post by diepruis on 2007-06-03
> **pfwd.tech said:**
> I bought the usb wireless adapter from The Linux Emporium its an EDIMAX ralink usb stick.  I haven't tested it on windows as i don't have a windows machine at hand. but i bought it specially for this.
Its like im so close lol.
How would i increase the link quality?

It should work, I'm just wondering about the link quality. You could put your PC in a higher place than the router, make sure there's no metal between the router and the card, decrease the distance between the two... etc. etc. There should be more tips somewhere on the Internet, I'm not an expert in these things ;)

But the fact that the scan works indicates I'm probably barking up the wrong tree, I'll have a look again tomorrow.

---

### Post by alexrb on 2007-06-03
yep, I'll try to get some sleep too.
it's 00:15 here

thanx for help anyway!

---

### Post by pfwd.tech on 2007-06-03
Thanks for the help [COLOR=Black][diepruis]("http://ubuntuforums.org/member.php?u=130971") i'm off to sleep too 11pm in England.  I will try moving the computer upstairs tomorrow.  I'm sat right by the router at the moment in fact the router and the usb adapter are right next to each other.   I hope by moving the pc upstairs it is a quick fix.  THanks again i will let you know how i get on[/COLOR]   					 vbmenu_register("postmenu_2775445", true)

---

### Post by Abadaar on 2007-06-03
> **alexrb said:**
> hi, diepruis

thanx for great howto. actually that's the only howto that made my g122 working.
but I'm having one problem.

After I edit /etc/network/interfaces as you wrote in the first post I can't connect to my wireless network after reboot. 

Here what I have: 
```

auto lo
iface lo inet loopback

auto eth1
iface  eth1 inet dhcp

auto rausb0
iface rausb0 inet dhcp
       pre-up ifconfig rausb0 up
       pre-up iwconfig rausb0 essid RALSTUDIO
       pre-up iwconfig rausb0 key "off"

```

hope you could help to solve my problem. thanx in advance!

best wishes from Ukraine,
Alex

I suggest that you try a newer version of the driver, you might have got a bad cvs version.

---

### Post by Abadaar on 2007-06-03
> **pfwd.tech said:**
> Thanks for the help [COLOR=Black][diepruis]("http://ubuntuforums.org/member.php?u=130971") i'm off to sleep too 11pm in England.  I will try moving the computer upstairs tomorrow.  I'm sat right by the router at the moment in fact the router and the usb adapter are right next to each other.   I hope by moving the pc upstairs it is a quick fix.  THanks again i will let you know how i get on[/COLOR]   					 vbmenu_register("postmenu_2775445", true)


If you sat right by the router then I don't think it is the position that is the cause of this...

**Just some brainstorming:**
It looks like you tried the official Ralink drivers first... And I don't think Ralink and serialmonkeys put the rt73.ko and rt73.bin at the same place in the kernel module and firmware directories. It might be that it still loads an old version of the driver or firmware... Quite far fetched since it started to work better, but you never know! :)

Test using no encryption. At first, I was only able to connect to my router without any encryption, and it makes it easier to find the problem.

Do the wireless network work for other computers?

Test a more recent version of the driver, just that version might have a flaw.

What is the name of the chipset in the device? (rt2571wf for example)

Try testing it on another computer if you have one.

Do you have a wireless phone close to the router? (They might actually operate on the same frequency!)


That's all I can think of right now. Good luck!

---

### Post by Mr_bleu on 2007-06-03
Thanks!!!!!!!!!!!!!!!!!!!  Much appreciated.  For some that still can't access the net, have them disable their current wireless device in network manager.

---

### Post by pfwd.tech on 2007-06-04
> **Abadaar said:**
> If you sat right by the router then I don't think it is the position that is the cause of this...


Hi thanks for the reply.
The network has other machines running fine on it.
I tried with no encryption and i got the same results.

I have a Belkin f065070 Version 1000  and i tried that with this guide but it didn't work.  So i bought an Edimax Wireless Lan USB adaptor from The Linux Emporuim who said in an email that it would work fine under Feisty Fawn just not under the Feisty Fawn driver. 
The chipset for this is the RT2571
There are instructions that came with the Edimax but they are really different from this guide.(its a cd that asks you questions and installs things for you).  Plus when i completed the instructions and rebooted like it said i got this message and the system locked up
```
Message from syslogd@pfwd at Sat Jun  2 17:52:00 2007 ...
pfwd kernel: [  102.933870] Oops: 0002 [1] SMP 

Message from syslogd@pfwd at Sat Jun  2 17:52:00 2007 ...
pfwd kernel: [  102.934165] CR2: 000000000010c00
```

Thats when i went back to this guide and tired it again.  This is the furtherest I've got.
Is there a way i could check if the driver i have is old?
The CD that came with the Edimax puts everything in the root/ralink/ folder and this guide is putting it in the usr/src folders. Do you think these to could conflict?
I'm new to Linux so i haven't deleted yet.

---

### Post by diepruis on 2007-06-04
> **Abadaar said:**
> I suggest that you try a newer version of the driver, you might have got a bad cvs version.

Ditto, that's all I can think of.

---

### Post by diepruis on 2007-06-04
> **pfwd.tech said:**
> The CD that came with the Edimax puts everything in the root/ralink/ folder and this guide is putting it in the usr/src folders. Do you think these to could conflict?
I'm new to Linux so i haven't deleted yet.

It might well be some sort of conflict, as Abadaar said. To test that theory you could try searching the hard drive for rt73.ko files, if there's more than one, the wrong one may be loading. You should also check for multiple copies of rt73.bin.

---

### Post by dannyboy79 on 2007-06-04
> **pfwd.tech said:**
> I have a Belkin f065070 Version 1000  and i tried that with this guide but it didn't work.  .
NOT GOOD, I bought this same one  cause I liked how it has the usb cable and stand off away frmo the usb port (interference reasons) I bought it cause I wanted to see if I can get wireless in my computer room when I work on customer's boxes, both linux and winbloz. I tried breifly to get the ndiswrapper and windows drivers to work but needed to upgrade the ndiswrapper version so I didn't bother since it was a customer's box that I had isntalled Edgy Xubuntu on it for him and he has an ehternet card that worked straight away.

 I have been so busy that I haven't really tried to get it working yet on a test Gutsy Gibbon box that I installed on an old Dell Dimension 8200 but I have followed the thread for a long time.

WHat's the reason you couldn't get the belkin to work do you know? How long did you try? DId deipruis try to help using Instant Messaging?

---

### Post by pfwd.tech on 2007-06-04
I was getting help from this thread regarding my belkin [http://ubuntuforums.org/showthread.php?t=453832&page=2](http://ubuntuforums.org/showthread.php?t=453832&page=2)
I got about as far as i am with the Belkin as i have with the Edimax. apart from the iwconfig messages. I will try all the suggestions when i get back from work later. This is now the 3rd week into trying to get my wireless working. Thanks for the reply

---

### Post by pfwd.tech on 2007-06-04
Humm check this out
```
pete@pfwd:~$ sudo find -iname "rt73.ko"
./rt73-cvs-2006123101/Module/rt73.ko
pete@pfwd:~$ sudo find -iname "rt73.bin"
./rt73-cvs-2006123101/Module/rt73.bin
./rt73-cvs-2007052916/Module/rt73.bin
```

maybe its best if i get rid of them all and start again

---

### Post by Austin_KW on 2007-06-04
> **pfwd.tech said:**
> Humm check this out
```
pete@pfwd:~$ sudo find -iname "rt73.ko"
./rt73-cvs-2006123101/Module/rt73.ko
pete@pfwd:~$ sudo find -iname "rt73.bin"
./rt73-cvs-2006123101/Module/rt73.bin
./rt73-cvs-2007052916/Module/rt73.bin
```

maybe its best if i get rid of them all and start again

Pop the cover off the dongle and verify the chipset (a fingernail should do it) , is it an rt2571 of some variety? They have a habit of changing the chipset without changing the usb ids.

---

### Post by pfwd.tech on 2007-06-04
its an rt2571wf

---

### Post by pfwd.tech on 2007-06-04
I have removed the above files and are using the ones in the usr/src folder(ithink)
im still getting this:
```
pete@pfwd:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     RT73 WLAN  ESSID:"blackbox"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
          Link Quality=0/100  Signal level:-36 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by pfwd.tech on 2007-06-04
Could this be something!

> There is already a pid file /var/run/dhclient.pid with pid 8099
killed old client process, removed PID file
pete@pfwd:~$ sudo dhclient wlan1
There is already a pid file /var/run/dhclient.pid with pid 8099
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan1/00:0e:2e:c6:c3:80
Sending on   LPF/wlan1/00:0e:2e:c6:c3:80
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Abadaar on 2007-06-04
> **pfwd.tech said:**
> Humm check this out
```
pete@pfwd:~$ sudo find -iname "rt73.ko"
./rt73-cvs-2006123101/Module/rt73.ko
pete@pfwd:~$ sudo find -iname "rt73.bin"
./rt73-cvs-2006123101/Module/rt73.bin
./rt73-cvs-2007052916/Module/rt73.bin
```

maybe its best if i get rid of them all and start again

Test this first:
```

sudo slocate -u
slocate rt73.ko
slocate rt73.bin
```
and post the output.

---

### Post by pfwd.tech on 2007-06-04
pete@pfwd:~$ slocate rt73.ko
/lib/modules/2.6.20-16-generic/extra/rt73.ko
/root/ralink/rt73-cvs-2006123101/Module/.rt73.ko.cmd
/root/ralink/rt73-cvs-2006123101/Module/rt73.ko
/usr/src/rt73-cvs-2007060313/Module/.rt73.ko.cmd
/usr/src/rt73-cvs-2007060313/Module/rt73.ko
pete@pfwd:~$ slocate rt73.bin
/lib/firmware/rt73.bin
/lib/firmware/2.6.20-15-generic/rt73.bin
/lib/firmware/2.6.20-16-generic/rt73.bin
/root/ralink/rt73-cvs-2006123101/Module/rt73.bin
/usr/src/rt73-cvs-2007060313/Module/rt73.bin
pete@pfwd:~$ 

Is the 2006123101 conflicting?

---

### Post by Abadaar on 2007-06-04
> **pfwd.tech said:**
> pete@pfwd:~$ slocate rt73.ko
/lib/modules/2.6.20-16-generic/extra/rt73.ko
/root/ralink/rt73-cvs-2006123101/Module/.rt73.ko.cmd
/root/ralink/rt73-cvs-2006123101/Module/rt73.ko
/usr/src/rt73-cvs-2007060313/Module/.rt73.ko.cmd
/usr/src/rt73-cvs-2007060313/Module/rt73.ko
pete@pfwd:~$ slocate rt73.bin
/lib/firmware/rt73.bin
/lib/firmware/2.6.20-15-generic/rt73.bin
/lib/firmware/2.6.20-16-generic/rt73.bin
/root/ralink/rt73-cvs-2006123101/Module/rt73.bin
/usr/src/rt73-cvs-2007060313/Module/rt73.bin
pete@pfwd:~$ 

Is the 2006123101 conflicting?

You seem to have several firmware versions installed at the same time, (re)move:
/lib/modules/2.6.20-16-generic/extra/rt73.ko
/lib/firmware/rt73.bin
/lib/firmware/2.6.20-15-generic/rt73.bin
/lib/firmware/2.6.20-16-generic/rt73.bin

and start from the beginning of the HOWTO again. That should do it! :)

---

### Post by pfwd.tech on 2007-06-04
Ok im posting this to show you want i have done in case this screws up again:
```
pete@pfwd:~$ sudo rm -r /lib/modules/2.6.20-16-generic/extra/rt73.ko 
Password:
pete@pfwd:~$ sudo rm -r /lib/firmware/rt73.bin 
pete@pfwd:~$ sudo rm -r /lib/firmware/2.6.20-15-generic/rt73.bin 
pete@pfwd:~$ sudo rm -r /lib/firmware/2.6.20-16-generic/rt73.bin 

```

---

### Post by pfwd.tech on 2007-06-04
still no luck
```
pete@pfwd:/usr/src/rt73-cvs-2007060413/Module$ sudo dhclient wlan1
There is already a pid file /var/run/dhclient.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:0e:2e:c6:c3:80
Sending on   LPF/wlan1/00:0e:2e:c6:c3:80
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
pete@pfwd:/usr/src/rt73-cvs-2007060413/Module$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     No scan results

```

---

### Post by pfwd.tech on 2007-06-04
EDIT -> network is up now but i still cant get to it :
```
pete@pfwd:/usr/src/rt73-cvs-2007060413/Module$ iwlist scanlo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:11:50:93:34:8E
                    ESSID:"blackbox"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Bit Rates:0 kb/s

```

---

### Post by pfwd.tech on 2007-06-04
Ive just tried ifup/down: heres what i get:
```
pete@pfwd:/usr/src/rt73-cvs-2007060413/Module$ sudo ifdown wlan1
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan1.pid with pid 5847
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:0e:2e:c6:c3:80
Sending on   LPF/wlan1/00:0e:2e:c6:c3:80
Sending on   Socket/fallback
pete@pfwd:/usr/src/rt73-cvs-2007060413/Module$ sudo ifup wlan1
There is already a pid file /var/run/dhclient.wlan1.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:0e:2e:c6:c3:80
Sending on   LPF/wlan1/00:0e:2e:c6:c3:80
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
pete@pfwd:/usr/src/rt73-cvs-2007060413/Module$ 
```

i take it this isnt a good sign?
```
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan1.pid with pid 5847
killed old client process, removed PID file
```

should i do th bit under > If the instructions above did work for you, here's what you can do to make the interface be brought up automatically across reboots:
its just last time i removed the network manager i was stuck and had to reinstall

---

### Post by Abadaar on 2007-06-04
> **pfwd.tech said:**
> Ive just tried ifup/down: heres what i get:
```
pete@pfwd:/usr/src/rt73-cvs-2007060413/Module$ sudo ifdown wlan1
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan1.pid with pid 5847
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:0e:2e:c6:c3:80
Sending on   LPF/wlan1/00:0e:2e:c6:c3:80
Sending on   Socket/fallback
pete@pfwd:/usr/src/rt73-cvs-2007060413/Module$ sudo ifup wlan1
There is already a pid file /var/run/dhclient.wlan1.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:0e:2e:c6:c3:80
Sending on   LPF/wlan1/00:0e:2e:c6:c3:80
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
pete@pfwd:/usr/src/rt73-cvs-2007060413/Module$ 
```

i take it this isnt a good sign?
```
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan1.pid with pid 5847
killed old client process, removed PID file
```

should i do th bit under 
its just last time i removed the network manager i was stuck and had to reinstall

Hmm, I don't have network-manager on my box (I don't need it). If you start synaptic and remove network-manager and network-manager-gnome it should not be any problems. It might be in the way, hindering the dhcpstuff or something.

---

### Post by pfwd.tech on 2007-06-04
last time i did that i couldn't get on the net using the cable.  but i will give it ago

---

### Post by Abadaar on 2007-06-04
> **pfwd.tech said:**
> last time i did that i couldn't get on the net using the cable.  but i will give it ago

Well if you need it for the cable, you can just kill nm-applet, NetworkManager and NetworkManagerDispatcher when you try to connect with the wireless... Or you could config the cable connection with the System->Administration->Network tool. Uncheck roaming mode and enter the info and save. It will write the config to /etc/network/interfaces.

---

### Post by pfwd.tech on 2007-06-04
It seem that i can use the cable without network manager now.  I couldn't before the restart tho.
I still cant get any wireless working.  This is really starting to get on my nerves.  Is there anything else i could do or check?

---

### Post by Abadaar on 2007-06-04
Attaching:
/etc/modprobe.d/aliases
/etc/modprobe.d/blacklist
/etc/network/interfaces

This is for a network with WPAPSK-TKIP security.

---

### Post by pfwd.tech on 2007-06-04
Cool thanks will have a look , im using wep but i will look and see if i can find anything out of place

---

### Post by pfwd.tech on 2007-06-04
From first glance i dont have the wlan* in the   /etc/modprobe.d/aliases

---

### Post by pfwd.tech on 2007-06-04
Still cant do it
Some outputs:
interfaces
```
auto eth0
iface eth0 inet dhcp
address 192.168.2.5
netmask 255.255.255.0
gateway 192.168.2.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto rausb0
iface rausb0 inet dhcp

auto wlan1
iface wlan1 inet dhc
```Does it have to be wlan1 i see every one either has rausb0 or wlan0 what gives?
I added ```
alias wlan* rt73
``` to the aliases
Blacklist
```
# Blacklist rt73usb, as it is a non-functional beta module which conflicts with the working rt73 module.
blacklist rt73usb
# Blacklist rt2570, as it causes conflicts with rt73
blacklist rt2570
# Other modules that break rt73
blacklist rt2500usb
blacklist rt2x00lib
```Searching for the file that you asked me to do before:
```
slopete@pfwd:~$ slocate rt73.ko
/lib/modules/2.6.20-16-generic/extra/rt73.ko
/root/ralink/rt73-cvs-2006123101/Module/.rt73.ko.cmd
/root/ralink/rt73-cvs-2006123101/Module/rt73.ko
/usr/src/rt73-cvs-2007060413/Module/.rt73.ko.cmd
/usr/src/rt73-cvs-2007060413/Module/rt73.ko
/usr/src/rt73-cvs-2007060313/Module/.rt73.ko.cmd
/usr/src/rt73-cvs-2007060313/Module/rt73.ko
pete@pfwd:~$ slocate rt73.bin
/lib/firmware/rt73.bin
/root/ralink/rt73-cvs-2006123101/Module/rt73.bin
/usr/src/rt73-cvs-2007060413/Module/rt73.bin
/usr/src/rt73-cvs-2007060313/Module/rt73.bin
```The root/ralink files are from the Edimax CD .....
Any ideas.  Sorry for being such a pain but i really need to get this going.  Thanks for everyones help.
Im going to bed, will check the thread at work and play some more next evening. Thanks again

EDIT-> Just thought when i ran this 
sudo modprobe -v rt73
Nothing happened it just went to a new line.  Is that ok?  Pulling ideas out of the air here lol

---

### Post by Abadaar on 2007-06-04
> **pfwd.tech said:**
> 
Does it have to be wlan1 i see every one either has rausb0 or wlan0 what gives?

wlan1 should be correct.
> **pfwd.tech said:**
> 
I added ```
alias wlan* rt73
``` to the aliases

Good.
> **pfwd.tech said:**
> 
Blacklist
```
# Blacklist rt73usb, as it is a non-functional beta module which conflicts with the working rt73 module.
blacklist rt73usb
# Blacklist rt2570, as it causes conflicts with rt73
blacklist rt2570
# Other modules that break rt73
blacklist rt2500usb
blacklist rt2x00lib
```

Looks alright.
> **pfwd.tech said:**
> 
Searching for the file that you asked me to do before:
```
slopete@pfwd:~$ slocate rt73.ko
/lib/modules/2.6.20-16-generic/extra/rt73.ko
/root/ralink/rt73-cvs-2006123101/Module/.rt73.ko.cmd
/root/ralink/rt73-cvs-2006123101/Module/rt73.ko
/usr/src/rt73-cvs-2007060413/Module/.rt73.ko.cmd
/usr/src/rt73-cvs-2007060413/Module/rt73.ko
/usr/src/rt73-cvs-2007060313/Module/.rt73.ko.cmd
/usr/src/rt73-cvs-2007060313/Module/rt73.ko
pete@pfwd:~$ slocate rt73.bin
/lib/firmware/rt73.bin
/root/ralink/rt73-cvs-2006123101/Module/rt73.bin
/usr/src/rt73-cvs-2007060413/Module/rt73.bin
/usr/src/rt73-cvs-2007060313/Module/rt73.bin
```

That's how it should be. Only one rt73.ko in /lib/modules/... and only one rt73.ko in /lib/firmware/...
> **pfwd.tech said:**
> 
EDIT-> Just thought when i ran this 
sudo modprobe -v rt73
Nothing happened it just went to a new line.  Is that ok?  Pulling ideas out of the air here lol


It's ok, that means it is already loaded.

If you have another computer available, you can try to install the device on it instead.

I can't think of anything else.

---

### Post by Austin_KW on 2007-06-04
pfwd.tech,

What is the output from lsmod, it still could be competing drivers.

Also couple of thing to try,
Turn off all encryption at your access point, generally a good idea when first debugging wireless problems.

Allow the system to boot and stabilize, Then insert the usb module & check "dmesg" for errors resetting/ failing to stabilise/ loading firmware. You may need a manual "sudo ifup --f wlan1"

You might also try different usb ports or maybe a powered hub if you have one available, some of these usb adapters are either using very cheap interfaces or are borderline spec compliant.

---

### Post by diepruis on 2007-06-05
> **pfwd.tech said:**
> Any ideas.  Sorry for being such a pain but i really need to get this going.  Thanks for everyones help.
Im going to bed, will check the thread at work and play some more next evening. Thanks again

The fact that both USB devices failed to work for you might point to a common problem, maybe there's something going wrong with the hub?

---

### Post by pfwd.tech on 2007-06-05
> **Austin_KW said:**
> pfwd.tech,

What is the output from lsmod, it still could be competing drivers.


lsmod
```
Module                  Size  Used by
binfmt_misc            14604  1 
rfcomm                 45352  0 
l2cap                  28160  5 rfcomm
bluetooth              62340  4 rfcomm,l2cap
fglrx                 623096  11 
ppdev                  11272  0 
acpi_cpufreq           10760  0 
cpufreq_powersave       3072  0 
cpufreq_ondemand       10640  2 
cpufreq_userspace       6176  0 
cpufreq_stats           8416  0 
freq_table              6336  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     9736  0 
dev_acpi               17028  0 
pcc_acpi               15616  0 
tc1100_wmi              9224  0 
sony_acpi               7064  0 
button                 10016  0 
asus_acpi              19756  0 
backlight               8448  1 asus_acpi
battery                12040  0 
container               6144  0 
ac                      6920  0 
sbs                    17856  0 
i2c_ec                  6912  1 sbs
i2c_core               26496  1 i2c_ec
dock                   11992  0 
video                  19080  0 
ipv6                  307456  14 
lp                     15048  0 
fuse                   51888  0 
snd_hda_intel          24224  1 
snd_hda_codec         262528  1 snd_hda_intel
snd_pcm_oss            49536  0 
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
snd_seq_midi           11008  0 
snd_rawmidi            29696  1 snd_seq_midi
af_packet              27020  8 
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rt73                  226048  0 
usbhid                 29088  0 
snd                    68904  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hid                    34048  1 usbhid
pcspkr                  4736  0 
parport_pc             40104  1 
parport                43404  3 ppdev,lp,parport_pc
soundcore              10272  1 snd
snd_page_alloc         11792  2 snd_hda_intel,snd_pcm
serio_raw               9092  0 
psmouse                43536  0 
shpchp                 37404  0 
pci_hotplug            36228  1 shpchp
iTCO_wdt               13648  0 
iTCO_vendor_support     5636  1 iTCO_wdt
intel_agp              29504  1 
evdev                  13056  4 
tsdev                  10112  0 
ext3                  143760  1 
jbd                    68208  1 ext3
mbcache                11400  1 ext3
sd_mod                 25092  3 
sg                     40616  0 
sr_mod                 18980  0 
cdrom                  40744  1 sr_mod
ata_generic            10628  0 
pata_jmicron            9088  2 
ehci_hcd               37004  0 
uhci_hcd               28320  0 
ahci                   25348  0 
r8169                  35720  0 
floppy                 67944  0 
ata_piix               17412  0 
libata                137000  4 ata_generic,pata_jmicron,ahci,ata_piix
scsi_mod              166968  4 sd_mod,sg,sr_mod,libata
generic                 6532  0 [permanent]
usbcore               154416  5 rt73,usbhid,ehci_hcd,uhci_hcd
thermal                16912  0 
processor              34952  2 acpi_cpufreq,thermal
fan                     6536  0 
fbcon                  44416  0 
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit
vesafb                 10376  0 
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
capability              7048  0 
commoncap               9472  1 capability
```is this a problem:
>  rt73                  226048  0 
Testing without encryption now

---

### Post by pfwd.tech on 2007-06-05
I GOT THE NET I GOT THE NET I GOT THE NET!!!!!!!!!!!!!!!
its unsecure but i got it!! Awsome

What i did. 
- Restored the Belkin Router Back to factory setting (Default ssid, no key or port forwarding)
- Rebooted the system without the usb stick in place.
- Changed the usb socket to the next one along typed in the following:
```
pete@pfwd:~$ sudo ifconfig wlan1 up
pete@pfwd:~$ sudo iwconfig wlan1 essid "belkin54g"
pete@pfwd:~$ sudo iwconfig wlan1 key "off"
pete@pfwd:~$ sudo dhclient wlan1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:0e:2e:c6:c3:80
Sending on   LPF/wlan1/00:0e:2e:c6:c3:80
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan1 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.2 -- renewal in 2147483648 seconds.
```

I will try it again tonight with the key on etc.. and report back.
Thanks everyone for all the help.  I have learnt a great deal of Linux command lines and a load about my wireless.  Thanks again.
PFWD.TECH

---

### Post by diepruis on 2007-06-05
> **pfwd.tech said:**
> I will try it again tonight with the key on etc.. and report back.
Thanks everyone for all the help.  I have learnt a great deal of Linux command lines and a load about my wireless.  Thanks again.
PFWD.TECH

You'd be surprised by the utterly (apparent) random nature of these things.

---

### Post by alexrb on 2007-06-05
> **diepruis said:**
> Ditto, that's all I can think of.

i guess the problem is in the usb stick. it's switched permanently. So I'll try to switch it off. Make ifconfig and iwconfig and then out it on the place.

i'll try later today or tomorrow morning and post the result.

---

### Post by pfwd.tech on 2007-06-05
Aghhh just came in from work to try it all out and its not working.
This is the output of an un-encrypted attempt
I get the same when i put the encription on
```
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:11:50:93:34:8E
                    ESSID:"belkin54g"
                    Mode:Managed
                    Channel:11
                    Encryption key:off
                    Bit Rates:0 kb/s

pete@pfwd:~$ sudo ifconfig wlan1 up
pete@pfwd:~$ sudo iwconfig wlan1 essid "belkin54g"
pete@pfwd:~$ sudo iwconfig wlan1 key "off"
pete@pfwd:~$ sudo dhclient wlan1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:0e:2e:c6:c3:80
Sending on   LPF/wlan1/00:0e:2e:c6:c3:80
Sending on   Socket/fallback
DHCPREQUEST on wlan1 to 255.255.255.255 port 67
DHCPREQUEST on wlan1 to 255.255.255.255 port 67
DHCPREQUEST on wlan1 to 255.255.255.255 port 67
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
Trying recorded lease 192.168.2.2
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persiste
```

any ideas why its decided not to work again.

---

### Post by pfwd.tech on 2007-06-05
Before i tired the connection tonight, i added the 32bit flash player using ndiswrapper
i got the installation script from here:
[http://ubuntuforums.org/showthread.php?t=425672&highlight=flash](http://ubuntuforums.org/showthread.php?t=425672&highlight=flash)
Could this be the problem?

---

### Post by pfwd.tech on 2007-06-05
[B]Please forget the above two posts i have discovered that i can access the wireless but only when the router is rest to factory settings!
<=                                                                                                                                                                                        =>[/B]
Ive been playing with the encription and the essid all night and it appears that when i set the router to factory default settings (default essid name, no encryption etc...) and rest the router for a few minutes the wireless works perfectly.  
Its only when i restore the settings on the router and change the wireless criteria  in iwconfig  for the essid and the key that it goes tits up.

is there any limitations that i need to know about how to secure the network?
The essid currently is two words both starting in capitals.  Is this an issue?
i have a 128bit wep encryption key which is generated by a word and two numbers (passpharse) is this a problem? should i put this down to 64bit?

I'm convinced i can get this working because it works when all the settings are stripped and the router is reset.  I just need to work out what i can do to get it secure and to access it.

Any ideas would be great many thanks

---

### Post by Austin_KW on 2007-06-05
Some of these things are a nightmare to get connected. Once connected it works fine but the hard part is getting it connected

When having problems, Remove the adapter then reinsert and reconfigure. If you are configuring using the interfaces file you need to "sudo ifup --f wlan1" when you reinsert.
If you are not configuring using the interfaces file, remove the auto wlanX or it may be changing underneath you.

I have seen SSIDs with spaces, hyphens etc, but I am nearly sure the specification says upto 32 alpha numeric characters  [a..z,A..Z,0..9], so it could cause problems. Mine looks like "AustinsNetwork" rather than "austin's network" And it is case sensitive

I don't think it would matter if you use 64/128 bit wep, except one can be cracked in 1 minute and the other sometimes takes more than 2 minutes to break;)  Use WPA if you value your privacy.

---

### Post by Austin_KW on 2007-06-05
> **pfwd.tech said:**
> ...
i have a 128bit wep encryption key which is generated by a word and two numbers (passpharse) is this a problem? should i put this down to 64bit?...
Silly question, but you are using the key, and not the passphrase used to generate it?

---

### Post by alexrb on 2007-06-06
okay. i've got it working.
almost. at least it starts every time i do some things.
0. deleted everything regarding rausb0 from /etc/network/interfaces 
1. sudo modprobe -rv rt73
2. sudo modprobe -v rt73
3. sudo ifconfig rausb0 up
4. sudo iwconfig rausb0 essid <my essid>
5. sudo iwconfig rausb0 key <my key>
6. dhclient rausb0

So the question is - how to make my life easier? ;)

---

### Post by Austin_KW on 2007-06-06
If only that sequence will work (remove & installing the driver), I suggest that you add the commands to /etc/rc.local (before the exit) 

rc.local is for local configuration and is run at the end of the boot sequence. You do not need to sudo the commands in rc.local as it is run in the root's context.

---

### Post by diepruis on 2007-06-06
> **alexrb said:**
> okay. i've got it working.
almost. at least it starts every time i do some things.
0. deleted everything regarding rausb0 from /etc/network/interfaces 
1. sudo modprobe -rv rt73
2. sudo modprobe -v rt73
3. sudo ifconfig rausb0 up
4. sudo iwconfig rausb0 essid <my essid>
5. sudo iwconfig rausb0 key <my key>
6. dhclient rausb0

So the question is - how to make my life easier? ;)

Just put the right instructions into /etc/network/interfaces and it **should** come up on boot. Check the HOWTO for details on how to do this. I see no reason why it should work like that, but fail using the network scripts.

---

### Post by Austin_KW on 2007-06-06
> **diepruis said:**
> Just put the right instructions into /etc/network/interfaces and it **should** come up on boot. Check the HOWTO for details on how to do this. I see no reason why it should work like that, but fail using the network scripts.

Some initialization is done by usbcore, when it probes the USB. Removing and re-installing the rt73 driver forces that init (including firmware load) to happen again.

I guess it could be done with preup/postup directives, I just was not sure what effect removing the driver in the middle of the interface configuration would have. Also rc.local is run towards the end of the boot sequence when hopefully the USB will have settled down.

---

### Post by diepruis on 2007-06-06
> **Austin_KW said:**
> Some initialization is done by usbcore, when it probes the USB. Removing and re-installing the rt73 driver forces that init (including firmware load) to happen again.

I guess it could be done with preup/postup directives, I just was not sure what effect removing the driver in the middle of the interface configuration would have. Also rc.local is run towards the end of the boot sequence when hopefully the USB will have settled down.

I think that's needlessly complex. It works on one of my local computers without any removing in the interface config. I meant that he should just configure the device like I detailed in the HOWTO.

---

### Post by dannyboy79 on 2007-06-06
jus an FYI, they still haven't fixed it in Gutsy. I am tester
i have a usb wireless adapter, it's the belkin F5D7050
this is what lsusb shows:
Bus 001 Device 003: ID 050d:705a Belkin Components

---

### Post by durfff on 2007-06-07
Woohoo!!!!!

Well well, after trying for a while and miserably noob-like failing, I think I've managed to get it working... I've been on the net in ubuntu for about 10 minutes now and all seems fine! It only took a clean install of feisty and a follow-up of the instructions on this wonderful thread... I hope it will stay this way when I reboot, if it doesn't there's plenty of talk on here about how to get it back up every time, so I'll give them a go if anything wrong happens...

For anyone's info, I'm running Feisty on an Athlon 2600 XP+, MSI KM4M-L mobo, with 512 RAM and an ATI Radeon 9200 graphics card... Mmmh, I've read a lot of bad stuff about that, next let's try to get that to display at 1280x960!

Ha

Chuffed, thanks diepruis for all the help, and of course everyone else, you've all been great!

Fred

---

### Post by ButteBlues on 2007-06-07
> **dannyboy79 said:**
> jus an FYI, they still haven't fixed it in Gutsy. I am tester
i have a usb wireless adapter, it's the belkin F5D7050
this is what lsusb shows:
Bus 001 Device 003: ID 050d:705a Belkin Components
I can confirm this:

> e$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-6-generic'
  CC [M]  /media/sda1/BACKUP/rt73-cvs-2007053015/Module/rtmp_main.o
  CC [M]  /media/sda1/BACKUP/rt73-cvs-2007053015/Module/mlme.o
  CC [M]  /media/sda1/BACKUP/rt73-cvs-2007053015/Module/connect.o
  CC [M]  /media/sda1/BACKUP/rt73-cvs-2007053015/Module/rtusb_bulk.o
  CC [M]  /media/sda1/BACKUP/rt73-cvs-2007053015/Module/rtusb_io.o
  CC [M]  /media/sda1/BACKUP/rt73-cvs-2007053015/Module/sync.o
  CC [M]  /media/sda1/BACKUP/rt73-cvs-2007053015/Module/assoc.o
  CC [M]  /media/sda1/BACKUP/rt73-cvs-2007053015/Module/auth.o
  CC [M]  /media/sda1/BACKUP/rt73-cvs-2007053015/Module/auth_rsp.o
  CC [M]  /media/sda1/BACKUP/rt73-cvs-2007053015/Module/rtusb_data.o
/media/sda1/BACKUP/rt73-cvs-2007053015/Module/rtusb_data.c: In function &#8216;RTUSBRxPacket&#8217;:
/media/sda1/BACKUP/rt73-cvs-2007053015/Module/rtusb_data.c:1950: error: &#8216;struct sk_buff&#8217; has no member named &#8216;mac&#8217;
make[2]: *** [/media/sda1/BACKUP/rt73-cvs-2007053015/Module/rtusb_data.o] Error 1
make[1]: *** [_module_/media/sda1/BACKUP/rt73-cvs-2007053015/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-6-generic'
*** Module rt73.ko built successfully


Module doesn't work though.

---

### Post by pfwd.tech on 2007-06-08
> **Austin_KW said:**
> Silly question, but you are using the key, and not the passphrase used to generate it?
Yeah im using the key.  Should this be in quotes and should this be in lowercase.  M having another go now

---

### Post by Austin_KW on 2007-06-08
> **pfwd.tech said:**
> Yeah im using the key.  Should this be in quotes and should this be in lowercase.  M having another go now

Been a while since I used WEP, but the key is just a number (hexadecimal) so it will either be 10 or 26 hexadecimal digits (0..9,a..f, A..F) and the case is not important.

---

### Post by dannyboy79 on 2007-06-08
> **ButteBlues said:**
> I can confirm this:



Module doesn't work though.

Wait, are you saying that even after you followed the guide that you can't get your Belkin wireless usb adapter to work? Did you blacklist rt73usb? 

I didn't think the F5D7050 used the rt73, I believe mine uses the rt2xxx. You need to verify the chipset of you adapter as there's like 3 different versions. Not to mention, your make command had 3 different errors:
/media/sda1/BACKUP/rt73-cvs-2007053015/Module/rtusb_data.c:1950: **error**: &#8216;struct sk_buff&#8217; has no member named &#8216;mac&#8217;
make[2]: *** [/media/sda1/BACKUP/rt73-cvs-2007053015/Module/rtusb_data.o] **Error 1**
make[1]: *** [_module_/media/sda1/BACKUP/rt73-cvs-2007053015/Module] **Error 2**

---

### Post by Austin_KW on 2007-06-08
> **dannyboy79 said:**
> Wait, are you saying that even after you followed the guide that you can't get your Belkin wireless usb adapter to work? Did you blacklist rt73usb? 

I didn't think the F5D7050 used the rt73, I believe mine uses the rt2xxx. You need to verify the chipset of you adapter as there's like 3 different versions. Not to mention, your make command had 3 different errors:
/media/sda1/BACKUP/rt73-cvs-2007053015/Module/rtusb_data.c:1950: **error**: ‘struct sk_buff’ has no member named ‘mac’
make[2]: *** [/media/sda1/BACKUP/rt73-cvs-2007053015/Module/rtusb_data.o] **Error 1**
make[1]: *** [_module_/media/sda1/BACKUP/rt73-cvs-2007053015/Module] **Error 2**
The 7050 v300x is rt73

I assume that he is making the point that it does not build with the 2.6.22 headers  in Gutsy. Is this the latest source tarball?

If it is the latest source; The error looks like it is only for for monitor mode, have you tried removing the offending block (line 1882-1964)? Ofcourse you may hit another error later on.

---

### Post by ButteBlues on 2007-06-08
> **Austin_KW said:**
> The 7050 v300x is rt73

I assume that he is making the point that it does not build with the 2.6.22 headers  in Gutsy. Is this the latest source tarball?

If it is the latest source; The error looks like it is only for for monitor mode, have you tried removing the offending block (line 1882-1964)? Ofcourse you may hit another error later on.
I'm confirming that rt73 doesn't build on Gutsy's kernel headers. I personally have a WUSB54GC.

In either case, yes it's latest CVS.

I think the issue comes from Gutsy's kernel having the new wireless stack implemented.

---

### Post by dannyboy79 on 2007-06-08
if they implemented a new wireless stack, why would the rt73 driver work for out wireless chipset's??????? and now we can't even get our wireless adapter's to work in Gutsy so what's left for us to do? Why are these chipsets so hard to include the correct driver????

I sound just like a newbie from winbloz but seriously though, I bought this wireless adapter thinking that it would work. Has anyone got any ideas? Has anyone filled this bug yet??? Please do or I will!

---

### Post by ButteBlues on 2007-06-08
It'll compile fine against older kernels.

I just use the Feisty kernel. Problem solved.

---

### Post by diepruis on 2007-06-08
> **dannyboy79 said:**
> if they implemented a new wireless stack, why would the rt73 driver work for out wireless chipset's??????? and now we can't even get our wireless adapter's to work in Gutsy so what's left for us to do? Why are these chipsets so hard to include the correct driver????

I sound just like a newbie from winbloz but seriously though, I bought this wireless adapter thinking that it would work. Has anyone got any ideas? Has anyone filled this bug yet??? Please do or I will!

I recall something about a new stack being implemented for rt2x00. We might have to switch to that driver if the kernel breakage continues.

---

### Post by lunarmelody on 2007-06-10
I have an odd question.  I tried this out, but it died when it asked for my key (sudo iwconfig wlan1 key ...).  I get the following error:
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan1 ; Invalid argument.

I know I'm typing it correctly, and I've tried both the ascii and hex versions.  Any ideas?  Thanks!

PS My network is WPA2, hidden.

---

### Post by diepruis on 2007-06-10
> **lunarmelody said:**
> I have an odd question.  I tried this out, but it died when it asked for my key (sudo iwconfig wlan1 key ...).  I get the following error:
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan1 ; Invalid argument.

I know I'm typing it correctly, and I've tried both the ascii and hex versions.  Any ideas?  Thanks!

PS My network is WPA2, hidden.

That sounds like a failure in the driver. Output from
```

dmesg | grep RT73
dmesg | grep rt73

```
will help to diagnose the problem. Please post it.

---

### Post by Austin_KW on 2007-06-10
> **lunarmelody said:**
> I have an odd question.  I tried this out, but it died when it asked for my key (sudo iwconfig wlan1 key ...).  I get the following error:
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan1 ; Invalid argument.

I know I'm typing it correctly, and I've tried both the ascii and hex versions.  Any ideas?  Thanks!

PS My network is WPA2, hidden.

WPA key is set using iwpriv commands not iwconfig
Hiding you SSID only causes problems and has no security value.

---

### Post by lunarmelody on 2007-06-10
demesg | grep RT73 returns nothing, but:
 ```
 dmesg | grep rt73
[   14.808101] usbcore: registered new interface driver rt73
```

---

### Post by lunarmelody on 2007-06-10
> **Austin_KW said:**
> WPA key is set using iwpriv commands not iwconfig
Hiding you SSID only causes problems and has no security value.

Alrighty, I went back and tried the tutorial again, this time using the iwpriv commands instead of iwconfig for setting the key.  Then I tried using the dhclient to get an IP address.  Here's the output I get:
```
christina@Thianzyn:~$ sudo dhclient wlan1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:1a:70:2f:4d:2d
Sending on   LPF/wlan1/00:1a:70:2f:4d:2d
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping
```.

It seems like it's not connecting to the access point.  If I run "iwlist scan", it finds my network, so I don't think I'm having a problem with it being hidden.  Any ideas?  Thanks!

---

### Post by Austin_KW on 2007-06-10
> **lunarmelody said:**
> ...

It seems like it's not connecting to the access point.  If I run "iwlist scan", it finds my network, so I don't think I'm having a problem with it being hidden.  Any ideas?  Thanks!

If you have it hidden, scan will not find it, are you sure it is your network.

you might also try reducing your security to WPA or removing encryption entirely until you resolve the connection issues.

Also make sure that you follow the howto order, and set the ssid, encryption type, authorization type and the PSK. The driver will need all this info to generate the actual encryption key.

---

### Post by monomaniacpat on 2007-06-10
Would it be possible to use this tutorial for other Ralink, specifically RT8180 (also serialmonkey) to set up WPA?

I have tried using it, but I get an error upon restarting networking.

```
Invalid command : set
Failed to bring up wlan0
```

This set of commands was also suggested by the WPA tutorial, so I think it should work for other serialmonkey drivers.

BTW, I am using Dapper.

---

### Post by diepruis on 2007-06-10
> **monomaniacpat said:**
> Would it be possible to use this tutorial for other Ralink, specifically RT8180 (also serialmonkey) to set up WPA?

I have tried using it, but I get an error upon restarting networking.

```
Invalid command : set
Failed to bring up wlan0
```

This set of commands was also suggested by the WPA tutorial, so I think it should work for other serialmonkey drivers.

BTW, I am using Dapper.

RT8180 is a Realtek chipset, not a RaLink one. Therefore you can expect differences with this driver, although there will also be similiarities. I don't know that driver, though, so I can't really answer your question.

---

### Post by lunarmelody on 2007-06-10
All right, I found my error.  Turns out my roommate (who set up the router) used different security settings than she told me she did.  The big one was using AES instead of TKIP.  Changing the settings on the router to use TKIP fixed the problems.  Thanks for the help though!

---

### Post by monomaniacpat on 2007-06-10
> **diepruis said:**
> RT8180 is a Realtek chipset, not a RaLink one. Therefore you can expect differences with this driver, although there will also be similiarities. I don't know that driver, though, so I can't really answer your question.

Ah bugger, thanks for pointing that out.

---

### Post by dannyboy79 on 2007-06-12
> **Austin_KW said:**
> WPA key is set using iwpriv commands not iwconfig
Hiding you SSID only causes problems and has no security value.

hiding your ESSID may not have any security benefits IF you're using WPA BUT if you're using WEP than anyone who is looking for an access point will see your ESSID since you're broadcasting it and then they can attempt to crack it. So I only agree with your statement IF you would have been more clear. People with older hardware can't use WPA, I have a pretty old Netgear WGR624 and although it says (i believe it does anyway) that it supports WPA no matter what I do I can't find that option, I only have WEP 64 and 128 bit. They don't even sell the model I have anymore, they sell it under a different name (WGT624 and WGT624SC) so it's possible that I could apply the firmware for that one to mine but I am not about to risk that as my router is serving me just fine for the last ton of years. (i know that last statement is weird, I don't know how many years I've had it)

---

### Post by Austin_KW on 2007-06-12
> **dannyboy79 said:**
> hiding your ESSID may not have any security benefits IF you're using WPA BUT if you're using WEP than anyone who is looking for an access point will see your ESSID since you're broadcasting it and then they can attempt to crack it. So I only agree with your statement IF you would have been more clear. People with older hardware can't use WPA, ...


Even if you are using WEP,  your client is broadcasting the SSID in the clear. You are only hiding the SSID from people who would not know how to crack your network. Hiding SSID for security is a myth that refuses to die.

---

### Post by dannyboy79 on 2007-06-12
> **Austin_KW said:**
> Even if you are using WEP,  your client is broadcasting the SSID in the clear. You are only hiding the SSID from people who would not know how to crack your network. Hiding SSID for security is a myth that refuses to die.

so you're saying that the setting within my router configuration that states, broadcast SSID "yes" or "no" and then making sure it states "no" isn't preventing someone from being able to sniff my SSID out of the air????? I can tell you for sure that my roommates windows machine when scanning for SSID's it didn't see mine so it appears to work??  I don't know about what you say and until I try myself with SNORT or similar I have to refuse to believe that.

---

### Post by Austin_KW on 2007-06-12
> **dannyboy79 said:**
> so you're saying that the setting within my router configuration that states, broadcast SSID "yes" or "no" and then making sure it states "no" isn't preventing someone from being able to sniff my SSID out of the air????? I can tell you for sure that my roommates windows machine when scanning for SSID's it didn't see mine so it appears to work??  I don't know about what you say and until I try myself with SNORT or similar I have to refuse to believe that.

Yes you are hiding only one method of SSID broadcast (in the beacon frames)

When you try to connect to your WLAN you send a 'probe request' with the SSID
the hidden AP responds with a 'probe response'
When you then associate you include the SSID in the packet.
If I cannot detect the above exchange I can send a disassociate request, pretending to be the AP and you will go through the the association process again, exposing your SSID.

If you use your wireless network, you are exposing your SSID.

---

### Post by dannyboy79 on 2007-06-12
explain one more time how if you don't know there's a wifi ap there, why you would be sitting there waiting for a probe response to be sent into the air or whatever it is your trying to say. I find this very interesting and should try it. Can you just use available tools to send a disassociate request to any AP within ear shot or what?

---

### Post by durfff on 2007-06-15
I dunno if I've posted on here after my success but I've got my D-LINK g122 rev c1 working, and it's working quite good I may say...

I have a link quality of around 70% (not great but compared to 24% in windows...), the only problem is that it sometimes drops, nothing a quick ifdown-ifup can't sort though. Actually, I find if I just ifup (no ifdown) it reconnects faster and somewhat better... If anyone wants some more info on this let me know I'll let you know what I've done!

(also got me old trusty ATI radeon 9200 SE to work proper, beryl/compiz and movies at 1280x960 not a problem, chuffed, that's all I need)

The only question is: how hard would it be to find an executable script that would get info from terminal, about signal strength, speed, etc... ? Or maybe to write it... How do I start writing little appz on ubuntu? I'm dead excited about it, loving it :)

CHeers to all who helped, on this forum or another

---

### Post by stansford on 2007-06-15
Hi,
Thought I'd post and let you know that thanks to the efforts of many on this thread I am surfing using WPA on Feisty 7.04 via this EDIMAX USB dongle (model 7318UG - using the Ralink RT73 drivers). Here's exactly what I did. (Note this was put together from others posts and any other info that I found helped):

1. sudo rmmod rt73usb (remove old drivers)
2. sudo gedit /etc/modprobe.d/blacklist (add the following lines at the end of the file):
blacklist rt73usb
blacklist rt2570
blacklist rt2x00lib
3.sudo apt-get install build-essential
4.sudo apt-get install linux-headers-`uname –r`
5.get the latest version of the driver source from the serialmonkey site. The name is rt73-cvs-daily.tar.gz. I saved it in /usr/src.
6.sudo wget [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) -O /usr/src/rt73-cvs-daily.tar.gz
7.sudo tar -zxvf rt73-cvs-daily.tar.gz
8.cd /usr/src/rt73*/Module
9.sudo make
10.strip –S rt73.ko (if it’s 2Mb instead of 250Kb ish)
11.sudo make install
12.sudo modprobe rt73
13.edit /etc/modules – add the text rt73 at the end
14.create text file called rt73 in /etc/modprobe.d
15.put the text “alias wlan1 rt73” in this file
16.remove /etc/modprobe.conf as it’s no longer needed
17.add the following to /etc/network/interfaces:
auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid "yourESSID"
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set Channel=11
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="your key"
18.reboot/restart network

Hope this helps you get the old wireless up and running
Oh another thing: if you want a link monitor I rate **rutilt** - it works a treat with ralink stuff and you can set it to run minimized at startup which gives you a nice little transmitter logo next to the clock

---

### Post by dannyboy79 on 2007-06-15
> **stansford said:**
> Hi,
Thought I'd post and let you know that thanks to the efforts of many on this thread I am surfing using WPA on Feisty 7.04 via this EDIMAX USB dongle (model 7318UG - using the Ralink RT73 drivers). Here's exactly what I did. (Note this was put together from others posts and any other info that I found helped):

1. sudo rmmod rt73usb (remove old drivers)
2. sudo gedit /etc/modprobe.d/blacklist (add the following lines at the end of the file):
blacklist rt73usb
blacklist rt2570
blacklist rt2x00lib
3.sudo apt-get install build-essential
4.sudo apt-get install linux-headers-`uname &#8211;r`
5.get the latest version of the driver source from the serialmonkey site. The name is rt73-cvs-daily.tar.gz. I saved it in /usr/src.
6.sudo wget [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) -O /usr/src/rt73-cvs-daily.tar.gz
7.sudo tar -zxvf rt73-cvs-daily.tar.gz
8.cd /usr/src/rt73*/Module
9.sudo make
10.strip &#8211;S rt73.ko (if it&#8217;s 2Mb instead of 250Kb ish)
11.sudo make install
12.sudo modprobe rt73
13.edit /etc/modules &#8211; add the text rt73 at the end
14.create text file called rt73 in /etc/modprobe.d
15.put the text &#8220;alias wlan1 rt73&#8221; in this file
16.remove /etc/modprobe.conf as it&#8217;s no longer needed
17.add the following to /etc/network/interfaces:
auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid "yourESSID"
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set Channel=11
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="your key"
18.reboot/restart network

Hope this helps you get the old wireless up and running
Oh another thing: if you want a link monitor I rate **rutilt** - it works a treat with ralink stuff and you can set it to run minimized at startup which gives you a nice little transmitter logo next to the clock
may I ask what the reason for putting the wlan1 alias if then in your interfaces file you put wlan0?? Also, I thought modprobe.conf is used for other stuff, so are sure removing it safe for EVERYONE? 

Thanks a lot for posting this as it a very clear guide of how some1 got this working! Great addition to original post. Maybe you could PM the author of the thread and ask him to edit the first page and put this at the bottom kind of like a, user's successful attempt thing, that way people see it instead of having to read thru 32 pages.

---

### Post by dannyboy79 on 2007-06-15
> **durfff said:**
> 
The only question is: how hard would it be to find an executable script that would get info from terminal, about signal strength, speed, etc... ? Or maybe to write it... How do I start writing little appz on ubuntu? I'm dead excited about it, loving it :)

CHeers to all who helped, on this forum or another

Check out the conky thread here: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)
there are many people that have gotten their link quality and speed to show up on their desktop etc etc using conky. I looked into it, but I don't see the point of having all that great info on your desktop when you have windows open, you won't be able to see it, so I use the Gnome Panel applets, they obviously aren't as versatile but I am trying to find out how to somehow write my own (gnome panel applets) and maybe I can copy from the conky configs.

Writing apps, I have looked into this as well, many coders/programmers say that Python is a good start. I have started a python tutorial but I haven't been super serious about it so I am not really getting anywhere and not devoting enough time to it to actually learn yet.

---

### Post by stansford on 2007-06-15
> **dannyboy79 said:**
> may I ask what the reason for putting the wlan1 alias if then in your interfaces file you put wlan0?? Also, I thought modprobe.conf is used for other stuff, so are sure removing it safe for EVERYONE? 

Thanks a lot for posting this as it a very clear guide of how some1 got this working! Great addition to original post. Maybe you could PM the author of the thread and ask him to edit the first page and put this at the bottom kind of like a, user's successful attempt thing, that way people see it instead of having to read thru 32 pages.

Dannyboy,

Opps - the wlan1 entry was a typo - it should have been wlan0. That was funny though I followed this procedure on Edgy and it created a wlan1 driver, but on feisty it was wlan0?? - I thought I'd removed all instances of wlan1, but obviously not! 
Re the modprobe.conf, I don't know if it's safe for everyone. I have to admit I took the deletion of this file on trust because it worked for others. I did however, back it up just in case it all went horribly wrong!

I've got a lot out of these forums in helping to solve problems so I wanted to give a little back by sharing what worked for me. Like you say there is so much info on this thread now, it wouldn't be a bad idea if someone could boil it down to a few methods that people seem to find work....

---

### Post by aldursys on 2007-06-20
Great HOWTO.

The question is - why does it appear so difficult to get this into the kernel stream and the Gusty distribution?

Surely it is not beyond the wit of man to just make Ralink equipment just work.

Anybody know what the fundamental problem is?

NeilW

---

### Post by Austin_KW on 2007-06-20
> **aldursys said:**
> Great HOWTO.

The question is - why does it appear so difficult to get this into the kernel stream and the Gusty distribution?

Surely it is not beyond the wit of man to just make Ralink equipment just work.

Anybody know what the fundamental problem is?

NeilW

The new drivers are trying to hit a moving target, development effort has supposedly moved to the new drivers but there does not seem to be a lot going on. The delay in the new drivers meant that people went back and fixed the old legacy drivers to add smp support etc. 
As I see it, the main problem is that ubuntu ships with the new drivers for rt73, even though they do not work. I don't know why they refuse to ship the working legacy drivers, they ship with the legacy drivers for the rt2500.

---

### Post by amic on 2007-06-20
This HOWTO was absolutely amazing. I'm running Feisty 7.04 (amd64 version) and am connecting to the internet using the wireless usb WUSB54GC from Linksys.

My only problem is that I can't, for the life of me, get this damn thing to connect at boot up. I'm always forced to manually re-enter the iwconfig/iwpriv commands via terminal

Here's what my /etc/network/interfaces looks like:

auto lo
iface lo inet loopback

auto wlan1
iface wlan1 inet dhcp
pre-up ifconfig wlan1 up
pre-up iwconfig wlan1 mode managed
pre-up iwconfig wlan1 essid x
pre-up iwpriv wlan1 set AuthMode=WPAPSK
pre-up iwpriv wlan1 set EncrypType=TKIP
pre-up iwpriv wlan1 set WPAPSK=x

As I mentioned, I always have to open up a terminal and re-enter the above commands (save the "pre-up" prefixes). Often I'll have to do it several times, even after I'm associated to the AP and have an Encryption Key present when I do iwconfig wlan1.

Any help on this would be greatly appreciated

Da5id

---

### Post by Austin_KW on 2007-06-20
I had similar problems using 64 bit. I still have problems where it comes up on boot about 60% of the time for 32 bit.

When you have problems;
Remove the adapter, reinsert and then "sudo ifup --f wlan0"
EDIT; wlan1 for your config
BTW the ifup --f will rerun the preups, might save you a bit of typing when you need to do the commands multiple times.

---

### Post by amic on 2007-06-20
i've been wondering what that command does :)
it'll definitely save me a lot of typing and up-arrow key pressing! haha, thank you for your prompt reply

Da5id

---

### Post by aldursys on 2007-06-21
> **Austin_KW said:**
> 
As I see it, the main problem is that ubuntu ships with the new drivers for rt73, even though they do not work. I don't know why they refuse to ship the working legacy drivers, they ship with the legacy drivers for the rt2500.

So who do we ask? Is there a bug outstanding in Launchpad? Is it a problem with the upstream kernel?

Patching to get working is all very well, but I'd rather it just worked.

NeilW

---

### Post by diepruis on 2007-06-21
> **aldursys said:**
> So who do we ask? Is there a bug outstanding in Launchpad? Is it a problem with the upstream kernel?

Patching to get working is all very well, but I'd rather it just worked.

NeilW

Not sure... Ubuntu now ships with the legacy drivers for RT61, so it can't be an objection to the firmware.

---

### Post by dannyboy79 on 2007-06-21
> **diepruis said:**
> Not sure... Ubuntu now ships with the legacy drivers for RT61, so it can't be an objection to the firmware.

which version is that? Cause my Belkin FD..5070 (not exactly sure what the model number was again, Im not at home) BUT I can gurantee that it still doesn't work in Gutsy Tribe 1.

---

### Post by diepruis on 2007-06-21
> **dannyboy79 said:**
> which version is that? Cause my Belkin FD..5070 (not exactly sure what the model number was again, Im not at home) BUT I can gurantee that it still doesn't work in Gutsy Tribe 1.

I noticed this is Feisty... the default drivers still didn't work though.

---

### Post by kevdog on 2007-06-27
Im trying to help someone setup their wireless interface, and after many posts about ndiswrapper, it turns out later I find he has a RT2500 chipset card.  I personally have no experience with this chipset, but am excited to learn (through him!).  Will this tutorial work for RT2500??  Does anyone know if this card works out of the box -- other posts suggest not!  Is it recommended to uninstall network manager?

Sorry about all these questions but for being so good with ndiswrapper, I really stink with RT's

---

### Post by Austin_KW on 2007-06-27
> **kevdog said:**
> Im trying to help someone setup their wireless interface, and after many posts about ndiswrapper, it turns out later I find he has a RT2500 chipset card.  I personally have no experience with this chipset, but am excited to learn (through him!).  Will this tutorial work for RT2500??  Does anyone know if this card works out of the box -- other posts suggest not!  Is it recommended to uninstall network manager?

Sorry about all these questions but for being so good with ndiswrapper, I really stink with RT's

The rt2500 driver works as shipped in ubuntu. No need to download & build the driver or blacklist any drivers (except maybe ndiswrapper if you installed it). Just replace the howto's wlan0 with ra0 in the /etc/network/interface file and it should work

---

### Post by kevdog on 2007-06-27
I really dont mean to drift off the topic of this forum but thanks for the info. I had him add the following to the interfaces file

auto ra0
iface ra0 inet dhcp

His card detects AP's in the area but does not connect.  In order to use the 2500 drivers do I need to re-write the interfaces file as proposed in the original post on this forum such as (I know substitute ra0 for wlan0)

	pre-up ifconfig wlan0 up
	pre-up iwconfig wlan0 essid YOUR_ESSID
	pre-up iwconfig wlan0 key WEP_KEY_OR_"OFF"_IF_YOU_HAVE_NONE

Do I also need to uninstall network-manager?

Sorry about the drift off topic.

---

### Post by Austin_KW on 2007-06-27
Yes, add the pre-ups for ra0, I don't think you need to remove network manager (unless maybe you tried earlier to configure ra0 using it and it is causing a conflict)

---

### Post by dannyboy79 on 2007-06-27
I have to ask, as many people who are compiling this for fiesty, has anyone used checkinstall to make some .deb's which then can be hosted in various locations for people? I mean, I would be willing to host them. Also, isn't there some free places online to host them? Wouldn't this be easier for those who are having such difficulty compiling this? Any takers?

---

### Post by kevdog on 2007-06-27
If I use this thread to compile the CVS drivers - can I use them as a replacement for the RT2500 drivers.  Im having a hard time getting the built-in ones working.  They can see two separate access points, but in both cases the signal is 0/100.  I think (even though I dont know) this is the reason I can not connect manually to either network.  I thought I would give compiling new drivers a try!

---

### Post by Austin_KW on 2007-06-27
> **kevdog said:**
> If I use this thread to compile the CVS drivers - can I use them as a replacement for the RT2500 drivers.  Im having a hard time getting the built-in ones working.  They can see two separate access points, but in both cases the signal is 0/100.  I think (even though I dont know) this is the reason I can not connect manually to either network.  I thought I would give compiling new drivers a try!

Yes, You can use the same procedure to build the rt2500 driver (or any serialmonkey legacy driver), but there is not a lot of changes. In general if you are having problems connecting, then start by temporarily disabling all encryption.

---

### Post by diepruis on 2007-06-27
> **kevdog said:**
> If I use this thread to compile the CVS drivers - can I use them as a replacement for the RT2500 drivers.  Im having a hard time getting the built-in ones working.  They can see two separate access points, but in both cases the signal is 0/100.  I think (even though I dont know) this is the reason I can not connect manually to either network.  I thought I would give compiling new drivers a try!

You can only use these drivers for RT 73 based devices, so no.

---

### Post by kevdog on 2007-06-27
Diepruis

Obviously you are the master of this thread, however if I look on the serialmonkey website it says the following:
This project is a development effort to provide free, stable and feature rich Linux drivers for wireless 802.11b/g/i cards based on the following Ralink chipsets: rt2400, rt2500, rt2570, rt61 and rt73

You are certain that if I grab the 2500 CVS tarball rather than the rt73 tarball, the installation instructions that you have provided will not work?

---

### Post by diepruis on 2007-06-29
> **kevdog said:**
> Diepruis

Obviously you are the master of this thread, however if I look on the serialmonkey website it says the following:
This project is a development effort to provide free, stable and feature rich Linux drivers for wireless 802.11b/g/i cards based on the following Ralink chipsets: rt2400, rt2500, rt2570, rt61 and rt73

You are certain that if I grab the 2500 CVS tarball rather than the rt73 tarball, the installation instructions that you have provided will not work?

Yes I am.

---

### Post by dannyboy79 on 2007-06-29
> **kevdog said:**
> You are certain that if I grab the 2500 CVS tarball rather than the rt73 tarball, the installation instructions that you have provided will not work?

> **diepruis said:**
>  Yes I am. 

diepruis, I would like to know the answer to his question but I don't think Yes I am really answers it?

Plus no 1 responded to my previous post on the last page. Can anyone comment on this suggestion, "I have to ask, as many people who are compiling this for fiesty, has anyone used checkinstall to make some .deb's which then can be hosted in various locations for people? I mean, I would be willing to host them. Also, isn't there some free places online to host them? Wouldn't this be easier for those who are having such difficulty compiling this? Any takers?"

---

### Post by diepruis on 2007-06-29
> **dannyboy79 said:**
> diepruis, I would like to know the answer to his question but I don't think Yes I am really answers it?

I will elaborate: the person in question suggested using the rt2500 driver for an rt73 card (if I understand correctly). To drive an rt73 card, you need the rt73 driver, since even a minor difference in hardware will cause the drivers to be incompatible.

Detailed enough?

---

### Post by ButteBlues on 2007-06-29
> **diepruis said:**
> I will elaborate: the person in question suggested using the rt2500 driver for an rt73 card (if I understand correctly). To drive an rt73 card, you need the rt73 driver, since even a minor difference in hardware will cause the drivers to be incompatible.

Detailed enough?
He has an rt2500 device for which the built-in drivers do not work.

He wants to know if he can build the rt2500 tarball using the same instructions (or rather close ones) here to build his rt2500 drivers for his rt2500 card.

---

### Post by diepruis on 2007-06-30
> **ButteBlues said:**
> He has an rt2500 device for which the built-in drivers do not work.

He wants to know if he can build the rt2500 tarball using the same instructions (or rather close ones) here to build his rt2500 drivers for his rt2500 card.

Thank you, that makes a lot more sense.

In that case, the answer is that the steps would be similiar. However, I can't tell you where they differ, as I have no experience with rt2500 devices.

---

### Post by lythandrel on 2007-07-01
Try the 1.04.0 or the current CVS drivers... they should work with feisty from what I've heard.  I'll find out tomorrow!!

---

### Post by microsoft92sucks on 2007-07-01
I did all the how to but now I don't know what the device is being called last time on my PC it was called eth1 but now that won't work and the rest of stuff I tried won't work. How can I found out what it's being. Or did I do something wrong somewere please help.

by the way if I put in ```
iwconfig
```
i get ```
lo
eth0
sit0
```
and non of them are getting a signal.

---

### Post by diepruis on 2007-07-01
> **microsoft92sucks said:**
> I did all the how to but now I don't know what the device is being called last time on my PC it was called eth1 but now that won't work and the rest of stuff I tried won't work. How can I found out what it's being. Or did I do something wrong somewere please help.

by the way if I put in ```
iwconfig
```
i get ```
lo
eth0
sit0
```
and non of them are getting a signal.

From that I would guess it's being called eth0 or *maybe* sit0, although that doesn't make any sense from my experiences with the driver.

Are you sure that 
[LIST=1]
[*]you installed  the correct driver,
[*]the device you're using is an rt73 card,
[*]there are no weird aliases in /etc/modprobe.conf or in one of the files under /etc/modprobe.d/
[*] you removed any drivers installed previously in an attempt to make the card work?
[/LIST]

---

### Post by microsoft92sucks on 2007-07-01
> **diepruis said:**
> From that I would guess it's being called eth0 or *maybe* sit0, although that doesn't make any sense from my experiences with the driver.

Are you sure that 
[LIST=1]
[*]you installed  the correct driver,
[*]the device you're using is an rt73 card,
[*]there are no weird aliases in /etc/modprobe.conf or in one of the files under /etc/modprobe.d/
[*] you removed any drivers installed previously in an attempt to make the card work?
[/LIST]
I just reinstalled Ubuntu. And I've used this how before on same PC. And I installed the rt73 CVS driver.      but every time I try step 12 I can't figure out what I'm supposed to put for wlan0 nothing works.

---

### Post by Austin_KW on 2007-07-01
lo is the loopback interface
eth0 is probably your ethernet interface
sit0 is ipv6 interface (encapsulated over ipv4)

is does not look like the rt73 driver is installed,
what is the output of the following commands
lsusb
lsmod

---

### Post by microsoft92sucks on 2007-07-01
> **Austin_KW said:**
> lo is the loopback interface
eth0 is probably your ethernet interface
sit0 is ipv6 interface (encapsulated over ipv4)

is does not look like the rt73 driver is installed,
what is the output of the following commands
lsusb
lsmod

I don't have my hp hooked up to the inernet. so I can't just copy and past the answer but I did know what you were looking for in both thoughs commands. And lsusb command it said there was a Belkin componet and some other stuff. And on the lsmod command I did find rt73.
And one more thing that could be of aportant is the Belkin usb adapter is'ent blinking. But the light is staying green. 
So is there any command that would tell me what it's being called. 
And thank's for all the help so far.

---

### Post by microsoft92sucks on 2007-07-01
I think I may have mest up on step 9
```
sudo ifconfig wlan0 down
sudo modprobe -r rt73usb
sudo modprobe -r rt2570
sudo modprobe -r rt2500usb
sudo modprobe -r rt2x00lib
```
becouse I  put ```
sudo ifconfig eth0 down 
sudo modprobe -r rt73usb
sudo modprobe -r rt2570
sudo modprobe -r rt2500usb
sudo modprobe -r rt2x00lib
```
which I now know was the wrong thing to put is this a big deal. Were should I go from here?

---

### Post by microsoft92sucks on 2007-07-01
I just did a complete reinstall and I'm on step 9 trying to figure out what it's calling the Belkin adepter. How can I figure out what it's being called PLEASE HELP. wlan0 is'ent working it say no such device exist. PLEASE ANY HELP. There has to be a command that would help.

---

### Post by microsoft92sucks on 2007-07-02
Never Mind I got it.

---

### Post by dannyboy79 on 2007-07-02
> **diepruis said:**
> I will elaborate: the person in question suggested using the rt2500 driver for an rt73 card (if I understand correctly). To drive an rt73 card, you need the rt73 driver, since even a minor difference in hardware will cause the drivers to be incompatible.

Detailed enough?
disregard

---

### Post by dannyboy79 on 2007-07-02
> **microsoft92sucks said:**
> Never Mind I got it.
could you possibly elaborate as to HOW you got it. THat way it'll benefit the community in caes other's are having the same issue's you did. That's generally the preferred thing to do instead of creating a new post just to tell us you got it. thank you from myself as well as the community

---

### Post by ButteBlues on 2007-07-02
> **dannyboy79 said:**
> could you possibly elaborate as to HOW you got it. THat way it'll benefit the community in caes other's are having the same issue's you did. That's generally the preferred thing to do instead of creating a new post just to tell us you got it. thank you from myself as well as the community
Just a note, the new drivers will build without patching on Gutsy's kernel (2.6.22 has a new wireless stack), while not breaking backwards compatibility.

---

### Post by durfff on 2007-07-02
For all complete newbies: I don't consider myself as an expert, but I've managed to learn from trial and error. Read EVERYTHING and make sure you understand what you're typing before you do type it. Or at least make sure you have a vague idea - "is this going to compile my kernel or not?" - "It has usb in it, does that mean it lists my PCI cards?" - ask yourself simple questions, if you cannot answer them research the question itself further (google "ubuntu lsusb" and you should manage to find some answers.)

lsusb and lsmod should give you a good idea as to what the devices on your machine are. If not just run ifconfig to see you connections to the net. eth0 is an ethernet connection (usually) and means it connects through a network card via an ethernet cable - shouldn't really matter here. Read the first few posts, they're usually helpful in answering simple questions. It's just a matter of being patient enough to read through boring stuff, then finding the little gem you were looking for.

If you are having to use another machine to get to the internet and read this howto, then I suggest you save th web pages. That's what I did and it helped a lot. Save the web page in a place you can access offline from your ubuntu distro, then launch ubuntu, and look at the pages, try things and you should make some progress. 

Most importantly, don't just type in everything you see; try to put a bit of reasoning into it to understand what it might do. i.e. lsusb lists the usb devices plugged into your computer; ifconfig lists the devices able to connect to the internet; iwconfig lists your wireless devices. 

Just put a bit of thought into it rather than just copy-paste and wonder why it's not working - not a digg, just a bit of advice, it helps greatly and you'll get around any future problem much quicker.

Hope this helps anyway :D

---

### Post by diepruis on 2007-07-03
> **durfff said:**
> For all complete newbies: I don't consider myself as an expert, but I've managed to learn from trial and error...

I can't agree more. We'd all like things to be simpler in Linux, but until we get there, you'll do well to follow this advice.

---

### Post by jerrydrussell on 2007-07-03
I wanted to give a huge thank you for this post, it got my wireless working flawlessly in Gnome (Feisty 7.04).

Do you know of any reason that it won't work if I switch the window manager to KDE?

If I log into a GNOME session, the network comes up in seconds. If I log out and log into KDE, it's still available.  But if there's a disconnect, or if I attempt to log in to KDE directly from boot, the network won't authenticate the WEP key,

---

### Post by diepruis on 2007-07-03
> **jerrydrussell said:**
> I wanted to give a huge thank you for this post, it got my wireless working flawlessly in Gnome (Feisty 7.04).

Do you know of any reason that it won't work if I switch the window manager to KDE?

If I log into a GNOME session, the network comes up in seconds. If I log out and log into KDE, it's still available.  But if there's a disconnect, or if I attempt to log in to KDE directly from boot, the network won't authenticate the WEP key,

It might be some KDE app trying to configure the network itself. Try to disable any such program (look for something like knetworkmanager first).

---

### Post by jerrydrussell on 2007-07-03
diepruis, 

I'd actually thought of that.  I removed knetworkmanager completely and installed wlanassistant.  It attempts to authenticate, but can't regardless of the WEP settings I give it.  I know WEP can be finicky, but I have to use it, as it's the only protocol my wife's laptop can use.

---

### Post by diepruis on 2007-07-03
> **jerrydrussell said:**
> diepruis, 

I'd actually thought of that.  I removed knetworkmanager completely and installed wlanassistant.  It attempts to authenticate, but can't regardless of the WEP settings I give it.  I know WEP can be finicky, but I have to use it, as it's the only protocol my wife's laptop can use.

Have you tried disabling wlanassistant?

---

### Post by jerrydrussell on 2007-07-03
Without wlanassistant I'm not sure how I'd even begin to connect.

what should I be looking for in the syslog to tell me if something's getting in the way?  I'm not a total *nix newbie, but it's been nearly 10 years since i ran Solaris machines all day for a living.  Needless to say, I'm a bit rusty.

---

### Post by ButteBlues on 2007-07-03
WPA_Supplicant does not work with these drivers - only the rt2x00 ones.

Also, note that knetworkmanager still depends on network-manager, so the daemon is likely still starting. Remove network-manager.

---

### Post by jerrydrussell on 2007-07-03
I'll give that a shot tomorrow.  I'd like o use KDE, but for the moment gnome is stable, working on the network well, and there's always actual work that needs to be done.

---

### Post by Matt Mc on 2007-07-03
Hey, I just want to stop by and say thanks for this thread. It got my Dlink DWL-G122 C1 wireless USB adapter working perfect :D  It was the only thing stopping me from switching to Linux, and I have many thanks to give you.

---

### Post by diepruis on 2007-07-03
> **jerrydrussell said:**
> Without wlanassistant I'm not sure how I'd even begin to connect.

what should I be looking for in the syslog to tell me if something's getting in the way?  I'm not a total *nix newbie, but it's been nearly 10 years since i ran Solaris machines all day for a living.  Needless to say, I'm a bit rusty.

Linux will connect automatically, that's what the file /etc/network/interfaces is for. The commands in this file are run as the PC starts up.

---

### Post by dongthao on 2007-07-04
I'm using rt73 driver, version: rt73-cvs-2007061718 for my wireless card (802.11 bg WLAN Ralink product). My OS is Ubuntu 7.04. It works fine, except can't show the Quality of the network in scan results. Below is the result of 'iwlist scan':
```

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:9A:74:29
                    ESSID:"inet"
                    Mode:Managed
                    Channel:6
                    Encryption key:on
                    Bit Rates:0 kb/s
          Cell 02 - Address: 00:40:F4:E1:32:0C
                    ESSID:"TV-Link JSC"
                    Mode:Managed
                    Channel:6
                    Encryption key:off
                    Bit Rates:0 kb/s

```
I don't know where exactly the problem is. The driver? My interface? Or Kernel? Give me some advices.

---

### Post by spartan777 on 2007-07-05
everything works fine when I'm doing the instructions, the internet works and all. the problem is when I reboot, i have no internet. The adapter powers on, but the "Link" light doesn't flash or go on at all. Also, when I run RutilT, i get the error "Network Interface is Down." I did the instructions to make everything run after reboot. this is my interfaces. 

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet static
wireless-essid minerhome
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1


iface wmaster0 inet dhcp
wireless-essid minerhome
wireless-key s:**************





auto rausb0
iface rausb0 inet dhcp
        pre-up ifconfig rausb0 up
        pre-up ifconfig rausb0 down
        pre-up ifconfig rausb0 up
        pre-up iwconfig rausb0 essid "MYESSID"
        pre-up iwconfig rausb0 mode Managed
        pre-up iwpriv rausb0 set AuthMode=WPAPSK
        pre-up iwpriv rausb0 set EncrypType=TKIP
        pre-up iwpriv rausb0 set WPAPSK="YOUR KEY"
        pre-up ifconfig rausb0 up


auto wlan0
iface wlan0 inet dhcp
	pre-up ifconfig wlan0 up
	pre-up iwconfig wlan0 essid minerhome
	pre-up iwconfig wlan0 key off





auto eth0
```

since wlan0 is my usb adapter, I get the feeling that wmaster0 is an erroneous entry. otherwise, i haven't a clue to what's wrong.

---

### Post by Austin_KW on 2007-07-05
> **spartan777 said:**
> everything works fine when I'm doing the instructions, the internet works and all. the problem is when I reboot, i have no internet. The adapter powers on, but the "Link" light doesn't flash or go on at all. Also, when I run RutilT, i get the error "Network Interface is Down." I did the instructions to make everything run after reboot. this is my interfaces. 
...
since wlan0 is my usb adapter, I get the feeling that wmaster0 is an erroneous entry. otherwise, i haven't a clue to what's wrong.

I don't think you are running the rt73 driver, have you followed the howto?

---

### Post by dannyboy79 on 2007-07-05
> **spartan777 said:**
> everything works fine when I'm doing the instructions, the internet works and all. the problem is when I reboot, i have no internet. The adapter powers on, but the "Link" light doesn't flash or go on at all. Also, when I run RutilT, i get the error "Network Interface is Down." I did the instructions to make everything run after reboot. this is my interfaces. 

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet static
wireless-essid minerhome
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1


iface wmaster0 inet dhcp
wireless-essid minerhome
wireless-key s:**************





auto rausb0
iface rausb0 inet dhcp
        pre-up ifconfig rausb0 up
        pre-up ifconfig rausb0 down
        pre-up ifconfig rausb0 up
        pre-up iwconfig rausb0 essid "MYESSID"
        pre-up iwconfig rausb0 mode Managed
        pre-up iwpriv rausb0 set AuthMode=WPAPSK
        pre-up iwpriv rausb0 set EncrypType=TKIP
        pre-up iwpriv rausb0 set WPAPSK="YOUR KEY"
        pre-up ifconfig rausb0 up


auto wlan0
iface wlan0 inet dhcp
	pre-up ifconfig wlan0 up
	pre-up iwconfig wlan0 essid minerhome
	pre-up iwconfig wlan0 key off





auto eth0
```

since wlan0 is my usb adapter, I get the feeling that wmaster0 is an erroneous entry. otherwise, i haven't a clue to what's wrong.

you should really remove ALL the interfaces that you're not using. either comment them out or save the file first, then delete them. enter this command after a fresh reboot
dmesg
then scroll down until you find any entry that has rausb0, or wlan0 or something for networking. that will tell you which one you need for sure.

any of the interfaces that have "auto" will attempted to be brought UP by ubuntu, so when you have more than one, of course there's conflicts. I notice that you have ath0 in there also, do you even have an Atheros card? I have the Netgear WG511T, it's got the AR5212 chipset and mine wifi interface is ath0. If I were you remove everything except for your wired interface, normally eth0, and your wifi interface, IF you're using the RT73, then I believe it should be rausb0. then set which ever ones you want to be brought up automagically by putting auto in from of them. good luck

---

### Post by jerrydrussell on 2007-07-05
If wpa_supplicant doesn't work with these drivers, how am I connecting now?  Or does that mean I can't use these drivers under KDE?

I may have stumbled upon something else as well.  I configured my wlan interface as per the documentation as wlan1, but the gnome network manager is reporting that I'm connected on eth1, which is *not* configured in /etc/network/interfaces

Here's the interfaces file:
```

auto ath0
iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
#wireless-essid twisted
#wireless-key s:ang3l

#wireless network device using DHCP
iface wlan1 inet dhcp
pre-up ifconfig wlan1 up
wireless-essd MY_ESSID
wireless-key s:MY_WEP_KEY
auto wlan1

iface wlan0 inet dhcp
wireless-essid MY_ESSID
wireless-key s:MY_WEP_KEY

auto wlan0

```

There is no eth1 interface listed, so I'm a tad confused by this, as the output in the "Connection Information"  outputs the following (excuse yypos, I'm adding this bit by hand)

```

Interface: Wireless Ethernet (eth1)
Speed: 11Mb/s
Driver: zd1211rw

```


The output from netstat -r
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.37.129.0     *               255.255.255.0   U         0 0          0 vnic0
192.168.0.0     *               255.255.255.0   U         0 0          0 eth1
link-local      *               255.255.0.0     U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth1
default         192.168.0.1     0.0.0.0         UG        0 0          0 eth1
default         *               0.0.0.0         U         0 0          0 eth0

```

I'm not sure why I'm connected to an adapter I haven't set up, but the same problem exists in the KDE environment. Knetworkmanager detects all local ESSID broadcasts, but simply will not connect to mine with WEP, period.

Do I need to add eth1 to /etc/network/interfaces, or add that I'm using WEP to the wlan1 configuration somehow?

Is WEP under KDE with serialmonkey drivers just not going to happen?  I can't see why gnome will connect perfectly but KDE can't.  I'm tempted to try a different desktom manager and see what the results are

---

### Post by Austin_KW on 2007-07-05
jerrydrussell,

What makes you think you have an rt73, you are reporting eth1 with driver zd1211rw. Have you confused a belkin usb V4000 for a v3000.

FYI, For your adapter, uou should replace wlan0 with eth1 in your interfaces.

---

### Post by jerrydrussell on 2007-07-05
*bangs head off keyboard in frustration*

Ugh, I Do have a V3000, I also have a V4000, which is lying on the table, over by the usb connector for the V40000, which is plugged in and working fine....

I didn't realized I'd switched them out.

Everything's working like a champ now.  Thanks so much!

---

### Post by spartan777 on 2007-07-05
I think my problem now (beside all the extra interfaces in the interfaces config file) is autostarting the drivers. if I do steps 11 and 12 over (Load the new module, Configure the interface) everything works fine. I'll go through the following steps and report back.

I have no doubt that my WUSB54GR is rt73- I think I read it on the linksys site. anywyas, if it wasn't rt73, nothing should work at all! and yes, i've followed every step of this how to.

---

### Post by simonishe on 2007-07-05
**THE MODULE IS NOW DEBIANIZED**

Hello everyone,

Just wanted to say that I've made a debianized-version of the module, so in order to compile it now, all you have to do is :
1) add _deb [http://liberdebian.shpro.eu/debian/ubuntu/edgy/](http://liberdebian.shpro.eu/debian/ubuntu/edgy/) ./_ to your debian reposit list (/etc/apt/sources.list)
2) install the package "module-assistant" (apt-get install module-assistant)

3) Type ```
module-assistant auto-install rt73
``` in a root terminal.

That's all! Hope that helps

---

### Post by spartan777 on 2007-07-05
simonishe, is that .deb pretty well tested? it would be a miracle if it was.

I assume the way to comment things out in the interfaces config file is with the "#" at the beginning of the line, correct?

---

### Post by kevdog on 2007-07-06
Does this process work for the 64bit Ubuntu version?

---

### Post by diepruis on 2007-07-06
> **simonishe said:**
> **THE MODULE IS NOW DEBIANIZED**

Hello everyone,

Just wanted to say that I've made a debianized-version of the module, so in order to compile it now, all you have to do is :
1) add _deb [http://liberdebian.shpro.eu/debian/ubuntu/edgy/](http://liberdebian.shpro.eu/debian/ubuntu/edgy/) ./_ to your debian reposit list (/etc/apt/sources.list)
2) install the package "module-assistant" (apt-get install module-assistant)

3) Type ```
module-assistant auto-install rt73
``` in a root terminal.

That's all! Hope that helps

How up to date is this repository, and how often will it be updated?

---

### Post by diepruis on 2007-07-06
> **spartan777 said:**
> I assume the way to comment things out in the interfaces config file is with the "#" at the beginning of the line, correct?

That's correct.

---

### Post by diepruis on 2007-07-06
> **kevdog said:**
> Does this process work for the 64bit Ubuntu version?

I can't think of any immediate reason that it wouldn't, and a quick search on rt2x00.serialmonkey.com turned up nothing. You'd have to investigate this yourself, as I don't have a 64 bit PC.

---

### Post by simonishe on 2007-07-06
>simonishe, is that .deb pretty well tested? it would be a miracle if it was.

Well, it works well on my system... Try it out and tell me!
I didn't know I was able to make miracles... :-)

>Does this process work for the 64bit Ubuntu version?

If the module works at all for the 64bit version, then it should work with this package too.

>How up to date is this repository, and how often will it be updated?

I can update it when people ask me (changes in cvs). The package is two days old. 
Anyway I'll make an update when they release a stable version at serialmonkey, before if people ask me to.

I'll try to add a note saying that you have to "ifconfig wifi0 up" to be able to 
"iwlist, iwconfig etc...", and maybe supply a rule for udev that would do that automatically (but I guess some people don't want to be invaded by microwaves, so that's why it's turned off by default).

---

### Post by dannyboy79 on 2007-07-06
> **simonishe said:**
> >simonishe, is that .deb pretty well tested? it would be a miracle if it was.

Well, it works well on my system... Try it out and tell me!
I didn't know I was able to make miracles... :-)

>Does this process work for the 64bit Ubuntu version?

If the module works at all for the 64bit version, then it should work with this package too.

>How up to date is this repository, and how often will it be updated?

I can update it when people ask me (changes in cvs). The package is two days old. 
Anyway I'll make an update when they release a stable version at serialmonkey, before if people ask me to.

I'll try to add a note saying that you have to "ifconfig wifi0 up" to be able to 
"iwlist, iwconfig etc...", and maybe supply a rule for udev that would do that automatically (but I guess some people don't want to be invaded by microwaves, so that's why it's turned off by default).

you're the man!! I have been asking if some1 could create a .deb for awhile now. I just figured with all these people compiling it over and over and over, wouldn't it be worth it if someone just made a deb instead? If you need help hosting it, I can put it at my ftp site as well. BUT, I would also like the driver that works for the Belkin F5D7050 Wireless USB , I think that's the rt2500 or the rt71.

If I understand correctly, you have only made the deb for the rt73 correct?

lsusb shows this: 
(i am not at home, but If I remember correctly, the box had v3 on it, is that version 3000, because I have read that there are version 2000 and version 2100 which uses the rt71 and not the rt2500.

---

### Post by diepruis on 2007-07-06
> **simonishe said:**
> >How up to date is this repository, and how often will it be updated?

I can update it when people ask me (changes in cvs). The package is two days old. 
Anyway I'll make an update when they release a stable version at serialmonkey, before if people ask me to.

I'll try to add a note saying that you have to "ifconfig wifi0 up" to be able to 
"iwlist, iwconfig etc...", and maybe supply a rule for udev that would do that automatically (but I guess some people don't want to be invaded by microwaves, so that's why it's turned off by default).

In that case, I propose you make a HOWTO based on using those .debs, while I maintain this one for people who want to compile the driver from scratch.

---

### Post by simonishe on 2007-07-06
>>I'll try to add a note saying that you have to "ifconfig wifi0 up" to be able to
>>"iwlist, iwconfig etc...", and maybe supply a rule for udev that would do that >>automatically (but I guess some people don't want to be invaded by microwaves, so >>that's why it's turned off by default).
>In that case, I propose you make a HOWTO based on using those .debs, while I >maintain this one for people who want to compile the driver from scratch.

Well, the "ifconfig up" issue has nothing to do with my .debs, it's a general issue...
I'm not sure it's a good idea to make again another HOWTO...

---

### Post by diepruis on 2007-07-07
> **simonishe said:**
> Well, the "ifconfig up" issue has nothing to do with my .debs, it's a general issue...
I'm not sure it's a good idea to make again another HOWTO...

Fair enough.

---

### Post by kevdog on 2007-07-07
How do you set a static IP address with these drivers using WEP.

Here is what I have tried and it doesnt seem to connect, although using dhcp is successful:

auto ra1
iface ra1 inet static
address 192.168.2.52
gateway 192.168.2.1
dns-nameservers 195.92.195.94
netmask 255.255.255.0
pre-up ifconfig ra1 up
pre-up iwconfig ra1 essid USR9110
pre-up iwconfig ra1 key "OFF"

Thanks

---

### Post by babysteps on 2007-07-08
I'm back and at it again. Ubuntu has been growing on me, Previously I was stuck at Breezy, and a dying hard drive. Now it's still not up to date, but up to Dapper 6.06.1.  as I try to follow Diepruis and Dannyboy79's recommendations. 

So far I've followed the How To and gotten the rt73.ko built successfully.  There were some complications until I also removed the Islsm_usb that came with Dapper (as per another post about Ndiswrapper and the Belkin) .  

Alas, my final hurdle was the message; "Hardware unstable".   Also, I'm not 100% sure what it's supposed to be: Wlan0? rausb0? At one point (before I removed the islsm driver), it showed up in ifconfig as eth0.  But after I removed islsm and blacklisted it, it hasn't come up in ifconfig, nor iwconfig.   

By the way, lsusb shows my device as a version 1000 of the infamous Belkin 
FSD7050(A)  Opening the usb stick I see on the chip RT2571 .  I think we have determined last time that this is the right How To for me, right?

Thanks for your help!
I


> **diepruis said:**
> Yes the colours do mean something. I *think* the light green indicates archives, while blue indicates directories. The Makefile is definitely not supposed to be blue. I'm not entirely sure what that indicates though. Perhaps something is corrupted somehow, and you need to re download and try again - still, that won't solve your gcc problems.

The "modules" error is my fault, sorry, the directory's name should be "Module".



You can upgrade from the any CD of the version after your current one. You can also do a fresh install of Feisty. If you can't get on line, check to see if your LoCo team could provide you with a CD. That said, I'm not sure that upgrading will solve your problem.



It's incredibly frustrating, I know. I struggled for about a week to get my rt61 card to work because I was barking up all sorts of wrong trees. If you keep at it, it'll work eventually.



I have a feeling this might be because of your old version of Ubuntu, since mine (Feisty) has gcc-3.4 available. You might need to upgrade just to get this package.


I'm sorry I can't be more help, but I never even had Breezy installed, nor did I try to run this driver on it. I'm tempted to agree with dannyboy and tell you to upgrade to a newer version of Ubuntu, but like I said, I don't know *for sure* that that'll work - still it's something to try.

---

### Post by sampbar on 2007-07-08
Hi,
I originally got my network card working by following the first part of this tutorial but when i tried to automate and rebooted i could not connect to the internet. This is fixed every time by entering the ifconfig and iwconfig information but i would be grateful if somebody could help me automate this.

Here is my iwconfig information:
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     RT73 WLAN  
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

and here is my /etc/network/interfaces information:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan1
iface wlan1 inet dhcp
	preup ifconfig wlan1 up
	preup iwconfig wlan1 essid Barrett
	preup iwconfig wlan1 key <REMOVED>

Thanks

Samuel

---

### Post by diepruis on 2007-07-09
> **sampbar said:**
> and here is my /etc/network/interfaces information:


You should replace "preup" with "pre-up".

---

### Post by diepruis on 2007-07-09
> **babysteps said:**
> Alas, my final hurdle was the message; "Hardware unstable".

Where did you see that message?

---

### Post by diepruis on 2007-07-09
> **kevdog said:**
> How do you set a static IP address with these drivers using WEP.

Here is what I have tried and it doesnt seem to connect, although using dhcp is successful:

auto ra1
iface ra1 inet static
address 192.168.2.52
gateway 192.168.2.1
dns-nameservers 195.92.195.94
netmask 255.255.255.0
pre-up ifconfig ra1 up
pre-up iwconfig ra1 essid USR9110
pre-up iwconfig ra1 key "OFF"

Thanks

I wouldn't know, since I use an address assigned by DHCP. A shortcut you could use is to tell your router to assign a static IP address to you, this is what I'm using and it works pretty well.

If I had to guess why it's not working, I would say that the card isn't trying to associate with the access point. See "man iwconfig" and refer to the entry under the "ap" command.

---

### Post by virogenesis1 on 2007-07-09
Thanks so much for this - after struggling with the Ralink drivers for my D-link usb adapter, I have finally managed to get my wireless connection working. All went exceedingly smoothly, thanks very much for producing such a clear and informative step-by-step. :)

---

### Post by kevdog on 2007-07-09
Just to follow-up, one of the users I was helping posted this about getting a static IP address to work.  I thought I would pass it along for the sake of completeness

```
auto ra1
iface ra1 inet static
address 192.168.2.52
netmask 255.255.255.0
network 192.168.2.1
gateway 192.168.2.1
        pre-up ifconfig ra1 up
        pre-up iwconfig ra1 essid "USR9110"
        pre-up iwconfig ra1 mode Managed
```

---

### Post by obidose on 2007-07-09
Is it not possible to put all this into a script which i can just download and run, rather than continual copy and paste?

---

### Post by diepruis on 2007-07-10
> **kevdog said:**
> Just to follow-up, one of the users I was helping posted this about getting a static IP address to work.  I thought I would pass it along for the sake of completeness

```
auto ra1
iface ra1 inet static
address 192.168.2.52
netmask 255.255.255.0
network 192.168.2.1
gateway 192.168.2.1
        pre-up ifconfig ra1 up
        pre-up iwconfig ra1 essid "USR9110"
        pre-up iwconfig ra1 mode Managed
```

Thanks, I'll add this information.

EDIT: I changed some of the settings, just look over the edited post to see if I got it right.

---

### Post by diepruis on 2007-07-10
> **obidose said:**
> Is it not possible to put all this into a script which i can just download and run, rather than continual copy and paste?

Yes it is. However, I prefer not to do that, for the following reasons:
[LIST=1]
[*] It's a lot of work that I have to maintain.
[*] People have very different setups that must be taken into account.
[*] This way encourages people to understand what exactly they're doing.
[/LIST]

You're welcome to create such a script, but be warned that it's bound to be a **lot** of work.

---

### Post by babysteps on 2007-07-10
> **diepruis said:**
> Where did you see that message?

Ah, sorry, I didn't keep good notes while doing this, but I think it was after I did this:


Code:

sudo ifdown rausb0
sudo modprobe -rv rt73
sudo modprobe -v rt73
sudo ifup rausb0

It seemed that everything was going to be working but the USB dongle is dying? That would be rather comical after all this. 

Also, I'm not sure if things change when I'm plugging the USB into the new USB 2.0 slot created with a PMCIA card? What I mean is, I now have 3 USB slots. One is the original 1.0 on the laptop. the other two are created with the PMCIA card.  I assume i should stick with one slot and always plug it into that one each time?

Thanks for your help. I'm going to have to get some time and re-do everything. I feel it's so close!

babysteps

---

### Post by kevdog on 2007-07-10
I want to run the rutilt executable at run time so that the icon shows up in the system tray, rather than having to type this everytime at command prompt to start.

Do you know if I put a line like
rutilt
in the /etc/rc.local file

or do I need to put it in a script in init.d directory.

A little direction would be greatful.

thanks

---

### Post by diepruis on 2007-07-10
> **babysteps said:**
> Also, I'm not sure if things change when I'm plugging the USB into the new USB 2.0 slot created with a PMCIA card? What I mean is, I now have 3 USB slots. One is the original 1.0 on the laptop. the other two are created with the PMCIA card.  I assume i should stick with one slot and always plug it into that one each time?

I don't think that matters either way.

> **babysteps said:**
> Thanks for your help. I'm going to have to get some time and re-do everything. I feel it's so close!

That might be a good idea. Please note exactly what happens, that'll make it much easier to help you.

---

### Post by diepruis on 2007-07-10
> **kevdog said:**
> I want to run the rutilt executable at run time so that the icon shows up in the system tray, rather than having to type this everytime at command prompt to start.

Do you know if I put a line like
rutilt
in the /etc/rc.local file

or do I need to put it in a script in init.d directory.

A little direction would be greatful.

thanks

You seem to be on the right track. However, if that utility is a graphical program you'll need to put it somewhere else. I can't say where though, since I've never tried before.

---

### Post by k-os on 2007-07-10
I've come almost to the goal! It's just that my wireless USB dongle, is not able to fetch any signal from any of the connections, the Broadcom PCI card I got has a lot of signal. 

 Probably I'm not that far from success, before I followed this how-to the wireless USB dongle wasn't even detected at all.

What could be wrong?

---

### Post by ~cyrus~ on 2007-07-11
Another 'thank you' to the thread starter for this 'how to'

In my case a successful connection on following these steps with a D-Link DWL-G122 Wireless G USB adapter from my desktop with WEP to my router. wlan1 got me connected.

What also worked a charm were the instructions to the interface that brings up the connection across reboots. What I didn't do was purge network manager.

What worried me initially was the result of install build-essential that stated no package found whose name matched "build-essential"

However...the end result is that it works...and that's what counts!

Thanks guys.

Cheers

---

### Post by diepruis on 2007-07-11
> **~cyrus~ said:**
> What also worked a charm were the instructions to the interface that brings up the connection across reboots. What I didn't do was purge network manager.

Mmm... interesting. This working for anyone else?

> **~cyrus~ said:**
> What worried me initially was the result of install build-essential that stated no package found whose name matched "build-essential"

How did you fix that problem?

> **~cyrus~ said:**
> 
However...the end result is that it works...and that's what counts!

Thanks guys.

Cheers

No problem, HTH.

---

### Post by diepruis on 2007-07-11
> **k-os said:**
> I've come almost to the goal! It's just that my wireless USB dongle, is not able to fetch any signal from any of the connections, the Broadcom PCI card I got has a lot of signal. 

 Probably I'm not that far from success, before I followed this how-to the wireless USB dongle wasn't even detected at all.

What could be wrong?

I can honestly not say. It depends on a lot of things. What exactly is the problem? Is the signal strength just lower on the dongle, or doesn't it connect at all?

---

### Post by k-os on 2007-07-11
"What exactly is the problem? Is the signal strength just lower on the dongle, or doesn't it connect at all?"

Actually, no signal at all with the USB dongle. It finds all the networks that the PCI-card finds, but there is no signal shown, that signal bar is empty... It's very weird... If I tr y to connect with it, it takes like 1 minute, and then it fails to connect... 

Could it be possible to trouble-shoot the connection process to see what could fail?

---

### Post by ~cyrus~ on 2007-07-11
I followed your instructions step by step. However,

```
sudo aptitude install build-essential linux-headers-`uname -r`
```

gave me the following response below (that I hand copied for further info if it was required..didn't know if I could connect at that stage) which I ignored actually, and just went on to your next step

```

Reading package lists...Done
Building dependency tree
Reading state information...Done
Reading extended state information
Initializing package states...Done
Building tag database...Done
Couldn't find any package whose name or description matched "build-essential"
No package will be installed, upgraded or removed
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded
Need to get 0B of archives. After unpacking 0B will be used
Writing extended state information...Done

```

---

### Post by dannyboy79 on 2007-07-11
please make sure that you have enabled the "extra" repositories before performing this tutorial. make sure you do a sudo aptitude update after updating repo's as well. Here's the guide for updating repo's.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

Let us know if you have any other issues. Obviously, to do an "update" and download any packages you need internet access so you'll need to use another means to get the required packages/files onto the machine you're trying to get wireless to work.

---

### Post by diepruis on 2007-07-11
> **k-os said:**
> "What exactly is the problem? Is the signal strength just lower on the dongle, or doesn't it connect at all?"

Actually, no signal at all with the USB dongle. It finds all the networks that the PCI-card finds, but there is no signal shown, that signal bar is empty... It's very weird... If I tr y to connect with it, it takes like 1 minute, and then it fails to connect... 

Could it be possible to trouble-shoot the connection process to see what could fail?

You can, but you should refer to the README file included with the source, and perhaps information on the serialmonkey website for details on exactly how. I can't help you with this, since I've never tried to do it, nor did I experience your problem.

---

### Post by ~cyrus~ on 2007-07-12
> **diepruis said:**
> I'm not following the development of Feisty, but if a new kernel was released in that update, you will have to recompile the driver. Please try this:

```

cd /usr/src/rt73-cvs-yyyymmddhh/Module
sudo make clean
sudo make
sudo make install

```

(Replacing the yyyymmddhh as appropriate.)

Reboot and it *should* work.

It did work.

Once I had a connection again I did install needed dependencies which I overlooked in your how-to without a connection, as well as remove network manager that I hadn't done earlier.

Question: Would I need to keep cleaning and installing the module after every kernel release?

---

### Post by diepruis on 2007-07-12
> **~cyrus~ said:**
> It did work.

Good to know.

> **~cyrus~ said:**
> Question: Would I need to keep cleaning and installing the module after every kernel release?

Yes, you have to.

---

### Post by nphx on 2007-07-13
Worked perfectly. Thank you! 

Shouldn't this be a wiki?

---

### Post by diepruis on 2007-07-13
> **nphx said:**
> Worked perfectly. Thank you! 

Shouldn't this be a wiki?

I wanted to sort out any potential problems before replacing the current wiki page, and make sure the latter isn't relevant any more ^_^

---

### Post by nphx on 2007-07-13
There's a bug in the latest build. Never had this in the previous versions of the CVS:

```

/usr/src/rt73-cvs-2007071311/Module$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/src/rt73-cvs-2007071311/Module/rtmp_main.o
In file included from /usr/src/rt73-cvs-2007071311/Module/rt_config.h:187,
                 from /usr/src/rt73-cvs-2007071311/Module/rtmp_main.c:36:
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:819: error: expected identifier or ‘(’ before ‘{’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:819: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:821: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:823: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:823: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:826: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:826: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:826: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:830: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:832: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:832: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:835: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:837: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:837: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:840: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:842: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:842: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:845: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:847: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:847: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:850: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:850: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:853: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:853: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:853: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:857: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:857: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:860: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:860: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:863: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:863: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:866: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:868: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:868: error: expected identifier or ‘(’ before ‘,’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_def.h:868: error: expected identifier or ‘(’ before ‘}’ token
/usr/src/rt73-cvs-2007071311/Module/rtmp_main.c:71: error: expected expression before ‘;’ token
make[2]: *** [/usr/src/rt73-cvs-2007071311/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/usr/src/rt73-cvs-2007071311/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
rt73.ko failed to build!
make: *** [module] Error 1


```

---

### Post by rjernst on 2007-07-13
The most recent change broke the build.  Go to the Module directory and modify rtmp_def.h

Go to the end of the file and replace the entire #define RT73_USB_DRIVERS with this:

#define RT73_USB_DEVICES { \
 /* AboCom */\
 {USB_DEVICE(0x07b8,0xb21d)},\
 /* Askey */\
 {USB_DEVICE(0x1690,0x0722)},\
 /* ASUS */\
 {USB_DEVICE(0x0b05,0x1723)},\
 {USB_DEVICE(0x0b05,0x1724)},\
 /* Belkin */\
 {USB_DEVICE(0x050d,0x7050)},\
 {USB_DEVICE(0x050d,0x705a)},\
 {USB_DEVICE(0x050d,0x905b)},\
 /* Billionton */\
 {USB_DEVICE(0x1631,0xc019)},\
 /* CNet */\
 {USB_DEVICE(0x1371,0x9022)},\
 {USB_DEVICE(0x1371,0x9032)},\
 /* Conceptronic */\
 {USB_DEVICE(0x14b2,0x3c22)},\
 /* D-Link */\
 {USB_DEVICE(0x07d1,0x3c03)},\
 {USB_DEVICE(0x07d1,0x3c04)},\
 /* Gemtek*/\
 {USB_DEVICE(0x15a9,0x0004)},\
 /* Gigabyte */\
 {USB_DEVICE(0x1044,0x8008)},\
 {USB_DEVICE(0x1044,0x800a)},\
 /* Huawei-3Com */\
 {USB_DEVICE(0x1472,0x0009)},\
 /* Hercules */\
 {USB_DEVICE(0x06f8,0xe010)},\
 {USB_DEVICE(0x06f8,0xe020)},\
 /* LinkSys */\
 {USB_DEVICE(0x13b1,0x0020)},\
 {USB_DEVICE(0x13b1,0x0023)},\
 /* MSI */\
 {USB_DEVICE(0x0db0,0x6877)},\
 {USB_DEVICE(0x0db0,0xa861)},\
 {USB_DEVICE(0x0db0,0xa874)},\
 /* Ralink */\
 {USB_DEVICE(0x148f,0x2573)},\
 {USB_DEVICE(0x148f,0x2671)},\
/* Qcom */\
 {USB_DEVICE(0x18e8,0x6196)},\
 {USB_DEVICE(0x18e8,0x6229)},\
 /* Sitecom */\
 {USB_DEVICE(0x0df6,0x9712)},\
 {USB_DEVICE(0x0df6,0x90ac)},\
 /* Surecom */\
 {USB_DEVICE(0x0769,0x31f3)},\
 /* Planex */\
 {USB_DEVICE(0x2019,0xab01)},\
 {USB_DEVICE(0x2019,0xab50)},\
 {USB_DEVICE(0,0)}} /* end marker */


Then run

sudo make

and it should build properly.

---

### Post by nphx on 2007-07-13
So it's just a syntax error, in **#define RT73_USB_DEVICES**. Thanks, I placed the **\** after each model number and it compiled. 

To further clearify, in the **rtmp_def.h** file change:

> /* AboCom */
 {USB_DEVICE(0x07b8,0xb21d)},\

to

/* AboCom */[COLOR="Red"]\[/COLOR]
 {USB_DEVICE(0x07b8,0xb21d)},\

repeat that for all the models** /* AboCom */**, ** /* Askey */**, ** /* ASUS */**, etc...

OR just download the file bellow:

**[COLOR="Red"]NOTE:[/COLOR]** I attached the fixed syntax error for **rt73-cvs-2007071311** version of the daily cvs. So download this and follow the guide until they fix it at serialmonkey's end.

---

### Post by diepruis on 2007-07-14
> **rjernst said:**
> The most recent change broke the build.  Go to the Module directory and modify rtmp_def.h

Go to the end of the file and replace the entire #define RT73_USB_DRIVERS with this:

#define RT73_USB_DEVICES { \
 /* AboCom */\
 {USB_DEVICE(0x07b8,0xb21d)},\
 /* Askey */\
 {USB_DEVICE(0x1690,0x0722)},\
 /* ASUS */\
 {USB_DEVICE(0x0b05,0x1723)},\
 {USB_DEVICE(0x0b05,0x1724)},\
 /* Belkin */\
 {USB_DEVICE(0x050d,0x7050)},\
 {USB_DEVICE(0x050d,0x705a)},\
 {USB_DEVICE(0x050d,0x905b)},\
 /* Billionton */\
 {USB_DEVICE(0x1631,0xc019)},\
 /* CNet */\
 {USB_DEVICE(0x1371,0x9022)},\
 {USB_DEVICE(0x1371,0x9032)},\
 /* Conceptronic */\
 {USB_DEVICE(0x14b2,0x3c22)},\
 /* D-Link */\
 {USB_DEVICE(0x07d1,0x3c03)},\
 {USB_DEVICE(0x07d1,0x3c04)},\
 /* Gemtek*/\
 {USB_DEVICE(0x15a9,0x0004)},\
 /* Gigabyte */\
 {USB_DEVICE(0x1044,0x8008)},\
 {USB_DEVICE(0x1044,0x800a)},\
 /* Huawei-3Com */\
 {USB_DEVICE(0x1472,0x0009)},\
 /* Hercules */\
 {USB_DEVICE(0x06f8,0xe010)},\
 {USB_DEVICE(0x06f8,0xe020)},\
 /* LinkSys */\
 {USB_DEVICE(0x13b1,0x0020)},\
 {USB_DEVICE(0x13b1,0x0023)},\
 /* MSI */\
 {USB_DEVICE(0x0db0,0x6877)},\
 {USB_DEVICE(0x0db0,0xa861)},\
 {USB_DEVICE(0x0db0,0xa874)},\
 /* Ralink */\
 {USB_DEVICE(0x148f,0x2573)},\
 {USB_DEVICE(0x148f,0x2671)},\
/* Qcom */\
 {USB_DEVICE(0x18e8,0x6196)},\
 {USB_DEVICE(0x18e8,0x6229)},\
 /* Sitecom */\
 {USB_DEVICE(0x0df6,0x9712)},\
 {USB_DEVICE(0x0df6,0x90ac)},\
 /* Surecom */\
 {USB_DEVICE(0x0769,0x31f3)},\
 /* Planex */\
 {USB_DEVICE(0x2019,0xab01)},\
 {USB_DEVICE(0x2019,0xab50)},\
 {USB_DEVICE(0,0)}} /* end marker */


Then run

sudo make

and it should build properly.

If this hasn't already been fixed upstream you should send them a patch.

---

### Post by k-os on 2007-07-14
Ok, I made it work first. I had to disable the NetworkManager applet, and I was online with my wireless USB dongle. Now, I had to re-do this process, I am not coming any further than to the point where I do "sudo make", and I get this error message:

```
$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/src/rt73-cvs-2007071410/Module/rtmp_main.o
In file included from /usr/src/rt73-cvs-2007071410/Module/rt_config.h:187,
                 from /usr/src/rt73-cvs-2007071410/Module/rtmp_main.c:36:
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:819: error: expected identifier or &#8216;(&#8217; before &#8216;{&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:819: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:821: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:823: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:823: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:826: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:826: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:826: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:830: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:832: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:832: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:835: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:837: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:837: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:840: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:842: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:842: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:845: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:847: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:847: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:850: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:850: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:853: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:853: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:853: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:857: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:857: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:860: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:860: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:863: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:863: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:866: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:868: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:868: error: expected identifier or &#8216;(&#8217; before &#8216;,&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_def.h:868: error: expected identifier or &#8216;(&#8217; before &#8216;}&#8217; token
/usr/src/rt73-cvs-2007071410/Module/rtmp_main.c:71: error: expected expression before &#8216;;&#8217; token
make[2]: *** [/usr/src/rt73-cvs-2007071410/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/usr/src/rt73-cvs-2007071410/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
rt73.ko failed to build!
make: *** [module] Error 1
```

There I'm really lost... Any further ideas?

Thanks

---

### Post by fluteflute on 2007-07-14
Try again but use the following line insted of the one in the post:
```
sudo wget [http://ubuntuforums.org/attachment.php?attachmentid=38098&d=1184356522](http://ubuntuforums.org/attachment.php?attachmentid=38098&d=1184356522) -O /usr/src/rt73-cvs-daily.tar.gz
```

I'm about to try but it should work. :)

EDIT: It worked and I'm typing this from Kubuntu!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! Thanks everyone.

---

### Post by babysteps on 2007-07-15
> **diepruis said:**
> I don't think that matters either way.



That might be a good idea. Please note exactly what happens, that'll make it much easier to help you.

I hope this is a little clearer for you to help me.  Although, in the mean time I'm having some problem with this Compaq Armada E500 with Dapper Drake.  It has several times refused to shut down: either getting stuck at "Bluetooth", or just not accepting further input, but only blinking dash.  I had to unplug to shut down. 

Just to refresh: This is the Belkin USB F5D7050.  1)On the outside of the usb stick it has an FCC ID: K7SF5D7050A,  2)the lsusb id it as 050d:7050 version 1000, WIFI  and finally 3)with the case pried open, the chip says RT2571.

Also, I wasn't always clear exactly when in the process of setting up I should physically plug the USB stick into the computer.  Dapper seem to react poorly to this Belkin in that it almost always freezes when I plug it in.  The last time I plugged it in after the driver was installed there was a warning about the Wireless program crashing unexpectedly.  (whereas the previous Breezy was pretty hardy).  Please advice. 

Thank you!

Babysteps

hl@hlarmada:~$ lsmod |grep usb
usbcore               130692  5 ndiswrapper,ehci_hcd,ohci_hcd,uhci_hcd
hl@hlarmada:~$ sudo rmmod ndiswrapper
Password:
hl@hlarmada:~$ lsmod |grep usb
usbcore               130692  4 ehci_hcd,ohci_hcd,uhci_hcd
hl@hlarmada:~$ cd /usr/src
hl@hlarmada:/usr/src$ cd Desktop
bash: cd: Desktop: No such file or directory
hl@hlarmada:/usr/src$ ~
bash: /home/hl: is a directory
hl@hlarmada:/usr/src$ cd ~
hl@hlarmada:~$ cd Desktop

(*********************************)abridged by baybsteps

hl@hlarmada:~/Desktop$ sudo cp rt73-cvs-daily.tar.gz /usr/src
hl@hlarmada:~/Desktop$ cd /usr/src
hl@hlarmada:/usr/src$ sudo tar -xvzf rt73-cvs-daily.tar.gz
rt73-cvs-2007071311/CVS/Repository
rt73-cvs-2007071311/CVS/Root
rt73-cvs-2007071311/CVS/Entries.Log
rt73-cvs-2007071311/CVS/Entries
rt73-cvs-2007071311/Module/CVS/Repository
rt73-cvs-2007071311/Module/CVS/Root
rt73-cvs-2007071311/Module/CVS/Entries
rt73-cvs-2007071311/Module/CVS/
rt73-cvs-2007071311/Module/iwpriv_usage.txt
rt73-cvs-2007071311/Module/sanity.c
rt73-cvs-2007071311/Module/rtmp_def.h~
rt73-cvs-2007071311/Module/rt73.bin
rt73-cvs-2007071311/Module/sync.c
rt73-cvs-2007071311/Module/Makefile
rt73-cvs-2007071311/Module/rtmp_wep.c
rt73-cvs-2007071311/Module/assoc.c
rt73-cvs-2007071311/Module/rtmp.h
rt73-cvs-2007071311/Module/mlme.c
rt73-cvs-2007071311/Module/rtmp_main.c
rt73-cvs-2007071311/Module/rtmp_init.c
rt73-cvs-2007071311/Module/md5.c
rt73-cvs-2007071311/Module/rtmp_def.h
rt73-cvs-2007071311/Module/md5.h
rt73-cvs-2007071311/Module/wpa.h
rt73-cvs-2007071311/Module/rtusb_bulk.c
rt73-cvs-2007071311/Module/rt2x00debug.h
rt73-cvs-2007071311/Module/connect.c
rt73-cvs-2007071311/Module/rtmp_type.h
rt73-cvs-2007071311/Module/rtusb_io.c
rt73-cvs-2007071311/Module/rtmp_info.c
rt73-cvs-2007071311/Module/rt_config.h
rt73-cvs-2007071311/Module/mlme.h
rt73-cvs-2007071311/Module/oid.h
rt73-cvs-2007071311/Module/rtmp_tkip.c
rt73-cvs-2007071311/Module/TESTING
rt73-cvs-2007071311/Module/wpa.c
rt73-cvs-2007071311/Module/rtusb_data.c
rt73-cvs-2007071311/Module/auth_rsp.c
rt73-cvs-2007071311/Module/rt73.h
rt73-cvs-2007071311/Module/auth.c
rt73-cvs-2007071311/CVS/
rt73-cvs-2007071311/Module/
rt73-cvs-2007071311/FAQ
rt73-cvs-2007071311/CHANGELOG
rt73-cvs-2007071311/THANKS
rt73-cvs-2007071311/LICENSE
rt73-cvs-2007071311/README
hl@hlarmada:/usr/src$ cd /usr/src/rt73-cvs-2007071311/Module
hl@hlarmada:/usr/src/rt73-cvs-2007071311/Module$ ls
assoc.c           Makefile  rt2x00debug.h  rtmp.h       rtmp_wep.c    TESTING
auth.c            md5.c     rt73.bin       rtmp_info.c  rtusb_bulk.c  wpa.c
auth_rsp.c        md5.h     rt73.h         rtmp_init.c  rtusb_data.c  wpa.h
connect.c         mlme.c    rt_config.h    rtmp_main.c  rtusb_io.c
CVS               mlme.h    rtmp_def.h     rtmp_tkip.c  sanity.c
iwpriv_usage.txt  oid.h     rtmp_def.h~    rtmp_type.h  sync.c
hl@hlarmada:/usr/src/rt73-cvs-2007071311/Module$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  CC [M]  /usr/src/rt73-cvs-2007071311/Module/rtmp_main.o
  CC [M]  /usr/src/rt73-cvs-2007071311/Module/mlme.o
  CC [M]  /usr/src/rt73-cvs-2007071311/Module/connect.o
  CC [M]  /usr/src/rt73-cvs-2007071311/Module/rtusb_bulk.o
  CC [M]  /usr/src/rt73-cvs-2007071311/Module/rtusb_io.o
  CC [M]  /usr/src/rt73-cvs-2007071311/Module/sync.o
  CC [M]  /usr/src/rt73-cvs-2007071311/Module/assoc.o
  CC [M]  /usr/src/rt73-cvs-2007071311/Module/auth.o
  CC [M]  /usr/src/rt73-cvs-2007071311/Module/auth_rsp.o
  CC [M]  /usr/src/rt73-cvs-2007071311/Module/rtusb_data.o
  CC [M]  /usr/src/rt73-cvs-2007071311/Module/rtmp_init.o
  CC [M]  /usr/src/rt73-cvs-2007071311/Module/sanity.o
  CC [M]  /usr/src/rt73-cvs-2007071311/Module/rtmp_wep.o
  CC [M]  /usr/src/rt73-cvs-2007071311/Module/rtmp_info.o
  CC [M]  /usr/src/rt73-cvs-2007071311/Module/rtmp_tkip.o
  CC [M]  /usr/src/rt73-cvs-2007071311/Module/wpa.o
  CC [M]  /usr/src/rt73-cvs-2007071311/Module/md5.o
  LD [M]  /usr/src/rt73-cvs-2007071311/Module/rt73.o
  Building modules, stage 2.
  MODPOST
  CC      /usr/src/rt73-cvs-2007071311/Module/rt73.mod.o
  LD [M]  /usr/src/rt73-cvs-2007071311/Module/rt73.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
*** Module rt73.ko built successfully
hl@hlarmada:/usr/src/rt73-cvs-2007071311/Module$ sudo make install
*** Install module in /lib/modules/2.6.15-26-386/extra ...
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/usr/src/rt73-cvs-2007071311/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  INSTALL /usr/src/rt73-cvs-2007071311/Module/rt73.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
/sbin/depmod -a
*** Update /etc/modprobe.conf alias for wlan*
grep: /etc/modprobe.conf: No such file or directory
*** Install firmware in /lib/firmware ...
*** Check config ...
hl@hlarmada:/usr/src/rt73-cvs-2007071311/Module$

---

### Post by diepruis on 2007-07-16
> **babysteps said:**
> I hope this is a little clearer for you to help me....

Well... so far so good. What happens when you try to follow the rest of the guide? Or does the PC crash at this point because you inserted the dongle?

---

### Post by digge on 2007-07-16
Hi all, i had big problems after following this guide and inserting my USB dongle my computer would hang. Reading a lot about it made me realize it has to do with the preemt or smp support in the generic kernel. So what i did was to install the"server" kernel via apt. At this time of writing its 2.6.20-16-server. That kernel have preemt disabled by default (i think), dont know about smp, but that made my card work without hard locks. Just thought id tell you all this since then you dont have to recompile kernels and stuff. Ive tried that and its always something you miss and have to start over... Maybe add this to a troubleshooting section of the guide?

---

### Post by diepruis on 2007-07-16
> **digge said:**
> Hi all, i had big problems after following this guide and inserting my USB dongle my computer would hang. Reading a lot about it made me realize it has to do with the preemt or smp support in the generic kernel. So what i did was to install the"server" kernel via apt. At this time of writing its 2.6.20-16-server. That kernel have preemt disabled by default (i think), dont know about smp, but that made my card work without hard locks. Just thought id tell you all this since then you dont have to recompile kernels and stuff. Ive tried that and its always something you miss and have to start over... Maybe add this to a troubleshooting section of the guide?

I did have a section on this, but I suggested installing the 386 (package linux-386) kernel. It has much the same effect, except that it is more appropriate for personal computers. However, some people who responded to the original post indicated that the bug has since been fixed. Could you please try the new version of the module and test the generic kernel again?

---

### Post by digge on 2007-07-16
I did try it from the 14th, when the bug in the usb vendor list was just  fixed (the compile bug just above)... Still hard locks my whole system, this kernel however is stable as a rock. Might be some other laptop related module that they excluded though since its a laptop.

Havnt tried the 386 kernel but wouldnt want to loose the 686 optimizations, my laptop is realy slow as it is.

BTW, thanks for a great guide.

---

### Post by babysteps on 2007-07-16
Yes, Diepruis, I can't get past the USB causing the hard lock.  If I don't plug it in at all, I have no device to configure. 



> **digge said:**
> Hi all, i had big problems after following this guide and inserting my USB dongle my computer would hang. Reading a lot about it made me realize it has to do with the preemt or smp support in the generic kernel. So what i did was to install the"server" kernel via apt. At this time of writing its 2.6.20-16-server. That kernel have preemt disabled by default (i think), dont know about smp, but that made my card work without hard locks. Just thought id tell you all this since then you dont have to recompile kernels and stuff. Ive tried that and its always something you miss and have to start over... Maybe add this to a troubleshooting section of the guide?

Digge, I just booted up the laptop that I had to unplug to force quit.  Since you mentioned preemt I thought I had seen that before, so, without doing anything further I checked the dmesg and there towards the end are the following line:
rtusb init ====>
usbcore: registered new driver rt73
ndiswrapper version 1.8 loaded (preempt=yes, smp=no)
usbcore: registered new driver ndiswrapper
NET: Registered protocol family 17

And while we're at it, further up the messages there were:

**** SET: Misaligned resource pointer: c7d72502 Type 07 len 0
ACPI: PCI Interrupt LInk [C158] enabled at IRQ 11
ACPI: PCI Interrupt 0000:00:09.0 [A} ->Link [C158] -> GSI 11 (level, low) -> IRQ 11
Detected Parameters Irq=11 BaseAddress=0x2800 ComADdress=0x2430


Does any of this tell us more about the problems with my laptop?


Thanks you, both!
Babysteps

---

### Post by Austin_KW on 2007-07-16
babysteps, have you got both the rt73 and ndiswrapper trying to manage the usb? you will need to blacklist one of them.

---

### Post by diepruis on 2007-07-17
> **digge said:**
> I did try it from the 14th, when the bug in the usb vendor list was just  fixed (the compile bug just above)... Still hard locks my whole system, this kernel however is stable as a rock. Might be some other laptop related module that they excluded though since its a laptop.

Havnt tried the 386 kernel but wouldnt want to loose the 686 optimizations, my laptop is realy slow as it is.

BTW, thanks for a great guide.

No problem, I'll add this information to a special troubleshooting section.

---

### Post by kevdog on 2007-07-17
Since this post is quickly approaching sticky status (***Hint to any forum admins monitoring this post***), I was wondering if you could add this to the original post.  Seems a lot of first time users try the advice in this post, but are having problems compiling the serial monkey source files since they do not understand that the build-essential package is a requirement.  You have already included information about installing the header files but was wondering if you could add something similar to the following:

> 
In order to compile the serial monkey drivers from source the build-essential package is required along with the linux kernel header files. If you already have an internet connection (ie a working wired ethernet connection), please skip to step #4.  Without any internet connection, please begin at step #1.

All commands typed at command prompt:
1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
2. sudo apt-cdrom add
3. sudo aptitude update
4. sudo aptitude install build-essential



5. (Would be a line to install the linux header files, since I assume these are coming from either the internet or the cd rom install)

---

### Post by Benadie on 2007-07-17
I have installed Feisty and have dowloaded (in Windows) the rt73 cvs files,  extracted in /usr/src/ and installed the build essentials from CD.

When I do sudo make, I get this output:

chris@chris-ubuntu:/usr/src/rt73-cvs-2007071315/Module$ sudo make
Password:
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /usr/src/rt73-cvs-2007071315/Module/rtmp_main.o
In file included from /usr/src/rt73-cvs-2007071315/Module/rt_config.h:187,
                 from /usr/src/rt73-cvs-2007071315/Module/rtmp_main.c:36:
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:819: error: expected identifier or â€˜(â€™ before â€˜{â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:819: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:821: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:823: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:823: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:826: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:826: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:826: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:830: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:832: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:832: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:835: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:837: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:837: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:840: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:842: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:842: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:845: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:847: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:847: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:850: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:850: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:853: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:853: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:853: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:857: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:857: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:860: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:860: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:863: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:863: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:866: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:868: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:868: error: expected identifier or â€˜(â€™ before â€˜,â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_def.h:868: error: expected identifier or â€˜(â€™ before â€˜}â€™ token
/usr/src/rt73-cvs-2007071315/Module/rtmp_main.c:71: error: expected expression before â€˜;â€™ token
make[2]: *** [/usr/src/rt73-cvs-2007071315/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/usr/src/rt73-cvs-2007071315/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
rt73.ko failed to build!
make: *** [module] Error 1

What does it mean and how do I fix it?

Thanks for a great forum
Francois

---

### Post by Benadie on 2007-07-17
I think I found the problem: the backslash after each hardware listed in the cvs file.  I downloaded the modified one (page 42 of this thread)

Will try it now and see

EDIT:
ealry in the morning and I have use the modified cvs file in this thread on page 41 not 42.  followed the rest of the how to on page 1 and it works a treat.  I am writing this edit using my wireless linkup !!

Linux forums are great - thanks to all you excellent hackers out there making available all of this info for the greater good

---

### Post by diepruis on 2007-07-18
> **kevdog said:**
> Since this post is quickly approaching sticky status (***Hint to any forum admins monitoring this post***), I was wondering if you could add this to the original post.  Seems a lot of first time users try the advice in this post, but are having problems compiling the serial monkey source files since they do not understand that the build-essential package is a requirement.  You have already included information about installing the header files but was wondering if you could add something similar to the following

You are correct. That's a pretty big oversight. It should be fixed now, though.

---

### Post by babysteps on 2007-07-19
> **Austin_KW said:**
> babysteps, have you got both the rt73 and ndiswrapper trying to manage the usb? you will need to blacklist one of them.

Austin_KW, I'm not sure how to totally uninstall Ndiswrapper.  I thought I had removed it.  I know that there was a point in time when I did lsmod |grep usb and I saw only the rt73 for a driver.   Or maybe because the computer didn't finish doing whatever it was doing when it freezes upon the USB's insertion? 

At this point I'm not sure what to do, except maybe look into internet sharing with my other laptop that's (knock on wood) on line by the end of the first day of Ubuntu. I can already tell that it's another puzzle to unravel....

---

### Post by diepruis on 2007-07-19
> **babysteps said:**
> Austin_KW, I'm not sure how to totally uninstall Ndiswrapper.  I thought I had removed it.  I know that there was a point in time when I did lsmod |grep usb and I saw only the rt73 for a driver.   Or maybe because the computer didn't finish doing whatever it was doing when it freezes upon the USB's insertion?

You don't need to remove ndiswrapper completely. Just add a line saying "blacklist ndiswrapper" to the file /etc/modprobe.d/blacklist.

---

### Post by kevdog on 2007-07-19
diepruis is correct about the blacklist statement, however if you want to remove ndiswrapper completely here are the instructions -- they are quite involved:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/)

---

### Post by pearlie on 2007-07-20
Thanks much - this worked most excellently!  :guitar:    ...... with one caveat: because the Belkin dongle was making this laptop act funny and lock up randomly, I had to go in and blacklist the other drivers FIRST before I could reboot and start at the beginning of your tutorial.  After that, it was smooth sailing :)!!  This could have just been an artifact of this particular machine, which is an 8 year old Thinkpad A20m which I've resurrected and installed Feisty on.  The old girl is working like a charm now.

---

### Post by File13 on 2007-07-21
Alright well i got my addlogix USB wireless adapter working perfectly with this so thanks very much for that. Only question is what if im out around and im searching for WiFi spots, since i removed the default tool in the tutorial i didnt know how i went about finding other AP's later on.

---

### Post by babysteps on 2007-07-21
> **diepruis said:**
> You don't need to remove ndiswrapper completely. Just add a line saying "blacklist ndiswrapper" to the file /etc/modprobe.d/blacklist.


OK, so I just reformatted in the mean time to get a clean slate.  I used a powered usb hub this time, and thank God the Belkin USB dongle did not freeze up Dapper like it did previously.  I still get error messages about the USB device "not accepting address 6...error  -110" or something like.

I just wanted to say that again I followed the instruction and got the rt73.ko made successfully and all that, but nothing.  I blacklisted, and rebooted.  Nothing stayed. I did the "sudo make clean" bit. and this time instead of getting the message that says "unstable Hardware" I get "Ignoring unknown interface wlan0=wlan0"

something about USB I have to know? 

Thanks for your help!

Babysteps

---

### Post by maarten80 on 2007-07-21
Super, this howto got my **sitecom WL-172 usb dongle **finally working! So simple...

This was the only thing preventing my parents from making the switch to ubuntu. Lets see how they like it now!

Thanks,
maarten

---

### Post by sunol on 2007-07-21
[COLOR="Red"]Solved! [/COLOR]This post pointed me in the right direction
[http://ubuntuforums.org/showthread.php?t=482406&highlight=failsafe+gnome](http://ubuntuforums.org/showthread.php?t=482406&highlight=failsafe+gnome)
I need to comment out the "pre-up" commands in the interfaces files for some reason. That did it and the USB stick still works great with my open access point.

Everything worked great following this thread. I am on the network. But now I am having a login problem. Posted to General Help.
[http://ubuntuforums.org/showthread.php?p=3057231#post3057231](http://ubuntuforums.org/showthread.php?p=3057231#post3057231)

Any hints on what I did wrong would be great!

Mike

---

### Post by the_original_bluefish on 2007-07-21
diepruis you are a legend. Your patience in helping so many with this issue is commendable!

I'm following the instructions on this page:
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver))

I've followed each instruction to the tee. I'm installing on Ubuntu 7.04 (Feisty). The kernel I have is 2.6.20-16-generic. I have a Belkin USB 54g wireless network adaptor (F5D7050 ver 3002au).

I'm at the end of the process, and I issue a sudo ifup rausb0 and unfortunately, all I get is 
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.

I've also tried a static ip setup but I still can't ping a local address.

What am I doing wrong?

/etc/network/interfaces
iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
wireless-essid home
wireless-key 12A4512D45AA3451E3451
auto rausb0


iwconfig
rausb0  RT73 WLAN ESSID:off/any
             Mode:Auto Channel=1 Bit Rate: 54 Mb/s
             RTS thr:off Fragment thr:off

ls /lib/modules/2.6.20-16-generic/extra
rt73.ko

cat /etc/modprobe.conf
alias rausb0 rt73

ls /etc/Wireless/RT73STA/
rt73.bin rt73sta.dat

---

### Post by the_original_bluefish on 2007-07-21
... ok... sorry... i thought this post was for this...
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver))

But it isn't. I tried your steps and they worked!... must update the help doco!

---

### Post by diepruis on 2007-07-22
> **babysteps said:**
> I just wanted to say that again I followed the instruction and got the rt73.ko made successfully and all that, but nothing.  I blacklisted, and rebooted.  Nothing stayed. I did the "sudo make clean" bit. and this time instead of getting the message that says "unstable Hardware" I get "Ignoring unknown interface wlan0=wlan0"

Curious... when you say that you get nothing, what exactly happens? Verbatim error messages would help a lot. From what you've given me, I can't even guess at what's gone wrong.

When you say "Nothing stayed" what do you mean by that?

EDIT: Forgot to mention that the error messages about the device not accepting its address points to a problem somewhere else. Could you try it in a different USB port and see if you still get those messages?

---

### Post by diepruis on 2007-07-22
> **pearlie said:**
> Thanks much - this worked most excellently!  :guitar:    ...... with one caveat: because the Belkin dongle was making this laptop act funny and lock up randomly, I had to go in and blacklist the other drivers FIRST before I could reboot and start at the beginning of your tutorial.  After that, it was smooth sailing :)!!  This could have just been an artifact of this particular machine, which is an 8 year old Thinkpad A20m which I've resurrected and installed Feisty on.  The old girl is working like a charm now.

I'll keep that in mind for when I encounter this type of error again, thanks.

---

### Post by diepruis on 2007-07-22
> **File13 said:**
> Alright well i got my addlogix USB wireless adapter working perfectly with this so thanks very much for that. Only question is what if im out around and im searching for WiFi spots, since i removed the default tool in the tutorial i didnt know how i went about finding other AP's later on.

That's a tough one. I suppose you could go download the RutilT utility from the serialmonkey website. That'll give you a GUI, or you could try some other application for this. I use the command line for this type of thing, so I can't really help, except to tell you how I do it:

*To scan for available networks*
```

iwlist wlan0 scan

```

The just use the appropriate section of the howto to connect to the right network. Hope this helps.

---

### Post by diepruis on 2007-07-22
> **the_original_bluefish said:**
> ... ok... sorry... i thought this post was for this...
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver))

But it isn't. I tried your steps and they worked!... must update the help doco!

Thanks for your kind words. I'll update the help docs in due course, i.e. when I have time and energy to check protocols and things like that.

---

### Post by gothelin on 2007-07-22
Thanks so much for this info, Diepruis.  Last night I tried installing this driver following the readme file.  It did actually work - for that session.  As soon as I restarted the computer it just wasn't possible to get the connection working again, no matter what I did!  Oh, it would claim it was working fine, however the inability to do anything net-related made me suspect that everything wasn't fine.  	:rolleyes:  In a fit of extreme frustration, I even totally re-installed the driver from scratch.  No joy.

Then I found your HOWTO.  I must admit, I started to feel a bit faint when I deleted network-manager and the connection immediately died.  However, upon restarting the connection was back and continues to *actually* be fine.  Woot!  :)  So, thanks again.  :)

---

### Post by diepruis on 2007-07-22
> **gothelin said:**
> Thanks so much for this info, Diepruis.  Last night I tried installing this driver following the readme file.  It did actually work - for that session.  As soon as I restarted the computer it just wasn't possible to get the connection working again, no matter what I did!  Oh, it would claim it was working fine, however the inability to do anything net-related made me suspect that everything wasn't fine.  	:rolleyes:  In a fit of extreme frustration, I even totally re-installed the driver from scratch.  No joy.

Then I found your HOWTO.  I must admit, I started to feel a bit faint when I deleted network-manager and the connection immediately died.  However, upon restarting the connection was back and continues to *actually* be fine.  Woot!  :)  So, thanks again.  :)

No problem, glad to hear it works.

---

### Post by mb108 on 2007-07-24
Very nice guide. 

Successfully used a variation on this to set up my rt61 driver from the serialmonkey CVS... just before I was going to trash Fiesty and roll back to 6.10.

You get stars!
:KS:KS:KS:KS:KS

---

### Post by Alex Broadbent on 2007-07-24
Hi, I've tried all these instructions and I still can't configure the device. It's seeing it but rausb0 up returns "no such device" messages. Any suggestions would be greatly appreciated! At least now plugging the device in doesn't make it freeze up...

---

### Post by diepruis on 2007-07-24
> **Alex Broadbent said:**
> Hi, I've tried all these instructions and I still can't configure the device. It's seeing it but rausb0 up returns "no such device" messages. Any suggestions would be greatly appreciated! At least now plugging the device in doesn't make it freeze up...

The interface name for this driver has changed. Please try using wlan0 instead of rausb0.

---

### Post by Alex Broadbent on 2007-07-25
I'm really not having much luck. To begin with, my laptop wireless card could see networks, but would not connect. Now it doesn't even see them (before I think it was using the rt73usb driver, which might explain why it could see the card and network but not use them). When I get to step 13 in your original instructions, I type -
sudo ifconfig wlan up
- as directed, and I get -
wlan: ERROR while getting interface flags: No such device

I'm sure you must be getting tired of answering questions like these by now. It's a real shame - if only this sort of thing were ironed out, people like me would dump Windows tomorrow.

Thanks,
Alex

---

### Post by kevdog on 2007-07-25
Did you blacklist the appropriate modules??

What driver is currently associated with your device --> lshw -C network

---

### Post by Alex Broadbent on 2007-07-25
Yes - I blacklisted rt73usb, rt2570, rt2500usb, rt2x00lib.

When I run the command you gave, I get:alex@alex-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 7c
       serial: 00:40:45:2a:c8:74
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.2 duplex=full ip=192.168.1.102 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: ioport:a000-a0ff iomemory:faffc800-faffc8ff irq:23
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT73 WLAN

---

### Post by kevdog on 2007-07-25
Ok lets just verify a few things:

sudo modprobe -l rt73
modinfo rt73
lsmod | grep rt73

Can you post 
/etc/iftab
/etc/network/interfaces

Have you looked through the system log: dmesg | more   to see if there is an error occuring??

---

### Post by Alex Broadbent on 2007-07-25
Hi,

I ran the first three lines and got the following:

alex@alex-laptop:~$ sudo modprobe -| rt73
Password:bash: rt73: command not found


[1]+  Stopped                 sudo modprobe - | rt73
alex@alex-laptop:~$ modinfo rt73
filename:       /lib/modules/2.6.20-15-generic/extra/rt73.ko
license:        GPL
description:    Ralink RT73 802.11abg WLAN Driver 1.0.3.6 CVS 2007072511
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     72CF115161B212940D46C85
alias:          usb:v2019pAB50d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB01d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0769p31F3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p90ACd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p9712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6229d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2671d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA861d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6877d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0023d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1472p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C04d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1631pC019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1724d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1723d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0722d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Dd*dc*dsc*dp*ic*isc*ip*
depends:        usbcore
vermagic:       2.6.20-15-generic SMP mod_unload # This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:40:45:2a:c8:74 arp 1
wlan0 mac 00:13:d3:76:cb:56 arp 1
parm:           debug:Debug mask: n selects filter, 0 for none (int)
parm:           firmName:Permit to load a different firmware: (default: rt73.bin)  (charp)
alex@alex-laptop:~$ lsmod | grep rt73
rt73                  226048  0 
usbcore               154416  4 rt73,ehci_hcd,uhci_hcd


You asked me to post /etc/iftab - here it is:

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:40:45:2a:c8:74 arp 1
wlan0 mac 00:13:d3:76:cb:56 arp 1

And finally, here's /etc/interfaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

# auto wmaster0
# iface wmaster0 inet dhcp


I looked through the system log but didn't see anything particularly exciting (I can post it though if you think it might help).

Thanks,
Alex

---

### Post by Austin_KW on 2007-07-25
Your interface is wlan1 (despite what is in iftab), this happens sometimes

confirm with "ifconfig -a"

Then configure wlan1 (not wlan0) in /etc/network/interfaces or using (ifconfig, iwconfig, iwpriv commands)


Edit; BTW that command was modprobe -l (l as in laugh) not the pipe symbol "|" ;)

---

### Post by diepruis on 2007-07-25
> **Alex Broadbent said:**
> 
sudo ifconfig wlan up


Just to be complete, that should be sudo ifconfig wlan0 (or wlan1) up

> **Alex Broadbent said:**
> 
I'm sure you must be getting tired of answering questions like these by now. It's a real shame - if only this sort of thing were ironed out, people like me would dump Windows tomorrow.

Thanks,
Alex

I honestly don't mind helping. I really hope that problems like these will become less and less in the next few years.

---

### Post by eduardsan on 2007-07-26
Thanks a lot Diepruis, your post was very helpful.

Just one comment, I followed all steps but after loading rt74 module I realized that my wlan0 interface was not there any more. I rebooted, it appeared and I could follow the rest of steps successfully. I'm not very knowledgeable about linux drivers so maybe you or someone else could explain why this happened and if there is a nicer solution than rebooting.

Thanks again!

---

### Post by diepruis on 2007-07-26
> **eduardsan said:**
> Just one comment, I followed all steps but after loading rt74 module I realized that my wlan0 interface was not there any more. I rebooted, it appeared and I could follow the rest of steps successfully. I'm not very knowledgeable about linux drivers so maybe you or someone else could explain why this happened and if there is a nicer solution than rebooting.

Maybe a hotplug malfunction?

---

### Post by eduardsan on 2007-07-28
I don't know, maybe. I was wondering whether it could be due to drivers unloading, but from your reply I assume it shouldn't. Thanks anyway!

---

### Post by diepruis on 2007-07-29
> **eduardsan said:**
> I don't know, maybe. I was wondering whether it could be due to drivers unloading, but from your reply I assume it shouldn't. Thanks anyway!

I don't really know, that was more of a guess :)

---

### Post by Alex Broadbent on 2007-07-29
Sorry for the slow reply. Changing wlan0 to wlan1 in the interfaces file worked! I'm thrilled! Thanks so much Austin KW and diepruis - really useful. - I had uninstalled Network Manager in one of my many efforts; am I ok to reinstall it now? It looked so nice, but I don't want to disturb the delicate balance...

Thanks again,
Alex

---

### Post by diepruis on 2007-07-30
> **Alex Broadbent said:**
> Sorry for the slow reply. Changing wlan0 to wlan1 in the interfaces file worked! I'm thrilled! Thanks so much Austin KW and diepruis - really useful. - I had uninstalled Network Manager in one of my many efforts; am I ok to reinstall it now? It looked so nice, but I don't want to disturb the delicate balance...

Thanks again,
Alex

I wouldn't recommend it. AFAIK that problem isn't fixed yet.

---

### Post by Alex Broadbent on 2007-07-30
Just to summarise - I reinstalled the system to see which of the various changes I had made, following various Googles, was making the difference. In the end it seems the following three steps sufficed to get my wireless network card up and running:
1) Search for and install kwlan with the Synaptics Package Manager (this automatically unintalls various other things, including Network Manager).
2) Run sudo gedit /etc/network/interfaces and change instances of wlan0 to wlan1.
3) Follow the excellent instructions on page 1 of this thread, but replacing wlan0 with wlan1.

Perhaps one (or more) of these steps is obsolete... Anyway, I'm happy, it worked!

Thanks again,
Alex

---

### Post by 1feistymedic on 2007-07-30
Hello..Can any of you guys/gals hop on over to the below post to help me out?  I looked at all the pages of this post and still cant get things to work...before I get too far and screw up my system, I would rather have your expert advice..and remember, I am as new as they come.....thanks


[http://ubuntuforums.org/showthread.php?t=512647](http://ubuntuforums.org/showthread.php?t=512647)

---

### Post by Albaraha on 2007-07-31
I'm running Ubuntu 7.04 and blacklisted the specified modules coming with th system.
I have compiled rt73.ko and installed it.
I reached the step **13 Configure the interface.** of your guide, and the system tries to get the IP but it couldn't. Providing the IP (Static) doesn't allow me to ping or reach the network.
I disabled the encryption (security) in the router, and that didn't help as well.

What I have is _**Linksys Wireless-G USB Adpater WUSB54GC**_ which Ubuntu claims that it supports it in version 7.0, while it didn't work.

---

### Post by Albaraha on 2007-07-31
Wow. at last I'm back with ubuntu.
It works. Thanks diepruis.
The mistake I did before was to compile RT73_Linux_STA_Drv1.0.4.0.tar.gz which I downloaded from: [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
This driver didn't work, the one provided in this tutorial works as expected.

---

### Post by diepruis on 2007-07-31
> **Albaraha said:**
> Wow. at last I'm back with ubuntu.
It works. Thanks diepruis.
The mistake I did before was to compile RT73_Linux_STA_Drv1.0.4.0.tar.gz which I downloaded from: [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
This driver didn't work, the one provided in this tutorial works as expected.

That can be confusing, unfortunately. Glad to hear you got it working!

---

### Post by markiep on 2007-08-03
after step 12 i just rebooted my laptop and used Network settings and just filled in the blanks and with crossed finger it worked! standard WEP 128 hex and my SSID.  Thank you so much 20 hours and 3 different tries with other How Tos  i was getting pretty frustrated.  ohh yeah xubuntu also. gotta love the little green light flashing :lolflag:

---

### Post by dannyboy79 on 2007-08-03
still can't get my Belkin Belkin FD..5070  to work in gutsy tribe 3 even using the source that the guide links to (which was rt73 cvs daily or somethign like that)

---

### Post by diepruis on 2007-08-03
> **markiep said:**
> after step 12 i just rebooted my laptop and used Network settings and just filled in the blanks and with crossed finger it worked! standard WEP 128 hex and my SSID.  Thank you so much 20 hours and 3 different tries with other How Tos  i was getting pretty frustrated.  ohh yeah xubuntu also. gotta love the little green light flashing :lolflag:

Glad to hear it. Users are welcome to try any GUI method of configuration, but the HOWTO instructions will remain terminal based because it makes the job easier for people providing support.

---

### Post by diepruis on 2007-08-03
> **dannyboy79 said:**
> still can't get my Belkin Belkin FD..5070  to work in gutsy tribe 3 even using the source that the guide links to (which was rt73 cvs daily or somethign like that)

Do you think it's a configuration error? If you don't, you should go post a bug in the appropriate place on the rt2x00 website (rt2x00.serialmonkey.com).

---

### Post by dannyboy79 on 2007-08-03
well if I follow the guide to a tee, the light does blink on it, wlan0 does show up but it just can never connect. it keeps trying DHCPDISCOVER over and over again and never works. I use the same wep key with my other wireless card in my laptop so I know that's not it.

---

### Post by diepruis on 2007-08-03
> **dannyboy79 said:**
> well if I follow the guide to a tee, the light does blink on it, wlan0 does show up but it just can never connect. it keeps trying DHCPDISCOVER over and over again and never works. I use the same wep key with my other wireless card in my laptop so I know that's not it.

What does iwconfig report your signal strength as?

---

### Post by dannyboy79 on 2007-08-03
unfortunately I am not at home right now. i'll have to post back. thanks for the help with this.
FYI, I am in the next room with a 2x4 wall thickness that has drywall/paint on it. The netgear pcmcia card is even further and that never has a problem connecting. It uses the Atheros AR5212 within Xubuntu Feisty on an ancient Hitachi 266mhz Pentium MMX 128mb ram. Neomagic 4mb video ram.

---

### Post by diepruis on 2007-08-03
> **dannyboy79 said:**
> unfortunately I am not at home right now. i'll have to post back. thanks for the help with this.
FYI, I am in the next room with a 2x4 wall thickness that has drywall/paint on it. The netgear pcmcia card is even further and that never has a problem connecting. It uses the Atheros AR5212 within Xubuntu Feisty on an ancient Hitachi 266mhz Pentium MMX 128mb ram. Neomagic 4mb video ram.

It shouldn't be a problem... but low signal strength could indicate a bug in the driver source code.

---

### Post by Austin_KW on 2007-08-03
> **dannyboy79 said:**
> well if I follow the guide to a tee, the light does blink on it, wlan0 does show up but it just can never connect. it keeps trying DHCPDISCOVER over and over again and never works. I use the same wep key with my other wireless card in my laptop so I know that's not it.

Also check your dmesg output for firmware load failures or usb probe failures.

And try removing/reinserting the dongle and "sudo ifup --f wlan0".  I still see occasional race conditions on feisty boot and doing this will fix it for my 7050v3

---

### Post by sefs on 2007-08-03
Hi there,

I am giving another shot at trying to migrate from ndiswrapper to this driver.  Ran int a hitch after sudo make install....

I get this at the very end...

```

*** Update /etc/modprobe.conf alias for wlan*
*** Install firmware in /lib/firmware ...
*** Check config ...
!!!
!!! WARNING: DEPRECATED CONFIG FOUND !
!!!
!!! -> Update your config and remove /etc/Wireless/RT73STA
!!! -> rt73.bin firmware has moved to /lib/firmware


```

I've only been using ndiswrapper for my networking period, I believe.

my modprobe.conf looks like this ..

```

alias wlan* rt73

```

There is an rt73.bin located at 
/etc/Wireless/RT73STA and /lib/firmware

for good measure i copied rt73.bin from the Module directory of the driver i downloaded to /lib/firmware over what was there.

Can anyone guide me from there?

Thanks.


with regards to the below

```

auto wlan0
iface wlan0 inet dhcp
    pre-up ifconfig wlan0 up
    pre-up iwconfig wlan0 essid "YOUR_ESSID"
    pre-up iwconfig wlan0 mode managed
    pre-up iwpriv wlan0 set AuthMode=WPAPSK
    pre-up iwpriv wlan0 set EncrypType=TKIP
    pre-up iwpriv wlan0 set WPAPSK="YOUR_WPA_PSK_KEY"
    pre-up iwpriv wlan0 set SSID="YOUR_SSID"

```

Is your_essid and your_ssid suppose to be the same values?  Also should we ignore the quotes?
What about the  "your_wpa_psk_key" ignore quotes again?

EncrypType ... formally i used WPA2 with AES i believe  should i replace TKIP with RSN or CCMP or something like that?

---

### Post by sefs on 2007-08-03
Ok I finally got it up and working with the following in interfaces, and by removing or commenting out alias "wlan* rt73" from /etc/modprobe.conf and removing the /etc/Wireless/RT73STA folder as specifed in an earlier post in this thread.


```

auto wlan0
iface wlan0 inet static
address 192.168.1.xxx
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.x
        pre-up ifconfig wlan0 up
        pre-up iwconfig wlan0 essid linksys
    	pre-up iwconfig wlan0 mode managed
    	pre-up iwpriv wlan0 set SSID=linksys
    	pre-up iwpriv wlan0 set Channel=6
    	pre-up iwpriv wlan0 set NetworkType=Infra
    	pre-up iwpriv wlan0 set AuthMode=WPA2PSK
    	pre-up iwpriv wlan0 set EncrypType=AES
    	pre-up iwpriv wlan0 set WPAPSK=244444449494939393939393929292929292

```

What confuses me though is why we need 
```

        pre-up iwconfig wlan0 essid linksys
    	pre-up iwconfig wlan0 mode managed

```

when 

```

    	pre-up iwpriv wlan0 set SSID=linksys
    	pre-up iwpriv wlan0 set NetworkType=Infra

```

Seems to be doing the same thing...can someone explain?

Thanks.

---

### Post by diepruis on 2007-08-04
> **sefs said:**
> Ok I finally got it up and working with the following in interfaces

Glad to hear you got it working.

> **sefs said:**
> 
What confuses me though is why we need 
```

        pre-up iwconfig wlan0 essid linksys
    	pre-up iwconfig wlan0 mode managed

```

when 

```

    	pre-up iwpriv wlan0 set SSID=linksys
    	pre-up iwpriv wlan0 set NetworkType=Infra

```

Seems to be doing the same thing...can someone explain?

Thanks.

Have you tried with only the latter settings?

---

### Post by sefs on 2007-08-04
Yes with the iwpriv only setting after "pre-up  ifconfig wlan0 up". And it seems to work ok.

I think that you can either go all iwpriv or all iwconfig but dont need to duplicate in the interfaces file.

---

### Post by diepruis on 2007-08-04
> **sefs said:**
> Yes with the iwpriv only setting after "pre-up  ifconfig wlan0 up". And it seems to work ok.

I think that you can either go all iwpriv or all iwconfig but dont need to duplicate in the interfaces file.

I suspect so as well.

EDIT: changed HOWTO and credited you.

---

### Post by blahfod on 2007-08-05
excellent guide

i managed to get wireless working with wep following the how to flawlessly, however, when i try to enable the WPA i get nothing. 

I have edited the interface following every example in this forum yet when i run sudo dhcclient wlan0 it attempts to receive DHCP an a number of different ports, then it attempts to ping the router and returns 100 percent packet loss and goes to sleep.

what am I doing wrong?

my interface looks like this

auto wlan0
iface wlan0 inet dhcp
        pre-up ifconfig wlan0 up
        pre-up iwconfig wlan0 essid fod
    	pre-up iwconfig wlan0 mode managed
    	pre-up iwpriv wlan0 set SSID=fod
    	pre-up iwpriv wlan0 set NetworkType=Infra
    	pre-up iwpriv wlan0 set AuthMode=WPA2PSK
    	pre-up iwpriv wlan0 set EncrypType=TKIP
    	pre-up iwpriv wlan0 set WPAPSK=censored
my router is configured to accept both AES and TKIP as well as both WPA and WPA2 automatically.

can someone shed some light on my troubles,
thanks
blahfod

---

### Post by kevdog on 2007-08-05
blahod

Can you post the results of iwlist scan, sometimes this gives secrets of best to configure your iwpriv statements.

---

### Post by Austin_KW on 2007-08-05
> **blahfod said:**
> excellent guide

i managed to get wireless working with wep following the how to flawlessly, however, when i try to enable the WPA i get nothing. 

I have edited the interface following every example in this forum yet when i run sudo dhcclient wlan0 it attempts to receive DHCP an a number of different ports, then it attempts to ping the router and returns 100 percent packet loss and goes to sleep.

what am I doing wrong?

my interface looks like this

auto wlan0
iface wlan0 inet dhcp
        pre-up ifconfig wlan0 up
        pre-up iwconfig wlan0 essid fod
    	pre-up iwconfig wlan0 mode managed
    	pre-up iwpriv wlan0 set SSID=fod
    	pre-up iwpriv wlan0 set NetworkType=Infra
    	pre-up iwpriv wlan0 set AuthMode=WPA2PSK
    	pre-up iwpriv wlan0 set EncrypType=TKIP
    	pre-up iwpriv wlan0 set WPAPSK=censored
my router is configured to accept both AES and TKIP as well as both WPA and WPA2 automatically.

can someone shed some light on my troubles,
thanks
blahfod

Change your router to wpa1/tkip and the AuthMode=WPAPSK. I have problems if my router is set to both wpa1/wpa2

---

### Post by blahfod on 2007-08-05
thanks for the quick response, the only trouble i have with that is on the windows partition i am using a dwa-552 draft n pci card. I have tried in vane to get it to work in ubuntu. as a last resort i started to try and use the dwl-g122 to try adn get access to the net on the ubuntu side. If i disable the mixed wpa and wpa2 mode as well as the mixed aes and tkip options on my router i lose the high speed connectivity on the windows side. I was hoping to get it so that in windows i can use the pci card, and in ubuntu i could use the usb card without having to constantly fiddle with the router settings. 

I will nevertheless try your recommends and see at least if i can get connected like that.

thanks 

blahfod

---

### Post by dannyboy79 on 2007-08-06
WAHOOOOO!!!

I finally got it, I've been trying on and off starting with Edgy. I purchased the Belkin F5D7050 (lsusb reports: Bus 001 Device 003: ID 050d:705a Belkin Components) because I thought it was compatible out of the box, well NOT with the modules that come with Edgy, Feisty or even Gutsy (im aware that Gutsy isn't done yet so hopefully they use the latest cvs of rt73 from serialmonkey)

Setup Info:
Dell Dimension 8200 w/ 256mb RAM
GeForce4 MX 420
Ubuntu Version: Gutsy Gibbon Tribe 3 (2.6.22-9-generic kernel)

I followed the instructions to the "T" but instead of using the link that points to the cvs rt73 in the guide, I went to serialmonkey and download that one myself. I use 128bit WEP (open) instead of WAP because another wifi adapter doesn't have WPA. Anyway, the instructions for static ip after the guide worked and I am all set.

Thank you thank you thank you!!!!


NOTE: one thing I made sure was that I deleted all previous .bin files (firmware) and .ko files (module) that I found scattered around the system. Just do a 
sudo find / -name rt73*.* 
that returned
/lib/firmware/2.6.22-8-generic/rt73.bin 
/lib/firmware/rt73.bin 
/lib/firmware/2.6.22-9-generic/rt73.bin 
/lib/modules/2.6.22-9-generic/extra/rt73.ko 
I then removed all those IF you tried and it didn't work with a previous rt73 cvs download. This is what the sudo find / -name rt73*.* should look like when it's working.
/lib/firmware/rt73.bin
/lib/modules/2.6.22-9-generic/extra/rt73.ko
/lib/modules/2.6.22-9-generic/ubuntu/wireless/rt2x00/rt73usb.ko
/usr/src/linux-headers-2.6.22-9-generic/rt73-cvs-daily.tar.gz
/usr/src/rt73-cvs-2007080606/Module/.tmp_versions/rt73.mod
/usr/src/rt73-cvs-2007080606/Module/rt73.ko
/usr/src/rt73-cvs-2007080606/Module/rt73.bin
/usr/src/rt73-cvs-2007080606/Module/rt73.o
/usr/src/rt73-cvs-2007080606/Module/rt73.h
/usr/src/rt73-cvs-2007080606/Module/rt73.mod.o
/usr/src/rt73-cvs-2007080606/Module/rt73.mod.c

This is what my interfaces file looks like:
auto wlan0
iface wlan0 inet static
address 192.168.0.6
netmask 255.255.255.0
network 192.168.0.1
gateway 192.168.0.1
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid ESSID HERE
pre-up iwconfig wlan0 key HEX KEY HERE


GOOD LUCK

---

### Post by diepruis on 2007-08-06
> **dannyboy79 said:**
> WAHOOOOO!!!

I finally got it...


Hey finally! I'm so glad it worked out for you in the end!

---

### Post by durfff on 2007-08-06
Yo, 

I used this thread a while ago when trying to set up my D-LINK USB dongle, and it was great help. I got most of my very limited knowledge in Linux trying to install the damn thing in fact!

Anyways, was doing fine (had to ifdown-up a few times but hey, was alright), until recently. Now every so often (too often - grrrr) there is what appears to be a loss of connection, but iwconfig still returns that wireless is working (signal ok and all). I used to try ifdown wlan0 but now there's no success, it hangs after the first DHCP Release line...

I have to shut the terminal and if I reopen and retry, it just creates loads of blank line in a loop, weird. After the second attempt, usually everything gets half-frozen: trying to start the terminal only opens the "Starting Terminal" in the task bar, but that disappears and terminal doesn't start. Same for any other application. 

More worryingly, the shut-down menu doesn't show up. And even worse, ctrl-alt-backspace doesn't do a thing.

I'm a bit stuck and probably in need of some expert help. I can post various command outputs for you but I don't know where to start... Puzzled really. Any help appreciated

Cheers

Fred

---

### Post by Austin_KW on 2007-08-06
Rather than ifdown followed by ifup try;
"sudo ifup --f wlan0"            (note the double '-')
Might work a bit better as it may not have to release resources just renew them. And its quicker :)

---

### Post by MathSWE on 2007-08-06
Hi all!

Got the rt73 driver working smoothly! Excellent tutorial! Wish the rt73 was shipped with Ubuntu! :)

However, there is a problem that I cant seem to find a solution for.

After a few hours the RT73-driver module hogs about 98% of my CPU, and the system more or less hangs... I found another thread describing this problem, but no solution.

Why is this happening? Can I fix it?

Thanks anyway for a great driver install description!!!!!

Bests regards

Mathias

---

### Post by diepruis on 2007-08-07
> **durfff said:**
> Yo, 

I used this thread a while ago when trying to set up my D-LINK USB dongle, and it was great help. I got most of my very limited knowledge in Linux trying to install the damn thing in fact!

Anyways, was doing fine (had to ifdown-up a few times but hey, was alright), until recently. Now every so often (too often - grrrr) there is what appears to be a loss of connection, but iwconfig still returns that wireless is working (signal ok and all). I used to try ifdown wlan0 but now there's no success, it hangs after the first DHCP Release line...

I have to shut the terminal and if I reopen and retry, it just creates loads of blank line in a loop, weird. After the second attempt, usually everything gets half-frozen: trying to start the terminal only opens the "Starting Terminal" in the task bar, but that disappears and terminal doesn't start. Same for any other application. 

More worryingly, the shut-down menu doesn't show up. And even worse, ctrl-alt-backspace doesn't do a thing.

I'm a bit stuck and probably in need of some expert help. I can post various command outputs for you but I don't know where to start... Puzzled really. Any help appreciated

Cheers

Fred

Did you change anything right before the problem started?

---

### Post by diepruis on 2007-08-07
> **MathSWE said:**
> Hi all!

Got the rt73 driver working smoothly! Excellent tutorial! Wish the rt73 was shipped with Ubuntu! :)

However, there is a problem that I cant seem to find a solution for.

After a few hours the RT73-driver module hogs about 98% of my CPU, and the system more or less hangs... I found another thread describing this problem, but no solution.

Why is this happening? Can I fix it?

Thanks anyway for a great driver install description!!!!!

Bests regards

Mathias

No problem. Please try to install a new version of the source code from the serialmonkey web site, it might be a recent problem. If the problem still persists, you might want to install linux-386, boot into the kernel that installs and follow the guide again. Other than that, I'm not sure what the problem could be.

---

### Post by Jhet on 2007-08-07
&#65279;Firstly I would like to thank Diepruis for his excellent guide.  I tried getting my wireless to work ages ago when i first switched to ubuntu.  I use a Belkin F5D7050. 
Lsusb states ```
Bus 005 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
```

When I first plugged it in it loaded the rt73 drivers in ubuntu, these didn't work, I tried ndiswrapper and this also failed.  Then I came across this tutorial.  Now I followed the guide, and it didn't work for me.  However I noticed that after removing all of the rt* drivers in ubuntu, and forcefully deleting them from the kernel folder (hope this doesn't cause serious problems) since they seemed to still be loading after being blacklisted. It still didn't work, but it was loading the rt73 driver from serialmonkey.  I then noticed that the system was also trying to use the prism54usb driver, so i purged all of the prism drivers too.  I finally decided that I should actually look at the chipset in the adapter and I found it was an RT2571F.  Serialmonkey has the drivers for this adapter and your instructions work fine for those too, just replace the driver name accordingly.  Their rutilit utility works great as well.

My only problem now is that I cannot get the adapter to come up on start-up so I can set a static ip.  What command would do this in /etc/network/interfaces  ? When I followed the instructions in your guide, it still doesn't bring the interface up.

Thanks again.

---

### Post by Austin_KW on 2007-08-07
> **Jhet said:**
> &#65279;Firstly I would like to thank Diepruis for his excellent guide.  I tried getting my wireless to work ages ago when i first switched to ubuntu.  I use a Belkin F5D7050. 
Lsusb states ```
Bus 005 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
```

When I first plugged it in it loaded the rt73 drivers in ubuntu, these didn't work, I tried ndiswrapper and this also failed.  Then I came across this tutorial.  Now I followed the guide, and it didn't work for me.  However I noticed that after removing all of the rt* drivers in ubuntu, and forcefully deleting them from the kernel folder (hope this doesn't cause serious problems) since they seemed to still be loading after being blacklisted. It still didn't work, but it was loading the rt73 driver from serialmonkey.  I then noticed that the system was also trying to use the prism54usb driver, so i purged all of the prism drivers too.  I finally decided that I should actually look at the chipset in the adapter and I found it was an RT2571F.  Serialmonkey has the drivers for this adapter and your instructions work fine for those too, just replace the driver name accordingly.  Their rutilit utility works great as well.

My only problem now is that I cannot get the adapter to come up on start-up so I can set a static ip.  What command would do this in /etc/network/interfaces  ? When I followed the instructions in your guide, it still doesn't bring the interface up.

Thanks again.


Just to make it clear for people searching on the usb id "050d:7050", These are usually not the rt73 chipset, some are ralink rt2570 (rt2500usb in windows), some are prism and I think the v1 was broadcom. Belkin did not update the ID eprom when they changed the chipset, helpfully adding to the list of drivers that need to  be blacklisted.

You should be able to set up a static address as per the example given in the original post. You may need to replace wlan0 with rausb0, but I can't remember if serialmonkey has changed the rt2570 interface to wlan0 (I have donated my 2570 to a family member)

---

### Post by Jhet on 2007-08-07
just retried the interfaces config and it worked. must of done it wrong the first few times :(
Thank you for you help.  The rt2570 driver is rausb0 still.

---

### Post by b.mann on 2007-08-07
I need a little help getting this to set up. The .gz extension, is that any different than the .tar file? Every time I copy paste the code, the terminal can't find the file, even though it's sitting right on my desktop. 
Thanks for any help provided,

Ben

---

### Post by dannyboy79 on 2007-08-07
> **Austin_KW said:**
> Just to make it clear for people searching on the usb id "050d:7050", These are usually not the rt73 chipset, some are ralink rt2570 (rt2500usb in windows), some are prism and I think the v1 was broadcom. Belkin did not update the ID eprom when they changed the chipset, helpfully adding to the list of drivers that need to  be blacklisted.

You should be able to set up a static address as per the example given in the original post. You may need to replace wlan0 with rausb0, but I can't remember if serialmonkey has changed the rt2570 interface to wlan0 (I have donated my 2570 to a family member)
just an FYI, i own the Belikn wireless USB adapter that's model number is F5D7050 and when I opened it up (just put fingernail in crack and spread apart, you won't break it) the actual CHIP on the circuit board did say rt2570.

lsusb states: Bus 001 Device 003: ID 050d:705a Belkin Components

and the latest cvs rt73 from serialmonkey DOES work if you follow the instructions.

---

### Post by dannyboy79 on 2007-08-07
> **b.mann said:**
> I need a little help getting this to set up. The .gz extension, is that any different than the .tar file? Every time I copy paste the code, the terminal can't find the file, even though it's sitting right on my desktop. 
Thanks for any help provided,

Ben

have you cd'd to your desktop directory if that's where it is or are you issuing the tar command and entering the full path to the file?

why aren't you following the guide. I know it doesn't matter where you extract it but it's just easier to follow what works.

sudo cp ~/Desktop/rt73-cvs-daily.tar.gz /usr/src
(IF it's on your desktop)

sudo tar -xvzf rt73-cvs-daily.tar.gz

and so on........

---

### Post by b.mann on 2007-08-07
> have you cd'd to your desktop directory if that's where it is or are you issuing the tar command and entering the full path to the file?

why aren't you following the guide. I know it doesn't matter where you extract it but it's just easier to follow what works.

sudo cp ~/Desktop/rt73-cvs-daily.tar.gz /usr/src
(IF it's on your desktop)

sudo tar -xvzf rt73-cvs-daily.tar.gz

and so on........ 


no i hadnt done the cd yet, didnt know that I needed to because I cannot access my usr/src (says access denied)

---

### Post by dannyboy79 on 2007-08-07
follow the guide please. it states to use sudo. just please read and follow the guide!

---

### Post by b.mann on 2007-08-07
I am, except for the fact that now I cannot tell the system to detect my network because my wlan0 device disappeared.

---

### Post by babysteps on 2007-08-07
> **Jhet said:**
> &#65279;Firstly I would like to thank Diepruis for his excellent guide.  I tried getting my wireless to work ages ago when i first switched to ubuntu.  I use a Belkin F5D7050. 
Lsusb states ```
Bus 005 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
```

When I first plugged it in it loaded the rt73 drivers in ubuntu, these didn't work, I tried ndiswrapper and this also failed.  Then I came across this tutorial.  Now I followed the guide, and it didn't work for me.  However I noticed that after removing all of the rt* drivers in ubuntu, and forcefully deleting them from the kernel folder (hope this doesn't cause serious problems) since they seemed to still be loading after being blacklisted. It still didn't work, but it was loading the rt73 driver from serialmonkey.  I then noticed that the system was also trying to use the prism54usb driver, so i purged all of the prism drivers too.  I finally decided that I should actually look at the chipset in the adapter and I found it was an RT2571F.  Serialmonkey has the drivers for this adapter and your instructions work fine for those too, just replace the driver name accordingly.  Their rutilit utility works great as well.

My only problem now is that I cannot get the adapter to come up on start-up so I can set a static ip.  What command would do this in /etc/network/interfaces  ? When I followed the instructions in your guide, it still doesn't bring the interface up.

Thanks again.


I have the exact same Belkin that you have, and Yes I opened up the usb stick and saw that it was a rt2571 chip.  Using Diepruis' instruction I had gotten everything to build perfectly, also having gone through the process of purging the islsm_usb that Dapper tried to load, but somehow I just couldn't get online.  I was driving myself crazy trying to get the right set of rules to follow.  It seems that in Dapper, even though the network manager wasn't "installed" the Network Monitor applet was installed, and was probably conflicting with me trying to configure it in  /etc/network/interfaces....In the mean time, only just yesterday, actually, I switched to Kubuntu and got my laptop to work with a Netgear card with the "wireless assistant", having given up on the Belkin after 4 months of researching and trying.

Well, it's great to hear that someone with the exact usb stick got it to work! I knew that there will be victory, somewhere, sometime soon!

Just for future reference, Could you tell me exactly which driver from Serial Monkey you used?  I remember looking for it, but only seeing the rt2570.  Also I thought the title of this thread implied that it can be for RT73 and RT71, but I guess it's still different from rt2571?

Again, congrats! 

Also, another thanks for Diepruis and others on this thread who are so dedicated in getting it to work!

---

### Post by diepruis on 2007-08-08
> **b.mann said:**
> I am, except for the fact that now I cannot tell the system to detect my network because my wlan0 device disappeared.

I'm confused. Why were you trying to install the driver if wlan0 was already being detected? Did the interface not work?

---

### Post by Jhet on 2007-08-08
> **babysteps said:**
> 
Just for future reference, Could you tell me exactly which driver from Serial Monkey you used?  I remember looking for it, but only seeing the rt2570.  Also I thought the title of this thread implied that it can be for RT73 and RT71, but I guess it's still different from rt2571?


I Used the rt2570 driver from serialmonkey, since it was closest in number to rt2571.  That was my logic, but since > **Austin_KW said:**
> some are ralink rt2570 (rt2500usb in windows), and my windows drivers (from my belkin cd) are rt2500usb, that seems to confirm rt2570 to be the right one.

---

### Post by Austin_KW on 2007-08-08
> **Jhet said:**
> I Used the rt2570 driver from serialmonkey, since it was closest in number to rt2571.  That was my logic, but since  and my windows drivers (from my belkin cd) are rt2500usb, that seems to confirm rt2570 to be the right one.

Yes checking the windows driver is probably the easiest way for the belkin sticks. The rev 3000 will be rt73.sys, the ID may have changed to 050d:705A from 050d:7050, and I think the chip changes to a 2571wf or 2571w.

---

### Post by babysteps on 2007-08-08
> **Austin_KW said:**
> Yes checking the windows driver is probably the easiest way for the belkin sticks. The rev 3000 will be rt73.sys, the ID may have changed to 050d:705A from 050d:7050, and I think the chip changes to a 2571wf or 2571w.


Quote:
Originally Posted by Jhet View Post
I Used the rt2570 driver from serialmonkey, since it was closest in number to rt2571. That was my logic, but since and my windows drivers (from my belkin cd) are rt2500usb, that seems to confirm rt2570 to be the right one.[/QUOTE]

Actually, I had tried the rt2570 from serialmonkey before trying the rt73, going on similar logic as you.  It didn't work for me then, probably because of other problems with the laptop's usb being unstable.  I'll keep that in mind for next time, when who knows which computer I will attempt to change to ubuntu...:)

just to clarify things though, Jhet, and Austin_KW, do we agree that this particular USB stick is a version 1000, and not rev 3000?  

babysteps

---

### Post by durfff on 2007-08-08
Yo!

No I didn't change anything but reading the messages after mine what MathSWE detailed looks like mine, so I'll try getting w newer version from serialmonkey and see if that helps. Yay.

---

### Post by b.mann on 2007-08-08
> **diepruis said:**
> I'm confused. Why were you trying to install the driver if wlan0 was already being detected? Did the interface not work?

I dont know, I thought that this is what I had to do in order for my wireless to work. Since it was detected earlier, what should  Ido to setup the connection?

---

### Post by bdann on 2007-08-08
This worked great for me.  Only thing different is my interface came up as wlan1 instead of wlan0, took me a minute to figure this out.  FINALLY have wireless LAN on ubuntu, oh happy day.

---

### Post by nandemonai on 2007-08-08
I followed the guide and for some reson when trying to bring up the interface (ifup wlan0) it continually throws BUG: scheduling while atomic: swapper/0x100000100/0

The term is still 'active' in that I can sudo ifdown wlan0 and it stops.

Any ideas?

With a seemingly good /etc/network/interfaces I still get no joy :?

---

### Post by diepruis on 2007-08-09
> **nandemonai said:**
> I followed the guide and for some reson when trying to bring up the interface (ifup wlan0) it continually throws BUG: scheduling while atomic: swapper/0x100000100/0

The term is still 'active' in that I can sudo ifdown wlan0 and it stops.

Any ideas?

With a seemingly good /etc/network/interfaces I still get no joy :?

Are you sure that the device is really an RT73 and that no other modules are loaded that conflict with rt73?

---

### Post by diepruis on 2007-08-09
> **b.mann said:**
> I dont know, I thought that this is what I had to do in order for my wireless to work. Since it was detected earlier, what should  Ido to setup the connection?

Try network manager first, unless you're sure it's an RT73 device. In that case we have to diagnose your problem, since the default rt73 modules will almost definitely not work.

---

### Post by nandemonai on 2007-08-09
> **diepruis said:**
> Are you sure that the device is really an RT73 and that no other modules are loaded that conflict with rt73?

Apologies on the very brief thread. Lack of sleep to blame there. I'll go into a little more detail.

Okies, essentially I have a Toshiba Satellite here, 333mhz/64mb ram.

I managed to get feisty on it via the xubuntu alternate installer. (As a sidenote for people trying to install xubuntu on a lappy with 64 mb, anthy will take a very very long time. You can safely hop to a term via alt F2 and find the ps id and kill it with seemingly no real issues. Installer continues fine. I just didn't have the time to wait over 2 hours for the dictionary to be 'configured'. Anyhoo.)

So, the problem I have is no network onboard. Hence I have a TP-Link TL-WN321G, usb wifi dongle thingo. I know for a fact it's the rt73 as I've had the thing work in windows with the ralink drivers no sweat and when feisty first started up it did recognise it and loaded the rt73usb module which of course didn't work. Actually anytime I tried to use the device the machine would 'almost' hang, in that the current term would halt and I'd have to switch to a new console. (TUI only btw)

So after much searching and almost giving up on this machine running ubuntu vs *shudder* Win 98 I finally found this thread, followed it and got the driver compiled fine. I removed the old modules listed here in the thread and also blacklisted them. Rebooted just to be safe.

So now the device is recognised. lsusb shows:

Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp.
Bus 001 Device 001: ID 0000:0000

dmesg:

rtusb init ====>
idVendor = 0x148f, idProduct = 0x2573
cs: IO  port probe etc etc no errors.

Now as far as conflicting modules I'm not sure. dmesg does say rtusb but I'm not sure if that means rt73usb vs rt73. I assume my blacklist took.

How would I go about making sure nothing is conflicting?

I'm soooo close! ;)

Appreciate the help.

---

### Post by kevdog on 2007-08-09
Do serial monkey drivers support wpa2??  If so how do you configure the /etc/network/interfaces file?  There seems to be a big debate whether wpa2 is supported by these drivers!

---

### Post by diepruis on 2007-08-09
> **nandemonai said:**
> dmesg:

rtusb init ====>
idVendor = 0x148f, idProduct = 0x2573
cs: IO  port probe etc etc no errors.

Now as far as conflicting modules I'm not sure. dmesg does say rtusb but I'm not sure if that means rt73usb vs rt73. I assume my blacklist took.

How would I go about making sure nothing is conflicting?

I'm soooo close! ;)

Appreciate the help.

Try 

```

dmesg | grep rt73

```

As well as...

```

dmesg | grep RT73

```

I think you only got alf there...

---

### Post by nandemonai on 2007-08-09
> **diepruis said:**
> Try 

```

dmesg | grep rt73

```

As well as...

```

dmesg | grep RT73

```

I think you only got alf there...

$ sudo dmesg | grep rt73
usbcore: registered new interface driver rt73
$

$ sudo dmesg | grep RT73
$

So, what did I miss? ;)

---

### Post by Austin_KW on 2007-08-09
> **nandemonai said:**
> Apologies ...

How would I go about making sure nothing is conflicting?

I'm soooo close! ;)

Appreciate the help.


The command "lsmod | grep usbcore" should tell you what modules/drivers are loaded and using the usb

---

### Post by d@ve on 2007-08-09
Can't thank you enough diepruis. I now have a fully functioning net adapter thanks to yourself and all the other contributors to this post.
Hopefully I'll be sticking with linux from now on

---

### Post by nandemonai on 2007-08-09
> **Austin_KW said:**
> The command "lsmod | grep usbcore" should tell you what modules/drivers are loaded and using the usb

Okies, output is:

usbcore 134280 3 rt73,ohci_hcd

I'm assuming that looks good then?

---

### Post by Austin_KW on 2007-08-09
> **nandemonai said:**
> Okies, output is:

usbcore 134280 3 rt73,ohci_hcd

I'm assuming that looks good then?

Yes, that looks OK.

Did you say you have only 64mB memory (not a lot for a modern OS), What size is your swap space and how much is free. What is the output of  "free -mt"

---

### Post by nandemonai on 2007-08-09
> **Austin_KW said:**
> Yes, that looks OK.

Did you say you have only 64mB memory (not a lot for a modern OS), What size is your swap space and how much is free. What is the output of  "free -mt"

At the moment it's CLI only.

With a few sessions and misc things going like top etc mem is as follows:

mem total 59 used 44 free 15
swap total 172 used 25 free 147
total 232 used 69 free 162

Pretty sure that's not the issue. I hope to get flux on it if I can get it online that is ;)

---

### Post by b.mann on 2007-08-09
> **diepruis said:**
> Try network manager first, unless you're sure it's an RT73 device. In that case we have to diagnose your problem, since the default rt73 modules will almost definitely not work.


Ok, will do. Its a Belkin f5d7050 (v3 i think)

EDIT: I tried that, and I still do not have the option to choose a wireless connection in the Networks menu. This only happened after I began with this tutorial, and a reinstall did not bring the wireless settings/options. Any idea on what I messed up?

---

### Post by diepruis on 2007-08-10
> **nandemonai said:**
> $ sudo dmesg | grep rt73
usbcore: registered new interface driver rt73
$

$ sudo dmesg | grep RT73
$

So, what did I miss? ;)

Sorry, I was making inferences from the rt61 driver. My bad.

It looks like you've done everything right. You only need to do some configuration now. Since you're using a CLI, you'll need to use "sudo vim" instead of "gksu gedit" to edit the needed files, of course.

---

### Post by diepruis on 2007-08-10
> **b.mann said:**
> Ok, will do. Its a Belkin f5d7050 (v3 i think)

EDIT: I tried that, and I still do not have the option to choose a wireless connection in the Networks menu. This only happened after I began with this tutorial, and a reinstall did not bring the wireless settings/options. Any idea on what I messed up?

I think you should create a new thread and PM me a link to it, then I can help you go through the howto again.

---

### Post by dannyboy79 on 2007-08-10
> **b.mann said:**
> Ok, will do. Its a Belkin f5d7050 (v3 i think)

EDIT: I tried that, and I still do not have the option to choose a wireless connection in the Networks menu. This only happened after I began with this tutorial, and a reinstall did not bring the wireless settings/options. Any idea on what I messed up?
open it by sticking your finger nail in the crack and spreading it apart very gently, if it says 2571wf, than you have the exact same one as me. I downloaded the latest rt73 cvs daily from the serialmonkey website, followed the guide exactly and it worked. I suppose it's possible that they uploaded a newer cvs daily and maybe it doesn't work anymore but i doubt it. I did uninstall network-manager, i forget if that's in the guide.

---

### Post by nandemonai on 2007-08-10
> **diepruis said:**
> Sorry, I was making inferences from the rt61 driver. My bad.

It looks like you've done everything right. You only need to do some configuration now. Since you're using a CLI, you'll need to use "sudo vim" instead of "gksu gedit" to edit the needed files, of course.

Seeing as I borked the install messing around (I like messing with things ;) ), I started fresh with a cli install of the latest xubuntu.

Went through the guide again, everything seemingly worked, compiled fine etc.

Again though when trying to bring up wlan0 the system starts throwing me BUG: scheduling while atomic: swapper/0x100000100/0.

I went ahead and did my /etc/network/interfaces thinking maybe it was working just being really noisy about it but even with a valid conf the interface does  not aquire an ip. Just sits there spewing BUG: scheduling while atomic: swapper/0x100000100/0 indeffinately.

Sad panda :(

As a side note I have it working on another partition running win2k so I know it's not a hardware problem.

---

### Post by dannyboy79 on 2007-08-10
it may not be your wireless hardware, have you thought about trying a different usb port? I also notice that you're using xubuntu BUT that of course shouldn't matter. 

IMPORTANT NOTES, I tried repeatedly over and over to get it to work in Xubuntu using the rt73 file that's linked in the beginning but I always had DHCPDISCOVER repeating itself over and over and it would never get an IP. 

The 2 difference's between then and now is the fact that I downloaded the source by actually going to serialmonkey and chosing the latest cvs daily rt73 and the fact that I am using Ubuntu Gutsy Tribe 3 NOT Xubuntu Gutsy Tribe 1. 

I installed Ubuntu (versus xubuntu) because I am a Technical Reviewer for a new book coming out covering Gutsy. The book is really good, it should be available for sale around December.

NOw I know that using Ubuntu versus Xubuntu shouldn't make the rt73 driver not work but maybe there's something else in the background not allowing it to work. Also the fact that I am using Gutsy tribe 3 versus Tribe 1 is another fact.

I have been told that Gutsy Tribe 4 DOES support my Belkin F5D7050 out of the box so I am going to be downloading it and giving it a go. I'll provide feedback when I can.

---

### Post by diepruis on 2007-08-10
> **nandemonai said:**
> Seeing as I borked the install messing around (I like messing with things ;) ),

Don't we all...

> **nandemonai said:**
>  started fresh with a cli install of the latest xubuntu.

Went through the guide again, everything seemingly worked, compiled fine etc.

Again though when trying to bring up wlan0 the system starts throwing me BUG: scheduling while atomic: swapper/0x100000100/0.

I went ahead and did my /etc/network/interfaces thinking maybe it was working just being really noisy about it but even with a valid conf the interface does  not aquire an ip. Just sits there spewing BUG: scheduling while atomic: swapper/0x100000100/0 indeffinately.

Sad panda :(

As a side note I have it working on another partition running win2k so I know it's not a hardware problem.

I have NO idea what could be causing this. You're better off posting this as a bug report on the serialmonkey site.

---

### Post by nandemonai on 2007-08-10
> **diepruis said:**
> Don't we all...



I have NO idea what could be causing this. You're better off posting this as a bug report on the serialmonkey site.

Appreciate your efforts regardless. I'll hit the serialmonkey forums and see if we cant get this nutted out.

---

### Post by b.mann on 2007-08-10
> **diepruis said:**
> I think you should create a new thread and PM me a link to it, then I can help you go through the howto again.

Ok, ill do that now

> **dannyboy79 said:**
> open it by sticking your finger nail in the crack and spreading it apart very gently, if it says 2571wf, than you have the exact same one as me. I downloaded the latest rt73 cvs daily from the serialmonkey website, followed the guide exactly and it worked. I suppose it's possible that they uploaded a newer cvs daily and maybe it doesn't work anymore but i doubt it. I did uninstall network-manager, i forget if that's in the guide.

Mine is a 2571F, so I have no idea why I am having so many issues.

---

### Post by dannyboy79 on 2007-08-10
well it's possible that the 2571w takes a different driver than the 2571wf?

---

### Post by Jhet on 2007-08-11
I have a RT2571F,  which as far as I know is a F5D7050 V1 and requires different drivers to the RT2571WF.  I used the rt2570 drivers from serialmonkey (because I couldn't get the rt73 ones to work, my original post is back on page 49), built exactly the same way as this guide says just using rt2570 instead of rt73.  Works fine for me.  It is possible that you will need to blacklist more drivers, since I found that the kernel was loading other drivers for the wireless adapter.  Just pay attention to dmesg when plugging the device in, that's what I did.

Hope it helps.

---

### Post by edward98 on 2007-08-11
hi,

My name is Edward and i have just recently installed ubuntu as a dual booting system along with ms media center. my network card is a ralink rt2500 and i followed all the instructions(changing rt73 with rt2500). Everything went well up until 12.module install. i type sudo modprobe -v rt2500. It then asks for my password. Then nothing happens. I then try to go onto instruction 13 but it just comes out with an error - wlan0: **_ERROR while getting interface flags: No such device._**
I have tried a million things but cant get it done . Gladly appriciate if anyone could give me some help.:(
thnks

---

### Post by dannyboy79 on 2007-08-11
> **edward98 said:**
> hi,

My name is Edward and i have just recently installed ubuntu as a dual booting system along with ms media center. my network card is a ralink rt2500 and i followed all the instructions(changing rt73 with rt2500). Everything went well up until 12.module install. i type sudo modprobe -v rt2500. It then asks for my password. Then nothing happens. I then try to go onto instruction 13 but it just comes out with an error - wlan0: **_ERROR while getting interface flags: No such device._**
I have tried a million things but cant get it done . Gladly appriciate if anyone could give me some help.:(
thnks

you're saying that you did the iwconfig things? if so, that should have setup the interface. it may be easier to turn off security just to make it less steps to see if it works. ALso, what does your interfaces file look like? One other thing would be to see if the module is even being loaded properly and making your device be seen by the kernel. what does dmesg show after entering the iwconfig settings?

---

### Post by dannyboy79 on 2007-08-11
I have BAD NEWS!!! 

Gutsy Tribe 4 Xubuntu still does NOT WORK out of the box with the provided rt2x00usb and rt73usb drivers. MAN!!! What's up. I was told that the new kernel worked with this device???? I'll have to go post where they told me that the Belkin F5D7050 worked with the latest kernel and tell them it doesn;t

---

### Post by Austin_KW on 2007-08-11
> **edward98 said:**
> hi,

My name is Edward and i have just recently installed ubuntu as a dual booting system along with ms media center. my network card is a ralink rt2500 and i followed all the instructions(changing rt73 with rt2500). Everything went well up until 12.module install. i type sudo modprobe -v rt2500. It then asks for my password. Then nothing happens. I then try to go onto instruction 13 but it just comes out with an error - wlan0: **_ERROR while getting interface flags: No such device._**
I have tried a million things but cant get it done . Gladly appriciate if anyone could give me some help.:(
thnks

The rt2500 device creates a ra0 device not wlan0. Should work with the default driver or you can build the latest serialmonkey driver, Just substitute ra0 for wan0

---

### Post by nandemonai on 2007-08-12
> **nandemonai said:**
> Seeing as I borked the install messing around (I like messing with things ;) ), I started fresh with a cli install of the latest xubuntu.

Went through the guide again, everything seemingly worked, compiled fine etc.

Again though when trying to bring up wlan0 the system starts throwing me BUG: scheduling while atomic: swapper/0x100000100/0.

I went ahead and did my /etc/network/interfaces thinking maybe it was working just being really noisy about it but even with a valid conf the interface does  not aquire an ip. Just sits there spewing BUG: scheduling while atomic: swapper/0x100000100/0 indeffinately.

Sad panda :(

As a side note I have it working on another partition running win2k so I know it's not a hardware problem.

'ello again

I've requested some help from the serialmonkeys forums but while I'm waiting on a reply I thought I'd add this info I found in /var/log/messages in case it may be helpful or rings any bells with someone as to what may be wrong.

```
Aug 12 15:43:15 slater kernel: [14002.970976] rt73 driver version - 1.0.3.6 CVS 
Aug 12 15:43:15 slater kernel: [14003.407891] ***rt73***: Interface goes up for the first time, activating permanent MAC 
Aug 12 15:43:15 slater kernel: [14003.407937] ***rt73***: Active MAC is: xx:xx:xx:xx:xx:xx. (Edited out) 
Aug 12 15:43:19 slater kernel: [14007.066819] [schedule+1528/2704] __sched_text_start+0x5f8/0xa90 
Aug 12 15:43:19 slater kernel: [14007.066925] [autoremove_wake_function+27/80] autoremove_wake_function+0x1b/0x50 
Aug 12 15:43:19 slater kernel: [14007.066994] [__activate_task+33/64] __activate_task+0x21/0x40 
Aug 12 15:43:19 slater kernel: [14007.067066] [try_to_wake_up+70/1152] try_to_wake_up+0x46/0x480 
Aug 12 15:43:19 slater kernel: [14007.067115] [__wake_up+56/80] __wake_up+0x38/0x50 
Aug 12 15:43:19 slater kernel: [14007.067198] [__cond_resched+22/64] __cond_resched+0x16/0x40 
Aug 12 15:43:19 slater kernel: [14007.067232] [cond_resched+42/64] cond_resched+0x2a/0x40 
Aug 12 15:43:19 slater kernel: [14007.067266] [__kmalloc+132/160] __kmalloc+0x84/0xa0 
Aug 12 15:43:19 slater kernel: [14007.067338] [<c503f582>] ohci_urb_enqueue+0xb2/0x7e0 [ohci_hcd] 
Aug 12 15:43:19 slater kernel: [14007.067447] [try_to_wake_up+70/1152] try_to_wake_up+0x46/0x480 
Aug 12 15:43:19 slater kernel: [14007.067562] [__next_cpu+18/32] __next_cpu+0x12/0x20 
Aug 12 15:43:19 slater kernel: [14007.067652] [<c506b48a>] usb_hcd_submit_urb+0x1da/0x930 [usbcore] 
Aug 12 15:43:19 slater kernel: [14007.067880] [<c522da27>] RTUSBRxPacket+0x117/0x1090 [rt73] 
Aug 12 15:43:19 slater kernel: [14007.068114] [<c503d179>] start_ed_unlink+0x19/0x60 [ohci_hcd] 
Aug 12 15:43:19 slater kernel: [14007.068172] [<c503d7ce>] dl_done_list+0x19e/0x1f0 [ohci_hcd] 
Aug 12 15:43:19 slater kernel: [14007.068248] [<c5224418>] RTUSBInitRxDesc+0x48/0x70 [rt73] 
Aug 12 15:43:19 slater kernel: [14007.068333] [<c5224c70>] RTUSBBulkRxComplete+0x0/0x40 [rt73] 
Aug 12 15:43:19 slater kernel: [14007.068453] [tasklet_action+99/224] tasklet_action+0x63/0xe0 
Aug 12 15:43:19 slater kernel: [14007.068555] [__do_softirq+130/256] __do_softirq+0x82/0x100 
Aug 12 15:43:19 slater kernel: [14007.068620] [do_softirq+85/96] do_softirq+0x55/0x60 
Aug 12 15:43:19 slater kernel: [14007.068655] [do_IRQ+69/128] do_IRQ+0x45/0x80 
Aug 12 15:43:19 slater kernel: [14007.068726] [common_interrupt+35/48] common_interrupt+0x23/0x30 
Aug 12 15:43:19 slater kernel: [14007.068761] [default_idle+0/96] default_idle+0x0/0x60 
Aug 12 15:43:19 slater kernel: [14007.068838] [native_safe_halt+2/16] native_safe_halt+0x2/0x10 
Aug 12 15:43:19 slater kernel: [14007.068885] [default_idle+61/96] default_idle+0x3d/0x60 
Aug 12 15:43:19 slater kernel: [14007.068907] [cpu_idle+73/208] cpu_idle+0x49/0xd0 
Aug 12 15:43:19 slater kernel: [14007.068948] [start_kernel+869/1056] start_kernel+0x365/0x420 
Aug 12 15:43:19 slater kernel: [14007.068999] [unknown_bootoption+0/608] unknown_bootoption+0x0/0x260
```

It repeats itself just like the 'BUG' message does for as long as I leave the interface up.

---

### Post by edward98 on 2007-08-12
Thanks Austin_KW

After a bt of tweking with the network I got it to work. Thanks so much for your help

Edward

---

### Post by dannyboy79 on 2007-08-13
> **nandemonai said:**
> 'ello again

I've requested some help from the serialmonkeys forums but while I'm waiting on a reply I thought I'd add this info I found in /var/log/messages in case it may be helpful or rings any bells with someone as to what may be wrong.

```
Aug 12 15:43:15 slater kernel: [14002.970976] rt73 driver version - 1.0.3.6 CVS 
Aug 12 15:43:15 slater kernel: [14003.407891] ***rt73***: Interface goes up for the first time, activating permanent MAC 
Aug 12 15:43:15 slater kernel: [14003.407937] ***rt73***: Active MAC is: xx:xx:xx:xx:xx:xx. (Edited out) 
Aug 12 15:43:19 slater kernel: [14007.066819] [schedule+1528/2704] __sched_text_start+0x5f8/0xa90 
Aug 12 15:43:19 slater kernel: [14007.066925] [autoremove_wake_function+27/80] autoremove_wake_function+0x1b/0x50 
Aug 12 15:43:19 slater kernel: [14007.066994] [__activate_task+33/64] __activate_task+0x21/0x40 
Aug 12 15:43:19 slater kernel: [14007.067066] [try_to_wake_up+70/1152] try_to_wake_up+0x46/0x480 
Aug 12 15:43:19 slater kernel: [14007.067115] [__wake_up+56/80] __wake_up+0x38/0x50 
Aug 12 15:43:19 slater kernel: [14007.067198] [__cond_resched+22/64] __cond_resched+0x16/0x40 
Aug 12 15:43:19 slater kernel: [14007.067232] [cond_resched+42/64] cond_resched+0x2a/0x40 
Aug 12 15:43:19 slater kernel: [14007.067266] [__kmalloc+132/160] __kmalloc+0x84/0xa0 
Aug 12 15:43:19 slater kernel: [14007.067338] [<c503f582>] ohci_urb_enqueue+0xb2/0x7e0 [ohci_hcd] 
Aug 12 15:43:19 slater kernel: [14007.067447] [try_to_wake_up+70/1152] try_to_wake_up+0x46/0x480 
Aug 12 15:43:19 slater kernel: [14007.067562] [__next_cpu+18/32] __next_cpu+0x12/0x20 
Aug 12 15:43:19 slater kernel: [14007.067652] [<c506b48a>] usb_hcd_submit_urb+0x1da/0x930 [usbcore] 
Aug 12 15:43:19 slater kernel: [14007.067880] [<c522da27>] RTUSBRxPacket+0x117/0x1090 [rt73] 
Aug 12 15:43:19 slater kernel: [14007.068114] [<c503d179>] start_ed_unlink+0x19/0x60 [ohci_hcd] 
Aug 12 15:43:19 slater kernel: [14007.068172] [<c503d7ce>] dl_done_list+0x19e/0x1f0 [ohci_hcd] 
Aug 12 15:43:19 slater kernel: [14007.068248] [<c5224418>] RTUSBInitRxDesc+0x48/0x70 [rt73] 
Aug 12 15:43:19 slater kernel: [14007.068333] [<c5224c70>] RTUSBBulkRxComplete+0x0/0x40 [rt73] 
Aug 12 15:43:19 slater kernel: [14007.068453] [tasklet_action+99/224] tasklet_action+0x63/0xe0 
Aug 12 15:43:19 slater kernel: [14007.068555] [__do_softirq+130/256] __do_softirq+0x82/0x100 
Aug 12 15:43:19 slater kernel: [14007.068620] [do_softirq+85/96] do_softirq+0x55/0x60 
Aug 12 15:43:19 slater kernel: [14007.068655] [do_IRQ+69/128] do_IRQ+0x45/0x80 
Aug 12 15:43:19 slater kernel: [14007.068726] [common_interrupt+35/48] common_interrupt+0x23/0x30 
Aug 12 15:43:19 slater kernel: [14007.068761] [default_idle+0/96] default_idle+0x0/0x60 
Aug 12 15:43:19 slater kernel: [14007.068838] [native_safe_halt+2/16] native_safe_halt+0x2/0x10 
Aug 12 15:43:19 slater kernel: [14007.068885] [default_idle+61/96] default_idle+0x3d/0x60 
Aug 12 15:43:19 slater kernel: [14007.068907] [cpu_idle+73/208] cpu_idle+0x49/0xd0 
Aug 12 15:43:19 slater kernel: [14007.068948] [start_kernel+869/1056] start_kernel+0x365/0x420 
Aug 12 15:43:19 slater kernel: [14007.068999] [unknown_bootoption+0/608] unknown_bootoption+0x0/0x260
```

It repeats itself just like the 'BUG' message does for as long as I leave the interface up.

are you using any boot options when you boot the kernel from grub? like for example noacpi or anything regarding irq? I also notice that you have a custom kernel! DId you see the note at the begining about having to use the i386 kernel instead of the i686? Is it possible that you enabled something in your kernel that none of the rest of us have?

---

### Post by nandemonai on 2007-08-14
> **dannyboy79 said:**
> are you using any boot options when you boot the kernel from grub? like for example noacpi or anything regarding irq? I also notice that you have a custom kernel! DId you see the note at the begining about having to use the i386 kernel instead of the i686? Is it possible that you enabled something in your kernel that none of the rest of us have?

It's the default Xubuntu Feisty kernel with no special boot options. Alternate disc, server install.

How would I got about getting an i386 kern installed? All that's on the CD in linux-generic.

---

### Post by diepruis on 2007-08-15
> **nandemonai said:**
> It's the default Xubuntu Feisty kernel with no special boot options. Alternate disc, server install.

How would I got about getting an i386 kern installed? All that's on the CD in linux-generic.

If you have one, an alternate connection will be very handy at this point. Carrying your PC to the router and connecting through an ethernet cable is probably the best option at this moment. You can also manually download the .debs and install them using dpkg.

However, I'm not sure this is really the problem. According to several reports the module is working with SMP and PREEMPT kernels (as opposed to previous versions that required the kernel downgrade). Your PC may be a special case, on the other hand.

---

### Post by fyz on 2007-08-15
After another few days trying, my wireless network still not working perfectly. :(

I have read the first post and followed the HOWTO instructions. With all your helps, I can at least  get the wireless connection. The driver was installed flawlessly (I think). But now I got three problems:
First, I still can not manage  to make the interface be brought up automatically across reboots; every time I have to manually type a few lines after reboot.  This is my interfaces files:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan1
iface wlan1 inet dhcp
   pre-up ifconfig wlan1 up
   pre-up iwconfig wlan1 essid belkin54g
   pre-up iwconfig wlan1 key "off"

```

Secondly, even when I try to configure the interface manually, it does not always work. Normally, after typing following code in terminal (after every  reboot ):
```

  sudo ifconfig wlan1 up
  sudo iwconfig wlan1 essid belkin54g
  sudo iwconfig wlan1 key "off"

```

I HAVE TO unplug the adapter and plug it in again, then WAIT FOR A WHILE (otherwise it won't work),  then I can type:
```

sudo dhclient wlan1

```

After all these, I can then  get connection! 

The third problem is I have to set the WEP security off in my router, other wise it won't work. Maybe I didn't set the key correctly in the configuration of interface. But this is ok for time being. The first two problems are more annoying. 

This is message when it failed to connect
```

Listening on LPF/wlan1/00:11:50:bc:ec:dd
Sending on   LPF/wlan1/00:11:50:bc:ec:dd
Sending on   Socket/fallback
DHCPREQUEST on wlan1 to 255.255.255.255 port 67
DHCPREQUEST on wlan1 to 255.255.255.255 port 67
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
Trying recorded lease 192.168.2.2
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```

This is the message when it does get connection after the **unplug/plug trick:**
```

Listening on LPF/wlan1/00:11:50:bc:ec:dd
Sending on   LPF/wlan1/00:11:50:bc:ec:dd
Sending on   Socket/fallback
DHCPREQUEST on wlan1 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.2 -- renewal in 960272812 seconds.

```

Do you have any ideas what is going on? Thanks a millions!

---

### Post by nandemonai on 2007-08-15
> **diepruis said:**
> If you have one, an alternate connection will be very handy at this point. Carrying your PC to the router and connecting through an ethernet cable is probably the best option at this moment. You can also manually download the .debs and install them using dpkg.

However, I'm not sure this is really the problem. According to several reports the module is working with SMP and PREEMPT kernels (as opposed to previous versions that required the kernel downgrade). Your PC may be a special case, on the other hand.

That's the problem. This machine is so old it doesn't even have a ethernet jack ;) I do however have a 56k card modem that seems to work fine. I'll *cough* dialup and see if a i386 kernel helps.

Will keep you posted.

---

### Post by diepruis on 2007-08-16
> **fyz said:**
> First, I still can not manage  to make the interface be brought up automatically across reboots; every time I have to manually type a few lines after reboot.

Mmm... what does "iwconfig" report directly after a reboot?

Did you perhaps receive a warning about an existing config file during the installation process? Recently rt73 switched from a .dat file based configuration to iwconfig support. If you still have that rt73sta.dat file somewhere on your PC it can interfere with the configuration process. A give-away sign would be the existence of /etc/Wireless

That aside, the problem could lie with the USB device, or perhaps a kernel bug that won't allow it to be recognised properly from a cold boot. I remember there being a previous device in this discussion that had similiar problems which we finally attributed to the card itself, instead of the software configuration. If you have another wireless adapter lying around, I would recommend testing that.

---

### Post by edward98 on 2007-08-16
Help pls!

I recently had to reinstall my ubuntu operating system as some of my tinkering mest up my 3d graphics. Last time this solved my problem however now when I type sudo dhclient ra0 if comes up with 3 lines of some ip adress codes and then comes with the error
No DHCPOFFERS recieved.
No working leases in persistent database - sleeping.
My other computers have all got the network working so my router is not off. Any help.
Thanks 
Edward

---

### Post by diepruis on 2007-08-16
> **edward98 said:**
> Help pls!

I recently had to reinstall my ubuntu operating system as some of my tinkering mest up my 3d graphics. Last time this solved my problem however now when I type sudo dhclient ra0 if comes up with 3 lines of some ip adress codes and then comes with the error
No DHCPOFFERS recieved.
No working leases in persistent database - sleeping.
My other computers have all got the network working so my router is not off. Any help.
Thanks 
Edward

What does "sudo iwconfig" report?

---

### Post by edward98 on 2007-08-16
lo     no wireless extension

eth0 no wireless extension

ra0    rt2500 Wireless ESSID:""
        Mode:Manager Frequency=2.412 ghz bit rate:11 mb/s tx-power:0 dBm

Rts thr: off      Fragement thr: off
Encryption key: off
link quality=0/100   singal level= 120 dBm   Noise Level:-204 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
tx excessive retries:0 invalid misc:0 missed beacon:0

thats it. Sorry but its not very acurate with spacing and capitals

---

### Post by edward98 on 2007-08-16
Can anyone bring any light on this situatuion. im really getting a headache with ubuntu.

---

### Post by dannyboy79 on 2007-08-16
well it appears as though you have gotten the attention of the thread author and is more than capable of helping you. Are you aware of exactly what chip you have? For instance, I have the belkin F5D7050 (when I split apart the adapter with a fingernail, it has rt2571wf on the chip inside) now I thought I would have to use the rt2x00 driver but it turned out that the rt73 cvs daily works with it. I followed the guide to the letter and wahla.

---

### Post by Austin_KW on 2007-08-16
> **edward98 said:**
> Can anyone bring any light on this situatuion. im really getting a headache with ubuntu.

Did you not have a rt2500. Should work without needing to rebuild the serialmonkey drivers. Or you can follow similar steps to the OP in this thread to build the latest driver. The rt2500 drivers are much more stable than the usb rt73/rt2570 sibling drivers.
It is probably just your configuration in /etc/network/interfaces. If you post your file we can take a look at it.

Also in  general when you have wireless problems you can try temporarily turning off all security to see if you can get a connection. But post you config file.

---

### Post by edward98 on 2007-08-16
Sorry Guys but I need to know exactly what stuff to post. I'm a complete newbie at linux. The wierd thing is it was working with that exact same method before. I have done everthing exactly the same but now it doesn't seem to work. All I did was instal ubuntu fiesty again then go on my laptop to get the instructions. What did I do wrong.

auto lo 
iface lo inet loopback

auto eth0 
iface eth0 inet dhcp

auto eth0 
iface eth0 inet

auto eth1 
iface eth1 inet dhcp

auto eth2 
iface eth2 inet dhcp

auto ath0 
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto ra0 
iface ra0 inet dhcp

---

### Post by Austin_KW on 2007-08-16
> **edward98 said:**
> Sorry Guys but I need to know exactly what stuff to post. I'm a complete newbie at linux. The wierd thing is it was working with that exact same method before. I have done everthing exactly the same but now it doesn't seem to work. All I did was instal ubuntu fiesty again then go on my laptop to get the instructions. What did I do wrong.

Post everything in /etc/network/interfaces which references ra0

---

### Post by diepruis on 2007-08-16
> **edward98 said:**
> 
auto ra0 
iface ra0 inet dhcp

You need some configuration information in here. It's detailed in the HOWTO under the section which explains /etc/network/interfaces

From your iwconfig output it also seems that you're using an old version of the driver. The newer versions use wlan0 as the interface name. It's not a big deal, but I thought I should mention it in case you want to stay current.

---

### Post by Austin_KW on 2007-08-16
> **diepruis said:**
> You need some configuration information in here. It's detailed in the HOWTO under the section which explains /etc/network/interfaces

From your iwconfig output it also seems that you're using an old version of the driver. The newer versions use wlan0 as the interface name. It's not a big deal, but I thought I should mention it in case you want to stay current.

It is still ra0 for the rt2500, but you will want to setup your configuration for your network (ssid, authentication & encryption). Just use ra0 for wlan0.

---

### Post by edward98 on 2007-08-16
Thanks ill first try and upgrade to the beta version. I'll post back any problems or success here. thanks

---

### Post by Austin_KW on 2007-08-16
> **edward98 said:**
> Thanks ill first try and upgrade to the beta version. I'll post back any problems or success here. thanks

By beta I hope you mean the rt2500-cvs and not the rt2x00 beta drivers as the latter does not work.

---

### Post by edward98 on 2007-08-16
Ahh! I tried to install the beta rt2500-1.1.0-b4.tar.gz but it doenst work either. Why does linux make it so hard to setup the system. Simple tasks like installing usually alwas involve the terminal.:(. 

Anyways i got an error on the sudo make. I have no idea wot to do. Linux is giving me a headache.

---

### Post by Austin_KW on 2007-08-16
> **edward98 said:**
> Ahh! I tried to install the beta rt2500-1.1.0-b4.tar.gz but it doenst work either. Why does linux make it so hard to setup the system. Simple tasks like installing usually alwas involve the terminal.:(. 

Anyways i got an error on the sudo make. I have no idea wot to do. Linux is giving me a headache.

The installed rt2500 driver should work. Just configure ra0 using the command line or /etc/network/interfaces. If you use /etc/network/interfaces then run the command "sudo ifup --f ra0" after making any changes

---

### Post by edward98 on 2007-08-16
How do I configure? im a complete newbie a linux.

---

### Post by dannyboy79 on 2007-08-16
WOW, I would either comment out or remove all those other interfaces that you don't use. plus , make it look like what's within the guide. have you tried unplugging the adapter and then replugging it in and then enter this command to see what it returns.
dmesg
what does
lsmod
show when entered into a terminal.

---

### Post by dannyboy79 on 2007-08-16
> **edward98 said:**
> How do I configure? im a complete newbie a linux.

you configure it using the guide  on page 1 and or page 2. Except if what the other guy says is true, you only need to follow the steps regarding iwconfig and whatnot. This means that you don't need to download, compile anything, or run modprobe. This is only true if the default rt2500 that comes with Feisty works as the previous poster says. BUT if you already downloaded and compiled and tried modprobing -r and modprobing other modules, now chances are you have multiple modules possibly loaded and this will create problems. You'll want to restart your machine. then do iwconfig, if it shows an interface but it's just not associated with an AP, then you merely have to configure it. meaning using 
iwconfig to set the ESSID and security if needed, then do the ifup etc etc. Just follow the guide for only configuring the interface. then if that works using iwconfig and what not. you'll want to ensure that your /etc/network/interfaces file gets updated so it works everytime you boot up. Here's the example from the beginning of the guide:
NOTE TO YOU: you would change the wlan0 to ra0 if that's what iwconfig shows.
auto wlan0
iface wlan0 inet static
address STATIC_IP_ADDRESS
netmask 255.255.255.0
network ROUTER_IP
gateway ROUTER_IP
        pre-up ifconfig wlan0 up
        pre-up iwconfig wlan0 essid YOUR_ESSID
        pre-up iwconfig wlan0 mode Managed


NOT to mention have you verified which wireless chip you have yet???? These rt*** drivers work for all sorts of different chips and not using the correct one with never make it work.

---

### Post by Austin_KW on 2007-08-16
> **edward98 said:**
> How do I configure? im a complete newbie a linux.

If you are having problems following the instructions then tell us, 
What is you network name 
What type of security do you use (wpa,wep[with hex/ascii key], none)

---

### Post by edward98 on 2007-08-16
My chips a ralink rt2500 i checked it with windows xp which is now seeming 1000 times better than linux

---

### Post by edward98 on 2007-08-16
Im having huge trouble with the instructions.
Network name MSHOME
Security none

---

### Post by Austin_KW on 2007-08-16
For those of you curious to use the new rt2x00 beta driver. I am now typing this on feisty with the new driver and networkmanager
```

austin@austin-laptop:~$ lsmod | grep usbcore
usbcore               137864  6 rt73usb,rt2x00usb,usbhid,ehci_hcd,ohci_hcd

```

Scanning is not finding all networks but it seems to work if you manually tell it the network name.

I had to install the gusty kernel and update the wireless tools. I have my rt73usb working but not my rt2500pci.

I attach my script to update to the Gutsy kernel and wireless tools (based on kernel.sh found in these forums). I will try updating the rt2x00 later and hopefully have futher success but it is looking good for gusty

You will have to make the script executable and change the blacklist, I am not giving instructions as if you dont know how you should not experiment with this. You will also need network manager if you removed it.

---

### Post by dannyboy79 on 2007-08-16
> **edward98 said:**
> Im having huge trouble with the instructions.
Network name MSHOME
Security none
network name should eb the ESSID which will be defined in your access point or wireless router. I hope you're not using the Workgroup name from your windows machine. Just making sure as MSHOME is the default Workgroup for sharing files in the windows environment. Also, you're sure that you don't have WEP or WPA security? That's very scary as anyone can sniff you're packets right out of the air and see any password you enter for banking or whatever. If you iwconfig shows ra0, please show me the output of
first to see what events your wireless adapter supports enter this
sudo iwlist ra0 event
hopefully it supports scanning for Access Points and what not. then do
sudo iwlist ra0 scan
NOTE, use whatever interface iwconfig showed. example: wlan0 or rausb0 or ra0 or whatever it showed.

---

### Post by Austin_KW on 2007-08-16
> **edward98 said:**
> Im having huge trouble with the instructions.
Network name MSHOME
Security none

your network name is not likely to be MSHOME. That is the default workgroup for microsoft home networking.

what is the output of the command "iwlist ra0 scan"

EDIT; Overlap posting with dannyboy ;)

---

### Post by diepruis on 2007-08-16
> **edward98 said:**
> Why does linux make it so hard to setup the system. Simple tasks like installing usually alwas involve the terminal.:(.

I know how you feel. This driver really should be the standard module included with Ubuntu, instead of the rt2x00 module it ships with now. The fact that there's been a bug report filed about this for the last release or so only makes it worse.

---

### Post by pfwd.tech on 2007-08-16
I too feel your pain.  I have resorted into setting up a wired network just because i still can't get the dam drivers to work. If only they were supplied with the releases things would be plain sailing.

---

### Post by corbinator9000 on 2007-08-16
This works exellently for Dapper, but nosomuch for feisty, in feisty i couldnt get the device recognised in feisty. any suggestions?

---

### Post by diepruis on 2007-08-16
> **corbinator9000 said:**
> This works exellently for Dapper, but nosomuch for feisty, in feisty i couldnt get the device recognised in feisty. any suggestions?

I wrote this guide after setting up the device under Feisty, so I doubt that's the problem. What specifically was your problem?

---

### Post by corbinator9000 on 2007-08-16
well i actually had previously had a dual-partition with dapper and feisty and this guide works exellently fr dapper (thanks) but it never seemed to work for feisty, so i ended up reformatting and only using dapper.. but if this should work for feisty i suppose ill try again and post the error message... thanks!

---

### Post by corbinator9000 on 2007-08-16
quick question though does this also work for 64bit ubuntu?

---

### Post by Austin_KW on 2007-08-16
For anyone trying this I had to make my interface wlan1. I now have my rt2500pci working on the beta driver. I don't know yet if the problem was that I had a previous wlan0 config but neither rt73 or my rt2500 would work as wlan0. So if you try this then you may need to edit your iftab and select wlan1 as your interface.

I am curious if others can successfully use the new drivers?

I could not get a later rt2x00 driver to build, interdependencies on a later mac802.11 module.

> **Austin_KW said:**
> For those of you curious to use the new rt2x00 beta driver. I am now typing this on feisty with the new driver and networkmanager
```

austin@austin-laptop:~$ lsmod | grep usbcore
usbcore               137864  6 rt73usb,rt2x00usb,usbhid,ehci_hcd,ohci_hcd

```

Scanning is not finding all networks but it seems to work if you manually tell it the network name.

I had to install the gusty kernel and update the wireless tools. I have my rt73usb working but not my rt2500pci.

I attach my script to update to the Gutsy kernel and wireless tools (based on kernel.sh found in these forums). I will try updating the rt2x00 later and hopefully have futher success but it is looking good for gusty

You will have to make the script executable and change the blacklist, I am not giving instructions as if you dont know how you should not experiment with this. You will also need network manager if you removed it.

---

### Post by diepruis on 2007-08-16
> **corbinator9000 said:**
> quick question though does this also work for 64bit ubuntu?

I see no reason why it shouldn't, but I'm not sure. Check the history of this (already pretty big) thread, I remember someone else asking about this.

---

### Post by diepruis on 2007-08-16
> **Austin_KW said:**
> I am curious if others can successfully use the new drivers?

I could not get a later rt2x00 driver to build, interdependencies on a later mac802.11 module.

The version I tried a few months ago still didn't have proper rt61 support, but I'll probably give it another shot once Gutsy comes out with its new kernel. Custom kernels and the like are way too much effort on Ubuntu IMHO.

---

### Post by Austin_KW on 2007-08-16
> **diepruis said:**
> The version I tried a few months ago still didn't have proper rt61 support, but I'll probably give it another shot once Gutsy comes out with its new kernel. Custom kernels and the like are way too much effort on Ubuntu IMHO.

No effort, just run the script, it downloads and installs the 2.6.22-9 kernel from the gusty repository. My rt2500 seems rock solid an my rt73 seems better than the legacy driver (at least on my laptop where it was failing on half my boots). I have also update to the gusty network manager and all seems to work but it is my first few hours of testing.

---

### Post by Austin_KW on 2007-08-16
> **corbinator9000 said:**
> quick question though does this also work for 64bit ubuntu?

It does work on 64bit, but it was less stable than the 32 bit version on my hardware. Unless you have more than 4GB of ram there is no reason to run the 64bit version, less supported packages and I think it boots and runs slower.

---

### Post by diepruis on 2007-08-17
> **Austin_KW said:**
> No effort, just run the script, it downloads and installs the 2.6.22-9 kernel from the gusty repository. My rt2500 seems rock solid an my rt73 seems better than the legacy driver (at least on my laptop where it was failing on half my boots). I have also update to the gusty network manager and all seems to work but it is my first few hours of testing.

Okay, I'll bite :)

Which version did you get to compile?

---

### Post by Austin_KW on 2007-08-17
> **diepruis said:**
> Okay, I'll bite :)

Which version did you get to compile?

No compile necessary, Just run the test.sh script I posted earlier which installs the gusty kernel and wireless tools (you may want to modify it to also update network-manager and network-manager-gnome). Then blacklist rt73 and unblacklist rt73usb (and any supporting modules). 
I also had to modify /etc/iftab s.t. the interface name is wlan1 not wlan0.

EDIT;
iwlist scan does not show networks you need "sudo iwlist scan"
If you use international channels (outside the usual ch1-11) you will need to add a parameter to mac80211 module. The easiest way is to first modify /etc/modprobe.d/options and add the following
```
# 802.11 to international mode; ieee80211_regdom:IEEE 802.11 regulatory domain; 64=MKK (int)
options mac80211 ieee80211_regdom=64

```
I think it then uses your regional settings to figure out what your available channels are.

---

### Post by NewWithoutClue on 2007-08-18
```
auto wlan0
iface wlan0 inet dhcp
	pre-up ifconfig wlan0 up
	pre-up iwconfig wlan0 essid SESSION_ID
	pre-up iwconfig wlan0 key s:sethb restricted # need to prefix ascii WEP keys with s:, and if it's a shared key, you also need to add "restricted"
```

Fully working.. thanks a lot man!

---

### Post by diepruis on 2007-08-18
> **NewWithoutClue said:**
> ```
auto wlan0
iface wlan0 inet dhcp
	pre-up ifconfig wlan0 up
	pre-up iwconfig wlan0 essid SESSION_ID
	pre-up iwconfig wlan0 key s:sethb restricted # need to prefix ascii WEP keys with s:, and if it's a shared key, you also need to add "restricted"
```

Fully working.. thanks a lot man!

Glad to hear it :)

I added the info on ASCII WEP keys to the HOWTO as I'd omitted it earlier, hope you don't mind.

---

### Post by diepruis on 2007-08-18
> **Austin_KW said:**
> I also had to modify /etc/iftab s.t. the interface name is wlan1 not wlan0.

Still giving problems on my machine... but then again, I've never installed rt73 on it before so it may be something unrelated. I was wondering why you set the interface name to wlan1... AFAIK that shouldn't make a difference, but if it worked for you...

---

### Post by sparkybean on 2007-08-18
First of all,  diepruis this is a great tutorial, really easy to follow.

I managed to follow it flawlessly until the end, at the last instruction where it says:

"wlan0: ERROR while getting interface flags: No such device"

I have an internal wireless device, but now where i could see my nework but not connect, i cant do either! please help, im sick of having to use a laptop with a fat wire plugged in the side...

---

### Post by Austin_KW on 2007-08-18
> **sparkybean said:**
> First of all,  diepruis this is a great tutorial, really easy to follow.

I managed to follow it flawlessly until the end, at the last instruction where it says:

"wlan0: ERROR while getting interface flags: No such device"

I have an internal wireless device, but now where i could see my nework but not connect, i cant do either! please help, im sick of having to use a laptop with a fat wire plugged in the side...

Check if your interface is wlan1("ifconfig -a" should list your intefaces), sometimes it creates wlan1 instead.

---

### Post by Austin_KW on 2007-08-18
> **diepruis said:**
> Still giving problems on my machine... but then again, I've never installed rt73 on it before so it may be something unrelated. I was wondering why you set the interface name to wlan1... AFAIK that shouldn't make a difference, but if it worked for you...

Should not have made a difference, I only noticed because I was testing with two ralink chipsets (an rt2500 and an rt73) and whichever was wlan0 would not work. It may be some old wlan0 config somewhere but I can not find it.

I have been testing today the beta driver with my rt2500, it is working but I am seeing speed problems. When I leave the connection idle the speed drops to 1 or 2Mbs and does not go back up until I force a reconnect.  

I am doing a system reinstall at present, I have so much crap installed that I dont know what is going on. I will try the beta rt73 again later and report back.

Hopefully the beta drivers will work with gutsy and we can stop doing all these work-arounds

---

### Post by Austin_KW on 2007-08-18
> **diepruis said:**
> Still giving problems on my machine... but then again, I've never installed rt73 on it before so it may be something unrelated. I was wondering why you set the interface name to wlan1... AFAIK that shouldn't make a difference, but if it worked for you...

You are correct, after I cleaned up my system I can now use wlan0. I presume it was the old wlan0 config in interfaces for the legacy driver that was causing the problems. 

I still have to use sudo to scan for networks, why the scan is a root command I don't know.
The speed on the rt73usb is solid at 54mbs, not bad for 2 rooms away on a different floor, much better that the beta rt2500pci sibling driver.

One thing that I have noticed is that when using the networkmanager if the connection does not establish then trying again seems to fix it.

---

### Post by diepruis on 2007-08-19
> **Austin_KW said:**
> I have been testing today the beta driver with my rt2500, it is working but I am seeing speed problems. When I leave the connection idle the speed drops to 1 or 2Mbs and does not go back up until I force a reconnect.  

Check out the mailing list (rt2400-devel). I believe they're looking to confirm that problem.

---

### Post by diepruis on 2007-08-19
> **Austin_KW said:**
> You are correct, after I cleaned up my system I can now use wlan0. I presume it was the old wlan0 config in interfaces for the legacy driver that was causing the problems. 

I still have to use sudo to scan for networks, why the scan is a root command I don't know.
The speed on the rt73usb is solid at 54mbs, not bad for 2 rooms away on a different floor, much better that the beta rt2500pci sibling driver.

One thing that I have noticed is that when using the networkmanager if the connection does not establish then trying again seems to fix it.

I have no idea why it's not working :/ I retried several times... and everything is set up correctly, but oddly I don't even get LEDs. It must be some oddity in my setup, I think I'll try again when I can get a clean install of Gutsy.

---

### Post by diepruis on 2007-08-19
> **sparkybean said:**
> I have an internal wireless device, but now where i could see my nework but not connect, i cant do either! please help, im sick of having to use a laptop with a fat wire plugged in the side...

Could you post the output of ```
lspci -n
```

The reason I'm asking for this is that I'm not sure they make *internal* RT73 devices. It's only used in USB devices AFAIK. Which means that you might be barking up the wrong drivers for the tree :)

That said, I may be completely inaccurate, so try Austin_KW's approach first ;)

---

### Post by PeteZA on 2007-08-19
Hi there,

I have read the bulk of this post, and tried everything as listed, and for the life of me i cant get my Dlink DWL-G122 usb device working, could somebody direct me to a post or something that may work

Tx

---

### Post by diepruis on 2007-08-19
> **PeteZA said:**
> Hi there,

I have read the bulk of this post, and tried everything as listed, and for the life of me i cant get my Dlink DWL-G122 usb device working, could somebody direct me to a post or something that may work

Tx

This is the most complete HOWTO that I have ever come across for this device. You could try some other Linux forums, but I doubt that it would you much. You're better off posting your specific problem so someone can help you individually.

---

### Post by Austin_KW on 2007-08-19
> **diepruis said:**
> Could you post the output of ```
lspci -n
```

The reason I'm asking for this is that I'm not sure they make *internal* RT73 devices. It's only used in USB devices AFAIK. Which means that you might be barking up the wrong drivers for the tree :)

That said, I may be completely inaccurate, so try Austin_KW's approach first ;)

I missed the "internal wireless" part of the post, it will not likely be a rt73. There are not many ralink chipsets used in internal cards but I suppose it could be a rt2500 or rt61. But post the output of lspci as suggested.

---

### Post by Austin_KW on 2007-08-19
> **PeteZA said:**
> Hi there,

I have read the bulk of this post, and tried everything as listed, and for the life of me i cant get my Dlink DWL-G122 usb device working, could somebody direct me to a post or something that may work

Tx

I think this is another one of those usb modules that has multiple chipsets depending on revision (prism, rt2570 and rt73). You will want to confirm your chipset or version. You may be able to open the module by prying apart with a fingernail or find the windows driver *.sys/*.inf that came with it.

Also check the output of "lsmod | grep usbcore" for conflicting drivers,

---

### Post by PeteZA on 2007-08-19
I tried the steps again, but it didnt work... again, and because i had to purge the network manager i cant get onto the net now. for starters, how do i now reconnect via my ethernet so i can post the errors?

---

### Post by Austin_KW on 2007-08-19
> **PeteZA said:**
> I tried the steps again, but it didnt work... again, and because i had to purge the network manager i cant get onto the net now. for starters, how do i now reconnect via my ethernet so i can post the errors?

Try "sudo dhclient eth0", should bring up the first ethernet  interface and try to get a dhcp address.

---

### Post by PeteZA on 2007-08-19
Thanks, I got the network is back up again, from step 12 of the guide onwards, this is the output:```
peter@peter-desktop:~$ sudo ifconfig wlan0 down
Password:
peter@peter-desktop:~$ sudo modprobe -r rt73usb
peter@peter-desktop:~$ sudo modprobe -r rt2570
peter@peter-desktop:~$ sudo modprobe -r rt2500usb
peter@peter-desktop:~$ sudo modprobe -r rt2x00lib
peter@peter-desktop:~$ sudo modprobe -v rt73
peter@peter-desktop:~$ sudo ifconfig wlan0 up
peter@peter-desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 5112
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:19:5b:2c:65:e6
Sending on   LPF/wlan0/00:19:5b:2c:65:e6
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Any ideas why it is not finding anything, to note tho, when the network manager was loaded, it did show my wireless network, but didnt give me an option for WPA

---

### Post by NewWithoutClue on 2007-08-19
> **PeteZA said:**
> Thanks, I got the network is back up again, from step 12 of the guide onwards, this is the output:```
peter@peter-desktop:~$ sudo ifconfig wlan0 down
Password:
peter@peter-desktop:~$ sudo modprobe -r rt73usb
peter@peter-desktop:~$ sudo modprobe -r rt2570
peter@peter-desktop:~$ sudo modprobe -r rt2500usb
peter@peter-desktop:~$ sudo modprobe -r rt2x00lib
peter@peter-desktop:~$ sudo modprobe -v rt73
peter@peter-desktop:~$ sudo ifconfig wlan0 up
peter@peter-desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 5112
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:19:5b:2c:65:e6
Sending on   LPF/wlan0/00:19:5b:2c:65:e6
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Any ideas why it is not finding anything, to note tho, when the network manager was loaded, it did show my wireless network, but didnt give me an option for WPA

is your network a secure one? :P

if you have wep encryption, you have to make sure you're authenticated before you request a DHCP lease.
Basically,
```
iwconfig wlan0 key YOUR_WEP_KEY
```
if it's an ascii (text) string, you need to prefix YOU_WEP_KEY with s: (s:YOUR_WEP_KEY) 

```
 man iwconfig 
```

---

### Post by PeteZA on 2007-08-19
No,as far as i am aware, I am using WPA, so that also didnt work :(

---

### Post by Austin_KW on 2007-08-19
> **PeteZA said:**
> No,as far as i am aware, I am using WPA, so that also didnt work :(

Can your see your network,"iwlist wlan0 scan"

Where are your wpa configuration commands? I would have expected to see them between ```
peter@peter-desktop:~$ sudo ifconfig wlan0 up
...
peter@peter-desktop:~$ sudo dhclient wlan0
```

---

### Post by PeteZA on 2007-08-19
i get the following output when i run iwlist: 
```
wlan0     Scan completed :
          Cell 01 - Address: 00:12:0E:69:58:08
                    ESSID:"Venter"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Bit Rates:0 kb/s
          Cell 02 - Address: 02:30:1A:69:58:08
                    ESSID:"Desktop"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Bit Rates:0 kb/s

```

the first one is set up on WPA, and the second one I set up on my router with WEP to see if I could get it to work

---

### Post by Austin_KW on 2007-08-19
> **PeteZA said:**
> i get the following output when i run iwlist: 
```
wlan0     Scan completed :
          Cell 01 - Address: 00:12:0E:69:58:08
                    ESSID:"Venter"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Bit Rates:0 kb/s
          Cell 02 - Address: 02:30:1A:69:58:08
                    ESSID:"Desktop"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Bit Rates:0 kb/s

```

the first one is set up on WPA, and the second one I set up on my router with WEP to see if I could get it to work

Ok, both of those are on channel 11, NOT a good idea, move one to channel 1 or 6.

If you are having problems it is usually a good idea to temporarily disable encryption to verify that you can connect and then turn encryption on when things are working/.

---

### Post by PeteZA on 2007-08-19
I disabled the second account there was no point if i am going to turn off the encryption for the time being, which i have done, when i run dhclient i get the following, and it still doesnt connect to the network:

 ```
peter@peter-desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 10505
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:19:5b:2c:65:e6
Sending on   LPF/wlan0/00:19:5b:2c:65:e6
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 10.0.0.2
bound to 10.0.0.4 -- renewal in 1628 seconds.

```

---

### Post by Austin_KW on 2007-08-19
> **PeteZA said:**
> I disabled the second account there was no point if i am going to turn off the encryption for the time being, which i have done, when i run dhclient i get the following, and it still doesnt connect to the network:

 ```
peter@peter-desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 10505
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:19:5b:2c:65:e6
Sending on   LPF/wlan0/00:19:5b:2c:65:e6
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 10.0.0.2
bound to 10.0.0.4 -- renewal in 1628 seconds.

```

That WORKED, you are on the network using address 10.0.0.4

Try the following 
ping your router "ping -c3 10.0.0.2"
ping google.com "ping -c3 google.com"
ping google.com by address "ping -c3 64.233.187.99"
Do a dns lookup of google.com "dig google.com"

---

### Post by PeteZA on 2007-08-19
ok, that didnt work here is the output:

```
peter@peter-desktop:~$ ping -c3 10.0.0.2
PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.

--- 10.0.0.2 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

peter@peter-desktop:~$ ping -c3 google.com
ping: unknown host google.com
peter@peter-desktop:~$ ping -c3 64.233.187.99
PING 64.233.187.99 (64.233.187.99) 56(84) bytes of data.

--- 64.233.187.99 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2001ms

peter@peter-desktop:~$ dig google.com

; <<>> DiG 9.3.4 <<>> google.com
;; global options:  printcmd
;; connection timed out; no servers could be reached

```

---

### Post by Austin_KW on 2007-08-19
> **PeteZA said:**
> ok, that didnt work here is the output:

```
peter@peter-desktop:~$ ping -c3 10.0.0.2
PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.

--- 10.0.0.2 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

peter@peter-desktop:~$ ping -c3 google.com
ping: unknown host google.com
peter@peter-desktop:~$ ping -c3 64.233.187.99
PING 64.233.187.99 (64.233.187.99) 56(84) bytes of data.

--- 64.233.187.99 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2001ms

peter@peter-desktop:~$ dig google.com

; <<>> DiG 9.3.4 <<>> google.com
;; global options:  printcmd
;; connection timed out; no servers could be reached

```
Ok, so it is not working after getting the address,
What is the ouput of "route"
You might try manually taking down eth0 in case it is still trying to route via eth0 "sudo ifconfig down eth0"

---

### Post by PeteZA on 2007-08-19
Here is the output of route, along with the error that it gave me when i tried to down eth0

```
peter@peter-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
10.0.0.0        *               255.255.255.0   U     0      0        0 wlan0
default         login.router    0.0.0.0         UG    0      0        0 wlan0
default         login.router    0.0.0.0         UG    0      0        0 eth0
peter@peter-desktop:~$ sudo ifconfig down eth0
Password:

eth0: Unknown host
ifconfig: `--help' gives usage information.

```

---

### Post by Austin_KW on 2007-08-19
> **PeteZA said:**
> Here is the output of route, along with the error that it gave me when i tried to down eth0

```
peter@peter-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
10.0.0.0        *               255.255.255.0   U     0      0        0 wlan0
default         login.router    0.0.0.0         UG    0      0        0 wlan0
default         login.router    0.0.0.0         UG    0      0        0 eth0
peter@peter-desktop:~$ sudo ifconfig down eth0
Password:

eth0: Unknown host
ifconfig: `--help' gives usage information.

```

That's the problem (the first route thru eth0) , sorry typo "sudo ifconfig eth0 down"

---

### Post by PeteZA on 2007-08-19
Hi, ok, that appeared to take down eth0, but the output from route was the following:

```
peter@peter-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
peter@peter-desktop:~$ sudo dhclient eth0

```

ok, I pinged google again, and it appears to be working now, will try to get WPA working by following the guide

[I]edit:[I]
I tried switching on WPA on the router, but then the wireless went down again. Not sure if it makes any difference i managed to get RutilT to connect to the router with WPA, or at least it said it was connected, however when i tried to ping google it still doesnt wotk :(...

ok, it appears to be working now with RutilT, i just need to find a way to get it to run on startup, but there will be a way

---

### Post by spartan777 on 2007-08-20
here is what I'm getting after typeing "sudo ifconfig wlan0 up" in step 13:

```
calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ sudo make install
*** Install module in /lib/modules/2.6.20-16-generic/extra ...
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/usr/src/rt73-cvs-2007082012/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  INSTALL /usr/src/rt73-cvs-2007082012/Module/rt73.ko
  DEPMOD  2.6.20-16-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
/sbin/depmod -a
*** Update /etc/modprobe.conf alias for wlan*
grep: /etc/modprobe.conf: No such file or directory
*** Install firmware in /lib/firmware ...
*** Check config ...
calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ sudo ifconfig wlan0 down
calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ sudo modprobe -r rt73usb
calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ sudo modprobe -r rt2570
calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ sudo modprobe -r rt2500usb
calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ sudo modprobe -r rt2x00lib
calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ gksu gedit /etc/modprobe.d/blacklist
calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ sudo modprobe -v rt73calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ 

```

My usb adapter is plugged in, what could be the problem?

---

### Post by Austin_KW on 2007-08-20
> **spartan777 said:**
> here is what I'm getting after typeing "sudo ifconfig wlan0 up" in step 13:

```
calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ sudo make install
*** Install module in /lib/modules/2.6.20-16-generic/extra ...
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/usr/src/rt73-cvs-2007082012/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  INSTALL /usr/src/rt73-cvs-2007082012/Module/rt73.ko
  DEPMOD  2.6.20-16-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
/sbin/depmod -a
*** Update /etc/modprobe.conf alias for wlan*
grep: /etc/modprobe.conf: No such file or directory
*** Install firmware in /lib/firmware ...
*** Check config ...
calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ sudo ifconfig wlan0 down
calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ sudo modprobe -r rt73usb
calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ sudo modprobe -r rt2570
calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ sudo modprobe -r rt2500usb
calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ sudo modprobe -r rt2x00lib
calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ gksu gedit /etc/modprobe.d/blacklist
calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ sudo modprobe -v rt73calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
calvin@calvin-desktop:/usr/src/rt73-cvs-2007082012/Module$ 

```

My usb adapter is plugged in, what could be the problem?

Is it wlan1, you can check with "ifconfig -a"

---

### Post by PeteZA on 2007-08-20
Ok, so I seem to have broken something (hopefully not too important), but i cant run the command 

> gksu gedit /etc/network/interfaces

it seems to just hang there now, it was working yesterday when i tried to run the HOWTO... any suggestions?

---

### Post by Austin_KW on 2007-08-20
> **PeteZA said:**
> Ok, so I seem to have broken something (hopefully not too important), but i cant run the command 



it seems to just hang there now, it was working yesterday when i tried to run the HOWTO... any suggestions?

You sure it is not open already, maybe minimized. Maybe reboot.

---

### Post by spartan777 on 2007-08-20
thanks Austin_kw, that did the job!

---

### Post by PeteZA on 2007-08-21
> **Austin_KW said:**
> You sure it is not open already, maybe minimized. Maybe reboot.

It does not appear to be open, and if i look at the system monitor, I don't see it loaded. tried rebooting, same thing. I can open it in read only mode if i do it through the explorer, thought I obviously can't save it then.

---

### Post by diepruis on 2007-08-21
> **PeteZA said:**
> It does not appear to be open, and if i look at the system monitor, I don't see it loaded. tried rebooting, same thing. I can open it in read only mode if i do it through the explorer, thought I obviously can't save it then.

Maybe you should install something like SciTE and just substitute that for gedit?

---

### Post by pshchelo on 2007-08-21
Hi everyone :)
Being rather new Ubuntu user I'm trying to get my rt73-based wlan usb adapter up and working. With the help of this great post I've succeeded half-way already :), but here is my problem:

I'm using Kubuntu-7.04-amd64 on Athlon64 X2. I've successfully compiled driver from sources, inserted the module into kernel, disabled all other possibly conflicting modules and uninstalled "Network Manager" - everything as the post suggests. I've configured the interface (via editing etc/network/interfaces) and now I'm even being able to successfully connect with the router and acquire an IP from its DHCP - luckily I have also a notebook and can check the status of router independently (and to write this post also :) ).

Now is the weird part - there is still no network. I can't even connect to the router's web interface via direct IP address - browser doesn't find this IP. I've played aroud a bit and found out that the problem might be in encryption - I was using WPA2-AES auth/ecrypt, and when I have disabled any encryption everything started working like a charm. But when I'm setting up the router and the adapter for anything encrypted (WEP, WPA, WPA2) - there is again no network. 

What could be the reason? :confused:

---

### Post by PeteZA on 2007-08-21
> **diepruis said:**
> Maybe you should install something like SciTE and just substitute that for gedit?

excuse my n00b-ness, but how would i do that. and how would it affect the command that needs to be run?

---

### Post by Austin_KW on 2007-08-21
> **PeteZA said:**
> It does not appear to be open, and if i look at the system monitor, I don't see it loaded. tried rebooting, same thing. I can open it in read only mode if i do it through the explorer, thought I obviously can't save it then.

Try command line editor
sudo nano /etc/network/interfaces (make changes and ctrl-x to exit)

if that does not work what are the permissions/owner  on the file "ls -l /etc/network/interfaces"

---

### Post by Austin_KW on 2007-08-21
> **pshchelo said:**
> Hi everyone :)
Being rather new Ubuntu user I'm trying to get my rt73-based wlan usb adapter up and working. With the help of this great post I've succeeded half-way already :), but here is my problem:

I'm using Kubuntu-7.04-amd64 on Athlon64 X2. I've successfully compiled driver from sources, inserted the module into kernel, disabled all other possibly conflicting modules and uninstalled "Network Manager" - everything as the post suggests. I've configured the interface (via editing etc/network/interfaces) and now I'm even being able to successfully connect with the router and acquire an IP from its DHCP - luckily I have also a notebook and can check the status of router independently (and to write this post also :) ).

Now is the weird part - there is still no network. I can't even connect to the router's web interface via direct IP address - browser doesn't find this IP. I've played aroud a bit and found out that the problem might be in encryption - I was using WPA2-AES auth/ecrypt, and when I have disabled any encryption everything started working like a charm. But when I'm setting up the router and the adapter for anything encrypted (WEP, WPA, WPA2) - there is again no network. 

What could be the reason? :confused:
Are you saying that you can get an IP address but cannnot browse/ping the router? If so it sounds like routing.
What is the output of the command "route"

If you get a dhcp address then encryption/key is working.

If you were also connected on ethernet, manually take down the ethernet interface "sudo ifconfig eth0 down", there may still be a route thru this interface.

I dont understand why it appears to work with encryption off.

---

### Post by pshchelo on 2007-08-21
> **Austin_KW said:**
> 
What is the output of the command "route"


the output of *route* without encryption
```
family@swthm-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan1
link-local      *               255.255.0.0     U     1000   0        0 wlan1
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan1
```

the output of *route* with encryption (pretty much the same)
```
family@swthm-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan1
link-local      *               255.255.0.0     U     1000   0        0 wlan1
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan1
```

> **Austin_KW said:**
> 
If you were also connected on ethernet, manually take down the ethernet interface "sudo ifconfig eth0 down", there may still be a route thru this interface.



I have a LAN on my motherboard, but I disabled it through BIOS since I don't use it  and Kubuntu was installed afterwards (so it should not even be aware of LAN presence). However I have these additional interfaces in my /etc/network/interfaces right from the installation

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
```

with only *lo* intarface always running (according to *ifconfig*)
```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

Don't know what they are for and is it safe to disable them...

---

### Post by Austin_KW on 2007-08-21
pshchelo.
I dont understand, you have an ip address from dhcp (with encryption turned on), where have you configured this, it is not in the interfaces file. You had to be networked and working to get this address

Are you just changing encryption on the router?

---

### Post by pshchelo on 2007-08-21
> **Austin_KW said:**
> pshchelo.
I dont understand, you have an ip address from dhcp (with encryption turned on), where have you configured this, it is not in the interfaces file. You had to be networked and working to get this address

Are you just changing encryption on the router?

No, of course not :) I change settings both on router and on PC. Sorry for misunderstanding, the above was just the beginning of the interfaces file. As a whole it is the following

/etc/network/interfaces
```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan1
iface wlan1 inet dhcp
 pre-up ifconfig wlan1 up
 pre-up iwconfig wlan1 mode managed
 pre-up iwconfig wlan1 channel 11
 pre-up iwconfig wlan1 ap 00:0C:F6:20:AB:30
# pre-up iwconfig wlan1 AuthMode=OPEN
 pre-up iwpriv wlan1 set AuthMode=WPA2PSK	
 pre-up iwpriv wlan1 set EncrypType=AES
 pre-up iwpriv wlan1 set SSID="Sweet Home"
 pre-up iwpriv wlan1 set WPAPSK="my_secret_code"
 pre-up iwpriv wlan1 set SSID="Sweet Home"


```

when configured without encryption I just comment/uncomment the wlan1-part as follows

```

auto wlan1
iface wlan1 inet dhcp
 pre-up ifconfig wlan1 up
 pre-up iwconfig wlan1 mode managed
 pre-up iwconfig wlan1 channel 11
 pre-up iwconfig wlan1 ap 00:0C:F6:20:AB:30
 pre-up iwconfig wlan1 AuthMode=OPEN
# pre-up iwpriv wlan1 set AuthMode=WPA2PSK	
# pre-up iwpriv wlan1 set EncrypType=AES
# pre-up iwpriv wlan1 set SSID="Sweet Home"
# pre-up iwpriv wlan1 set WPAPSK="my_secret_code"
 pre-up iwpriv wlan1 set SSID="Sweet Home"

```

---

### Post by Austin_KW on 2007-08-21
pshchelo.
Ok, makes more sense now,
So what do you type after changing the encyrption, Something like "sudo ifup --f wlan1" or do you restart networking or do you reboot.

What is the output from "sudo ifup --f wlan1" Note the double '-' before the 'f'

---

### Post by corbinator9000 on 2007-08-21
This works great for me in 6.06, but in feisty, after the line 
      "sudo ifconfig wlan0 up"
I get the response 
      "wlan0: ERROR while getting interface flags: No such device"
Any ideas? 

Note: before using this guide I did a complete uninstall on networkmanager with synaptic if that might have caused anything

Thanks!

---

### Post by Austin_KW on 2007-08-21
Check if your interface is wlan1. Use "ifconfig -a" or "iwconfig" to list your interfaces

Diepruis, Maybe you should add a comment to the OP about the interface number. I seems to be comming up as wlan1 for a number of posters? Not sure why wlan0 is still reserved after taking down the interface and 'modprobe -r' of the original drivers.

---

### Post by diepruis on 2007-08-22
> **PeteZA said:**
> excuse my n00b-ness, but how would i do that. and how would it affect the command that needs to be run?

Just search for a package named "scite" through the package manager, or type "sudo aptitude install scite" into a terminal window. Then you need to type "gksu scite /etc/network/interfaces". Of course, you can also use nano as Austin_KW suggested.

---

### Post by diepruis on 2007-08-22
> **Austin_KW said:**
> Diepruis, Maybe you should add a comment to the OP about the interface number. I seems to be comming up as wlan1 for a number of posters? Not sure why wlan0 is still reserved after taking down the interface and 'modprobe -r' of the original drivers.

Good idea, it's been added.

---

### Post by pshchelo on 2007-08-22
> **Austin_KW said:**
> pshchelo.
Ok, makes more sense now,
So what do you type after changing the encyrption, Something like "sudo ifup --f wlan1" or do you restart networking or do you reboot.

What is the output from "sudo ifup --f wlan1" Note the double '-' before the 'f'
Austin_KW,
I was always using ifdown/ifup without "--f" switch. And when going from encryption to no encription that was enough, however when going backwards (from no encrypt to encrypt) nothing but reboot helped. I have just tried it with "--f" and no reboot was needed - adapter connects to the router and gets an IP, but still no connection under encryption and everything is fine without it.

here is "ifup --f wlan1" output
```
root@swthm-desktop:~# ifup --f wlan1
There is already a pid file /var/run/dhclient.wlan1.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:0e:2e:e3:18:39
Sending on   LPF/wlan1/00:0e:2e:e3:18:39
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 11
DHCPOFFER from 192.168.0.1
DHCPREQUEST on wlan1 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.102 -- renewal in 387565 seconds.
```

---

### Post by Austin_KW on 2007-08-22
> **pshchelo said:**
> ...

here is "ifup --f wlan1" output
```
root@swthm-desktop:~# ifup --f wlan1
There is already a pid file /var/run/dhclient.wlan1.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:0e:2e:e3:18:39
Sending on   LPF/wlan1/00:0e:2e:e3:18:39
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 11
DHCPOFFER from 192.168.0.1
DHCPREQUEST on wlan1 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.102 -- renewal in 387565 seconds.
```

Now I really dont understand. It is working right here or it could not get the DHCPOFFER from 192.168.0.1


Things to try;
Remove the Space from your SSID. This is technically a violation of the specification. I have seen lots of people do it but the spec says that the SSID should be max 32 alphanumeric characters. The SSID and the PSK is used in a hash function to create the encryption key so maybe there is some problem on the hashing function. You might also try a temporary simpler 8 character alphanumeric PSK (i dont know what you are using but some early routers has errors in the hashing function for special characters). It is unlikely this will be your problem as you router must be newer if it supports WPA2.

Also try reducing your authentication and encryption to WPA-PSK.

After that, I'll have to think. Maybe someone else has some ideas.

---

### Post by dannyboy79 on 2007-08-22
> **Austin_KW said:**
> For those of you curious to use the new rt2x00 beta driver. I am now typing this on feisty with the new driver and networkmanager
```

austin@austin-laptop:~$ lsmod | grep usbcore
usbcore               137864  6 rt73usb,rt2x00usb,usbhid,ehci_hcd,ohci_hcd

```

Scanning is not finding all networks but it seems to work if you manually tell it the network name.

I had to install the gusty kernel and update the wireless tools. I have my rt73usb working but not my rt2500pci.

I attach my script to update to the Gutsy kernel and wireless tools (based on kernel.sh found in these forums). I will try updating the rt2x00 later and hopefully have futher success but it is looking good for gusty

You will have to make the script executable and change the blacklist, I am not giving instructions as if you dont know how you should not experiment with this. You will also need network manager if you removed it.

well I finally got around to trying this on Xubuntu Gutsy Tribe 4 and it still does NOT work. I have ran your script, usbcore shows all 3 of the rt73usb, rt2500usb, rt2x00lib or whatever it was, wlan0 does show up but still nothing! WHen I try to do sudo ifup --f wlan0 i get something like not enough room in buffer. It was a very weird error. I am at work so i'll have to check it again and write the exact thing down. Also, when you say to install teh latest gutsy wireless-tools, does something other than just ensuring that I enable the gutsy backport (proposed) within the Package Source dialog, then ensuring that I am all up-to-date with all my packages? Cause like I said, I am already runninng Tribe 4.

This is getting pretty rediculious. I could just be using the rt73 from serialmonkey and not messing with this "out-of-the-box" driver that doesn't seem to be working for me within Xubuntu BUT I do want to help ensure this does work when gutsy is released which is the only reason I am sticking with this.

---

### Post by kevdog on 2007-08-22
Rather than checking ifconfig -a to find the interface name (ie wlan0), isn't it more accurate to actually check lshw -C network, look for the wireless device, and then find the line that states logical name??  The reason for this is that in cases where the /etc/iftab is configured incorrectly, I think the ifconfig statment can produce erroneous results.

In either method you are recommending for the instructions, I would post an example of the output of the specific command (ie ifconfig, lshw ...) and highlight the interface name.  Although your instructions are clear as day, I'm finding a lot of people skipping the text part of your instructions and just attenmpting to type whatever is in the code boxes.  Also just to make the point more clear, I would refer to the interface name for the remainder of the instructions, as <interface _name> rather than specifically wlan0, etc.  

I think this might help cut down on the number of questions regarding common errors regarding wlan0 errors.

---

### Post by Austin_KW on 2007-08-22
Dannyboy79,

I think it should work in gutsy. I only had to update to the gutsy tools and drivers because I am running on feisty. (I did not put clear instructions on this because I don't want new users to do this, it can be difficult to undo)

You do not want to use ifup or the interfaces file to bring up the network. This will cause problems. Remove all the wlan0 configuration from the interfaces file. Use the network manager, it should list your network (assuming it is not hidden).

You may want to blacklist rt2500usb, I did not have to, but it would depend on your USB id. Do NOT blacklist rt2x00lib.

First try "sudo iwlist scan" Note you need sudo for the beta drivers

I had to edit /etc/iftab, and change my interface to wlan1, because I had a legacy driver configuration in /etc/network/interfaces for wlan0 that was causing me problems.

Do not remove the usb device when the interface is up. First "sudo ifconfig wlan0 down", wait 10 seconds, then remove it. Then "sudo ifconfig wlan0 up when you reinsert it" It caused all networking to hang if I just removed it, but this may be because I was basically running on feisty.

When you use the network manager, just select your Network name, it should be listed. If it does not get an IP address in a couple of seconds, just select it again. It usually works the second time.

I have gone back to the legacy drivers because the rt2500pci (my main card) has speed problems when left idle, but the rt73usb worked great (better than the rt73 legacy driver which has problems on my laptop).

---

### Post by pshchelo on 2007-08-22
Austin_KW,
tried what you proposed (all accumulating one by one):
removed space from SSID - no change;
then removed spaces in PSK - no change;
then shortened PSK to 8 chars - no change (the router even complained a bit that the PSK should be minimum 8 chars).
And then I moved to WPA, and here had some changes - but not the positive ones. Now I cannot connect to the router at all, "ifup --f wlan1" doesn't find any "DHCPOFFERS", and when I look at the router associated wireless clients list I see the connection rapidly appearing and disappearing. When I took a look in the routers log, I've found following repeating lines:
```
0day 03:56:00 wlan0: A wireless client is associated - 00:0E:2E:E3:18:39
0day 03:56:00 wlan0: WPA-TKIP PSK authentication in progress... 
0day 03:56:00 wlan0: Open and authenticated 
0day 03:56:03 wlan0: A STA is rejected by 802.1x daemon - 00:0E:2E:E3:18:39

```
Also another active interface "wlan1:aha" appeared when switching WPA and doing "ifup -- f wlan1" - don't know if it means anything.
I tried it in all combinations auth/encrypt and only WPA-auth gives such a result, switching between AES and TKIP has no effect. For the sake of completeness I also tried WEP 64bit and WEP 128bit, and there situation is the same as with WPA2 (authenticated and IP leased but no networking).
Slowly starting to think that it could be some strange bug in the router firmware (but on the over hand in Windows everything works without any problems). I'm going to try to upgrade it (saw some newer but beta versions on vendor's site).

---

### Post by corbinator9000 on 2007-08-22
I dont know if reposting comments is allowed, but mine seemed to be lost at the end of the page. I hope no one minds me reposting this. 

This works great for me in 6.06, but in feisty, after the line
"sudo ifconfig wlan0 up"
I get the response
"wlan0: ERROR while getting interface flags: No such device"
Any ideas?

Note: before using this guide I did a complete uninstall on networkmanager with synaptic if that might have caused anything

Thanks!

---

### Post by Austin_KW on 2007-08-22
> **corbinator9000 said:**
> I dont know if reposting comments is allowed, but mine seemed to be lost at the end of the page. I hope no one minds me reposting this. 

This works great for me in 6.06, but in feisty, after the line
"sudo ifconfig wlan0 up"
I get the response
"wlan0: ERROR while getting interface flags: No such device"
Any ideas?

Note: before using this guide I did a complete uninstall on networkmanager with synaptic if that might have caused anything

Thanks!

Eh, Check first post on the top of following page ;) use wlan1

---

### Post by Murrquan on 2007-08-22
> Please post your results with this steps, as I need that information to make this HOWTO better. If you experience problems, please ask in a separate thread and post a link to that thread here.

[Here]("http://ubuntuforums.org/showthread.php?p=3236429#post3236429") are my experiences following your instructions! I was trying to get the rt2500 drivers working, and ended up following pretty much the same procedure except that I substituted 2500 for 73. In addition, any reference to wlan0 failed, because I was looking for ra0 instead! I was stumped. But kevdog, on the linked thread, suggested using lshw -C network to find out what the interface was called. That worked for me, and my wireless in now up and running.

So, that's what happened. You may want to change the guide to reflect that it works with rt2500 as well, as it looks like some people have been asking about those. I don't know about the whole ra0 thing, maybe my PC's just weird. ^.^ At any rate, many thanks for the guide!

---

### Post by diepruis on 2007-08-23
> **Murrquan said:**
> So, that's what happened. You may want to change the guide to reflect that it works with rt2500 as well, as it looks like some people have been asking about those. I don't know about the whole ra0 thing, maybe my PC's just weird. ^.^ At any rate, many thanks for the guide!

I'll think about it. My only concern is that it might over complicate the thread.

---

### Post by diepruis on 2007-08-23
> **kevdog said:**
> Rather than checking ifconfig...

You make some good points and, for the most part, I agree with you. However, don't you think that these changes might make the guide a little too challenging to follow for the newbies? I'd prefer it if people could copy and paste most of the guide. If the instructions get too complicated, people might just give up entirely.

---

### Post by kevdog on 2007-08-23
I see your point about cutting and pasting, however its a two edge sword.  I refer a lot of people to your thread, and they do just that -- cut and paste -- no reading, just skipping to the boxes and cutting and pasting.  And then I get alot of comments like, wlan0 didnt work for me, or this command didnt work -- but I kept going and nothing worked in the end (because their interface name wasnt wlan0).

You are the author of this thread, so you write it anyway you think is best -- obviously it works for a lot of people, but look how many posts are written about problems that boil down to the wrong interface name (even some of your most experienced users!!).  Im not sure what the right answer is.  You might just add a section telling people how to correctly find their interface name and include an example(which I personally think is lshw -C network, but ifconfig probably works in the majority of cases), and then include your commands with the wlan0 interface (as currently written), with a disclaimer at the top in bold type stating **(These commands assume your interface name is wlan0, if yours is different (as described above) substitute your interface name in place of wlan0)**.

---

### Post by dannyboy79 on 2007-08-23
> **Austin_KW said:**
> For those of you curious to use the new rt2x00 beta driver. I am now typing this on feisty with the new driver and networkmanager
```

austin@austin-laptop:~$ lsmod | grep usbcore
usbcore               137864  6 rt73usb,rt2x00usb,usbhid,ehci_hcd,ohci_hcd

```

Scanning is not finding all networks but it seems to work if you manually tell it the network name.

I had to install the gusty kernel and update the wireless tools. I have my rt73usb working but not my rt2500pci.

I attach my script to update to the Gutsy kernel and wireless tools (based on kernel.sh found in these forums). I will try updating the rt2x00 later and hopefully have futher success but it is looking good for gusty

You will have to make the script executable and change the blacklist, I am not giving instructions as if you dont know how you should not experiment with this. You will also need network manager if you removed it.

still can't get my belkin F5D7050 to work with gutsy Tribe 4 xubuntu. I have even tried your attached test.sh. 

I get this error when trying to bring up the interface:
sudo ifup --f wlan0
SIOCSIFFLAGS: No buffer space available
Failed to bring up wlan0.

this is the kernel
2.6.22-9-generic

the version of wireless-tools:
29~pre20-1ubuntu1 

So, please please help me understand how you got yours working WITHOUT downloading the rt73 from serialmonkey.com. thank you.

---

### Post by Austin_KW on 2007-08-23
> **dannyboy79 said:**
> still can't get my belkin F5D7050 to work with gutsy Tribe 4 xubuntu. I have even tried your attached test.sh. 

I get this error when trying to bring up the interface:
sudo ifup --f wlan0
SIOCSIFFLAGS: No buffer space available
Failed to bring up wlan0.

this is the kernel
2.6.22-9-generic

the version of wireless-tools:
29~pre20-1ubuntu1 

So, please please help me understand how you got yours working WITHOUT downloading the rt73 from serialmonkey.com. thank you.

Yes same versions, ('cept I have them installed (hacked) on feisty)

But you are still trying to bring the interface up with ifup. That would read the config from /etc/network/interfaces. You need to use the network-manager.** Remove all wlan0 config from the interfaces file.**
Then start with "ifconfig" did it create wlan0 and wmaster0
Does "sudo iwlist scan" list your networks

---

### Post by dannyboy79 on 2007-08-23
> **Austin_KW said:**
> Yes same versions, ('cept I have them installed (hacked) on feisty)

But you are still trying to bring the interface up with ifup. That would read the config from /etc/network/interfaces. You need to use the network-manager.** Remove all wlan0 config from the interfaces file.**
Then start with "ifconfig" did it create wlan0 and wmaster0
Does "sudo iwlist scan" list your networks
yes, it created wlan0 and wmaster0
i am using xubuntu, so I don't have network-manager. I did install it but it didn't add an entry into my menu. When I try to run it manually by issuing
gksudo network-manager
it says command not found. Any suggestions? Also, I noticed that rt2500 was not installed but was there in synaptic when I did a search using keyword "wireless", am I supopse to install that also? Also, do I need to blacklist anything, you said I did but you're other post stated that you weren't going to post how because it would confuse the thread. can you send me a pm then?

---

### Post by Austin_KW on 2007-08-23
> **dannyboy79 said:**
> yes, it created wlan0 and wmaster0
i am using xubuntu, so I don't have network-manager. I did install it but it didn't add an entry into my menu. When I try to run it manually by issuing
gksudo network-manager
it says command not found. Any suggestions? Also, I noticed that rt2500 was not installed but was there in synaptic when I did a search using keyword "wireless", am I supopse to install that also? Also, do I need to blacklist anything, you said I did but you're other post stated that you weren't going to post how because it would confuse the thread. can you send me a pm then?

You probably want "sudo apt-get install network-manager-gnome" and i think the application is then nm-applet (not sure as I usually use kde).
I think rt2500 is just a source package and not needed.

You may want to remove rt2500usb.ko. "sudo modprobe -r rt2500usb" and add then add "blacklist rt2500usb" to /etc/modprobe.d/blacklist. I use the same belkin card and I did not need to. But if you are having problems.


What about the output from "sudo iwlist wlan0 scan", do you see you networks?

---

### Post by diepruis on 2007-08-25
> **kevdog said:**
> I see your point about cutting and pasting, however its a two edge sword.  I refer a lot of people to your thread, and they do just that -- cut and paste -- no reading, just skipping to the boxes and cutting and pasting.  And then I get alot of comments like, wlan0 didnt work for me, or this command didnt work -- but I kept going and nothing worked in the end (because their interface name wasnt wlan0).

You are the author of this thread, so you write it anyway you think is best -- obviously it works for a lot of people, but look how many posts are written about problems that boil down to the wrong interface name (even some of your most experienced users!!).  Im not sure what the right answer is.  You might just add a section telling people how to correctly find their interface name and include an example(which I personally think is lshw -C network, but ifconfig probably works in the majority of cases), and then include your commands with the wlan0 interface (as currently written), with a disclaimer at the top in bold type stating **(These commands assume your interface name is wlan0, if yours is different (as described above) substitute your interface name in place of wlan0)**.

Any other opinions on this?

---

### Post by File13 on 2007-08-28
alright this has worked for me multiple times after ive reinstalled from screwing something or other up anyways question is until recently i had no need to change wireless AP's since i was only in my house but now im taking my laptop to school and when i want to connect on campus im not sure how to go about doing that as my /etc/network/interfaces is set to my house. so my question is is there some sort of sequence it can follow like if it doesnt see my house ESSID it will goto the school campus one, or better yet how would i just go about connecting to other AP's in general that arnt listed in my /etc/network/interfaces. im dying to know!

---

### Post by diepruis on 2007-08-28
> **File13 said:**
> alright this has worked for me multiple times after ive reinstalled from screwing something or other up anyways question is until recently i had no need to change wireless AP's since i was only in my house but now im taking my laptop to school and when i want to connect on campus im not sure how to go about doing that as my /etc/network/interfaces is set to my house. so my question is is there some sort of sequence it can follow like if it doesnt see my house ESSID it will goto the school campus one, or better yet how would i just go about connecting to other AP's in general that arnt listed in my /etc/network/interfaces. im dying to know!

The usual approach is to use a graphical program and set up multiple profiles. Take a look at RutilT, which is available from the serialmonkey website (rt2x00.serialmonkey.com).

Of course, you can always just set up a shell script and run that...

---

### Post by dannyboy79 on 2007-08-28
bad news, it still DOESN'T work in Gutsy Tribe 5!!!!! Same ol one this whole time. Belkin F5D7050, it has a 2571wf chip in it. MAN, how long until they get this right????

Bus 001 Device 003: ID 050d:705a Belkin Components

lsmod | grep rt
rt2500usb              22016  0 
rt73usb                25344  0 
rt2x00usb              12032  2 rt2500usb,rt73usb
rt2x00lib              19712  3 rt2500usb,rt73usb,rt2x00usb
rfkill                  8208  1 rt2x00lib
mac80211              171016  3 rc80211_simple,rt2x00usb,rt2x00lib
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
iTCO_vendor_support     4868  1 iTCO_wdt
agpgart                35016  1 intel_agp
usbcore               137864  8 usb_storage,libusual,rt2500usb,rt73usb,rt2x00usb,usbhid,uhci_hcd


uname -r
2.6.22-10-generic


[ 6680.636084] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3008 with error -110.
[ 6680.735955] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3024 with error -110.
[ 6680.835830] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3024 with error -110.
[ 6680.935705] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3020 with error -110.
[ 6681.035580] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3020 with error -110.
[ 6681.135458] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[ 6681.235331] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[ 6681.336204] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3050 with error -110.
[ 6681.436080] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3050 with error -110.
[ 6681.535954] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3064 with error -110.
[ 6681.635831] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -110.
[ 6681.735704] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x01 failed for offset 0x0000 with error -110.
[ 6681.835579] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[ 6681.935453] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3030 with error -110.
[ 6682.035329] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[ 6682.151187] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[ 6682.267040] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[ 6682.382894] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[ 6682.498750] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[ 6682.513866] phy0 -> rt73usb_enable_radio: Error - Register initialization failed.


I will try what Austin said to do, to blacklist rt2500usb on the previous page and then if that doesn't do it, than I don't know what would!

---

### Post by Austin_KW on 2007-08-28
I have never had much luck with RutilT, it reports my network as WEP even thoughh it is WPA and refuses to connect. (I should capture the beacon frame and post the IEs to serialmonkey forums)

I just use the command line and save it to a script if I am going to use a network more than once. If you an not sure of the iwconfig/iwpriv commands then use the original post and make yourself a sample OPEN,WEP and WPA-PSK script then just modify the SSID and key as needed. Remember to "chmod +x scripfilename" to make it executable.


You may have better luck with RutilT, so it may be worth trying.
Download it from here [http://cbbk.free.fr/bonrom/](http://cbbk.free.fr/bonrom/)

You will need some extra build stuff;
sudo apt-get install  libgtk2.0-dev g++

When you build it use
./configure.sh --launcher=external
make
sudo make install

---

### Post by Austin_KW on 2007-08-28
> **dannyboy79 said:**
> bad news, it still DOESN'T work in Gutsy Tribe 5!!!!! Same ol one this whole time. Belkin F5D7050, it has a 2571wf chip in it. MAN, how long until they get this right????

Bus 001 Device 003: ID 050d:705a Belkin Components
...
[ 6682.498750] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[ 6682.513866] phy0 -> rt73usb_enable_radio: Error - Register initialization failed.


I will try what Austin said to do, to blacklist rt2500usb on the previous page and then if that doesn't do it, than I don't know what would!

Yes try the blacklist, I have updated to the latest kernel (should be the same, albeit on feisty)
austin@austin-laptop:~$ uname -a
Linux austin-laptop 2.6.22-10-generic #1 SMP Wed Aug 22 08:11:52 GMT 2007 i686 GNU/Linux

and I have the same adapter.
austin@austin-laptop:~$ lsusb
Bus 003 Device 005: ID 050d:705a Belkin Components
Bus 003 Device 001: ID 0000:0000


You might also try the latest CVS build
You need to make 2 modifications to get it to build
tar -xvzf rt2x00-cvs-daily.tar.gz 
cd rt2x00-cvs-2007082807 

In  file rt2x00mac.c change "rt2x00dev->interface.id," to "//rt2x00dev->interface.id," on line 60 and 64
Add a missing definition to rt2x00.h with;
echo '#define IEEE80211_TXCTL_LONG_RETRY_LIMIT (1<<10)' >> rt2x00.h

make 
sudo make install

remove your adapter
remove the old drivers "sudo modprobe -rv rt73usb". (And its dependencies)

reinsert your module

---

### Post by dannyboy79 on 2007-08-28
thanks for the info, are you informing the developer's of all this?? I mean, if you can solve it this easily, why can't they? I want it to work "out-of-the-box" as it's a pretty common adapter. If it doesn't work out of the box, than many many Users will just go back to Winbloz. I won't because I know how to fix it either using rt73 or what you have posted above but that's not the point.

---

### Post by Austin_KW on 2007-08-28
> **dannyboy79 said:**
> thanks for the info, are you informing the developer's of all this?? I mean, if you can solve it this easily, why can't they? I want it to work "out-of-the-box" as it's a pretty common adapter. If it doesn't work out of the box, than many many Users will just go back to Winbloz. I won't because I know how to fix it either using rt73 or what you have posted above but that's not the point.

No, It worked out of the box for me; Also I have a mixed feisty/gutsy (unsupported) system.  What does not work for me is the rt2500pci (well it works but the speed drops to 1/2 Mbs and then does not go back up) So my main driver is the legacy rt2500. 

Another problem seems to be that the card manufacturers seem to change chipsets without changing the ID eeprom. Hence we get the multiple drivers trying to manage the adapters (even with the legacy drivers) I dont know how the developers can fix this unless the serialmonkey drivers do a better job of probing the USB devices/chipsets but if the use the same usb interface chips then that may be impossible.

If you look at the drivers 
```

 grep 705a *
rt2500usb.c:    { USB_DEVICE(0x050d, 0x705a), USB_DEVICE_DATA(&rt2500usb_ops) },
rt73usb.c:      { USB_DEVICE(0x050d, 0x705a), USB_DEVICE_DATA(&rt73usb_ops) },

```
you see that this id can be rt2500usb or a rt73. So it looks like belkin/other OEMs are to blame for this. Hence all the blacklisting in the OP of this thread.

So did you get the beta driver to work? If so how did it perform.

---

### Post by dannyboy79 on 2007-08-28
i haven't been home yet to try blacklisting or anything yet. when you say to try out the beta driver, are you talking about the downloading of rt2x00-cvs-daily.tar.gz and doing your instructions?

I will first attempt everything in my power to resolve "out-of-the-box"  wireless support, if all else fails than I will give the beta drivers a try. if those fail I will go back to the trusty rt73 daily cvs build that I had working in Tribe 4 Ubuntu.

thanks for all your comments. they are very knowledgable as I normally don't open up the code as you have shown me. it's a problem as you say with the Manufactures. They think all Winbloz people will buy it and could care less about other OS's which is probably why they change the chip without changing whatever it was you said.

---

### Post by File13 on 2007-08-28
also before i go reinstalling is there a way i can for sure check weather the usb device is wlan1 or wlan0. i know ive gone through the instructions before thinking it was wlan0 and it ended up being wlan1 so what do i type in terminal to check which one it is?

---

### Post by Austin_KW on 2007-08-28
> **File13 said:**
> also before i go reinstalling is there a way i can for sure check weather the usb device is wlan1 or wlan0. i know ive gone through the instructions before thinking it was wlan0 and it ended up being wlan1 so what do i type in terminal to check which one it is?

"ifconfig -a" will list all your network interfaces
"iwconfig" will list the wireless extensions to the network interfaces

---

### Post by dannyboy79 on 2007-08-29
blacklisting rt2x00usb or rt2500usb does not work with either WPA-PSK or WEP or no encryption. Oh well, another alpha release where it doesn't work. In fact, I booted the live cd without the sub adapter plugged in, blacklisted the rt2x00usb, and then when I plugged it in, the module was still loaded and I couldn't even modprobe -r it. it said it was being used. huh?

---

### Post by Austin_KW on 2007-08-29
> **dannyboy79 said:**
> blacklisting rt2x00usb or rt2500usb does not work with either WPA-PSK or WEP or no encryption. Oh well, another alpha release where it doesn't work. In fact, I booted the live cd without the sub adapter plugged in, blacklisted the rt2x00usb, and then when I plugged it in, the module was still loaded and I couldn't even modprobe -r it. it said it was being used. huh?

I dont think you want to blacklist rt2x00usb, this is a generic driver used by rt73usb. Just blacklist rt2500usb and make sure it is not loaded.

When you use the networkmanager; sometimes it takes a couple of attempts to connect and get an Ip address. If it does not work within ~20 seconds just select your network again.

---

### Post by dannyboy79 on 2007-08-29
ok, i'll try that but I didn't see rt2500 within lsmod when I checked it after I inserted the usb adapter. Also, it appeared to connect (the little network icon changed from the 2 computers with the orange thingy, to the little steps going to the right and they were filled in with blue) when I tried WPA-PSK BUT as soon as I tried firefox, I had these errors filling my syslog and dmesg.

[ 6680.636084] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3008 with error -110.

here's the bug I submitted and more info for you if you're interested. 

[https://bugs.launchpad.net/ubuntu/+source/rt2x00/+bug/135279](https://bugs.launchpad.net/ubuntu/+source/rt2x00/+bug/135279)

---

### Post by File13 on 2007-08-30
it lists as wlan0 before i run that wlan0 down command, but after you reload the module it comes up as wlan1...is this normal and what should i do?

---

### Post by Austin_KW on 2007-08-30
> **File13 said:**
> it lists as wlan0 before i run that wlan0 down command, but after you reload the module it comes up as wlan1...is this normal and what should i do?

Don't worry about, it is just a name. It means that wlan0 was still in use when the driver allocated the name. Just use wlan1.

---

### Post by File13 on 2007-08-30
ok well this has happened two times in a row now but only since i dual booted but i doubt that has anything to do with it. anyways right when you take down wlan0 and blacklist the drivers when up load the new module and are asked to do ifconfig -a my usb doesnt come up it only lists lo and eth. ubuntu see's it still though if i run lsusb it shows its there, why is it not showing up as wlan though?!

---

### Post by Austin_KW on 2007-08-30
> **File13 said:**
> ok well this has happened two times in a row now but only since i dual booted but i doubt that has anything to do with it. anyways right when you take down wlan0 and blacklist the drivers when up load the new module and are asked to do ifconfig -a my usb doesnt come up it only lists lo and eth. ubuntu see's it still though if i run lsusb it shows its there, why is it not showing up as wlan though?!

Why are you taking it down/blacklisting/loading modules. This only ever needs to be done once. The blacklist is just that; a blacklist the stops the incompatible drivers from ever loading again.

Go through the installation procedure once; then forget about it and just use your connection on wlan0/wlan1 whatever it is.

---

### Post by File13 on 2007-08-31
i only do it once per install im not saying im blacklisting multiple times per install. when i take wlan0 down and modprobe the drivers then add them to the blacklist upon reloading the kernel nothing shows wlan0 or wlan1, thats what im trying to say, after i blacklist and remove the ones it tells me to the device is no longer listed. its only listed under lsusb.

---

### Post by Austin_KW on 2007-08-31
> **File13 said:**
> i only do it once per install im not saying im blacklisting multiple times per install. when i take wlan0 down and modprobe the drivers then add them to the blacklist upon reloading the kernel nothing shows wlan0 or wlan1, thats what im trying to say, after i blacklist and remove the ones it tells me to the device is no longer listed. its only listed under lsusb.

Sorry i misunderstood. 

What you are asking about is probably udev, This automatically recognizes your hardware, loads drivers into the kernel etc. It is "event" driven, i.e, it may need some stimulus to activate, like unplugging and reinserting the adapter.

---

### Post by jeclarim on 2007-08-31
Hi! I've installed Ubuntu 7.04 Feisty on my brand new mini-laptop UMPC Kohjinsha K601 (SH6).
Wifi device USB vendor/product id is 18e8:6238

I first tried to install Ralink 1.0.4.0 driver. It works but you have to configure manually the default parameters in /etc/Wireless/RT73STA/rt73sta.dat
However scanning was disabled. Scanning code was commented out in rtmp_main.c because of #ifdef  testing for WIRELESS_EXT <= 20. I put 21 and scanning now does work.

I also tried to install serialmonkey driver instead.
USB device id 18e8:6238 wasn't listed in the source files so I added it.
wlan0 goes up, scanning works but dhcp fails with a timeout.

Which driver is supposed to be up to date and will make it in standard Ubuntu code tree?
(I guess serialmonkey rt73 code was derived from an older version than 1.0.4.0 by Ralinktech)

---

### Post by Austin_KW on 2007-08-31
The latest version is the cvs tar ball, see the original post in this thread. The serialmonkey drivers are derived from the GPL ralink drivers.

The newer beta drivers do not work in feisty so stay clear of them. 

If that is a new ID you may want to post in the serialmonkey forum for rt73 and rt2x00 to have them add it to the drivers.

---

### Post by Alex Broadbent on 2007-09-02
I apologise if this has already been covered somewhere in this very helpful thread, but: I got my Ralink usb stick working, but then the kernel updated itself, and when I restarted, the driver was obviously no longer working. But I can't reinstall because the build-essential headers aren't there. I don't have internet access on that computer except through wireless, but obviously I have internet access on another computer. So my questions are:
i) How can I download the required headers using another computer, put them on a CD or flash disk, and then install them from there?
ii) Alternatively - can I roll back to the old kernel? - Is there much point in updating it all the time, given that I'll need to recompile drivers every time?
iii) Can I set the download manager to get the necessary headers when it gets the new kernel? Alternatively, can I set it not to update the kernel at all?

Any assistance would be greatly appreciated!

Many thanks,
Alex

---

### Post by diepruis on 2007-09-02
> **Alex Broadbent said:**
> I apologise if this has already been covered somewhere in this very helpful thread, but: I got my Ralink usb stick working, but then the kernel updated itself, and when I restarted, the driver was obviously no longer working. But I can't reinstall because the build-essential headers aren't there. I don't have internet access on that computer except through wireless, but obviously I have internet access on another computer. So my questions are:
i) How can I download the required headers using another computer, put them on a CD or flash disk, and then install them from there?
ii) Alternatively - can I roll back to the old kernel? - Is there much point in updating it all the time, given that I'll need to recompile drivers every time?
iii) Can I set the download manager to get the necessary headers when it gets the new kernel? Alternatively, can I set it not to update the kernel at all?

Any assistance would be greatly appreciated!

Many thanks,
Alex

Hey, I'll answer your questions out of order, since that will make more sense:

II. Yes you can. Just hit escape when you see messages from GRUB during boot and choose the old kernel from the list.
III. Yes you can. You need to mark linux-headers, I believe, then it will automatically download headers for any new kernels.
I. Just boot your old kernel and download the headers from there.

---

### Post by Alex Broadbent on 2007-09-02
Thanks! I couldn't work out where to check "download headers" but I've checked "Always Ask" next to System Upgrades in package manager, so it doesn't upgrade automatically. That way I can decide whether to upgrade and then download the packages manually. - The driver/system relationship seems a bit delicate - two of the four kernels I have hard lock when I try to use the device (of the others, one works, and one I haven't tested - the ne that prompted this question).

One follow-up question - can I manipulate the order things appear in the GRUB menu? At present I have to manually select the only working kernel, which is a bit of a hassle. (Incidentally I would also like to have it boot Windows by default, for the sake of my long-suffering family who also use the computer and aren't as thrilled as I am by Ubuntu.)

Thanks again,
Alex

---

### Post by Austin_KW on 2007-09-02
> **Alex Broadbent said:**
> Thanks! I couldn't work out where to check "download headers" but I've checked "Always Ask" next to System Upgrades in package manager, so it doesn't upgrade automatically. That way I can decide whether to upgrade and then download the packages manually. - The driver/system relationship seems a bit delicate - two of the four kernels I have hard lock when I try to use the device (of the others, one works, and one I haven't tested - the ne that prompted this question).

One follow-up question - can I manipulate the order things appear in the GRUB menu? At present I have to manually select the only working kernel, which is a bit of a hassle. (Incidentally I would also like to have it boot Windows by default, for the sake of my long-suffering family who also use the computer and aren't as thrilled as I am by Ubuntu.)

Thanks again,
Alex

You can edit /boot/grub/menu.lst, 
Do not rearrange the order, you can; but the next install will reorder them.

Use the default keyword, Find "default" in /boot/grub/menu.lst, and remove the any comment '#'. The newest kernel is 0, the newest recovery kernel is 1, the previous kernel is 2 and so on down the list, eg,
default         2          #Will boot the previous kernel

---

### Post by Alex Broadbent on 2007-09-02
Thank you!!
Alex

---

### Post by File13 on 2007-09-03
its not working for me now that i have the system dual booted. i followed the steps just like i used to on non dual boots but now when i boot into ubuntu nothing happens, i have to go and manually type the sudo ifconfig wlan1 up, sudo iwconfig wlan1 essid,etc. to get it working. any idea why this is?

---

### Post by Alex Broadbent on 2007-09-03
Sorry, I am back with a slightly different question.

For some reason, I don't stay connected very reliably. After a time, I have to cycle the interface (ifdown wlan1, ifup wlan1). This almost always works (and if not I can mess around till it does) but I just wondered why it might be happening.

I suspect it is something to do with the message "renewal in 32570 seconds" which I get after running dhclient - I'm guessing it's not renewing. And I wonder whether that has anything to do with something called a PID file, which it tells me about when I go ifdown. The message I get then is:

```

root@alex-laptop:/home/alex# ifdown wlan1
There is already a pid file /var/run/dhclient.wlan1.pid with pid 13231
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:13:d3:76:cb:56
Sending on   LPF/wlan1/00:13:d3:76:cb:56
Sending on   Socket/fallback
DHCPRELEASE on wlan1 to 192.168.1.1 port 67
root@alex-laptop:/home/alex#

```

Any ideas?
Thanks,
Alex

---

### Post by diepruis on 2007-09-03
> **Alex Broadbent said:**
> Sorry, I am back with a slightly different question.

For some reason, I don't stay connected very reliably. After a time, I have to cycle the interface (ifdown wlan1, ifup wlan1). This almost always works (and if not I can mess around till it does) but I just wondered why it might be happening.

This could be nearly anything, from bad quality hardware, a poor router or obstructions to errors in the driver code. I suggest you pay a visit to the serialmonkey forums and post your problem there, along with some debug information. They should know more than me.

> **Alex Broadbent said:**
> 
I suspect it is something to do with the message "renewal in 32570 seconds" which I get after running dhclient - I'm guessing it's not renewing. And I wonder whether that has anything to do with something called a PID file, which it tells me about when I go ifdown. The message I get then is:


The renewal message has to do with something called a "DHCP lease", which is issued by your router to your network card. It contains an IP address for the device. Basically, that message means that your current IP address will expire in roughly 9 hours.

The PID file is simply a file containing the process ID for dhclient, the program that gets DHCP leases. If a process has a PID file, it means that it's currently running. This message is also pretty normal, I get it too.

---

### Post by Austin_KW on 2007-09-03
I have noticed that the drivers do not always reconnect  if they lose connection. 
If you are not connected the ifdown can take some time to complete (it tries to release the dhcp address). I use "sudo ifup --f wlan0" to reconnect, it is faster as it does not have to do the release.

---

### Post by Austin_KW on 2007-09-03
> **File13 said:**
> its not working for me now that i have the system dual booted. i followed the steps just like i used to on non dual boots but now when i boot into ubuntu nothing happens, i have to go and manually type the sudo ifconfig wlan1 up, sudo iwconfig wlan1 essid,etc. to get it working. any idea why this is?

Post you /etc/network/interfaces

---

### Post by Alex Broadbent on 2007-09-03
Thanks diepruis - it sounds like it could just be my (fairly rubbish) router. Thinking about it, I don't have to do this as often on some other networks when I'm out and about.

- And thanks Austin_KW for the faster reconnection tip too (I had noticed it chewing on the ifdown command).

---

### Post by File13 on 2007-09-03
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan1
iface wlan1 inet dhcp
pre-up ifconfig wlan1 up
pre-up iwconfig wlan1 essid Internetz
pre-up iwconfig wlan1 key 1834730061
```

---

### Post by Austin_KW on 2007-09-03
> **File13 said:**
> ```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan1
iface wlan1 inet dhcp
pre-up ifconfig wlan1 up
pre-up iwconfig wlan1 essid Internetz
pre-up iwconfig wlan1 key 1834730061
```
That looks ok; assuming that your interface is still wlan1 and you have not changed you network name or key. 

Try to bring it up with "sudo ifup --f wlan1". You should be able to use this command at any time to test configuration in the interfaces file.

Aside; If your router supports WPA-PSK your should consider changing to it.

---

### Post by diepruis on 2007-09-04
> **File13 said:**
> ```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan1
iface wlan1 inet dhcp
pre-up ifconfig wlan1 up
pre-up iwconfig wlan1 essid Internetz
pre-up iwconfig wlan1 key 1834730061
```

Mmmm... not too sure of myself here, but from the lack of A, B, C, D, E and F's in that key, I'm guessing it might be a string instead of a hex key. You could try putting an "s:" in front of those numbers (without the quotation marks of course).

---

### Post by Austin_KW on 2007-09-04
> **diepruis said:**
> Mmmm... not too sure of myself here, but from the lack of A, B, C, D, E and F's in that key, I'm guessing it might be a string instead of a hex key. You could try putting an "s:" in front of those numbers (without the qu4otation marks of course).

I thought of that but it is the right length for a 40 bit wep key and they are valid hex digits.
A string would be 5 or 13 characters (equivalent to 10 or 26 hex digits) and passphrase is not supported by iwconfig.

---

### Post by diepruis on 2007-09-04
> **Austin_KW said:**
> I thought of that but it is the right length for a 40 bit wep key and they are valid hex digits.
A string would be 5 or 13 characters (equivalent to 10 or 26 hex digits) and passphrase is not supported by iwconfig.

Ahhh... okay, fair enough.

---

### Post by jeclarim on 2007-09-05
> **Austin_KW said:**
> If that is a new ID you may want to post in the serialmonkey forum for rt73 and rt2x00 to have them add it to the drivers.

Done, thanks.
rt73 driver is now working on my Kohjinsha K601 (a.k.a. SH6 or Vye S37) :)

---

### Post by SteveDean on 2007-09-08
Thanks a lot for this Diepruis, and every other contributor. I'd been trying for weeks to get my D-Link GWL card working. After following this guide it's finally working!  No more cable running down the stairs, and I can finally dump that other, more common, (note 'common,' not 'popular'!) O/S and use some decent software. So, thanks to you people, that's one less for the MS and one more for Linux, Huzzah!

Thanks again

Steve Dean


:grin:

---

### Post by tranzit on 2007-09-08
Hello,
For several months I have tried to make my DWL-G122 rev. C1 adapter to work, but with no luck. I was advised to try your walk around, but it didn't helped too :( I think I did everything ok, but my internet connection needs ISP account (I may be wrong, because I am totally noob). I would be very grateful for any kind of help. I also attach my terminal's output, etc/network/interfaces and black list.

---

### Post by diepruis on 2007-09-09
> **tranzit said:**
> Hello,
For several months I have tried to make my DWL-G122 rev. C1 adapter to work, but with no luck. I was advised to try your walk around, but it didn't helped too :( I think I did everything ok, but my internet connection needs ISP account (I may be wrong, because I am totally noob). I would be very grateful for any kind of help. I also attach my terminal's output, etc/network/interfaces and black list.

Is the problem that you cannot access the internet? Or is the whole network (LAN) inaccessible? From what I can see, your logs look fine, except that your wlan1 interface does not have a IPv4 address. This might be a problem, but I'm not sure... could you post the output of

```

sudo ifdown wlan1
sudo ifup wlan1

```

---

### Post by tranzit on 2007-09-09
> Is the problem that you cannot access the internet? Or is the whole network (LAN) inaccessible? From what I can see, your logs look fine, except that your wlan1 interface does not have a IPv4 address. This might be a problem, but I'm not sure... could you post the output of

I can access my network, but i can't access internet. My internet connection requires a user name and password. In other forum someone with same problem was advised to use "sudo pppoeconf" and it worked for me!! Now i can surf internet too, but after 5 minutes line drops and i couldn't restore it until next reboot. After rebooting same story 5mins of joy and 20 of rebooting:/  But now i know that i am going in good way:)

---

### Post by diepruis on 2007-09-09
> **tranzit said:**
> I can access my network, but i can't access internet. My internet connection requires a user name and password. In other forum someone with same problem was advised to use "sudo pppoeconf" and it worked for me!! Now i can surf internet too, but after 5 minutes line drops and i couldn't restore it until next reboot. After rebooting same story 5mins of joy and 20 of rebooting:/  But now i know that i am going in good way:)

If the network is managed by a router that also handles the connection to the internet, you might be able to configure the router in such a way that *it* dials into the network instead of the computers connected to it. Look for a section titled PPPoE or Account Settings, something like that, or call your ISP's tech support department.

I have no experience using PPPoE, so you might be better off asking for help in a new post.

---

### Post by tranzit on 2007-09-09
> you might be able to configure the router in such a way that *it* dials into the network instead of the computers connected to it

It would be really cool to do that, but i can't access my router's settings. I mean when trying to connect to [http://192.168.1.1/](http://192.168.1.1/) (i also tried every ip from ipconfig/all, tracert, downloading spec. software) my browser always return "The connection has timed out" error. So I think that the only way to change my router's settings would be to press "reset" button on my router, but I am afraid that after that I still couldn't access it's settings and my internet connection would be lost forever. 

> call your ISP's tech support department

I would better buy a new router/adapter...

---

### Post by diepruis on 2007-09-09
> **tranzit said:**
> It would be really cool to do that, but i can't access my router's settings. I mean when trying to connect to [http://192.168.1.1/](http://192.168.1.1/) (i also tried every ip from ipconfig/all, tracert, downloading spec. software) my browser always return "The connection has timed out" error. So I think that the only way to change my router's settings would be to press "reset" button on my router, but I am afraid that after that I still couldn't access it's settings and my internet connection would be lost forever. 

It's much easier getting the IP for the router. You could use "route" and check the Gateway column, or you could check the output of "dhclient wlan1". The IP reported as sending DHCPACKs or DCHPOFFERs will be the router's IP. For example, on my computer:

```

DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPACK from 10.0.0.2
bound to 10.0.0.227 -- renewal in 958130521 seconds.

```

So I know my router is 10.0.0.2

> **tranzit said:**
> I would better buy a new router/adapter...

You should check first, since I'm out of my depth here. It might be that your ISP requires the individual PC dialing routine.

---

### Post by tranzit on 2007-09-10
> It's much easier getting the IP for the router. You could use "route" and check the Gateway column, or you could check the output of "dhclient wlan1". The IP reported as sending DHCPACKs or DCHPOFFERs will be the router's IP. For example, on my computer

I was always tried to get my router's ip, but just from windows command prompt."dhclient wlan1" and  "route" gave same ip's like on windows and i still couldn't open my routers setting panel. I think that guy who configure my router's settings set some thing witch does not allow to connect to it's configuration's panel. So the only way is to press  reset button on my router (it sets all settings to default).

---

### Post by Dragonfi on 2007-09-10
Your guide is good ,It could save a lot of time itf I find it faster
    ,but now I'm rebooted the system and cannot get the connection working.
I have no idea what went wrong , It should start automatically becaues I edited the interfaces file,bit I cannot even get IP manually (there is some sort of connection, there is 61 signal strength and some recived /sended packages).
I go back and continue, maybe I missed a detail somewhere.

Ps: I'm new to Linux just started using it yesterday.

---

### Post by diepruis on 2007-09-11
> **tranzit said:**
> I was always tried to get my router's ip, but just from windows command prompt."dhclient wlan1" and  "route" gave same ip's like on windows and i still couldn't open my routers setting panel. I think that guy who configure my router's settings set some thing witch does not allow to connect to it's configuration's panel. So the only way is to press  reset button on my router (it sets all settings to default).

That's possible, but also risky. Have you tried connecting to it directly with an ethernet cable? It might have a security setting allowing only access with a physical connection...

---

### Post by diepruis on 2007-09-11
> **Dragonfi said:**
> Your guide is good ,It could save a lot of time itf I find it faster
    ,but now I'm rebooted the system and cannot get the connection working.
I have no idea what went wrong , It should start automatically becaues I edited the interfaces file,bit I cannot even get IP manually (there is some sort of connection, there is 61 signal strength and some recived /sended packages).
I go back and continue, maybe I missed a detail somewhere.

Ps: I'm new to Linux just started using it yesterday.

Would you mind posting /etc/network/interfaces, output from "sudo iwconfig" and "sudo ifup --f wlan0"?

---

### Post by deadlydeathcone on 2007-09-11
Thanks a LOT for the instructions, Austin; I was having the exact same issue as Dannyboy, and the latest cvs revision cleared everything up.

If anyone wants to save themselves some compiling, I posted 32-bit binaries of the drivers [here]("http://www.box.net/shared/gvggarfk4y").
Make sure to backup the old drivers first, then copy the rt2x00 folder from the archive to ```
/lib/modules/2.6.22-11-generic/ubuntu/wireless
```

Reboot, and enjoy some working wireless.

---

### Post by Dragonfi on 2007-09-11
Interfaces:
```

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp



iface wlan0 inet dhcp
wireless-essid Default
wireless-key s:admin

auto wlan0
wireless-essid Default
wireless-key s:admin

auto wlan1
iface wlan1 inet dhcp
pre-up ifconfig wlan1 up
pre-up iwconfig wlan1 essid Default
pre-up iwconfig wlan1 key s:admin
```
I hope I didn't mess somethong up ,because:
```
dragonfi@dragonfi-2:~$ sudo ifup --f wlan1
/etc/network/interfaces:23: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"

```
```
dragonfi@dragonfi-2:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     RT73 WLAN  
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```
And after ```
sudo ifconfig wlan1 up
sudo iwconfig wlan1 essid Default
sudo iwconfig wlan1 key admin
```
I get this:
> dragonfi@dragonfi-2:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     RT73 WLAN  ESSID:"Default"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:19:5B:B8:D5:C9   
          Bit Rate=24 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:6164-6D69-6E
          Link Quality=65/100  Signal level:-74 dBm  Noise level:-107 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

But still no access to router or internet.

---

### Post by Austin_KW on 2007-09-11
Dragonfi ,
The ifup command is telling you there is an error on line 23 in "/etc/network/interfaces". It will stop processing the config file after finding this error. Remove all the wlan0 configurations and the ath0 config (you do not have an atheros chipset). The "sudo ifup --f wlan1" should work once you fix this.

Also; Your manual config is working and you are associated to an access point. The encryption key is correct but you have not done the dhcp step. Add the command "sudo dhclient wlan1" to the end of your command sequence and you should have internet access. But you should not need to do this once you fix the interfaces file.

---

### Post by dannyboy79 on 2007-09-12
I have been really busy but any progress on getting the belkin f5d7050 working "out of the box" on Gutsy yet? Last I tried was Tribe 5 and it still DIDN'T work. I know how to get wireless to work, that's not the point. I will post the last debug info that they request here
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/135279](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/135279)
 and hopefully the dev's will make this work "out of the box", meaning no messing around with anything but click on wireless network, say join, enter security info and BOOM, you're connected. That's the definition of "out of the box". (IMHO)

---

### Post by Samuelito on 2007-09-12
Hi. I've followed this HOWTO and made the Belkin to work also at starting up Ubuntu. The thing is I installed Kdevelop this morning with aptitude and it gave me an error during installation as if I had no network access. I tried with dhclient command but it isn't able to obtain nothing when it does DHCPREQUEST. I also tried recompiling the module  and installing it again but the same thing happens. I have no error messages is just as if the router doesn't reply. Now I'm writing this post in windows with the same router and the same wireless adapter and it works correctly and with high network signal. Any ideas? Many thanks

---

### Post by Austin_KW on 2007-09-12
> **Samuelito said:**
> Hi. I've followed this HOWTO and made the Belkin to work also at starting up Ubuntu. The thing is I installed Kdevelop this morning with aptitude and it gave me an error during installation as if I had no network access. I tried with dhclient command but it isn't able to obtain nothing when it does DHCPREQUEST. I also tried recompiling the module  and installing it again but the same thing happens. I have no error messages is just as if the router doesn't reply. Now I'm writing this post in windows with the same router and the same wireless adapter and it works correctly and with high network signal. Any ideas? Many thanks

Are you associated with the network, does "sudo iwconfig" list an access pint Mac address?

Check that the wlan0 has not changed to wlan 1
And check the output of  "lsmod | grep usbcore" for any other wireless drivers trying to manage the belkin (i.e. Are you sure you have blacklisted all competing drivers because the belkin ID will map to at least 2 ralink chipsets and possible a prism chipset)

---

### Post by Samuelito on 2007-09-12
> **Austin_KW said:**
> Are you associated with the network, does "sudo iwconfig" list an access pint Mac address?

Check that the wlan0 has not changed to wlan 1
And check the output of  "lsmod | grep usbcore" for any other wireless drivers trying to manage the belkin (i.e. Are you sure you have blacklisted all competing drivers because the belkin ID will map to at least 2 ralink chipsets and possible a prism chipset)

sudo ifconfig returns eth1 which is ok.

with "lsmod | grep usbcore" it returns: 
usbcore   134280  5  rt73, zd1211rw, ehci_hcd, ohci_hcd

I blacklisted the drivers the manual suggested to so I suppose it's ok. Thanks for your quick reply.

---

### Post by Austin_KW on 2007-09-12
> **Samuelito said:**
> sudo ifconfig returns eth1 which is ok.

with "lsmod | grep usbcore" it returns: 
usbcore   134280  5  rt73, zd1211rw, ehci_hcd, ohci_hcd

I blacklisted the drivers the manual suggested to so I suppose it's ok. Thanks for your quick reply.

ifconfig will return all interfaces, iwconfig will return the wireless extensions for wireless interfaces. What does "sudo iwconfig eth1" output

Are you sure that you have an rt73 device, the output for lsmod above is also showing the zd1211rw driver, (for a belkin v4000). One of these needs to be blacklisted and if you need to blacklist the rt73 then you are in the wrong thread. 
Pop the usb dongle apart, use your fingernail in the seam and it will split apart without much force. Read the part number off the chip

---

### Post by Dragonfi on 2007-09-12
Finally I get my wireless adapter working.
Thanks for  diepruis for writing this guide ,it saved me from  lot of headache.
Thanks for noob12 to redirect me here , and for Austin_KW for the quick answer , I hope I will enjoy my time with Ubuntu. ( I am sure , i will with an active community like it ).

---

### Post by Samuelito on 2007-09-12
> **Austin_KW said:**
> ifconfig will return all interfaces, iwconfig will return the wireless extensions for wireless interfaces. What does "sudo iwconfig eth1" output

Are you sure that you have an rt73 device, the output for lsmod above is also showing the zd1211rw driver, (for a belkin v4000). One of these needs to be blacklisted and if you need to blacklist the rt73 then you are in the wrong thread. 
Pop the usb dongle apart, use your fingernail in the seam and it will split apart without much force. Read the part number off the chip

Ok. The chipset number is the zd1211b, so I suppose I'll have to find a different solution. But as I posted before, it worked ok with this howto just after I tried to install kdevelop. Do you think an easy solution would be to blacklist the zd1211 to see if it works again? 
If you have any good thread about the zd1211 please let me know. Many, many thanks.

---

### Post by Austin_KW on 2007-09-12
> **Samuelito said:**
> Ok. The chipset number is the zd1211b, so I suppose I'll have to find a different solution. But as I posted before, it worked ok with this howto just after I tried to install kdevelop. Do you think an easy solution would be to blacklist the zd1211 to see if it works again? 
If you have any good thread about the zd1211 please let me know. Many, many thanks.
To be clear, It did not work with this howto, What you had was a race condition where it may work if the zd1211 driver got in first. Installing more stuff may have altered your boot timing and the wrong driver tried to manage the device.

First thing you want to do is remove the dongle and add rt73 to the blacklist and then remove the running rt73 module with "sudo modprobe -rv rt73". You do not want the rt73 driver running now or on the next boot.
When you re-insert the dongle it should be running with the zd driver. I dont know the state of this driver, but once you know your chipset it is easy to search these forums for help.

---

### Post by brianna_allington on 2007-09-16
Hi,
What's the best way to go about setting up the wireless if I am going to use it in different places?  Also, is RutilTv the only graphical interface available as I am having trouble compiling it?
Thanks,

---

### Post by brianna_allington on 2007-09-16
Oh, and also, tremendous thanks on even being able to get on the internet with this at all.  There's no telling how many walls I've wanted to bang my head into.
Thanks very much,
brianna

---

### Post by diepruis on 2007-09-16
> **brianna_allington said:**
> Hi,
What's the best way to go about setting up the wireless if I am going to use it in different places?  Also, is RutilTv the only graphical interface available as I am having trouble compiling it?
Thanks,

You'd need some sort of program that supports multiple profiles and such. The crudest way would be to create a shell script for each location, but that's really a last resort.

As far as I know RutilT is the only program that works with the Realtek drivers. Since their interfaces are somewhat non-standard it seems that programs like network-manager don't work with them.

You might try something like *kwlan*, I remember having some success using that with my RT61 card.

Alternatively, I could try and help you install RutilT, or just compile a copy and send you the package.

> **brianna_allington said:**
> Oh, and also, tremendous thanks on even being able to get on the internet with this at all.  There's no telling how many walls I've wanted to bang my head into.
Thanks very much,
brianna

You're very welcome =D

---

### Post by diepruis on 2007-09-16
> **brianna_allington said:**
> Also, is RutilTv the only graphical interface available as I am having trouble compiling it?

RutilT compiles beautifully on my install. What are you having trouble with?

---

### Post by Anthony on 2007-09-18
Thanks very much for the instructions. Worked like a charm with my Belkin Wireless G USB Network Adapter

---

### Post by tarntow on 2007-09-20
Thank you. Very happy I have finally found the right solution. Nice one.

---

### Post by dr_hash on 2007-09-20
thank you very much! i felt myself in trouble after upgrading to feisty but you solved my problem.

---

### Post by titaniumlou on 2007-09-22
In case anyone needs it, here is what I placed in my /etc/network/interfaces file in order to get WPA working automatically after a restart:

```

auto ra0
iface ra0 inet dhcp
pre-up ifconfig ra0 up
pre-up iwconfig ra0 essid "YOUR_ESSID"
pre-up iwconfig ra0 mode managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="WPA_KEY"

```

---

### Post by Austin_KW on 2007-09-22
> **titaniumlou said:**
> In case anyone needs it, here is what I placed in my /etc/network/interfaces file in order to get WPA working automatically after a restart:

```

auto ra0
iface ra0 inet dhcp
pre-up ifconfig ra0 up
pre-up iwconfig ra0 essid "YOUR_ESSID"
pre-up iwconfig ra0 mode managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="WPA_KEY"

```

Wrong thread? That is the config (ra0) for a rt2500 or rt61 chipset?

---

### Post by brianna_allington on 2007-09-26
I followed most of the instructions in this how-to and now my wireless connects to whatever is available most of the time and I don't even have to type anything in terminal.  This is freakin' awesome!  Just out of curiosity, how does it know to do this?  The only thing in the interfaces file is:
auto wlan0
iface wlan0 inet dhcp

Does this tell it to do that?
Thanks.

---

### Post by Austin_KW on 2007-09-26
> **brianna_allington said:**
> I followed most of the instructions in this how-to and now my wireless connects to whatever is available most of the time and I don't even have to type anything in terminal.  This is freakin' awesome!  Just out of curiosity, how does it know to do this?  The only thing in the interfaces file is:
auto wlan0
iface wlan0 inet dhcp

Does this tell it to do that?
Thanks.

If you do not tell it what network (SSID) to connect to it will connect to ANY available network, it may even fallback to ANY if your network ssid is not available. The "dhcp" parameter tells it to automatically configure the IP address, routing and dns.

Note; This means that your network is not secured, and that anyone can connect to your network or snoop your traffic over the air. Once you have got it working this far you should follow the rest of the tutorial and setup WPA-PSK encryption to keep away the trolls.

---

### Post by brianna_allington on 2007-09-26
Well, I usually just run around to random coffee shops and use whatever's available, so unfortunately I don't think I can use WPA.  However, I don't have a clue how WPA works of anything so I don't really know if I can use it.  Is it something that the network administrator would have to tell you or is it something that you assign yourself?
thnks,
brianna

---

### Post by diepruis on 2007-09-27
Just a quick note to everyone following this thread. I recently upgraded my network to WPA2 and had to upgrade configuration files for an RT61 and an RT73 device. Instead of doing that, I installed RutilT instead, which is much easier. It's also convenient for people who use multiple networks, as it offers profiles. I'd recommend it to anyone using a laptop or anyone too lazy to fiddle with the arcane way RT chipsets handle WPA.

---

### Post by cyberwiz on 2007-09-27
Followed the instructions and my WUSB54GC adapter works fine with the rt73 module.
Thanks a lot!!!
:)

---

### Post by CorneliusBear on 2007-09-27
Hey Everyone,

I've followed the instructions that diepruis posted.  My setup is connecting to a router via an RT73 based device (Linksys WUSB54GC), where the network is secured wia WPA.  But for some reason, even though the driver loads fine, and I can detect my network, I can never get dhclient to work.  I should mention that I used to use ndiswrapper along with wpasupplicant, and connected on most occasions (though it never lasted longer than around 30 minutes).  So the adapter does work.  I'm using the latest CVS source (rt73-cvs-2007091723).

Here's the pertinent info:

ifconfig -a
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15457 (15.0 KiB)  TX bytes:15457 (15.0 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:18:39:12:8F:BD  
          inet6 addr: fe80::218:39ff:fe12:8fbd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1943 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1062628 (1.0 MiB)  TX bytes:17892 (17.4 KiB)

wlan0:ava Link encap:Ethernet  HWaddr 00:18:39:12:8F:BD  
          inet addr:169.254.6.174  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1


```

iwconfig wlan0:
```
wlan0     RT73 WLAN  ESSID:"<myssid>"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0F:66:E2:78:5B   
          Bit Rate=12 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=43/100  Signal level:-76 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

cat /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
	pre-up ifconfig wlan0 up
	pre-up iwpriv wlan0 set AuthMode=WPAPSK
	pre-up iwpriv wlan0 set EncrypType=TKIP
	pre-up iwpriv wlan0 set WPAPSK=<myhexkey>
	pre-up iwpriv wlan0 set SSID="<myssid>"
	pre-up iwpriv wlan0 set NetworkType=Infra

```

The entries below [HTML]<b>iface wlan0 inet dhcp</b>[/HTML] in the interfaces file all begin with tabs, as it appears in the first post.  I've also tried having the WPAPSK key enclosed in double quotes, no joy.  Is this o.k?  It seems to me that I can't get the encryption working, from what iwconfig and ifconfig tell me; the device comes up fine.  Is my syntax using iwpriv o.k?  I would greatly appreciate any help you guys could provide.  I'll try recompiling the driver with debug, seeing if that gives me any leads.  Thanks in advance,

CB.

---

### Post by diepruis on 2007-09-28
> **CorneliusBear said:**
> 
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
	pre-up ifconfig wlan0 up
	pre-up iwpriv wlan0 set AuthMode=WPAPSK
	pre-up iwpriv wlan0 set EncrypType=TKIP
	pre-up iwpriv wlan0 set WPAPSK=<myhexkey>
	pre-up iwpriv wlan0 set SSID="<myssid>"
	pre-up iwpriv wlan0 set NetworkType=Infra

```


The README file in the source tarball suggests the following order, which is all I can see that might be wrong there:
[LIST=1]
[*]iwconfig wlan0 mode managed
[*]ifconfig wlan0 up
[*]iwconfig wlan0 essid <ESSID>
[*]iwpriv wlan0 set AuthMode=WPAPSK
[*]iwpriv wlan0 set WPAPSK=<KEY>
[*]iwpriv wlan0 set EncrypType=TKIP
[*]dchlient wlan0
[/LIST]
Note that for WPA2, you need to set AuthMode to WPA2PSK and EncrypType to AES. Some people have also remarked that they need to set the ESSID using iwpriv **and** iwconfig. I've been unable to get WPA2 to work in my setup, and I have an rt61 and an rt73 card. The only configuration option that worked for me was RutilT.

---

### Post by Austin_KW on 2007-09-28
CorneliusBear, 
You mentioned that you were using ndiswrapper, have you now blacklisted/removed ndiswrapper. Connection problems are often due to interfering drivers so check the output of "lsmod | grep usbcore"

---

### Post by CorneliusBear on 2007-09-28
Hey all,

Austin_KW: I've edited /etc/modules so that ndiswrapper does not load.  lsmod indicates that only the rt73 module is currently loaded, so I don't think it's a conflict with ndiswrapper. 

diepruis: I'll try out your advice below later tonight.  

I'm about to package up a comprehensive post containing oodles of debug info to the appropriate forum on serialmonkey.  If anything surprising results from that I'll post here.  Thanks,

CB.

---

### Post by Bonder5678 on 2007-09-30
I'm having problems compiling the module.  When I run "sudo make" I get the following output:
```
make[1]: Entering directory `/lib/modules/2.6.20-16-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.20-16-386/build'
rt73.ko failed to build!
make: *** [module] Error 1
```
I've tried everything I can think of.  Anyone have any ideas?

---

### Post by CorneliusBear on 2007-09-30
My device now works.  In a final attempt to get this device to work, I made sure to kill all the existing dhclient processes.  I can't believe that was the problem!  Aargh!  Thanks for your help diepruis & Austin_KW.  In case it could be a useful reference to others, I'll post my /etc/network/interfaces file.  Once the driver loads o.k, all my configuration is done there, no need to mess around on the command line, no need for RutilT.

/etc/network/interfaces:
```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid "myssid"
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK=<hexkey>

```

---

### Post by roachk71 on 2007-09-30
Haven't tested it with WPA yet, but it works like a charm using 104-bit WEP on my computer's built-in USB wireless!

Thanks a bunch; I'm really a happy camper now! :guitar:

(Somewhat an) Update: The Serialmonkey driver works much better than the factory-shipped driver did in Vista! That driver had problems simply connecting!

---

### Post by diepruis on 2007-10-01
> **Bonder5678 said:**
> I'm having problems compiling the module.  When I run "sudo make" I get the following output:
```
make[1]: Entering directory `/lib/modules/2.6.20-16-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.20-16-386/build'
rt73.ko failed to build!
make: *** [module] Error 1
```
I've tried everything I can think of.  Anyone have any ideas?

What's the output of

```

file /lib/modules/2.6.20-16-386/build

```

---

### Post by pshchelo on 2007-10-01
Finally I got it working!

I had a very strange problem with network being unavailable with any encryption turned on, even when router was recognizing me and giving proper IP - posted on this already here.

What I did today was installing Ralink's own drivers, not the serialmonkey ones, and then just editing corresponding .dat file, without any iwconfig/iwpriv usage and /etc/network/interfaces editing at all (I'm using DHCP), mainly following [_this_]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73") guide.

---

### Post by Alfred_McGee on 2007-10-01
After following this howto, my usb wifi card is recognized with the lsusb command and successfully executes **iwlist scanning** to find lots of networks. I haven't yet used it for connecting to the internet, though, because my computer's internal wifi card is more powerful and I haven't yet figured out how to disable it. But my question is really te following:
When trying to run Kismet through my usb adapter, I get the following error message: 

[I]FATAL: Unknown capture source type 'rt73' in source 'rt73,wlan1,default'
[/I]

So the problem seems to be that I don't know what to put in my kismet.conf file as the driver I'm using to run this card.

This command  **dmesg | grep rt73**

returns this:   **rt73 driver version - 1.0.3.6 CVS**

From the directory  *usr/src*
this command **ls -d rt73***

returns this: rt73-cvs-2007091519

Installing and compiling Kismet was not easy, so I'd love some help getting past this last hurdle!

---

### Post by Bonder5678 on 2007-10-01
> **diepruis said:**
> What's the output of

```

file /lib/modules/2.6.20-16-386/build

```
My output is:
```
/lib/modules/2.6.20-16-386/build: directory
```
When I first ran make, it gave me an error saying that the /build directory didn't exist, so I used mkdir to create it (i.e. the directory is empty).  I have the feeling that I'm missing some packages I need for make to work properly.  I don't know how to find what, if any, packages I'm missing.  I did run
```
sudo aptitude install build-essential linux-headers-`uname -r`
```
before trying to use make as per step 6 in the OP, but perhaps I have to get the packages I need somewhere else.

---

### Post by diepruis on 2007-10-02
> **Bonder5678 said:**
> My output is:
```
/lib/modules/2.6.20-16-386/build: directory
```
When I first ran make, it gave me an error saying that the /build directory didn't exist, so I used mkdir to create it (i.e. the directory is empty).  I have the feeling that I'm missing some packages I need for make to work properly.  I don't know how to find what, if any, packages I'm missing.  I did run
```
sudo aptitude install build-essential linux-headers-`uname -r`
```
before trying to use make as per step 6 in the OP, but perhaps I have to get the packages I need somewhere else.

That directory should be a "symlink" to the source code for the kernel you're running, like so:

```

file /lib/modules/2.6.20-16-generic/build
/lib/modules/2.6.20-16-generic/build: symbolic link to `/usr/src/linux-headers-2.6.20-16-generic'

```

I think this might be caused by not having your kernel headers installed. Remove the directory,

```

sudo rmdir /lib/modules/2.6.20-16-386/build

```

Then please post output from,

```

sudo aptitude install linux-headers-`uname -r`

```

---

### Post by pshchelo on 2007-10-02
> **pshchelo said:**
> Finally I got it working!
Oopsey, false positive :(
After the restart it's once again the same "unreachable network" weirdness.. But it definitely worked yesterday :confused:
now I'm really-really confused

---

### Post by Bonder5678 on 2007-10-02
> **diepruis said:**
> I think this might be caused by not having your kernel headers installed. Remove the directory,

```

sudo rmdir /lib/modules/2.6.20-16-386/build

```

Then please post output from,

```

sudo aptitude install linux-headers-`uname -r`

```
Ok.  The output is:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
```
So, this is why I'm confused, I believe I have the headers installed, but something is clearly not right.  Also, I noticed that after running the above command, it did not create the /lib/modules/2.6.20-16-386/build directory.  Could it be that I do not have the proper repositories enabled?  Anyway, thanks for the continuing help.

---

### Post by dannyboy79 on 2007-10-02
> **pshchelo said:**
> Oopsey, false positive :(
After the restart it's once again the same "unreachable network" weirdness.. But it definitely worked yesterday :confused:
now I'm really-really confused

and did you do the update of the /etc/network/interfaces file to include whatever interface your wifi card (wlan0 or wlan1). if not, you have to do the iwconfig part at the end of the guide all over again which will bring up the interface, set the ssid, set any security if network is secure, then request a ip from the dhcp server.

you can find it out by issuing: sudo iwconfig or ifconfig

also, please post the output of the following commands:

cat /etc/modprobe.d/blacklist | grep rt*

AND

lsmod | grep rt*

NOTE: I still can't believe that this stupid hardware is NOT compatiable with Gutsy Alpha 5 out of the box and that we still need to compile from source to get this to work!!!!

---

### Post by Bonder5678 on 2007-10-02
I managed to fix my problem by uninstalling and then reinstalling the headers.  Thanks for all the help.

---

### Post by diepruis on 2007-10-03
> **dannyboy79 said:**
> and did you do the update of the /etc/network/interfaces file to include whatever interface your wifi card (wlan0 or wlan1). if not, you have to do the iwconfig part at the end of the guide all over again which will bring up the interface, set the ssid, set any security if network is secure, then request a ip from the dhcp server.

He used the RaLink drivers, which don't require editing /etc/network/interfaces. That said, did you try just issuing "sudo dhclient rausb0" (or whatever the interface name is).

> **dannyboy79 said:**
> NOTE: I still can't believe that this stupid hardware is NOT compatiable with Gutsy Alpha 5 out of the box and that we still need to compile from source to get this to work!!!!

Neither can I. Does anyone know what the reason for this is?

---

### Post by Austin_KW on 2007-10-03
> **diepruis said:**
> ...
Neither can I. Does anyone know what the reason for this is?

Seems to be a moving target. The beta drivers are still being developed but so is the 802.11 stack. The drivers do not appear to stabilize before they are modified again. Last I checked, you cannot now even build the the beta CVS in gutsy so we may well be stuck with the legacy drivers for gutsy. No one, but the most expert users are going to track kernel and driver changes in the git environment.


I should mention that the beta drivers worked for me for rt73usb, but not for rt2500 so it may be a bit hit and miss in gutsy, depending on configurations, hardware etc?

---

### Post by dannyboy79 on 2007-10-03
i was able to build the cvs daily of rt73 from the serialmonkey website on gutsy tribe 4. I downloaded it awhile ago and keep using that to get my wireless working within ubuntu when it doesn't work out of the box, are you saying that if I tried to download the cvs daily build of rt73 again, it won't compile in gutsy? Glad I have this old copy then if that's true.

---

### Post by Austin_KW on 2007-10-03
> **dannyboy79 said:**
> i was able to build the cvs daily of rt73 from the serialmonkey website on gutsy tribe 4. I downloaded it awhile ago and keep using that to get my wireless working within ubuntu when it doesn't work out of the box, are you saying that if I tried to download the cvs daily build of rt73 again, it won't compile in gutsy? Glad I have this old copy then if that's true.

Yes, I think that is the case. 
Do not delete that snapshot ;)  I also have working tars (for my rt73) but my rt2500 has problems so I was trying to use a later tarfile. It is just annoying that we look like we are going to get another round of "rtxxx does not work" on 7.10. Ok, for those of us who have been using the legacy drivers and understand modprobe and blacklisting but a nightmare for new users.

---

### Post by pshchelo on 2007-10-03
> **diepruis said:**
> That said, did you try just issuing "sudo dhclient rausb0" (or whatever the interface name is).

Ok, it looks like I've found more on the origin of the problem.

Once again the problem description: when I'm using any wireless encryption (WEP, WPA, WPA2) my traffic is jammed in such a way that although my adapter connects to WLAN-router and gets an IP from it (which is surely only after successful authentication), the network is unreachable - it is very strange and funny to see dhclient output saying  that it obtained an IP from 192.168.0.1 and just couple of seconds later "ping 192.168.0.1" outputing "Host unreachable"...

I've tried it many times with serialmonkey's and RaLInk drivers, but with no success. Then I decided to make it once again and this time clean, searched and removed all rt73.ko, bin and dat files from system, compiled and installed RaLink drivers and hop-la - it worked. But the next day it was all other again.

Now I've found the cause (but not the reason) and I have a partial solution.

I have dual-boot computer with WinXP, and this bug appears (at least with RaLink drivers) only when my last previously booted system was Windows. And the solution is simple (but not comfortable) - just shut this network interface down, replug the WLAN-adapter and start the interface again. That's all.

I have no idea on why is it so. How does Windows mess with USB (or something else) in such a way that after that in Linux the networking glitches? And how could this bug be resolved without repluging? Any thoughts?

---

### Post by diepruis on 2007-10-04
> **pshchelo said:**
> I have no idea on why is it so. How does Windows mess with USB (or something else) in such a way that after that in Linux the networking glitches? And how could this bug be resolved without repluging? Any thoughts?

It certainly is strange, but I've seen some previous complaints on message boards and mailing lists concerning this issue. Most people put it down to Windows leaving the device in an anomalous state. I don't know much about the actual hardware, is it possible that the EEPROMs on the cards store some state between reboots? If that's the case then it might be as simple as resetting these to legal values, though I wouldn't know how to actually go about doing this.

---

### Post by diepruis on 2007-10-04
> **Austin_KW said:**
> Seems to be a moving target. The beta drivers are still being developed but so is the 802.11 stack. The drivers do not appear to stabilize before they are modified again. Last I checked, you cannot now even build the the beta CVS in gutsy so we may well be stuck with the legacy drivers for gutsy. No one, but the most expert users are going to track kernel and driver changes in the git environment.

Okay, what you're saying makes sense, at least for rt73. But I've been using the rt61 (legacy) beta since forever and it's been working fine. The rt2x00 tree, on the other hand, is frequently broken completely and only half-works at the best of times. Why would the Ubuntu devs choose a *more* unstable driver if that's their concern?

---

### Post by Austin_KW on 2007-10-04
> **diepruis said:**
> Okay, what you're saying makes sense, at least for rt73. But I've been using the rt61 (legacy) beta since forever and it's been working fine. The rt2x00 tree, on the other hand, is frequently broken completely and only half-works at the best of times. Why would the Ubuntu devs choose a *more* unstable driver if that's their concern?

I am guessing, but it must be for network-manager & wpa suppliciant support. 
Once the beta drivers ***work*** then no more manual or interface file configuration, just click on the network and you are prompted for the password. 
Of course shipping with broken drivers causes more problems than shipping with no drivers, just look at the length of this thread ;)

Also on that warm start from windows issue, I mentioned it somewhere in this thread for the legacy driver, but I cannot remember if it is fixed in the beta driver. I think it might be. Of course most people cannot get a beta driver due to the complicated build process.

---

### Post by diepruis on 2007-10-04
> **Austin_KW said:**
> I am guessing, but it must be for network-manager & wpa suppliciant support. 

Yeah, I wouldn't be surprised if that's the case.

> **Austin_KW said:**
> Once the beta drivers ***work*** then no more manual or interface file configuration, just click on the network and you are prompted for the password. 
Of course shipping with broken drivers causes more problems than shipping with no drivers, just look at the length of this thread ;)

Also true.

---

### Post by marmundo on 2007-10-04
Hello,

I follow the above steps and a take a IP from dhclient, but I can't take a internet conection.
Follow the results of my commands:

marcelo@manguaba:~$ ifconfig -a 

wlan0      Encapsulamento do Link: Ethernet  Endereço de HW 00:0E:2E:DA:D6:F5  
          inet end.: 10.241.153.2  Bcast:10.255.255.255  Masc:255.255.255.252
          endereço inet6: fe80::20e:2eff:feda:d6f5/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:11387 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:174 erros:0 descartados:18 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:808460 (789.5 KiB) TX bytes:19078 (18.6 KiB)

marcelo@manguaba:~$ ping 10.0.0.1
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
From 169.254.11.27 icmp_seq=1 Destination Host Unreachable
From 169.254.11.27 icmp_seq=2 Destination Host Unreachable
From 169.254.11.27 icmp_seq=3 Destination Host Unreachable
From 169.254.11.27 icmp_seq=4 Destination Host Unreachable
From 169.254.11.27 icmp_seq=5 Destination Host Unreachable
From 169.254.11.27 icmp_seq=6 Destination Host Unreachable
 
--- 10.0.0.1 ping statistics ---
9 packets transmitted, 0 received, +6 errors, 100% packet loss, time 8037ms
, pipe 3
marcelo@manguaba:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

What's wrong? What have I do to fix it?
Thanks

---

### Post by Austin_KW on 2007-10-04
Is this a dhcp address? 
The mask says the subnet range is 10.241.153.1 to 10.241.153.3
What is the output of
```

ping -c 3 10.241.153.1
cat /etc/resolv.conf
route -n
cat /etc/network/interfaces    

```

---

### Post by dannyboy79 on 2007-10-11
This is the gzipped tarball of the rt73 cvs daily build I had downloaded awhile ago. It DOES successfully build in Gutsy as of 10-10-07. It makes my [COLOR=black]Belkin[/COLOR] F5D7050 with the rt2571wf wifi chip inside if you split it open. Just use this tarball and build per page 1 guide and you'll be good to go!!

---

### Post by Mikey_S on 2007-10-14
Hey folks,
First of all, I'm a Linux noob, although I'm not that clueless with computers in general.

I own an Edimax EW-7318Ug Wireless adapter. After a fresh install of Ubuntu feisty 7.04 (64 bit version) I downloaded the latest serialmonkey driver from my other computer, and followed all your instructions, after a while I was able to get it working (with WPA-PSK and everything) which was quite an uplifting event :)

After a while I've bumped into two more problems:
1. For some odd reason, while browsing, it takes a long time to resolve the domain name's ip which really slows things up.

2. I'm experiencing random disconnects, I can't browse, nor connect to the router interface (on a LAN).
I tried turning my wlan off and on (sudo ifconfig wlan1 down/up) still won't do it... i've also tried restarting the network interface: "sudo /etc/init.d/networking restart" that doesnt work as well...
Only a reboot can get everything working again.

any suggestions?

P.S
I really appreciate your help, it is certainly a life saver for noobs like me :)

Thanks,
Mikey

---

### Post by dannyboy79 on 2007-10-14
you could try to hard code some DNS servers within the DNS section within the Network Admin Settings Box, if you use a home router, some times they are not actually very good at forwarding DNS requests

---

### Post by Mikey_S on 2007-10-14
Man, 
not sure what you're talking about... told you i'm just a noob :)

---

### Post by diepruis on 2007-10-15
> **Mikey_S said:**
> After a while I've bumped into two more problems:
1. For some odd reason, while browsing, it takes a long time to resolve the domain name's ip which really slows things up.

There's a couple of things you can do here, I doubt the RT73 is to blame. You can, like dannyboy said, use a faster DNS server. See this page: [http://www.opendns.com/](http://www.opendns.com/)

Do you have this problem on Windows too?

> **Mikey_S said:**
> 2. I'm experiencing random disconnects, I can't browse, nor connect to the router interface (on a LAN).
I tried turning my wlan off and on (sudo ifconfig wlan1 down/up) still won't do it... i've also tried restarting the network interface: "sudo /etc/init.d/networking restart" that doesnt work as well...
Only a reboot can get everything working again.

any suggestions?

This seems to be a problem with some of the RT73 devices, you're better off posting on the serialmonkey website as the problem is most likely in the driver itself... or perhaps even in the firmware.

What you can do is try to improve the signal quality between the RT73 and the AP. Search around on the Internet, there's plenty guides on doing that.

> **Mikey_S said:**
> P.S
I really appreciate your help, it is certainly a life saver for noobs like me :)

^_^

---

### Post by Austin_KW on 2007-10-15
> **Mikey_S said:**
> Hey folks,
First of all, I'm a Linux noob, although I'm not that clueless with computers in general.

I own an Edimax EW-7318Ug Wireless adapter. After a fresh install of Ubuntu feisty 7.04 (64 bit version) I downloaded the latest serialmonkey driver from my other computer, and followed all your instructions, after a while I was able to get it working (with WPA-PSK and everything) which was quite an uplifting event :)

After a while I've bumped into two more problems:
1. For some odd reason, while browsing, it takes a long time to resolve the domain name's ip which really slows things up.

2. I'm experiencing random disconnects, I can't browse, nor connect to the router interface (on a LAN).
I tried turning my wlan off and on (sudo ifconfig wlan1 down/up) still won't do it... i've also tried restarting the network interface: "sudo /etc/init.d/networking restart" that doesnt work as well...
Only a reboot can get everything working again.

any suggestions?

P.S
I really appreciate your help, it is certainly a life saver for noobs like me :)

Thanks,
Mikey

As suggested switching to the opendns servers may help. But if this is not happening when using a wired connection it may be due to a weak signal or RF interference.

Check that you have blacklisted all conflicting drivers what is the output of 
```
lsmod | grep usbcore
```

There is a number of things you can do to improve your wireless signal, notably changing channel to (1,6 or 11) and repositioning you router. 

Rather than reboot, try removing and reinserting the adapter and running ```
sudo ifup --f wlan1
```

---

### Post by Mikey_S on 2007-10-15
Thanks for the quick reply:
Ok couple of things, about the poor wireless signal: I'm comparing this to browsing in XP and Vista on the same computer, it seems just fine. 
Note that I also configured the DNS servers manually in that dhclient file, still won't work...

about the conflict between devices, i'll try the command and give you the result as soon as ill get back home.

Thanks again!

---

### Post by The Joe on 2007-10-15
Great guide thanks.
I'm running a Belkin G+ MIMO Router, when I run

sudo dhclient wlan0

I get the following output (I've had to type it out because it's a laptop I'm trying to get online)
There is already a pid file /var/run/dhclient.pid with pid 9239
Some copyright info crap...

Listening on LPF/wlan0/00:lc:df:08:18:a6
Repeated top line
Sending on socket/fallback

DCHPDISCOVER on wlan- to 255.255.255.255 port 67 interval 4
Repeated 3 more times with different interval numbers

No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Any help would be appreciated, there is no WEP/WAP key.

---

### Post by Austin_KW on 2007-10-15
> **The Joe said:**
> Great guide thanks.
I'm running a Belkin G+ MIMO Router, when I run

sudo dhclient wlan0

I get the following output (I've had to type it out because it's a laptop I'm trying to get online)
There is already a pid file /var/run/dhclient.pid with pid 9239
Some copyright info crap...

Listening on LPF/wlan0/00:lc:df:08:18:a6
Repeated top line
Sending on socket/fallback

DCHPDISCOVER on wlan- to 255.255.255.255 port 67 interval 4
Repeated 3 more times with different interval numbers

No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Any help would be appreciated, there is no WEP/WAP key.

What is the output from iwconfig after this; is it associated i.e. does it show an ssid and an ap mac address? 
If not then what other commands are you running before the dhclient or what is the contents of /etc/network/interfaces

---

### Post by The Joe on 2007-10-15
Actually it's ok now for some reason, I connected fine and I'm  on Ubuntu online for the first time since last November! Feels gooooood!

---

### Post by sefs on 2007-10-19
Is anyone expericing the below prob with gutsy and these drivers.

When I plug the usb adapter into an upgrad to gutsy the system immediately halts/hangs and the caps lock and scroll lock on the keyboard blinks repeateadly off and on in unison.

The only way to get back control is to pull the dongle out and do a hard reboot.

UPDATE: some guy over at the serial monkey forums has figued that this only happens when you use wpa and aes, [http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=26874#26874](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=26874#26874),  is it only me and him that is having this problem with serial monkey drivers on gutsy?

---

### Post by ~cyrus~ on 2007-10-19
Have just upgraded to 7.10 from 7.04, where rt73 was working fine with my Dlink usb adapter, showing wlan1

After the upgrade I compiled again as per instructions here, and notice that my wireless is now wlan0

Configured the network interface file as wlan0 and am connecting, but cannot access the internet.

I am writing this from my laptop and cannot paste any terminal output as I would have to type the entire message, but it seems to be up. iwconfig is showing up OK, have blacklisted all the other drivers,  interface file seems OK, and am totally perplexed as to why I'm not connecting. I have done this before in 7.04 with a kernel upgrade and all went off smoothly on reboot then.

I have at different stages compiled 3 different rt73 drivers. One working one that I had, one that was available from this forum, and one that I had downloaded and stored a few days ago. All seem to work, and I can't see anything abnormal. Just can't get an internet connection.

Appreciate some help.

Regards,

cyrus

---

### Post by sefs on 2007-10-19
cyrus What authenticaton / encrtytion are you using ? wpa? aes?

---

### Post by ~cyrus~ on 2007-10-19
wep

I have also tried sudo ifconfig wlan0 down and then configured it again. I seem to connect to my router but cannot access the internet.

---

### Post by ~cyrus~ on 2007-10-20
I have tried to systematically follow this whole thread in case I had missed out on something, but just cannot find the answer.

My latest discovery was that I can ssh into a server, so that seems to work.

I have tried network tools and I am successful in pinging a site.

My speed and signal strength are showing up well.

Has anyone got this working after upgrading to gutsy?

Appreciate some advice.

cyrus

---

### Post by pshchelo on 2007-10-21
Hi everybody,
just 10 minutes ago I made a clean install of Gutsy and guess what - my Logilink wlan dongle based on RT73 "just works" now!
Network Manager shows list of SSID's, when connecting to my home w-router with WPA2-AES just prompts for passphrase and that's all! I still haven't tried though the issue I described earlier (with weird network unavailability with the previously booted system being Windows, solved by repluging the dongle), but anyway that is simply great and relieving :mrgreen:

---

### Post by diepruis on 2007-10-21
> **sefs said:**
> Is anyone expericing the below prob with gutsy and these drivers.

When I plug the usb adapter into an upgrad to gutsy the system immediately halts/hangs and the caps lock and scroll lock on the keyboard blinks repeateadly off and on in unison.

The only way to get back control is to pull the dongle out and do a hard reboot.

UPDATE: some guy over at the serial monkey forums has figued that this only happens when you use wpa and aes, [http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=26874#26874](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=26874#26874),  is it only me and him that is having this problem with serial monkey drivers on gutsy?

My guess is that the upgrade overwrote your blacklist file. Please check if the appropriate drivers are still blacklisted. Can you maybe try to get some dmesg output as well?

---

### Post by diepruis on 2007-10-21
> **~cyrus~ said:**
> I have tried to systematically follow this whole thread in case I had missed out on something, but just cannot find the answer.

My latest discovery was that I can ssh into a server, so that seems to work.

I have tried network tools and I am successful in pinging a site.

My speed and signal strength are showing up well.

Has anyone got this working after upgrading to gutsy?

Appreciate some advice.

cyrus

Mmmm... could you please paste output from those pings? Did you try using domain names as well as IPs?

---

### Post by diepruis on 2007-10-21
> **pshchelo said:**
> Hi everybody,
just 10 minutes ago I made a clean install of Gutsy and guess what - my Logilink wlan dongle based on RT73 "just works" now!
Network Manager shows list of SSID's, when connecting to my home w-router with WPA2-AES just prompts for passphrase and that's all! I still haven't tried though the issue I described earlier (with weird network unavailability with the previously booted system being Windows, solved by repluging the dongle), but anyway that is simply great and relieving :mrgreen:

Sweet! Looks like some progress is being made on rt2x00.

---

### Post by ~cyrus~ on 2007-10-21
Thanks for the response diepruis

I can also now confirm that rt73 works out of the box with my dlink dwl-g122 wireless adapter. 

Figured this out when I tried the livecd that I burnt that had network manager. Same thing...couldn't connect with my browser...disabled ipv6...and I can now browse with firefox.

What I can't do is get updates, or... wget, irc, and pidgin for my msn. Just not connecting. It does with a live 7.04 cd though, so something is not right for me, at least, in 7.10 with regard to other connections except the browser. Even tried the live 7.10 cd and couldn't browse till i turned off ipv6 in firefox.

---

### Post by diepruis on 2007-10-22
> **~cyrus~ said:**
> Thanks for the response diepruis

I can also now confirm that rt73 works out of the box with my dlink dwl-g122 wireless adapter. 

Figured this out when I tried the livecd that I burnt that had network manager. Same thing...couldn't connect with my browser...disabled ipv6...and I can now browse with firefox.

What I can't do is get updates, or... wget, irc, and pidgin for my msn. Just not connecting. It does with a live 7.04 cd though, so something is not right for me, at least, in 7.10 with regard to other connections except the browser. Even tried the live 7.10 cd and couldn't browse till i turned off ipv6 in firefox.

Try adding the following line to /etc/modprobe.d/blacklist

```

blacklist ipv6

```

And reboot.

---

### Post by dannyboy79 on 2007-10-22
I really don't want to uninstall my rt73 driver and unblacklist the rt drivers to see if my Belkin F5D7050 (the one with the rt2571wf chip in it) works out of the box. Has anyone found that this adapter works out of the box with the latest Gutsy release?? I suppose I can try it but would rather not.

---

### Post by dgel on 2007-10-22
Well, I have a bit of a mixed message here.

I did a fresh install of gutsy, as the updater broke my feisty install.
 Once booted, i decided to try and get wireless up and running first. So, in the network manager, i selected the wireless interface, input the ssid and password etc. and miraculously, i had an internet connection.
 So, next I decided to get the desktop effects working. I downloaded and installed the compizconfig-manager through synaptic, and fiddled around a bit.
 I decided to look something up on the internet and apparently, my connection had gone. What's more, there wasn't even a wireless connection showing in the network manager. 

Any ideas to get it working again? should I simply follow this guide, although it had worked just an hour ago?

---

### Post by diepruis on 2007-10-22
> **Na-Fiann said:**
> Well, I have a bit of a mixed message here.

I did a fresh install of gutsy, as the updater broke my feisty install.
 Once booted, i decided to try and get wireless up and running first. So, in the network manager, i selected the wireless interface, input the ssid and password etc. and miraculously, i had an internet connection.
 So, next I decided to get the desktop effects working. I downloaded and installed the compizconfig-manager through synaptic, and fiddled around a bit.
 I decided to look something up on the internet and apparently, my connection had gone. What's more, there wasn't even a wireless connection showing in the network manager. 

Any ideas to get it working again? should I simply follow this guide, although it had worked just an hour ago?

You might want to try blacklisting ipv6 first. I've heard several reports of problems with it in Gutsy.

---

### Post by Austin_KW on 2007-10-22
> **Na-Fiann said:**
> Well, I have a bit of a mixed message here.

I did a fresh install of gutsy, as the updater broke my feisty install.
 Once booted, i decided to try and get wireless up and running first. So, in the network manager, i selected the wireless interface, input the ssid and password etc. and miraculously, i had an internet connection.
 So, next I decided to get the desktop effects working. I downloaded and installed the compizconfig-manager through synaptic, and fiddled around a bit.
 I decided to look something up on the internet and apparently, my connection had gone. What's more, there wasn't even a wireless connection showing in the network manager. 

Any ideas to get it working again? should I simply follow this guide, although it had worked just an hour ago?

Check what drivers are loaded "lsmod | grep usbcore"
The race conditions is still there between rt2500usb and rt73usb so you may want to blacklist rt2500usb and remove it "sudo modprobe -rv rt2500usb"

---

### Post by dgel on 2007-10-22
Thanks for the replys :) blacklisting ipv6 doesn't work for me.
The result of lsmod | grep usbcore is:

usbcore               138632  5 rt73usb,rt2x00usb,ehci_hcd,ohci_hcd

I have rt2x00usb blacklisted, but it still loads it and when i try to remove it, it gives says:

FATAL: Module rt2x00usb is in use.

so how do i remove it?
Ubuntu is very erratic when it comes to my wifi. It seems like it works randomly and for a random amount of time.

---

### Post by Austin_KW on 2007-10-22
> **Na-Fiann said:**
> Thanks for the replys :) blacklisting ipv6 doesn't work for me.
The result of lsmod | grep usbcore is:

usbcore               138632  5 rt73usb,rt2x00usb,ehci_hcd,ohci_hcd

I have rt2x00usb blacklisted, but it still loads it and when i try to remove it, it gives says:

FATAL: Module rt2x00usb is in use.

so how do i remove it?
Ubuntu is very erratic when it comes to my wifi. It seems like it works randomly and for a random amount of time.

You should not blacklist rt2x00usb, it is the generic driver used by  rt73usb and rt2500usb.

---

### Post by jemy_x on 2007-10-23
This HOWTO fixed wireless access for me in Gutsy. Good job diepruis and all those who have contributed their invaluable help; now that I have wireless net access, I'm one big step closer to switching to Ubuntu more frequently for everyday tasks!

For reference, I have a D-Link GWL-122 Revision C1, with the RT73 chipset. Also, I use WPA encryption, and hide the SSID of the network.
While Ubuntu sadly could not get it to work straight away post-install with the RT73USB driver (all the correct info was supplied), this guide set me right with a minimum of fuss.

Here's hoping for 8.04!

---

### Post by dannyboy79 on 2007-10-25
> **jemy_x said:**
> This HOWTO fixed wireless access for me in Gutsy. Good job diepruis and all those who have contributed their invaluable help; now that I have wireless net access, I'm one big step closer to switching to Ubuntu more frequently for everyday tasks!

For reference, I have a D-Link GWL-122 Revision C1, with the RT73 chipset. Also, I use WPA encryption, and hide the SSID of the network.
While Ubuntu sadly could not get it to work straight away post-install with the RT73USB driver (all the correct info was supplied), this guide set me right with a minimum of fuss.

Here's hoping for 8.04!

sad isn't it! i posted bugs at launchpad and everything. the dev's still couldn't get this working right. I know it's hard to accomidate all the various wireless cards but we have been screaming about this since Edgy!

---

### Post by ebs16 on 2007-10-25
has anyone managed to get the rt2x00 drivers to actually compile and work in master mode? i'm running into a few problems at the compile stage in gutsy.

---

### Post by Austin_KW on 2007-10-25
> **ebs16 said:**
> has anyone managed to get the rt2x00 drivers to actually compile and work in master mode? i'm running into a few problems at the compile stage in gutsy.

I dont think that the rt2x00 cvs snapshot will build on gutsy, it did until a few week ago but the have been interface changes (mac80211 I think)

To build the current you would probably need git and roll your own;  a lot of work.

Don't know about master mode, never tried it.

---

### Post by ebs16 on 2007-10-25
Thanks for the info.  Master mode is supposed to be implemented in the new drivers.

I have downloaded the git files, but i'm not at all sure of what i'm supposed to do with them.  Has anyone managed to build successfully using git?

thanks!

---

### Post by dgel on 2007-10-26
Hi,

well i think i tried everyting with the original drivers, but the times I can get it up, it doesn't stay up for more than 2 hours:P So, I installed the serialmonkey drivers, everything works perfect except for one thing.
At startup, I have no internet, I have to run a lot of steps again including the 'sudo modprobe -v rt73' step. My network/interfaces file is configured properly, it used to work under feisty... any idea what's going wrong here?

---

### Post by Austin_KW on 2007-10-26
> **Na-Fiann said:**
> Hi,

well i think i tried everyting with the original drivers, but the times I can get it up, it doesn't stay up for more than 2 hours:P So, I installed the serialmonkey drivers, everything works perfect except for one thing.
At startup, I have no internet, I have to run a lot of steps again including the 'sudo modprobe -v rt73' step. My network/interfaces file is configured properly, it used to work under feisty... any idea what's going wrong here?

You can have the driver load at boot by adding it to /etc/modules
What are the other steps you have to take?

---

### Post by dannyboy79 on 2007-10-26
> **Na-Fiann said:**
> Hi,

well i think i tried everyting with the original drivers, but the times I can get it up, it doesn't stay up for more than 2 hours:P So, I installed the serialmonkey drivers, everything works perfect except for one thing.
At startup, I have no internet, I have to run a lot of steps again including the 'sudo modprobe -v rt73' step. My network/interfaces file is configured properly, it used to work under feisty... any idea what's going wrong here?
I have been on Gutsy for a long time, the rt73_cvs_daily tarball from serialmonkey that I saved locally a long time ago has is building properly and using the guide it just works even after booting up.  i posted the tarball a few pages back if anyone needs it.

---

### Post by Austin_KW on 2007-10-26
> **Na-Fiann said:**
> Hi,

well i think i tried everyting with the original drivers, but the times I can get it up, it doesn't stay up for more than 2 hours:P So, I installed the serialmonkey drivers, everything works perfect except for one thing.
At startup, I have no internet, I have to run a lot of steps again including the 'sudo modprobe -v rt73' step. My network/interfaces file is configured properly, it used to work under feisty... any idea what's going wrong here?

Also check, /etc/udev/rules.d/70-persistent-net.rules (this got confused on one of my updates to gutsy)

---

### Post by dgel on 2007-10-27
Thanks for the help :)
This is the steps I take to get wireless working:

sudo modprobe -v rt73
sudo ifconfig wlan0 up
sudo iwpriv wlan0 set AuthMode=WPAPSK
sudo iwpriv wlan0 set EncrypType=TKIP
sudo iwpriv wlan0 set WPAPSK="Censored"
sudo iwpriv wlan0 set SSID="Censored"
sudo iwpriv wlan0 set NetworkType=Infra
sudo dhclient wlan0

also, my 70-persistent-net,rules looks like this:

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10de:0x0066 (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:0c:6e:7f:24:c5", NAME="eth0"

# USB device 0x13b1:0x0020 (rt73usb)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:18:f8:2c:2a:94", ATTRS{type}=="1", NAME="wlan0"

# PCI device 0x10b7:0x9201 (3c59x)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:26:54:10:ca:c2", NAME="eth1"


Do I need to change it or add something?

---

### Post by Austin_KW on 2007-10-27
Na-Fiann, 

Looks Ok, If it will not work by setting the commands in /etc/network/interfaces then just add the commands to /etc/rc.local (before the exit) and they will be run at the end  of the boot sequence.

---

### Post by diepruis on 2007-10-28
Just a quick update:

RT **61** is *finally* working for me on 7.10 out of the box. I encourage people to test and see whether the same goes for RT73, then we can maybe get rid of this thread ^_^

Happy ubuntuing and thanks to the devs for the best release, liek evar!

---

### Post by Austin_KW on 2007-10-28
diepruis , 
If you leave it connected does the rx speed drop. 
On my RT2500 the new driver starts off at 54Mbs but after a time drops to 1 or 2 Mbs on the RX. The iwconfig still reports the TX speed as 54Mbs but the  speed as reported on my router is 1/2Mbs and the network performance is rubbish.

---

### Post by Mars73 on 2007-10-28
I took the plunge and did a fresh install of Ubuntu Gutsy.
I have a Belkin wireless USB stick with RT73 chipset.
With Feisty it didn't work out of the box and had to follow Diepruis's instructions and with Gutsy it's no different.
Thanks god I knew where to look at (I had my experience from Feisty) and had it up and running in no time only it seems with Gutsy the RT73 is not working with WPA (AES and TKIP), so I now only have WEP installed.
I really want it to work with WPA/AES, which worked without problems in Feisty but somehow in Gutsy not anymore.
When using WPA the Scroll Lock and Caps Lock leds are blinking and Gutsy is frozen.
If anyone knows a solution to this I'm all ear...for now it's WEP and the rest of Ubuntu Gutsy is all working fine, no problems.

---

### Post by Mars73 on 2007-10-28
Well already a little update.
It looks like I have a solution to the RT73 and WPA/AES problem (maybe it's been here before but I have not read every page in this thread).
I downloaded Rtutilt and changed WEP into WPA/AES in my router, then started Rtutilt and did a scan, connected to my router and gave the WPA/AES password and low and behold everything works in WPA security!
Why it doesn't work with /etc/network/interfaces is beyond me but if I can do this with a GUI then even better.
Anyway hope to help some others with this.

---

### Post by diepruis on 2007-10-28
> **Austin_KW said:**
> diepruis , 
If you leave it connected does the rx speed drop. 
On my RT2500 the new driver starts off at 54Mbs but after a time drops to 1 or 2 Mbs on the RX. The iwconfig still reports the TX speed as 54Mbs but the  speed as reported on my router is 1/2Mbs and the network performance is rubbish.

I haven't noticed anything so far and net performance is good.

I remember reading something about that on rt2x00 devel.... There was a simple source tweak that fixed it. It's there for some workaround reason. IIRC the thread mentioned the rate control algorithm and a simple hack to force it to use 54Mbps. It also mentions a recent commit that helped. Did you try compiling a new version? Not sure if it will work on the current Ubuntu kernel though.

---

### Post by diepruis on 2007-10-28
> **Mars73 said:**
> Well already a little update.
It looks like I have a solution to the RT73 and WPA/AES problem (maybe it's been here before but I have not read every page in this thread).
I downloaded Rtutilt and changed WEP into WPA/AES in my router, then started Rtutilt and did a scan, connected to my router and gave the WPA/AES password and low and behold everything works in WPA security!
Why it doesn't work with /etc/network/interfaces is beyond me but if I can do this with a GUI then even better.
Anyway hope to help some others with this.

I had the same problem with my rt61 and my sister's rt73. RutilT also solved it, but I have no idea why! The drivers are probably just incompatible with wireless-utils

:shrug:

---

### Post by Austin_KW on 2007-10-28
> **diepruis said:**
> I haven't noticed anything so far and net performance is good.

I remember reading something about that on rt2x00 devel.... There was a simple source tweak that fixed it. It's there for some workaround reason. IIRC the thread mentioned the rate control algorithm and a simple hack to force it to use 54Mbps. It also mentions a recent commit that helped. Did you try compiling a new version? Not sure if it will work on the current Ubuntu kernel though.

Latest CVS will not compile on gutsy, but I should have some older snapshots. I will try and find the fix and see if I can patch the older code.

---

### Post by ~cyrus~ on 2007-10-29
> **diepruis said:**
> Try adding the following line to /etc/modprobe.d/blacklist

```

blacklist ipv6

```

And reboot.

Solved my [connectivity issue]("http://ubuntuforums.org/showthread.php?t=586395").

Looks like it was related to "DNS resolves everything to 1.0.0.0 intermittently on some ADSL Routers."

---

### Post by dgel on 2007-10-29
Hi,

Austin_KW, if I add the commands to rc.local, should it look exactly the same as in interfaces? Or should it look like what I do in the terminal, but without the sudo part?

---

### Post by Austin_KW on 2007-10-29
> **Na-Fiann said:**
> Hi,

Austin_KW, if I add the commands to rc.local, should it look exactly the same as in interfaces? Or should it look like what I do in the terminal, but without the sudo part?

Terminal commands without sudo

---

### Post by gardhauge on 2007-10-30
Just wanted to share with you that I found a way to make my  D-Link DWL -G122 C1 (rt73) work in Gutsy. It won't just work out of the box, and the serialmonkey-cvs snapshot only made my kernel panic, which is not good, and makes it completely useless. But by acciddent I discovered that all I needed to do was to keep some of the module blacklistings by keeping/inserting the following in /etc/modprobe.d/blacklist

```
# Blacklist rt2570, as it causes conflicts with rt73
 blacklist rt2570
# Other modules that break rt73
 blacklist rt2500usb
 blacklist rt2x00lib
#Disable the serialmonkey rt73
 blacklist rt73
```

It seems as the rt73usb module already in ubuntu is working fine, but not when (one of) the other modules are running.

I'm using WPA-TKIP and connecting with dhcp. I have also uninstalled network-manager, but I'm not sure if that has anything to with the fact that this is working, but you should try it if you're having problems.

Hope it helps somebody. :)

---

### Post by Mars73 on 2007-10-30
> **diepruis said:**
> I had the same problem with my rt61 and my sister's rt73. RutilT also solved it, but I have no idea why! The drivers are probably just incompatible with wireless-utils

:shrug:

Well it's still working perfectly over here, so no complaints. :-)
So following your information on page 1 and then install RutilT and I'm a happy man.
Also what I noticed with Feisty is that I had to disable IPv6 because of really slow internet browsing but now with Gutsy the speed is great (with IPv6 still on).
I'm a happy Gutsier.: )

---

### Post by Austin_KW on 2007-10-30
> **gardhauge said:**
> Just wanted to share with you that I found a way to make my  D-Link DWL -G122 C1 (rt73) work in Gutsy. It won't just work out of the box, and the serialmonkey-cvs snapshot only made my kernel panic, which is not good, and makes it completely useless. But by acciddent I discovered that all I needed to do was to keep some of the module blacklistings by keeping/inserting the following in /etc/modprobe.d/blacklist

```
# Blacklist rt2570, as it causes conflicts with rt73
 blacklist rt2570
# Other modules that break rt73
 blacklist rt2500usb
 blacklist rt2x00lib
#Disable the serialmonkey rt73
 blacklist rt73
```

It seems as the rt73usb module already in ubuntu is working fine, but not when (one of) the other modules are running.

I'm using WPA-TKIP and connecting with dhcp. I have also uninstalled network-manager, but I'm not sure if that has anything to with the fact that this is working, but you should try it if you're having problems.

Hope it helps somebody. :)

Many manufacturers seem to use the same ID for rt2570 & rt73 dongles, hence the need to blacklist the rt2570 and rt2500usb. You should only need to blacklist rt2570 if you manually installed the rt2570 legacy driver

You should only need to blacklist rt73 if you manually installed the legacy driver

You should not need to blacklist rt2x00lib, I think this will be ignored as it is loaded by rt73usb as a dependency anyway.

---

### Post by gardhauge on 2007-10-31
> You should only need to blacklist rt73 if you manually installed the legacy driver

That's the driver that made my kernel panic during startup of Ubuntu.

I noted a peculiarity with my setup; that the wireless won't connect at startup. If I disable and enable the wireless after logging into the system, it starts to work, so once again my tiny little restart_wireless-script came in handy:

```
#!/bin/bash
gksu ifdown wlan0
gksu ifup wlan0
```

Also, I can not see the strength of the wireless signal, it shows 0% in the system tray, usually it's about 80%. 

It's not a pretty solution I've come up with, but at least it makes my d-link connect.

I will play around a bit to see if I can get it to work a little better.

And thanks for the response btw. :)

---

### Post by mushusker on 2007-11-01
> **Mars73 said:**
> Well already a little update.
It looks like I have a solution to the RT73 and WPA/AES problem (maybe it's been here before but I have not read every page in this thread).
I downloaded Rtutilt and changed WEP into WPA/AES in my router, then started Rtutilt and did a scan, connected to my router and gave the WPA/AES password and low and behold everything works in WPA security!
Why it doesn't work with /etc/network/interfaces is beyond me but if I can do this with a GUI then even better.
Anyway hope to help some others with this.

Yeah, I kind of stumbled on this myself...wish I would have seen this post first!

I have the Belkin Wireless G USB Network Adapter (Part # F5D7050 version 3000), and although there was no problem getting it to be detected (running Ubuntu 7.10), and it found my wireless network, trying to connect by typing in the WEP key through NetworkManager got me nowhere. (I love the interface for NetworkManager though!)

I installed RutilT, did a scan, typed in the WEP key, and everything's perfect. Well, except for the ugly look of RutilT.

---

### Post by diepruis on 2007-11-01
> **mushusker said:**
> Yeah, I kind of stumbled on this myself...wish I would have seen this post first!

I have the Belkin Wireless G USB Network Adapter (Part # F5D7050 version 3000), and although there was no problem getting it to be detected (running Ubuntu 7.10), and it found my wireless network, trying to connect by typing in the WEP key through NetworkManager got me nowhere. (I love the interface for NetworkManager though!)

I installed RutilT, did a scan, typed in the WEP key, and everything's perfect. Well, except for the ugly look of RutilT.

Is there a guide somewhere on compiling RutilT for Gutsy that I can link to? If there is no such guide, then I'll write one myself.

---

### Post by dgel on 2007-11-01
hi,

I've still not managed to get my wireless up automatically, I'm thinking of making a small script out of the iwpriv commands and running it at login, see if that works:P (getting kinda desperate)
Anyhoo, as somewhat of a last resort i'm trying to use rutilt, from the repo's, but everytime I enter my password for the network it recognises perfectly, it crashes.
Any ideas?

[edit]
I just made a small script running the exact commands i use to get wireless up. running it (with dhclient at the end) gives me a lot of these messages:
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
and in the end, connecting fails.
If, however even just after that i run the commands one by one in the terminal again, it works... is my ubuntu f*cked up or something?
[/edit]

---

### Post by Austin_KW on 2007-11-01
> **Na-Fiann said:**
> hi,

I've still not managed to get my wireless up automatically, I'm thinking of making a small script out of the iwpriv commands and running it at login, see if that works:P (getting kinda desperate)
Anyhoo, as somewhat of a last resort i'm trying to use rutilt, from the repo's, but everytime I enter my password for the network it recognises perfectly, it crashes.
Any ideas?

[edit]
I just made a small script running the exact commands i use to get wireless up. running it (with dhclient at the end) gives me a lot of these messages:
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
and in the end, connecting fails.
If, however even just after that i run the commands one by one in the terminal again, it works... is my ubuntu f*cked up or something?
[/edit]
There are problems with rutilt, which I think are data dependent, I think there is a buffer overflow that is only seen by some people.

Does the connection work if you manually run the script rather than entering the same commands in a terminal. You may have a timing issue. try adding sleep commands between the commands eg "sleep 1" to add a 1 second delay between the commands, like there would be if you manually typed them.

---

### Post by kevdog on 2007-11-01
Here is the post Im recommending for people wanting to setup rutilti
[http://ubuntuforums.org/showthread.php?t=554089&highlight=rutilt](http://ubuntuforums.org/showthread.php?t=554089&highlight=rutilt)

I was wondering if someone in the main thread could clarify the exact modules that need to be blacklisted since it seems some people need to add additional modules.

---

### Post by dgel on 2007-11-01
I played around with sleep commands a bit and found out that inserting "sleep 0.1" after setting my ssid, the script would work. Could this be the reason my /etc/network/interfaces doesn't work?

---

### Post by Austin_KW on 2007-11-01
> **Na-Fiann said:**
> I played around with sleep commands a bit and found out that inserting "sleep 0.1" after setting my ssid, the script would work. Could this be the reason my /etc/network/interfaces doesn't work?

Yes could be a race condition on SMP. thy adding "pre-up sleep 1" to the interfaces file.

---

### Post by -Stevey-Wonder-1990- on 2007-11-03
i was following this guide when my computer froze and crashed i dont know where to start now,

i have made a thread about it here

[http://ubuntuforums.org/showthread.php?p=3697200#post3697200](http://ubuntuforums.org/showthread.php?p=3697200#post3697200)

please can you help

---

### Post by fatyandao on 2007-11-04
Hi All,

This is my first post in here with regards to troubleshooting with Ubuntu.

I have an IBM T20, which is now working well after looking at thinkwiki.

However, there seems to be a problem with installing my USB WiFi dongle on my laptop.

It most probably uses the rt73 chipset; the drivers supplied is for Fedora 4.0, and I can't any other way of finding it out other than hacking apart the dongle (and how to find it out from there?)

[http://www.planex.net/download/wireless/gw-us54mini2.htm](http://www.planex.net/download/wireless/gw-us54mini2.htm)

The first time I installed it with the tarball from serialmonkey, there wasn't any problem until one or two days. I forgot what I did, except to guess out the chipset of my dongle, and find the relevant drivers.

In the end, desperate to make my dongle work again, I've reformatted and reinstalled Ubuntu 7.04 several times in a row now. The thing still doesn't work.

What do you need to help me on my debugging? Please post in this forum, and I'll try as much as I can to paste it all here.



Hardware: Planex GW-US54Mini2 (USB)
Wireless Network: Linksys WRT54G, Channel 6 (2.437Ghz), Running on WEP, with 10 hex digit key.
Laptop: IBM T20

Runnign iwlist: if you need the details, I'll paste them, but scanning shows my network cell.
with ap/accesspoint, it shows my  router's signal quaility to be 73/100.

Running iwconfig: shows my essid to be my router's essid. RTS thr is off, Fragment thr is off. Link Quality is 0/100. Sigbal level is -40dBm, Noise Level is -115 dBm.

Will try to paste the information here. When there is connectivity (the led is green), but now it's always orange.

Please help! Thank you....

---

### Post by a_smartboy8 on 2007-11-04
Hi, I am having  EDIMAX EW-7318USg wireless usb card and i configured it using the serialmonkey drivers instructions given here [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

My computer is installed with 64 bit gutsy with the kernel 2.6.22-14-generic .( Earlier it was on feisty and it also had the same problem)

After several tries i managed to get the wireless working. But few minutes later the connection dropped. After searching through a lot of forums, i found out that the problem is with the ehci_hcd module and so i disabled it using the command 'modprobe -r ehci_hcd' and then the wireless worked without dropping the connection.

Now my real problem started. When the system boots up, it hangs if my wireless card is plugged in. If i remove the wireless card then the system boots up without a problem. After system booting, i plug in the wireless card, remove ehci_hcd module manually and then load rt73 module; Wireless starts working with out any problems and for every system-boot, i have to repeat the procedure. So i reckon that this is a problem with the driver modules.  my etc/modprobe.d/blacklist is given below:
```


blacklist rt73usb
blacklist rt2570
blacklist rt2500usb
blacklist rt2x00lib


```

lsusb gives the following output
```


Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 008: ID 148f:2573 Ralink Technology, Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


```

/etc/udev/rules.d/70-persistent-net.rules is giving the following values

```

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="Wired_MAC_Address", ATTRS{type}=="1", NAME="eth0"


# USB device 0x148f:0x2573 (rt2500usb)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="Wireless_MAC_Address", ATTRS{type}=="1", NAME="wlan0"


```

It is interesting to note that they are loading the rt2500usb driver here, which is appearing to be a bit strange for me

dmesg|grep rt gives the following output ( i have included only the relevant entries)
```

[   53.160908] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   53.161069] hub 4-0:1.0: 6 ports detected
[   57.025695] rtusb init ====>
[   57.025729] usbcore: registered new interface driver rt73
[  726.191997] rt73 driver version - 1.0.3.6 CVS
[  726.210792] rt73 driver version - 1.0.3.6 CVS
[  726.210850] rt73 driver version - 1.0.3.6 CVS
[  737.046366] rt73 driver version - 1.0.3.6 CVS
[  737.286216] ***rt73***: Interface goes up for the first time, activating permanent MAC
[  737.286229] ***rt73***: Active MAC is: "Wireless_MAC_Address"

```

Note that ehci_hcd usb2.0 started despite manual removal of the module..

Can anyone help me in solving this problem?

---

### Post by shaunybo on 2007-11-06
i have tried you method several times and ive tried other methods aswell without sucess in getting my usb dongle to work, has anyone got an idea on how to help me?

---

### Post by diepruis on 2007-11-06
> **shaunybo said:**
> i have tried you method several times and ive tried other methods aswell without sucess in getting my usb dongle to work, has anyone got an idea on how to help me?

We'll try to help you, but we need some more information. What exactly is happening?

---

### Post by Austin_KW on 2007-11-06
> **shaunybo said:**
> i have tried you method several times and ive tried other methods aswell without sucess in getting my usb dongle to work, has anyone got an idea on how to help me?

Not knowing the state of your system can you post the output of some terminal commands
```

lsusb
lsmod | grep usbcore
cat /etc/network/interfaces
cat /etc/modprobe.d/blacklist
modinfo rt73
ifconfig -a
sudo iwconfig

```

---

### Post by fatyandao on 2007-11-07
Hi Austin,

Here is the output from my PC:

> lsusb
```
Bus 001 Device 004: ID 2019:ab50  
Bus 001 Device 003: ID 058f:6366 Alcor Micro Corp. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. 
Bus 001 Device 001: ID 0000:0000  
```
ID 2019:ab50 is my device... I'm sure of it.
> lsmod | grep usbcore
```
usbcore               134280  5 rt73,usb_storage,libusual,uhci_hcd
```
> cat /etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
#iface wlan0 inet static
#address 192.168.1.250
#netmask 255.255.255.0
#network 192.168.1.1
#gateway 192.168.1.
	pre-up ifconfig wlan0 up
	pre-up iwconfig wlan0 essid spwireless2
	pre-up iwconfig wlan0 key KEY
	pre-up iwconfig wlan0 mode Managed


```
> cat /etc/modprobe.d/blacklist
```
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

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

blacklist rt73usb
blacklist rt2570
blacklist rt2500usb
blacklist rt2x00lib

```

> modinfo rt73
```
filename:       /lib/modules/2.6.20-15-generic/extra/rt73.ko
license:        GPL
description:    Ralink RT73 802.11abg WLAN Driver 1.0.3.6 CVS 2007102609
author:         http://rt2x00.serialmonkey.com
srcversion:     C9DCB57A802E5F892321DB6
alias:          usb:v1740p7100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB50d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB01d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0769p31F3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p90ACd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p9712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6238d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6229d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2671d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA861d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6877d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0023d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1472p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C04d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1631pC019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00F4d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1724d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1723d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0722d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Dd*dc*dsc*dp*ic*isc*ip*
depends:        usbcore
vermagic:       2.6.20-15-generic SMP mod_unload 586 
parm:           debug:Debug mask: n selects filter, 0 for none (int)
parm:           firmName:Permit to load a different firmware: (default: rt73.bin)  (charp)

```
> ifconfig -a```

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:754 errors:0 dropped:0 overruns:0 frame:0
          TX packets:754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60372 (58.9 KiB)  TX bytes:60372 (58.9 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:90:CC:E8:09:BD  
          inet6 addr: fe80::290:ccff:fee8:9bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2371 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:646 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:197510 (192.8 KiB)  TX bytes:35952 (35.1 KiB)

wlan0:ava Link encap:Ethernet  HWaddr 00:90:CC:E8:09:BD  
          inet addr:169.254.8.182  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

```
> sudo iwconfig
```

wlan0     RT73 WLAN  ESSID:"spwireless2"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:680A-BC80-80
          Link Quality=0/100  Signal level:-52 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by shaunybo on 2007-11-07
im sure i have installed the driver correctly as there were no errors but the light still wont come on the dongle, and i cant choose to connect to a wireless connection and if i put in the details manualy it just wont connect. sorry for being so vauge in my last post.

> lsusb

```
Bus 004 Device 002: ID 050d:705a Belkin Components
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 10df:0101 In-Win Development, inc
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

> lsmod | grep usbcore

```

usbcore                              138632   6  rt73,usb_storage,libusual, ehci_hcd,uhci_hcd 
```

>  cat /etc/network/interfaces 

```
 # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback



iface rausb inet dhcp
wireles-key **********
wireless-essid d-link
```

>  cat /etc/modprobe.d/blacklist 

```
his file lists those modules which we don't want to be loaded by
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

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# blacklist rt73usb, as it is a non-functional beta module wich conflicts with the working rt73 module.
blacklist rt73usb

# blacklist rt2570, as it causes conflicts with rt73
blacklist rt2570

# orther modules that break rt73
blacklist rt2500usb
blacklist rt2x00lib


```

>  modinfo rt73 

```
 filename:       /lib/modules/2.6.22-14-generic/extra/rt73.ko
license:        GPL
description:    Ralink RT73 802.11abg WLAN Driver 1.0.3.6 CVS 2007102912
author:         http://rt2x00.serialmonkey.com
srcversion:     A653E55A1EC9977E989F1CC
alias:          usb:v1740p7100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB50d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB01d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0769p31F3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p90ACd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p9712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6238d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6229d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2671d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA861d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6877d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0023d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1472p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C04d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1631pC019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00F4d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1724d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1723d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0722d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Dd*dc*dsc*dp*ic*isc*ip*
depends:        usbcore
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           debug:Debug mask: n selects filter, 0 for none (int)
parm:           firmName:Permit to load a different firmware: (default: rt73.bin)  (charp)


```

>  ifconfig -a 

```
 eth0      Link encap:Ethernet  HWaddr 00:40:CA:6F:F7:EE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1784 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:141616 (138.2 KB)  TX bytes:141616 (138.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


``` 

>  sudo iwconfig 

```
 lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT73 WLAN  
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


```

---

### Post by diepruis on 2007-11-07
> **shaunybo said:**
> 
```
 # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback



iface rausb inet dhcp
wireles-key **********
wireless-essid d-link
```


Here you use "rausb" as the interface name. Yet ifconfig reports it as wlan0. Please try the guide again, but use wlan0 instead of rausb.

> **shaunybo said:**
> 
```
 eth0      Link encap:Ethernet  HWaddr 00:40:CA:6F:F7:EE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1784 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:141616 (138.2 KB)  TX bytes:141616 (138.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```


---

### Post by Austin_KW on 2007-11-07
fatyandao,

I don't see anything obvious, Verify the KEY (680A-BC80-80)? that you set in the interfaces file. You might also try temporarily turning off encryption to see if you get a dhcp address.

---

### Post by jazzcat on 2007-11-07
Is there any opinion about which driver to use?  Should I use the SerialMonkey driver, or should I use the debian driver included with the EW-7318 driver disk?  The driver included on the disk consists of a source code part (you compile for your kernel) and a binary module.  I'd *think* that I'd have better results using the EDIMax driver, but interesting things have happened when I've *thought* before...

Oh, also, is there better "plug and play" support in Gutsy Gibbon for this adapter?

---

### Post by shaunybo on 2007-11-07
i sorted :D i did it again and it just worked this time...thank you for taking your time to try and help me :)

---

### Post by fatyandao on 2007-11-07
> **Austin_KW said:**
> fatyandao,

I don't see anything obvious, Verify the KEY (680A-BC80-80)? that you set in the interfaces file. You might also try temporarily turning off encryption to see if you get a dhcp address.

Hi Austin,

Laptop doesn't have access to internet, so i will post the details later. FYI, the key is correct. Even with disabling WEP on the router, it still doesn't work.
Is there anything else you'll like to need from me?

Some output from running dhclient:

Coming sooonnnnn.

---

### Post by diepruis on 2007-11-08
> **jazzcat said:**
> Is there any opinion about which driver to use?  Should I use the SerialMonkey driver, or should I use the debian driver included with the EW-7318 driver disk?  The driver included on the disk consists of a source code part (you compile for your kernel) and a binary module.  I'd *think* that I'd have better results using the EDIMax driver, but interesting things have happened when I've *thought* before...

Oh, also, is there better "plug and play" support in Gutsy Gibbon for this adapter?

Mmmm... are you sure this device is rt73? I don't recall ever hearing about an rt73 with this type of device.... That said, try the serialmonkey drivers first, binary blobs don't mix that well with Linux in my experience.

---

### Post by Fraser67 on 2007-11-08
I've had my rt73 USB wireless dongle working on Xubuntu 7.04 but after a fresh install of Xubuntu 7.10 it’s not playing. It finds the lsusb finds the dongle but no life at from the dongle.  However main reason for posting is how to I install Rutilt. I have down loaded the RutilTv0.15.tar.gz and unpacked but it running ./config.sh won't run due to a host of dependencies, which I can't really sort out since I don't have an  easy access to the internet since rt73 won't run because I think I can't configure it. Are there any other ways of installing Rutilt that have all the stuff that it needs to run?

---

### Post by jazzcat on 2007-11-08
> **diepruis said:**
> Mmmm... are you sure this device is rt73? I don't recall ever hearing about an rt73 with this type of device.... That said, try the serialmonkey drivers first, binary blobs don't mix that well with Linux in my experience.

Yep, it sure is an RT73.  It seems to be able to find networks with Gutsy Gibbon with no tweaking on my part, but since I'm not at home I don't know if the adapter will log on to any.  The drivers on the SerialMonkey site are actually later versions of the driver provided on the CD; the binary BLOB is actually firmware for the chipset.

By default, Feisty Fawn locked up the machine when I inserted this adapter, but GG *seems* to be OK with it.  We'll see....

Cheers,
-JC

---

### Post by diepruis on 2007-11-08
> **jazzcat said:**
> Yep, it sure is an RT73.  It seems to be able to find networks with Gutsy Gibbon with no tweaking on my part, but since I'm not at home I don't know if the adapter will log on to any.  The drivers on the SerialMonkey site are actually later versions of the driver provided on the CD; the binary BLOB is actually firmware for the chipset.

By default, Feisty Fawn locked up the machine when I inserted this adapter, but GG *seems* to be OK with it.  We'll see....

Cheers,
-JC

Ahh okay, of course (had a bit of a d'oh moment there). My advice is to go with what works, if it's not locking up just leave it alone :)

---

### Post by Kazaksan on 2007-11-10
I can't seem to copy the rt73-cvs-daily.tar.gz into usr/scr. Tried "save as" in the archive manager.

---

### Post by diepruis on 2007-11-11
> **Kazaksan said:**
> I can't seem to copy the rt73-cvs-daily.tar.gz into usr/scr. Tried "save as" in the archive manager.

Did you try the command that was posted in the HOWTO? If so, please post what you typed and what the terminal replied.

---

### Post by Albaraha on 2007-11-11
I'm writing to assure you that this lovely procedure works on Gusty on my machine as well.
Thanks diepruis.

---

### Post by jnui on 2007-11-14
ok these instructions did not work for me, but I did finally get it working on Gutsy Gibbon

I have an Edimax EW 7318USg USB stick wifi.

I had to use older drivers, I have posted all the information, and a copy of the older drivers on my forum here [http://www.niumata.com/forum/viewtopic.php?id=6](http://www.niumata.com/forum/viewtopic.php?id=6)

it includes the little known iwpriv command that this ralink device supports.
if you want WPA to work with this wifi device you will have to use this command.

I also recommend rutilt, which is specifically for ralink (I think)

Johnny
[www.niumata.com](www.niumata.com)

---

### Post by ayenack on 2007-11-14
Hello diepruis. Great tutorial often direct people here to get their cards working.

Not 100% sure this is relevant, but was reading through your tutorial and just thinking that instead of

**sudo aptitude purge network-manager**

Would it not be better to have

**sudo aptitude purge network-manager network-manager-gnome**

ayenack.

---

### Post by Austin_KW on 2007-11-14
> **jnui said:**
> ok these instructions did not work for me, but I did finally get it working on Gutsy Gibbon

I have an Edimax EW 7318USg USB stick wifi.

I had to use older drivers, I have posted all the information, and a copy of the older drivers on my forum here [http://www.niumata.com/forum/viewtopic.php?id=6](http://www.niumata.com/forum/viewtopic.php?id=6)

it includes the little known iwpriv command that this ralink device supports.
if you want WPA to work with this wifi device you will have to use this command.

I also recommend rutilt, which is specifically for ralink (I think)

Johnny
[www.niumata.com](www.niumata.com)

In your post you say; "I tried WPA-psk encryption with rutilt and it crashed"
I assume you mean that rutilt crashed? it has a number of bugs

---

### Post by Fraser67 on 2007-11-14
OK after much trial and error I am on the internet. However its not quite right. I have followed all the instruction in the How To (many thanks) and my /etc/network/interfaces file contains:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
	pre-up ifconfig wlan0 up
	pre-up ifconfig wlan0 down
	pre-up ifconfig wlan0 up
	pre-up ifconfig wlan0 essid "my essid"
	pre-up ifconfig wlan0 mode managed
	pre-up ifconfig wlan0 channel 9
	pre-up iwpriv wlan0 set AuthMod=WPAPSK
	pre-up iwpriv wlan0 set EncrypType=TKIP
	pre-up iwpriv wlan0 set WPAPSK="my key"

This does nothing. iwconfig returns info with nothing set. What calls this file and how is it called manually from a terminal?

If I use Rtutil and use the scan tab I can see my router and select it. I then enter the key code and answer yes to use dhcp. Rutil then closes automatically (looks like it crashes to me). But I now have a connection to my router and the internet

So why does this work and not the info in my interfaces file. I can also enter the commands in the interfaces file in a termial (without a pre-config) and I get a connection.

How do I make this happen automatically?

I using a Dell Latitude CPi (P2) with Xubuntu 7.10.

Also I note that during the installation phase after sudo make install a file called rt73.bin appears in /lib/firmware/ and nothing is changed or added in /lib/firmware/2.6.22-14-generic were an original file called rt73.bin lives. I have manually overwritten this file with a copy of the one in /lib/firmware. This seems wrong to me but this is not from a position of strength.

So any ideas how I can get my Belkin usb 11g stick to automatically connect to my router would be welcome. I am using the serial monkey driver that is a week old. Thanks Fraser

---

### Post by Austin_KW on 2007-11-14
To force a configure from the interfaces file
```
sudo ifup --f wlan0
```
Note the double '-', It should report any errors in the file.

I see a typo AuthMod Vs **AuthMode**
It should not be necessarry to set the channel

---

### Post by stpe on 2007-11-15
Thank you very much. It went like a charm and now my MSI mini PCIe card connects right away.
The funny thing is that I did not have any problem connecting with the Gutsy LiveCD, but after hard disk installation, it refused to activate the card. After following this tutorial though, all is well.

Again, thanks a lot!!

---

### Post by DJ_Cyberdance on 2007-11-15
Hi!

I have got a cheap notebook, brand "Hasee" from China, with a built-in RT73 USB WLAN module. I am running Ubuntu Studio (gutsy) and of course the wireless module did not work out of the box. I successfully compiled the driver and did the following

```

root@notebook:/home/christoph# lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 148f:2573 Ralink Technology, Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

root@notebook:/home/christoph# rmmod rt2500usb rt2x00usb rt2x00lib rt73
root@notebook:/home/christoph# modprobe rt73
root@notebook:/home/christoph# ifconfig wlan0 up
root@notebook:/home/christoph# iwconfig wlan0 essid 98sg.com
root@notebook:/home/christoph# iwconfig wlan0 key 9999988888
root@notebook:/home/christoph# dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:10:60:21:0e:0c
Sending on   LPF/wlan0/00:10:60:21:0e:0c
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

dmesg:

[  190.419074] usbcore: deregistering interface driver rt2500usb
[  190.429698] usbcore: deregistering interface driver rt73
[  190.429740] unregister_netdev()
[  190.448044] <=== rtusb exit
[  215.730596] rtusb init ====>
[  215.731140] idVendor = 0x148f, idProduct = 0x2573 
[  215.768621] usbcore: registered new interface driver rt73
[  223.885027] NET: Registered protocol family 10
[  223.885135] lo: Disabled Privacy Extensions
[  262.002707] rt73 driver version - 1.0.3.6 CVS
[  262.162300] ***rt73***: Interface goes up for the first time, activating permanent MAC
[  262.162314] ***rt73***: Active MAC is: 00:10:60:21:0e:0c.
[  272.688500] wlan0: no IPv6 routers present
[  301.534257] NET: Registered protocol family 17

```

I have no idea what I did wrong, you have any recommendations? It probably is worth mentioning that Ubuntu Studio uses an RT kernel, maybe it has to do something with that?

---

### Post by David_G_D on 2007-11-16
I used the drivers Johnny mentioned, which work about as well as the latest snapshot for me, and I have a weird issue.  I have to do:

sudo ifdown wlan0
[unplug device]
[plug device back in]
sudo iwconfig wlan0 essid 'mynetwork' key 'mykey'

and then it works great. I have fiddled around quite a bit, and I can't figure out any other way to make this thing work. Is there some way to avoid all this trouble every time I want to use my wifi dongle?

I use a Edimax EW-7318USg, which is reported by lsusb as:
Bus 002 Device 011: ID 148f:2573 Ralink Technology, Corp. 

Thanks for all the great info.

David

[QUOTE=...

I had to use older drivers, I have posted all the information, and a copy of the older drivers on my forum here [http://www.niumata.com/forum/viewtopic.php?id=6](http://www.niumata.com/forum/viewtopic.php?id=6)

...

Johnny
[www.niumata.com](www.niumata.com)[/QUOTE]

---

### Post by Fraser67 on 2007-11-16
Thanks for that tip for running the interfaces file and the typo. I have also noticed that I used ifconfig for the eesid, channel and mode. This should have been iwconfig! That is what you get when you end up doing these things late at night!

Mind you I still have a question were the rt73.bin file is meant to live and is it normal for Rutilt to disappear after it connects.

Thanks for the replies they have been appreciated.

---

### Post by jazzcat on 2007-11-18
> **jnui said:**
> 
I had to use older drivers, I have posted all the information, and a copy of the older drivers on my forum here [http://www.niumata.com/forum/viewtopic.php?id=6](http://www.niumata.com/forum/viewtopic.php?id=6)


Thanks for the instructions!  I tried this, after a failed attempt using the latest serialmonkey drivers...

wlan0 comes up ok!
wlan0 can see my router!
wlan0 gets a dhcp address just dandy!

but...

when I send the first packet out of the interface, the machine locks up hard.

Any idea how I can find this bugger?

Cheers,
-jc

---

### Post by rockstar on 2007-11-19
I found this very helpful, my first step to getting Kismet to work.

I think I did everything correctly however I'm having the following problem.  The DCHPDISCOVER fails.

On this step: sudo modprobe -r rt2x00lib

Here's what happened:

paul@shuttlebox:~$ sudo modprobe -r rt2x00lib
FATAL: Module rt2x00lib is in use.

Also here is the output from one of the last steps:

paul@shuttlebox:~$ sudo ifconfig wlan0 up
paul@shuttlebox:~$ sudo iwconfig wlan0 essid JOKES
paul@shuttlebox:~$ sudo iwconfig wlan0 key off
paul@shuttlebox:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 6823
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:f8:a8:a7:f5
Sending on   LPF/wlan0/00:18:f8:a8:a7:f5
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Austin_KW on 2007-11-19
> **rockstar said:**
> I found this very helpful, my first step to getting Kismet to work.

I think I did everything correctly however I'm having the following problem.  The DCHPDISCOVER fails.

On this step: sudo modprobe -r rt2x00lib

Here's what happened:

paul@shuttlebox:~$ sudo modprobe -r rt2x00lib
FATAL: Module rt2x00lib is in use.
....

This means that at least one of the rt2x00 beta drivers is still in use, probably the beta rt73usb.

---

### Post by kevdog on 2007-11-19
Austin

Are the rt drivers shipped in Gutsy the ra or serial monkey drivers -- the rt73pci for example??

Why does it seem that downloading and installing the serial monkey drivers from cvs (not the 2x00 legacy drivers) is still the preferred solution?

---

### Post by Austin_KW on 2007-11-19
> **kevdog said:**
> Austin

Are the rt drivers shipped in Gutsy the ra or serial monkey drivers -- the rt73pci for example??

Why does it seem that downloading and installing the serial monkey drivers from cvs (not the 2x00 legacy drivers) is still the preferred solution?

They are the beta serial monkey drivers; people seem to still have problems with them; eg, My rt2500pci runs at 2Mbs with the gutsy driver but the rt73usb was ok for me with the gutsy driver. Appears that mileage varies?

---

### Post by ubulap on 2007-11-20
Greetings,

I've installed Gutsy Gibbon on a laptop.
It has a Gigabyte GN-WI05GS embedded card that apparently uses the ralink 73 chipset.

I was unable to use the default driver that Gutsy provides, so I switched to ndiswrapper.
After successfully having connected to my AP using WPA encription, I decided to give the rt73 driver a try, since in order to use ndiswrapper I had to run sudo /etc/init.d/networking restart everytime I wanted to connect to the internet.

I've blacklisted ndiswrapper module, as well as the rt73usb one that came with Gutsy.
I've installed the rt73 driver, and I've managed to connect to the Internet as long as the router has no encription set.

As soon as I enable WPA encription in my router, I fail to ping it or connect to the Internet.
I've an static IP configuration.
This is my /etc/network/interfaces

```

auto rausb0
iface rausb0 inet static
address 192.168.2.15
netmask 255.255.255.0
network 192.168.2.0
gateway 192.168.2.1
	pre-up ifconfig rausb0 up
        pre-up iwconfig rausb0 mode Managed
	pre-up iwconfig rausb0 essid MYESSID
	pre-up iwpriv rausb0 set NetworkType=Infra
	pre-up iwpriv rausb0 set AuthMode=WPAPSK
    	pre-up iwpriv rausb0 set EncrypType=TKIP
	pre-up iwpriv rausb0 set SSID=MYESSID
    	pre-up iwpriv rausb0 set WPAPSK=Keyphrase
    	pre-up iwpriv rausb0 set SSID=MYESSID
    	
```

My WPA password is a sentence with spaces, such as: My key
I've tried therefore using  pre-up iwpriv rausb0 set WPAPSK=My\ key in the config file on /etc/network/interfaces but to no avail.

If I run iwconfig it has the SSID correctly set, and the AP Hw address shows up correctly.
It seems I'm doing something wrong with the WPA authentification, any help in order to solve this issue would be appreciated.

Thanks in advance.

---

### Post by Austin_KW on 2007-11-20
Ubulap,
The quotes should work, any other quotes in the key? and the key is at least 8 printable characters.
If you use the escape character then I dont think you should also use quotes.

Also anything odd about your SSID, this is used in a hash  with the passphrase to generate the actual key.

---

### Post by ubulap on 2007-11-20
Thanks for your reply Austin_KW,

I'm afraid my post might have lead you to confusion.
My passphrase is a sentence that uses characters with spaces, but no quotes.
I added the quotes on my post trying it to be clearer, I'll edit it.
So, my passphrase is something like: my key is this one

I then have on /etc/network/interfaces

pre-up iwpriv rausb0 set WPAPSK=my\ key\ is\ this\ one

But it just doesn't work.
Also, as for the SSID it's a normal string, without quotes nor any odd character in it.
It shows correctly when doing iwconfig (although it shows the ESSID surrounded with quotes, but I think that's iwconfig displaying way)
iwconfig also reports the correct Mac address of the router, as well as the mode (managed) and the channel.

---

### Post by Austin_KW on 2007-11-20
OK I just tried it with one of my APs and the it works with
```
pre-up iwpriv wlan0 set  WPAPSK="my key is this one"

```
Obviously my interface is wlan0

---

### Post by Austin_KW on 2007-11-20
Just reread your post; do you actually mean backspaces or spaces?

---

### Post by ubulap on 2007-11-20
Thank you once again Austin_KW,

you're entirely right I've been mistyping all the time. I obviously meant "spaces".  :/

Also, I've used the code you've attached me, substituting wlan0 by rausb0.
This time I've been able to ping the router.

Just for the note, I added also this blacklists according to the first post of the thread:
```

# Blacklist rt2570, as it causes conflicts with rt73
blacklist rt2570
# Other modules that break rt73
blacklist rt2500usb
blacklist rt2x00lib
```

Upon restart, the rausb0 interface is configured alright, iwconfig shows correct information.
But, in order to ping the router I necessarily need to bring down the eth0 interface.
(This might have been an issue since the first moment, for both eth0 and rausb0 have different but similar IP addresses)

Would there be any way as to make the wifi work from the start without bringing the eth0 interface down?

---

### Post by dannyboy79 on 2007-11-20
does the /etc/network/interfaces file get parsed to see which interface is "auto", meaning it will be brought up each time? Check that out, I can't ssh into my box right now for some reason otherwise I'd check out my interfaces file. I am using Gutsy with a Belkin usb wifi adapter, I use the rt73 cvs module and my wifi works without having to do anything else when I turn the computer on. It's also possible it's because I don't have an ethernet cable plugged in though?

---

### Post by Austin_KW on 2007-11-20
> **ubulap said:**
> Thank you once again Austin_KW,

you're entirely right I've been mistyping all the time. I obviously meant "spaces".  :/

Also, I've used the code you've attached me, substituting wlan0 by rausb0.
This time I've been able to ping the router.

Just for the note, I added also this blacklists according to the first post of the thread:
```

# Blacklist rt2570, as it causes conflicts with rt73
blacklist rt2570
# Other modules that break rt73
blacklist rt2500usb
blacklist rt2x00lib
```

Upon restart, the rausb0 interface is configured alright, iwconfig shows correct information.
But, in order to ping the router I necessarily need to bring down the eth0 interface.
(This might have been an issue since the first moment, for both eth0 and rausb0 have different but similar IP addresses)

Would there be any way as to make the wifi work from the start without bringing the eth0 interface down?

Ok, that makes sense, if you are using the ethernet while testing the wireless.

You default route will be to your gateway router but still via the ethernet connection. When you remove the cable to test the wireless this route is not deleted.

If you only ever use the wireless connection you should be all set. (if you use a static IP address and gateway you may want to remove the "auto eth0" otherwise you should be ok)

---

### Post by ubulap on 2007-11-21
Removing the auto eth0 makes the wireless act by default, thanks.

I was just hoping that having no ethernet cable would turn the wireless into the default interface to use (in fact, I did have auto eth0 in /etc/network/interfaces when I was using ndiswrapper, and after using the command sudo /etc/init.d/networking restart, the wireless worked as the default interface) but it's not such a big deal, ethernet configuration is much straight forward than wireless one. :)

Now let's hope this rt73 driver proves itself stable enough, thanks everyone for their help and sorry for the slight off-topic with the ethernet question.

---

### Post by FutbolEsVida on 2007-11-27
I have one problem:

cd /usr/src/rt73-cvs-2007112510/Module

when i try to enter this command into the terminal, i get back this response:

bash: cd: /usr/src/rt73-cvs-2007112510/Module: No such file or directory

how can i fix this? i need serious help! thanks a bunch.

---

### Post by diepruis on 2007-11-28
Sorry for not getting back to many of the posts on this thread. My Internet was down for nearly two weeks :'(

> **FutbolEsVida said:**
> I have one problem:

cd /usr/src/rt73-cvs-2007112510/Module

when i try to enter this command into the terminal, i get back this response:

bash: cd: /usr/src/rt73-cvs-2007112510/Module: No such file or directory

how can i fix this? i need serious help! thanks a bunch.

Could you please post the output of these two commands?
```

ls /usr/src
ls /usr/src/rt73-cvs-2007112510

```

---

### Post by TimH1980 on 2007-11-30
Hi,

I posted another topic about my wireless problem. Now I found this helpful tutorial about getting the RT73 driver. I followed all the steps but still my wireless doesn't work. I have two dongles, the other dongle seemed to be suitable for the driver.. 

It's really making me crazy!! Any help would be welcome! (thanks in advance!)

This is the output with iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT73 WLAN  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

This is my usb list:

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 004 Device 002: ID 0a4d:00f5 Evolution Electronics, Ltd UC-33e MIDI Controller
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0a4d:0090 Evolution Electronics, Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 148f:2573 Ralink Technology, Corp. 
Bus 003 Device 001: ID 0000:0000  

This is now my config file for sudo gedit /etc/network/interfaces:


# The loopback network interface
auto lo
iface lo inet loopback



iface eth1 inet dhcp
wireless-key AAF6E465A43E5826CC5A9ADD12
wireless-essid Livebox-dv5d

auto eth1

auto wlan0
iface wlan0 inet dhcp

(I'm not stupid ;-) changed some key letters and essid in this topic)

ifconfig:

tim@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:76:DC:03:27  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:76ff:fedc:327/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1713 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2107754 (2.0 MB)  TX bytes:141451 (138.1 KB)
          Interrupt:16 Base address:0x6f80 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7169 (7.0 KB)  TX bytes:7169 (7.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:0A:0B:18:7D  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:aff:fe0b:187d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2532 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6261 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:242987 (237.2 KB)  TX bytes:591672 (577.8 KB)

In case somebody wants to know more, please ask. 

Thanks in advance again for helping me out..

---

### Post by diepruis on 2007-12-01
Hi Tim!

From this output you can see that your RT73 device is called "wlan0":

> **TimH1980 said:**
> This is the output with iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT73 WLAN  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


But in your /etc/network/interfaces...

> **TimH1980 said:**
> 
# The loopback network interface
auto lo
iface lo inet loopback



iface eth1 inet dhcp
wireless-key AAF6E465A43E5826CC5A9ADD12
wireless-essid Livebox-dv5d

auto eth1

auto wlan0
iface wlan0 inet dhcp


...you placed the wireless configuration options under eth1. These need to be under wlan0, as well as some other options specified in the howto.

---

### Post by TimH1980 on 2007-12-01
Thanks Diepruis!

Yesterday with keep on trying I solved the problem. 

I loaded the rt73 driver in my ndisgtk and than after giving it a static IP address it worked!

I think why it didn't work before was because I didn't blacklist the driver but I'm not sure anymore. 

Thanks for posting and help!

---

### Post by diepruis on 2007-12-01
> **TimH1980 said:**
> Thanks Diepruis!

Yesterday with keep on trying I solved the problem. 

I loaded the rt73 driver in my ndisgtk and than after giving it a static IP address it worked!

I think why it didn't work before was because I didn't blacklist the driver but I'm not sure anymore. 

Thanks for posting and help!

Mmmm... ndisgtk is a graphical front end to ndiswrapper, which loads Windows drivers and makes them work on Linux systems.

The driver described in this howto is a native one. In theory you don't need ndiswrapper for this device. If it works for you, great, but if it starts giving you problems you may want to give the native driver another shot.

---

### Post by TimH1980 on 2007-12-02
So far no problems. Only problem now is my soundcard.. 

But internet works flawlessly. Overall very satisfied with Ubuntu Studio. If everything works I'll kick Windows of my computer ;-)

But if my internet is doing weird than I'll do the tutorial again!

---

### Post by Prestwick on 2007-12-02
Using a Belkin USB Dongle (F5D7050) on a Dell Vostro 1000 laptop and it worked first time. Turned off the Broadcom on board wi-fi and am using this instead now! Cheers diepruis!

Should I periodically update to the latest release via CVS by the way?

---

### Post by diepruis on 2007-12-03
> **Prestwick said:**
> Using a Belkin USB Dongle (F5D7050) on a Dell Vostro 1000 laptop and it worked first time. Turned off the Broadcom on board wi-fi and am using this instead now! Cheers diepruis!

Should I periodically update to the latest release via CVS by the way?

That's not necessary. As long as it continues working for you, leave it alone! =D

---

### Post by Austin_KW on 2007-12-03
> **diepruis said:**
> That's not necessary. As long as it continues working for you, leave it alone! =D

But you will have to **make** and **make install** after any kernel updates
/a

---

### Post by diepruis on 2007-12-03
> **Austin_KW said:**
> But you will have to **make** and **make install** after any kernel updates
/a

True.

---

### Post by nyex on 2007-12-03
yikes!

i followed the tutorial and everything seemed ok.
only it didn't quite work.

here's what happened in the final step:


olivia@olivia-laptop:~$ sudo ifconfig wlan0 up
olivia@olivia-laptop:~$ sudo iwconfig wlan0 essid cultcoolfreak
olivia@olivia-laptop:~$ sudo iwconfig wlan0 key s:key
olivia@olivia-laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:19:db:0e:b8:fb
Sending on   LPF/wlan0/00:19:db:0e:b8:fb
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


and then whichever could be useful for solving the problem:


olivia@olivia-laptop:~$ ifconfig
lo         Encapsulamento do Link: Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:152 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:152 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:13456 (13.1 KB) TX bytes:13456 (13.1 KB)

wlan0      Encapsulamento do Link: Ethernet  Endereço de HW 00:19:DB:0E:B8:FB  
          endereço inet6: fe80::219:dbff:fe0e:b8fb/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

wlan0:ava  Encapsulamento do Link: Ethernet  Endereço de HW 00:19:DB:0E:B8:FB  
          inet end.: 169.254.9.193  Bcast:169.254.255.255  Masc:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1


olivia@olivia-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT73 WLAN  ESSID:"cultcoolfreak"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


olivia@olivia-laptop:~$ lsmod | grep 'rt'
parport_pc             37412  0 
parport                37448  3 ppdev,parport_pc,lp
rt73                  214912  0 
iTCO_vendor_support     4868  1 iTCO_wdt
agpgart                35016  3 drm,intel_agp
usbcore               138632  6 usb_storage,libusual,rt73,ehci_hcd,uhci_hcd


and /etc/network/interfaces:

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
        pre-up ifconfig wlan0 up
        pre-up iwconfig wlan0 essid cultcoolfreak
        pre-up iwconfig wlan0 key s:key


it's a simple WEP key. it was everything working with the rt73usb driver, but it would die every once in a while and then i had to reboot to get it up again, so i decided to try this.

any clues? i'd be very grateful :)

---

### Post by diepruis on 2007-12-03
> **nyex said:**
> any clues? i'd be very grateful :)

What does
```

iwlist wlan0 scan

```
report?

Have you tried associating with WEP turned off in the router?

---

### Post by nyex on 2007-12-03
gah!

result:

```
wlan0       No scan results
```

---

### Post by nyex on 2007-12-03
and turning off WEP didn't do no good :(

---

### Post by nyex on 2007-12-03
if nothing goes right anyway, how do i get back to using rt73usb?

---

### Post by nyex on 2007-12-03
diepruis, i loaded rt73usb again and blacklisted rt73. it'll probably be terrible and dying all over again, but at least it gives me some time of internet when i don't try any heavy downloading.

either way, if you have any clue as to what could be my problem, i'd appreciate it :)

---

### Post by diepruis on 2007-12-03
> **nyex said:**
> diepruis, i loaded rt73usb again and blacklisted rt73. it'll probably be terrible and dying all over again, but at least it gives me some time of internet when i don't try any heavy downloading.

either way, if you have any clue as to what could be my problem, i'd appreciate it :)

Mmmm... not sure what your problem could be. Your device is obviously RT73 and there's cleary no error in the router setup, since rt73usb can associate.

It could be that your device is bugged with rt73, but not with rt73usb. Perhaps you should check rt2x00.serialmonkey.com to see if there's a bug report filed for rt73 and your device.

You might also want to check whether moving the router closer helps, as you might get a weaker signal with the rt73 driver. I doubt this will do any good, though.

One last thing: you might want to check dmesg and syslog with rt73 loaded and trying to associate, although you'll have to recompile in debug mode to get any information out of the module.

Other than that, I'm pretty blank as to what can cause this.

---

### Post by blackaardvark on 2007-12-05
Hi guys. 

Your guide helped me last time so I'm back again. I had this driver working with Feisty for my USB Belkin device and now it's refusing to work with Gutsy.  
It took me ages to get working in the first place so could someone tell me how to wipe all previous settings/interfaces/blacklists etc. from my setup so I can start from scratch? I'm hesitant to start deleting things as you probably can understand.  
Maybe I could show you my interface/modprobe results? A guideline to whats required for debugging the problem would be helpful in the first entry btw.  I'm sending this off a windows PC so I'll return with all the output some time in the near future.

Thanks!

---

### Post by nyex on 2007-12-05
ham.
yep, no idea either. anything that involves recompiling (or compiling, anyway), is too much for me. i'm back at rt73usb, and luckly it hasn't died on me again yet. if the issue only happens every once in a while, i guess i can deal with it, until they fix it (or so i hope).

thanks anyway :)
i'll take a look at what you said, just to be sure.

---

### Post by paxmaniac on 2007-12-06
> **nyex said:**
> ham.
yep, no idea either. anything that involves recompiling (or compiling, anyway), is too much for me. i'm back at rt73usb, and luckly it hasn't died on me again yet. if the issue only happens every once in a while, i guess i can deal with it, until they fix it (or so i hope).

thanks anyway :)
i'll take a look at what you said, just to be sure.

I have exactly the same issue as you.  My card is a TP-Link TL-WN321G usb dongle, which has the same Ralink chipset as yours I think.

rt73usb works (as long as rt2500usb is blacklisted), but every now and then stops working.  I will post the kernel messages next time it happens.  When it stops, I cannot get it working again despite unloading and reloading modules or removing (which sometimes freezes the system completely) and reinserting the dongle.

I'm a bit frustrated, as I bought this device specifically because of the Linux support.

I cannot get rt73 working - same issue as nyex (card is recognized but cannot scan or connect).  ndiswrapper also fails (can scan but cannot connect).

All of this is with security off, so that's not the issue.

---

### Post by diepruis on 2007-12-06
> **paxmaniac said:**
> I have exactly the same issue as you.  My card is a TP-Link TL-WN321G usb dongle, which has the same Ralink chipset as yours I think.

rt73usb works (as long as rt2500usb is blacklisted), but every now and then stops working.  I will post the kernel messages next time it happens.  When it stops, I cannot get it working again despite unloading and reloading modules or removing (which sometimes freezes the system completely) and reinserting the dongle.

I'm a bit frustrated, as I bought this device specifically because of the Linux support.

I cannot get rt73 working - same issue as nyex (card is recognized but cannot scan or connect).  ndiswrapper also fails (can scan but cannot connect).

All of this is with security off, so that's not the issue.

This is starting to look more and more like an issue with the driver, rather than the installation. I'd advise you guys to head over to [http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com") and try your luck there.

Sorry I can't be more help :(

---

### Post by paxmaniac on 2007-12-06
> **diepruis said:**
> This is starting to look more and more like an issue with the driver, rather than the installation. I'd advise you guys to head over to [http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com") and try your luck there.

Sorry I can't be more help :(

Fair enough.  For the record, my kernel errors are:

[ 6464.748554] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 6464.848442] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[ 6468.544557] phy0 -> rt73usb_bbp_write: Error - PHY_CSR3 register busy. Write failed.

rinse and repeat with various offsets

---

### Post by diepruis on 2007-12-06
> **paxmaniac said:**
> Fair enough.  For the record, my kernel errors are:

[ 6464.748554] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 6464.848442] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[ 6468.544557] phy0 -> rt73usb_bbp_write: Error - PHY_CSR3 register busy. Write failed.

rinse and repeat with various offsets

You should double check that you have the right driver (if rt73usb works, that's enought) and then give this information to the driver's developer's.

---

### Post by Austin_KW on 2007-12-06
> **paxmaniac said:**
> Fair enough.  For the record, my kernel errors are:

[ 6464.748554] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 6464.848442] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[ 6468.544557] phy0 -> rt73usb_bbp_write: Error - PHY_CSR3 register busy. Write failed.

rinse and repeat with various offsets

Seen those errors somewhere before, ?wrong driver?.
Have you got the other rt2500usb driver blacklisted ?

---

### Post by paxmaniac on 2007-12-07
> **Austin_KW said:**
> Seen those errors somewhere before, ?wrong driver?.
Have you got the other rt2500usb driver blacklisted ?

Well the driver works fine for quite extended periods, so I don't think it's the wrong driver.  Yes, rt2500usb is blacklisted.  I agree it's almost certainly a driver issue - will check there for similar.

---

### Post by diepruis on 2007-12-07
> **paxmaniac said:**
> Well the driver works fine for quite extended periods, so I don't think it's the wrong driver.  Yes, rt2500usb is blacklisted.  I agree it's almost certainly a driver issue - will check there for similar.

At first glance I'd point the finger at concurrency issues.

---

### Post by panchofmx on 2007-12-18
> **paxmaniac said:**
> Fair enough.  For the record, my kernel errors are:

[ 6464.748554] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
[ 6464.848442] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
[ 6468.544557] phy0 -> rt73usb_bbp_write: Error - PHY_CSR3 register busy. Write failed.

rinse and repeat with various offsets


i got the same problem... on my ibook 3g powerpc runing gutsy

disconnect some time. i realy think the problem is the driver rt73usb on the kernel of gutsy
I will try the driver from  [http://homepages.tu-darmstadt.de/~p_larbig/wlan/](http://homepages.tu-darmstadt.de/~p_larbig/wlan/)  (also this driver it work good with aircrack)
I will have to blacklist the old Module. i hope it work.

my other option is update to the last kernel at kernel.org that will do it for sure. ( to update kernel automatic go to [http://ubuntuforums.org/showthread.php?t=618563](http://ubuntuforums.org/showthread.php?t=618563)  download kernelcheck to update.

that is my last option.

---

### Post by dannyboy79 on 2007-12-19
you guys all state the the rt73 from serialmonkey isn't working. Have you tried the older rt73 that I attached  pages back? I know when I went from Feisty to Gutsy on my machine, I had to reuse an older downloaded version of the rt73 driver because the one at serialmonkey would NOT work. I'll have posted the link to the thread where I attached the tarball of the rt73 driver that does work for me. I am running Mythbuntu which is based on Gutsy so it should work for you. As long as you follow the guide in the begining and use this tarball, it should work if you have the same WIFI chip as me. Which is the Belkin F5D7050 with the rt2571wf wifi chip inside if you split it open.

[http://ubuntuforums.org/showthread.php?t=400236&page=75](http://ubuntuforums.org/showthread.php?t=400236&page=75)

---

### Post by diepruis on 2007-12-22
> **dannyboy79 said:**
> you guys all state the the rt73 from serialmonkey isn't working. Have you tried the older rt73 that I attached  pages back? I know when I went from Feisty to Gutsy on my machine, I had to reuse an older downloaded version of the rt73 driver because the one at serialmonkey would NOT work. I'll have posted the link to the thread where I attached the tarball of the rt73 driver that does work for me. I am running Mythbuntu which is based on Gutsy so it should work for you. As long as you follow the guide in the begining and use this tarball, it should work if you have the same WIFI chip as me. Which is the Belkin F5D7050 with the rt2571wf wifi chip inside if you split it open.

[http://ubuntuforums.org/showthread.php?t=400236&page=75](http://ubuntuforums.org/showthread.php?t=400236&page=75)

A general piece of advice: if a specific version doesn't work for you, you can always report the problem on rt2x00.serialmonkey.com and hope they fix it (if we can't).

Downloading a newer version of the beta a few days later might also fix your problems.

---

### Post by dannyboy79 on 2007-12-22
i'd rather stick with what I know works then mess around with newer downloads that haven't worked in the past. Hence why I uploaded the version of the rt73 that works and compiles on gutsy.

---

### Post by helenuh on 2007-12-23
Thanks so much diepruis, this helped me a lot :)

---

### Post by diepruis on 2007-12-23
> **dannyboy79 said:**
> i'd rather stick with what I know works then mess around with newer downloads that haven't worked in the past. Hence why I uploaded the version of the rt73 that works and compiles on gutsy.

That's true... but my post was meant to be general advice for the people that might have problems with *that* version.

---

### Post by Ganesh.Puri on 2007-12-25
This driver works with my new C54RU Stick on a freshly downloaded and installed Gutsy. Without this driver the network connection kept crashing.

---

### Post by dannyboy79 on 2007-12-26
> **diepruis said:**
> That's true... but my post was meant to be general advice for the people that might have problems with *that* version.

uh? I thought this guide was created because the drivers in ubuntu aren't working properly and you need to download the drivers from serialmonkey website and compile them? Now you're saying that the guide wasn't for that at all? I am a little confused. The actual title states, "RT73", so how can you say that the guide was created for people who are having problems with the RT73?

Regardless, the rt73 that I attached works with WEP in Gutsy and Feisty. Those that can't get the default rt73usb driver provided with Ubuntu, give the one I uploaded a try.

---

### Post by dynamethod on 2007-12-26
im getting this alot with my rt73 driver and dynalink usb adapter:

kernel: [34871.283621] ERROR!!! <7>RTUSBHardTransmit: TX RING full

alot.

---

### Post by diepruis on 2007-12-27
> **dannyboy79 said:**
> uh? I thought this guide was created because the drivers in ubuntu aren't working properly and you need to download the drivers from serialmonkey website and compile them? Now you're saying that the guide wasn't for that at all? I am a little confused. The actual title states, "RT73", so how can you say that the guide was created for people who are having problems with the RT73?

Regardless, the rt73 that I attached works with WEP in Gutsy and Feisty. Those that can't get the default rt73usb driver provided with Ubuntu, give the one I uploaded a try.

Yes, I'd recommend people give that one a try. But if that doesn't work either, try a newer vrsion.

Of course the guide was for people having trouble with the rt2x00 driver... But the thread also deals with support questions regarding the installation of rt73 detailed in the original howto.

---

### Post by art_beyond_entertainment on 2007-12-27
Hello,
        I have waded through 88 pages of this thread and I'm still at a loss on what to do.

I have followed the how-to step-by-step and I can connect to the internet, but only for a couple minutes.  I heard that issues like this are related to conflicting drivers, but i don't believe this is the problem, as you will see from the files I attach.

Rebooting does nothing, unplugging and plugging does nothing.  sudo ifup --f wlan0 does nothing.
I have to manually type in the sudo iwpriv wlan0 set .....  to get it to work for a couple minutes.

I'm running Ubuntu Studio 64-bit edition w/ a 2.6.22.14-rt kernel.

Here's all the information I think could possibly help: (PART I)

Please, if anyone could possibly help, I'm at my wit's end.

---

### Post by art_beyond_entertainment on 2007-12-27
the other files:

---

### Post by dannyboy79 on 2007-12-27
have you tried uninstalling network-manager? iwconfig, it only shows eth0? there should be a wlan0 there if you have the rt73 working. Is that what driver you're using? What type of wifi chip does your adapter have in it What is the manufacturer of your wifi adapter?

Have you tried following the guide word for word BUT using the rt73 tarball I have uploaded a few pages back? that's if you're chipset within the wifi adapter is the 2571wf. It should say it right on the chip if you open the wifi adapter.

---

### Post by art_beyond_entertainment on 2007-12-27
Yes, I've tried uninstalling network-manager and network-manager-gnome

iwconfig shows a wlan0.

Yes, I'm using the rt73.

It's a Belkin ID 050d:705a

I haven't tried your tarball, might try that later

---

### Post by dannyboy79 on 2007-12-27
are you using WPA? I only use WEP 128bit Hex Key with my Belkin adapter. I beleive we have the same one but can't be confirmed unless you use a knife and pry it open (it won't break just do it very slowly) and see if the wifi chip is the 2571wf. I think that's the chip. You can search this specific thread for posts by me and read mine if that would help you.

---

### Post by art_beyond_entertainment on 2007-12-27
I opened up the adapter and, indeed, it was the 2571wf chip, so I downloaded your tarball and so far so good!

Thanks a million - i would've never guessed this was the problem.

---

### Post by dannyboy79 on 2007-12-27
> **art_beyond_entertainment said:**
> I opened up the adapter and, indeed, it was the 2571wf chip, so I downloaded your tarball and so far so good!

Thanks a million - i would've never guessed this was the problem.

glad you got it working!

---

### Post by art_beyond_entertainment on 2007-12-27
actually, it worked for a while (longer than normal) and then quit again..


*sigh*

---

### Post by dannyboy79 on 2007-12-27
what does dmesg report? or syslog

---

### Post by skoalman88 on 2007-12-27
Edimax 7318USG works perfectly with the driver posted on pg. 75. Thanks!!

---

### Post by dannyboy79 on 2007-12-27
what channel are you using also? are there many wireless networks around you?

---

### Post by art_beyond_entertainment on 2007-12-28
I'm not sure what you mean by what channel I'm using.  There aren't really any other wireless networks around I could pick up.

And I AM using WPA.

Here's my dmesg, as long as this internet still works for a few more seconds.

---

### Post by art_beyond_entertainment on 2007-12-28
HALLELUJAH!

Everything's working - to the point I even restarted it and things work.  I ended up just using the link in here to compile RutilT and that works wonders for me.

thanks for all the help, dannyboy

now I can sleep at night.

---

### Post by dannyboy79 on 2007-12-29
glad you got it working! so are you using the rt73 that I uploaded?

---

### Post by diepruis on 2007-12-30
> **art_beyond_entertainment said:**
> HALLELUJAH!

Everything's working - to the point I even restarted it and things work.  I ended up just using the link in here to compile RutilT and that works wonders for me.

thanks for all the help, dannyboy

now I can sleep at night.

What were you using to configure the interface before RutilT?

---

### Post by SingingWing on 2007-12-30
I previously used the serialmonkeys CVS download to compile a RT73 version for Feisty and it worked just fine using a USB Belkin F5D9050. This uses a RT2671F chip.

Since upgrading to Gutsy it will no longer work after a recompile. During the iwpriv wlan0 set WPAPSK= command the notebook locks up solidly needing a power reset. None of the CVS versions work including the archived version posted by Dannyboy. The result is always a locked computer whichever version is used.

I've narrowed it down to the length of key submitted to the set WPAPSK command. I supply a hex WPA2PSK key and if I reduce the length of key it no longer crashes. It doesn't work of course since the key is wrong but it no longer crashes. Almost like a string buffer overrun situation. I haven't determined the exact string length length acceptable, like if it's a WEP 26 char key for example. The hex key is exactly 64 chars long.

I think someone else here had the same symptom of a crashed PC...

Any suggestions?
-- 
Steve

---

### Post by diepruis on 2007-12-31
> **SingingWing said:**
> I previously used the serialmonkeys CVS download to compile a RT73 version for Feisty and it worked just fine using a USB Belkin F5D9050. This uses a RT2671F chip.

Since upgrading to Gutsy it will no longer work after a recompile. During the iwpriv wlan0 set WPAPSK= command the notebook locks up solidly needing a power reset. None of the CVS versions work including the archived version posted by Dannyboy. The result is always a locked computer whichever version is used.

I've narrowed it down to the length of key submitted to the set WPAPSK command. I supply a hex WPA2PSK key and if I reduce the length of key it no longer crashes. It doesn't work of course since the key is wrong but it no longer crashes. Almost like a string buffer overrun situation. I haven't determined the exact string length length acceptable, like if it's a WEP 26 char key for example. The hex key is exactly 64 chars long.

I think someone else here had the same symptom of a crashed PC...

Any suggestions?
-- 
Steve

That definitely does sound like a buffer overrun. Will you please report your findings to [http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com")?

In the meantime, you could try to use RutilT, which you will be able to find on the serialmonkey website. If you need help compiling it, please see these forums for a guide. If you cannot find one, I'll write one quickly.

---

### Post by SingingWing on 2008-01-01
Thanks Diepruis,

Using rutilt has the same result - a crash. I have established that a 58 char hex key is the point at which the iwpriv command causes a lockup.  If I get time I'll look through the wireless sources to see what changed between Feisty & Gutsy that might have a bearing.

Meanwhile I'll try & work out how to post a bug report...

Happy New Year,
-- 
Steve

---

### Post by wzwilliam on 2008-01-01
Hi everybody. I was having the same problems as nyex, that unstable but functional internet connection stuff. but since i tried the tutorial everything is working as it should, even my wireless switch which was always on, it didn't matter the position. but theres only one thing: i'm using no encryption. did anybody find a way to make it work under WPE encryption? since i mostly use my workplace network, i can't leave it open.
thanks in advance.

---

### Post by thasan on 2008-01-02
I have a D-Link DWL-122 and having some bad luck with it.  I am running 64-bit Gusty and found out that whenever I plugin DWL-122 into the usb dongle, the system freezes.  After following your instructions I was able keep the system up even after I plugin he dwl-122, but not able to connect to the Access Point.  
My interface can see the AP, but not able to connect as I am not able to run the command iwpriv with the option "set" to set the encap or key. It fails with the "unknown command set".  
What could be wrong?  How do I fix this?  


Thank you.

---

### Post by thasan on 2008-01-02
Forgot to mention that if I keep network-manager after loading rt73, I can connect to the AP by entering the values through the network config gui.  But for some reason, it looses the connection after few minutes and tries to reconnect.  When doing so, the system freezes.  So, I decided to remove the network-manager as you have mentioned at the bottom of the guide.
The only way to recover the system when it freezes with network-manager was to reboot the system.  So, keeping the network-manager was not an option for me.

Thanks

---

### Post by wzwilliam on 2008-01-02
just dropped by to say that today i set the router back to wpe encryption and it just WORKED PERFECTLY!!! :-D:-D:-D:-D:-D

thank you very much, you guys!

---

### Post by dannyboy79 on 2008-01-02
> **wzwilliam said:**
> Hi everybody. I was having the same problems as nyex, that unstable but functional internet connection stuff. but since i tried the tutorial everything is working as it should, even my wireless switch which was always on, it didn't matter the position. but theres only one thing: i'm using no encryption. did anybody find a way to make it work under WPE encryption? since i mostly use my workplace network, i can't leave it open.
thanks in advance.

i am using 128 bit WEP channel 6 with my Belkin adapter, with Mythbuntu Gutsy and it works fine. I uninstalled network manager. I am using the rt73 tarball I uploaded above or a few pages back NOT the current one from the serialmonkey website.

---

### Post by diepruis on 2008-01-02
> **SingingWing said:**
> Thanks Diepruis,

Using rutilt has the same result - a crash. I have established that a 58 char hex key is the point at which the iwpriv command causes a lockup.  If I get time I'll look through the wireless sources to see what changed between Feisty & Gutsy that might have a bearing.

Meanwhile I'll try & work out how to post a bug report...

Happy New Year,
-- 
Steve

I think the serialmonkey guys just use forum posts for those. Could be wrong though.

---

### Post by diepruis on 2008-01-02
> **thasan said:**
> I have a D-Link DWL-122 and having some bad luck with it.  I am running 64-bit Gusty and found out that whenever I plugin DWL-122 into the usb dongle, the system freezes.  After following your instructions I was able keep the system up even after I plugin he dwl-122, but not able to connect to the Access Point.  
My interface can see the AP, but not able to connect as I am not able to run the command iwpriv with the option "set" to set the encap or key. It fails with the "unknown command set".  
What could be wrong?  How do I fix this?  


Thank you.

I had the same problem. Using RutilT to configure the interface solved it for me. You can get RutilT from the serialmonkey site, and instructions should be on these forums. If you can't find a tutorial, ask me and I'll write one up.

---

### Post by dannyboy79 on 2008-01-02
> **wzwilliam said:**
> just dropped by to say that today i set the router back to wpe encryption and it just WORKED PERFECTLY!!! :-D:-D:-D:-D:-D

thank you very much, you guys!

are you talking about WPA or WEP?

---

### Post by thasan on 2008-01-02
> **diepruis said:**
> I had the same problem. Using RutilT to configure the interface solved it for me. You can get RutilT from the serialmonkey site, and instructions should be on these forums. If you can't find a tutorial, ask me and I'll write one up.

Thank you diepruis, but this utility doesn't seem to support WPA, only WEP.   I could configure the same without this utility through the command line.  Just like the example you have in the tutorial for the WEP.  The other option I have would be to switch my AP to WEP instead of WPA.  WEP is not what I want though, it is not as safe as.

---

### Post by wzwilliam on 2008-01-02
> **dannyboy79 said:**
> are you talking about WPA or WEP?

WEP 64k. using the serialmonkey drivers. when i installed the drivers, it just couldn't connect with WEP activated. then i disabled the WEP encryptio in the router and i could connect to the internet and to my network, it was last sunday. this morning, i enabled the WEP back, just for test purposes, and it connected perfectly. not to mention that it solved the wireless unstability problem. since i'm a noob to linux unfortunately i can't explain what and why happened.

---

### Post by alfre on 2008-01-03
I followed the tutorial from diepruis, but after typing sudo modprobe -v rt73 in step 12 my computer does not react. Therefore in step 13 the hardware was not detected. How can I solve this?

---

### Post by dannyboy79 on 2008-01-03
> **alfre said:**
> I followed the tutorial from diepruis, but after typing sudo modprobe -v rt73 in step 12 my computer does not react. Therefore in step 13 the hardware was not detected. How can I solve this?

please post the output of 

lsusb

so we can see what usb wifi adapter you're using. or if it's a pci wifi card, type this

lspci

and paste the output from the commands. also, are you positive that you're following the guide to a "T"?

---

### Post by alfre on 2008-01-03
wasmann@wasmann-laptop:~$ lsusb
Bus 002 Device 005: ID 04b4:0033 Cypress Semiconductor Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. 
Bus 001 Device 001: ID 0000:0000  

wasmann@wasmann-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
08:0a.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:0a.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
08:0a.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
08:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
wasmann@wasmann-laptop:~$

---

### Post by dannyboy79 on 2008-01-03
well with that exact chipset usb adapter, here's a bug report and some solutions which allow you to use the default ubuntu provided modules but some changes need to be made. just read the bug report. good luck

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/139070](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/139070)

---

### Post by diepruis on 2008-01-03
> **dannyboy79 said:**
> well with that exact chipset usb adapter, here's a bug report and some solutions which allow you to use the default ubuntu provided modules but some changes need to be made. just read the bug report. good luck

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/139070](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/139070)

Interesting... does that workaround work for anyone here?

---

### Post by dannyboy79 on 2008-01-03
i have no idea.

---

### Post by art_beyond_entertainment on 2008-01-05
Sorry that it took so long to get around to this.

> **dannyboy79 said:**
> glad you got it working! so are you using the rt73 that I uploaded?

Yes, I am.

> **diepruis said:**
> What were you using to configure the interface before RutilT?

I'm not sure that I even know the answer to that question....  I suppose it would be... nothing?  The System>Admin>Network deal never seemed to work for me, though I thought that's what we were trying to avoid in the first place.

Not sure if this helps.

---

### Post by diepruis on 2008-01-06
> **art_beyond_entertainment said:**
> I'm not sure that I even know the answer to that question....  I suppose it would be... nothing?  The System>Admin>Network deal never seemed to work for me, though I thought that's what we were trying to avoid in the first place.

Not sure if this helps.

Sorry, looked through your previous posts, I understand now that you were using iwconfig + iwpriv. Thanks :)

---

### Post by RostokMcSpoons on 2008-01-06
Hi, I'm having 'fun' with my TP-Link WN321G.

It's worked for a bit, but I restarted to see if my changes to the Interfaces file have taken, and now it doesn't work, even if I redo the steps manually.   The only thing I think is different is on the first go I did this:

disabled WEP on the router.
got connection.
re-enabled WEP
sudo iwconfig wlan0 key ec3ed....etc
still got connection.

after the reboot I left WEP on.
I've tried changing the case of the wep key, but it doesn't help.

the router shows my pc, but says it's 'inactive'.  
I've tried cycling it up and down, but the problem is that I can't successfully 'dhclient'.  

As I'm a noob I'm pleased to have got this far, but it's late and I'm stuck :(  Any assistance gratefully received!

edit: as I'm sure someone would ask me to, I disabled WEP on the router, and I still can't get my connection to work again :(

---

### Post by diepruis on 2008-01-07
> **RostokMcSpoons said:**
> Hi, I'm having 'fun' with my TP-Link WN321G.

It's worked for a bit, but I restarted to see if my changes to the Interfaces file have taken, and now it doesn't work, even if I redo the steps manually.   The only thing I think is different is on the first go I did this:

disabled WEP on the router.
got connection.
re-enabled WEP
sudo iwconfig wlan0 key ec3ed....etc
still got connection.

after the reboot I left WEP on.
I've tried changing the case of the wep key, but it doesn't help.

the router shows my pc, but says it's 'inactive'.  
I've tried cycling it up and down, but the problem is that I can't successfully 'dhclient'.  

As I'm a noob I'm pleased to have got this far, but it's late and I'm stuck :(  Any assistance gratefully received!

edit: as I'm sure someone would ask me to, I disabled WEP on the router, and I still can't get my connection to work again :(

What's the output of ```
lsmod | grep rt
```?

---

### Post by RostokMcSpoons on 2008-01-07
> **diepruis said:**
> What's the output of ```
lsmod | grep rt
```?


I'm at work right now, so I can't post the exact stuff, but I've got it down to rt73 if I grep rt, or un-grepped it's rt73 plus some others... so I've managed to unload all the other rt2500 / rt2x00 / rt73usb modules that conflict.  (I've not managed to get it to do that automatically when I reboot yet.. but that request for help is in another thread!)

---

### Post by diepruis on 2008-01-07
> **RostokMcSpoons said:**
> I'm at work right now, so I can't post the exact stuff, but I've got it down to rt73 if I grep rt, or un-grepped it's rt73 plus some others... so I've managed to unload all the other rt2500 / rt2x00 / rt73usb modules that conflict.  (I've not managed to get it to do that automatically when I reboot yet.. but that request for help is in another thread!)

Sorry... forgot to ask, but could you also post
```

lsmod | grep usbcore

```
It's possible that some additional modules are conflicting that I've neglected to mention in the guide. There are a couple of modules that don't play well with rt73.

---

### Post by RostokMcSpoons on 2008-01-07
> **diepruis said:**
> 
It's possible that some additional modules are conflicting that I've neglected to mention in the guide. There are a couple of modules that don't play well with rt73.

Right... here are the modules loaded for usbcore:

rt73
usbhid
ehci_hcd
ohci_hcd

In my /etc/interfaces file I have this:

auto wlan0
iface wlan0 inet dhcp
wireless-key ec3ed595c4
wireless-essid RossLinuxPC
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid RossLinuxPC
pre-up iwconfig wlan0 key ec3ed...etc

tbh I think I've learnt just enough to confuse myself... I'm going around in cycles of ifconfig wlan0 down/up, trying to set the WEP key so it shows in ifconfig or iwconfig (which it's now refusing to do.. I'm trying 
sudo iwconfig wlan0 key ec3ed...
sudo iwconfig wlan0 key "ec3ed..."
sudo iwconfig wlan0 key EC3ED...
sudo iwconfig wlan0 key "EC3ED..."
...all to no avail)

I need some expert hand-holding :(

---

### Post by dannyboy79 on 2008-01-07
> **RostokMcSpoons said:**
> Right... here are the modules loaded for usbcore:

rt73
usbhid
ehci_hcd
ohci_hcd

In my /etc/interfaces file I have this:

auto wlan0
iface wlan0 inet dhcp
wireless-key ec3ed595c4
wireless-essid RossLinuxPC
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid RossLinuxPC
pre-up iwconfig wlan0 key ec3ed...etc

tbh I think I've learnt just enough to confuse myself... I'm going around in cycles of ifconfig wlan0 down/up, trying to set the WEP key so it shows in ifconfig or iwconfig (which it's now refusing to do.. I'm trying 
sudo iwconfig wlan0 key ec3ed...
sudo iwconfig wlan0 key "ec3ed..."
sudo iwconfig wlan0 key EC3ED...
sudo iwconfig wlan0 key "EC3ED..."
...all to no avail)

I need some expert hand-holding :(

this is what my interfaces file looks like for my 128bit WEP key using a static ip address using the rt73 module that I uploaded awhile back.

auto wlan0
iface wlan0 inet static
address 192.168.0.6
netmask 255.255.255.0
network 192.168.0.1
gateway 192.168.0.1
        pre-up ifconfig wlan0 up
        pre-up iwconfig wlan0 essid DRAWN
        pre-up iwconfig wlan0 mode Managed
        pre-up iwconfig wlan0 key ce6cXXXXXXXXXXXXXXXXXXXXXX

NOTE: X's equal my key which I am not going to show here. he he 

as you can see 128bit WEP uses 26 hex key, you only have 10? Are you using 40bit or 64bit? or is there a difference? SHouldn't it have 13 characters versus 10?

---

### Post by Austin_KW on 2008-01-07
Try removing 
```
wireless-key ec3ed595c4
wireless-essid RossLinuxPC
```

Save the changes to interfaces file and run "sudo ifup --f wlan0"

64 bit key is actually 40 bit (24 bit Init Vector) So 10 hex digits or 5 axcii chars is correct.

---

### Post by RostokMcSpoons on 2008-01-07
It's just hacker-friendly 64bit, 10 char key at the moment ;)   When I get the thing working consistently at that level, then I'll try and step up the security.

What's so annoying is that the darned thing *did* work for a bit.  I even saved a big chunk of my Terminal window to a text file so I could go through the same steps again... but now it doesn't work :(

I am wondering if I've got a conflict with my first attempt to load the drivers - I followed another thread's advice and tried to install into /usr/lib/     Should I delete the directory in there?  Or should I just scrap the whole install and try again? (That's seems a bit drastic - if everytime I make a mistake I have to scrap it, then me and Linux ain't going to get along...)

---

### Post by RostokMcSpoons on 2008-01-07
> **Austin_KW said:**
> Try removing 
```
wireless-key ec3ed595c4
wireless-essid RossLinuxPC
```

Save the changes to interfaces file and run "sudo ifup --f wlan0"

64 bit key is actually 40 bit (24 bit Init Vector) So 10 hex digits or 5 axcii chars is correct.

lol   so much for my attempt to hide my Wep key :)  <sob>



edit:  regarding an earlier post - my router is already set to 802.11b/g

edit2: I've followed those instructions, and also managed to get the WEP key show up in iwconfig, but still I get 'No DHCPOFFERS received' :(

---

### Post by amic on 2008-01-16
I was originally going to start a new thread, but I figured I'd post here first. Let me give you all some background. This is my second attempt to migrate from Windows to Linux and so far I haven't booted into Windows in a few weeks. I've got just about everything working perfectly, and have a virtualbox installation of Windows setup for the things I *must* run in windows (my poker software and adobe photoshop mainly). 

This is a fresh install of 7.10 64-bit
My wireless was working pretty well out of the box w/ network manager, but as time went on and after some software updates my wireless seemed to be getting less and less stable. I was dropping quite often (4/5 bars to 0) and to reconnected I'd have to unplug my wireless card (Linksys WUSB54GC) and plug it back in, and reconnect to my router. Eventually it got to the point where I was spending more time attempting to reconnect than I was using my computer.

I turned to this thread, followed the instructions and everything went flawlessly (using the WPA configuration). I also removed networkmanager as instructed (I dislike this however because I no longer have a visual monitor on my toolbar to show me my connection status/strength)

Here's the problem:
Everytime I boot up I need to open up the terminal and re-enter the iwpriv commands (authmode, encryptype, wpapsk, ssid and networktype) and then do "sudo dhclient wlan0". This'll work for a while but my connection will still drop in a seemingly random fashion, and I'll have to reissue the "dhclient wlan0" command again to gain connectivity, and sometimes, I'll even have to reissue the iwpriv commands beforehand, as if I'm just booting up.

Any suggestions to the issues of: dropping, re-entering all the commands, and some sort of replacement for a visual monitor on my toolbar would be appreciated. (But the dropping is obviously the most pressing issue.)

Thank you very much, in advance

---

### Post by skruffer on 2008-01-17
I follow the instructions all the way to number 6, and then i get this message:

Please insert the disc labeled 'Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)' in the drive '/cdrom/' and press [Enter].

I've searched the forums for this message, but it seems i'm the only one getting it...
I'm rather new to Linux (Kubuntu), so be gentle with me :P

---

### Post by lswest on 2008-01-17
well, what the error message is asking you for is for you to insert the kubuntu cd you have, and to hit enter to have it continue working.  however, since this is an aptitude/apt-get attempt, be sure to check your repositories so that the cdrom repo is no longer checked (i'd tell you how to do it, but i'm not a kde man)

---

### Post by dannyboy79 on 2008-01-17
> **lswest said:**
> well, what the error message is asking you for is for you to insert the kubuntu cd you have, and to hit enter to have it continue working.  however, since this is an aptitude/apt-get attempt, be sure to check your repositories so that the cdrom repo is no longer checked (i'd tell you how to do it, but i'm not a kde man)

and that you have internet access of course, without that, the packages it's trying to install can't get installed.

---

### Post by dannyboy79 on 2008-01-17
> **amic said:**
> 

Thank you very much, in advance 

have you edited the /etc/network/interfaces file and saved it?

---

### Post by frvo on 2008-01-17
The perfection in a HOWTO for anybody and specially like me who I've been workin with ubuntu and linux in general for 3 months. Every line is perfect and everything worked flawlessly. Thank you and sorry about my english.

---

### Post by kanhh on 2008-01-17
Hey, I have a problem on gutsy with these drivers! I can connect to the router (I can access it through 10.0.0.1), but it wont connect to the internet! on windows it can, so is not a problem of the router (i guess!).
below is some info:

**iwconfig** and** ifconfig**

> 
kan@kan:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT73 WLAN  ESSID:"227-6E"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:80:5A:37:0A:07   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=74/100  Signal level:-65 dBm  Noise level:-99 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

kan@kan:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2296 (2.2 KB)  TX bytes:2296 (2.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:85:37:8B:03  
          inet addr:10.0.0.3  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::214:85ff:fe37:8b03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1910 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:299981 (292.9 KB)  TX bytes:140126 (136.8 KB)

**/etc/network/interfaces**

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-key blablabla
wireless-essid blabla

thanks

---

### Post by Austin_KW on 2008-01-17
> **kanhh said:**
> Hey, I have a problem on gutsy with these drivers! I can connect to the router (I can access it through 10.0.0.1), but it wont connect to the internet! on windows it can, so is not a problem of the router (i guess!).
below is some info:
...
thanks

post the output of the commands
```
cat /etc/resolv.conf
route

```

---

### Post by amic on 2008-01-17
> **dannyboy79 said:**
> have you edited the /etc/network/interfaces file and saved it?

yes i have

---

### Post by amic on 2008-01-17
it seems to just be an issue where i'll get dropped and i'll have to re-enter only the "iwpriv ... WPAPSK=*" part and then do "dhclient wlan0" and my i'll get bound w/ renewal in 34,795 seconds.  Unfortunately my connection never makes it that long...

---

### Post by kanhh on 2008-01-17
> **Austin_KW said:**
> post the output of the commands
```
cat /etc/resolv.conf
route

```

Here they are!:

> 
kan@kan:~$ cat /etc/resolv.conf
nameserver 10.0.0.1

kan@kan:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     1000   0        0 wlan0
10.0.0.0        *               255.0.0.0       U     0      0        0 wlan0
default         mygateway1.ar7  0.0.0.0         UG    100    0        0 wlan0


thnks

---

### Post by Austin_KW on 2008-01-17
> **kanhh said:**
> Here they are!:



thnks

That looks right assuming mygateway1.ar7 is 10.0.0.1
verify with "route -n"

also check for dns problems with 
```

ping -c3 64.233.187.99
    AND
ping -c3 google.com

```

---

### Post by amic on 2008-01-17
Any assistance please? Or am I just a doomed statistic :confused:

---

### Post by mr297 on 2008-01-17
Thanks! This guide has been an absolute life saver for me.

---

### Post by kanhh on 2008-01-17
> **Austin_KW said:**
> That looks right assuming mygateway1.ar7 is 10.0.0.1
verify with "route -n"

also check for dns problems with 
```

ping -c3 64.233.187.99
    AND
ping -c3 google.com

```

mygateway1.ar7 actually is 10.0.0.1 but...
I took your advice and I (think) found that something with DNS is not working...take a look!:

> 
kan@kan:~$ ping -c3 64.233.197.99
PING 64.233.197.99 (64.233.197.99) 56(84) bytes of data.

--- 64.233.197.99 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms


kan@kan:~$ ping -c3 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (66.102.9.104) 56(84) bytes of data.
64 bytes from [www.google.com](www.google.com) (66.102.9.104): icmp_seq=1 ttl=240 time=124 ms
64 bytes from [www.google.com](www.google.com) (66.102.9.104): icmp_seq=2 ttl=240 time=117 ms
64 bytes from [www.google.com](www.google.com) (66.102.9.104): icmp_seq=3 ttl=240 time=119 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 117.979/120.738/124.655/2.859 ms

in firefox is the opposite, i can connect to 64.233.197.99 but not to google. how can I "fix" it?
thanks

---

### Post by Austin_KW on 2008-01-17
kanhh  
Typo in you ping, Try ping -c3 64.233.**187**.99
Seems like you are connected OK

I still think it is a DNS issue;
In firefox turn off ipv6 for dns, Sometimes cause resolving problems;
in the ulr type **about:config**
in the filter type **ipv6**
make sure it is disable = true; Changes when you double click on the value.

---

### Post by kanhh on 2008-01-17
It's working now! I'm figuring out how I can fix this in the whole system, I've seen some threads about disabling ipv6 but none worked :( Anyway, I really appreciated your help, thanks a lot!

---

### Post by diepruis on 2008-01-18
> **amic said:**
> it seems to just be an issue where i'll get dropped and i'll have to re-enter only the "iwpriv ... WPAPSK=*" part and then do "dhclient wlan0" and my i'll get bound w/ renewal in 34,795 seconds.  Unfortunately my connection never makes it that long...

I think this is a hardware issue, you might want to try serialmonkey's website and file a bug report there. They'll be able to tell you how to debug the driver itself, as I don't think this is an issue with the installation. However, just to be safe, what is the output of
```

lsmod | grep usbcore

```
?

---

### Post by rodica.balasa on 2008-01-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/62535](https://bugs.launchpad.net/bugs/62535) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I managed to make the edimax drivers to work, here is the howto:

[URL="http://www.len.ro/work/tools/old-new-i8000-2"]http://www.len.ro/work/tools/old-new-i8000-2
[/URL]

---

### Post by amic on 2008-01-18
> **diepruis said:**
> I think this is a hardware issue, you might want to try serialmonkey's website and file a bug report there. They'll be able to tell you how to debug the driver itself, as I don't think this is an issue with the installation. However, just to be safe, what is the output of
```

lsmod | grep usbcore

```
?

lsmod | grep usbcore
usbcore               161584  7 rt73,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd

Thanks for the assistance

---

### Post by diepruis on 2008-01-19
> **amic said:**
> lsmod | grep usbcore
usbcore               161584  7 rt73,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd

Thanks for the assistance

Mmmm... okay, I would like to try a debug run on the module itself. Could you go back to the /usr/src/rt73-cvs-yyyymmdd/Module directory and issue the following commands?

```

sudo make clean
sudo make debug
sudo ifconfig wlan0 down
sudo rmmod rt73
sudo insmod rt73.ko debug=31

```

Then configure your interface as usual. As soon as it goes down again, please post /var/log/syslog here (**attach** the file please, don't paste it's contents into the post window).

---

### Post by martin_n_c on 2008-01-19
Just a couple of points that might help people here (depending on their setup):

1) I'm using an Edimax EW-7318UG USB dongle, and this thread's howto worked fine for me in Feisty (7.04). When I did a fresh install of Gutsy (7.10), though, the network connected  *almost*  out of the box. There was no need to compile any drivers. I followed the simple instructions here:
[http://www.lockergnome.com/linux/2007/11/04/ubuntu-gutsy-with-expresscard-working-options/]("http://www.lockergnome.com/linux/2007/11/04/ubuntu-gutsy-with-expresscard-working-options/")
on Matt Hartley's post for January 10, 2008 @ 4:38 pm (not the main tutorial instructions at the top of the page). The script he refers to in step 3 is towards the top of the page, just under the YouTube video. Look for a link called  'rt73usb-wifi'.

2) I'm on a dual boot, with Gutsy in one half and Windows XP (SP2) in the other. When I reboot from Windows XP to Ubuntu, it blocks my internet connection. Network Manager says I'm connected but Firefox times out. The only solution is to unplug and replug my wireless usb. Bringing down the network and bringing it up again from the terminal doesn't work - I have to unplug the hardware. If I *shut down* from Windows and boot up in Ubuntu, NM says I've got no internet connection. Once again, unplugging and replugging the dongle fixes this. 

The curious thing is that if I restart or boot up from Ubuntu to Ubunto there's no problem at all. The internet connection is made straightaway. I wonder if the Windows connection is leaving some residual state in my hardware. It seems to be time-dependent, whatever it is. If I shut down Windows at night and fire up Ubuntu next day there's no problem.

Looking back on it, I think this caused me frustration when I followed this thread's howto, because I only had an internet connection in Windows and was rebooting from Windows all the time! I couldn't understand why sometimes the connection was working and sometimes it wasn't.

By the way, diepruis: still helping people after 95 pages - that's really kind of you. Glad people appreciate what you're doing here :)

---

### Post by amic on 2008-01-19
> **diepruis said:**
> Mmmm... okay, I would like to try a debug run on the module itself. Could you go back to the /usr/src/rt73-cvs-yyyymmdd/Module directory and issue the following commands?

```

sudo make clean
sudo make debug
sudo ifconfig wlan0 down
sudo rmmod rt73
sudo insmod rt73.ko debug=31

```

Then configure your interface as usual. As soon as it goes down again, please post /var/log/syslog here (**attach** the file please, don't paste it's contents into the post window).

Done & Done.
Note: I had to strip the rt73.ko again (file size error)
As soon as it occurs I'll post the results -- thanks a lot

---

### Post by amic on 2008-01-19
attached is /var/log/syslog as requested, however it's syslog.0, the actual syslog is 45 MB's - if that's the one you need I'll upload it to a ftp - just let me know.

it's named syslog.zip b/c it's size is greater than the allowance for txt based docs on the forums, just rename it or open is up as a text file

also, if the aforementioned will suffice, how i can disable the syslog? is the file size capped at all, or will it just keep growing?

---

### Post by zuan on 2008-01-21
Hi I manage to buy a new USB D-Link DWL-G122 C1(USB) and it definately using RT73.

I manage to install all the driver and stuff, but I encountered a few problem such as

1. the wlan0 interface dosent auto UP itself when the usb stick plugged
2. it will freeze my systems when i try to connect to an Access Point manually via RutilT gui

anyone have the same problem??

Thanks

---

### Post by Huppi on 2008-01-21
Hi folks!

First thing: I'm a complete Linux newbie, so I'm quite proud I got it to work.

Anyway: for my Sweex USB Wireless Stick (the LC100060), I followed the steps from the first post literally (including blacklisting), and hurray, it worked!

Before this, I tried ndiswrapper and the RT2500 drivers, which both didn't work. As I said, the steps depicted in this thread made my day :-)

So, Diepruis, thanks a lot!

---

### Post by ParliamentFunkadelic on 2008-01-28
Hi, after going through this tutorial step by step, I ended up getting stuck after I entered the following command
sudo iwconfig wlan0 essid YOUR_NETWORK_NAME_HERE

When I substituted my network name where it was supposed to go it gave me this error

raph@raph-desktop:/usr/src/rt73-cvs-2008012815/Module$ sudo ifconfig rausb0 essid Russell
essid: Unknown host
ifconfig: `--help' gives usage information.

Do you have any suggestions? thanks

---

### Post by dannyboy79 on 2008-01-28
it's should be 
sudo iwconfig rausb0 essid Russell

also, it may be saying that it can't find a ESSID of Russell, are you sure that your ESSID is Russell with capital R? what does 

sudo iwlist rausb0 scan

show?

I think that's the command to scan for wireless networks. also, are you sure that you're using the rausb0 interface and not the wlan0 interface? what does ifconfig or iwconfig return?

---

### Post by CeeDub on 2008-01-29
I had trouble following the steps.  After ```
sudo modprobe -v rt61
``` everything seems to go according to plan (and everything up to that point works just as you said).  But when I enter ```
ifconfig -a
``` there is no wlan0 or anything like that.  What's going on?  Here's all the info that I imagine you would need:

```
saulback@saulback-desktop:~$ lsusb
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 002: ID 0bda:8187 Realtek Semiconductor Corp.
.
.

```

```
saulback@saulback-desktop:~$ lshw -C network
  *-network
....(ethernet)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:64:2e:90
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.8 multicast=yes wireless=IEEE 802.11g

```

Important stuff of lsmod:
```
saulback@saulback-desktop:~$ lsmod
Module                  Size  Used by
rtl8187                35328  0
rc80211_simple          6912  1
mac80211              171016  2 rtl8187,rc80211_simple
eeprom_93cx6            3200  1 rtl8187
usbcore               138632  6 rtl8187,usblp,usbhid,ehci_hcd,uhci_hcd

```

The card is a rtl8187 and from what I've gleaned off the internet, it uses the rt61 chipset.  I replaced everything in the tutorial from rt73 to rt61.  I was pointed here from this thread:
 [http://ubuntuforums.org/showthread.php?t=594857](http://ubuntuforums.org/showthread.php?t=594857)
to do this tutorial and apparently it has helped some with the rt61 chipset.  So, what do I do?

---

### Post by iris-n on 2008-02-01
Very thanks Mr. diepruis, that got me online.
The only issue is that i had to reboot for the internet to work, which you didn't say in your guide.

---

### Post by diepruis on 2008-02-02
> **CeeDub said:**
> I had trouble following the steps.  After ```
sudo modprobe -v rt61
``` everything seems to go according to plan (and everything up to that point works just as you said).  But when I enter ```
ifconfig -a
``` there is no wlan0 or anything like that.  What's going on?  Here's all the info that I imagine you would need:

```
saulback@saulback-desktop:~$ lsusb
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 002: ID 0bda:8187 Realtek Semiconductor Corp.
.
.

```

```
saulback@saulback-desktop:~$ lshw -C network
  *-network
....(ethernet)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:64:2e:90
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.8 multicast=yes wireless=IEEE 802.11g

```

Important stuff of lsmod:
```
saulback@saulback-desktop:~$ lsmod
Module                  Size  Used by
rtl8187                35328  0
rc80211_simple          6912  1
mac80211              171016  2 rtl8187,rc80211_simple
eeprom_93cx6            3200  1 rtl8187
usbcore               138632  6 rtl8187,usblp,usbhid,ehci_hcd,uhci_hcd

```

The card is a rtl8187 and from what I've gleaned off the internet, it uses the rt61 chipset.  I replaced everything in the tutorial from rt73 to rt61.  I was pointed here from this thread:
 [http://ubuntuforums.org/showthread.php?t=594857](http://ubuntuforums.org/showthread.php?t=594857)
to do this tutorial and apparently it has helped some with the rt61 chipset.  So, what do I do?

MMmmmmm... If it is an rt61, you'll need to blacklist rtl8187 and modprobe -v rt61, then tell me if you receive any errors from that last command and post them here.

---

### Post by diepruis on 2008-02-02
> **iris-n said:**
> Very thanks Mr. diepruis, that got me online.
The only issue is that i had to reboot for the internet to work, which you didn't say in your guide.

It shouldn't be necessary... As long as it works!

---

### Post by diepruis on 2008-02-02
> **amic said:**
> attached is /var/log/syslog as requested, however it's syslog.0, the actual syslog is 45 MB's - if that's the one you need I'll upload it to a ftp - just let me know.

it's named syslog.zip b/c it's size is greater than the allowance for txt based docs on the forums, just rename it or open is up as a text file

also, if the aforementioned will suffice, how i can disable the syslog? is the file size capped at all, or will it just keep growing?

Sorry for the late reply, been really busy :'(

That's unfortunately the wrong syslog you posted. When syslog get's full, it's copied to syslog.0 and syslog.0 becomes syslog.1 etc. So I need the syslog file. If you can maybe compress it into a tar.gz and upload to ftp, that would be great. We could also transfer it via p2p file sharing. Chat me on Jabber sometime and we could set that up.

---

### Post by bianchino on 2008-02-02
I have installed the alpha of Kubuntu 8.04. I wish to use my Belkin wireless USB adapter with RT73 so I followed this tutorial  and all the following posts. It goes straight up to a certain point.
I can compile the driver, install everything, but when I type

ifconfig wlan0 up
I get
SIOCSIFFLAGS: Invalid argument

here are other attempts:

desktop:~# ifconfig -a
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wlan1 Link encap:Ethernet HWaddr 00:00:00:00:00:00
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)


desktop:~# iwconfig
lo no wireless extensions.

wlan1 RT73 WLAN
Link Quality:0 Signal level:0 Noise level:113
Rx invalid nwid:0 invalid crypt:0 invalid misc:0

I have no other interfaces, no ethernet, no other wireless.
Whato do I have to do, please ? Thanx a lot.
__________________
Thanks Edit/Delete Message

---

### Post by diepruis on 2008-02-02
> **bianchino said:**
> I have installed the alpha of Kubuntu 8.04. I wish to use my Belkin wireless USB adapter with RT73 so I followed this tutorial  and all the following posts. It goes straight up to a certain point.
I can compile the driver, install everything, but when I type

ifconfig wlan0 up
I get
SIOCSIFFLAGS: Invalid argument

here are other attempts:

desktop:~# ifconfig -a

...

wlan1 Link encap:Ethernet HWaddr 00:00:00:00:00:00
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

...



Sorry... I didn't see this while answering your PM. Does this work for you:

```

ifconfig wlan1 up

```

---

### Post by bianchino on 2008-02-03
unfortunately "wlan0" was a typo in the post to the forum. I entered correctly "wlan1", and, as I wrote, I get:

ifconfig wlan1 up
SIOCSIFFLAGS: Invalid argument

If I try 
iwconfig wlan1 mode managed

I get
network is down

I really don't know what else to do...

---

### Post by CeeDub on 2008-02-03
> **diepruis said:**
> MMmmmmm... If it is an rt61, you'll need to blacklist rtl8187 and modprobe -v rt61, then tell me if you receive any errors from that last command and post them here.

That's exactly what I did the first time through. No errors or anything.  Everything seemed to work until I got to the step mentioned.  rtl8187 is mentioned in lsmod to show what lsmod looked like before blacklisting it.  rt61 was there afte'modprobe -v rt61'.

---

### Post by lcburgundy on 2008-02-04
> **diepruis said:**
> 

If you are using WPA security on your wireless network, then your /etc/network/interfaces file should look like this:

```

auto wlan0
iface wlan0 inet dhcp
    pre-up ifconfig wlan0 up
    pre-up iwpriv wlan0 set AuthMode=WPAPSK
    pre-up iwpriv wlan0 set EncrypType=TKIP
    pre-up iwpriv wlan0 set WPAPSK="YOUR_WPA_PSK_KEY"
    pre-up iwpriv wlan0 set SSID="YOUR_SSID"
    **pre-up iwpriv wlan0 set NetworkType=Infra**

```

Thanks to peterthewolf, sefs & Austin_KW for helping with this part.


FYI, for anyone else following this, these instructions were almost spot on for a Hawking 802.11g USB wireless adapter w/the built in antenna connecting to a Linksys WAP54g w/WPA-PSK enabled. However, the bolded line for NetworkType above made it simply not work. Commenting out/deleting that line in that file fixed everything and it now works smoothly.

---

### Post by daxumaming on 2008-02-07
I have to agree that this is a great Howto, and kudos to diepruis for taking the time in helping us out.

However, my wn321g just won't work on gutsy. heh, i think im giving up.

---

### Post by shoenigman on 2008-02-08
Hi,

I hope that you can offer me some help. I posted a new question about this process here [http://ubuntuforums.org/showthread.php?t=691186]("http://ubuntuforums.org/showthread.php?t=691186").

I would greatly appreciate a push in the right direction. Thanks!

---

### Post by Screaming_Angel on 2008-02-13
> **CeeDub said:**
> I had trouble following the steps.  After ```
sudo modprobe -v rt61
``` everything seems to go according to plan (and everything up to that point works just as you said).  But when I enter ```
ifconfig -a
``` there is no wlan0 or anything like that.  What's going on?  Here's all the info that I imagine you would need:

```
saulback@saulback-desktop:~$ lsusb
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 002: ID 0bda:8187 Realtek Semiconductor Corp.
.
.

```

```
saulback@saulback-desktop:~$ lshw -C network
  *-network
....(ethernet)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:64:2e:90
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.8 multicast=yes wireless=IEEE 802.11g

```

Important stuff of lsmod:
```
saulback@saulback-desktop:~$ lsmod
Module                  Size  Used by
rtl8187                35328  0
rc80211_simple          6912  1
mac80211              171016  2 rtl8187,rc80211_simple
eeprom_93cx6            3200  1 rtl8187
usbcore               138632  6 rtl8187,usblp,usbhid,ehci_hcd,uhci_hcd

```

The card is a rtl8187 and from what I've gleaned off the internet, it uses the rt61 chipset.  I replaced everything in the tutorial from rt73 to rt61.  I was pointed here from this thread:
 [http://ubuntuforums.org/showthread.php?t=594857](http://ubuntuforums.org/showthread.php?t=594857)
to do this tutorial and apparently it has helped some with the rt61 chipset.  So, what do I do?

CeeDub,

I'm not certain that the two aren't somehow related, but the rtl8187 module is for a **Realtek** device, and the rt61/rt73 modules you're trying to use are for **Ralink** devices.  It's my understanding that Realtek and Ralink are two different companies.

Based on your lsusb output, I would stick with the Realtek modules for your hardware.

I hope I've cleared up some confusion without creating more! :)

SA

---

### Post by nixxofugi on 2008-02-14
HELP!!! My computer won't boot after doing the walk through... Any one else encounter this???

---

### Post by dannyboy79 on 2008-02-14
> **nixxofugi said:**
> HELP!!! My computer won't boot after doing the walk through... Any one else encounter this???
have you tried to unplug the usb wifi adapter, then try to boot? or are you saying that the computer won't even POST? (meaning the bios doesn't even come up?) If that's the case, it's nothing you did in ubuntu, it's something with your bios or hardware. you could try to clear the cmos, which means remove the cmos battery for about 5 mins. IMPORTANT, whenever sticking your hands in your computer case, unplug all connections and touch something metal on the case before touching anything in the case like the motherboard etc etc. if you can get to ubuntu boot screen, you can hit ESC to enter grub menu, then in the grub menu:
    * Press 'e' to start editing.
    * Scroll down to the "kernel..." line. This is the line that tells Grub which kernel to boot with and the parameters to be passed to the kernel when it boots are placed at the end of this line.
    * Press 'e' again to edit this line.
    * Move to the end of the line. You will see any existing parameters
    * at the end of the line, remove the word splash. 
    * Then press 'b' to boot using that kernel without the cute ubuntu splash screen.

this will allow ubuntu to boot and you'll be able to see where it's hanging or any errors that are occuring.

---

### Post by nixxofugi on 2008-02-14
thanks for the quick reply... i have tried booting from the live cd to comment out the lines that were added in the walkthrough. attempted a reboot and still no luck... i also tried removing the word splash from the line you mentioned and that wont even display anything at all... i really dont want to format this thing to get it up again...

---

### Post by nixxofugi on 2008-02-14
so I removed the ralink file from modprobe.d and boom! it booted right up... now the question i have is why did the connection work while the system was up, but on reboot it wouldnt even load the system at all

---

### Post by blackaardvark on 2008-02-14
Well now my wireless works. Thank you.

Could I add that between steps 4 and 5 you should make it clear that the working directory should be /usr/src seeing as you are copying it from the home directory, people (me included) can end up extracting the driver into their home directory.

Thanks again!

---

### Post by dannyboy79 on 2008-02-14
> **blackaardvark said:**
> Well now my wireless works. Thank you.

Could I add that between steps 4 and 5 you should make it clear that the working directory should be /usr/src seeing as you are copying it from the home directory, people (me included) can end up extracting the driver into their home directory.

Thanks again!
yeah, he could change step 5 to be like this:
cd /usr/src/ && sudo tar -xvzf rt73-cvs-daily.tar.gz

---

### Post by Sunnyboyuk on 2008-02-15
you have just saved a laptop from being junked !!!  Thanks for taking the time to explain !!!

---

### Post by diepruis on 2008-02-16
> **blackaardvark said:**
> Well now my wireless works. Thank you.

Could I add that between steps 4 and 5 you should make it clear that the working directory should be /usr/src seeing as you are copying it from the home directory, people (me included) can end up extracting the driver into their home directory.

Thanks again!

That's a good point. I changed step 4 to add the necessary "cd" command. Thanks for the recommendation :)

---

### Post by foxdie on 2008-02-17
diepruis  I really appreciate the guide it has been very helpful. Unfortunately I am a total newbie and I was hoping to maybe recive some help. Here are the condtions of my comp.

Im using the Hardys new kernel.

I'm pretty sure I followed the guide properly, the error i think im encountering is that Im trying to use a linksys wusb54gc with rt71, however   i also have a intel4965 card inside the laptop. here is the error maybe you can make since of it....

foxdie@foxdie:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

Warning: Driver for device wlan1 has been compiled with version 22
of Wireless Extension, while this program supports up to version 20.
Some things may be broken...

wlan1     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     RT73 WLAN  
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

...................................................................................................................................
I'm really confused and stumped, I dont know if i need some how remove

1. remove the detection of the intel4965 hardware, thought i do use it in my windows dual boot.
2. maybe the kernel im using dosent work, with your guide.
3.If i possible didn't follow the guide right. I did run into problem with step 6.
but skipped them, so that might be it aswell.

---

### Post by diepruis on 2008-02-18
> **foxdie said:**
> 

<snip>

I'm really confused and stumped, I dont know if i need some how remove

1. remove the detection of the intel4965 hardware, thought i do use it in my windows dual boot.

You can blacklist the module that controls the intel chip if you know it's name, that won't affect the windows side of things.

> **foxdie said:**
> 
2. maybe the kernel im using dosent work, with your guide.


If you look closely, your output states that the problem is with the driver for wlan1, not wlan0, which is the RT73 according to iwconfig.

> **foxdie said:**
> 
3.If i possible didn't follow the guide right. I did run into problem with step 6.
but skipped them, so that might be it aswell.

Which steps did you skip? What was the problem? Please post any error output. Step 6 is crucial, without the dependencies it installs the driver will not work.

From the output, however, it seems that everything is installed right. Have you tried to configure the device (i.e. give it an essid and passphrase etc.)?

---

### Post by jhb1608 on 2008-02-19
This won't work, what did I do wrong? I think I feel it is the WEP issue, but I wasn't sure. So... hm. 

I followed all of your steps and it works, but it say server not found, is it is the dns servers or what?

P.S: Oh! What's the default DNS server addresses? I think I deleted it :|. I wasn't sure if it is the setting I setup in wireless or I think I setup the wrong thing in networkmanager and I don't want to remove networkmanager. Now it won't let me see the wireless icon or even wireless list now! How do I fix it?

I just wish someone can do it in PDF format and make the code bold and direction in normal. This way I can make sure I did it correctly. You may email me the PDF document of this tutorial. But just make it easier to understand for me. But reply me if you have made the PDF version of this tutorial. 

Maybe I can do the checkbox list thing. It'll be easier for me. I don't like to write everything on the paper, and had to type it carefully and don't make mistakes... :|.

---

### Post by diepruis on 2008-02-20
> **jhb1608 said:**
> This won't work, what did I do wrong? I think I feel it is the WEP issue, but I wasn't sure. So... hm.

What are you referring to here, specifically?

> **jhb1608 said:**
> I followed all of your steps and it works, but it say server not found, is it is the dns servers or what?

What gives you that message? What were you doing?

> **jhb1608 said:**
> P.S: Oh! What's the default DNS server addresses? I think I deleted it :|. I wasn't sure if it is the setting I setup in wireless or I think I setup the wrong thing in networkmanager and I don't want to remove networkmanager. Now it won't let me see the wireless icon or even wireless list now! How do I fix it?

The fact that you did not remove networkmanager might be the cause for why it is not working. Usually, the DNS server address is the IP address of your router. If you do not know what this is, ask again and I will explain.

> **jhb1608 said:**
> I just wish someone can do it in PDF format and make the code bold and direction in normal. This way I can make sure I did it correctly. You may email me the PDF document of this tutorial. But just make it easier to understand for me. But reply me if you have made the PDF version of this tutorial. 

A PDF format is unlikely. The code & most of the output is already highlighted in a specific style used by the entire forum. If you need further clarification, please refer to specific sections, I can't help you understand if you don't tell me what to help you with.

Just follow the instructions carefully, read the output from the terminal carefully and as soon as something appears that looks like an error message, post it here and we can help you step by step.

> **jhb1608 said:**
> Maybe I can do the checkbox list thing. It'll be easier for me. I don't like to write everything on the paper, and had to type it carefully and don't make mistakes... :|.

You can save this page to an HTML file from Firefox using File -> Save Page As. Then you can copy the file to the machine on which you are doing the tutorial and copy and paste the code instead. This will drastically reduce errors, believe me.

You can also print out the page, if you want to check things off one by one and make notes.

---

### Post by jhb1608 on 2008-02-20
Answers:

What are you referring to here, specifically? 
I want to have wireless on Benkin USB Wireless G USB adapter. Meh, I'm sorry, my brain is just messed up today.


What gives you that message? What were you doing? 
I did your steps, compling files, and all steps you provided. and when I tried to get on wireless. It won't let me get on and the server give me error in firefox.

Can you explain DNS means? I am familar wioth DNS, but unsure if I think it was correct.

And I'll try your HTML saving and printing techique.

Wait you mean I had to uninstall networkmanager, isn't that is the only tool it will be needed to get the networking running?

---

### Post by jhb1608 on 2008-02-20
okay. It keep freezing when I plug in the wireless adapter, what did I do wrong? I did put the correct information, and I had to put the WPA key and SSID name and I followed and reboot and it froze when I leave the usb adapter on and it blinks the light, but it freezes. Why it did that?

---

### Post by jhb1608 on 2008-02-21
Alright. How do I restore it all in the same way as before? Then I can do it in steps. I printed it out. I found out why it freezes, because I hadn't blacklisted the rt73 driver. But I just need to figure out why it won't work.

I did the:

> cd /usr/src

Then I downloaded the rt-73-daily TAR file, then copy and pasting everything... BUT! the steps make me doomed:

sudo ifconfig wlan0 down
sudo modprobe -r rt73usb
sudo modprobe -r rt2570
sudo modprobe -r rt2500usb
sudo modprobe -r rt2x00lib

Some warnings appears but some don't appear.

and also added the blacklist codes and loaded the module, and also did the ipconfig -a
and did the ifconfig wlan0 up and everything, all information were correct, but it won't work... 

Why?

I also keep going on adding the interfaces code also

But unsure you are meant on:

auto wlan0
iface wlan0 inet dhcp

add on behind it or what?

```
	pre-up ifconfig wlan0 up
	pre-up iwconfig wlan0 essid YOUR_ESSID
	pre-up iwconfig wlan0 key WEP_KEY_OR_"OFF"_IF_YOU_HAVE_NONE
```

This one confused me also.

Also I did remove the networkmanager also.

but after this step I reboot and it won't load in internet? Why? I might feel I missed something.

BTW it is WPA. Last time I checked, I was on the laptop and looked the setup and say it is WPA, so I have the key for it and also the name. But why it won't work?

Just IM me in Yahoo or something or email is even better.

My email is: [EMAIL="jhb1608@gmail.com"]jhb1608@gmail.com[/EMAIL]

---

### Post by oliverwebb on 2008-02-21
Major problem here.

Got everything set up fine. Only thing is computer won't connect to WEP or WPA networks. Not matter the type. I can get into unsecured networks fine. What's going on?

I get an IP address and everything, it just won't bring any webpages up in Firefox or ping anything.

Obviously I don't want an unsecured network in my house, that's just very stupid. Any ideas?

---

### Post by Austin_KW on 2008-02-21
Check your routing. If you are switching between wired and wireless while setting things up, it can leave the wired route after you disconnect the cable. 
Try "sudo ifdown eth0" to remove the wired route.

---

### Post by oliverwebb on 2008-02-21
I'm not using the ethernet. At all. Purely wireless.

Installed it using the offline method.

---

### Post by Austin_KW on 2008-02-21
> **oliverwebb said:**
> I'm not using the ethernet. At all. Purely wireless.

Installed it using the offline method.

Isolate the problem
ping yourRouterIP
ping 64.233.187.99 #google by ip
ping google.com #google by dns lookup

---

### Post by jhb1608 on 2008-02-21
> **oliverwebb said:**
> Major problem here.

Got everything set up fine. Only thing is computer won't connect to WEP or WPA networks. Not matter the type. I can get into unsecured networks fine. What's going on?

I get an IP address and everything, it just won't bring any webpages up in Firefox or ping anything.

Obviously I don't want an unsecured network in my house, that's just very stupid. Any ideas?

Well my problem is similar, but I don't go to unsecured area. :).

---

### Post by oliverwebb on 2008-02-22
> **Austin_KW said:**
> Isolate the problem
ping yourRouterIP
ping 64.233.187.99 #google by ip
ping google.com #google by dns lookup


```
oliver@ubuntu:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.4 icmp_seq=2 Destination Host Unreachable
From 192.168.2.4 icmp_seq=3 Destination Host Unreachable
From 192.168.2.4 icmp_seq=4 Destination Host Unreachable
From 192.168.2.4 icmp_seq=5 Destination Host Unreachable
From 192.168.2.4 icmp_seq=6 Destination Host Unreachable
From 192.168.2.4 icmp_seq=7 Destination Host Unreachable
From 192.168.2.4 icmp_seq=8 Destination Host Unreachable
From 192.168.2.4 icmp_seq=9 Destination Host Unreachable
```

Then I control + C'ed it and ran the next one, I get exactly the same thing.

Then:

```
Ping: unknown host google.com
```

for the DNS lookup.

SIGH!

---

### Post by Austin_KW on 2008-02-22
> **oliverwebb said:**
> ```
oliver@ubuntu:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.4 icmp_seq=2 Destination Host Unreachable
From 192.168.2.4 icmp_seq=3 Destination Host Unreachable
From 192.168.2.4 icmp_seq=4 Destination Host Unreachable
From 192.168.2.4 icmp_seq=5 Destination Host Unreachable
From 192.168.2.4 icmp_seq=6 Destination Host Unreachable
From 192.168.2.4 icmp_seq=7 Destination Host Unreachable
From 192.168.2.4 icmp_seq=8 Destination Host Unreachable
From 192.168.2.4 icmp_seq=9 Destination Host Unreachable
```

Then I control + C'ed it and ran the next one, I get exactly the same thing.

Then:

```
Ping: unknown host google.com
```

for the DNS lookup.

SIGH!
So you can't even get to the router after the initial DHCP ack.
whats is output from the commands?
```

ifconfig -a
sudo iwconfig
route -n
lsmod | grep usbcore

```

---

### Post by oliverwebb on 2008-02-22
> **Austin_KW said:**
> So you can't even get to the router after the initial DHCP ack.
whats is output from the commands?
```

ifconfig -a
sudo iwconfig
route -n
lsmod | grep usbcore

```

```
oliver@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:14:85:08:E4:05  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:14:85:08:E4:07  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:1C:DF:4B:91:9A  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:dfff:fe4b:919a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:789 errors:0 dropped:0 overruns:0 frame:0
          TX packets:222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:83510 (81.5 KiB)  TX bytes:18142 (17.7 KiB)

```

```
oliver@ubuntu:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT73 WLAN  ESSID:"Belkin54g"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:11:50:7F:E6:B4   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:0101-0101-01
          Link Quality=70/100  Signal level:-58 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.
```

```
oliver@ubuntu:~$ route -n
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0

```

```
oliver@ubuntu:~$ lsmod | grep usbcore
usbcore               134280  11 snd_usb_audio,snd_usb_lib,gspca,rt73,usbhid,usb_storage,libusual,ohci_hcd,uhci_hcd,ehci_hcd


```

---

### Post by Austin_KW on 2008-02-22
@oliverwebb  
That all looks good

You might consider turning off ipv6 but I dont think it is the problem. 
Are you running firestarter or any other iptables firewall? You might try flushing all the rules 
```
sudo iptables -F 
```

I dont know the sequence that got you here so, If all else fails, remove the dongle, reinsert and force it to reread interfaces configuration with ```
 sudo ifup --f wlan0
```

---

### Post by oliverwebb on 2008-02-22
Holy crap that worked!

---

### Post by dannyboy79 on 2008-02-22
> **oliverwebb said:**
> Holy crap that worked!

just keep in mind if you flushed all your iptables rules you no longer are protected if you were relying on your software firewall (iptables) to protect you.

---

### Post by Austin_KW on 2008-02-22
> **dannyboy79 said:**
> just keep in mind if you flushed all your iptables rules you no longer are protected if you were relying on your software firewall (iptables) to protect you.

True, but in this case he is behind a NAT firewall (belkin router)

---

### Post by Austin_KW on 2008-02-22
Anyone using the Rutilt utility to manage their connections. Just tried V0.16 and it is finally recognising my router as WPA, the older versions seeing it incorrectly as WEP.

I had been using the interfaces file and the CLI when I had to connect to a strange network but RutilT V0.16 seems better.

---

### Post by jhb1608 on 2008-02-23
ok I got the dongle to work, but need the WPA files. 

Where can I get the required files: wpa_supplicant ?

And also, where can I get Wicd also? PM me ;).

---

### Post by jhb1608 on 2008-02-23
> **Austin_KW said:**
> Anyone using the Rutilt utility to manage their connections. Just tried V0.16 and it is finally recognising my router as WPA, the older versions seeing it incorrectly as WEP.

I had been using the interfaces file and the CLI when I had to connect to a strange network but RutilT V0.16 seems better.

Can you give me the link to RutilT V0.16 also?

---

### Post by jhb1608 on 2008-02-23
someone's right, Rulit is easier.

---

### Post by Austin_KW on 2008-02-24
Rutilt can be downloaded at [http://cbbk.free.fr/bonrom/](http://cbbk.free.fr/bonrom/)
to build and install it
```

tar -xvzf RutilTv0.16.tar.gz
cd  RutilTv0.16/
./configure.sh  --launcher=external
make
sudo make  install

```

---

### Post by mandeepsmagh on 2008-02-25
Hi, guys. I have got **Dlink dwl -g122 revc1 usb adaptor**.  I am getting constant 

connection breaking problem. When I check connection information it shows** rt73 usb driver**.

  Output of iwconfig is this
[PHP]
    singh@singh-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"dlink"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:11:90:AD:9C   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[/PHP]

Output of lsusb is
[PHP]
singh@singh-desktop:~$ lsusb
Bus 005 Device 004: ID 07d1:3c03 D-Link System 
[/PHP]

 just beacuse of this connection problem. I keep booting back into windows. Which is in a sense 

preety annoying. Pls help me out. Thanks !

---

### Post by gamergod131 on 2008-02-25
Whenever I try to load the new module, I get this message:

```
FATAL: Error inserting rt73 (/lib/modules/2.6.22-14-generic/extra/rt73.ko): Invalid module format

```

What is wrong?:confused:

---

### Post by diepruis on 2008-02-26
> **gamergod131 said:**
> Whenever I try to load the new module, I get this message:

```
FATAL: Error inserting rt73 (/lib/modules/2.6.22-14-generic/extra/rt73.ko): Invalid module format

```

What is wrong?:confused:

What is the output of ```
dmesg | tail
``` **right** after you issue that command?

---

### Post by diepruis on 2008-02-26
> **Austin_KW said:**
> Anyone using the Rutilt utility to manage their connections. Just tried V0.16 and it is finally recognising my router as WPA, the older versions seeing it incorrectly as WEP.

I had been using the interfaces file and the CLI when I had to connect to a strange network but RutilT V0.16 seems better.

I find it a **lot** easier to configure rt73 with this program. RT61 luckily works with network-manager in 7.10. Perhaps a tutorial on installing Rutilt is in order?

---

### Post by yesterday on 2008-02-26
I would just like to say here that rt73 does in fact work almost out of the box in Gutsy.  The ralink drivers provided with Gutsy are indeed old drivers, but they are drivers that work with wpa_supplicant, unlike the "new legacy" drivers at serialmonkey.  What's missing is the firmware binary, which is available at the Ralink website.  Once the binary file ("rt73.bin") is in /lib/firmware/[kernel version], the interface can be brought up/seen,  and since the older legacy driver support wpa_supplicant, unlike the newer ones, you can use NetworkManager for WPA1/2

I've also tried this with Fedora 8 -- same thing there.  Older rt2x00lib and rt73usb drivers + firmware + Network Manager + WPA2 = pretty easy networking!

---

### Post by gamergod131 on 2008-02-27
Well thanks anyway. I tried the entire tutorial again and it worked! :) I noticed that there was a new release when I did the date command, maybe the one I was using previously had a problem?

---

### Post by kbehel on 2008-03-02
I've got a Linksys WUSB54GC that uses the RT73 driver out of the box with Gutsy. 
That connection dies after high traffic with rt2x00usb_vendor_request errors. 
So I tried the instructions at the first page of this thread - and it became much worse. I don't recall seeing any error messages, but my ping time would randomly change from 2ms to 600ms for no apparent reason. I'm using this computer for streaming video playback (mythtv frontend connected over a wireless network) so those sort of random delays cause problems. 
I reverted back to the original drivers.

This thread is now very long - so what I'm wondering is, has anyone determined if the serial monkey drivers actually are stable with Gutsy? Is there a different install procedure? Did anyone else have random network delay problems when using the instructions from the first page?


thanks,

Kevin

---

### Post by yesterday on 2008-03-03
the only issue with the serialmonkey drivers is they generate alot of interrupts.  Check youd load avg in top with the drivers --- you'll see it's around 3 or maybe greater.

---

### Post by kbehel on 2008-03-03
Can't check on that system anymore - I reverted back to a backup image so my wireless mythtv setup would work for the kids.

Seems that a driver that generates enough interrupts to drastically reduce network latency is not a minor issue.

thanks,

Kevin

---

### Post by Lourie on 2008-03-05
I have managed to carry out the first 11 steps with no problem.  I am finding that Step 12: Load the new module does not execute; it just goes back to the prompt. Needless to say, Step 13 does not detect the wireless hardware, so I cannot continue. Can anybody tell me how to overcome this problem? Or is there another method of getting the driver installed? I must say, these steps are easy to follow, thanks for that. :confused:

---

### Post by a3k on 2008-03-10
tutorial worked well ...  thanks diepruis

---

### Post by mandeepsmagh on 2008-03-10
Thanks, diepruis. Great thread. Solved constant internet connection 

  breaking problem. Since I don't have wired internet connection, had to 

  use  default rt73usb driver to Install serialmonkey drivers and then 

  blacklisted rt73usb driver. Thanks again !

---

### Post by chinatony on 2008-03-11
Oh, has been too difficult, cannot understand.

---

### Post by diepruis on 2008-03-11
> **chinatony said:**
> Oh, has been too difficult, cannot understand.

Which part did you not understand?

---

### Post by Keltenbleich on 2008-03-11
Dear Diepruis,

I have installed ubuntu on two pcs a few days ago. (Ex Windows XP)

I use a USB dongle ([COLOR="Navy"]Conceptronic C54RU with a rt73 driver)  to access a wireless network shared by a secondr pc. The second pc is doing fine, as it is directly connected to the router through a RJ-45 switch[/COLOR])

Since I have installed Ubuntu, I have problems with pc number one (the one with USB dongle).

The internet connection only lasts a few minutes, then I have to unplug and replug the USB dongle to get the connection back.

As the rt73 driver is not supported by LINUX it should not function at all in the first place...but it does, at least for a couple of minutes.  Do you have an idea why this is so?

tks+rgds
Keltenbleich

---

### Post by mandeepsmagh on 2008-03-12
> Since I have installed Ubuntu, I have problems with pc number one (the one with USB dongle).

The internet connection only lasts a few minutes, then I have to unplug and replug the USB dongle to get the connection back.

As the rt73 driver is not supported by LINUX it should not function at all in the first place...but it does, at least for a couple of minutes. Do you have an idea why this is so?

 


 Hi, Keltenbleich. I assume that u might be using default rt73usb drivers. I also had the 

 same problem. I solved it by installing serialmonkey drivers following the steps described  

 by Diepruis on the first page. As with my case installing serialmonkey driver may solve ur 

 problem.

---

### Post by diepruis on 2008-03-12
> **Keltenbleich said:**
> As the rt73 driver is not supported by LINUX it should not function at all in the first place...but it does, at least for a couple of minutes.  Do you have an idea why this is so?

The rt73 driver is indeed supported by Linux. It has been opensourced by RaLink, the people who developed the chipset and is being maintaned by these guys: [Serialmonkey]("http://rt2x00.serialmonkey.com")

Like mandeepsmagh said, try following the instructions on this post, they solve the problems with this device for most people. The underlying problem with this device is not that it is unsupported by Linux, but that Ubuntu ships rt73usb, which is an upgrade to rt73, but still in beta. This tutorial details how to install rt73 and remove rt73usb.

---

### Post by kbehel on 2008-03-13
I just installed the rt73 module with the directions on the first page, and now the connection is completely dead upon bootup even though it shows up in lsusb. 
For what it is worth, the device's light does flash a little while ubuntu is booting up which implies to me that something is trying to use the device, however it then appears that the connection dies and the light goes off.  

iwconfig says that I am connected to my network, but ping just returns a network unreachable error.
No amount of ifup/ifdown or networking restarts will make the connection work.

I can make it work properly by removing my card from the USB slot and then reinserting it. 

lsmod shows only rt73, I've got all the other rt73usb, rt2x00usb, rt2x00lib modules blacklisted.

Does anyone have an idea what is going on? The rt2x00 modules were working reasonably well with my Linksys WUSB54GC card before this, though the connection would die after too much traffic.

thanks,

Kevin

---

### Post by mandeepsmagh on 2008-03-14
> **kbehel said:**
> I just installed the rt73 module with the directions on the first page, and now the connection is completely dead upon bootup even though it shows up in lsusb. 
For what it is worth, the device's light does flash a little while ubuntu is booting up which implies to me that something is trying to use the device, however it then appears that the connection dies and the light goes off.  

iwconfig says that I am connected to my network, but ping just returns a network unreachable error.
No amount of ifup/ifdown or networking restarts will make the connection work.

I can make it work properly by removing my card from the USB slot and then reinserting it. 

lsmod shows only rt73, I've got all the other rt73usb, rt2x00usb, rt2x00lib modules blacklisted.

Does anyone have an idea what is going on? The rt2x00 modules were working reasonably well with my Linksys WUSB54GC card before this, though the connection would die after too much traffic.

thanks,

Kevin
It also happened to me. Have u configued it manually or u r using network manager in roaming mode. Manual configuration solved my problem. Network manager does not work with serialmonkey drivers. 

If u want wlan manager,u can install **rutilt wlan manager**. It supports serialmonkey drivers.  But manual configuration should work, if u don't want to insatll any wlan manager.

---

### Post by kbehel on 2008-03-14
It's all manually configured in /etc/networking/interfaces
It was working (mostly) fine using the native drivers (rt73usb, rt2x00) - it just lost the connection 
after a lot of traffic.

Kevin

---

### Post by mandeepsmagh on 2008-03-14
> **kbehel said:**
> It's all manually configured in /etc/networking/interfaces
It was working (mostly) fine using the native drivers (rt73usb, rt2x00) - it just lost the connection 
after a lot of traffic.

Kevin
Well, in that case I don't have any idea. Because I did not follow these commands , when it can be configured easily through network interface. Just go to **system - administration - networ**k

 and check that it shows the properties u configured through terminal.

---

### Post by kbehel on 2008-03-15
Has anyone else had a problem with their interface not being detected on bootup after installing the rt73 drivers? Mine isn't detected on boot, and it still occasionally drops the connection - error is that the network is unreachable even though iwconfig says that it is still connected.

Anyone have an idea?

thanks,

Kevin

---

### Post by linyanam on 2008-03-23
Hi,
Finally my usb wifi stick (Bluenext BN-WD54G ) is recognised and working out of box with hardy beta.
I was using this howto for the last 1 year with rutilt to connect to
WAP 2 connection. 
My driver is RT73.
[http://www.bluenext.co.uk/wifi-adapter/bn-wd54g-wireless-usb-adapter.html](http://www.bluenext.co.uk/wifi-adapter/bn-wd54g-wireless-usb-adapter.html)
Thanks diepruis.
Linyanam.

---

### Post by slayer^_^ on 2008-03-25
i am very disappointed, i had to install ubuntu on my father's pc. i had many troubles with a simple TP-LINK TL-WN321G and had to give up... you know, i can't tell my father to repeat that long procedure every time ubuntu updates the kernel, neither i could tell him to connect opening up the terminal and giving the command sudo /etc/init.d/networking restart...

i know noone pays anyone here, i thank everyone of you for all you do, but i am very disappointed for having to give up installing ubuntu on my father's pc... now there's xp on it, and that wireless dongle works fine... ARGH !!!

---

### Post by Existentialist on 2008-03-25
> **Lourie said:**
> I have managed to carry out the first 11 steps with no problem.  I am finding that Step 12: Load the new module does not execute; it just goes back to the prompt. Needless to say, Step 13 does not detect the wireless hardware, so I cannot continue. Can anybody tell me how to overcome this problem? Or is there another method of getting the driver installed? I must say, these steps are easy to follow, thanks for that. :confused:

I'm having the same issue, everything installs with no errors returned, but the rt73 module is not found.  I have tried a few of the daily builds, but still no luck.  Any advice?  I'm running 8.04 beta, 64 bit, 2.6.24-12-generic.

---

### Post by slayer^_^ on 2008-03-26
to the developers : is it such a bad idea to remove the rt73usb modules that are beta, and putting back the rt73 ones? a post with more than 100 pages should be significant :(

hope to see a solution in hardy :°D

good work!

---

### Post by diepruis on 2008-03-26
> **Existentialist said:**
> I'm having the same issue, everything installs with no errors returned, but the rt73 module is not found.  I have tried a few of the daily builds, but still no luck.  Any advice?  I'm running 8.04 beta, 64 bit, 2.6.24-12-generic.

Mmmm... It could be because 8.04 is still beta, I believe another person had problems with it, or it could possibly be a 64 bit issue. What is the output from the compile step?

---

### Post by diepruis on 2008-03-26
> **slayer^_^ said:**
> to the developers : is it such a bad idea to remove the rt73usb modules that are beta, and putting back the rt73 ones? a post with more than 100 pages should be significant :(

hope to see a solution in hardy :°D

good work!

I agree! There's been a bug report posted and everything... must be some reason for keeping rt73usb then...

---

### Post by dannyboy79 on 2008-03-26
> **slayer^_^ said:**
> to the developers : is it such a bad idea to remove the rt73usb modules that are beta, and putting back the rt73 ones? a post with more than 100 pages should be significant :(

hope to see a solution in hardy :°D

good work!

i have been saying this since Dapper. it's very disappointing that every release they say they are working on wireless issues yet they haven't fixed the issue with the rt73usb. What I don't get is that there is a driver that works just fine, the rt73 from serialmonkey, why in the world are they not just implementing that??????????/

Please developers, can you get this fixed before Hardy is released?

---

### Post by diepruis on 2008-03-26
> **dannyboy79 said:**
> i have been saying this since Dapper. it's very disappointing that every release they say they are working on wireless issues yet they haven't fixed the issue with the rt73usb. What I don't get is that there is a driver that works just fine, the rt73 from serialmonkey, why in the world are they not just implementing that??????????/

Please developers, can you get this fixed before Hardy is released?

Has there been a bug report?

---

### Post by Existentialist on 2008-03-26
> **diepruis said:**
> Mmmm... It could be because 8.04 is still beta, I believe another person had problems with it, or it could possibly be a 64 bit issue. What is the output from the compile step?

I finally got it working through a combination of reinstalling my kernel headers, and using locate to remove anything to do with rt73 and rt73usb.  All the output from make, and make install were the same after doing this, but the module now loads and runs fine.

---

### Post by Austin_KW on 2008-03-26
> **diepruis said:**
> Mmmm... It could be because 8.04 is still beta, I believe another person had problems with it, or it could possibly be a 64 bit issue. What is the output from the compile step?

The legacy drivers work with 32bit hardy. I have not tried 64 bit.

The beta drivers still have problems and you cannot build the beta cvs without replacing the wireless tools. (same old, same old...)

---

### Post by diepruis on 2008-03-27
> **Existentialist said:**
> I finally got it working through a combination of reinstalling my kernel headers, and using locate to remove anything to do with rt73 and rt73usb.  All the output from make, and make install were the same after doing this, but the module now loads and runs fine.

Mmmm... perhaps Ubuntu was loading the wrong module, or you had the wrong headers installed?

---

### Post by Existentialist on 2008-03-27
> **diepruis said:**
> Mmmm... perhaps Ubuntu was loading the wrong module, or you had the wrong headers installed?

The headers were the correct ones, but there was one rt73.ko file located with the kernel drivers that I found with locate.  I imagine that it may have been from when I was attempting to patch and install the older versions of the driver that were not built to work with kernel 2.6.24.  I think deleting that is what fixed my problem.

---

### Post by badweasel on 2008-04-08
first of all thanks for this guide :)

now could you help me solve a couple of tiny details please 

#1 i have to launch kwifimanager ---> scan for networks --> connect to network to get a link
(adhock since i dont have a access point or router if i can get this sorted it will be my ap :))

#2 i cant get anything across the link nada  no http pings smb shares anything
 
followed all steps and also blacklisted ipv6

usbcore               134280  7 rt73,ov511,usb_storage,libusual,ehci_hcd,uhci_hcd
Bus 005 Device 004: ID 148f:2573 Ralink Technology, Corp.

wlan0     Link encap:Ethernet  HWaddr 00:19:E0:14:25:CA
          inet addr:192.168.0.20  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2458 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:535664 (523.1 KiB)  TX bytes:189666 (185.2 KiB)
any other info you need to help me fix it im happy to supply :) ta oh and it only links at b mode instead of b/g

---

### Post by cleverest on 2008-04-14
Is the method on page 1 still current with a device I'm trying to use RT73 drivers with? (it's a ralink device...a Hawking USB wireless G adapter)  I believe I accidentally installed rt2500 drivers before figuring out I wanted to use RT73 drivers..(I'm pretty new at this).and now when I airmon-ng rausb0 it says I'm using a RT2500 chipset, but when I iwconfig rausb0 it tells me it's a RT73...

can anyone help me?  Is page 1 still a current method of fixing my issue?  (I can get it all to work except packet injection, it only reads packets...) in BT3 it works fine out of the box.....if that's any help.....

- Brett

---

### Post by diepruis on 2008-04-16
> **cleverest said:**
> can anyone help me?  Is page 1 still a current method of fixing my issue?  (I can get it all to work except packet injection, it only reads packets...) in BT3 it works fine out of the box.....if that's any help.....

- Brett

That's good news!

I believe the driver doesn't support packet injection. Please check [Serialmonkey's website]("http://rt2x00.serialmonkey.com") to verify.

As to the currency of the instructions, they were written up after installing under Feisty (7.04). They won't be current for 8.04. If there are still problems with the device after the upgrade, I will update the first page of this thread.

---

### Post by Kiefer Rodriguez on 2008-04-16
**'D-Link DWL-G122 Rev. C: Driver Installer'**

Hey all,
First off - diepruis, Great guide, keep up the good work.
Ive had to go through that guide and repeat the steps countless times, So last night I threw together
a Python script to do it for me, then made it a little more dynamic so that pretty much anyone can run it.
Below is the script itself, but Ive archived the script, a FAQ, a README and some other files (that are
required for the script to work) and uploaded it. 

Edit: The script and information on it can be found on [its thread]("http://ubuntuforums.org/showthread.php?p=4732883#post4732883").

Any input/errors/bugs would be appreciated, cheers - Kiefer Rodriguez.

---

### Post by diepruis on 2008-04-17
> **Kiefer Rodriguez said:**
> **'D-Link DWL-G122 Rev. C: Driver Installer'**

Hey all,
First off - diepruis, Great guide, keep up the good work.
Ive had to go through that guide and repeat the steps countless times, So last night I threw together
a Python script to do it for me, then made it a little more dynamic so that pretty much anyone can run it.
Below is the script itself, but Ive archived the script, a FAQ, a README and some other files (that are
required for the script to work) and uploaded it. Heres the script:



Wow! Very decent work! Can someone please test this and get some feedback? If this works properly I'll link it to the front page.

---

### Post by Kiefer Rodriguez on 2008-04-17
Heh Cheers mate,
Ive Just Updated the script to version 1.1, some bug fixes, error fixes, and syntax fixes, I wont be updating the above post by myself, instead I made a thread for it :p
I would be more than happy for you to link to it once its confirmed working ^_^

[RT73 Device Installer Script Thread.]("http://ubuntuforums.org/showthread.php?p=4732883#post4732883")

Thanks again for the great guide :)

---

### Post by diepruis on 2008-04-17
> **Kiefer Rodriguez said:**
> Heh Cheers mate,
Ive Just Updated the script to version 1.1, some bug fixes, error fixes, and syntax fixes, I wont be updating the above post by myself, instead I made a thread for it :p
I would be more than happy for you to link to it once its confirmed working ^_^

[RT73 Device Installer Script Thread.]("http://ubuntuforums.org/showthread.php?p=4732883#post4732883")

Thanks again for the great guide :)

No problems :) Maybe you should link here as well so people know where to find an explanation of what the script does?

---

### Post by Kiefer Rodriguez on 2008-04-17
Way ahead of ya' :p

---

### Post by kbehel on 2008-04-17
I've tried the steps on the front page twice now, and both times I've found the serial-monkey drivers to be more unstable than the regular ones that came with Gutsy. It would work fine for low through put (web surfing, email, etc). However, it seems that under conditions of high traffic (copying files over the network for example), the connection would disappear even though iwconfig would still say that it is connected. Other times the ping time to the rest of the network would go from 10ms to 1000ms.

Has anyone else seen this? Am I the only person to have had these problems with the serial monkey drivers, or is everyone else doing low throughput stuff?

any suggestions appreciated,

thanks,

Kevin

---

### Post by Austin_KW on 2008-04-18
> **kbehel said:**
> I've tried the steps on the front page twice now, and both times I've found the serial-monkey drivers to be more unstable than the regular ones that came with Gutsy. It would work fine for low through put (web surfing, email, etc). However, it seems that under conditions of high traffic (copying files over the network for example), the connection would disappear even though iwconfig would still say that it is connected. Other times the ping time to the rest of the network would go from 10ms to 1000ms.

Has anyone else seen this? Am I the only person to have had these problems with the serial monkey drivers, or is everyone else doing low throughput stuff?

any suggestions appreciated,

thanks,

Kevin

Most people are using the driver for the full range of activity. I use it for 12mbs internet and it can easily keep up.

EDIT; When you day "10ms ping to rest of the network" do you mean LAN or internet as LAN ping should be ~2ms

Also are you sure that you are using the legacy driver because what you describe is very like the behavior seen with the beta rt2x00 drivers

---

### Post by Juhla Mokka on 2008-04-18
Apologies for intruding this thread but I am completely lost what to do!

Tried to install rt73usb driver, but something went wrong. :confused:

Problem here: [http://ubuntuforums.org/showthread.php?p=4740485#post4740485](http://ubuntuforums.org/showthread.php?p=4740485#post4740485)
The area where the thread is does not seem as active as this.

---

### Post by Kiefer Rodriguez on 2008-04-18
> **Juhla Mokka said:**
> Apologies for intruding this thread but I am completely lost what to do!

Tried to install rt73usb driver, but something went wrong. :confused:

Problem here: [http://ubuntuforums.org/showthread.php?p=4740485#post4740485](http://ubuntuforums.org/showthread.php?p=4740485#post4740485)
The area where the thread is does not seem as active as this.

If you are trying to get a device working that uses the rt73 Ralink chipset, You might consider trying the rt73 Wireless Device installer script (Link in my sig).

If the script fails to work, I recommend posting any error messages recieved on the rt73 Ralink chipset install script thread (again, the link is in my sig.).

Let me know how it goes.

---

### Post by Austin_KW on 2008-04-18
> **Kiefer Rodriguez said:**
> If you are trying to get a device working that uses the rt73 Ralink chipset, You might consider trying the rt73 Wireless Device installer script (Link in my sig).

If the script fails to work, I recommend posting any error messages recieved on the rt73 Ralink chipset install script thread (again, the link is in my sig.).

Let me know how it goes.

+, for this the script seem to do a lot of the grunt work and should clean up by blacklisting and removing conflicting drivers.

The lshw is showing the driver as rt73sta. I don't remember what this is (ralink tech original drivers or ndiswrapper)?

---

### Post by Juhla Mokka on 2008-04-18
Hi

Thanks for this. Let's see then...

1. I use WAP not WEP, but went around this by taking all security down 
3. just after I had installed the Ralink driver, the wireless name was rausb0, now back to it's wlan0 - not sure which one I should have typed in this script
2. the script tried to download something off web (ubuntu/canonical.com) even I had answered I had no connection

I downloaded the driver from Ralink website - their driver for Linux.

```
Ralink rt73: Driver Installer - by Kiefer Rodriguez.
Please enter your intended AP name (e.g. 'OfficeWireless' or 'Our_Internet') : Censored
Please enter the WEP key for Toad (or type 'off' if there isnt one, ASCII keys need to be prefixed with 's:' without the quotes and without any spaces.) : off
Please enter your package manager (e.g. 'apt-get' or 'aptitude') : apt-get
Do you currently have an active internet connection? [y/n] : n
Enter the interface name for the device to activate (Most likely 'wlan0') : wlan0
*       Copying rt73 module .tar to /usr/src..
*       Unpacking rt73 module in /usr/src..
Please insert your [Edu/U/Ku]buntu CD, wait 10 seconds then press enter.
%       Gathering required header files from CD, this may take a while..
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [b23710d0071ddbf904b10cfe355c13af-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called: 
'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
Copying package lists...gpgv: Signature made Tue 16 Oct 2007 00:53:09 BST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
Unmounting CD-ROM...
Repeat this process for the rest of the CDs in your set.
*       Added CD-Rom to sources list, now updating list..
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
50% [Connecting to archive.canonical.com] [Connecting to archive.ubuntu.com]   
Err http://archive.canonical.com gutsy Release.gpg                          
  Could not resolve ‘archive.canonical.com’
Err http://archive.ubuntu.com gutsy Release.gpg                             
  Could not resolve ‘archive.ubuntu.com’
Err http://archive.ubuntu.com gutsy/universe Translation-en_GB              
  Could not resolve ‘archive.ubuntu.com’
Err http://archive.canonical.com gutsy/partner Translation-en_GB            
  Could not resolve ‘archive.canonical.com’
42% [Connecting to archive.canonical.com] [Connecting to archive.ubuntu.com]


```

---

### Post by Kiefer Rodriguez on 2008-04-18
> **Juhla Mokka said:**
> Hi

Thanks for this. Let's see then...

1. I use WAP not WEP, but went around this by taking all security down 
3. just after I had installed the Ralink driver, the wireless name was rausb0, now back to it's wlan0 - not sure which one I should have typed in this script
2. the script tried to download something off web (ubuntu/canonical.com) even I had answered I had no connection

I downloaded the driver from Ralink website - their driver for Linux.

```
Ralink rt73: Driver Installer - by Kiefer Rodriguez.
Please enter your intended AP name (e.g. 'OfficeWireless' or 'Our_Internet') : Censored
Please enter the WEP key for Toad (or type 'off' if there isnt one, ASCII keys need to be prefixed with 's:' without the quotes and without any spaces.) : off
Please enter your package manager (e.g. 'apt-get' or 'aptitude') : apt-get
Do you currently have an active internet connection? [y/n] : n
Enter the interface name for the device to activate (Most likely 'wlan0') : wlan0
*       Copying rt73 module .tar to /usr/src..
*       Unpacking rt73 module in /usr/src..
Please insert your [Edu/U/Ku]buntu CD, wait 10 seconds then press enter.
%       Gathering required header files from CD, this may take a while..
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [b23710d0071ddbf904b10cfe355c13af-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called: 
'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
Copying package lists...gpgv: Signature made Tue 16 Oct 2007 00:53:09 BST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
Unmounting CD-ROM...
Repeat this process for the rest of the CDs in your set.
*       Added CD-Rom to sources list, now updating list..
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
50% [Connecting to archive.canonical.com] [Connecting to archive.ubuntu.com]   
Err http://archive.canonical.com gutsy Release.gpg                          
  Could not resolve ‘archive.canonical.com’
Err http://archive.ubuntu.com gutsy Release.gpg                             
  Could not resolve ‘archive.ubuntu.com’
Err http://archive.ubuntu.com gutsy/universe Translation-en_GB              
  Could not resolve ‘archive.ubuntu.com’
Err http://archive.canonical.com gutsy/partner Translation-en_GB            
  Could not resolve ‘archive.canonical.com’
42% [Connecting to archive.canonical.com] [Connecting to archive.ubuntu.com]


```

Hrmm, how odd, this seems like an error on my behalf.
Give me a few moments to check the script to see what its doing wrong and get back to you.

Thanks,
Kiefer Rodriguez

---

### Post by Kiefer Rodriguez on 2008-04-18
Ahh I think I may have found the problem, open up 'install_rt73/install_rt73_drivers.py' in a text editor and replace its contents with the following code:

```
#!usr/bin/python						

# Version : 	1.1 *BUILD 2* [See Changelog.]
# Author: 	Kiefer Rodriguez.
#		Thanks to diepruis for a great guide on the serialmonkey driver installation!
# Contact: 	E-mail= [kiefer[dot]rodriguez[at]gmail[dot]com], 
#		IRC= kiefer08 (usually in ##linux on irc.freenode.net)
# Script: 	'Ralink rt73: Driver Installer - by Kiefer Rodriguez.' -- Installs and configures the 'D-Link DWL-G122
#		Rev. C' Wireless Device, and any other device that uses the rt73 chipset.


print "Ralink rt73: Driver Installer - by Kiefer Rodriguez."
# Import 'os' so we can run os.system(<command>) later, very important module.
try:
	import os
except ImportError:
	print "Error: ImportError: Couldnt import the python module 'os'. Aborting Script."
	raise SystemExit
# Initiate the log file for troubleshooting.
log = file("rt73-logfile", 'w')
log.write("Log File Initiated.\n")
log.close()
log = file("rt73-logfile", 'r')

# Get some Info from the user for future use.
try:
	ESSID = str(raw_input("Please enter your intended AP name (e.g. 'OfficeWireless' or 'Our_Internet') : "))
	WEP_KEY = str(raw_input("Please enter the WEP key for " + ESSID + " (or type 'off' if there isnt one, ASCII keys need to be prefixed with 's:' without the quotes and without any spaces.) : "))
	pm = str(raw_input("Please enter your package manager (e.g. 'apt-get' or 'aptitude') : "))
	answer1 = str(raw_input("Do you currently have an active internet connection? [y/n] : "))
	iface = str(raw_input("Enter the interface name for the device to activate (Most likely 'wlan0') : "))
except:
	print "Error: BadInput: Aborting Script."	# Better now then later. :\
	raise SystemExit

print "*	Copying rt73 module .tar to /usr/src.."
os.system("sudo cp rt73-cvs-daily.tar.gz /usr/src")
print "*	Unpacking rt73 module in /usr/src.."
os.system("sudo tar -xvzf /usr/src/rt73-cvs-daily.tar.gz > rt73-logfile")

if answer1 == 'n':		# THE BELOW CODE HAS NOT BEEN EXTENSIVELY TESTED!.
	__0xFFFFa__ = raw_input("Please insert your [Edu/U/Ku]buntu CD, wait 10 seconds then press enter.")
	print "%	Gathering required header files from CD, this may take a while.."
	os.system("sudo apt-cdrom add")
	print "*	Added CD-Rom to sources list, now updating list.."
	os.system("sudo aptitude update")
	print "*	Installing headers.."
	os.system("sudo aptitude install build-essential linux-headers-`uname -r`")
				# THE ABOVE CODE HAS NOT BEEN EXTENSIVELY TESTED!.
else:
	print "*	Installing headers.."
	os.system("sudo " + pm + " install build-essential linux-headers-`uname -r`")
print "*	Compiling rt73 module [1/2].."
try:
	os.system("cd /usr/src/rt73-cvs-2008??????/Module") # Sometimes [2/2] Doesnt 'cd' for some reason.
except:
	os.system("cd /usr/src/rt73-cvs-2008*/Module")
print "*	Compiling rt73 module [2/2].."
os.system("cd /usr/src/rt73-cvs-????*/Module && sudo make > /tmp/rt73-logfile")
warning = str(raw_input("*	Did you just recieve a 'WARNING' message regarding file size? [y/n] : "))
if warning == 'y':
	print "*	Fixing the size issue [known 'bug'].."
	os.system("sudo strip -S rt73.ko > rt73-logfile")
print "*	Installing module.."
os.system("sudo make install > rt73-logfile")
print "*	Bringing down wireless device.."
os.system("sudo ifconfig  " + iface + "  down")
print "*	Removing obsolete modules.."
os.system("sudo modprobe -r rt73usb > rt73-logfile")
# os.system("sudo modprobe -r rt2570 > rt73-logfile") Seems to cause freezing sometimes. Uncomment at your own risk.
os.system("sudo modprobe -r rt2500usb > rt73-logfile")
os.system("sudo modprobe -r rt2x00lib > rt73-logfile")

print "*	Making a backup of /etc/modprobe.d/blacklist to your Home dir. just in-case.."
os.system("sudo cp /etc/modprobe.d/blacklist ~/BACKUP-OF-BLACKLIST")
os.system("sudo cp /etc/modprobe.d/blacklist ~/rt73-blacklist.temp")
print "*	Opening /etc/modprobe.d/blacklist.."
modprobe = file("rt73-blacklist.temp", 'a')
print "*	Writing to /etc/modprobe.d/blacklist.."
modprobe.write("#ADDED BY DWL SCRIPT:\nblacklist rt2570\nblacklist rt73usb\nblacklist rt2500usb\nblacklist rt2x00lib\n#END.")
os.system("sudo mv rt73-blacklist.temp /etc/modprobe.d/blacklist") # Experimental - May be replaced in next version.
print "*	Closing blacklist.."
modprobe.close()
print "*	Deleting temp file[s].."
os.system("sudo rm -rf rt73-blacklist.temp")
print "*	Making sure rt73 installed correctly.."
os.system("sudo modprobe -v rt73 > rt73-logfile")
print "*	Bringing up device.."
os.system("sudo ifconfig " + iface + " up")
print "*	Configuring new device.."
os.system("sudo iwconfig " + iface + " essid " + ESSID)
os.system("sudo iwconfig " + iface + " key " + WEP_KEY)
print "*	Running dhclient.."
os.system("sudo dhclient " + iface + " > rt73-logfile")
print"*		Script complete, You should now be able to connect, if not - Read the FAQ."

# This script is licensed under the GNU public license, You are free to edit, modify and distribute this script as you wish, as long as the original authors name ('Kiefer Rodriguez') remains. =)
```

then try running the script again, let me know how you fare =).

~Kiefer

---

### Post by Juhla Mokka on 2008-04-18
Cheers :KS

```
Ralink rt73: Driver Installer - by Kiefer Rodriguez.
Please enter your intended AP name (e.g. 'OfficeWireless' or 'Our_Internet') : censored
Please enter the WEP key for censored (or type 'off' if there isnt one, ASCII keys need to be prefixed with 's:' without the quotes and without any spaces.) : off
Please enter your package manager (e.g. 'apt-get' or 'aptitude') : apt-get
Do you currently have an active internet connection? [y/n] : n
Enter the interface name for the device to activate (Most likely 'wlan0') : wlan0
*       Copying rt73 module .tar to /usr/src..
*       Unpacking rt73 module in /usr/src..
Please insert your [Edu/U/Ku]buntu CD, wait 10 seconds then press enter.
%       Gathering required header files from CD, this may take a while..
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [b23710d0071ddbf904b10cfe355c13af-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called: 
'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
Copying package lists...gpgv: Signature made Tue 16 Oct 2007 00:53:09 BST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
Unmounting CD-ROM...
Repeat this process for the rest of the CDs in your set.
*       Added CD-Rom to sources list, now updating list..
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Get:1 http://archive.ubuntu.com gutsy Release.gpg [191B]                        
Hit http://archive.ubuntu.com gutsy/universe Translation-en_GB              
Get:2 http://archive.canonical.com gutsy Release.gpg [191B]
Ign http://archive.canonical.com gutsy/partner Translation-en_GB
Hit http://archive.ubuntu.com gutsy/main Translation-en_GB
Hit http://archive.ubuntu.com gutsy Release    
Hit http://archive.canonical.com gutsy Release 
Hit http://archive.canonical.com gutsy/partner Packages
Hit http://archive.ubuntu.com gutsy/universe Packages
Hit http://archive.canonical.com gutsy/partner Sources
Hit http://archive.ubuntu.com gutsy/main Packages
Fetched 382B in 0s (2163B/s)
Reading package lists... Done
*       Installing headers..
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
*       Compiling rt73 module [1/2]..
cd: 1: can't cd to /usr/src/rt73-cvs-2008??????/Module
*       Compiling rt73 module [2/2]..
cd: 1: can't cd to /usr/src/rt73-cvs-????*/Module
*       Did you just recieve a 'WARNING' message regarding file size? [y/n] : n
*       Installing module..
make: *** No rule to make target `install'. Stop.
*       Bringing down wireless device..
*       Removing obsolete modules..
*       Making a backup of /etc/modprobe.d/blacklist to your Home dir. just in-case..
*       Opening /etc/modprobe.d/blacklist..
*       Writing to /etc/modprobe.d/blacklist..
*       Closing blacklist..
*       Deleting temp file[s]..
*       Making sure rt73 installed correctly..
*       Bringing up device..
*       Configuring new device..
*       Running dhclient..
There is already a pid file /var/run/dhclient.pid with pid 6154
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:19:db:9f:f8:7b
Sending on   LPF/wlan0/00:19:db:9f:f8:7b
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 3462 seconds.
*               Script complete, You should now be able to connect, if not - Read the FAQ.

```

---

### Post by Juhla Mokka on 2008-04-18
I did the above, then re-booted. The only difference I noticed, was that the nm-applet did not pop up asking the keyring (I guess because I had taken WAP down).

The nm-applet icon shows black screens and only gives manual configuration option, where it used to have nearby wireless networks listed.

What should I do next?

---

### Post by diepruis on 2008-04-19
> **Juhla Mokka said:**
> Apologies for intruding this thread but I am completely lost what to do!

Tried to install rt73usb driver, but something went wrong. :confused:

Problem here: [http://ubuntuforums.org/showthread.php?p=4740485#post4740485](http://ubuntuforums.org/showthread.php?p=4740485#post4740485)
The area where the thread is does not seem as active as this.

MMmm... please note that this HOWTO is for the rt73 driver, not rt73usb. The latter is a beta driver that will eventually replace the former, but is still not working properly.

Also, rausb0 is *supposes* to disappear. Since the beta release a couple of months ago, rt73 has been using *wlan0*, as is the Linux standard. Please try your ifconfig commands using wlan0 instead of rausb0 and tell us if it worked.

---

### Post by Juhla Mokka on 2008-04-19
Hi, Thanks.

I dowloaded the driver from this site [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html) and it is the one that says RT73. Then I followed this/the other thread as a guide on how to install a driver.
When I go to my Restricted drivers manager, I can see it as "RT73 Wireless LAN Linux Driver".

I am sorry, what do you mean using ifconfig with wlan0? :confused:

---

### Post by Juhla Mokka on 2008-04-19
If I just type ifconfig this is what I get:

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:03:0D:78:BA:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:19:DB:9F:F8:7B  
          inet addr:192.168.1.101  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::219:dbff:fe9f:f87b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18689 errors:0 dropped:0 overruns:0 frame:0
          TX packets:684 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3357991 (3.2 MB)  TX bytes:56802 (55.4 KB)


```

---

### Post by diepruis on 2008-04-19
> **Juhla Mokka said:**
> If I just type ifconfig this is what I get:

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:03:0D:78:BA:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:19:DB:9F:F8:7B  
          inet addr:192.168.1.101  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::219:dbff:fe9f:f87b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18689 errors:0 dropped:0 overruns:0 frame:0
          TX packets:684 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3357991 (3.2 MB)  TX bytes:56802 (55.4 KB)


```

Nevermind! I didn't see the posts above mine! :blush:

Your device should work after running Kiefer's script... does it?

---

### Post by Juhla Mokka on 2008-04-19
No it does not work :'(

Just after I had installed it by hand (before running the script) the little icon still looked 'healthy' - I mean it started looking for networks. Then it froze (the icon) and since then it has only had the manual configuration option. 

I don't know what questions to ask so it is difficult to find help... The first 3 days I spent trying to figure out why the connections hangs, then a few days trying to find out what is my wireless card called, then I found out there is a problem with the driver. Now have installed it, but it feels more broken as I cannot connect at all now, where it used to work for 1 min to 1 hour before. Also I am trying to convince my boyfriend, who's running windows, that linux is better! Not easy! :(

**EDIT - [COLOR="Red"]It does work!  :)[/COLOR] **But.. the icon does not. Do you know how I can select a network (it is a laptop)? Also, why I did not have to write my WAP passphrase? I re-enabled WAP that last night.

---

### Post by diepruis on 2008-04-19
> **Juhla Mokka said:**
> No it does not work :'(

Just after I had installed it by hand (before running the script) the little icon still looked 'healthy' - I mean it started looking for networks. Then it froze (the icon) and since then it has only had the manual configuration option. 

I don't know what questions to ask so it is difficult to find help... The first 3 days I spent trying to figure out why the connections hangs, then a few days trying to find out what is my wireless card called, then I found out there is a problem with the driver. Now have installed it, but it feels more broken as I cannot connect at all now, where it used to work for 1 min to 1 hour before. Also I am trying to convince my boyfriend, who's running windows, that linux is better! Not easy! :(

**EDIT - [COLOR="Red"]It does work!  :)[/COLOR] **But.. the icon does not. Do you know how I can select a network (it is a laptop)? Also, why I did not have to write my WAP passphrase? I re-enabled WAP that last night.

The script provided to you automatically sets up the network. Unfortunately, I don't think rt73 works with network-manager (the icon). Your best bet is to install RutilT that you can get from the serialmonket website. There should be a howto for that on the forums. That program will allow you to configure other networks. Otherwise, you can type "man iwconfig" and take a look there... WARNING: not for the faint of heart, iwconfig and all the accompanying programs have resulted in anuerisms, heart attacks and seizures.

---

### Post by Juhla Mokka on 2008-04-19
Thanks for your help Kiefer & diepruis! At least I have my connection now. I will worry about the rest later. I take my laptop now connects to the strongest network nearby. I was a little puzzled as why I did not have to type my WAP PSK passphrase? maybe i can figure that out...

Thanks again :)

---

### Post by Juhla Mokka on 2008-04-19
Unfortunately I am having problems with RutilT setup. I am stuck in step 6 first line.
[http://ubuntuforums.org/showthread.php?t=554089&highlight=rutilt+setup](http://ubuntuforums.org/showthread.php?t=554089&highlight=rutilt+setup)

First I got a message 'permission denied' then I logged in as root and got 'bash: nameserver: command not found' and with sudo 'sudo: nameserver: command not found'. Any ideas? The how to help thread seems to be closed...

**EDIT - I have moved this to the HOW TO RutilT thread** [http://ubuntuforums.org/showthread.php?p=4745960#post4745960](http://ubuntuforums.org/showthread.php?p=4745960#post4745960)

---

### Post by Kiefer Rodriguez on 2008-04-19
> **Juhla Mokka said:**
> Thanks for your help Kiefer & diepruis! At least I have my connection now. I will worry about the rest later. I take my laptop now connects to the strongest network nearby. I was a little puzzled as why I did not have to type my WAP PSK passphrase? maybe i can figure that out...

Thanks again :)

You are more than welcome, Im happy to have confirmed the script works :)
Enjoy your wireless buddie.

~Kiefer

---

### Post by diepruis on 2008-04-20
> **Kiefer Rodriguez said:**
> You are more than welcome, Im happy to have confirmed the script works :)
Enjoy your wireless buddie.

~Kiefer

I've added a link to the front page, hopefully this will help people get online quicker and easier.

Here's to Kiefer and python ;)

---

### Post by Kiefer Rodriguez on 2008-04-20
> **diepruis said:**
> I've added a link to the front page, hopefully this will help people get online quicker and easier.

Here's to Kiefer and python ;)

Heh Cheers buddie :D

~Kiefer

---

### Post by IHATEDLINK on 2008-04-25
Eeeekk can't get it done!Network manager gives me the following:
Network connection: wlan0:avahi
When i click on it this windows shows up: 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=67226&stc=1&d=1209178942[/IMG]

HELP PLEASE, I've been trying to make this work over a month now..
I did everything the tutorial said, HELP!!

When i tried to connect to my WI-FI network over the terminal (just like the HOWTO said) i got the fallowing:

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1b:11:20:d9:1c
Sending on   LPF/wlan0/00:1b:11:20:d9:1c
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
paco@paco-ubuntu:/usr/src/rt73-cvs-2008042520/Module$

---

### Post by dwp0980 on 2008-04-26
I'm also getting the same problem as the user above.  I think this is something that's wrong with Hardy.  The only way I've got this to work so far is to take down the offending wlan0:avahi then issuing the dhclient command.

Any help gratefully received!

---

### Post by dwp0980 on 2008-04-26
I'm also getting the same problem as the user above.  I think this is something that's wrong with Hardy.  The only way I've got this to work so far is to take down the offending wlan0:avahi then issuing the dhclient command.

Any help gratefully received!

---

### Post by danpos on 2008-04-26
@diepruis

First all thanks for the detailed howto in order to fix the rt73usb wireless device issue. Very appreciated! :)

Currently I'm running **Hardy Heron** (i386) on my notebook and desktop machines and on the mobile the problem with lost of connection to AP (**wlan0: No ProbeResp from current AP XX:XX:XX:XX:XX:XX - assume out of range.**), using the driver delivered by Ubuntu's installation, was driving my crazy...

I did follow your guide until step 13 and so I did install the Wicd application in order to manage my connections (wireless/wired ones). One suggestion is to modify the Makefile (into Module directory) in order to install the firmware at correct place:

```
FIRM_DIR :=    /lib/firmware/2.6.24-16-generic
```

(in my case uname -r == 2.6.24-16-generic)

With regards on Wicd, the instructions present at [FAQ page]("http://wicd.sourceforge.net/wiki/doku.php?id=faq") guide the user to properly set Wicd up.

That's all. :)

Regards,

Danpos.

---

### Post by wzwilliam on 2008-04-27
Hi there. I was using my RT73 wifi adapter using the tutorial on this thread and the serial monkey drivers. After updating from gutsy to hardy it stopped working, the wlan adapter is not even list when i type lshw on console. Any ideas of what could have happened?

---

### Post by Austin_KW on 2008-04-27
> **wzwilliam said:**
> Hi there. I was using my RT73 wifi adapter using the tutorial on this thread and the serial monkey drivers. After updating from gutsy to hardy it stopped working, the wlan adapter is not even list when i type lshw on console. Any ideas of what could have happened?
You need to reinstall the driver
make and make install again
You will need to do this for any new kernel.

---

### Post by T4_ on 2008-04-27
Same problem here: no DHCPOFFERS received. (Using Kubuntu 7.04)

When I start Wireless Assistant (to see a bit more), it sees the network and tries to connect, but fails.

I have yet to try the Python script (at work now), I will do that in the morning. Hopefully that'll sort it out, but if anyone has any suggestions in the meantime they'll be greatly appreciated :)

---

### Post by wzwilliam on 2008-04-28
> **Austin_KW said:**
> You need to reinstall the driver
make and make install again
You will need to do this for any new kernel.
results on make:
```
make: *** /lib/modules/2.6.24-16-rt/build: No such file or directory. Stop.
*** Module rt73.ko built successfully
```

results on make install:
```
*** Install module in /lib/modules/2.6.24-16-rt/extra ...
make: *** /lib/modules/2.6.24-16-rt/build No such file or directory. Stop.
make: *** [modules_install] Error 2
```

I really don't understand the advanced aspects of linux, but is it something like it can't find my correct kernel version?
Thank you for any input.

---

### Post by Austin_KW on 2008-04-28
looks like you have changed your kernel verion to some real-time one, try the following to create the missing dirs;
```

 sudo aptitude install build-essential linux-headers-`uname -r`
 make
 sudo make install

```

> **wzwilliam said:**
> results on make:
```
make: *** /lib/modules/2.6.24-16-rt/build: No such file or directory. Stop.
*** Module rt73.ko built successfully
```

results on make install:
```
*** Install module in /lib/modules/2.6.24-16-rt/extra ...
make: *** /lib/modules/2.6.24-16-rt/build No such file or directory. Stop.
make: *** [modules_install] Error 2
```

I really don't understand the advanced aspects of linux, but is it something like it can't find my correct kernel version?
Thank you for any input.

---

### Post by wzwilliam on 2008-04-28
> **Austin_KW said:**
> looks like you have changed your kernel verion to some real-time one, try the following to create the missing dirs;
```

 sudo aptitude install build-essential linux-headers-`uname -r`
 make
 sudo make install

```

sorry if it's a stupid question, but the 'uname -r' is exactly like it appears or should i change the 'uname' part for something? because after entering the command i have something with:
```
Couldn't find any package whose name description matched "linux-headers-uname -r"
```
where did i mess?

---

### Post by Austin_KW on 2008-04-28
> **wzwilliam said:**
> sorry if it's a stupid question, but the 'uname -r' is exactly like it appears or should i change the 'uname' part for something? because after entering the command i have something with:
```
Couldn't find any package whose name description matched "linux-headers-uname -r"
```
where did i mess?

uname -r is a command, quoting it `uname -r` will expand the command when it is run (in your case to linux-headers-2.6.24-16-rt)

---

### Post by wzwilliam on 2008-04-28
> **Austin_KW said:**
> uname -r is a command, quoting it `uname -r` will expand the command when it is run (in your case to linux-headers-2.6.24-16-rt)

i guess i know what i missed. should i run this command on /usr/src/rt73-cvs-... or at any other folder (i ran it in /home) will do the job?

---

### Post by wzwilliam on 2008-04-28
well, tried it again and still the same error after sudo make and sudo make install :(

---

### Post by Austin_KW on 2008-04-28
Odd, a quick look at the dependancies for linux-headers-2.6.24-16-rt shows it creates lib/modules/2.6.24-16-rt/build which was your make error..

---

### Post by wzwilliam on 2008-04-29
I took a look a the folder is there, except for the /build. I even created the folder /build myself, but i still have the same errors after running make and make install. Any tips on uninstalling it so i can start it all over?

---

### Post by Ezetreal on 2008-05-01
> **bianchino said:**
> unfortunately "wlan0" was a typo in the post to the forum. I entered correctly "wlan1", and, as I wrote, I get:

ifconfig wlan1 up
SIOCSIFFLAGS: Invalid argument

If I try 
iwconfig wlan1 mode managed

I get
network is down

I really don't know what else to do...


I am having the same problem, was this ever solved ?

I am trying to convert a friend to ubuntu, she'll run back to windows if her wireless doesn't work !  :(

Thanks for the help

---

### Post by travismoore on 2008-05-01
Sorry dono if I'm just being a retard because i don't know how to use the terminal properly.

```
travis@travis-desktop:~$ cd /usr/src/rt73-cvs-yyyymmddhh/Module
bash: cd: /usr/src/rt73-cvs-yyyymmddhh/Module: No such file or directory

```

whats wrong?

---

### Post by Ezetreal on 2008-05-01
The yyyymmddhh refers to a number that comes in the directory name once you have extracted it, in /usr/src type dir and see what the directory name actually is, or just use "tab" after typing /usr/src/rt73  to fill in the name.

good luck

---

### Post by thatrandomguy on 2008-05-01
Hey,

I just tried that tutorial and everything was going well until it tried to get an ip address (the sudo dhclient wlan0 on step 14.)

Here is the Message i got:

Listening on LPF/wlan0/00:17:3f:ad:79:c8
Sending on   LPF/wlan0/00:17:3f:ad:79:c8
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received
No working leases in persistent database - sleeping.


Can anyone help?

Thanks
Chris

---

### Post by Gloria81 on 2008-05-01
After updating to Hardy Heron, I found the network doesn't come up at step 14 due to "SIOCSIFFLAGS failed: Invalid argument".

With Google I found an open bug on Hardy Heron with the same message ([https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/191745](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/191745)). Will see how this continues.

---

### Post by Austin_KW on 2008-05-01
Make sure that you are running just the legacy driver

check what drivers are loaded
```
lsmod | grep usbcore

```

---

### Post by Ezetreal on 2008-05-02
Austin, I don't know if you were responding to the FFLAG error, but here is my output for lsmod | grep usbcore

4 rt73,ehci_hcd,ohci_hcd       it says used by 4, only lists those three.


Thanks for the help

---

### Post by Austin_KW on 2008-05-02
> **Ezetreal said:**
> Austin, I don't know if you were responding to the FFLAG error, but here is my output for lsmod | grep usbcore

4 rt73,ehci_hcd,ohci_hcd       it says used by 4, only lists those three.


Thanks for the help

I was responding to all the SIOCSIFFLAGS errors.
I have something similar before but I don't remember if it was a conflicting legacy/beta driver or perhaps ndiswrapper. 

Also if you have dual booted windows and have restarted ubuntu from windows there can be a driver init problem.

Unplug the usb adapter
Reinsert the adapter
Retry the config commands.

---

### Post by Ezetreal on 2008-05-02
I am not sure I understood this correctly. I am only running Hardy Heron on a laptop. You want me to unplug the usb adapter ? as in unscrew the laptop and unplug it ? 

I am not sure i can do that considering that it is not my latop :)

Thanks anyway, but i'll wait a little bit and hope for another solution :)

---

### Post by Austin_KW on 2008-05-02
> **Ezetreal said:**
> I am not sure I understood this correctly. I am only running Hardy Heron on a laptop. You want me to unplug the usb adapter ? as in unscrew the laptop and unplug it ? 

I am not sure i can do that considering that it is not my latop :)

Thanks anyway, but i'll wait a little bit and hope for another solution :)


No, just remove the usb dongle, wait a few seconds and reinsert it. Sometimes there is a problem loading the adapter firmware.
After you reinsert the adapter check the end of the log for errors with the following command
```
dmesg
```

---

### Post by Ezetreal on 2008-05-02
The wireless card on this laptop is integrated, not a usb dongle.
I don't know if I got the wrong driver for the card, but I don't think so, that's the one that was being used by ubuntu, the rt-73...

lspci gives 

ethernet controller realtek semiconductor

lsusb gives

Micro Star international <---------  i have no idea what it is.


Thanks Austin

Sorry for the trouble

---

### Post by wzwilliam on 2008-05-02
ok, i've just given up on the upgrade thing and had a fresh install on hardy heron. After installation, the old malfunctioning issue came back, so i started following the guide. on step 12, after the command modprobe -v rt73 i've got:
```
insmod /lib/modules/2.6.24-16-rt/extra/rt73.ko 
FATAL: Error inserting rt73 (/lib/modules/2.6.24-16-rt/extra/rt73.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```
how can i solve this?

---

### Post by Austin_KW on 2008-05-02
Ok my bad assumption, did not realise it was an internal module on the usb bus.

It may still be an initialisation issue.
check the dmesg comand for errors
 
> **Ezetreal said:**
> The wireless card on this laptop is integrated, not a usb dongle.
I don't know if I got the wrong driver for the card, but I don't think so, that's the one that was being used by ubuntu, the rt-73...

lspci gives 

ethernet controller realtek semiconductor

lsusb gives

Micro Star international <---------  i have no idea what it is.


Thanks Austin

Sorry for the trouble

---

### Post by Austin_KW on 2008-05-02
> **wzwilliam said:**
> ok, i've just given up on the upgrade thing and had a fresh install on hardy heron. After installation, the old malfunctioning issue came back, so i started following the guide. on step 12, after the command modprobe -v rt73 i've got:
```
insmod /lib/modules/2.6.24-16-rt/extra/rt73.ko 
FATAL: Error inserting rt73 (/lib/modules/2.6.24-16-rt/extra/rt73.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```
how can i solve this?

Any make errors?
and what does *dmesg* say

---

### Post by wzwilliam on 2008-05-02
> **Austin_KW said:**
> Any make errors?
and what does *dmesg* say

a warning in make:
```
WARNING: "there_is_no_init_MUTEX_LOCKED_for_RT_semaphores" [usr/src/rt73-cvs-2008050207/Module/rt73.ko] undefined!
```

results of dmesg are going attached instead, since i have no internet connection on my laptop and it appeared truncated on the .txt file.

---

### Post by Austin_KW on 2008-05-02
The dmesg is full of "evbug.c: Event...."

To get rid of these add the following to /etc/modprobe.d/blacklist
```
blacklist evbug
```

also unload the running evbug
```
 sudo modprobe -r evbug
```

---

### Post by Austin_KW on 2008-05-02
@wzwilliam

It is something to do with the -rt kernel. The generic kernel works fine

---

### Post by Ezetreal on 2008-05-02
Thanks Austin, I'll give it a go after the weekend, i do not have access to the laptop anymore.

Cheers

---

### Post by wzwilliam on 2008-05-02
> **Austin_KW said:**
> @wzwilliam

It is something to do with the -rt kernel. The generic kernel works fine

so what steps should i follow?

---

### Post by wzwilliam on 2008-05-05
help, anyone? :(

---

### Post by jtrindle on 2008-05-05
I've got the generic kernel as well as the -rt kernel installed on my system.  If you install the generic kernel from aptitude you should see multiple options in your Grub boot menu (when you first start).

If you boot under the generic kernel and make the serialmonkey drivers the same way you did before, it will use the generic headers instead of the -rt headers and compile.

However, I've built the rt73 driver under the generic kernel.  It builds fine but I get no connection!!  I've reverted to the rt73usb while I try to figure that out.

---

### Post by nieve on 2008-05-07
Thanks for this excellet how to
It works for me with mimo usb g in ubuntu 8.04
just it does not start when I start, I have to make ifconfig, iwconfig essid, key and dhclient
but it is not too much work so thanks a lot, I can surf because of you

---

### Post by diepruis on 2008-05-07
> **nieve said:**
> Thanks for this excellet how to
It works for me with mimo usb g in ubuntu 8.04
just it does not start when I start, I have to make ifconfig, iwconfig essid, key and dhclient
but it is not too much work so thanks a lot, I can surf because of you

No problem :) Check out RutilT, it might automate these tasks for you.

---

### Post by jtrindle on 2008-05-07
I've got the rt73 driver from serialmonkey working under the -generic kernel.  I had to blacklist the other rt modules (rt2500usb and rt2x00lib as well as rt73usb) before it would work.

Now my VNC works for extended periods.  However, I *always* get about 36-40% packet loss when pinging from a neighboring machine.  This drops 3 or 4 packets every 8 seconds or so.  There are no odd messages in dmesg or syslog.  This causes noticable lag in remote operation.

I'd like to get the -rt kernel back, and I'd like to get rid of the lag.  I've downloaded the 2.6.25 kernel to give that a try, but don't want to reboot into it from remote.

Any ideas on this extensive packet loss?  I'm seeing good signal strength and I've moved the channel number away from the neighbors' channels with no effect (I'm now on 1, they're on 6 and 11).

---

### Post by gdw2 on 2008-05-07
I have the Everex StepNote ST5340T laptop.  I just installed 8.04 (Hardy).  From what I read, it's supposed to work out of the box.  I found that to be true when I recently traveled and connected to an unencrypted hotel network, but at home, even when I disable the encryption, the out-of-the-box drivers won't connect me to my Netgear router (weird huh?).

So, this is what I did:

[LIST]
[*]Follow the instructions in the first post of this thread (they work perfectly)
[*]sudo apt-get remove network-manger
[*]sudo apt-get install rutilt
[/LIST]

Rutilt will be in the Applications > Internet folder

I'm not positive that network-manager won't work or that rutilt is superior. 

So now it works, WPA and all!

---

### Post by diepruis on 2008-05-08
> **gdw2 said:**
> I have the Everex StepNote ST5340T laptop.  I just installed 8.04 (Hardy).  From what I read, it's supposed to work out of the box.  I found that to be true when I recently traveled and connected to an unencrypted hotel network, but at home, even when I disable the encryption, the out-of-the-box drivers won't connect me to my Netgear router (weird huh?).

So, this is what I did:

[LIST]
[*]Follow the instructions in the first post of this thread (they work perfectly)
[*]sudo apt-get remove network-manger
[*]sudo apt-get install rutilt
[/LIST]

Rutilt will be in the Applications > Internet folder

I'm not positive that network-manager won't work or that rutilt is superior. 

So now it works, WPA and all!

Great! Good to see that RutilT made it into the repositories.

---

### Post by wzwilliam on 2008-05-08
Thank you diepruis for the guide and thank you Austin_KW for all the help. Just moved to the generic kernel and my wireless adpter is working fine now.
:)

---

### Post by stansford on 2008-05-11
> **diepruis said:**
> Great! Good to see that RutilT made it into the repositories.

Diepruis - Thanks for the how to info. I have this working under 8.04 with WPA, though not all the time...and there are some strange goings on:
1. Can't get the wifi to load at boot even though I have what I think are the right entries in /etc/network/interfaces file. This used to work all the time under Feisty with the Serialmonkey drivers.
2. Rutilt doesn't connect it either, although it says it has by the icon in the Gnome panel, but when you check, it hasn't got an ip address...so what's that all about - when is a connection not a connection?

By the way I have uninstalled network-manager, yet there is no consistency in when I can connect. Sometimes I get no dhcp offers and sometimes I do...what's that all about given it's just me, the wife's pc and the router!

When I get a connection it is sometimes by doing a connect a few times repeatedly from rutilt, that seems to work eventually. Or sometimes I will do an "sudo ifup -a" and that does the trick. But why doesn't it connect reliably?

A few musings here, any answers appreciated, but hey, at least I'm writing this via rt73 wifi, so thanks for the work!

---

### Post by Austin_KW on 2008-05-11
I have seen problems with rutilt not getting an ip address, especially on a borderline connection.

I think Rutilt is reporting the association status, ie you are connected to the wireless network (layer 2) but you do not have an ip addresss (layer 3).

If you have problems with rutilt getting an ip address try running dhcp client manually from the command line.
```
sudo dhclient wlan0
```
If you look at /usr/local/share/apps/rutilt/set_ip.sh this is all that rutilt does so I am not sure why it does not work consistently

---

### Post by diepruis on 2008-05-13
> **Austin_KW said:**
> I have seen problems with rutilt not getting an ip address, especially on a borderline connection.

I think Rutilt is reporting the association status, ie you are connected to the wireless network (layer 2) but you do not have an ip addresss (layer 3).

If you have problems with rutilt getting an ip address try running dhcp client manually from the command line.
```
sudo dhclient wlan0
```
If you look at /usr/local/share/apps/rutilt/set_ip.sh this is all that rutilt does so I am not sure why it does not work consistently

As you said, the problem may be with a weak signal. Perhaps sever packet loss is causing the DHCP offers to be lost?

---

### Post by EnigMattic on 2008-05-14
Hi
Is there anyway to do this without removing network manager?

---

### Post by diepruis on 2008-05-14
> **EnigMattic said:**
> Hi
Is there anyway to do this without removing network manager?

You can try it without network manager, this works in some cases. However, the driver does not support it, so why do you need it?

---

### Post by EnigMattic on 2008-05-14
> **diepruis said:**
> You can try it without network manager, this works in some cases. However, the driver does not support it, so why do you need it?

Fair point, it DOES work. I was just a bit worried about the dependencies of ubuntu-desktop. I'm using Hardy amd64 and an Asus WL-167G (RT73 version). Would it be possible simply to disable network manager rather than completely remove it?

---

### Post by Austin_KW on 2008-05-14
Network manager should ignore the wlan interface if you add the auto wlan0 ...  to the /etc/network/interfaces file.

---

### Post by diepruis on 2008-05-14
> **Austin_KW said:**
> Network manager should ignore the wlan interface if you add the auto wlan0 ...  to the /etc/network/interfaces file.

Austin_KW is probably right... I tried to disable network-manager for a while, but I just couldn't manage it. So I thought I'd recommend completely removing it, to avoid as much confusion as I could.

---

### Post by EnigMattic on 2008-05-14
> **diepruis said:**
> Austin_KW is probably right... I tried to disable network-manager for a while, but I just couldn't manage it. So I thought I'd recommend completely removing it, to avoid as much confusion as I could.

Ok, thanks guys. I'll just leave it uninstalled no biggy. Thanks for the tutorial btw, diepruis! Works a treat :KS

---

### Post by diepruis on 2008-05-15
> **EnigMattic said:**
> Ok, thanks guys. I'll just leave it uninstalled no biggy. Thanks for the tutorial btw, diepruis! Works a treat :KS

No worries :P

---

### Post by stansford on 2008-05-15
> **Austin_KW said:**
> I have seen problems with rutilt not getting an ip address, especially on a borderline connection.

I think Rutilt is reporting the association status, ie you are connected to the wireless network (layer 2) but you do not have an ip addresss (layer 3).

If you have problems with rutilt getting an ip address try running dhcp client manually from the command line.
```
sudo dhclient wlan0
```
If you look at /usr/local/share/apps/rutilt/set_ip.sh this is all that rutilt does so I am not sure why it does not work consistently


When I try and do a "sudo dhclient wlan0" at the command line, I mostly get the "no offers received so sleeping" message.
I don't understand why I'm not getting an offer from the router, but assume it must be a rt73 problem, because the same thing with the eth0 via the rj45 connection works first time every time. Also the signal strength is good and I'm physically next door to the router. 
There just doesn't seem to be a reliable way to connect which is frustrating as I end up trying; dhclient, ifup, network restart in a fraught attempt to get the b****r connected.

---

### Post by Austin_KW on 2008-05-15
> **stansford said:**
> When I try and do a "sudo dhclient wlan0" at the command line, I mostly get the "no offers received so sleeping" message.
I don't understand why I'm not getting an offer from the router, but assume it must be a rt73 problem, because the same thing with the eth0 via the rj45 connection works first time every time. Also the signal strength is good and I'm physically next door to the router. 
There just doesn't seem to be a reliable way to connect which is frustrating as I end up trying; dhclient, ifup, network restart in a fraught attempt to get the b****r connected.

Try with encryption temporarily turned off. Is the behaviour any different?

Also try changing the wireless channel at the router; try channels 1,6,11,13 (one of these usually gives a good connection)

---

### Post by stansford on 2008-05-15
> **Austin_KW said:**
> Try with encryption temporarily turned off. Is the behaviour any different?

Also try changing the wireless channel at the router; try channels 1,6,11,13 (one of these usually gives a good connection)

Thanks for those suggestions, I'll give them a go later and let you know. 

One thing though, say it does connect OK without encryption, what am i going to do then?....because I can't run the network without encryption...I'll have everyone in the neighbourhood surfing for free off my system!!

---

### Post by stansford on 2008-05-15
oh - forgot to say, the rt73 worked flawlessly with serialmonkey under Feisty. It even connected itself on bootup....that's why I wonder if it's some change in some bit of ubuntu or even the serialmonkey drivers...

---

### Post by Austin_KW on 2008-05-15
> **stansford said:**
> Thanks for those suggestions, I'll give them a go later and let you know. 

One thing though, say it does connect OK without encryption, what am i going to do then?....because I can't run the network without encryption...I'll have everyone in the neighbourhood surfing for free off my system!!

It is just a test; Way back when, I had to put delays in the command sequence to get wpa to reliably work. Just want to eliminate this, as the wpa command sequence can be tricky :)

Also forget to ask, you are not hiding SSID ? as it can complicate the connection sequence.

And no other rt73 drivers loaded, check with "lsmod | grep usbcore"

---

### Post by stansford on 2008-05-15
> **Austin_KW said:**
> It is just a test; Way back when, I had to put delays in the command sequence to get wpa to reliably work. Just want to eliminate this, as the wpa command sequence can be tricky :)

Also forget to ask, you are not hiding SSID ? as it can complicate the connection sequence.

And no other rt73 drivers loaded, check with "lsmod | grep usbcore"

Austin_KW - Fair enough, I can't do it now, but will run these tests tonight and post back. 
Re SSID, no it is not hidden, I don't hide it by default so I'm certain. 
Re other rt73 drivers, all the drivers mentioned in diepruis guide have been removed and blacklisted as per the instructions, but again I will post back the result of the lsmod in case something strange has happened.

I did wonder about recompiling the rt73 in debug mode to see whether any log created gave clues to the problem. Have you ever done this and if so was it useful?

Also does Rutilt have any logging you can look at or configure at all??

thanks for your help

---

### Post by stansford on 2008-05-15
> **stansford said:**
> Austin_KW - Fair enough, I can't do it now, but will run these tests tonight and post back. 
Re SSID, no it is not hidden, I don't hide it by default so I'm certain. 
Re other rt73 drivers, all the drivers mentioned in diepruis guide have been removed and blacklisted as per the instructions, but again I will post back the result of the lsmod in case something strange has happened.

I did wonder about recompiling the rt73 in debug mode to see whether any log created gave clues to the problem. Have you ever done this and if so was it useful?

Also does Rutilt have any logging you can look at or configure at all??

thanks for your help

Austin_KW. OK I checked the lsmod and this is what it returned:

$ lsmod | grep usbcore
usbcore               146028  3 rt73,uhci_hcd
$

so I think all is well there. I have been getting better connection tonight without removing the security, but I wanted to ask you what entries do you think you should have in /etc/network/interfaces. I've seen some posts that say you should up and down your wlan0 a couple of times and that helps, but what would be really useful would be to know what you use.

I haven't connected without encryption yet. I want to see if this is the start of a more stable period. 

thanks

---

### Post by Austin_KW on 2008-05-15
> **stansford said:**
> Austin_KW. OK I checked the lsmod and this is what it returned:

$ lsmod | grep usbcore
usbcore               146028  3 rt73,uhci_hcd
$

so I think all is well there. I have been getting better connection tonight without removing the security, but I wanted to ask you what entries do you think you should have in /etc/network/interfaces. I've seen some posts that say you should up and down your wlan0 a couple of times and that helps, but what would be really useful would be to know what you use.

I haven't connected without encryption yet. I want to see if this is the start of a more stable period. 

thanks

My  interfaces file was the same as the original post, It is currently on a windows machine. I am using an rt2500 with the serialmonkey driver and the sequence is the same.

Try a different channel, I had a problem at a house today where it could not get an IP address. It was due to a 2.4Ghz video sender and I solved it by changing the channel

---

### Post by brocruit on 2008-05-16
I'm not using Ubuntu on the laptop(Suse 10.3), but all works great when logged into gnome term as root and take out all the sudos.  Only place anywhere online that was helpful with this driver install.

I was beating my head against this even after I got it working because I could not connect with WEP.  Whenever I leave it unsecure and login under windows on my other machine it kindly reports to me its found and an xbox 360 on my network and asks if I want to configure media center.  Can't blame my neighbors, cause I'd probably do it too, but I like my bandwidth and not interested in sharing.  

I was looking through my router (Trendnet TEW-633GR) and found it has MAC address filtering that can be activated to only filter wireless.  So I added just my laptop's MAC address as the only one allowed and now all is happy.  Except I have to figure out something thats probably been mentioned; I have to up and down wlan0 everytime I reboot... kinda dumb.

---

### Post by stansford on 2008-05-16
> **Austin_KW said:**
> My  interfaces file was the same as the original post, It is currently on a windows machine. I am using an rt2500 with the serialmonkey driver and the sequence is the same.

Try a different channel, I had a problem at a house today where it could not get an IP address. It was due to a 2.4Ghz video sender and I solved it by changing the channel

Austin_KW - OK I've moved to channel 11 on the router and now I seem to be able to connect 3/3 for the times I've tried. Also connecting at boot is working. I'll monitor it over the next week and see if this continues, but it is better than before.
Many thanks for your help...and fingers crossed.

---

### Post by Austin_KW on 2008-05-16
> **brocruit said:**
> I'm not using Ubuntu on the laptop(Suse 10.3), but all works great when logged into gnome term as root and take out all the sudos.  Only place anywhere online that was helpful with this driver install.

I was beating my head against this even after I got it working because I could not connect with WEP.  Whenever I leave it unsecure and login under windows on my other machine it kindly reports to me its found and an xbox 360 on my network and asks if I want to configure media center.  Can't blame my neighbors, cause I'd probably do it too, but I like my bandwidth and not interested in sharing.  

I was looking through my router (Trendnet TEW-633GR) and found it has MAC address filtering that can be activated to only filter wireless.  So I added just my laptop's MAC address as the only one allowed and now all is happy.  Except I have to figure out something thats probably been mentioned; I have to up and down wlan0 everytime I reboot... kinda dumb.

Many devices will connect to the first available unsecured network (especially if you use the default SSID on a router). So you neighbors may not even be aware that they are using your connection.

Mac address filtering only protects against connecting accidentally to a network. I will not stop anyone who understands networking, Changing you MAC address to one you have 'seen' working is as easy as " ifconfig wlan0 hw ether **:**:**:**:**:**"

WEP is only a little better, It takes me 20 mins to crack any wep but I have only done it as a demo. Most crackers can break wep in 2 mins.

Usually problems connecting with encryption are due to the wrong password or incorrect use of the commands. 

That said you really should use WPA-PSK encryption with a 20+ character password. 

If you are having problems getting encryption to work try rutilt, it is a little graphical utility to manage ralink wireless chipsets and you should find it in your package management (yast or whatever suse uses these days).

---

### Post by brocruit on 2008-05-16
Actually I spent all night with and narrowed it down to what I believe is bad motherboard.  I posted too soon because it started dropping connection after a few minutes and i couldn't get it back up without restarting.  Reseating device and wlan0 down/wlan0 up had no effect on being able to reconnect.  I'd have to restart and then bring the device down and up.
After getting the same behavior on the Xubuntu live cd.  I took the nic and trusty live cd to another computer and wpa or wep works just fine and pretty fast.  I guess a lot of headache for nothing.

---

### Post by peterballard on 2008-05-16
Hi all,

I followed all the instructions at the first post in this thread, and I got connectivity (new PC, dual boot with XP, Ubuntu 8.04, D-Link DWA-110 wireless adapter). Occasionally it would not connect on startup, but "sudo dhclient wlan0" would connect for me, I think.

With connectivity finally up, I then installed some other packages I wanted, all using the Synaptic Package Manager:
- ubuntu-restricted-extras  (so I could run Flash player)
- emacs
- gawk
- fetchmail
- sendmail, which required me to install m4, procmail, sendmail-base, sendmail-bin, sendmail-cf, sensible-mda.

(the common thread here is that email on emacs uses sendmail).

sendmail caused boot to take about 10 minutes, so I decided to uninstall sendmail, sendmail-base, sendmail-bin, sendmail-cf, and sensible-mda, and use Evolution for my email instead.

Since the next day (possibly the first reboot after using Evolution), I have not been able to reconnect. Re-installing sendmail etc was no help.

I believe the only system files I have changed (as part of following the instructions in this thread) are these two:

/etc/modprobe.d/blacklist, to which I've added:
```

blacklist rt73usb
blacklist rt2570
blacklist rt2500usb
blacklist rt2x00lib
blacklist dr71wu

```

and /etc/network/interfaces to which I've added:

```

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid ballardnet
pre-up iwconfig wlan0 key "off"

```

(The instructions at the start of this thread said to use "YOUR_ESSID" but gave no indication what "YOUR_ESSID" might be, so I made up the name "ballardnet").

Can anyone suggest what might be screwed up, and what files I should check?

I know it's not a hardware problem because it's a dual boot system and Windows XP connects every time.

Thanks in advance...

---

### Post by dmub82 on 2008-05-17
> **peterballard said:**
> Hi all,
(The instructions at the start of this thread said to use "YOUR_ESSID" but gave no indication what "YOUR_ESSID" might be, so I made up the name "ballardnet").

Can anyone suggest what might be screwed up, and what files I should check?
Thanks in advance...

That's your problem. You're supposed to replace YOUR_ESSID to match the ESSID set on your router. Easy way if you don't know this already: open a terminal, type ```
sudo iwlist scan
``` and you should get a list of all the wireless networks your card can see. Figure out which one is yours and use the essid from that listing.

If that doesn't work, get a wired connection to your router (from that machine or another, doesn't matter), go to its configuration page (to get there, you'll go to an address something like 192.168.1.1 or 192.168.2.1 or 192.168.1.100, the address will be in the manual for your router or you can google your brand and model). Find the setting labeled SSID or ESSID or the name of your wireless network, and that's what you need to put in your /etc/network/interfaces.

---

### Post by peterballard on 2008-05-17
> **dmub82 said:**
> That's your problem. You're supposed to replace YOUR_ESSID to match the ESSID set on your router. Easy way if you don't know this already: open a terminal, type ```
sudo iwlist scan
``` and you should get a list of all the wireless networks your card can see. Figure out which one is yours and use the essid from that listing.


Thanks, that worked. According to "sudo iwlist scan" the ESSID name was simply "default" (including the double quotes), so that's what I put in my /etc/network/interfaces, i.e. in all I added these lines to my original /etc/network/interaces:
```

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid "default"
pre-up iwconfig wlan0 key "off"

```

Now my connection comes up every time (although one time it did drop out after a while). 

What's more, sendmail now doesn't delay my reboot forever (presumably because sendmail comes up quickly if the internet connection is up), so I can keep sendmail and use emacs+RMAIL for my email after all. Luddite bliss!

--
Peter

---

### Post by travismoore on 2008-05-17
Having some errors please help =D

```
travis@travis-desktop:/usr/src$ ls -alh rt73.ko
ls: cannot access rt73.ko: No such file or directory
travis@travis-desktop:/usr/src$ sudo make install
make: *** No rule to make target `install'. Stop.

```

---

### Post by Austin_KW on 2008-05-17
> **travismoore said:**
> Having some errors please help =D

```
travis@travis-desktop:/usr/src$ ls -alh rt73.ko
ls: cannot access rt73.ko: No such file or directory
travis@travis-desktop:/usr/src$ sudo make install
make: *** No rule to make target `install'. Stop.

```

You need to change to the Module directory
```
cd rt73*/Module 
``` and then continue with sudo make ...

---

### Post by travismoore on 2008-05-17
> **Austin_KW said:**
> You need to change to the Module directory
```
cd rt73*/Module 
``` and then continue with sudo make ...

Thanks but i have another error now :eek:

```
travis@travis-desktop:~$ cd /usr/src
travis@travis-desktop:/usr/src$ cd rt73*/Module
travis@travis-desktop:/usr/src/rt73-cvs-2008051712/Module$ sudo make install
[sudo] password for travis: 
!!! rt73.ko does not exist: run 'make'
make: *** [modules_install] Error 1
travis@travis-desktop:/usr/src/rt73-cvs-2008051712/Module$ 

```

---

### Post by Austin_KW on 2008-05-17
> **travismoore said:**
> Thanks but i have another error now :eek:

```
travis@travis-desktop:~$ cd /usr/src
travis@travis-desktop:/usr/src$ cd rt73*/Module
travis@travis-desktop:/usr/src/rt73-cvs-2008051712/Module$ sudo make install
[sudo] password for travis: 
!!! rt73.ko does not exist: run 'make'
make: *** [modules_install] Error 1
travis@travis-desktop:/usr/src/rt73-cvs-2008051712/Module$ 

```

You are skipping more steps
```
sudo make
```

---

### Post by travismoore on 2008-05-17
How do i know what "my network name" is?

---

### Post by Austin_KW on 2008-05-17
> **travismoore said:**
> How do i know what "my network name" is?

It is the ESSID name broadcast by your router, could be anything. Look at your router config pages or use the scan command to locate all SSIDs 
```
sudo iwlist scan
```

---

### Post by travismoore on 2008-05-17
thanks

this appears to have not worked:

```
travis@travis-desktop:/usr/src/rt73-cvs-2008051712/Module$ sudo iwconfig wlan0 essid belkin54g
travis@travis-desktop:/usr/src/rt73-cvs-2008051712/Module$ sudo iwconfig wlan0 key off
travis@travis-desktop:/usr/src/rt73-cvs-2008051712/Module$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:11:50:6a:ca:3f
Sending on   LPF/wlan0/00:11:50:6a:ca:3f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by Austin_KW on 2008-05-17
> **travismoore said:**
> thanks

this appears to have not worked:

```
travis@travis-desktop:/usr/src/rt73-cvs-2008051712/Module$ sudo iwconfig wlan0 essid belkin54g
travis@travis-desktop:/usr/src/rt73-cvs-2008051712/Module$ sudo iwconfig wlan0 key off
travis@travis-desktop:/usr/src/rt73-cvs-2008051712/Module$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:11:50:6a:ca:3f
Sending on   LPF/wlan0/00:11:50:6a:ca:3f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
Post back the output of the following commands
```
 sudo iwconfig
lsmod | grep usbcore

```

---

### Post by travismoore on 2008-05-17
> **Austin_KW said:**
> Post back the output of the following commands
```
 sudo iwconfig
lsmod | grep usbcore

```

sudo iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT73 WLAN  ESSID:"belkin54g"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

lsmod | grep usbcore:
```
usbcore               146028  5 p54usb,rt73,ehci_hcd,ohci_hcd
```

---

### Post by Austin_KW on 2008-05-17
> **travismoore said:**
> sudo iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT73 WLAN  ESSID:"belkin54g"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

lsmod | grep usbcore:
```
usbcore               146028  5 p54usb,rt73,ehci_hcd,ohci_hcd
```


Why p54usb? This is a driver for a prism wireless chipset
what is the output of ```
lsusb
lshw -C net 
```

---

### Post by travismoore on 2008-05-17
> **Austin_KW said:**
> Why p54usb? This is a driver for a prism wireless chipset
what is the output of ```
lsusb
lshw -C net 
```

I don't know im trying to get the rt73 to work.

```
travis@travis-desktop:~$ lsusb
Bus 004 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

```
travis@travis-desktop:~$ lshw -C net
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 190 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 00
       serial: 00:1b:b9:a5:8f:64
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis190 driverversion=1.2 ip=192.168.2.5 latency=0 module=sis190 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:6a:ca:3f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT73 WLAN
```

---

### Post by Austin_KW on 2008-05-17
@travismoore

Belkin change the chipset without changing the IDs. So you can get multiple drivers loaded. You could open the adapter (a fingernail usually pops it open) and read the chip ID (it is usually a the large square black chip)

If you think it is an rt73 chip then try unloading the prism driver;
unplug the adapter
```
sudo modprobe -r p54usb
```
add "blacklist p54usb" to  /etc/modprobe.d/blacklist
reinsert the adapter
and rerun the config commands

---

### Post by travismoore on 2008-05-17
> **Austin_KW said:**
> @travismoore

Belkin change the chipset without changing the IDs. So you can get multiple drivers loaded. You could open the adapter (a fingernail usually pops it open) and read the chip ID (it is usually a the large square black chip)

If you think it is an rt73 chip then try unloading the prism driver;
unplug the adapter
```
sudo modprobe -r p54usb
```
add "blacklist p54usb" to  /etc/modprobe.d/blacklist
reinsert the adapter
and rerun the config commands

I couldn't get it open but i believe it the rt73 driver i need.

cant seem to get this right:
```
travis@travis-desktop:~$ /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied

```

---

### Post by Austin_KW on 2008-05-17
you need superuser privs to edit these files

gksu gedit /etc/modprobe.d/blacklist (if you are using Ubuntu)
kdesu kate /etc/modprobe.d/blacklist (if you are using Kubuntu)

---

### Post by travismoore on 2008-05-17
Still no luck:
```
travis@travis-desktop:/usr/src/rt73-cvs-2008051712/Module$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 11845
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:11:50:6a:ca:3f
Sending on   LPF/wlan0/00:11:50:6a:ca:3f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```


sudo iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT73 WLAN  ESSID:"belkin54g"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lsmod | grep usbcore:
```
usbcore               146028  4 rt73,ehci_hcd,ohci_hcd
```

lsusb:
```
Bus 004 Device 004: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

lshw -C net:
```
  *-network               
       description: Ethernet interface
       product: 190 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 00
       serial: 00:1b:b9:a5:8f:64
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis190 driverversion=1.2 ip=192.168.2.5 latency=0 module=sis190 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:6a:ca:3f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT73 WLAN

```

---

### Post by Austin_KW on 2008-05-17
@travismoore

Check your router config at 
[http://192.168.2.1](http://192.168.2.1)

default password is blank (just click submit)
Go to security under wireless
And verify it is disabled.

If it is then go to "Channel and SSID" under wireless and try changing the channel. Try 1,6,11 or 13 and see if that helps.

---

### Post by travismoore on 2008-05-17
> **Austin_KW said:**
> @travismoore

Check your router config at 
[http://192.168.2.1](http://192.168.2.1)

default password is blank (just click submit)
Go to security under wireless
And verify it is disabled.

If it is then go to "Channel and SSID" under wireless and try changing the channel. Try 1,6,11 or 13 and see if that helps.

security is disabled

how do i check if changing the channels worked?

---

### Post by Austin_KW on 2008-05-17
@travismoore

Change the channel and click apply
Then use the scan command to check that the router is using the new channel
sudo iwlist wlan0 scan

Then rerun the config commands
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid YOUR_NETWORK_NAME_HERE
sudo iwconfig wlan0 key YOUR_WEP_KEY_HERE_OR_"off"_FOR_NO_KEY
sudo dhclient wlan0

---

### Post by peterballard on 2008-05-18
> **peterballard said:**
> Thanks, that worked. According to "sudo iwlist scan" the ESSID name was simply "default" (including the double quotes), so that's what I put in my /etc/network/interfaces, i.e. in all I added these lines to my original /etc/network/interaces:
```

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid "default"
pre-up iwconfig wlan0 key "off"

```

Now my connection comes up every time (although one time it did drop out after a while). 


One more thing: how do I bring the connection back up if it dies? 

Thanks, Peter

(For those who missed my earlier post, I've got a D-Link DWA-110 wireless usb adapter, Ubuntu 8.04, and using the instructions from the first post in this thread)

---

### Post by Austin_KW on 2008-05-18
@peterballard

You can force a rerun of the configuration from the interfaces file using 
*sudo ifup --f wlan0*

Once you have everything working you should;
Change your SSID to something non-default and easily recognisable (eg *peterNet*)
Enable WPA-PSK (or WPA2-PSK) encryption with a 20+ character password

---

### Post by peterballard on 2008-05-20
> **Austin_KW said:**
> @peterballard

You can force a rerun of the configuration from the interfaces file using 
*sudo ifup --f wlan0*


Unfortunately that doesn't bring the connection up. Any suggestions what to check? (As mentioned above, hardware is OK because Windows XP works). 

And am I better off asking in the main forum rather than here in the archives?

Thanks, Peter

---

### Post by Austin_KW on 2008-05-20
> **peterballard said:**
> Unfortunately that doesn't bring the connection up. Any suggestions what to check? (As mentioned above, hardware is OK because Windows XP works). 

And am I better off asking in the main forum rather than here in the archives?

Thanks, Peter

If you are rebooting from windows etc; the adapter can be left in a state where it does not initialise properly. (I think it is the load firmware that fails probably due to the fact that the adapter never powers off)

Unplug the adapter, 
Reinsert the adapter 
Then rerun the config commands or "sudo ifup --f wlan0"

---

### Post by peterballard on 2008-05-21
> **Austin_KW said:**
> If you are rebooting from windows etc; the adapter can be left in a state where it does not initialise properly. (I think it is the load firmware that fails probably due to the fact that the adapter never powers off)

Unplug the adapter, 
Reinsert the adapter 
Then rerun the config commands or "sudo ifup --f wlan0"

That doesn't work, alas. 

(And in any case, if the Windows driver can handle an improperly initialised adaptor, you'd think the Linux driver could too).

So I still suspect some software setup problem.

---

### Post by sefmars on 2008-05-21
i have been trying to configure a wireless adaptor to work in master mode(as an AP) but to no avail , i have fallowed your how to   , managed to to configure my card but when i try to set in in master mode it gives something like this:

root@mars:~# iwconfig wlan1 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan1 ; Invalid argument.


root@mars:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

eth2      no wireless extensions.

wlan1     RT73 WLAN  ESSID:""
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by georg_c on 2008-05-25
Hi everybody,

first of all thanks to diepruis for this excellent guide and to Austin_KW and Kiefer Rodriguez for their valuable input (Kiefer, I will try out your automated script the next time I do a kernel update !).

I did a fresh install of Hardy Heron on my notebook some days ago and was able to get my D-Link G122 wireless USB adapter up and running in no time thanks to this guide.

While wireless networking per se works fine, there are still two issues that just "don't feel right":

1. Booting with the USB wireless adapter connected results in a kernel panic. This is not really a showstopper due to the obvious workaround, however it is not how things should ideally be. I noticed at least one other person in this thread had the same issue - are there any new insights?

2. This is a weird one (and hopefully, I have not overlooked a similar post in this long thread):
I prefer static IP addresses for my home LAN. For the moment, I manually execute a script to bring up the wlan0 interface. When I bring up the wlan0 interface, it is assigned the IP address 192.168.2.31 in accordance to the settings in my /etc/network/interfaces file. Yet, when I check the logs of my router, I can see that wlan0 is registered with an IP address of 192.168.2.30 (which happens to be the static address of my eth0 interface in the interfaces file; and yes, when I connect wlan0, I bring eth0 down first, the ethernet cable is not plugged in, and the MAC address in the router logs is identical to the one in the 'ifconfig' output).
Yet, wireless networking does not seem to be affected in any way.
This behaviour happens reliably every time I bring up the wlan0 interface and it persists across reboots. I have uninstalled network manager.
Btw., the very first time I followed the instructions in this guide, for the sake of simplicity I connected the USB wireless via DHCP; I don't remember, though, which IP address was assigned to wlan0 that very first time.

Is it possible to have stale data somewhere that cause this? 


Here's some technical stuff:

```
 ~ $ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 07d1:3c03 D-Link System 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

```
 ~ $ lsmod | grep rt73
rt73                  215168  1 
usbcore               143724  3 rt73,uhci_hcd

```

```
 cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

( ... snip ...)

# Blacklist rt73usb, as it is a non-functional beta module which conflicts with the working rt73 module.
blacklist rt73usb
# Blacklist rt2570, as it causes conflicts with rt73
blacklist rt2570
# Other modules that break rt73
blacklist rt2500usb
blacklist rt2x00lib

```

```
 ~ $ ifconfig
lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:2022 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2022 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:210505 (205.5 KB)  TX bytes:210505 (205.5 KB)

wlan0     Link encap:Ethernet  Hardware Adresse 00:19:5b:74:d1:72  
          inet Adresse:192.168.2.31  Bcast:192.168.2.255  Maske:255.255.255.0
          inet6-Adresse: fe80::219:5bff:fe74:d172/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:37258 errors:0 dropped:2603 overruns:2603 frame:2603
          TX packets:8013 errors:0 dropped:1 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:6966640 (6.6 MB)  TX bytes:731544 (714.3 KB)

```

```
 ~ $ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.2.30
netmask 255.255.255.0
gateway 192.168.2.1

auto eth0

iface wlan0 inet static
address 192.168.2.31
netmask 255.255.255.0
gateway 192.168.2.1
wireless-essid *********

```

```
 ~ $ sudo cat /root/wlanstarter
[sudo] password for <myself>: 
#! /bin/bash

#this is the script I execute to bring wlan0 up

wlan_up () {

	
	[ -n "$( ifconfig | grep eth0 )" ] && ifdown eth0
	ifconfig wlan0 up
	iwconfig wlan0 mode managed
	iwpriv wlan0 set AuthMode=WPAPSK
	iwpriv wlan0 set EncrypType=TKIP
	iwconfig wlan0 essid "*********"
	iwpriv wlan0 set WPAPSK="*********************"
	iwconfig wlan0 essid "*********"
	ifup wlan0

}

#check for available interfaces
d_link=`lsusb | grep D-Link`
[ -n "$d_link" ]  && wlan_up

```

```
 ~ $ route
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.2.1     0.0.0.0         UG    100    0        0 wlan0

```

---

### Post by fyz on 2008-05-27
Now it works perfectly with 8.04

> **fyz said:**
> After another few days trying, my wireless network still not working perfectly. :(

I have read the first post and followed the HOWTO instructions. With all your helps, I can at least  get the wireless connection. The driver was installed flawlessly (I think). But now I got three problems:
First, I still can not manage  to make the interface be brought up automatically across reboots; every time I have to manually type a few lines after reboot.  This is my interfaces files:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan1
iface wlan1 inet dhcp
   pre-up ifconfig wlan1 up
   pre-up iwconfig wlan1 essid belkin54g
   pre-up iwconfig wlan1 key "off"

```

Secondly, even when I try to configure the interface manually, it does not always work. Normally, after typing following code in terminal (after every  reboot ):
```

  sudo ifconfig wlan1 up
  sudo iwconfig wlan1 essid belkin54g
  sudo iwconfig wlan1 key "off"

```

I HAVE TO unplug the adapter and plug it in again, then WAIT FOR A WHILE (otherwise it won't work),  then I can type:
```

sudo dhclient wlan1

```

After all these, I can then  get connection! 

The third problem is I have to set the WEP security off in my router, other wise it won't work. Maybe I didn't set the key correctly in the configuration of interface. But this is ok for time being. The first two problems are more annoying. 

This is message when it failed to connect
```

Listening on LPF/wlan1/00:11:50:bc:ec:dd
Sending on   LPF/wlan1/00:11:50:bc:ec:dd
Sending on   Socket/fallback
DHCPREQUEST on wlan1 to 255.255.255.255 port 67
DHCPREQUEST on wlan1 to 255.255.255.255 port 67
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
Trying recorded lease 192.168.2.2
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```

This is the message when it does get connection after the **unplug/plug trick:**
```

Listening on LPF/wlan1/00:11:50:bc:ec:dd
Sending on   LPF/wlan1/00:11:50:bc:ec:dd
Sending on   Socket/fallback
DHCPREQUEST on wlan1 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.2 -- renewal in 960272812 seconds.

```

Do you have any ideas what is going on? Thanks a millions!

---

### Post by needlenose on 2008-05-28
First thanks to Diepruis and all else involved in this thread (how to). I came back to Ubuntu because of this how-to hoping to get my wireless working. But I'm still having problems. I'm running Ubuntu 8.04, which I'd hoped would work out of the box, but didn't. I've tried the how to twice and have gotten to ifconfig -a to get this
john@dumbass-desktop:/usr/src/rt73-cvs-2008052714/Module$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:d8:22:55:15  
          inet addr:192.168.0.197  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fe22:5515/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6316 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5845 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5333124 (5.0 MB)  TX bytes:608284 (594.0 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3360 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:168000 (164.0 KB)  TX bytes:168000 (164.0 KB)
From make install I get this
john@dumbass-desktop:/usr/src/rt73-cvs-2008052714/Module$ sudo make install
*** Install module in /lib/modules/2.6.24-17-generic/extra ...
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
  INSTALL /usr/src/rt73-cvs-2008052714/Module/rt73.ko
  DEPMOD  2.6.24-17-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
/sbin/depmod -a
*** Update /etc/modprobe.d/ralink alias for wlan*
*** Install firmware in /lib/firmware ...
*** Check old config ...

the last 3 lines have me wondering if I need to do more.

lsusb lists
john@dumbass-desktop:/usr/src/rt73-cvs-2008052714/Module$ lsusb
Bus 005 Device 002: ID 07d1:3c09 D-Link System 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
which lists my D-link dongle 

lsmod | grep usbcore 
john@dumbass-desktop:/usr/src/rt73-cvs-2008052714/Module$ lsmod | grep usbcore
usbcore               146028  6 rt73,usb_storage,libusual,ehci_hcd,uhci_hcd

Hopefully someone can help me figure this out.
Any and all help is greatly appreciated

---

### Post by Austin_KW on 2008-05-28
@needlenose
Are you sure this is and rt73 device
```


austin@austin-laptop:~/rt/rt73-cvs-2008052814/Module$ grep 07d1 *
rtmp_def.h: {USB_DEVICE(0x07d1,0x3c03)},\
rtmp_def.h: {USB_DEVICE(0x07d1,0x3c04)},\
rtmp_def.h: {USB_DEVICE(0x07d1,0x3c07)},\

```

Your device 07d1:3c09 is not listed?

---

### Post by needlenose on 2008-05-28
Austin_KW Thanks for your quick reply. I know I once did a google (or maybe it was someone at gentoo) that lead me to believe I needed the RT73 driver, after another google I've found I need the RT2870 driver. After trying for 3 weeks to get this working I realize I've been beating my head upon a brick wall to open a wooden door. Thank you for pointing that out, I was getting quite a headache.](*,)

---

### Post by Austin_KW on 2008-05-28
> **needlenose said:**
> Austin_KW Thanks for your quick reply. I know I once did a google (or maybe it was someone at gentoo) that lead me to believe I needed the RT73 driver, after another google I've found I need the RT2870 driver. After trying for 3 weeks to get this working I realize I've been beating my head upon a brick wall to open a wooden door. Thank you for pointing that out, I was getting quite a headache.](*,)

You might try drivers directly from ralink tech [http://web.ralinktech.com/ralink/Home/Support/Linux.html](http://web.ralinktech.com/ralink/Home/Support/Linux.html)

---

### Post by sugarfresh on 2008-05-29
i ran into a problem when trying to use this guide, once i get to step 9 where in the terminal you type "sudo make install" i get this
"make: *** No rule to make target `install'. Stop."
can someone help me? i followed all the other steps with no problem

---

### Post by diepruis on 2008-05-30
> **sugarfresh said:**
> i ran into a problem when trying to use this guide, once i get to step 9 where in the terminal you type "sudo make install" i get this
"make: *** No rule to make target `install'. Stop."
can someone help me? i followed all the other steps with no problem

From the same directory, what does ```
pwd
``` return?

---

### Post by whirley on 2008-06-03
Hi all i had BT broadband which worked perfectly with this driver but now i have SKY broadband and i cannot seem to be able to connet to it at all.

They sent me a sagem router and all the windows boxes in the house is working  but not my ubuntu. 

if i start the boot cd i am able to browse the net but i know that is not the serialmonkey drivers.

only other difference i think would be the use of a ASCII key instead of a hex key like before. any ideas?

---

### Post by Austin_KW on 2008-06-03
I don't know the sky sagem router BUT the sky netgear with similar V2 firmware uses a short (8 char ?) ***WPA*** key. Check this and then follow the instructions for WPA in the original post. (BT routers default to wep so slightly different instructions)


Otherwise, if it is a WEP key;
ascii keys can be set using iwconfig with "s:"
eg 
sudo iwconfig wlan0 key s:asciiKey (where asciiKey is the 5 or 13 charctger key)

or in /etc/network/interfaces with
pre-up iwconfig wlan0 key s:asciiKey

---

### Post by anoxan on 2008-07-04
hello world. I've been fighting with 7.10 to get my linksys wusb54gc working. for some reason I can't even boot into 8.04.. this solved my problem though. the only thing I'd like to see now is a way to monitor the connection like network manager kinda did. oh well. I'm happy now. :D

---

### Post by Austin_KW on 2008-07-04
> **anoxan said:**
> hello world. I've been fighting with 7.10 to get my linksys wusb54gc working. for some reason I can't even boot into 8.04.. this solved my problem though. the only thing I'd like to see now is a way to monitor the connection like network manager kinda did. oh well. I'm happy now. :D

The best utility for ralink devices is rutilt from [http://cbbk.free.fr/bonrom/](http://cbbk.free.fr/bonrom/) Works as a monitor and can configure the device.

Download and build it, From memory you may need "sudo apt-get install g++ libgtk2.0-dev" before you can build.

untar the archive and build (in the RutilTv0.16 directory) with
./configure.sh --launcher=external
make 
sudo make install


EDIT: may not be necessary, I see rutilt is now in the repositories. Just install from your package manager

---

### Post by EngMAF on 2008-07-11
sorry i am a newbie when i copy the archive file to /usr/src i tell me that i have no permission 
:confused:

---

### Post by Austin_KW on 2008-07-11
> **EngMAF said:**
> sorry i am a newbie when i copy the archive file to /usr/src i tell me that i have no permission 
:confused:

You need to preface the commands with sudo i.e. sudo cp ...
Just enter the terminal commands as they are shown in the original post.

---

### Post by munnyman5 on 2008-07-12
I don't know if this happened to anybody else, but I'm a huge N00b and have no idea what any of this code means; I'm blindly entering it as you say. I get this when I do the "sudo make" thing at step 7:

"make: *** No targets specified and no makefile found.  Stop."

and that's it. That's where it ends. I tried it again and again to no avail
PLZ HELP! i have a dlink gwl-122 revision C1 and I need it to be recognized by Xubuntu for me to connect to the internet!

---

### Post by dannyboy79 on 2008-07-14
> **munnyman5 said:**
> I don't know if this happened to anybody else, but I'm a huge N00b and have no idea what any of this code means; I'm blindly entering it as you say. I get this when I do the "sudo make" thing at step 7:

"make: *** No targets specified and no makefile found.  Stop."

and that's it. That's where it ends. I tried it again and again to no avail
PLZ HELP! i have a dlink gwl-122 revision C1 and I need it to be recognized by Xubuntu for me to connect to the internet!
where did you extract the archive to? did you cd to that directory first? that would be the only reason there wouldn't be a make in the directory, because you didn't go to that directory first or you didn't extract it first.

---

### Post by Austin_KW on 2008-07-14
@munnyman5
You need to closely follow the guide.
Make sure you cd to the correct directory
```

cd /usr/src/rt73-cvs*/Module
sudo make
sudo make install
... 
```

---

### Post by kjk85 on 2008-07-18
is this working for usb wireless adapter d-link G DWA 110 ? thx

---

### Post by Yigido on 2008-07-20
> **Austin_KW said:**
> The best utility for ralink devices is rutilt from [http://cbbk.free.fr/bonrom/](http://cbbk.free.fr/bonrom/) Works as a monitor and can configure the device
....
... looks good, but Rutilt says "The device cannot be configured  for this network because WPA is unsupported, this could be a driver limitation ."
the AP i would like to connect ist from my uni and uses PAP and TTLS.

greetz
Yigido

---

### Post by EngMAF on 2008-07-21
Could not resolve 'eg.archive.ubuntu.com'


```

maf@maf-desktop:~$ sudo aptitude install build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  linux-restricted-modules-common tk8.4 
The following NEW packages will be automatically installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev 
The following packages have been kept back:
  app-install-data-commercial bind9-host bsdutils cdrecord cupsys cupsys-bsd cupsys-client cupsys-common dbus dbus-1-utils 
  dnsutils e2fslibs e2fsprogs firefox firefox-gnome-support foo2zjs genisoimage gimp gimp-data gimp-python gnome-media 
  gnome-media-common gnome-system-tools hpijs hplip hplip-data iptables language-pack-ar language-pack-en 
  language-pack-gnome-ar language-pack-gnome-en libbind9-0 libblkid1 libcairo2 libcomerr2 libcupsimage2 libcupsys2 libcurl3 
  libdbus-1-3 libdns22 libflac7 libgimp2.0 libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa libgnome-media0 libisc11 libisccc0 
  libisccfg1 libjasper-1.701-1 libkpathsea4 libkrb53 liblwres9 libmagick9 libmono-cairo1.0-cil libmono-corlib1.0-cil 
  libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil 
  libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil 
  libnspr4 libnss3 libopal-2.2.0 libperl5.8 libpng12-0 libpoppler1 libpoppler1-glib libpt-1.10.0 libpt-plugins-alsa 
  libpt-plugins-v4l libpt-plugins-v4l2 libsmbclient libsndfile1 libsnmp-base libsnmp9 libss2 libssl0.9.8 libuuid1 
  libvorbis0a libvorbisenc2 libvorbisfile3 libwrap0 libxfont1 libxml2 libxml2-utils linux-headers-2.6.20-16 
  linux-image-2.6.20-16-generic linux-restricted-modules-2.6.20-16-generic mesa-utils mkisofs mono-common mono-gac mono-jit 
  mono-runtime mount openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core 
  openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-en-us openoffice.org-math 
  openoffice.org-style-human openoffice.org-writer openssh-client openssl perl perl-base perl-modules poppler-utils 
  python-launchpad-bugs python-libxml2 python-uno rsync samba-common smbclient ssh-askpass-gnome tar tcpdump tomboy 
  ttf-opensymbol tzdata update-manager update-manager-core util-linux util-linux-locales vim-common vim-tiny wodim 
  xserver-xorg-core 
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev 
The following packages will be upgraded:
  linux-headers-2.6.20-16-generic 
1 packages upgraded, 7 newly installed, 0 to remove and 146 not upgraded.
Need to get 8897kB of archives. After unpacking 33.7MB will be used.
Do you want to continue? [Y/n/?] y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  g++-4.1 g++ linux-libc-dev libstdc++6-4.1-dev linux-headers-2.6.20-16-generic dpkg-dev libc6-dev build-essential 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": yes
Writing extended state information... Done
Err http://eg.archive.ubuntu.com feisty-updates/main linux-libc-dev 2.6.20-16.35
  Could not resolve 'eg.archive.ubuntu.com'
Err http://eg.archive.ubuntu.com feisty/main libc6-dev 2.5-0ubuntu14
  Could not resolve 'eg.archive.ubuntu.com'
Err http://eg.archive.ubuntu.com feisty/main libstdc++6-4.1-dev 4.1.2-0ubuntu4
  Could not resolve 'eg.archive.ubuntu.com'
Err http://eg.archive.ubuntu.com feisty/main g++-4.1 4.1.2-0ubuntu4
  Could not resolve 'eg.archive.ubuntu.com'
Err http://eg.archive.ubuntu.com feisty/main g++ 4:4.1.2-1ubuntu1
  Could not resolve 'eg.archive.ubuntu.com'
Err http://eg.archive.ubuntu.com feisty/main dpkg-dev 1.13.24ubuntu6
  Could not resolve 'eg.archive.ubuntu.com'
Err http://eg.archive.ubuntu.com feisty/main build-essential 11.3
  Could not resolve 'eg.archive.ubuntu.com'
Err http://security.ubuntu.com feisty-security/main linux-libc-dev 2.6.20-16.35
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com feisty-security/main linux-headers-2.6.20-16-generic 2.6.20-16.35
  Could not resolve 'security.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-libc-dev_2.6.20-16.35_i386.deb: Could not resolve 'security.ubuntu.com'



```



what should i do 
thanks in advance

---

### Post by ugm6hr on 2008-07-27
I can confirm that despite the claims of "out-of-the-box" functionality for Hardy (Ubuntu 8.04LTS) with the RT2570 / rt73 chip[set (Edimax EW-7318USg USB wifi adapter), the current CVS serialmonkey drivers are 1000% more stable than the default with Network Manager.

I followed instructions 1-13, then installed RutilT from the repository to give me a GUI for the connection:
```
sudo aptitude install rutilt
```

I tried the interfaces file edit - but that didn't seem to work for me on WPA; not sure why... (EDIT: see post below)

Then added **rutilt -dp "New profile"** to the startup commands in Sessions (System->Preferences), removed Network Manager from startup; then set RutilT to startup in the system tray (a la Network Manager).

Then remove Network Manager:
```
sudo aptitude purge network-manager
```

Works great with my WPA connection.

Just a word of warning - it appears impossible to get this to work with the realtime (-rt) kernel.

---

### Post by ugm6hr on 2008-08-26
Managed to get it to connect to WPA at login, without RutilT!

The following 2 lines in /etc/network/interfaces are not needed
```
pre-up iwpriv wlan0 set SSID="YOUR_SSID"
    pre-up iwpriv wlan0 set NetworkType=Infra
```

They are replaced by:
```
pre-up iwconfig wlan0 essid YOUR_SSID
```

So the final result for etc/network/interfaces:
```
auto wlan0
iface wlan0 inet dhcp
    pre-up ifconfig wlan0 up
    pre-up iwconfig wlan0 essid YOUR_SSID
    pre-up iwpriv wlan0 set AuthMode=WPAPSK
    pre-up iwpriv wlan0 set EncrypType=TKIP
    pre-up iwpriv wlan0 set WPAPSK="YOUR_WPA_PSK_KEY"

```

EDIT:
In fact Wicd works perfectly with this.  I have left my interfaces file as above, and installed Wicd 1.5.3 (from their Ubuntu Hardy repo).  Wicd is set with ralink legacy as WPA driver, and it picks up my network connection automatically.

I have written a quick script to speed up the post-kernel upgrade reconfiguration (to be run as sudo rt73.sh):
```

#!/bin/sh

cd /usr/src/rt73-cvs-2008122110/Module
make clean
make
strip -S rt73.ko
ifdown wlan0
modprobe -rv rt73
make install
modprobe -v rt73
ifup wlan0
```

---

