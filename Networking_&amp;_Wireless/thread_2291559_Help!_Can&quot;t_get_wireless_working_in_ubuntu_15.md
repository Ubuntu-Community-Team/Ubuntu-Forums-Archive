---
title: "Help! Can&quot;t get wireless working in ubuntu 15.04"
date: 2015-08-21
forum: Networking &amp; Wireless
---

### Post by trey9 on 2015-08-21
Ok so im using ubuntu 15.04 and i cant get my wireless card working and ive already re installed ubuntu i need help getting my wifi working im using a usb wifi piece right now to get online

---

### Post by Bucky Ball on 2015-08-21
*Thread moved to **Networking & Wireless**.*

Welcome. Can't give support based on the information you've provided. Please open a terminal and cut/paste this in:

```
sudo lshw -C network
```

Hit return, type your password in (it will be invisible) and hit enter. Copy and paste the output back here between code tags (see last link in my signature). All of it. Thanks.

PS: The above command will give us basic info. If you're feeling lucky, please try the wireless info script in my signature which will give comprehensive details. May or not be needed later. :)

---

### Post by trey9 on 2015-08-21
```

*-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:17 memory:c0300000-c0303fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1
       logical name: wlan0
       serial: e0:46:9a:b4:ba:34
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ath9k_htc driverversion=3.19.0-26-generic firmware=1.3 ip=192.168.1.109 link=yes multicast=yes wireless=IEEE 802.11bgn

```

---

### Post by trey9 on 2015-08-21
do you want the ethernet info too??

---

### Post by Hadaka on 2015-08-21
Hi ,please open a terminal ctrl/alt/t then
while connected to the internet COPY
and paste these commands,one at a time.
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
remove the usb wifi,remove the wired connection, boot
test wireless

---

### Post by trey9 on 2015-08-21
```

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by trey9 on 2015-08-21
got this for sudo apt-get update (above)

---

### Post by Hadaka on 2015-08-21
if possible please run these from a working wired connection,
if not..use what you have..please COPY and paste..
```
 sudo rm -rf /var/lib/apt/lists/lock
sudo apt-get update
sudo dpkg -r bcmwl-kernel-source
```
then do..
#dont worry if the first command says file not found..continue on..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```

*Dont forget to remove the usb wifi to test..

---

### Post by ajgreeny on 2015-08-21
That error is common if you are trying to use the terminal to manage packages or update but another application to do the same activity is still open, eg software-centre (or synaptic, if you have that installed).

Make sure any other package-management apps are closed and try those commands again.

If there is still a problem you can make sure all applications are closed by rebooting, though that should not be necessary.

---

### Post by trey9 on 2015-08-21
for 
sudo dpkg -r bcmwl-kernel-source i got:
```

sudo dpkg -r bcmwl-kernel-source
dpkg: error: dpkg status database is locked by another process

```

---

### Post by Hadaka on 2015-08-21
Hi, try this..
```
sudo dpkg --configure -a
sudo apt-get autoremove

```
if it fails i need the /var/ path..what is being locked
thanks.

---

### Post by trey9 on 2015-08-21
i got this from sudo dpkg --configure -a:
```

Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu2) ...
Removing old bcmwl-6.30.223.248+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.248+bdcom
Kernel:  3.19.0-26-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.............

DKMS: uninstall completed.

------------------------------
Deleting module version: 6.30.223.248+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
Building only for 3.19.0-26-generic
Building for architecture i686
Building initial module for 3.19.0-26-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-26-generic/updates/dkms/

depmod........

DKMS: install completed.


```

---

### Post by Hadaka on 2015-08-21
ok,good please copy and paste ..
*if you get an error with the second command..not to worry
continue on with the next command
```

sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```

---

### Post by trey9 on 2015-08-21
should i open a new terminal? it didnt do anything for the first code
```

DKMS: install completed.
sudo apt-get update

```

---

### Post by Hadaka on 2015-08-21
this has output even if its up to date
```
sudo apt-get update
```
please COPY and paste these commands to help avoid error.
so..boot the computer...bring up a terminal ...and repeat the
commands in post #13
thanks

---

