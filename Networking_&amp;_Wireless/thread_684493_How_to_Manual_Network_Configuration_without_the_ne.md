---
title: "How to: Manual Network Configuration without the need for Network Manager"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-10-09
In setting up their wireless connection for the first time, Im discovering many individuals having problems connecting through Network Manager or other GUI wireless connection tools.  In fact my Network Manager is intermittently buggy, connecting sometimes and not others.   This guide benefits all users in case the GUI tools are not working, and is useful for testing a wireless connection during initial installation of wireless drivers since it provides for good debugging output.

[SIZE="3"]**Unencrypted/ WEP / WPA connections will be covered in this guide.**[/SIZE]
[SIZE="2"]**This guide is for anyone attempting to establish a network connection manually at the command line. **[/SIZE] 

**Pre-requisites**
1. Properly installed network driver -- This guide can be used to troubleshoot driver installation to see if it is properly functioning
2. The ESSID of your router must be broadcasted and not hidden
3. Knowlege of your wireless cards driver (please see Prerequisite #4 to determine driver).  [SIZE="2"]**Those using the r8187/r818x driver please see the end of the guide**[/SIZE]
4. Knowledge of your wireless card's Interface Name - The user must know the proper interface of the wireless connection (wlan0, eth1, rausb1, etc).  To discover this information, at command line type:

```
lshw -C network
```

There may be multiple interfaces listed, however look under the section appropriate to your wireless device for the line labeled logical name.  Here is an example:

```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       **[SIZE="2"]logical name: wlan0[/SIZE]**
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **[SIZE="2"]driver=ndiswrapper+lsbcmnds[/SIZE]** driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11

```
 
In the example above the interface name is wlan0.  **[SIZE="2"]I will refer to the interface name throughout the rest of this guide as <interface>.[/SIZE]** 

For people first setting up their connection, please note that the above also lists the driver used for the network card.  In the example above, the driver used is ndiswrapper.  [SIZE="2"]**If your network device comes back UNCLAIMED or there is no driver listed, then you have not correctly installed the driver for your device.**[/SIZE]  You must review the procedures for installation of your wireless driver.

**For those wanting to use static IP addresses, please see section at bottom of guide regarding configuration for static IP addresses**

____________________________________________________________________________
[SIZE="4"]**Unencrypted Connection**[/SIZE]

All commands typed at the command line:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```

____________________________________________________________________________
[SIZE="4"]**WEP Connection**[/SIZE]

You must have either your 64bit or 128 bit HEX Key or the ASCII Equivalent of your HEX Key.

```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
****Additional Comand that may be needed  -- sudo iwconfig <interface> key open  <<<----See note below
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```

***The security mode may be open or restricted, and its meaning depends on the card used. With most cards, in open mode no authentication is used and the card may also accept non-encrypted sessions, whereas in restricted mode only encrypted sessions are accepted and the card will use authentication if available.
____________________________________________________________________________
[SIZE="4"]**WPA Connection  - WPA-PSK or WPA2-PSK**[/SIZE]

For uses of Ra-based chipsets: rt61, rt73, rt2500 please skip directly to the WPA Section entitled **WPA with Ra based chipsets**

Requirements: In most cases the wpa_supplicant package is required in order to connect via WPA.  If you have a working ethernet or unencrypted/WEP wireless connection, this package may be installed via:
```
sudo aptitude install wpasupplicant
```

If only wireless is available, I would recommend that an unencrypted connection first by established and tested first before directly proceeding to make a WPA connection.  WPA adds another layer of complexity.

1. Creation of /etc/wpa_supplicant.conf file

At command line:
```
gksu gedit /etc/wpa_supplicant.conf
```

Inside the file add the following for WPA(1):

```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="ESSID_IN_QUOTES"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="ASCII PSK Password in Quotes"
        pairwise=TKIP
        group=TKIP
}
```

For WPA(2) (see this thread: [http://ubuntuforums.org/showthread.php?t=607410](http://ubuntuforums.org/showthread.php?t=607410)):
```

ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="ESSID_IN_QUOTES"
        psk="ASCII PSK Password in Quotes"
        key_mgmt=WPA-PSK
        proto=RSN
        pairwise=CCMP
}

```

***Word of caution -- In some cases I have found WPA(2) to have different settings than the above.  Some Broadcom cards use the pairwise/group TKIP cipher for WPA2 rather than CCMP.  **I would suggest all initially use WPA(1)** and then later convert to WPA2 since some variations to the above may be needed

2. Connect via command line
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo wpa_supplicant -w -D<****see footer below***> -i<interface> -c/etc/wpa_supplicant.conf -dd 
sudo ifconfig <interface> up
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

```

***footer
The value listed here is dependent on the driver you have installed.  Typing man wpa_supplicant at command line will give you the full gamut of choices however a quick reference
ndiswrapper=wext  (use wext and not ndiswrapper despite what documentation might suggest)
ath_pci = madwifi
ipw2100/2200=ipw

[SIZE="3"]**WPA with Ra Based Chipsets**[/SIZE]

