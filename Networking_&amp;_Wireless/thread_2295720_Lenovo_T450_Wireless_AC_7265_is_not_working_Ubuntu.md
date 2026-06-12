---
title: "Lenovo T450 Wireless AC 7265 is not working Ubuntu 15.04"
date: 2015-09-20
forum: Networking &amp; Wireless
---

### Post by Jimmy_Chandra on 2015-09-20
Dear experts,

I had purchased new laptop Lenovo Thinkpad T450 few days ago. I choose it because I hope everything works out of the box with Ubuntu, but unfortunately it didn't :(

The wireless didn't show up. I have dual boot the laptop with Windows 10 and wireless seems working very well in Windows.

OS: Ubuntu 15.04 Vivid
Kernel: 3.19.0-15-generic
Network controller [0280]: Intel Corporation Wireless 7265 [8086:095b] (rev 59)


Wireless Info
```


########## wireless info START ##########

Report from: 21 Sep 2015 10:41 WIB +0700

Booted last: 22 Sep 2015 00:25 WIB +0700

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (3) I218-LM [8086:15a2] (rev 03)
    Subsystem: Lenovo Device [17aa:2226]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095b] (rev 59)
    Subsystem: Intel Corporation Device [8086:5212]

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 5986:0366 Acer, Inc 
Bus 001 Device 002: ID 1038:1384 Ideazon, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              540672  0 
wmi                    20480  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          inet6 addr: fd24:69a5:c7:f200:1c9b:ded9:4fbe:33cc/64 Scope:Global
          inet6 addr: fd24:69a5:c7:f200:<IP6 'eth0' [IF]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51568 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:55394269 (55.3 MB)  TX bytes:3986691 (3.9 MB)
          Interrupt:20 Memory:e1100000-e1120000 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    1024   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       674     1  0 10:25 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (3) I218-LM
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 2.3.2-k
GENERAL.FIRMWARE-VERSION:               0.2-3
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       4a53ba8d-3219-4ab9-8e36-9f3bd45574e3
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   4a53ba8d-3219-4ab9-8e36-9f3bd45574e3 | Wired connection 1
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 192.168.1.5/24, gw = 192.168.1.254
IP4.DNS[1]:                             192.168.1.254
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        expiry = 1442917540
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.254
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       ip_address = 192.168.1.5
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       domain_name_servers = 192.168.1.254 0.0.0.0
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.254
IP6.ADDRESS[1]:                         ip = fd24:69a5:c7:f200:1c9b:ded9:4fbe:33cc/64, gw = ::
IP6.ADDRESS[2]:                         ip = fd24:69a5:c7:f200:<IP6 'eth0' [IF]>/64, gw = ::
IP6.ADDRESS[3]:                         ip = fe80::<IP6 'eth0' [IF]>/64, gw = ::
IP6.ROUTE[1]:                           dst = fd24:69a5:c7:f200::/64, nh = ::, mt = 1

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

##### iw reg get ########################

Region: Asia/Jakarta (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.19.0-15-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     268045EBCFAFDADD136DCF6
depends:        
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:64:80:70:92:F3:A6:A8:F6:6F:3B:7E:A4:CB:37:67:FD:FA:E0:8A
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x15a2 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[    6.577417] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3

########## wireless info END ############


```

I had tried:
- Live cd 15.04: **not working**
- Upgrade kernel 4.2: **not working**
- Live cd 15.10beta: **not working**
- sudo apt-get install linux-firmware: **not working**

Any help would be great.

Thank you so much

---

### Post by jeremy31 on 2015-09-21
This one isn't supported yet but you could try my patched backports to see if they work
```
sudo apt-get install build-essential linux-header-$(uname -r)
```
```
wget https://www.dropbox.com/s/gyuvdlhzx5ho277/backports-20150731.tar.gz
```
```
tar -zxvf backports-20150731.tar.gz
```
```
cd backports-20150731
```
```
make defconfig-iwlwifi
```
```
make
```
```
sudo make install
```

---

### Post by Jimmy_Chandra on 2015-09-21
@jeremy31
I followed your step, but unfortunately it didn't work :(

Any ideas?

---

### Post by chili555 on 2015-09-21
Please help young Jeremy out by showing him:```
sudo modprobe iwlwifi
dmesg | grep iwl
```Thanks.

---

### Post by Jimmy_Chandra on 2015-09-21
@chili555

I executed
```

sudo modprobe iwlwifi
dmesg | grep iwl

```

show nothing

---

### Post by chili555 on 2015-09-21
> Intel Corporation Wireless 7265 [8086:095b] (rev 59)
    Subsystem: Intel Corporation Device [[COLOR="#FF0000"]8086:5212[/COLOR]]I think the problem is that the subsystem ID 8086:5212 is not yet covered in iwlwifi.

Here is my device for comparison:```
Intel Corporation Centrino Advanced-N 6200 [8086:4239] (rev 35)
	Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1311]
	Kernel driver in use: iwlwifi

```I probe the device IDs in the driver iwlwifi:```
$ modinfo iwlwifi | grep 1311
alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v0000[COLOR="#FF0000"]8086[/COLOR]d0000[COLOR="#FF0000"]4239[/COLOR]sv*sd0000[COLOR="#FF0000"]1311[/COLOR]bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*

```However, when I probe the driver for your device:```
$ modinfo iwlwifi | grep 5212
```I see nothing.

I am trying to work out how to add the subsystem ID 5212 to the backports package you compiled but so far have not yet found it. 