### Post by trey9 on 2015-08-21
sudo apt-get update:
```

 Failed to fetch cdrom://Ubuntu 15.04 _Vivid Vervet_ - Release i386 (20150422)/dists/vivid/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 15.04 _Vivid Vervet_ - Release i386 (20150422)/dists/vivid/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

``` 
what should i do

---

### Post by Bucky Ball on 2015-08-21
Have you got a CD in the slot? Go to 'Software and Sources' and untick it or take it out then update again.

---

### Post by trey9 on 2015-08-21
i used a usb start up disk creator to make a usb one so no

---

### Post by Hadaka on 2015-08-21
so....are you trying to update an os on a usb? are you not putting
ubuntu on your computers hard drive,?? something is amiss here
please explain.

---

### Post by trey9 on 2015-08-21
i installed ubuntu through a usb start up disk

---

### Post by ajgreeny on 2015-08-21
Just go to software-sources from the dash (or menu depending on the DE you are using), then unselect the cdrom at the top of the list in "Other software" tab.

---

### Post by trey9 on 2015-08-21
i switched off the cdrom but no luck

---

### Post by Hadaka on 2015-08-21
Hi, what do you mean by "no luck" ?
no luck what.?.please provide print out so that we may
see what needs to be done. and did you boot? if not
please do. and then try..
```
sudo apt-get update
```
thanks

---

### Post by trey9 on 2015-08-21
i switched off cd rom wireless not working still but i will boot and do that

---

### Post by trey9 on 2015-08-21
i did sudo apt-get update wifi not on i turned on the propietary driver but it doesnt work

---

### Post by Hadaka on 2015-08-21
ok..thats the problem ..the proprietary driver is the wrong
driver..that is the broadcom-kernel-source driver .wl
you need the b43 driver for the type of wireless card you have
so let's try this again..providing the updates ran. please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
if this runs ok..remove the usb wifi..boot and test

---

### Post by trey9 on 2015-08-21
sudo modeprobe b43 hasnt ended yet in my terminal

---

### Post by trey9 on 2015-08-21
can i still boot ??

---

### Post by Hadaka on 2015-08-21
yes boot..but..you need to delete the proprietary driver.
connect to the internet and do..

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43

```
this time..post back the output from each command..thanks.

---

### Post by trey9 on 2015-08-22
```

sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for trey: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-15 linux-headers-3.19.0-15-generic
  linux-headers-generic linux-image-3.19.0-15-generic
  linux-image-extra-3.19.0-15-generic linux-image-generic ndiswrapper-common
  ndiswrapper-dkms ndiswrapper-utils-1.9 thermald
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 59 not upgraded.
trey@trey-MX6448:~$ 

```

---

### Post by trey9 on 2015-08-22
```
 sudo apt-get install firmware-b43-installer
[sudo] password for trey: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-15 linux-headers-3.19.0-15-generic
  linux-headers-generic linux-image-3.19.0-15-generic
  linux-image-extra-3.19.0-15-generic linux-image-generic ndiswrapper-common
  ndiswrapper-dkms ndiswrapper-utils-1.9 thermald
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 59 not upgraded.
trey@trey-MX6448:~$ 

```

---

### Post by trey9 on 2015-08-22
```

sudo modprobe b43
[sudo] password for trey: 
trey@trey-MX6448:~$ 