Ra cards do not require the wpa_supplicant package to use WPA.  Here is how to connect from the command line with these cards:
References: [http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey), [http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto#Using_WPA](http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto#Using_WPA)

WPA(1)
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <inteface> essid "ESSID_IN_QUOTES"
sudo iwpriv <interface> set AuthMode=WPAPSK
sudo iwpriv <interface> set EncrypType=TKIP
sudo iwpriv <interface> set WPAPSK="YOUR_WPA_PSK_KEY"
sudo dhclient <interface>

```

For WPA(2), I have no working configuration yet.  If someone would like to help me refine these instructions for WPA2 with Ra-based chipsets, I would appreciate your help!

____________________________________________________________________________
**[SIZE="4"]A successful connection in all cases will results in this[/SIZE]**:
```
user@computer:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:12:17:35:17:10
Sending on   LPF/wlan0/00:12:17:35:17:10
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 299133 seconds.
```

The computer in this example has received an IP address of 192.168.1.101

____________________________________________________________________________
[SIZE="3"]** Users of RTL 8180, RTL8185, RTL 8187 using the built in native r8187 / r818x drivers **[/SIZE]

By default the r8187 and r818x drivers are blacklisted due to a know bug.  These drivers are usuable however with a twist to the above methods

If you want to try using these drivers, please load the kernel modules:
```

sudo modprobe r818x
sudo modprobe r8187

```

**[SIZE="2"]These drivers require a bogus or extra letter be suffixed to the essid name in order for these drivers to work**[/SIZE]
For example if your are trying to connect to a router with essid=Router, at he command line you would type essid=Routerx.  Notice the extra x or bogus character.  I have provided an example using the unencrypted connection procedure below, however this extra character needs to be used if attempting to connect to all network types (unencrypted/ WEP / WPA)

```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "Routerx"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```

If these drivers work for you, and you would like these drivers to load automatically at startup for you, avoiding to have to type sudo modprobe everytime, please edit your blacklist file:

```

gksu gedit /etc/modprobe.d/blacklist

```

And comment out (or prefix the following lines with a # sign).  You want the following lines to appear as below:
```

#blacklist r8187
#blacklist r818x 

```


____________________________________________________________________________
[SIZE="3"]** Static IP Addresses **[/SIZE]

Im going to give an example of how to configure your interface using a static IP address using an unencrypted wireless connection.   The two lines highlighted below however can be used with WEP and WPA connections.  Values in italics must be customized to meet your particular situation

```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
[SIZE="2"][B]sudo ifconfig <interface> *192.168.1.100* netmask *255.255.255.0* up
sudo route add default gw *192.168.1.1*[/B][/SIZE]
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```

If when using static IP addresses you are getting a problem with name resolution, you will have to specifiy specific dns (domain name servers) in order to translate URLs to IP addresses.  Unfortunately there is not an easy way to configure this from the command line.  This requires that you edit the /etc/resolv.conf file and manually enter the domain name server(s) you want to use.  In many cases users can specifiy their router, their internet service providers dns servers, or use opendns (or use all three).  Please note that changes made to the /etc/resolv.conf file will not be retained between reboots.  To make the nameservers permanent, the /etc/dhcp3/dhclient.conf file needs to be edited as instructed here: [http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)

```
sudo gedit /etc/resolv.conf
```
and add the nameservers you want to use, one to a line, in the following format.
```
nameserver <nameserver>
```
You can add as many as you want but most isps normally provide two (primary and secondary). 

____________________________________________________________________________
[SIZE="3"]**Setting the Wireless Interface to Connect at Boot **[/SIZE]  ***Courtesy of Maricaibo

If you are successful in bringing up the Interface Manually,  the commands may be placed inside the /etc/rc.local file to run the commands at boot, and establish a wireless connection.  There is no GUI to give visual confirmation of the connection.  The user should type **ifconfig** at the command line to verify an IP address has indeed been granted by the router. 

The process of adding the commands to the /etc/rc.local file is documented below (**this connects to an unencrypted network** -- to connect to a WEP or WPA encrypted network, some modifications as used above will need to be added):

```
gksu gedit /etc/rc.local
```

This opens up the file in the gedit utility and allows you to make changes and save the file

```

ifconfig <**wired** network connection interface> down
ifconfig <**wireless** network connection interface> down
dhclient -r <wireless_interface>
iwconfig <wireless_interface> essid <router name>
iwconfig <wireless_interface> mode Managed
ifconfig <wireless_interface> up
dhclient <wireless_interface>

```

Be sure this text goes into the /etc/rc.local file **BEFORE** the line reading "exit 0".

Save and close the /etc/rc.local file.

Open up a Terminal window (the shell) and type in:

```

sudo chmod +x /etc/rc.local

```

This command turns the rc.local file into an executable that will run at startup. **Here's an example of what the /etc/rc.local file should contain**. **Your device names may be different**:

```

#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ifconfig eth0 down
ifconfig wlan0 down
dhclient -r wlan0
iwconfig wlan0 essid "ESSID_IN_QUOTES"
iwconfig wlan0 mode Managed
ifconfig wlan0 up
dhclient wlan0

exit 0

```

NOTE: **The first line in the rc.local file downs your wired connection**, so if for some reason you need the wired connection back just open up a Terminal window (shell) and type:

sudo <wired_interface> up
sudo dhclient <wired_interface>
____________________________________________________________________________
[SIZE="3"]** Useful Commands **[/SIZE]

**ifconfig** - lists IP address (similar to ipconfig in Windows)
**iwlist scan** - shows wireless networks that are available in the area along with basic encryption information
**lshw -C network** - Shows interface and driver associated with each networking device
**lspci -nn** - Shows hardware connected to the pci bus
**lsusb** - Shows USB connected hardware
**lshw -C usb** - Additional info on USB related hardware (good for USB dongles)
**cat /etc/modprobe.d/blacklist** - List modules that will not be loaded by the Operating System at boot time
**lsmod** - lists currently loaded kernel modules.  (Example usage - lsmod | grep ndiswrapper)
**route -n** - Lists kernel IP routing table -- Good for troubleshooting problems with the gateway (netstat -rn = equivalent command)
**sudo route add default gw 192.168.1.1** - Example of how to set the default gateway to 192.168.1.1 
**sudo route del  default gw  192.168.1.1** - Example of how to delete the default gateway setting
**sudo modprobe ******* - Loads the kernel module **** .  (Example usage - sudo modprobe ndiswrapper, sudo modprobe r818x, sudo modprobe ath_pci)
**sudo modprobe -r ****** - Unloades the kernel module ****.  (Example usage - sudo modprobe -r ndiswrapper)
**sudo ifup/ifdown <interface>** - Brings up/down the interface and clears the routing table for the specified interface
**sudo ifconfig <interface> up/down** - Brings up/down the interface for the specified interface 
**sudo dhclient <interface>** - Request IP address from DNS server for specified interface
**sudo dhclient -r <interface>** - Release IP address associated with specified interface
**sudo iptables -L** - Lists firewall rules 
**dmesg | more** - Lists boot log -- good for troubleshooting problems with modules/drivers not being loaded
**uname -r** - Displays kernel version
**/etc/iftab (Feisty and pre-releases (Edgy, etc)) -  /etc/udev/rules.d/70-persistent-net.rules (Gutsy)** - File which assigns logical names (eth0, wlan0, etc) to MAC addresses
**cat /etc/resolv.conf** - Lists DNS servers associated with network connections (Network Manager)
**/etc/dhcp3/dhclient.conf** - File which sets or modifies dns (domain name servers) settings

**Further references:**
**Official Broadcom site for bcm43xx firmware** - [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
**Broadcom 64bit Drivers for Use with Ndiswrapper** - [http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php)
**Ra chipsets - Serial Monkey Drivers** - rt2500, rt73, rt61, rt2570 drivers - [http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey) - Author diepruis
**Rutilt - A Network Manager Like GUI for Ra Chipsets** - [http://ubuntuforums.org/showthread.php?t=554089&highlight=rutilt](http://ubuntuforums.org/showthread.php?t=554089&highlight=rutilt) - Author sulilogs
**Ndiswrapper installation for Broadcom chipsets** - [http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963) - Author Jamie Jackson
**Ndiswrapper General Installation Guide - SVN, Troubleshooting Tips (My Personal Guide)** - [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501) - Author KevDog
**Madwifi website for certain Atheros Chipset**s - [http://madwifi.org/](http://madwifi.org/) -- If your Atheros chipset is listed on this website - it should work out of the box with installation of the linux restricted drivers package for your kernel version
**Does your madwifi connection keep dropping??? Possible solution** -- [http://ubuntuforums.org/showthread.php?t=540101](http://ubuntuforums.org/showthread.php?t=540101) = Author robnz/tranalbert
**Realtek win98 driver** - [http://www.majorgeeks.com/Realtek_RTL8187_USB_Wireless_LAN_ME2000XP_d5165.html](http://www.majorgeeks.com/Realtek_RTL8187_USB_Wireless_LAN_ME2000XP_d5165.html) - For use with ndiswrapper if native r818x, r8187 driver is buggy
**Realtek win98 driver installation** - [http://ubuntuforums.org/showthread.php?t=493958&highlight=8187](http://ubuntuforums.org/showthread.php?t=493958&highlight=8187) - Author Panurge
**Realtek - Installation with Native Driver** - [http://ubuntuforums.org/showthread.php?t=567505](http://ubuntuforums.org/showthread.php?t=567505)
**DNS related problems?? - Configuration for OpenDNS servers** - [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659) - Author noob12
**Turn off/Disable IPv6** - [http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034) - Author handy
**General Linux Page Discussing Network Setups - Default Gateways** - [http://linux-ip.net/html/basic-changing.html](http://linux-ip.net/html/basic-changing.html)
**Log Files -- Your Friend to Debug almost anything on your System** - [https://help.ubuntu.com/community/LinuxLogFiles#head-90a79f52ee3f6d766a16e1ee67f98267e009db55](https://help.ubuntu.com/community/LinuxLogFiles#head-90a79f52ee3f6d766a16e1ee67f98267e009db55)

**Other things Linux**
**Control Programs Kept in Swap vs Memory** - [http://ubuntuforums.org/showpost.php?p=4088251&postcount=150](http://ubuntuforums.org/showpost.php?p=4088251&postcount=150)
**Realtek 8187B Native Patch for Realtek 818x USB Devices -- Relevant only to USB wireless devices** - [http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/) - Author Cuervo
**If your Wireless Freezes after Suspend/Resume - Check here** - [http://ubuntuforums.org/showpost.php?p=2796307&postcount=12](http://ubuntuforums.org/showpost.php?p=2796307&postcount=12) - Author Harty83

---

### Post by JustinAllen on 2007-10-12
Excellent post!  Worked as advertised!  I had been using the NetworkManager but all of a sudden, it stopped wanting to connect to my wireless.  These instructions got me connected once again.  Thanks a lot!!

---

### Post by Beggar on 2007-10-12
After upgrading to gutsy my WIFI broke after the first reboot. The output from the first command is:

```

darren@BeggarBox:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
       ...

```

Notice it is not given a logical name. How do I set it back to being eth1? /etc/iftab seems to be the best option, but I dont know the mac address. Any ideas?

It doesn't seem like /etc/iftab is used anymore, back to square one....

---

### Post by kevdog on 2007-10-12
Beggar

Interesting situation you present, cant say that Ive ever seen your situation before .. so its kind of neat.  What does
dmesg

say after you boot.  Anything about the interface.  Does 
ifconfig
lend any clues.

My forte is not with the ipw drivers.  I think noob12 is much better in this area than I.

---

### Post by ivanpetrov on 2007-10-12
My wireless (eth1) has gone upon the latest "partial upgrade" of the gutsy preview I've been using for a couple of weeks.

~$ dmesg|grep ipw2200
[   18.384000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   18.384000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   18.628000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   18.872000] ipw2200: Unable to load ucode: -62
[   18.872000] ipw2200: Unable to load firmware: -62
[   18.872000] ipw2200: failed to register network device
[   18.872000] ipw2200: probe of 0000:02:01.0 failed with error -5

---

### Post by kevdog on 2007-10-12
If you have an older kernel version installed (ie you upgraded from feisty), press the ESC key when booting to enter the grub menu and see if you can use the ipw driver in an older kernel version.  One other option, although its pretty drastic would be to compile your own vanilla kernel.  I think (not certain), that the ipw drives are included by default, but confirm this. The masterkernel thread is a good place to start in the forums.

---

### Post by Beggar on 2007-10-12
Mine loads fine, but then I found this little gem a few lines down.

```

[   16.088000] ipw3945: Radio Frequency Kill Switch is On:
[   16.088000] Kill switch must be turned off for wireless networking to work.

```

Might be hard for me to turn my kill switch off however, considering I don't have one...

----

Scratch that, I didnt notice it, but since the gutsy upgrade my function keys work. Apparently right after the upgrade I used fn-f2 instead of ctrl-f2, fn-f2 is my computers wifi killswitch. 
Boy do I feel stupid. I only spent 5+ hours trying to fix that. Hard to debug something you dont think works suddenly getting fixed on you...

---

### Post by ivanpetrov on 2007-10-12
> **kevdog said:**
> If you have an older kernel version installed (ie you upgraded from feisty), press the ESC key when booting to enter the grub menu and see if you can use the ipw driver in an older kernel version...

Luck would have it, I just removed the older kernels yesterday.  Have rebooted a couple of times since then with everything working fine.  But ran the latest updates (some sort of a partial upgrade) just today, and that did the wireless in.

Oh well, gonna have another look.  Thanks for your suggestions.

---

### Post by nosneros on 2007-10-13
Hi,

Just wanted to say thanks for the post, kevdog.

I just followed your advice to connect to my girlfriend's WRT54G v8 with WPA1. It was working under Windows, but not (K)ubuntu. The only oddity I found is that I have to use the wext driver instead of ipw when running wpa_supplicant, even though I have an Intel 2915 card in my laptop. I found that out by reading the output of wpa_supplicant with the -Dipw option.

Thanks again!

---

### Post by kevdog on 2007-10-13
Hmm, I guess you are right

wext is for any generic linux driver.  
ipw is for the intel ipw 2100 and 2200 driver.

Good thing you read the man pages since this part of configuring the wpa_supplicant.conf file can be a little tricky

---

### Post by madgreek on 2007-10-21
I installed Mepis 6.5.02 on my Dell Inspiron 1721 last week.  I gave Vista the boot and Mepis installed real easy and connected to my Linksys router w/no issues.  Today, I downloaded Kubuntu 7.10 and tried to set it up to dual boot.  I ran into some problems and finally threw my hands up and just installed it over Mepis.  I couldn't get connected to the wireless router.  Then I tried Mepis again and was able to dual boot both Kubuntu and mepis (happy days!), however, now I can't connect to the wireless on Mepis.  Right now I am connected wired into the access point.

I ran you scripts and here is what I saw....

iwconfig wlan0 essid Gameserver
root@1[/]# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate=54 Mb/s   Tx-Power:32 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

root@1[/]# ifconfig wlan0 down
root@1[/]# dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:1c:26:91:c7:ec
Sending on   LPF/wlan0/00:1c:26:91:c7:ec
Sending on   Socket/fallback
root@1[/]# ifconfig wlan0 up
root@1[/]# ifconfig wlan0 essid "Gameserver"
essid: Unknown host
ifconfig: `--help' gives usage information.
root@1[/]# iwconfig wlan0 essid "Gameserver"
root@1[/]# iwconfig wlan0 mode Managed
root@1[/]# dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:1c:26:91:c7:ec
Sending on   LPF/wlan0/00:1c:26:91:c7:ec
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@1[/]#

Please help!!!

---

### Post by kevdog on 2007-10-21
What does 
iwlist scan show

Make sure you take down your wired interface when trying to connect, such as
sudo ifconfig eth0 down

Also can you post 
lshw -C network

---

### Post by madgreek on 2007-10-21
Here you go!

root@2[eleni]# sudo ifconfig eth0 down
root@2[eleni]# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:1F:A4:3E
                    ESSID:"default"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:1A:70:F6:C6:99
                    ESSID:"Gameserver"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

root@2[eleni]# lshw -C network
  *-network
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:1c:26:91:c7:ec
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Broadcom,10/12/2006, 4.100.15.5 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:fe8fc000-fe8fffff irq:19
  *-network DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:8a:f6:f8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=0.97 link=no multicast=yes
       resources: iomemory:fe5fe000-fe5fffff irq:22

---

### Post by kevdog on 2007-10-21
What driver are you using bcmwl5??

Once the eth0 interface is down, can you repeat the unencrypted manual commands for wlan0 and see what happens??

---

### Post by BC7333 on 2007-10-21
> **Beggar said:**
> After upgrading to gutsy my WIFI broke after the first reboot. The output from the first command is:

```

darren@BeggarBox:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
       ...

```

Notice it is not given a logical name. How do I set it back to being eth1? /etc/iftab seems to be the best option, but I dont know the mac address. Any ideas?

It doesn't seem like /etc/iftab is used anymore, back to square one....

I remarked out # the last line in /etc/udev/rules.d/70-persistent-net.rules, rebooted and wireless started working.  Seems upgrade replaced iftab but then setup rules.d with two interface names for the same mac address...

Here the files before I remarked out the redundant entry in rules.d

**/etc/iftab**

Code:

# **This file is no longer used and has been automatically replaced.**
# See /etc/udev/rules.d/70-persistent-net.rules for more information.
#

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

##eth0 mac 00:09:5d:15:60:23 arp 1
#wlan0 mac 00:19:D2:BB:50:59 arp 1
[B]
/etc/udev/rules.d/70-persistent-net.rules
[/B]
Code:

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:09:5d:15:60:23", ATTRS{type}=="1", NAME="eth0"

[B]# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:19:D2:BB:50:59", ATTRS{type}=="1", NAME="wlan0"


# PCI device 0x8086:0x4222 (ipw3945)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:19:d2:bb:50:59", NAME="eth1"[/B]

---

### Post by madgreek on 2007-10-21
Same error!

root@1[/]# ifconfig wlan0 up
root@1[/]# iwconfig wlan0 essid "Gameserver"
root@1[/]# iwconfig wlan0 mode Managed
root@1[/]# dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:1c:26:91:c7:ec
Sending on   LPF/wlan0/00:1c:26:91:c7:ec
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


How do I find what the driver is?

---

### Post by kevdog on 2007-10-21
Look in the /etc/ndiswrapper folder.  There should be a subdirectory, and inside this subdirectory I believe is contained the driver.

Are you broadcasting the essid on the router?  No MAC filtering on the router correct??

---

### Post by kthakar on 2007-10-21
What are the steps to connect to a network with hidden ESSID (WEP) using command line?

---

### Post by kevdog on 2007-10-21
The commands are the same, however Im not sure if this will work.  Its something about the drivers and Linux.  So basically Im saying is that Im not certain ubuntu can connect to any router with hidden ssid broadcast.

---

### Post by madgreek on 2007-10-21
eleni@1[~]$ cd /etc
eleni@1[etc]$ cd ndis*
eleni@1[ndiswrapper]$ ls
bcmwl5  lsbcmnds

The SSID is being broadcasted.  Not sure about MAC filtering. I see a MAC address for the Router Lan settings and another for the Router Wan settings. Encryption is WEP.  I can get to the point where it asks me for the key.  I put it in and it gets to 28% complete and fails.  I have tried connected to some unprotected wireless networks and the same thing happens.  28% and quits.  My sound doesn't work either and that was working before I did the dual boot setup.

---

### Post by kevdog on 2007-10-21
Where are you getting the 28% stuff -- From the command line Im not familar with that output at all.

What is in the lscmnds subfoler??

---

### Post by madgreek on 2007-10-21
There is an icon in the tray where you can click to connect to a wireless network.  When I tell it to connect it starts connecting until it gets to 28% and then fails.  It does this on any wireless network, not just my router.

---

### Post by nismoskys on 2007-10-21
followed all the directions step by step, but I'm still getting "No DHCPOFFERS received."

*posted a thread on my question instead ->  [http://ubuntuforums.org/showthread.php?p=3592180#post3592180]("http://ubuntuforums.org/showthread.php?p=3592180#post3592180")

---

### Post by kevdog on 2007-10-21
No icon is involved in these instructions --  if your having a problem with the icon, these instuctions are not for you!

I see that you are getting no dhcp offers.  What is the sgnal strength reported for your router for 

iwlist scan

---

### Post by nismoskys on 2007-10-21
```
 Quality:76/100 Signal level:-47dBm Noise level:-96 dBm
```

---

### Post by nismoskys on 2007-10-21
anything??

---

### Post by madgreek on 2007-10-21
I am not using the icon with these instructions.  It won't connect when I follow the instructions.  When I use the GUI to manually set addresses, DNS, and Gateway or if I set it to automatic, there is a Icon to click to see available wireless networks.  I can see the network, but when it tries to connect it only gets to 28%.

Here is the scan

wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:1F:A4:3E
                    ESSID:"default"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:1A:70:F6:C6:99
                    ESSID:"Gameserver"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

---

### Post by kevdog on 2007-10-21
I wish I could help you guys more, since it seems like you guys are doing everything right.  Ive seen random problems like this before, and its always something I would never think to do that would fix it -- like uninstall a different package, or disable ipv6.  Try disabling ipv6, not sure if this is going to help.  Ive also seen some cards struggle with 64 bit wep (some driver problem) so I dont know if you are effected by this.  Have you tried ascii based wep authentication:
sudo iwconfig wlan0 key s:ASCII

With WEP, are you using the first hex key??
You can set your key index with the following command:
sudo iwconfig wlan0 key [1] XXXXXXX (or s:ASCII) key [1]

---

### Post by Rbleattler on 2007-10-23
dude i love you, you're now my best friend in the world!

---

### Post by underscoredavid on 2007-10-23
Kevdog

Here's one for you.
I have two identical network cards. (ipw3945)

One is working A-OK.
The other is showing up in the system, but with no logical name, and no mac address. I've checked the wireless switches, bios settings for the card - and it is enabled...

Here's what I get for "lshw -C network"

  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:60:79:85
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=10.10.1.9 latency=0 module=ipw3945 multicast=yes wireless=IEEE 802.11g

Obviously - the bottom one is working, top is not.

Where would I even start to get a logical name assigned to this. Querying "dmesg" doesn't give me anything interesting (errors) about this card.

I've tried other forums, threads, and this is the closest one I could find relevent. ANY help at all is appreciated.

Thanks.

---

### Post by kevdog on 2007-10-23
Just some random thoughts

Do you need two wireless cards running at the same time?? Ok I guess I could think of some situations this might be needed but just a thought.

If the working wireless card is removed, does the other card work.

Ive used two different wireless cards plugged into two separate pcmcia slots before, (atheros and broadcom), however I didnt use them at the same time.  I brought one interface down and the other up. Your situation is slightly different since your not even getting an interface name assigned.

I guess first step is to verify the first card actually works.

---

### Post by underscoredavid on 2007-10-23
> **kevdog said:**
> Just some random thoughts

Do you need two wireless cards running at the same time?? Ok I guess I could think of some situations this might be needed but just a thought.

If the working wireless card is removed, does the other card work.

Ive used two different wireless cards plugged into two separate pcmcia slots before, (atheros and broadcom), however I didnt use them at the same time.  I brought one interface down and the other up. Your situation is slightly different since your not even getting an interface name assigned.

I guess first step is to verify the first card actually works.


The card actually works - I've used both by themselves in the same install with no problems. However, once there are two cards present, only one works. 

As far as the need - if I don't want to buy another card, for what I'm trying to do/play with, yeah, this situation I need two.

Thanks for responding, you're the first in about a million posts all over the place - any ideas on where to start after verifying the card functions correctly?

---

### Post by kevdog on 2007-10-23
Are these two pcmcia slots?? Just wondering if one slot is given priority over the other.  

Couple things to try, say you got the same scenario as you presented above, what if you bring the interface down, modprobe -r the ipw module, then modprobe the ipw module, then check with lshw -C network?  Which card is assigned the interface name.  What if you switch the cards?

How many times in lsmod | grep ipw is the ipw driver listed?

---

### Post by underscoredavid on 2007-10-23
> **kevdog said:**
> Are these two pcmcia slots?? Just wondering if one slot is given priority over the other.  

Couple things to try, say you got the same scenario as you presented above, what if you bring the interface down, modprobe -r the ipw module, then modprobe the ipw module, then check with lshw -C network?  Which card is assigned the interface name.  What if you switch the cards?

How many times in lsmod | grep ipw is the ipw driver listed?


These are two mini-pci express cards (Intel 3945abg) - I'm getting the feeling slot 2 is getting priority. If I switch the cards, it seems to follow that slot. It's the first slot I'm having problems with.

I've verified this slot works however, because, in the windows side of this install - it works flawlessly - except, I have no use for two cards in windows.

Under "lsmod" i've only got the driver coming up once.

When I "modprobe -r ipw3945" then "lshw" - both cards show up as unclaimed network controllers.

When I "modprobe ipw3945" - both cards show up again, the second one w/ the logical name/mac/etc... the other, with just the same basic info. This is the same as it was before.

---

### Post by kevdog on 2007-10-23
Im just shooting from the hip here b/c I googled around and found nothing similar to your problem except my experience (which isnt exactly similar).  However just wondering if there are windows xp drivers available for your device.  Here is what Im thinking.  Im not sure if you are hardware limited and only one device is going to work at a time, or its more a driver issue where two devices cant use the same driver at once.  I just dont know.  What if however we could make one device use the native ipw driver and the other ndiswrapper.  Im not sure if this would work.

Here is what I was thinking however
Most likely the card not show is interface eth0
The card in slot two is interface eth1

You could probably confirm this by taking out the card in slot 2 and just using slot 1 and see if the device is assigned eth0.

You could then probably add some aliases in /etc/modules like the following:
alias eth0 ndiswrapper
alias eth1 ipw3945

Here is a reference although I dont if I completely understand everything:
[http://linux.about.com/od/lkm_howto/a/hwtlkm06t03.htm](http://linux.about.com/od/lkm_howto/a/hwtlkm06t03.htm)


One last random thought
What if you just type
sudo ifconfig eth0 up

What happens??

---

### Post by underscoredavid on 2007-10-23
> **kevdog said:**
> Im just shooting from the hip here b/c I googled around and found nothing similar to your problem except my experience (which isnt exactly similar).  However just wondering if there are windows xp drivers available for your device.  Here is what Im thinking.  Im not sure if you are hardware limited and only one device is going to work at a time, or its more a driver issue where two devices cant use the same driver at once.  I just dont know.  What if however we could make one device use the native ipw driver and the other ndiswrapper.  Im not sure if this would work.

Here is what I was thinking however
Most likely the card not show is interface eth0
The card in slot two is interface eth1

You could probably confirm this by taking out the card in slot 2 and just using slot 1 and see if the device is assigned eth0.

You could then probably add some aliases in /etc/modules like the following:
alias eth0 ndiswrapper
alias eth1 ipw3945

Here is a reference although I dont if I completely understand everything:
[http://linux.about.com/od/lkm_howto/a/hwtlkm06t03.htm](http://linux.about.com/od/lkm_howto/a/hwtlkm06t03.htm)


One last random thought
What if you just type
sudo ifconfig eth0 up

What happens??

The ndiswrapper route is a no-go. That limits what I'm trying to do with the card. (Monitoring mode/injection/etc...). You may have hit it on the head w/ the two cards not being able to use the same driver, though I'm not proficient enough to know/find out.

As far as eth0 is concerned - that's actually the integrated broadcom nic and hasn't given me any problems. 

Looks like I may be buying a PCMCIA card or another mini-pci express card for this setup. That sucks.

Thanks for your help though!

---

### Post by kevdog on 2007-10-24
What if you just type
sudo ifconfig eth2 up

---

### Post by underscoredavid on 2007-10-24
> **kevdog said:**
> What if you just type
sudo ifconfig eth2 up


eth2 doesn't exist.
the exact error is "eth2: ERROR while getting interface flags: No such device"

interesting thing though - i disabled one of the mini-pci e slots completely in the bios (the one that was working flawlessly) and the other card came up immediately, except in the system it had it as "eth3" , there was no eth1 or eth2. worked and everything.

if i could get the second card assigned a logical name, while the first card was working, i'd be able to troubleshoot if from there. i'm wondering if this is some sort of bug with 2 cards using the same driver, you wouldn't think so, but i'm not familiar enough with the way hardware interfaces with drives under linux.

---

### Post by kevdog on 2007-10-24
Thats why I wanted you to use ndiswrapper -- only for testing purposes.  Im not sure if you can use the same driver twice, however it would seem logical that if one was using ndiswrapper and the other ipw and for some reason both network cards worked in this scenario, that it would tell me that it was most likely a driver or configuration problem rather than a hardware problem.  Again Im not exactly sure how the kernel interacts and assigns drivers (or duplicate copies of a driver).  Im just trying to rule some things out.

---

### Post by SeanBlader on 2007-10-25
Kevdog, wanted to let you know this worked for me in Gutsy using NDISWrapper 1.47 with a Broadcom 43xx on a Dell Inspiron 8500. So it looks like it's an issue with Gutsy's Network manager or something. I was also glad to see someone mention the change to iftab for Gutsy, I did see that previously as well. Any idea if Network Manager can be backdated to Feisty's or if there's a configuration fix for it somewhere? If not, at least I know it CAN work, nice job.

---

### Post by tonafernandez on 2007-10-25
Hello, i have been looking around
i have a dv2000 hp laptop with an AMD and the 64bit version of Gutsy
My wireless network has WPA it works
After i go thru a lot of hoops
boot up, change the settings on my wireless ssid and password, click ok (they are already stored)
change them back
and the network manager does it thing and activates the connection

i dont know why i dont get an IP at the moment of boot up, if i go to wired connection everything works as supposed
i have a broadcom 43xx driver

any ideas?... all i can think of is that unfortunatly my card is not trying to fetch an IP from the router

i have tried static ip as well and it doesnt work 

pls help!

---

### Post by kevdog on 2007-10-25
You got to give me more details like how you are setting up your wpa connection.  This post is really only concerned with setting up manual connections, and not with problems with network manager.  I know a lot about network manager, but to delve into it here in this particular post would be a little off topic.

---

### Post by d_thrasher on 2007-10-28
Kevdog, I am hoping you are still around and can help me with this:

My wifi card has the logical address of wifi0, but the iwlist scan is performed by ath0?  Is this why I'm not getting any connection? And what about the wifi0: unknown hardware address type 801 error in the dhclient command?
 
Please help me sever the cable!

devo@devo-desktop:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network:0             
       description: Ethernet interface 
       product: SiS900 PCI Fast Ethernet 
       vendor: Silicon Integrated Systems [SiS] 
       physical id: 4 
       bus info: pci@0000:00:04.0 
       logical name: eth0 
       version: 90 
       serial: 00:14:85:14:9f:fc 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.1.44 latency=64 maxlatency=11 mingnt=52 module=sis900 multicast=yes 
  *-network:1 
       description: Wireless interface 
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor 
       vendor: Atheros Communications, Inc. 
       physical id: c 
       bus info: pci@0000:00:0c.0 
       logical name: wifi0 
       version: 01 
       serial: 00:18:e7:2e:60:50 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g 

devo@devo-desktop:~$ sudo iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wifi0     Interface doesn't support scanning. 

ath0      Scan completed : 
          Cell 01 - Address: 00:E0:98:CC:54:D7 
                    ESSID:"ThrasherNet" 
                    Mode:Master 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=17/70  Signal level=-78 dBm  Noise level=-95 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s 
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                              36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Extra:bcn_int=200 
          Cell 02 - Address: 00:09:5B:ED:5D:B2 
                    ESSID:"NETGEAR" 
                    Mode:Master 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm 
                    Encryption key:off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:bcn_int=100 
                    Extra:ath_ie=dd0900037f01010006ff7f 
          Cell 03 - Address: 00:18:39:3F:17:5F 
                    ESSID:"linksys" 
                    Mode:Master 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=19/70  Signal level=-76 dBm  Noise level=-95 dBm 
                    Encryption key:off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 
                              12 Mb/s; 48 Mb/s 
                    Extra:bcn_int=100 
          Cell 04 - Address: 00:12:0E:40:DC:B6 
                    ESSID:"06B408648877" 
                    Mode:Master 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=158/70  Signal level=-193 dBm  Noise level=-95 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s 
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                              36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Extra:bcn_int=200 

devo@devo-desktop:~$ sudo dhclient ath0 
There is already a pid file /var/run/dhclient.pid with pid 134519120 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

wifi0: unknown hardware address type 801 
wifi0: unknown hardware address type 801 
Listening on LPF/ath0/00:18:e7:2e:60:50 
Sending on   LPF/ath0/00:18:e7:2e:60:50 
Sending on   Socket/fallback 
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15 
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 1 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping.

---

### Post by kevdog on 2007-10-28
Your using the madwifi drivers.  According to the madwifi specs it creates a virtual interface for each device.  The device is wifi0, the virtual interface is ath0.  All command line is directed toward the virtual interface, not the physical device itself.  You need to probably specifiy a specific essid on the command line before the dhclient command.  All though you mentioned the error with wifi0, where is the output that  showed this error?

---

### Post by d_thrasher on 2007-10-28
where would I put the essid in the command? wifi0 error listed below.

devo@devo-desktop:~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:18:e7:2e:60:50
Sending on LPF/ath0/00:18:e7:2e:60:50
Sending on Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by kevdog on 2007-10-28
Look at the original post (first page).  It will tell you where to put the essid.  If that error persists, it could be a problem.

Post 
lshw -C network

---

### Post by d_thrasher on 2007-10-28
I just ran trough the entire exercise again.  Output below. I'm sure it has something to do with the unknown hardware 801 error after sudo dhclient -r ath1, but I don't know what to do about it. Is there a way I can start from scratch? maybe something wonky in a configuration file?

devo@devo-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 90
       serial: 00:14:85:14:9f:fc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.1.44 latency=64 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: wifi0
       version: 01
       serial: 00:18:e7:2e:60:50
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
devo@devo-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath1      Scan completed :
          Cell 01 - Address: 00:E0:98:CC:54:D7
                    ESSID:"ThrasherNet"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=13/70  Signal level=-82 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
          Cell 02 - Address: 00:09:5B:ED:5D:B2
                    ESSID:"NETGEAR"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=209/70  Signal level=-142 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f01010006ff7f
          Cell 03 - Address: 00:18:39:3F:17:5F
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=0/70  Signal level=-95 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

devo@devo-desktop:~$ sudo ifconfig eth0 down
devo@devo-desktop:~$ sudo ifconfig ath1 down
devo@devo-desktop:~$ sudo dhclient -r ath1
There is already a pid file /var/run/dhclient.pid with pid 7271
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath1/00:18:e7:2e:60:50
Sending on   LPF/ath1/00:18:e7:2e:60:50
Sending on   Socket/fallback
devo@devo-desktop:~$ sudo ifconfig ath1 up
devo@devo-desktop:~$ sudo iwconfig ath1 essid "ThrasherNet"
devo@devo-desktop:~$ sudo iwconfig ath1 key 526d2c6b426a42646f3f382058
devo@devo-desktop:~$ sudo iwconfig ath1 mode managed
devo@devo-desktop:~$ sudo dhclient ath1
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath1/00:18:e7:2e:60:50
Sending on   LPF/ath1/00:18:e7:2e:60:50
Sending on   Socket/fallback
DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by kevdog on 2007-10-28
Check your system logs (there is a reference in the reference section in the original post) to see if you find anything

dmesg | more

---

### Post by d_thrasher on 2007-10-28
Well, there is this: 
[   39.235637] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.319034] ath_hal: module license 'Proprietary' taints kernel.
[   39.319859] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   39.547523] wlan: 0.8.4.2 (0.9.3.2)
[   39.567685] ath_pci: 0.9.4.5 (0.9.3.2)
[   39.567748] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 16 (level, low) -> IRQ 21
[   40.236346] ath_rate_sample: 1.2 (0.9.3.2)
[   40.236900] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   40.236906] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   40.236916] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   40.236923] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   40.236927] wifi0: mac 7.9 phy 4.5 radio 5.6
[   40.236933] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   40.236935] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   40.236937] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   40.236939] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   40.236941] wifi0: Use hw queue 8 for CAB traffic
[   40.236943] wifi0: Use hw queue 9 for beacons
[   40.306535] wifi0: Atheros 5212: mem=0xe8000000, irq=21