Perhaps Jeremy or one of the other experts here can help us.

---

### Post by Jimmy_Chandra on 2015-09-21
@chili555
Thank you for your investigation.

So upgrading kernel to >= 4.2 and add firmware iwlwifi-7265-14.ucode won't help too?

---

### Post by chili555 on 2015-09-21
Please open the backports package you compiled. Drill down to drivers > net > wireless > iwlwifi > pcie. Open the file drv.c with any text editor, like gedit. Scroll down to line 406.

Here, I've used some guesswork. I assume this is a 2ac_cfg device. We will simply change an unneeded line to needed. Change:```
{IWL_PCI_DEVICE(0x095B, 0x9200, iwl7265_2ac_cfg)},
```To read:```
{IWL_PCI_DEVICE(0x095B, 0x5212, iwl7265_2ac_cfg)},
```Spacing, punctuation, brackets, etc. ```

```are crucial and must be perfect. Proofread carefully, save and close the text editor. Now:```
cd backports-20150731
make clean
make defconfig-iwlwifi
make
sudo make install 
```Reboot. Any improvement?

---

### Post by Jimmy_Chandra on 2015-09-21
@chili555
OMG YOU'RE GOD. It works!

Here's the result:

Probing Device ID 5212 success
```

jim@padnix:~$ modinfo iwlwifi | grep 5212
alias:          pci:v00008086d0000095Bsv*sd00005212bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005212bc*sc*i*

```

iwconfig now showing wlan0
```

jim@padnix:~$ iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"MYSSID"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 24:69:A5:00:C7:F8   
          Bit Rate=2 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

lo        no wireless extensions.

```

---

### Post by Jimmy_Chandra on 2015-09-21
Thank you so much @chili555 and @jeremy31.

Here's the **complete solution** for everyone who is facing same the problem with me:

Lenovo T450 with wireless AC7265
Network controller [0280]: Intel Corporation Wireless 7265 [8086:095b] (rev 59)
Subsystem: Intel Corporation Device [**8086:5212**]

Look that the Device ID: [**8086:5212]**, we need to probe the driver for that device (because it doesn't exist)

```

sudo apt-get install build-essential linux-headers-$(uname -r)
wget https://www.dropbox.com/s/gyuvdlhzx5ho277/backports-20150731.tar.gz
tar -zxvf backports-20150731.tar.gz
cd backports-20150731

```

As @chili555 told:
open the backports package you compiled. Drill down to drivers > net > wireless > iwlwifi > pcie. Open the file drv.c with any text editor, like gedit. Scroll down to line 406.

We will simply change an unneeded line to needed. Change:

```

{IWL_PCI_DEVICE(0x095B, 0x9200, iwl7265_2ac_cfg)},

```
To read:
```

{IWL_PCI_DEVICE(0x095B, 0x5212, iwl7265_2ac_cfg)},

```

Spacing, punctuation, brackets, etc. are crucial and must be perfect. Proofread carefully, save and close the text editor. Now:
```

cd backports-20150731
make clean
make defconfig-iwlwifi
make
sudo make install

```

Reboot then wireless should be detected now :)

---

### Post by chili555 on 2015-09-21
And does it connect?

Not THE GOD, maybe a god! LOL!!

---

### Post by Jimmy_Chandra on 2015-09-21
My last question:

Do I need to compile this backport everytime I upgrade ubuntu kernel or dist?

---

### Post by Jimmy_Chandra on 2015-09-21
> **chili555 said:**
> And does it connect?

Not THE GOD, maybe a god! LOL!!
Yes. Connect flawlessly

---

### Post by chili555 on 2015-09-21
> **Jimmy_Chandra said:**
> My last question:

Do I need to compile this backport everytime I upgrade ubuntu kernel or dist?Yessir.```
cd backports-20150731
make clean
make defconfig-iwlwifi
make
sudo make install
```Please retain the files and these instructions for that time.

Please accept my answer over on askubuntu.com. Thanks.

---

### Post by Jimmy_Chandra on 2015-09-21
> **chili555 said:**
> Yessir.```
cd backports-20150731 make clean make defconfig-iwlwifi make sudo make install
```Please retain the files and these instructions for that time.  Please accept my answer over on askubuntu.com. Thanks. OK. I did.  Thank you so much. You're really a smart person.

---

### Post by jeremy31 on 2015-09-21
I made the change to the backports from dropbox, so it won't need to be patched..it seems I changed a line with 95A instead of 95B

Thanks for the assist chili555

---

### Post by Jimmy_Chandra on 2015-09-22
> **jeremy31 said:**
> I made the change to the backports from dropbox, so it won't need to be patched..it seems I changed a line with 95A instead of 95B

Thanks for the assist chili555
@jeremy31

Thank you so much. I believe your patch will be easier to compile.

---

### Post by jeremy31 on 2015-09-22
You are good to go since you patched the source, you just have to follow chili555's instructions for recompiling it after a kernel update until we get this patch submitted to Ubuntu.  The Intel wifi group is doing an internal review of the patch before sending it upstream to the Linux kernel team, after that we can send it to the Ubuntu people so kernel updates will contain the patch.

I updated my backports so that if we happen to see this chipset issue again, we won't have to instruct on how to patch the source code.  I missed the 95B thing originally but that's what happens when you try to do things early in the morning and that is why your modinfo results in post 9 show a 95A and 95B result

---

### Post by Jimmy_Chandra on 2015-12-10
Update: Now wireless is working flawlessly using kernel 4.3

---