```

---

### Post by Hadaka on 2015-08-22
ok..now please do..
```
sudo apt-get autoremove
```
do these,,one at a time..if you get a warning or error ignore it
and continue to the next command untill all 4 are entered
```
sudo modprobe -rfv ndiswrapper
sudo apt-get remove --purge ndisgtk ndiswrapper*
sudo rm /etc/modprobe.d/ndis*
sudo rm -r /etc/ndiswrapper/*

```
then do
```
sudo modprobe b43
```
remove your usb wifi, boot 
you should now have wireless

*Do NOT activate the proprietary driver..additional drivers..it is incorrect for your card

---

### Post by trey9 on 2015-08-22
no wireless still i got error messages on all 4 codes too

---

### Post by trey9 on 2015-08-22
would it help to see my driver info?

---

### Post by Hadaka on 2015-08-22
what would help if possible is to connect your computer to the ethernet cable instead of a usb wireless.
but..if thats all you have,then use that. Yes i would like to see the wireless info, problem is you are using
it with wireless usb. anyway,,,read careflly and run the "wireless info script"
from here [URL="http://ubuntuforums.org/showthread.php?t=370108&"]http://ubuntuforums.org/showthread.php?t=370108&
[/URL]the wireless info script will be in your home directory..copy and past it here
thanks

---

### Post by trey9 on 2015-08-22
```

########## wireless info START ##########

Report from: 22 Aug 2015 02:16 EDT -0400

Booted last: 22 Aug 2015 02:12 EDT -0400

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-27-generic #29-Ubuntu SMP Fri Aug 14 21:43:05 UTC 2015 i686 athlon i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
    Subsystem: Gateway, Inc. Device [107b:0367]
    Kernel driver in use: sky2

05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0465]
    Kernel driver in use: wl

##### lsusb #############################

Bus 001 Device 002: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k_htc              65536  0 
ath9k_common           32768  1 ath9k_htc
ath9k_hw              442368  2 ath9k_common,ath9k_htc
ath                    24576  3 ath9k_common,ath9k_htc,ath9k_hw
mac80211              626688  1 ath9k_htc
wl                   6152192  1 
cfg80211              462848  5 wl,ath,ath9k_common,mac80211,ath9k_htc

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2708 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1833 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3137073 (3.1 MB)  TX bytes:304323 (304.3 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"SpiderBee"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'SpiderBee' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:57   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    400    0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       523     1  0 02:13 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         NETGEAR WNA
GENERAL.PRODUCT:                        WNA1100
GENERAL.DRIVER:                         ath9k_htc
GENERAL.DRIVER-VERSION:                 3.19.0-27-generic
GENERAL.FIRMWARE-VERSION:               1.3
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:13.2/usb1/1-1/1-1:1.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     SpiderBee
GENERAL.CON-UUID:                       5442a4cd-f071-4b51-af41-9830a55d7326
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     54 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5442a4cd-f071-4b51-af41-9830a55d7326 | SpiderBee
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 192.168.1.109/24, gw = 192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             68.105.28.11
IP4.DNS[2]:                             68.105.29.11
IP4.DNS[3]:                             68.105.28.12
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        network_number = 192.168.1.0
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_time_offset = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_host_name = 1
DHCP4.OPTION[8]:                        host_name = trey-MX6448
DHCP4.OPTION[9]:                        expiry = 1440310440
DHCP4.OPTION[10]:                       requested_wpad = 1
DHCP4.OPTION[11]:                       requested_domain_name = 1
DHCP4.OPTION[12]:                       next_server = 192.168.1.1
DHCP4.OPTION[13]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_subnet_mask = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       ip_address = 192.168.1.109
DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[19]:                       requested_static_routes = 1
DHCP4.OPTION[20]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[21]:                       dhcp_lease_time = 86400
DHCP4.OPTION[22]:                       domain_name_servers = 68.105.28.11 68.105.29.11 68.105.28.12
DHCP4.OPTION[23]:                       requested_domain_name_servers = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[27]:                       requested_interface_mtu = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       requested_netbios_scope = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'wlan0' [IF]>/64, gw = ::

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Marvell Technology Group Ltd.
GENERAL.PRODUCT:                        88E8038 PCI-E Fast Ethernet Controller
GENERAL.DRIVER:                         sky2
GENERAL.DRIVER-VERSION:                 1.30
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off

SSID       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
ATT448     <MAC 'ATT448' [AN1]>  Infra  6     2437 MHz  54 Mbit/s  12      &#9602;___  WPA1 WPA2  no        
SpiderBee  <MAC 'SpiderBee' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2       yes     * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/SpiderBee]] (600 root)
[connection] id=SpiderBee | type=wifi
[wifi] ssid=SpiderBee | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

```

---

### Post by trey9 on 2015-08-22
```

lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency=2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'SpiderBee' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"SpiderBee"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000062815b233
                    Extra: Last beacon: 216ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k_htc]
filename:       /lib/modules/3.19.0-27-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       htc_9271.fw
firmware:       htc_7010.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     9FC596B0C1CEBEED9FFC60F
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.19.0-27-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        59:F9:ED:39:B7:0E:7C:0C:30:49:A3:F1:B8:FC:38:17:65:8B:28:D7
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.19.0-27-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     8836292C9539A29CB162A5D
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       3.19.0-27-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        59:F9:ED:39:B7:0E:7C:0C:30:49:A3:F1:B8:FC:38:17:65:8B:28:D7
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.19.0-27-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     C1A24C37619ED65AB1240B9
depends:        ath
intree:         Y
vermagic:       3.19.0-27-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        59:F9:ED:39:B7:0E:7C:0C:30:49:A3:F1:B8:FC:38:17:65:8B:28:D7
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.19.0-27-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     D89F916A5E804AF040C4D29
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-27-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        59:F9:ED:39:B7:0E:7C:0C:30:49:A3:F1:B8:FC:38:17:65:8B:28:D7
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-27-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     DF4E06FB15FF0707074A816
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-27-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        59:F9:ED:39:B7:0E:7C:0C:30:49:A3:F1:B8:FC:38:17:65:8B:28:D7
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[wl]
filename:       /lib/modules/3.19.0-27-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     9A49255BA90267D99664757
depends:        cfg80211
vermagic:       3.19.0-27-generic SMP mod_unload modversions 686 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.19.0-27-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-27-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        59:F9:ED:39:B7:0E:7C:0C:30:49:A3:F1:B8:FC:38:17:65:8B:28:D7
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k_htc]
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/sl-modem.conf]
install slamr /sbin/modprobe -qb ungrab-winmodem; /sbin/modprobe --ignore-install slamr; test -e /dev/slamr0 && (chmod 660 /dev/slamr0 && chgrp dialout /dev/slamr0) || (/bin/mknod -m 660 /dev/slamr0 c 242 0 2>/dev/null && chgrp dialout /dev/slamr0)
remove slamr /sbin/modprobe --remove --ignore-remove slamr; test -e /dev/slamr0 && /bin/rm -f /dev/slamr0 2>/dev/null
install slusb /sbin/modprobe -qb ungrab-winmodem; /sbin/modprobe --ignore-install slusb; test -e /dev/slusb0 && (chmod 660 /dev/slusb0 && chgrp dialout /dev/slusb0) || (/bin/mknod -m 660 /dev/slusb0 c 243 0 2>/dev/null && chgrp dialout /dev/slusb0)
remove slusb /sbin/modprobe --remove --ignore-remove slusb; test -e /dev/slusb0 && /bin/rm -f /dev/slusb0 2>/dev/null

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
Binary file /etc/udev/rules.d/70-persistent-net.rules matches

##### dmesg #############################

[   17.336009]  [<f9c4c9f3>] wl_free_if.isra.15+0x23/0xa0 [wl]
[   17.336009]  [<f9c4d1f2>] wl_free+0x52/0x270 [wl]
[   17.336009]  [<f9c4d76c>] wl_pci_probe+0x35c/0x6e0 [wl]
[   17.336009]  [<f922f06d>] wl_module_init+0x6d/0x1000 [wl]
[   58.637616] usb 1-1: ath9k_htc: Firmware htc_9271.fw requested
[   58.638463] usbcore: registered new interface driver ath9k_htc
[   58.976833] usb 1-1: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   59.213078] ath9k_htc 1-1:1.0: ath9k_htc: HTC initialized with 33 credits
[   59.451233] ath9k_htc 1-1:1.0: ath9k_htc: FW Version: 1.3
[   59.451242] ath: EEPROM regdomain: 0x60
[   59.451244] ath: EEPROM indicates we should expect a direct regpair map
[   59.451249] ath: Country alpha2 being used: 00
[   59.451251] ath: Regpair used: 0x60
[   63.774734] wlan0: authenticate with <MAC 'SpiderBee' [AC1]>
[   64.062060] wlan0: send auth to <MAC 'SpiderBee' [AC1]> (try 1/3)
[   64.063884] wlan0: authenticated
[   64.064277] ath9k_htc 1-1:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   64.064288] ath9k_htc 1-1:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   64.068085] wlan0: associate with <MAC 'SpiderBee' [AC1]> (try 1/3)
[   64.070952] wlan0: RX AssocResp from <MAC 'SpiderBee' [AC1]> (capab=0x411 status=0 aid=6)
[   64.080149] wlan0: associated

########## wireless info END ############

```

---

### Post by Hadaka on 2015-08-22
you must have loaded every possible deriver there is
plaese do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe b43
```



05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0465]
    Kernel driver in use: wl <-WRONG DRIVER

---

### Post by trey9 on 2015-08-22
```

sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for trey: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 7,136 kB disk space will be freed.
Do you want to continue? [Y/n] 
Y
(Reading database ... 208130 files and directories currently installed.)
Removing bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu2) ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu2) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-27-generic
trey@trey-MX6448:~$ sudo apt-get remove --purge ath9k
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ath9k
trey@trey-MX6448:~$ 

```

---

### Post by Hadaka on 2015-08-22
did you..
```
sudo modprobe b43
```
is the wireless now working?
Please copy and paste and post the output of..
```
lspci -nnk | grep -iA2 net
```
thanks

---

### Post by trey9 on 2015-08-22
```

trey@trey-MX6448:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
    Subsystem: Gateway, Inc. Device [107b:0367]
    Kernel driver in use: sky2
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0465]
    Kernel driver in use: b43-pci-bridge
trey@trey-MX6448:~$ 

```

---

### Post by Hadaka on 2015-08-22
Finally you have the correct driver loaded. remove the usb wireless
boot and see if you have wireless working..again as a reminder  do
no not load the propriety driver...additional drivers...it is incorrect,
you have the correct b43 now.
if you dont connect..please re-insert the usb wifi or better still use
the ethernet cable and run and post the wireless info txt file again.
also please post ..
```
lsusb
```
thanks

---

### Post by trey9 on 2015-08-23
```

########## wireless info START ##########

Report from: 23 Aug 2015 00:55 EDT -0400

Booted last: 22 Aug 2015 23:45 EDT -0400

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-27-generic #29-Ubuntu SMP Fri Aug 14 21:43:05 UTC 2015 i686 athlon i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
    Subsystem: Gateway, Inc. Device [107b:0367]
    Kernel driver in use: sky2

05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0465]
    Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 001 Device 002: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k_htc              65536  0 
ath9k_common           32768  1 ath9k_htc
ath9k_hw              442368  2 ath9k_common,ath9k_htc
ath                    24576  3 ath9k_common,ath9k_htc,ath9k_hw
b43                   401408  0 
bcma                   49152  1 b43
mac80211              626688  2 b43,ath9k_htc
ssb_hcd                16384  0 
cfg80211              462848  5 b43,ath,ath9k_common,mac80211,ath9k_htc
ssb                    57344  2 b43,ssb_hcd

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1886 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1678 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:568861 (568.8 KB)  TX bytes:305654 (305.6 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"SpiderBee"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'SpiderBee' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:59   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    400    0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       549     1  0 Aug22 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         NETGEAR WNA
GENERAL.PRODUCT:                        WNA1100
GENERAL.DRIVER:                         ath9k_htc
GENERAL.DRIVER-VERSION:                 3.19.0-27-generic
GENERAL.FIRMWARE-VERSION:               1.3
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:13.2/usb1/1-1/1-1:1.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     SpiderBee
GENERAL.CON-UUID:                       5442a4cd-f071-4b51-af41-9830a55d7326
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     54 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5442a4cd-f071-4b51-af41-9830a55d7326 | SpiderBee
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 192.168.1.109/24, gw = 192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             68.105.28.11
IP4.DNS[2]:                             68.105.29.11
IP4.DNS[3]:                             68.105.28.12
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        network_number = 192.168.1.0
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_time_offset = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_host_name = 1
DHCP4.OPTION[8]:                        host_name = trey-MX6448
DHCP4.OPTION[9]:                        expiry = 1440388051
DHCP4.OPTION[10]:                       requested_wpad = 1
DHCP4.OPTION[11]:                       requested_domain_name = 1
DHCP4.OPTION[12]:                       next_server = 192.168.1.1
DHCP4.OPTION[13]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_subnet_mask = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       ip_address = 192.168.1.109
DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[19]:                       requested_static_routes = 1
DHCP4.OPTION[20]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[21]:                       dhcp_lease_time = 86400
DHCP4.OPTION[22]:                       domain_name_servers = 68.105.28.11 68.105.29.11 68.105.28.12
DHCP4.OPTION[23]:                       requested_domain_name_servers = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[27]:                       requested_interface_mtu = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       requested_netbios_scope = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'wlan0' [IF]>/64, gw = ::

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Marvell Technology Group Ltd.
GENERAL.PRODUCT:                        88E8038 PCI-E Fast Ethernet Controller
GENERAL.DRIVER:                         sky2
GENERAL.DRIVER-VERSION:                 1.30
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off

SSID       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
SpiderBee  <MAC 'SpiderBee' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WPA2      yes     * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/SpiderBee]] (600 root)
[connection] id=SpiderBee | type=wifi
[wifi] ssid=SpiderBee | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency=2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.437 GHz (Channel 6)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'SpiderBee' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"SpiderBee"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a9afa2a5f
                    Extra: Last beacon: 228ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ATT448' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"ATT448"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c3294dc183
                    Extra: Last beacon: 1788ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k_htc]
filename:       /lib/modules/3.19.0-27-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       htc_9271.fw
firmware:       htc_7010.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     9FC596B0C1CEBEED9FFC60F
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.19.0-27-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        59:F9:ED:39:B7:0E:7C:0C:30:49:A3:F1:B8:FC:38:17:65:8B:28:D7
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.19.0-27-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     8836292C9539A29CB162A5D
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       3.19.0-27-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        59:F9:ED:39:B7:0E:7C:0C:30:49:A3:F1:B8:FC:38:17:65:8B:28:D7
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.19.0-27-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     C1A24C37619ED65AB1240B9
depends:        ath
intree:         Y
vermagic:       3.19.0-27-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        59:F9:ED:39:B7:0E:7C:0C:30:49:A3:F1:B8:FC:38:17:65:8B:28:D7
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.19.0-27-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     D89F916A5E804AF040C4D29
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-27-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        59:F9:ED:39:B7:0E:7C:0C:30:49:A3:F1:B8:FC:38:17:65:8B:28:D7
sig_hashalgo:   sha512

[b43]
filename:       /lib/modules/3.19.0-27-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     11BDA0A580599B083FE4F2B
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-27-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        59:F9:ED:39:B7:0E:7C:0C:30:49:A3:F1:B8:FC:38:17:65:8B:28:D7
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/3.19.0-27-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F17244FFF75F9BDF92327ED
depends:        
intree:         Y
vermagic:       3.19.0-27-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        59:F9:ED:39:B7:0E:7C:0C:30:49:A3:F1:B8:FC:38:17:65:8B:28:D7
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-27-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     DF4E06FB15FF0707074A816
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-27-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        59:F9:ED:39:B7:0E:7C:0C:30:49:A3:F1:B8:FC:38:17:65:8B:28:D7
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[ssb_hcd]
filename:       /lib/modules/3.19.0-27-generic/kernel/drivers/usb/host/ssb-hcd.ko
license:        GPL
description:    Common USB driver for SSB Bus
author:         Hauke Mehrtens
srcversion:     2A4C0EB5791EE9A11133FCB
depends:        ssb
intree:         Y
vermagic:       3.19.0-27-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        59:F9:ED:39:B7:0E:7C:0C:30:49:A3:F1:B8:FC:38:17:65:8B:28:D7
sig_hashalgo:   sha512

[cfg80211]
filename:       /lib/modules/3.19.0-27-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-27-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        59:F9:ED:39:B7:0E:7C:0C:30:49:A3:F1:B8:FC:38:17:65:8B:28:D7
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.19.0-27-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     551AE4C23939F7FBED9DA61
depends:        
intree:         Y
vermagic:       3.19.0-27-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        59:F9:ED:39:B7:0E:7C:0C:30:49:A3:F1:B8:FC:38:17:65:8B:28:D7
sig_hashalgo:   sha512

##### module parameters #################

[ath9k_htc]
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/sl-modem.conf]
install slamr /sbin/modprobe -qb ungrab-winmodem; /sbin/modprobe --ignore-install slamr; test -e /dev/slamr0 && (chmod 660 /dev/slamr0 && chgrp dialout /dev/slamr0) || (/bin/mknod -m 660 /dev/slamr0 c 242 0 2>/dev/null && chgrp dialout /dev/slamr0)
remove slamr /sbin/modprobe --remove --ignore-remove slamr; test -e /dev/slamr0 && /bin/rm -f /dev/slamr0 2>/dev/null
install slusb /sbin/modprobe -qb ungrab-winmodem; /sbin/modprobe --ignore-install slusb; test -e /dev/slusb0 && (chmod 660 /dev/slusb0 && chgrp dialout /dev/slusb0) || (/bin/mknod -m 660 /dev/slusb0 c 243 0 2>/dev/null && chgrp dialout /dev/slusb0)
remove slusb /sbin/modprobe --remove --ignore-remove slusb; test -e /dev/slusb0 && /bin/rm -f /dev/slusb0 2>/dev/null

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
Binary file /etc/udev/rules.d/70-persistent-net.rules matches

##### dmesg #############################

[   15.719580] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   15.748171] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   15.748195] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 2, Version 0
[   15.836976] b43 ssb0:0: firmware, attempted to load /lib/firmware/b43/ucode5.fw, but failed with error -22
[   15.836984] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -22
[   15.837115] b43 ssb0:0: firmware, attempted to load /lib/firmware/b43/ucode5.fw, but failed with error -22
[   15.837119] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -22
[   15.837162] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2 (repeated 2 times)
[   15.837185] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" request failed (err=-22)
[   15.837189] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   15.837192] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  102.848275] usb 1-1: ath9k_htc: Firmware htc_9271.fw requested
[  102.848753] usbcore: registered new interface driver ath9k_htc
[  103.288331] usb 1-1: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[  103.525000] ath9k_htc 1-1:1.0: ath9k_htc: HTC initialized with 33 credits
[  103.785015] ath9k_htc 1-1:1.0: ath9k_htc: FW Version: 1.3
[  103.785024] ath: EEPROM regdomain: 0x60
[  103.785027] ath: EEPROM indicates we should expect a direct regpair map
[  103.785031] ath: Country alpha2 being used: 00
[  103.785033] ath: Regpair used: 0x60
[  107.939594] wlan0: authenticate with <MAC 'SpiderBee' [AC1]>
[  108.231828] wlan0: send auth to <MAC 'SpiderBee' [AC1]> (try 1/3)
[  108.234210] wlan0: authenticated
[  108.234725] ath9k_htc 1-1:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  108.234737] ath9k_htc 1-1:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  108.239337] wlan0: associate with <MAC 'SpiderBee' [AC1]> (try 1/3)
[  108.242772] wlan0: RX AssocResp from <MAC 'SpiderBee' [AC1]> (capab=0x411 status=0 aid=6)
[  108.249898] wlan0: associated

########## wireless info END ############

```

---

### Post by trey9 on 2015-08-23
```

trey@trey-MX6448:~$ lsusb
Bus 001 Device 002: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
trey@trey-MX6448:~$ 

```

---

### Post by Hadaka on 2015-08-23
do you have access to your router?..can you connect to it with eth0
as in make a hard wire connection?
please run and post the output of.,
```
sudo apt-get install firmware-b43-installer
```
thanks

---

### Post by trey9 on 2015-08-23
i might have access to an ethernet tomorrow
```

trey@trey-MX6448:~$ sudo apt-get install firmware-b43-installer
[sudo] password for trey: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
trey@trey-MX6448:~$ 

```

---

### Post by Hadaka on 2015-08-23
That would be best,, your last info text file shows that you
arent getting the b43 firmware files.
```
   15.837185] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" request failed (err=-22) [   15.837189] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
``` Trying to shoot wireless trouble
with a usb wireless connection makes it difficult because ..wireless is working.
if you get a wired connection tomorrow ..please do..
and do each command..even if there are errors,,or file not found,,
make sure you remove the usb wifi before running these
```
sudo apt-get update
sudo rm /etc/modprobe.d/blacklist-bcm43.conf     #<---this will probably fail...thats ok..continue on
sudo apt-get install firmware-b43-installer
```
then do.
```
sudo iw reg set US
sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
thanks.

---

### Post by praseodym on 2015-08-23
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
should do the trick. It contains the missing files.
Reboot

---