Then a lot of stuff like this: 

[ 1683.492931] Unknown OutputIN= OUT=ath1 SRC=169.254.5.129 DST=192.168.1.1 LEN=80 TOS=0x00 PREC=0x00 TTL=64 ID=13146 DF PROTO=UDP SPT=32780 DPT=53 
LEN=60 
[ 1689.336286] Unknown OutputIN= OUT=ath1 SRC=192.168.1.44 DST=205.188.9.53 LEN=112 TOS=0x00 PREC=0x00 TTL=64 ID=9813 DF PROTO=TCP SPT=56667 DPT=519
0 WINDOW=29957 RES=0x00 ACK PSH URGP=0 
[ 1712.238621] eth0: Media Link On 100mbps full-duplex 
[ 1719.782730] eth0: no IPv6 routers present
[ 1820.302925] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:12:f0:a3:29:4a:08:00 SRC=192.168.1.47 DST=192.168.1.255 LEN=237 TOS=0x00 PREC=0x00 TTL=
128 ID=541 PROTO=UDP SPT=138 DPT=138 LEN=217 
[ 1826.247646] ath1: no IPv6 routers present
[ 2085.655551] ath1: no IPv6 routers present
[ 2225.572919] Unknown OutputIN= OUT=ath1 SRC=192.168.1.44 DST=207.46.106.20 LEN=70 TOS=0x00 PREC=0x00 TTL=64 ID=41815 DF PROTO=TCP SPT=32997 DPT=18
63 WINDOW=13936 RES=0x00 ACK PSH URGP=0 
[ 2231.415242] Unknown OutputIN= OUT=ath1 SRC=169.254.5.129 DST=192.168.1.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=19331 DF PROTO=UDP SPT=32780 DPT=53 
LEN=43 

Any of that say anything to you?

---

### Post by kevdog on 2007-10-28
Are you running wired and wireless at the same time??

Can you post
ifconfig

---

### Post by d_thrasher on 2007-10-28
devo@devo-desktop:~$ ifconfig
ath1      Link encap:Ethernet  HWaddr 00:18:E7:2E:60:50  
          inet6 addr: fe80::218:e7ff:fe2e:6050/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:14:85:14:9F:FC  
          inet addr:192.168.1.44  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fe14:9ffc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22085 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14910385 (14.2 MB)  TX bytes:3101423 (2.9 MB)
          Interrupt:20 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5176 (5.0 KB)  TX bytes:5176 (5.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-18-E7-2E-60-50-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65942 errors:0 dropped:0 overruns:0 frame:62139
          TX packets:3557 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:5605636 (5.3 MB)  TX bytes:180947 (176.7 KB)
          Interrupt:21

---

### Post by kevdog on 2007-10-28
Did you bring the wired interface down prior to trying to bring up the wireless interface?

sudo ifconfig eth0 down
sudo ifconfig ath1 up

---

### Post by d_thrasher on 2007-10-28
yep

---

### Post by Griff on 2007-10-29
This is a *great* guide.  Very nice work.  I'll definitely be using this later to figure out a few issues of my own.

---

### Post by Griff on 2007-10-30
Kevdog.  Thank you.  This was so much easier than trying to find the right gui that worked.  The last time I installed a *buntu on my laptop I struggled for a couple days trying to figure out why I couldn't connect to wireless networks and it ended up being a gui problem.  Nice guide.=D>

---

### Post by kevdog on 2007-10-30
If you can do it from the command line, you dont ever have to worry what happens if suddenly network manager acts up (which it does), or if you take your laptop elsewhere and it cant connect through the GUI  -- but it did at home.  Again, the command line gives you the basic knowledge to get a connection when other methods are failing -- its a very reliable if not the ultimate fallback!!

---

### Post by Griff on 2007-11-04
I have no issues with establishing/maintaining connection on unprotected networks (like at school), but WEP just isn't working.  The last step yields the following message, "No DHCPOFFERS received.  No working leases in persistent database - sleeping."

Now I know the network is up because I can scan for it and see it with the pre installed gui.  Any idea what's going on?

Thanks,
Griff

---

### Post by kevdog on 2007-11-04
64 or 128 bit wep??  Are you using hexidecimal or ascii?  If hexidecimal did you set the key index correctly?? (man iwconfig gives examples how to do this)

---

### Post by Griff on 2007-11-04
It's 128 hex and I believe I did it correctly.  I'll double check.

---

### Post by Griff on 2007-11-04
> **kevdog said:**
> If hexidecimal did you set the key index correctly??
I'm not sure what you mean by index, but according to the man page all I should need to do is:
```
 sudo iwconfig eth0 key 11111111111111111111111111
```
right?

edit: I saw the entry about index but from what it says I don't think it applies to me

---

### Post by kevdog on 2007-11-04
yes thats the right formati, you need to make sure then that key is 25 (24??) characters is in length and that its key index 1 on the router.

---

### Post by solaris_wiz on 2007-11-04
I went through the steps, but I'm still unable to pull an IP.  Any help would be appreciated.

Here's what I end up getting:

> $ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:12:17:9d:8a:ee
Sending on   LPF/eth1/00:12:17:9d:8a:ee
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


---

### Post by Griff on 2007-11-04
All right, it was key 1 on the router and I enforced the key to index [1] on my card, but the outcome is the same as before.

---

### Post by solaris_wiz on 2007-11-04
> **Griff said:**
> All right, it was key 1 on the router and I enforced the key to index [1] on my card, but the outcome is the same as before.

looks like we're in the same boat right now, Griff.

did you bring your ether connection down before you tried enabling your wifi connection?
Just a thought, perhaps that could be holding you back, as I read it in a previous page.

---

### Post by HUIG on 2007-11-06
Now, does it matter if the ESSID contains spaces? Does it matter if the WPA is a passphrase? (both within the quotation marks tho)

Now, this is what I'm (also) getting

Listening on LPF/eth1/00:19:7e:b3:2c:89
Sending on   LPF/eth1/00:19:7e:b3:2c:89
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

using ndiswrapper-1.47 installed on a clean gusty as detailed in
[http://ubuntuforums.org/showthread.php?t=297092&highlight=bcm43xx](http://ubuntuforums.org/showthread.php?t=297092&highlight=bcm43xx)

network name was found after this installation but i never got connected to it. also switching back to wired connection never works immediately, it might just take some time but usually i switch it on and off a couple of times from Administration/Network before anything happens

now did I use this command correctly?
sudo wpa_supplicant -w -Dwext -ieth1 -c/etc/wpa_supplicant.conf

it does not result in anything, I had to terminate

And here's some more info
  *-network DISABLED      
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:b3:2c:89
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.47+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g


Thanks, this is wrecking my head, being a beginner doesn't help!

---

### Post by kevdog on 2007-11-06
Here is your problem:

*-network DISABLED

So if you have a wired connection, bring down the wired interface, and then bring up the wireless interface:

sudo ifconfig eth0 down
sudo ifconfig eth1 up

Recheck lshw -C network to confirm you do not have a disabled statement.

No spaces in essid --- spaces = BIG PROBLEMS!

Try an unencrypted connection before using wpa.

---

### Post by HUIG on 2007-11-06
> **kevdog said:**
> Here is your problem:

*-network DISABLED

So if you have a wired connection, bring down the wired interface, and then bring up the wireless interface:

sudo ifconfig eth0 down
sudo ifconfig eth1 up

Recheck lshw -C network to confirm you do not have a disabled statement.

No spaces in essid --- spaces = BIG PROBLEMS!

Try an unencrypted connection before using wpa.

ah yeah well that was only disabled when I copied that report, thats not the problem here

but apparently "get your own broadband, DICK!"-essid has to be changed, bah. been having problems logging into the router and its a common one to our house so just wanted to try and get it working without service disrupts but thats an another story altogether and will have to have a look at it now then...

thanks!

---

### Post by Ubuntiac on 2007-11-11
I'm having the *exact* same problem as d_thrasher, right down to the outputs above, error messages and logical names, and yes I've checked that my wired is down and there's no NETWORK DISABLED on my ath0/wifi0 device.

---

### Post by kevdog on 2007-11-11
Ubuntiac

Can you post the results of lshw -C network and iwlist scan?

---

### Post by Ubuntiac on 2007-11-12
> **kevdog said:**
> Can you post the results of lshw -C network and iwlist scan?

lshw -C network:
```
  *-network DISABLED
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:19:d1:88:59:b4
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=1.1-0 latency=0 link=no module=e1000 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wifi0
       version: 01
       serial: 00:18:e7:27:12:5f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

```


iwlist scan:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

```


and just for good measure, lspci:

```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b1)
07:00.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
07:01.0 RAID bus controller: Silicon Image, Inc. PCI0680 Ultra ATA-133 Host Controller (rev 02)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

```

Strange thing is that it seemed to work fine before the recent network-manager update, and now it still seems to work *sometimes*. If I don't use it for a few hours though it just seems to drop out and not even a computer restart gets it back. Oh, and for the record, my Atheros card usually supports scanning, just fine!

Thanks in advance for any ideas!

---

### Post by kevdog on 2007-11-12
You are using the madwifi drivers which usually are very reliable.  B/c of the way madwifi works, it creates virutal interfaces (usually ath0) for your physical card located at wifi0.  

I used to have a problem with my broadcom card doing something similar to what you describe.  Short of rebooting, the only thing I found would work was to create a script that would bring down the interface, unload the driver module, reload the driver module, and then bring up the interface.  Although definitely not an ideal solution it would at least save me a reboot.  

Since you state that sometimes your atheros card work, see if it scan (iwlist scan) using ath0.  I dont think wif0 is truly the interface to work through.

---

### Post by tonycollinet on 2007-11-12
Thanks for this process - wirless now works if I type in these commands.

Now - sorry for a total noob question (I am one - a noob that is)

How do I set things up so I don't have to type the command sequence everytime I start my PC? I assume I can put them into some sort of script file and have it auto run at start up? What if I want to make it flexible for different networks?

Or is there anything I can do to make the GUI work (It detects the SSID from the wirless, but repeatedly asks me to put in the WEP Key, and gets no further, although it did work once.)

---

### Post by Ubuntiac on 2007-11-12
I know in Kubuntu (or any KDE distro) you just put the script in a text file in ~/.kde/autostart, make sure the file name ends in .sh, rick click on it and check "executable" under the permissions tab. I'm sure there's something similar in gnome.

---

### Post by kevdog on 2007-11-12
If the manual commands are working for you on the command line, then Im not sure why network manager is not working.

A couple of things
WICD is an alternative to network manager.  You might try this.  I know that at its heart it works similar to the command line, but is very fancy and provides a GUI, tray icon, etc.

You can always write a script file that you either launch manually or when you log in.  You could get really fancy with the script file, or keep it rather basic.  Seems in my situation the more I jazz up the script file, I decrease the chances it will actually work.  Usually I just scan for available networks with iwlist scan, and then wrote a script and call it with:
network_connect NETWORK_NAME

NETWORK_NAME in the script is variable $1, so everything pretty much connects.  Simple but it works.

---

### Post by bliffle on 2007-11-12
"wicd" gave me a headache last week. the install unloaded NetworkManager then failed to complete. I couldn't successfully reload NM after that, so I was forced to upgrade from Feisty to Gutsy before I planned.

---

### Post by Ubuntiac on 2007-11-12
Thanks for your help Kevdog,

I guess I'm interested in getting my wireless to work via commandline not only so I can have it working (I have a working laptop with an Intel card :)), but also so I can find out what was wrong and let the good folks maintaining network-manager fix it for everyone, so I think I'll skip WICD. Thanks for th suggestion, though. Now to try and figure out what's actually going on here...

---

### Post by bliffle on 2007-11-12
If a guy had ONE cli command that would spell out what the pertinent values are for a wireless connection, then a guy could record that info when the connection is running correctly and go about re-instating those values when he has a problem.

The first step to solving most bugs is to insrument the system.

---

### Post by bliffle on 2007-11-13
Is there a monitor program of some kind that will dynamically display the current upload and download speeds?

---

### Post by kevdog on 2007-11-13
Check out conky.  I really like it, however it might not be what you are looking for.  Its a system monitor tool.  There is a HOW-TO in the Tutorials&Tips section.

---

### Post by Chazall1 on 2007-11-14
I need assistance Please

  I have Gutsy on a Dell Dimension B110 Desktop using a Linksys Router with  WEP. I can not conect to my WEP. However I was connecting to the Internet using other Linksys networks in the neighborhood. This however has stoped working, I do not have ndiswrapper installed, would this make a difference???
Here are my outputs if I use wmaster0 as my interface:

ace@ace-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:12:17:8c:99:3c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:13:20:d4:8e:45
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes

If I use wmaster0 in <interface>
ace@ace-desktop:~$ sudo ifconfig wmaster0 down
[sudo] password for ace:
ace@ace-desktop:~$ sudo dhclient -r wmaster0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
ace@ace-desktop:~$ sudo ifconfig wmaster0 up
ace@ace-desktop:~$ sudo iwconfig wmaster0 essid "lish1"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wmaster0 ; Operation not supported.
ace@ace-desktop:~$ sudo iwconfig wmaster0 key 6063547000
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wmaster0 ; Operation not supported.
ace@ace-desktop:~$ sudo iwconfig wmaster0 mode Managed
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wmaster0 ; Operation not supported.
ace@ace-desktop:~$ sudo dhclient wmaster0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

If I run wlan0, here is the output:

ace@ace-desktop:~$ sudo ifconfig wlan0 down
[sudo] password for ace:
ace@ace-desktop:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 6040
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:12:17:8c:99:3c
Sending on   LPF/wlan0/00:12:17:8c:99:3c
Sending on   Socket/fallback
ace@ace-desktop:~$ sudo ifconfig wlan0 up
ace@ace-desktop:~$ sudo iwconfig wlan0 essid "lish1"
ace@ace-desktop:~$ sudo iwconfig wlan0 key 6063547000
ace@ace-desktop:~$ sudo iwconfig wlan0 mode Managed
ace@ace-desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:12:17:8c:99:3c
Sending on   LPF/wlan0/00:12:17:8c:99:3c
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Can anyone assist me, I have no WIRELESS at this time

Thanks

---

### Post by kevdog on 2007-11-15
Can you post the results of 

iwlist scan

---

### Post by oraste on 2007-11-15
Great, my main broplem was that set configuration from X to WPA and the whole system freezes. With this info I got it back default by 

gksudo gedit /etc/network/interfaces

saved the old file and made orginal as black. restart and voila :)

---

### Post by Chazall1 on 2007-11-15
NM Showing no Wireless

ace@ace-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

I added ndiswrapper and followed the How Too RT2500, etc wireless cards Gutsy in the forums.
When I add the drivers to the 'Blacklist in etc/modprobs, everything seems fine untill
I run ndiswrapper -l, my output is this,
ace@ace-desktop:~$ ndiswrapper -l
rt2500 : invalid driver!
rt2500pci : invalid driver!
ace@ace-desktop:~$ 
I have no Internet now, The NM does not give me an option for wireless!!
Here is my network interface file info as well

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 intel dhcp

---

### Post by kevdog on 2007-11-15
Chazall

You have two different options for your rt2500 card

#1. Compile and use serial monkey rt2500 driver
#2. Use ndiswrapper with windows driver (xp) for the rt2500 

In both cases the rt2500pci driver shipped in gutsy needs to be blacklisted (since this third option -- using the built-in driver -- is very unstable in most cases -- hence resorting to options #1 or #2).  Which option above are you trying to use??

---

### Post by Chazall1 on 2007-11-15
#2. Use ndiswrapper with windows driver (xp) for the rt2500 
I have installed ndiswrapper and have followed the instructions here, [http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547)

I have Blacklisted the rt2500 and the rt2500pci drivers. However now when I boot up My Network fails to load, along with the modules, I see this briefly in the Usplash script that indicates the status of the loading process.
Some additional outputs

I am having NO luck on getting my Wireless to Function any more, Before I added ndiswrapper, I had some functionality with picking up other non WEP Linksys connections, Now I do not even have a choice for any Wireless functions, Dell Dimension B110, Here are some outputs

ace@ace-desktop:~$ iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

I added ndiswrapper and followed the How Too RT2500, etc wireless cards Gutsy in the forums.
When I add the drivers to the 'Blacklist in etc/modprobs, everything seems fine untill
I run ndiswrapper -l, my output is this,
ace@ace-desktop:~$ ndiswrapper -l
rt2500 : invalid driver!
rt2500pci : invalid driver!
ace@ace-desktop:~$
I have no Internet now, The NM does not give me an option for wireless!!
Here is my network interface file info as well

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 intel dhcp

Before ndiswrapper
Output I have Gutsy on a Dell Dimension B110 Desktop using a Linksys Router with WEP. I can not conect to my WEP. However I was connecting to the Internet using other Linksys networks in the neighborhood. This however has stoped working, I do not have ndiswrapper installed, would this make a difference???
Here are my outputs if I use wmaster0 as my interface:

ace@ace-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
*-network:0
description: Wireless interface
product: RT2500 802.11g Cardbus/mini-PCI
vendor: RaLink
physical id: 0
bus info: pci@0000:01:00.0
logical name: wmaster0
version: 01
serial: 00:12:17:8c:99:3c
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=rt2500pci latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11g
*-network:1
description: Ethernet interface
product: 82562EZ 10/100 Ethernet Controller
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:01:08.0
logical name: eth0
version: 02
serial: 00:13:20:d4:8e:45
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes

If I use wmaster0 in <interface>
ace@ace-desktop:~$ sudo ifconfig wmaster0 down
[sudo] password for ace:
ace@ace-desktop:~$ sudo dhclient -r wmaster0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on LPF/wmaster0/
Sending on Socket/fallback
ace@ace-desktop:~$ sudo ifconfig wmaster0 up
ace@ace-desktop:~$ sudo iwconfig wmaster0 essid "lish1"
Error for wireless request "Set ESSID" (8B1A) :
SET failed on device wmaster0 ; Operation not supported.
ace@ace-desktop:~$ sudo iwconfig wmaster0 key 6063547000
Error for wireless request "Set Encode" (8B2A) :
SET failed on device wmaster0 ; Operation not supported.
ace@ace-desktop:~$ sudo iwconfig wmaster0 mode Managed
Error for wireless request "Set Mode" (8B06) :
SET failed on device wmaster0 ; Operation not supported.
ace@ace-desktop:~$ sudo dhclient wmaster0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on LPF/wmaster0/
Sending on Socket/fallback
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

If I run wlan0, here is the output:

ace@ace-desktop:~$ sudo ifconfig wlan0 down
[sudo] password for ace:
ace@ace-desktop:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 6040
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:12:17:8c:99:3c
Sending on LPF/wlan0/00:12:17:8c:99:3c
Sending on Socket/fallback
ace@ace-desktop:~$ sudo ifconfig wlan0 up
ace@ace-desktop:~$ sudo iwconfig wlan0 essid "lish1"
ace@ace-desktop:~$ sudo iwconfig wlan0 key 6063547000
ace@ace-desktop:~$ sudo iwconfig wlan0 mode Managed
ace@ace-desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:12:17:8c:99:3c
Sending on LPF/wlan0/00:12:17:8c:99:3c
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Maybe I should Re-Install, My internet was working for a couple of weeks, without my WEP

---

### Post by Chazall1 on 2007-11-15
Sorry, I forgot I gave you this Info already !!!

---

### Post by NothingtoGein on 2007-11-15
I followed all your steps and still can't get on.  I get the same line everyone else is getting "No DHCPOFFERS received.  No working leases persisting databases - sleeping."

Have you or anyone figured out why everyone keeps getting these messages?

---

### Post by kevdog on 2007-11-15
I read your previous post however Im just trying to grasp your knowledge of what you are trying to accomplish since your setup is kind of messed up.

configuration: broadcast=yes driver=rt2500pci

This line tells me your system is trying to use the builtin rt2500pci driver for your wireless card.  So if you dont want to use this driver you need to do the following:

sudo modprobe -r rt2500pci
Place a line in the /etc/modprobe.d/blacklist file that states
blacklist rt2500pci

This prevents the drivers from loading at startup 

With ndiswrapper- where are your .sys and .inf files located (these are the windows drivers)?  You cant try to load multiple drivers with ndiswrapper, so to basically start over and wipe the slate clean, you

sudo rm -rf /etc/ndiswrapper/*

Then you load the windows drivers into ndiswrapper with:
sudo ndiswrapper -i ****.inf
And then load the ndiswrapper module into the kernel with:
sudo modprobe ndiswrapper

To make sure the ndiswrapper custom module is loaded at boot, place a line in the /etc/modules files that states:
ndiswrapper

Please also post iwlist scan.

---

### Post by NothingtoGein on 2007-11-15
Actually I just figured out the problem.  It wasn't any of the above.  I needed a static IP address instead of a DHCP.

Just input something like

DEVICE=eth0
BOOTPROTO=static
IPADDR=192.168.1.2
NETMASK=255.255.255.0
NETWORK=192.168.1.0
BROADCAST=192.168.1.255
ONBOOT=yes

Gives you a static IP - no more "No DHCPOFFERS received messages".

Google static IP ubuntu for people suffering the same problem I had - which just looking at this thread...ALOT.

---

### Post by kevdog on 2007-11-15
NothingtoGein

Where do you put or type this information??

---

### Post by Chazall1 on 2007-11-15
Well I, # out what ndiswrapper configured in /etc/modules, and /etc/modprobe.d/blacklist. I set /etc/network/interfaces to

auto lo
iface lo inet loopback

I have Wireless back, I have been using the internet for the past 3 hrs, on another router, not mine. I disabled my WEP about an hour ago, and the NM still showes a security key in the NM Wireless networks. I will watch and see what happens!!!!!

---

### Post by Ubuntiac on 2007-11-19
I can't believe I missed this but...

sudo ifconfig ath0 up
sudo dhclient ath0 essid myessid
<ignore error messages>
<open webbrowser and...>

Internet all works! I think my problem before was that when I saw errors in the command line and NM still showed unconnected, I nievely thought that it mustn't have worked, yet when I actually use a browser / instant messenger / adept it all just works. Almost instantly NM then notices and shows connected.

Happy d'oh!

Thanks Kevdog, you are a legend amongst men for supporting this thread (and you have the coolest avatar ever!).

Praise be to Kevdog, awooooooooooooo!

---

### Post by kevdog on 2007-11-19
I definitely no legend, legend in your mine but not mine.

---

### Post by madsmaddad on 2007-11-25
> **kevdog said:**
> The commands are the same, however Im not sure if this will work.  Its something about the drivers and Linux.  So basically Im saying is that Im not certain ubuntu can connect to any router with hidden ssid broadcast.

It does. Kubuntu Feisty and Gutsy both connected fine to my router. I am using a 3COM 3CRUSB100075 usb stick. 

This is without encryption. I am still trying to get WPA working. :(

Madsmaddad

---

### Post by kevdog on 2007-11-25
Thanks for the tip about connecting to a hidden SSID.

How are you trying to get WPA working?

---

### Post by madsmaddad on 2007-12-02
Tried via the Gui programs: is it kwifimanager? But it didn't work, then tried installing wpa_supplicant, and it didn't work either, But thanks to your post about the wkihelps, I have learned that supplicant does not support ZD1211 chipset, so am thinking that I am back to square 1. 

Still have encryption enabled on my router, so am doing this from XP, which means I can't get at all the info about what I have done. 

Any pointers appreciated. :(

Peter M.

---

### Post by kevdog on 2007-12-02
Where did you find the info that the wpasupplicant package does not support your chipset???  Im only curious since Ive never seen this before.

---

### Post by madsmaddad on 2007-12-03
[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

does not show the Zydas ZD1211 chipset as being supported. 

I note that page was last updated 2/12/07, so guess that  the information is current.

---

### Post by ender8282 on 2007-12-03
I started another thread but this thread already seems to be dealing with my issues. My problem is that I can connect to secured networks (at least 2 different networks) but I cannot connect to any unsecured networks.  To connect to my secured network I am using:
```

sudo ifconfig eth1 down
sudo iwconfig eth1 essid 'MY_NETWORKS_ESSID' key MY_KEY mode Managed
sudo ifconfig eth1 up
sudo dhclient eth1

```
It works and I have a connection.  
When I try to connect to an unsecured network with:
```

sudo ifconfig eth1 down
sudo iwconfig eth1 mode Managed essid 'NETGEAR'
sudo ifconfig eth1 up
sudo dhclient eth1

```
I get the error:
```

There is already a pid file /var/run/dhclient.pid with pid 7188
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:16:cf:8f:80:98
Sending on   LPF/eth1/00:16:cf:8f:80:98
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
Trying recorded lease 192.168.1.103
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```
I can connect to this network under XP so I know that there is no MAC filtering going on or anything like that.  
Thanks in advance for any advice.

---

### Post by kevdog on 2007-12-03
For your zydas card, what driver are you using??


----


For your unencrypted network, can you post
iwlist scan

Try to connect from the command line leaving out the mode Managed part.

---

### Post by dendy7h on 2007-12-04
Maybe this can help someone.  My WEP key has some special characters in it.  This is the error message I was getting.
```
$ sudo iwconfig eth0 key s:KG"hSRaS{G!#[
sudo iwconfig eth0 key s:KG"hSRaS{Gsudo iwconfig eth0 key s:KG"hSRaS{G[

.....

$sudo dhclient eth0
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I escape the special characters with a \ and it works

```
$sudo iwconfig eth0 key s:KG\"hSRaS\{G\!\#\[

```

Maybe this can help some people who can't get their connections working.

Thanks Kevdog for posting this :guitar:!!!!!

Dendy

---

### Post by kevdog on 2007-12-04
Thanks for the tip -- I thought special characters were out of the question -- I guess they are not!

---

### Post by ender8282 on 2007-12-04
> **kevdog said:**
> For your zydas card, what driver are you using??


----


For your unencrypted network, can you post
iwlist scan

Try to connect from the command line leaving out the mode Managed part.

I don't know about zydas but I am have a Broadcom 1390 wireless chipset.  I am using the windows driver with ndiswrapper.  I followed this ([how to]("http://ubuntuforums.org/showthread.php?t=297092")) to get everything set up.  

At the moment I can't see the unencrypted wireless network but I will try to connect to it without the mode field tomorrow and I will get the iwlist scan as well.  
Thanks

---

### Post by ender8282 on 2007-12-04
The network signal is a little week this morning but when I scan I see it as:
```

          Cell 02 - Address: 00:0F:B5:67:F0:22
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```
Normally the quality is minimum of 30.
I also tried connecting without specifying mode and I get the same 'no dhcp offers' error msg.

---

### Post by kevdog on 2007-12-04
Can you do anything to get the signal stronger such as move closer to the router?

---

### Post by AJWhitewolf on 2007-12-06
I am having a very similar problem to this...  I have no problems connecting to a secured wireless network, but when I attempt to connect to an unsecured network, I receive no DHCPOFFER.

I have a D-Link card and the driver I am using is ath_pci

I just got rid of Network Manager and started doing everything from the command line, following the guide outlined at the beginning of this thread, and I am receiving this same message:

DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

The network does show up in iwlist (would post it, but my comp. has no internet, so I'm posting this at work), and I have used a variety of settings for iwconfig to try and make this work, including: 
iwconfig ath0 mode managed
iwconfig ath0 key off
iwconfig ath0 enc off

And also, of course, setting the essid.

The wireless network I am trying to connect to is the free wireless internet that my apartment complex provides, so I do not have access to their router to change any settings.  However, I have a wireless router at my house, and when I turn on security, I am able to connect to it without problem, but when I make the network unsecured, I receive the errors listed above, so I am positive that it is a common cause that only affects my ability to connect to unsecured networks.

Any help would definitely be appreciated!

---

### Post by kevdog on 2007-12-06
Please type of list the commands you are using attempting to connect to your unencrypted wireless network.

---

### Post by AJWhitewolf on 2007-12-07
sudo ifconfig ath0 down
sudo dhclient -r ath0
sudo ifconfig ath0 up
sudo iwconfig ath0 essid "Pardeeville"
sudo iwconfig ath0 mode managed
sudo dhclient ath0

I have also tried adding:
sudo iwconfig ath0 key off
sudo iwconfig ath0 enc off

I have also manually set the channel and frequency to match that of the network I am trying to connect to, but it makes no difference.

If you need any further information, just ask!

---

### Post by malc_adams on 2007-12-08
kevdog, it took about 3 days of searching and trying other solutions, none of which worked, but I finally found your definitive answer and got my ra61 wireless card working in about 15 minutes. You have my grateful thanks.

---

### Post by Thiago Cesar Vieira on 2007-12-09
Yes, I agree with malc_adams: your post is very helpful and I follow a lot of tricks listed there.

After 1 week using wireless in Ubuntu, suddenly **my connection gets bad**. Sometimes I can use normally, other losing some packages and almost all time with no wireless.

I use wireless normally in **Windows**, so my adapter and the router is working fine. My problem is in Ubuntu configuration. I use dhcp in a D-Link router with WEP 128 bits.

As I said, I follow your procedure to fix bugs in wireless, and I listed above the results. Does anyone have already seen it before or knows the procedure to fix my problem?

**$ lspci**
[I]...
05:06.0 Network controller: Texas Instruments ACX 111 _54Mbps_ Wireless Interface
...[/I]

**$ iwlist wlan0 scanning**
[I]wlan0     Scan completed :
          Cell 01 - Address: 00:1B:11:FE:48:6E
                    ESSID:"[MY_ESSID]"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/100  Signal level=21/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s[/I]

**$ cat /etc/network/interfaces**
[I]auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-key s:[MY-KEY]
wireless-essid [MY_ESSID]

auto wlan0[/I]

**$ ifconfig -a**
[I]eth0 ...
lo   ...

wlan0     Link encap:Ethernet  HWaddr 00:13:46:34:D3:85  
          inet addr:192.168.0.151  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:fe34:d385/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3092 errors:17 dropped:0 overruns:0 frame:0
          TX packets:2802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3025914 (2.8 MB)  TX bytes:561166 (548.0 KB)
          Interrupt:16 Base address:0x8000[/I]

**$ iwconfig wlan0**
[I]wlan0     IEEE 802.11b+/g+  ESSID:"[MY_ESSID]"  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:11:FE:48:6E   
          _Bit Rate:54 Mb/s_   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=39/100  Signal level=14/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/I]


**$ lshw -C network**
[I]  *-network:0
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 6
       bus info: pci@0000:05:06.0
       logical name: wlan0
       version: 00
       serial: 00:13:46:34:d3:85
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci ip=192.168.0.151 latency=32 module=acx multicast=yes wireless=IEEE 802.11b+/g+
  *-network:1
...[/I]


**$ sudo dhclient wlan0**
[I]Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:13:46:34:d3:85
Sending on   LPF/wlan0/00:13:46:34:d3:85
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.0.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.151 -- renewal in 579250 seconds.[/I]


After some minutes it starts to **lose packages** when I ping in router (192.168.0.1)... rate of successful packages 100% goes to 80%, 60%, 40%...

My **log files** listed bellow start logging problems...
[I]/var/log/kern.log
/var/log/messages
/var/log/syslog[/I]

[I]Dec  9 11:51:52 kernel: [ 1035.974387] acx: got IV_ICV_Failure (crypto) IRQ(s)
Dec  9 11:52:21 kernel: [ 1064.191699] wlan0: tx error 0x10, buf 05! (MSDU lifetime timeout? - try changing 'iwconfig retry lifetime XXX')
Dec  9 12:00:52 kernel: [ 1575.379976] NETDEV WATCHDOG: wlan0: transmit timed out
Dec  9 12:00:52 kernel: [ 1575.379984] wlan0: FAILED to free any of the many full tx buffers. Switching to emergency freeing. Please report!
Dec  9 12:00:52 kernel: [ 1575.380015] wlan0: tx timeout!
Dec  9 12:00:52 kernel: [ 1575.380118] wlan0: recalibrating radio
...
Dec  9 12:05:52 kernel: [ 1875.164877] wlan0: got disassoc frame with reason 4 (due to inactivity)
A cada 2segundos printa essa mensagem:
Dec  9 12:06:29 kernel: [ 1912.366504] acx: BUG: no free txdesc left[/I]


**$ iwconfig wlan0**
[I]wlan0     IEEE 802.11b+/g+  ESSID:"[MY_ESSID]"  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          _Bit Rate:1 Mb/s_   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=43/100  Signal level=20/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0[/I]


**$ sudo dhclient wlan0**
[I]There is already a pid file /var/run/dhclient.pid with pid 5944
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:13:46:34:d3:85
Sending on   LPF/wlan0/00:13:46:34:d3:85
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
Trying recorded lease 192.168.0.151
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.[/I]


**$ sudo ifconfig wlan0 down**
Stops to log errors.

**$ sudo dhclient -r wlan0**
[I]There is already a pid file /var/run/dhclient.pid with pid 6505
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:13:46:34:d3:85
Sending on   LPF/wlan0/00:13:46:34:d3:85
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.[/I]


**$sudo ifconfig wlan0 up**
Starts to log again:
[I]Dec  9 12:18:33 kernel: [ 2635.423531] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec  9 12:19:10 kernel: [ 2672.586353] acx: BUG: no free txdesc left[/I]

[B]$ sudo iwconfig wlan0 essid "[MY_ESSID]"
$ sudo iwconfig wlan0 key s:[MY_KEY]
$ sudo iwconfig wlan0 mode Managed
$ sudo dhclient wlan0[/B]

[I]After last command
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:13:46:34:d3:85
Sending on   LPF/wlan0/00:13:46:34:d3:85
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/I]


**My /var/log/syslog prints**
[I]Dec  9 12:33:22 dhclient: No DHCPOFFERS received.
Dec  9 12:33:22 dhclient: No working leases in persistent database - sleeping.
Dec  9 12:33:22 avahi-autoipd(wlan0)[6945]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Dec  9 12:33:22 avahi-autoipd(wlan0)[6945]: Successfully called chroot().
Dec  9 12:33:22 avahi-autoipd(wlan0)[6945]: Successfully dropped root privileges.
Dec  9 12:33:22 avahi-autoipd(wlan0)[6945]: Starting with address 169.254.7.33
Dec  9 12:33:23 kernel: [ 3524.796812] acx: BUG: no free txdesc left
Dec  9 12:33:26 kernel: [ 3527.294933] acx: BUG: no free txdesc left
Dec  9 12:33:27 avahi-autoipd(wlan0)[6945]: Callout BIND, address 169.254.7.33 on interface wlan0
Dec  9 12:33:27 avahi-daemon[5278]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.7.33.
Dec  9 12:33:27 avahi-daemon[5278]: New relevant interface wlan0.IPv4 for mDNS.
Dec  9 12:33:27 avahi-daemon[5278]: Registering new address record for 169.254.7.33 on wlan0.IPv4.
Dec  9 12:33:30 kernel: [ 3531.841374] acx: BUG: no free txdesc left
Dec  9 12:33:31 avahi-autoipd(wlan0)[6945]: Successfully claimed IP address 169.254.7.33
Dec  9 12:33:32 kernel: [ 3533.338381] acx: BUG: no free txdesc left
Dec  9 12:33:34 kernel: [ 3535.836501] acx: BUG: no free txdesc left
Dec  9 12:33:37 kernel: [ 3538.334619] acx: BUG: no free txdesc left
Dec  9 12:33:39 kernel: [ 3540.832737] acx: BUG: no free txdesc left
Dec  9 12:33:41 avahi-autoipd(wlan0)[6945]: SIOCSIFFLAGS failed: Permission denied
Dec  9 12:33:41 avahi-autoipd(wlan0)[6945]: Callout STOP, address 169.254.7.33 on interface wlan0
Dec  9 12:33:41 avahi-daemon[5278]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec  9 12:33:41 avahi-daemon[5278]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.7.33.
Dec  9 12:33:41 avahi-daemon[5278]: Withdrawing address record for 169.254.7.33 on wlan0.
Dec  9 12:33:41 avahi-daemon[5278]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.7.33.
Dec  9 12:33:41 dhclient: receive_packet failed on wlan0: Network is down
Dec  9 12:33:41 avahi-daemon[5278]: New relevant interface wlan0.IPv4 for mDNS.
Dec  9 12:33:41 avahi-daemon[5278]: Registering new address record for 169.254.7.33 on wlan0.IPv4.
Dec  9 12:33:41 dhclient: receive_packet failed on wlan0: Network is down
Dec  9 12:33:41 avahi-daemon[5278]: Withdrawing address record for 169.254.7.33 on wlan0.
Dec  9 12:33:41 avahi-daemon[5278]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.7.33.
Dec  9 12:33:41 avahi-daemon[5278]: Interface wlan0.IPv4 no longer relevant for mDNS.[/I]


After I **restart **my machine...
[I]Dec  9 12:44:55 NetworkManager: <info>  Updating allowed wireless network lists. 
Dec  9 12:44:55 NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

Dec  9 12:50:16 kernel: [  420.557064] wlan0: rx: 8 DUPs in 21 packets received in 10 secs
Dec  9 12:50:35 kernel: [  439.245000] wlan0: tx error 0x20, buf 02! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
Dec  9 12:50:35 kernel: [  439.245012] wlan0: tx error 0x20, buf 03! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
Dec  9 12:50:35 kernel: [  439.245023] wlan0: tx error 0x20, buf 04! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
Dec  9 12:50:39 kernel: [  443.182437] wlan0: several excessive Tx retry errors occurred, attempting to recalibrate radio. Radio drift might be caused by increasing card temperature, please check the card before it's too late!
Dec  9 12:50:39 kernel: [  443.182450] wlan0: tx error 0x20, buf 05! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
Dec  9 12:50:39 kernel: [  443.182458] wlan0: tx error 0x20, buf 06! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
Dec  9 12:50:39 kernel: [  443.182468] wlan0: tx error 0x20, buf 07! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
Dec  9 12:50:39 kernel: [  443.182489] wlan0: recalibrating radio
Dec  9 12:50:39 kernel: [  443.229739] wlan0: successfully recalibrated radio[/I]



If you you have some advice, I'd like to "hear". Any words for you is much for me to understand Ubuntu better.

---

### Post by madsmaddad on 2007-12-09
> **kevdog said:**
> For your zydas card, what driver are you using??


----


For your unencrypted network, can you post
iwlist scan

Try to connect from the command line leaving out the mode Managed part.

took awhile, But I have it.  XP works with not encryption so I have to keep booting back to post. I have tried 'unsetting' everything to get back to Unencrypted operation in Kubuntu, but it's not happy. Here's  the gen:
peterm@peterm-Kdesktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:58:4B:C3:23
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xe400

eth1      Link encap:Ethernet  HWaddr 00:14:7C:66:B7:97
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:462 (462.0 b)

eth1:avah Link encap:Ethernet  HWaddr 00:14:7C:66:B7:97
          inet addr:169.254.8.14  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:352 (352.0 b)  TX bytes:352 (352.0 b)

peterm@peterm-Kdesktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"zd1211"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

peterm@peterm-Kdesktop:~$

peterm@peterm-Kdesktop:~$
from dmesg:
[   41.677158] zd1211rw 4-3:1.0: firmware version 4605
[   41.719113] zd1211rw 4-3:1.0: zd1211 chip 6891:a727 v4721 high 00-14-7c RF295
9_RF pa0 g----
[   41.721657] zd1211rw 4-3:1.0: eth1
[   41.721682] usbcore: registered new interface driver zd1211rw
....
[   86.446150] NET: Registered protocol family 10
[   86.449854] lo: Disabled Privacy Extensions
[   86.451412] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   86.451468] ADDRCONF(NETDEV_UP): eth1: link is not ready        ??not noticed this before..


peterm@peterm-Kdesktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:6E:CA:89:2C
                    ESSID:"bmth_wireless"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=100/100  Signal level=94/100
                    Extra: Last beacon: 80ms ago


peterm@peterm-Kdesktop://etc/network$ cat interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth0 inet static
address 192.168.1.12
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1
iface eth1 inet dhcp


Thanks for any help. I'll keep playing to try and get it working 'open'. Would it help to uninstall wpa_supplicant, even though it is not configured?

Peter

---

### Post by kevdog on 2007-12-09
Im not sure what to make about this line:

[ 86.451468] ADDRCONF(NETDEV_UP): eth1: link is not ready ??not noticed this before..

Try connecting from the command line for eth1.  The instructions are in my signature.  Try just a regular unencrypted connection first.

---

### Post by caricc on 2007-12-10
Kevdog - you helped me out a while back on a wireless connection problem. I was hoping you could do teh same again. I am now setting up a Dell Latitude 600 with Ubuntu 7.10. Hard drive was empty do it's a fresh install. i have a listing of the following: 
lshw -C network
route
ifconfig
iwlist scan.

posting list:
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:c9:0f:c2
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 firmware=5705-v3.16 ip=192.168.1.64 latency=32 mingnt=64 module=tg3 multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 04
       serial: 00:0c:f1:4e:fd:4e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=32 maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         home            0.0.0.0         UG    100    0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth1

eth0      Link encap:Ethernet  HWaddr 00:0F:1F:C9:0F:C2  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fec9:fc2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2419 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2822985 (2.6 MB)  TX bytes:294129 (287.2 KB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:0C:F1:4E:FD:4E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:1 dropped:1 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:395 (395.0 b)  TX bytes:4500 (4.3 KB)
          Interrupt:5 Base address:0x6000 Memory:fafef000-fafeffff 

eth1:avah Link encap:Ethernet  HWaddr 00:0C:F1:4E:FD:4E  
          inet addr:169.254.8.83  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:5 Base address:0x6000 Memory:fafef000-fafeffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 olo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1A:04:F6:68:91
                    ESSID:"CARICK"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality:93  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 28ms ago
          Cell 02 - Address: 00:19:E4:14:63:41
                    ESSID:"2WIRE569"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:35  Signal level:0  Noise level:0
                    Extra: Last beacon: 24ms ago
verruns:0 carrier:0

I am trying to use WICD as the network manager. I am not happhappy with nm that came with ubuntu. thanks in advance. 


          collisions:0 txqueuelen:0 
          RX bytes:280 (280.0 b)  TX bytes:280 (280.0 b)

---

### Post by kevdog on 2007-12-10
What commands have you typed at the command line to attempt to connect?

---

### Post by caricc on 2007-12-10
I have followed your instructions in the help file you have posted here. Still will not connect.

---

### Post by caricc on 2007-12-10
I have an update: I was able to use a static ip address and now able to get online. But I would still like to have dhcp working and not have to use a static ip. Any suggestions?
I am using wicd as my network manager.  
DHCP would allow me to have this laptop to move on to other networks. 

any help. thanks in advance.

---

### Post by madsmaddad on 2007-12-10
> **kevdog said:**
> Im not sure what to make about this line:

[ 86.451468] ADDRCONF(NETDEV_UP): eth1: link is not ready ??not noticed this before..

Try connecting from the command line for eth1.  The instructions are in my signature.  Try just a regular unencrypted connection first.

Once I uninstalled wpa_supplicant, the unencrypted connection worked. This is coming over an unencrypted wireless link. 

config details as so:
 
eth1      Link encap:Ethernet  HWaddr 00:14:7C:66:B7:97
          inet addr:192.168.1.5  Bcast:192.168.1.7  Mask:255.255.255.248
          inet6 addr: fe80::214:7cff:fe66:b797/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7552 errors:184 dropped:455 overruns:0 frame:175
          TX packets:7674 errors:51 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7780642 (7.4 MB)  TX bytes:1334843 (1.2 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

peterm@peterm-Kdesktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:6E:CA:89:2C
                    ESSID:"bmth_wireless"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=100/100  Signal level=47/100
                    Extra: Last beacon: 80ms ago


Note I have restricted speed to 802.11b as it gives better range through walls than g, and with a 512Kb/s broadband I don't need faster Wireless. Also Channel 11 to be aways from others in neighborhood. 

Almost tempted to re-install wpa_supplicant and the kwlan gui manager for it, and see if that works. I didn't use kwlan last time.

---

### Post by aldo_m on 2007-12-23
ok i need help  kevdog . man after the last update it was somthing todo with the kernal. but after restarting i lost my wg511t card i only have one light flashing. soi use the command in the beging of this thread and i came up with somthing i didnt find with anyone withthe same problem.

root@Nsa:~# iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"denise"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:18:39:42:6F:3F   
          Bit Rate=24 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=65/100  Signal level=-66 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@Nsa:~# lshw -C network
  *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 03
       serial: 00:90:4b:44:53:c7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic ip=192.168.1.109 latency=64 link=yes module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 10
       serial: 00:02:3f:69:80:34
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0 maxlatency=28 mingnt=10

its showing my network card *-network UNCLAIMED. please helpme i need to finsh cracking this wep.
i will give you the biggest hug ever kev and lick your toe jam.:lolflag:

---

### Post by PhrozenPhoenix on 2007-12-27
I think Madsmaddad found a way to do this already, but for anyone getting the "No DHCP Offers" message try:

sudo iwconfig [interface] key open

I found that when looking up the parameters of iwconfig on google.. it led me to: [http://gd4.tuwien.ac.at/.vhost/linuxcommand.org/man_pages/iwconfig8.html](http://gd4.tuwien.ac.at/.vhost/linuxcommand.org/man_pages/iwconfig8.html)


This is only my second day as a linx user (running Xubunto wirelessly atm), so I dont know if that helps any.. but I'm thinking the reason so many people are getting that error message is because their WEP settings on their router dont have "shared keys" but "open keys," if that makes any sense.. hope this helps.

Oh, and thanks a lot for the tutorial Kevdog... i've been going through a lot of troubles installing Xubuntu (install cd not burning, updates not working, loose video card making my system freeze, etc.) but its nice to finally have a working wireless system to play around with!

---

### Post by kevdog on 2007-12-28
PhrozenPhoenix

Updated the thread instructions with your suggestion.  I dont really use WEP a whole bunch.  The iwconfig documentation gives a poor explanation of when to use or not use the open command.  Hopefully people will try this command if they are receiving problems when trying to make a WEP connection

---

### Post by Tombo5150 on 2007-12-29
Allrighty! First off, Kevdog, awesome tutorial man as you know it is greatly appreciated. First, I had problems with the Hex key (WEP encryption). After following your advice and reading the man iwconfig, I saw that they put the key in XXXX-XXXX-XXXX-XXXX and since my key is a ten character key i thought to put it in as XXXX-XXXX-XX and it worked! So now I know how to get the wireless to work.......however, is all of this just a temporary fix untill you reboot your computer? The problem, is that this is my parents computer and I just installed Gutsy only a few days ago on it. I'm showing them an alternative to windows which has been giving them problems. These steps would be easy for me and I would certainly not have a problem entering them everytime I needed wireless, but it would be much easier if it would just stay after I got the wireless to work. Is there someway of making this permanent?

---

### Post by kevdog on 2007-12-29
Again as stated in the tutorial, this method isnt really for everyday use, rather than troubleshooting or just testing to see if the wireless network card works.  As far as everyday use, are you planning on using network manager??   Also is this with a laptop or a desktop you are working with -- what Im getting at here is there any situation with this computer that you might need network roaming?  If you do not need roaming then within the /etc/network/interfaces file you would put (for WEP)

auto <inteface>
iface <interface> inet dhcp
wireless-essid <essid>
wireless-key <key>
wireless-mode Managed

Thats about it.  You probably have to do a
sudo /etc/init.d/networking restart

This should (cross your fingers) bring the network connection up on boot.

---

### Post by Tombo5150 on 2007-12-30
Bring the connection up in the network manager? Because it hasn't even been giving me an option for wireless. It's for my parents desktop, so it won't need to roam. I'll try what you told me then i'll get back to you. Thanks again!

---

### Post by Kadou on 2007-12-30
Hey, I've been having some trouble with connecting with this method. After I set up everything (hex WEP key included) I'm still getting that same error at the last command:

```

No DHCPOFFERS received.
 No working leases in persistent database - sleeping.
```

I'm grateful that I can at least see what the problem is, but I still have no idea how to solve it. Help would be appreciated!

---

### Post by kevdog on 2007-12-30
I cant help you with this -- it could be a configuration issue, a reception issue, or something else.  Try first with unencryption to verify that everything is setup properly (minus the WEP line).

---

### Post by Tombo5150 on 2008-01-02
> **kevdog said:**
> Again as stated in the tutorial, this method isnt really for everyday use, rather than troubleshooting or just testing to see if the wireless network card works.  As far as everyday use, are you planning on using network manager??   Also is this with a laptop or a desktop you are working with -- what Im getting at here is there any situation with this computer that you might need network roaming?  If you do not need roaming then within the /etc/network/interfaces file you would put (for WEP)

auto <inteface>
iface <interface> inet dhcp
wireless-essid <essid>
wireless-key <key>
wireless-mode Managed

Thats about it.  You probably have to do a
sudo /etc/init.d/networking restart

This should (cross your fingers) bring the network connection up on boot.


I did this but it won't let me save the file. It says that the file is read only. I opened it in gedit, is there some way I should do this?

---

### Post by rustybronco on 2008-01-02
> **Tombo5150 said:**
> I did this but it won't let me save the file. It says that the file is read only. I opened it in gedit, is there some way I should do this?sudo gedit...

---

### Post by madsmaddad on 2008-01-03
from message 117. 

Have re-installed wpa_supplicant and kwlan. 

set my router to wpa2/TKIP. 

Having worked through a bunch of configuration stuff, I am confused. 

Do I edit /etc/network/interfaces with the WPA config stuff, 

or

/etc/wpa_supplicant.conf? 

And how do I know which wpa driver is appropriate for my wireless hardware? Is there a table anywhere?

Kwlan seems to pick up the profile if there isa  wpa_supplicant.conf file, but will not allow me to edit the encryption parameters to set them up. Note I started kwlan from the terminal as 'sudo kwlan'.

Am I just confusing myself?

Thanks for any guidance (again).

---

### Post by ...Max... on 2008-01-03
Trying on this thread in hopes it'll get noticed sooner. I won't copy the bulk of the previos message from [http://ubuntuforums.org/showthread.php?p=4064688#post4064688](http://ubuntuforums.org/showthread.php?p=4064688#post4064688)

In short, what can I look for when dhclient simply fails to get any offers and quits? No other relevant error messages anywhere in the log. I've tested this with the driver that does work properly in dual booted XP so it's gotta be a problem somewhere in the wireless stack/config rather than in the driver/hardware/access point. Is there any way to enable verbose logging from the wireless stack (whatever it consists of)? Note that all iw* commands SEEM to work -- as in no error messages and iwlist/iwconfig reflect the changes. Except, the essid is never set to what I specified -- iwconfig always shows it as "off/any".

---

### Post by kevdog on 2008-01-03
Can you post an example?

---

### Post by ...Max... on 2008-01-03
Could you be more specific? The lspci listing is in the linked post. What would help -- protocol from the terminal window? Log excerpts? There's precious little infornation in either :( Something else? I need some ideas in which direction to dig...

---

### Post by hulleye on 2008-01-05
To those having the "No DHCP Offers Received" problem. I was getting this message repeatedly no matter what I tried. I just randomly decided to experiment with the settings on my router and discovered that just switching from a pure 802.11g network to a mixed 802.11b/g network solved my issues instantly. Felt quite silly in that instant

Am using the Orinoco driver for my wireless card. Might be worth a try to play around with your router settings.

Btw KevDog, hidden SSID seems to work fine for me.

---

### Post by kevdog on 2008-01-05
Hidden ESSID is very sporadic, it works for some but not for others.  Not sure why -- likely related to whatever driver you are using.  Maybe someone should come up with a poll in a new thread to find what drivers work with hidden ESSID and what drivers do not?  Could also by a router specific issue -- but I dont that!

---

### Post by madsmaddad on 2008-01-06
Still having problems, but making progress.  And yes, I am using a hidden ESSID, WPA2 and TKIP on a 3COM USB stick.  

Have configured wpa_supplicant.conf for my setup by thinking about comments earlier in this thread. 

file wpa_supplicant.conf:

ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="bmth_wireless"
	psk=13953c483e5d42339779f01317e83931b12e530f6ee5416144da6185a89b499e
	key_mgmt=WPA-PSK
	proto=RSN
	pairwise=TKIP
}

When I run through the list of commands this is what I get:
peterm@peterm-Kdesktop:~$ sudo ifconfig eth1 down
[sudo] password for peterm:
peterm@peterm-Kdesktop:~$ sudo dhclient -r eth1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:14:7c:66:b7:97
Sending on   LPF/eth1/00:14:7c:66:b7:97
Sending on   Socket/fallback
peterm@peterm-Kdesktop:~$ sudo wpa_supplicant -w -Dwext -ieth1 -c/etc/wpa_supplicant.conf
Trying to associate with 00:18:6e:ca:89:2c (SSID='bmth_wireless' freq=2462 MHz)
ioctl[SIOCSIWFREQ]: Operation not permitted
Association request to the driver failed
Associated with 00:18:6e:ca:89:2c
WPA: Key negotiation completed with 00:18:6e:ca:89:2c [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:18:6e:ca:89:2c completed (auth) [id=0 id     _str=]

Hung here so CTRL-C

CTRL-EVENT-TERMINATING - signal 2 received

The MAC address 3 lines back is the router, So that's what I mean by progress. 

Any Ideas why it hangs at this point? Initially the association attempt fails, but then it happens. 

When I put the Group parameter in the .conf file, the system did not like that. 

I am wondering if for some reason it is having trouble at this point getting an IP address, as I am using DHCP. :confused:

---

### Post by kevdog on 2008-01-06
broadcast the essid.

---

### Post by Mboo on 2008-01-07
I was able to connect to my wirless using the instruciton below, but how do I get those setting to hold? After a restart, I have to do it all over again.

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
****Additional Comand that may be needed  -- sudo iwconfig <interface> key open  <<<----See note below
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

---

### Post by madsmaddad on 2008-01-07
> **kevdog said:**
> broadcast the essid.

When I checked, I was. 

So, I don't know for how long I have been, but I am broadcasting. I am trying to keep reasonable documentation on what  am doing, but I missed that. 

Looks like you are trying to help multiple people  on the same thread - Gets confusing?  But I am also interested in the next guys solution. 

Peter M.:confused:

---

### Post by kevdog on 2008-01-07
You just put the commands in a shell script -- make the file executable, and then add the file to your list of startup programs at boot.

---

### Post by mabovo on 2008-01-07
Hello ! May I ask permission to enter in this thread ?

I have a MacBook 2,1 with artheros AR5418 wireless card.
With today updates I finally  got this wireless card working but only with Security disable.

My router is a DI-624 and is possible to configure security from WEP-WPA-WPA2-WPA-AUTO

The problem is :  I am newbee in wireless networking and don't know how to configure security in my home network.  Can You help me ?

Thanks.

---

### Post by Mboo on 2008-01-07
> **kevdog said:**
> You just put the commands in a shell script -- make the file executable, and then add the file to your list of startup programs at boot.

I'm still pretty new to Linux.  I don't know how to make a shell script, make is executable or make it load on startup.

---

### Post by mabovo on 2008-01-07
I have this result from:

mabovo@macbook:~$ sudo wpa_supplicant -w -D wext -i ath0 -c/ etc/wpa_supplicant.conf -dd
Initializing interface 'ath0' conf '/' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/' -> '/'
Reading configuration file '/'
Initializing interface (2) 'ath0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:1b:63:05:81:11
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface ath0
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=12
Ignore event for foreign ifindex 3
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 231 bytes of scan results (1 BSSes)
Scan results: 1
No suitable AP found.
Setting scan request: 0 sec 0 usec
No enabled networks - do not scan
State: SCANNING -> INACTIVE

P.S. Have no idea what it means. :-)

---

### Post by mabovo on 2008-01-07
Second try:
[HTML]
mabovo@macbook:~$ sudo su
root@macbook:/home/mabovo# ifconfig ath0 down
root@macbook:/home/mabovo# ifconfig wifi0 down
root@macbook:/home/mabovo# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:11 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:2  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@macbook:/home/mabovo# ifconfig ath0 up
root@macbook:/home/mabovo# modprobe wlan_scan_sta
root@macbook:/home/mabovo# wlanconfig ath0 list scan
SSID            BSSID              CHAN RATE  S:N   INT CAPS
bovo            00:15:e9:79:52:9e   11   54M 26:0   100 EPSs WPA
root@macbook:/home/mabovo# iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:15:E9:79:52:9E
                    ESSID:"bovo"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-70 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

root@macbook:/home/mabovo# iwlist ath0 key tchecoslovaquia148
iwlist: command `keys' needs fewer arguments (max 0)
root@macbook:/home/mabovo# iwlist ath0 key <tchecoslovaquia148>
bash: erro de sintaxe próximo a símbolo inesperado `newline'
root@macbook:/home/mabovo# ifconfig ath0 down
root@macbook:/home/mabovo# dhclient -r ath0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:1b:63:05:81:11
Sending on   LPF/ath0/00:1b:63:05:81:11
Sending on   Socket/fallback
root@macbook:/home/mabovo# ifconfig ath0 up
root@macbook:/home/mabovo# iwconfig ath0 essid "bovo"
root@macbook:/home/mabovo# iwconfig ath0 key open "tchecoslovaquia148"
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device ath0 ; Invalid argument.
root@macbook:/home/mabovo# iwconfig ath0 key open <tchecoslovaquia148>
bash: erro de sintaxe próximo a símbolo inesperado `newline'
root@macbook:/home/mabovo# iwconfig ath0 key open tchecoslovaquia148
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device ath0 ; Invalid argument.
root@macbook:/home/mabovo# iwconfig ath0 key tchecoslovaquia148
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "tchecoslovaquia148".
root@macbook:/home/mabovo# iwconfig ath0 key "tchecoslovaquia148"
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "tchecoslovaquia148".
root@macbook:/home/mabovo# iwconfig ath0 key ASCII_KEY "tchecoslovaquia148"
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "ASCII_KEY".
root@macbook:/home/mabovo# iwconfig ath0 key s:ASCII_KEY "tchecoslovaquia148"
iwconfig: unknown command "tchecoslovaquia148"
root@macbook:/home/mabovo# iwconfig ath0 key s:ASCII_KEY tchecoslovaquia148
iwconfig: unknown command "tchecoslovaquia148"
root@macbook:/home/mabovo# iwconfig ath0 key s:ASCII_KEY <tchecoslovaquia148>
bash: erro de sintaxe próximo a símbolo inesperado `newline'
root@macbook:/home/mabovo# 

[/HTML]

---

### Post by mabovo on 2008-01-07
From Madwifi HowTo I got this:

[HTML]
mabovo@macbook:~$ iwconfig ath0 ap any
Error for wireless request "Set AP Address" (8B14) :
    SET failed on device ath0 ; Operation not permitted.
mabovo@macbook:~$ iwconfig ath0 ap auto
Error for wireless request "Set AP Address" (8B14) :
    SET failed on device ath0 ; Operation not permitted.
mabovo@macbook:~$ sudo iwconfig ath0 ap auto
[sudo] password for mabovo: 
mabovo@macbook:~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:1b:63:05:81:11
Sending on   LPF/ath0/00:1b:63:05:81:11
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
mabovo@macbook:~$ sudo dhcpcd ath0
sudo: dhcpcd: command not found
mabovo@macbook:~$ ifconfig ath0 192.168.0.187 netmask 255.255.255.0 up
SIOCSIFADDR: Permissão negada
SIOCSIFFLAGS: Permissão negada
SIOCSIFNETMASK: Permissão negada
SIOCSIFFLAGS: Permissão negada
mabovo@macbook:~$ sudo ifconfig ath0 192.168.0.187 netmask 255.255.255.0 up
mabovo@macbook:~$ ping bbc.co.uk
PING bbc.co.uk (212.58.224.131) 56(84) bytes of data.
64 bytes from rdirwww-vip.thdo.bbc.co.uk (212.58.224.131): icmp_seq=1 ttl=118 time=250 ms
64 bytes from rdirwww-vip.thdo.bbc.co.uk (212.58.224.131): icmp_seq=2 ttl=118 time=223 ms
64 bytes from rdirwww-vip.thdo.bbc.co.uk (212.58.224.131): icmp_seq=3 ttl=118 time=196 ms
64 bytes from rdirwww-vip.thdo.bbc.co.uk (212.58.224.131): icmp_seq=4 ttl=118 time=215 ms
64 bytes from rdirwww-vip.thdo.bbc.co.uk (212.58.224.131): icmp_seq=5 ttl=118 time=209 ms
64 bytes from rdirwww-vip.thdo.bbc.co.uk (212.58.224.131): icmp_seq=6 ttl=118 time=225 ms

--- bbc.co.uk ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5010ms
rtt min/avg/max/mdev = 196.348/220.030/250.027/16.463 ms
mabovo@macbook:~$ 


[/HTML]

---

### Post by kevdog on 2008-01-07
Those commands need sudo in front of them

sudo iwconfig etc.

---

### Post by peevee07 on 2008-01-08
I have found this "how to" most helpful in the past. I have just replaced my wireless router and now I find that the command line statements don't get me through to connection. I'm using 7.04 and I end up with No DHCPOFFERS. I can't get beyond that. Kwifimanager and wifi assistant don't help. So I'm looking for help.

---

### Post by madsmaddad on 2008-01-08
On mine, I have just run through the commands and the output of wpa_suuplicant with the -dd (extensive debug) parameter gives the following as the last few lines:

WPA: Key negotiation completed with 00:18:6e:ca:89:2c [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:18:6e:ca:89:2c completed (auth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
EAPOL: startWhen --> 0

At this point nothing happens. It doesn't complete. 

Any idea what EAPOL is looking for? 

Thanks for any guidance.
:confused:

---

### Post by kevdog on 2008-01-08
When you run it with the -dd command and it seems to stop -- pop open another terminal window, and then continue typing the next series of commands.  See if that works for you -- again this is only for testing purposes.

---

### Post by MyrddinWyllt on 2008-01-10
Hello, I am trying to get my wireless working on a computer running ubuntu 7.10 server. I have a Linksys WMP54GS wireless card, which uses a broadcom 4306 chipset. I opened a thread about it on the beginner forum, and they recommended that I ask here.

The original thread is here:
[http://ubuntuforums.org/showthread.php?t=662363](http://ubuntuforums.org/showthread.php?t=662363)

Hopefully you guys can help, I'm about out of ideas..

---

### Post by kevdog on 2008-01-10
MyrddinWyllt

See following thread:

[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

---

### Post by MyrddinWyllt on 2008-01-10
> **kevdog said:**
> MyrddinWyllt

See following thread:

[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

Another vote for NDISWrapper, then, I guess my current approach is totally wrong :)

Thanks!

---

### Post by Mike1949 on 2008-01-10
Thanks for the post.  I was able to get my wifi working, only now I don't know how to make the fix permanent.  When I reboot, I have to run the commands again.  I could always create a script and put it in rc.local, but I expect there's a better way.  What do you recommend?

---

### Post by kevdog on 2008-01-10
Either script or wicd.

---

### Post by Maricaibo on 2008-01-11
I cannot get network settings to hold after reboot. I put the following script in my /etc/init.d folder:

sudo ifconfig ra0 down
sudo dhclient -r ra0
sudo iwconfig ra0 essid 2WIRE596
sudo iwconfig ra0 key 1234567890
sudo iwconfig ra0 mode Managed
sudo ifconfig ra0 up
sudo dhclient ra0

But I must still run these commands manuallt to get my wireless working.

The script is owned by root  and I CHMOD +x on the script.

What in blazes is happening? the Wired connection camoes back up at reboot just fine...:confused:

---

### Post by kevdog on 2008-01-12
Does the script actually run??  Can you check the boot log or dmesg (system log) to see if the script ran and is it giving any errors?  Is it supposed to go in rc.local instead?  Also disable the wired connection at boot adding to your script

sudo ifconfig eth0 down

---

### Post by Maricaibo on 2008-01-12
SOLVED!

I'd read an earlier post on putting a startup shell script in the init.d folder.

When the commands are in the** etc/rc.local** file (set as an executable) viola!

THANKS!!!!!!!

Getting wireless working is a...challenge.

---

### Post by kevdog on 2008-01-12
Can you post your /etc/rc.local file?

I shall add this to the guide!

---

### Post by kilometers on 2008-01-12
kevdog,

Thanks for this thread it is of much help.  I am setting up my roommate's laptop with ubuntu 7.10 an trying to get his wireless card working.  It is a D-Link DWL-650 RevP with a Prosm 3.0 chipset.  Using Synaptic I installed some drivers that recognize the card.

The iwconfig displays two wireless devices; wifi0 and wlan0, but ifconfig only shows the ethernet and lo.

I started with your manual configuration and all went smoothly until the essid command

'sudo iwconfig wlan0 essid "mynetwork" 
Error for wireless request "Set ESSID" (8B1A):
     SET failed on device wlan0 ; Invalid argument.'

Any ideas of what to do?  I have a hunch that I need to edit some network configuration files.

thnx again,

kilometers

---

### Post by kevdog on 2008-01-12
Can you post the results of 

lshw -C network
iwlist scan
ifconfig

Thanks

---

### Post by Jay Jay on 2008-01-13
Kevdog,

Just wanted to say thanks, your guide has worked brilliantly for me. Before I read your post I had to boot into Windows at times because Network Manager & Wireless Assistant could see the router I wanted to use,* but could not connect to it*. This would annoy me to no end... The same problem often occurred under Kubuntu 7.04 too and my workaround for that was to save my preferred ESSID within the interfaces file. 

On a side note, does this mean there is a bug in the GUI connectivity software seeing as there are no issues when going through the Command Line?

Thanks again,

Jay

---

### Post by kevdog on 2008-01-13
Jay Jay

I dont know why the GUI managers do not work all the time.  The closest one Ive found to emulate the command line is WICD.  I dont know how NM works.

Do you have a bigger picture of your avatar?? I cant make it out!

---

### Post by Jay Jay on 2008-01-13
lol how's this?

[http://starwars.wikia.com/wiki/Image:Cody%3B_Order_66.jpg](http://starwars.wikia.com/wiki/Image:Cody%3B_Order_66.jpg)

:)

---

### Post by kevdog on 2008-01-13
Ahhhh, that's a lot better!

---

### Post by madsmaddad on 2008-01-13
Me back again: Trying to get this 3CRUSB10075 working with WPA2. 

Following on from what you have done so far with me, and from some thing I found on a fedoa forum about getting it working: I changed my wpa_supplicant.conf file to read:

ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="bmth_wireless"
        psk=13953c483e5d42339779f01317e83931b12e530f6ee5416144da6185a89b499e
        key_mgmt=WPA-PSK
        proto= WPA RSN
        pairwise=TKIP CCMP
}

and ran through the list of commands. As you suggested when the first terminal session seemed to hang after processing the wpa_supplicant command,I opened another window and did the rest of the commands, and here I am updating this online from Kubuntu 7.10. It seemed to need the WPA and CCMP parameters adding. 

Now I need to fix it so it works every time:) 

Peter M.

---

### Post by kevdog on 2008-01-13
Can you post the exact line you enter with the wpa_supplicant command??

I see the wpa_supplicant.conf file, I just want you to post the command

---

### Post by kilometers on 2008-01-13
kevdog,

sorry for the long reply time.  here is the output for the commands you requested me to run.

**lshw -C network**
  *-network
       description: DWL-650 Wireless PC Card RevP
       product: ISL37101P-10
       vendor: D-Link
       physical id: 0
       version: A3
       slot: Socket 0
       resources: irq:3
  *-network
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 83
       serial: 00:e0:b8:57:79:a1
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=hostap driverversion=0.4.4-kernel firmware=0.0.0 multicast=yes wireless=IEEE 802.11-DS

**iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning : Network is down

wlan0     Interface doesn't support scanning : Network is down

**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:E0:B8:57:79:A1
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Thanks for the help.

-kilometers

---

### Post by madsmaddad on 2008-01-13
The exact commands were:

sudo ifconfig eth1 down
sudo dhclient -r eth1
sudo wpa_supplicant -w -Dwext -ieth1 -c/etc/wpa_supplicant.conf

then to new terminal session:

sudo ifconfig eth1 up
sudo iwconfig eth1 mode managed
sudo dhclient eth1

I gave you the  wpa_supplicant.conf file in a previous post. 

I am now trying to figure out what to put in the Interfaces file to get it to work automatically on boot. 

Peter M.

---

### Post by kevdog on 2008-01-13
so what happens if you bring the interface up

sudo ifconfig wlan0 up

and then do a 
iwlist scan

---

### Post by kilometers on 2008-01-13
kevdog,

**sudo ifconfig wlan0 up**

followed by 

**iwlist scan**

gave the same out put as above

a **dmesg** command gave the following output:
[ 9121.948000] pccard: PCMCIA card inserted into slot 0
[ 9121.948000] pcmcia: registering new device pcmcia0.0
[ 9121.948000] hostap_cs: setting Vcc=33 (constant)
[ 9121.948000] Checking CFTABLE_ENTRY 0x01 (default 0x01)
[ 9121.948000] IO window settings: cfg->io.nwin=1 dflt.io.nwin=1
[ 9121.948000] io->flags = 0x0047, io.base=0x0000, len=128
[ 9121.948000] hostap_cs: Registered netdevice wifi0
[ 9121.988000] hostap_cs: index 0x01: , irq 3, io 0x3080-0x30ff
[ 9122.488000] hostap_cs: assuming no Primary image in flash - card initialization not completed
[ 9122.488000] wifi0: test Genesis mode with HCR 0x1f
[ 9122.488000] prism2_pccard_cor_sreset: original COR 41
[ 9122.492000] prism2_pccard_genesis_sreset: original COR 41
[ 9122.520000] Readback test failed, HCR 0x1f write 00 e1 a1 ff read 00 ce a1 ce
[ 9122.520000] wifi0: test Genesis mode with HCR 0x0f
[ 9122.520000] prism2_pccard_cor_sreset: original COR 41
[ 9122.524000] prism2_pccard_genesis_sreset: original COR 41
[ 9122.556000] Readback test succeeded, HCR 0x0f
[ 9122.556000] prism2_pccard_genesis_sreset: original COR 41
[ 9122.584000] wifi0: registered netdevice wlan0
[ 9122.724000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[ 9122.724000] wlan0: could not set interface UP - no PRI f/w

does that shed any light on the problem?

-kilometers

---

### Post by kevdog on 2008-01-13
madsmaddad

Substitute the following command

sudo wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf

Notice the B flag starts the wpa_supplicant daemon in the background.  You can confirm this if you do a 

sudo ps -ef | grep wpa

Does the process show up as running?

You dont put this in the /etc/network/interfaces file to get it to load at boot, you add it to

/etc/rc.local

See about 10-20 post back -- this was addressed and solved by another user!

---

### Post by kevdog on 2008-01-13
kilo

I see in your dmesg log:

[ 9122.724000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[ 9122.724000] wlan0: could not set interface UP - no PRI f/w

I have no idea what that means.  I dont have really any experience with the hostap driver either.  I think its more than likely a bad or incorrect driver you have.  You may want to search the forums for your particular card or use the term hostap.  Sometimes those cards are difficult to configure correctly -- meaning the driver setup is sometimes a pain.

---

### Post by Maricaibo on 2008-01-14
Here's how I got my wireless card to startup at boot time.

After ensuring your wireless card is working (device is up and can get an IP address from your router), add the following text to your** /etc/rc.local** file using **your** equipment names inside the brackets. I used this command in a Terminal (shell) window:

**sudo gedit /etc/rc.local**

This opens up the file in the **gedit** utility and allows you to make changes and save the file

ifconfig <wired network connection device> down
ifconfig <wireless network connection device> down
dhclient -r <wireless device>
iwconfig <wireless device> essid <router name> 
iwconfig <wireless device> key  <WEP key in ascii>
iwconfig <wireless device> mode Managed
ifconfig <wireless device> up
dhclient <wireless device>

Be sure this text goes into the** /etc/rc.local **file BEFORE the line reading "exit 0".

Save and close the **/etc/rc.local **file.

Open up a Terminal window (the shell) and type in:

**sudo CHMOD +x /etc/rc.local**

This command turns the rc.local file into an executable that will run at startup. Here's what my /etc/rc.local file now looks like. Your device names will be different:

#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ifconfig eth0 down
ifconfig ra0 down
dhclient -r ra0
iwconfig ra0 essid 2WIRE596
iwconfig ra0 key 1234567890
iwconfig ra0 mode Managed
ifconfig ra0 up
dhclient ra0

exit 0


NOTE: The first line in the rc.local file downs your wired connection, so if for some reason you need the wired connection back just open up a Terminal window (shell) and type:

sudo <wired connection> up
sudo dhclient <wired connection>

NOTE! kevdog correctly pointed out the use of 'sudo' in the rc.local file was redundant, as the file is owned and executed by ROOT at bootup anyway- thanks!
Many thanks to all here who posted helpful tips, hints and suggestions. I could NOT have done this otherwise. Good luck!

---

### Post by kilometers on 2008-01-14
Thanks for the help kevdog.  I know this thread will be useful when I get the drivers configured correctly.

---

### Post by Kenniej on 2008-01-16
Thank you SO MUCH for this tutorial , i've been working all day to get a EDIMAX old usb adapter to get to work.

Kudo's to you !!

Grtz,
Kenniej

---

### Post by dub_u on 2008-01-16
> **kevdog said:**
> Thanks for the tip -- I thought special characters were out of the question -- I guess they are not!

First, thanks for this "Howto", I finally managed to get my wireless connection to work with WEP on my Ubuntu machine (worked on two windows though...and worked non-secure on Ubuntu).
Just wanted to add that my key includes only one special character (a "&" at the end) and that works as long as I write 
sudo ifconfig wlan0 key s:"ABCDEFG1234&" but not s:ABCDEFG1234&

---

### Post by Pointswest on 2008-01-17
I would like to thank you so much for your tutorials on wireless networking.  I have been trying to get this to work for months.  Yours is the only instructions that seem to work.  I have installed ndiswrapper from my 7.10 cd  and followed your instructions for installation.  I can see that ndis 1.45 is installed from the lshw -C network command.  By using the network manager and manual config I can see my signal and if roaming is unchecked the bar graph comes up with a signal strength, but I am unable to connect to the internet.

My router is using wep encryption.  I have tried to use the commands in this post to add the WEP but when I type "ifconfig wlan0 down" I receive an error about permission denied.  Can you tell me where I have gone wrong?  Have also tried same command using "sudo iconfig wlan0 down" with no results.

Thanks again for the useful tips. this issue of wireless connection is getting so many posts it's becoming hard to sort it all out.

Pointswest

---

### Post by kevdog on 2008-01-17
Good to see another guy from Colorado using Ubuntu

You need to preface the commands with sudo
You also need to make sure your wireless interface is referred to as wlan0 rather than eth1 or some other name.  The best way to tell this in most cases is by looking at the results of lshw -C network, however in some cases this could be misleading (for example when using the madwifi drivers).

---

### Post by Mor Hedroom on 2008-01-17
Hi, kevdog -

Thanks so much for the tie and patience you put into your work in this forum!  I've got an interesting/irritating problem, and I'm wondering if you have any suggestions.

First off, I've been successfully using my current setup, with the ability to switch freely between wired/wireless.  Some time in the last couple days, I've lost the ability to connect wirelessly to my router.  To my knowledge, the only changes made to my system were Ubuntu updates.  The system is always under my direct supervision, and is not likely the victim of tampering.

My setup:
Computer: HP ze4420us
OS:  Ubuntu (Gutsy) 7.10
Wireless: Airlink101 Cardbus - Ralink chipset
Driver:  rt61pci
Interface name:  wmaster0

It turns out that the reason I turned to your guide is I can see access points, including my own, but I cannot connect to them.  Thinking it might be something going on with Network Manager, I tried the steps you outline in the beginning of this thread:
from lshw -C network:
```
*-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:a4:e2:f4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 ip=192.168.2.3 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes
  *-network
       description: Wireless interface
       product: RT2600 802.11 MIMO
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:14:a5:87:69:86
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g

```

I think this shows that my driver is actually installed, and the wireless card is in fact detected.  The interface name is wmaster0 and the driver is rt61pci.

I then proceed with your instructions for WEP connections:

```
sudo ifconfig wmaster0 down

```

where I am asked for my sudo password, and I give it, and am returned to the prompt.  Assumably, the command has been executed.

Then:
```
sudo dhclient -r wmaster0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback

```

Strange, but I thought, "OK, I'll go ahead."

```
sudo ifconfig wmaster0 up
SIOCSIFFLAGS: Operation not supported
```

After which point I'm not sure whether it makes sense to proceed, but I try:

```
sudo iwconfig wmaster0 essid "BioBoy"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wmaster0 ; Operation not supported.
```

While I'm certainly new at Ubuntu, I'm pretty certain that continuing with your supplied commands will not produce meaningful results at this point.  Do you have any suggestions as to how I may proceed to get my wireless back?

Thanks in advance.
-Mor Hedroom

---

### Post by Pointswest on 2008-01-17
I am still stuck with this  command "ifconfig wlan 0 down". If I type the command as shown it says permission denied.  If I add sudo the computer just blinks and goes back to the desktop prompt line.  I didn't know if the brackets around wlan0 were part of the command or not.  Tried both ways, neither worked.

Using the lshw -C network command, it shows my adapter on wlan0.  I noticed using the dmesg  command that one line in the scan said "Failure registering capabilities with primary security module".  Also the ndiswrapper -l command shows "network disabled".  The command d gksu gedit /etc/network/interfaces only shows:  auto lo and iface lo net, no menion of wlan0.  I have included a screenshot with the results of some of these commands for reference.

Any help with this is appreciated, I have been trying this for a  long  time  without success.  Last night was the first time I got the adapter to even turn on. Thanks

Pointswest

---

### Post by kevdog on 2008-01-17
Mor

can you post ifconfig?

---

### Post by kevdog on 2008-01-17
points


Howcome you have two entries for ndiswrapper?  this cant be right

---

### Post by Pointswest on 2008-01-17
kevdog

I have been trying for many months to get this wireless working and have read many posts and typed lots of commands trying to get this to work.  I wouldn't be suprised if I somehow  I got this on the machine twice.  At one point last week I managed to get a ndiswrapper 1.49 to the desktop but didn't know to use the commands to install it from there.  I finally gave up trying to install this and followed your instructions to install ndis. from the 7.10CD.  A few of the commands in your tutorial gave me messages that said already installed so I just went to the next step.  The version I thought I installed with the CD was 1.45 and is the version shown in the wireless interface section.  The version 1.49  was not installed unless it happened by accident because it was on the desktop.  

One thing I noticed with the ifconfig command was that I not only have a wlan0 but a wlano.ava.  No clue about this.  I am just trying to teach myself to use Linux so all I can do at this point is copy commands from the forum, not knowing why or how to use them.  I thought I was so close last night when the bar graph showed up after clicking the monitor icon but then I was not able to connect to any web sites.

I thought this might be because I didn't use the command lines to set the  WEP.  I only used the network manager to set the hex key.  As you can tell I am really new at this and don't know if I can even explain the problems correctly. 

Thanks 

Pointswest

---

### Post by kevdog on 2008-01-17
For one, just try reloading the ndiswrapper driver:

sudo modprobe -r ndiswrapper
sudo rm -R /etc/ndiswrapper/*

Reload the driver into ndiswrapper (I dont know where the driver is so you are going to have to change to the directory where the driver is located:

sudo ndiswrapper -i <driver.inf file>
sudo modprobe ndiswrapper

Check your work with:

ndiswrapper -l
dmesg | more

To see if the driver is correct

---

### Post by Pointswest on 2008-01-18
Kevdog

I have run the commands "sudo modprobe -r ndiswrapper" and" sudo rm -R/etc/ndiswrapper/*.  I dont think anything has happened from these commands.  I have included screenshots from these commands.

The ndiswrapper -l shows my driver rtl8187b (Airlink 101 w/realtek 8187b chipset) as loaded with ndiswrapper 1.45 which was on the 7.10CD.

Just a new note to add to this.  I followed your instructions for setting wep and they worked this time.  Now I can connect wirelessly.  I am thrilled about this.  Although I set my hex key with the command line, when I surf, a window tells me I am using an unencrypted connection.  Have I missed something here?  I cant thank you enough for your patience with me, I was beginning to think you were the only one in North America using Ubuntu wirelessly.

Pointswest

---

### Post by kevdog on 2008-01-18
Your screenshot tells me nothing other than you are using ndiswrapper.  What screen tells you that you are using an unencrypted connection?  When connecting via command line, there shouldnt be a popup, gui, or other desktop method like an icon that is going to tell you anything (that is definitely a negative with using the command line since there isnt a good feedback system). 

Sometimes
iwlist scan will show you the encryption type.

Are you trying to use network manager or a GUI?

---

### Post by Pointswest on 2008-01-18
Kevdog

As the old song goes "The Thrill is Gone".  After connecting last night  for a short while,when the computer shut down it would not reconnect on reboot.  

When it started working I had just finished running the commands for the WEP encriptions.  I also used the  monitor icon on the toolbar to set my hex key as well as going to network manager and unchecking roaming, entering my ESSID and hex key, and setting configuration to dhcp, then rechecking enable roaming mode.

I think the message screens showed up when going from one ebay site to another.  I dont see how my computer could connect through my router if it was not encr ypted the same as the router .  iwlist scan shows my ESSID "pointswest. also says the encryption key is on.

After  loosing the connection I tried modifing the network  interface files.  The only entries were: auto lo and iface lo inet loopback.  I added auto eth0,iface eth0 inet dhcp.auto wlan0, and iface wlan0 inet dhcp to the list.  I haven't  modified the etc/iftab file as shown on the tutorial because my interface is wlan0.

Today when I look at ifconfig there is no wlan0 listed, yesterday the same command showed wlan0 and wlan0.ava
Thanks again

Pointswest

---

### Post by kevdog on 2008-01-18
I dont use network manager -- well I do on one computer -- but the whole purpose of this guide was not to use network manager b/c its oftentimes just plain buggy.  If you can see your network with iwlist, then the driver is likely set up appropriately.

You need to complete your connection by using the commands on the command line as stated on page 1 of the tutorial -- forget network manager or any gui for now.  And if things are not working initially, turn off WEP temporarily.  Boil it down to the simplest common denominator, and then increase complexity with encryption.

---

### Post by madsmaddad on 2008-01-19
Kevdog, Thanks for all your help. 

As You know, Gutsy picked up this device on install. It uses the ZD1211 chipset. 

I now have it working with WPA2, and ESSID Broadcast. The rc.local file and the wpa_supplicant.conf file are listed here:

/etc$ cat rc.local

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sudo ifconfig eth1 down
sudo dhclient -r eth1
sudo wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf
sudo ifconfig eth1 up
sudo iwconfig eth1 mode managed
sudo dhclient eth1

exit 0

/etc$ cat wpa_supplicant.conf

ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="bmth_wireless"
        psk=13953c483e5d42339779f01317e83931b12e530f6ee5416144da6185a89b499e
        key_mgmt=WPA-PSK
        proto= WPA RSN
        pairwise=TKIP CCMP
}
    
As noted on another users comments, I am using an 8 character encryption key. 

I did try turning off ESSID Broadcast on my router, but then couldn't connect.. There is a parameter mentioned in the How-to by Weiman01 (thread 318539) to set this capability. 

Not sure if I needed to put all the 'sudo's in the rc.local file, but did it anyway.

Overall, though we have to admit that this is a workaround. I would still like to see a solution as per message 126 in this thread and the weiman01 thread where the parameters are placed in the Interfaces file. 

One thing that I have not determined is where the GUI configuration applications look/store the data. 

Thanks again.

---

### Post by kevdog on 2008-01-19
A lot of chipsets within linux can not or have problems connecting to access points with hidden essids.  This is a known problem and unfortunately I cant do anything about it.

As far as the settings in the /etc/network/interfaces file, that is for network manager and other programs and have nothing to do with this method.  This method is a simpler alternative.  Although definitely not as sexy, this method seems to default the ultimate fallback method.  I would suggest making another post asking for help with network manager or settings within the interfaces file.  You are not the only one to have problem with the other approach.


Yes the sudo statements within the rc.local file are redundant -- you dont need the sudo statement.

---

### Post by yknivag on 2008-01-21
Firstly, kevdog, thank you for such an excellent guide.  I've now got my wireless working perfectly at home.

However, using the access point at work is a different story.  there are a couple of differences.  My home WIFI is WPA protected with a PSK and TKIP encryption and uses static IPs.  The one at work is WEP and supports DHCP.  I know that the work one is functioning and that DHCP is working as my colleagues can connect OK from their Windoze machines.

Here is what I tried (following the OP as best I could) and the results.  

ifconfig
```
gavin@knuckle:/etc/init.d$ sudo ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:0A:81:19:46  
          inet6 addr: fe80::211:aff:fe81:1946/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:164590 (160.7 KB)

ath0:avah Link encap:Ethernet  HWaddr 00:11:0A:81:19:46  
          inet addr:169.254.3.***  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:08:02:E6:9D:02  
          inet addr:10.0.0.20  Bcast:10.255.255.255  Mask:255.0.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27578 (26.9 KB)  TX bytes:27578 (26.9 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-0A-81-19-46-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60496 errors:0 dropped:0 overruns:0 frame:18237
          TX packets:1715 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:5454899 (5.2 MB)  TX bytes:225734 (220.4 KB)
          Interrupt:11 
```
iwconfig
```
gavin@knuckle:/etc/init.d$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Livebox-****"  Nickname:""
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:14:A4:7D:**:**   
          Bit Rate:36 Mb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-45 dBm  Noise level=-98 dBm
          Rx invalid nwid:2731  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.
```
iwlist scan
```
gavin@knuckle:/etc/init.d$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 02 - Address: 00:14:A4:7D:**:**
                    ESSID:"Livebox-****"
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Quality=52/70  Signal level=-43 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

irda0     Interface doesn't support scanning.
```
lshw -C network
```
gavin@knuckle:/etc/init.d$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wifi0
       version: 01
       serial: 00:11:0a:81:19:46
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network:1 DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5705M_2 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 03
       serial: 00:08:02:e6:9d:02
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=half firmware=5705-v3.14 ip=10.0.0.20 latency=64 link=no mingnt=64 module=tg3 multicast=yes port=twisted pair
```
Commands
```
gavin@knuckle:/etc/init.d$ sudo ifconfig ath0 down
gavin@knuckle:/etc/init.d$ sudo iwconfig ath0 essid "Livebox-****"
gavin@knuckle:/etc/init.d$ sudo iwconfig ath0 key "**************************"
gavin@knuckle:/etc/init.d$ sudo iwconfig ath0 key open (tried with and without this)
gavin@knuckle:/etc/init.d$ sudo ifconfig ath0 up
```
Result
```
gavin@knuckle:/etc/init.d$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:0a:81:19:46
Sending on   LPF/ath0/00:11:0a:81:19:46
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I hope someone can shed some light on things. I just can't understand why it works at home and not at work.

---

### Post by Ber P on 2008-01-22
I finaly got my wifi to work with WEP. But I have to retype the key every time I log in :(.

Then I found this guide, and got it all to work from the command line, made the rc.local, and - it dosen't run when I boot!! I can execute it manualy, and then it works, so the file is apparently ok. 
When executed manualy, however, I have to use administrator rights. So mayby it's a user rights issue? Isn't rc.local executed with administrator rights?

---

### Post by kevdog on 2008-01-22
I believe rc.local has administrator rights -- or at least it should.

You can check by doing the following:

ls -la /etc/rc.local

---

### Post by Ber P on 2008-01-23
```
:~$ ls -la /etc/rc.local
-rwxr-xr-x 1 root root 481 2008-01-22 21:21 /etc/rc.local

```

Should I uninstall NetworkManager? Is it because it forces other settings after rc.local is done?

---

### Post by Pointswest on 2008-01-23
After connecting a few nights ago, then losing the connection upon shutdown  I found if I re-entered the  start up commands at the console I can always connect with no problem.  I have left this connection on for over 24 hours without the connection dropping.

I have changed the  rc.local file as noted above to try to get the adapter to turn on at boot, but still get no connection.  I do not have network manager installed so I don't think this is the problem.  I am using WEP encryption.

After closer inspection of my rc.local file I found I had made a keystroke error when entering the start-up commands, upon correction the wireless adapter now starts every time at boot without the addition of of the sleep 40 command.  For those of you who are new at using the terminal like me, make sure the commands are written as posted to avoid problems.

Thanks

Pointswest

---

### Post by kevdog on 2008-01-23
You may want to put a sleep 40 statement at the top of the rc.local file (or at least the networking section) to give time for other services to start.  Im not sure why it doesnt work for you since others have reported success with this method.  I guess you could always fall back on a script that you could run either from command line, or put an icon on the desktop that would link to the executable.

---

### Post by Ber P on 2008-01-24
I do use a script in the moment, but would realy like to have it working automaticly, since the computer is used by my kids and wife too. 

I'll try the sleep command  when i come home. Might just work, because yesterday it actually connected by itself one time (out of ~20)??!?!?

---

### Post by LPA on 2008-01-26
Thanks, but ... 
This is all well and good if you are a real Linux techie and understand command-line lingo, but I'm not. I want my Ubuntu to work simply, and from the GUI - for real dummies. Any good idea?

Richard

---

### Post by kevdog on 2008-01-26
LPA

Please see another post.  I think the title of this post was explicitly clear -- Connecting from the Command Line.  Your complaint was kind of like going to a post explaining how to make mp3's, and then complaining that you wanted to make ogg files.

---

### Post by walterhisownself on 2008-01-26
kevdog,

I attempted the commands you suggest at the beginning of this thread and here are my results. I am using an Atheros wireless card AR5212 and running (newly installed) Gutsy 7.10 and my wireless router has security turned off.
 The wireless router is working properly because I am able to connect to it with another laptop which was upgraded to Gutsy from 7.04 and does not use an Atheros wireless card, but a Cisco Aironet.

Here's my terminal session with the commands you suggested:

[FONT="Courier New"]lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:11:25:45:31:3b
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A latency=64 mingnt=255 module=e1000 multicast=yes
  *-network:1
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wifi0
       version: 01
       serial: 00:05:4e:4d:a7:7b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

 sudo ifconfig wifi0 down
 sudo dhclient -r wifi0
There is already a pid file /var/run/dhclient.pid with pid 5623
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Sending on   Socket/fallback

 sudo ifconfig wifi0 up
 sudo iwconfig wifi0 essid "collards"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wifi0 ; Invalid argument.

sudo iwconfig wifi0 mode Managed
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wifi0 ; Invalid argument.

sudo dhclient wifi0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Sending on   Socket/fallback
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/FONT]

Any thoughts?

iwconfig gives the following results:

[FONT="Courier New"]iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"collards"  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-83 dBm  Noise level=-83 dBm
          Rx invalid nwid:195831  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/FONT]

Thanks for any help you can provide.

---

### Post by kevdog on 2008-01-27
For atheros based cards with the madwifi driver, you need to use the interface name ath0 rather than wifi0 since the madwifi driver creates virtual interface points to connect to the actual driver.

---

### Post by walterhisownself on 2008-01-27
kevdog,

Thanks for your prompt reply. I'll give those commands a try with "ath0" rather than "wifi0" and let you know what happens.

---

### Post by walterhisownself on 2008-01-27
kevdog,

Here's what I get when using "ath0" for my atheros wireless card with the madwifi driver:

[FONT="Courier New"]sudo ifconfig ath0 down
sudo dhclient -r ath0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:05:4e:4d:a7:7b
Sending on   LPF/ath0/00:05:4e:4d:a7:7b
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
walaka@afagddu:~$ sudo ifconfig ath0 up
walaka@afagddu:~$ sudo iwconfig ath0 essid "collards"
walaka@afagddu:~$ sudo iwconfig ath0 mode Managed
walaka@afagddu:~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:05:4e:4d:a7:7b
Sending on   LPF/ath0/00:05:4e:4d:a7:7b
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/FONT]

Any thoughts on this? It almost seems that it times out before being issued a DHCP address. I say this because when I boot up with an ethernet cable unplugged, and successfully logon, the small icon for Network Manager attempts to join any unsecured wireless network (because I have it set to roaming mode). One of the two "balls" representing the wireless network connection with Network Manager as it attempts to connect turns green. The other stays dark blue and the connection never successfully connects. This is the reason I am attempting to connect via the command line using the commands you suggest in this thread.

I'm not sure where to go from here. At times it will connect with Network Manager, but it's really sporatic.

Thanks in advance for any pointers you can provide.

---

### Post by kevdog on 2008-01-27
Can you see your network at least with 

iwlist scan

and what is the reported signal strength?

---

### Post by walterhisownself on 2008-01-29
I can see my network with "iwlist scan" or "iwlist ath0 scanning"


Here's the output:

[FONT="Courier New"]
Cell 02 - Address: 02:19:5B:C7:8F:97
                    ESSID:"collards"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-49 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s[/FONT]

I can see other networks and actually the laptop connected automatically when I unplugged it from ethernet to another unsecured network because I have it in roaming mode. I saw the Network Manager icon in the upper right panel attempt to connect to any unsecured network and it was successful in joining that network.

---

### Post by kevdog on 2008-01-30
So it sounds like the problem is solved?

---

### Post by akhyarsi on 2008-01-30
Dear all,

I have problem with my WLI-U2-KG54-AI wireless LAN USB adapter.
Gutsy uses rt2500usb driver for the device. I can see network signals, its strength after login, but the internet is not working. 

I do not know what to do.
Is the rt2500usb really compatible with my device? why the driver does not appear when I type "lshw -C network" in the terminal?

I attach my screenshot below.

Any idea? thanks in advance.

---

### Post by sofamensch on 2008-01-30
Weird thing happening here when trying the static IP address. I really need it :-(

Ok so whats happening? Assume i already did all the commands for iwconfig (WEP Network), it works to get me connected, but not the part with the static ip.

```

sudo dhclient ath0 -r
sudo ifconfig ath0 192.168.0.254 netmask 255.255.255.0 up
sudo route add default gw 192.168.0.1
sudo dhclient ath0
>There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0f:b5:8a:ce:8e
Sending on   LPF/ath0/00:0f:b5:8a:ce:8e
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPOFFER from 192.168.0.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.155 -- renewal in 244411 seconds.
alex@desktop:~$ 

```

Shortly said, i tell him the wanted IP Address, but he still acquires an IP vom the DHCP server. Any idea? I already tried to rm dhclient.pid but no difference.

---

### Post by Hillwalker on 2008-01-30
Kevdog

I didn't post a query - all my problems were already well documented by others. I followed the advice you gave them and this is my first on-line posting with my first Ubuntu- driven machine. Many thanks for originating and sustaining the thread. Thanks too to Maricaibo for his boot script - that worked first time. For the record my card is Belkin F5D7000de with an RTL8185 chipset. I had trouble with the NDIS wrapper on the 7.10 installation disk and upgraded to the latest version (your how to came in pretty handy there too). I used the WIN98 driver set downloaded from the RealTek website. And despite having an installed and fully operational card, lspci still shows it as an unknown device. Wierd!

One bit of advice I followed was to switch to a fixed IP. That seems to have helped me along the way. However, the recipes (several of them) directed me to ~/etc/resolv.conf to remove old dhcp server assignments. Resolve.conf doesn't seem to exist in 7.10 although. When I ran dhclient this induced a couple of error messages which, I found to my great pleasure can be ignored.

Thanks again and good wishes to all other followers of the path of wisdom and truth mapped out in all that has gone before

HW

---

