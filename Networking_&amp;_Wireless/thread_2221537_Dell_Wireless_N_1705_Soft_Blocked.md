---
title: "Dell Wireless N 1705 Soft Blocked"
date: 2014-05-02
forum: Networking &amp; Wireless
---

### Post by Doug_Ellington on 2014-05-02
Hello 

Upfront - forgive me for newbie question. 

I am running Ubuntu 12.04.4 LTS through a USB Drive. My wireless card is  a Dell Wireless-N 1705, my laptop is a Dell Inspiron i15RV-1435BLK.  Wired Ethernet will work, but wireless has not worked since install. In  Network Manager I can see the name of my wireless network, but there is  no way to connect to it. I have done research on the internet and  attempted to download many drivers, but I fear this has made it worse.  Below are my results in terminal. I have been sitting next to my  wireless router (not close to my office) for quite some time trying to  get this working. Any help is greatly appreciated. 

anonymous@computer:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
anonymous@computer:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr ec:f4:bb:01:a9:a3  
          inet addr:192.168.1.172  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::eef4:bbff:fe01:a9a3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11031 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5688 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11228449 (11.2 MB)  TX bytes:1366361 (1.3 MB)
          Interrupt:42 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:83177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27872131 (27.8 MB)  TX bytes:27872131 (27.8 MB)

anonymous@computer:~$ iwlist wlan 0 scan
iwlist: unknown command `0' (check 'iwlist --help').
anonymous@computer:~$ dmesg | grep b43

---

### Post by Hadaka on 2014-05-02
Hi, please do...
```
sudo apt-get update
rfkill unblock all
```
boot...then do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
thanks.

---

### Post by Doug_Ellington on 2014-05-02
Thanks for the fast reply Hadaka.

Please help - what am i doing wrong. I ctrl + alt + t to open terminal and copy and paste ctrl + shift + v:
sudo apt-get update
rfkill unblock all

but only sudo apt-get update seems to run. So I put it all on one line and get the following in terminal:

anonymous@computer:~$ sudo apt-get update rfkill unblock all
[sudo] password for anonymous: 
E: The update command takes no arguments
anonymous@computer:~$ 

Again apologies for extremely newbie question and thanks for the assistance.

---

### Post by Hadaka on 2014-05-02
the rfkill unblock command was a single comand.
when it comes back and says noing..it means..no change...or i was done.'
ok.
from the wired connection connected to the internet...please do
*ignore any error but run anyway...
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
then do..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
then
```
rfkill ublock all
rfkill list all
```
thanks

---

### Post by Doug_Ellington on 2014-05-02
Hadaka 

You are a godsend - thanks for taking the time. Unfortunately, still showing as softblocked. I think the problem came with 
sudo rm /etc/modprobe.d/blacklist-bcm43.conf 

and

sudo modprobe b43






I know you said to ignore any error messages, but I don't think those went through.

Am I doing something wrong? Here is a copy of the terminal:
[B]
anonymous@computer:~$ sudo apt-get remove --purge bcmwl-kernel-source[/B]
[sudo] password for anonymous: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bcmwl-kernel-source is not installed, so not removed
The following packages were automatically installed and are no longer required:
  gir1.2-polkit-1.0 libc-dev-bin libgomp1 linux-libc-dev gcc-4.6 gcc dkms
  libc6-dev libquadmath0 gnome-icon-theme-symbolic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 110 not upgraded.
**anonymous@computer:~$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf**
rm: cannot remove `/etc/modprobe.d/blacklist-bcm43.conf': No such file or directory
**anonymous@computer:~$ sudo apt-get install linux-firmware-nonfree**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  gir1.2-polkit-1.0 libc-dev-bin libgomp1 linux-libc-dev gcc-4.6 gcc dkms
  libc6-dev libquadmath0 gnome-icon-theme-symbolic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 110 not upgraded.
[B]anonymous@computer:~$ sudo modprobe b43
anonymous@computer:~$ rfkill ublock all[/B]
Usage:    rfkill [options] command
Options:
    --version    show version (0.4-1ubuntu2 (Ubuntu))
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
**anonymous@computer:~$ rfkill list all**
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
anonymous@computer:~$

---

### Post by Hadaka on 2014-05-02
you'rer not doing anything wrong, this is just all new
and confusing to you,but..you'll get it !
ok..do this...ONE time hold the fn key and press the f2 key
ONCE ~!//then post
```
rfkill list all
```
thanks.

---

### Post by Doug_Ellington on 2014-05-02
Hadaka, I followed your instructions and the terminal finally showed:

anonymous@computer:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
anonymous@computer:~$ 

At least something is changing? Unfortunately wifi still is not working. After rebooting, when I right  click the network manager icon in the bottom right corner there is still  no option for wifi. Any ideas on what the solution might be? These are  my lsmod and lspci results from terminal, please let me know if any  other information will be helpful:

**anonymous@computer:~$ lsmod**
Module                  Size  Used by
joydev                 17393  0 
snd_hda_codec_hdmi     31823  1 
snd_hda_codec_realtek   174313  1 
ip6t_LOG               16846  5 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
nf_conntrack_ipv6      13581  5 
nf_defrag_ipv6         13175  1 nf_conntrack_ipv6
xt_hl                  12465  6 
ip6t_rt                12473  3 
ipt_REJECT             12512  1 
ipt_LOG                12783  6 
parport_pc             32114  0 
ppdev                  12849  0 
xt_limit               12541  14 
xt_tcpudp              12531  24 
xt_state               12514  10 
xt_addrtype            12596  4 
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
ip6table_filter        12711  1 
ip6_tables             18432  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24959  1 nf_nat_ftp
nf_conntrack_ipv4      19084  7 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack            73847  8  nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
snd_hda_intel          32719  1 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ip_tables              18106  1 iptable_filter
x_tables                22011  13  ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_state,xt_addrtype,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
psmouse                96744  0 
rts5139               279656  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                     62218  12  snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
serio_raw              13027  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mei                    36570  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
dm_crypt               22528  1 
usb_storage            39646  2 
wmi                    18744  1 dell_wmi
i915                  428213  2 
r8169                  56396  0 
drm_kms_helper         45466  1 i915
drm                   197641  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19115  1 i915

**anonymous@computer:~$ lspci**
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)

---

### Post by Doug_Ellington on 2014-05-03
Okay here are the results of running this wireless script:


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux computer 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:40:43 UTC 2013 i686 i686 i386 GNU/Linux

##### lspci #####

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:0597]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Dell Device [1028:020c]

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 1f75:0903  
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0c45:64ad Microdia 

##### PCMCIA Card Info #####

##### rfkill #####

0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes

##### iw reg get #####

##### interfaces #####

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#NetworkManager#iface eth0 inet dhcp

##### iwconfig #####

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth2
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth2

##### resolv.conf #####

nameserver 127.0.0.1
search home

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth2  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.172
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

##### iwlist #####

##### iwlist channel #####

##### lsmod #####

##### modinfo #####

##### modules #####

loop
lp

##### blacklist #####

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
blacklist hp_wmi
blacklist hp_wmi

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### udev rules #####

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

##### dmesg #####

########## wireless info END ############

---

### Post by Hadaka on 2014-05-03
Hi, ok please do the fn/f2 key press again.ONE time
(this toggeles on/off the wireless) right now it is off
we need it on.
then do..
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
and BOOT!...Please stop plugging and unplugging usb wireless dongles
it is making it confusing to trouble shoot.
then..from the wired connection connected to the internet please do..

```
sudo apt-get linux-frmware-nonfree
sudo modprobe -r b43
sudo modprobe -v b43
```
boot
after the boot..please run the wireless script again...

---

### Post by Doug_Ellington on 2014-05-03
Hadaka you are a good person. Thanks for your continued help. I will not unplug the USB drive going further, I did not realize that had an impact.

I followed your instructions. Please note that when I inputted sudo rm /etc/udev/rules.d/70-persistent-net.rules, I got a blank response. 

Additionally, this was the response for sudo apt-get linux-frmware-nonfree:

anonymous@computer:~$ sudo apt-get linux-frmware-nonfree
E: Invalid operation linux-frmware-nonfree
anonymous@computer:~$ 

sudo modprobe -r b43 - was blank
sudo modprobe -v b43 - ran, and had the most results


These are the results of the wireless script:



########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux computer 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:40:43 UTC 2013 i686 i686 i386 GNU/Linux

##### lspci #####

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:0597]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Dell Device [1028:020c]

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0c45:64ad Microdia 
Bus 004 Device 002: ID 1f75:0903  
Bus 001 Device 006: ID 0cf3:0036 Atheros Communications, Inc. 

##### PCMCIA Card Info #####


##### rfkill #####

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####


##### interfaces #####

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#NetworkManager#iface eth0 inet dhcp

##### iwconfig #####


##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.0.1
search home

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        EC:F4:BB:01:A9:A3

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.172
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=EC:F4:BB:01:A9:A3,

[ifupdown]
managed=false

##### iwlist #####

---

### Post by Hadaka on 2014-05-03
ok, I have good news..bad news,,and good news

GOOD NEWS...you no longer have any blocks with rfkill list

BAD NEWS...you currently have loaded ubuntu12.04 your wireless card for 12.04

02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01

doent have the [168c:0036] pci-id in its modinfo list.

GOOD NEWS..you can load 14.04 or..13.10 both have that pciid for your ath9k card.

let us know what you would like to do.
thanks.

---

### Post by Doug_Ellington on 2014-05-04
Hadaka- 

Anything that can get my ubuntu working is not bad news! Thank you. My first instinct when I had the issue was go to Update Manager &#8211; Menu / System Tools / Update Manager. It informed me I was in need of an update (I'm assuming 14.04) and it would take ~300mb, and I needed to free up 30mb in my /boot folder, it recommended I clean out my trash folder (which I did) but it was not sufficient to free up enough space. 

Please keep in mind this ubuntu is running from a 16gb usb drive, and I have 10.6gb of free space! How do I free up necessary space in /boot to upgrade?

---

### Post by Hadaka on 2014-05-04
Hi, what the update manager is requesting is an update to security files,
e-mail files and alot of other files that make up the os 12.04..it is NOT
a request to update to 14.04 or whatever. Running Ubuntu on a mem stick
is possible, I have 12.04 on a bootable stick as well,and like you i am unable
to do the updates on it. You are really better off to just load it to the computer.
you can use a usb drive as a novelty or to run on different machines, but..keep
in mind..it is doubtfull the wireless will work on any of them, and they will all be
different. so to be effective a mem stick os needs to run hardwired to a modem.
good luck to you.

---

### Post by Doug_Ellington on 2014-05-04
Hadaka - you have been so incredibly helpful. Thank you for your time. I really need to get ubuntu working from a usb drive! 

Two questions:

1. Is it possible to upgrade my mem stick to os 14.04?
2. If I was to buy a new notebook computer with a different wireless card would wireless work with this bootable stick and os 12.04?

---

### Post by Hadaka on 2014-05-04
Hey Doug
  I dont hve 14.04 loaded so i have no idea if it will work. Anyone with info on this
please feel free to comment.
Yes on a different laptop,although it would be cheper to just change the wifi card.
 I am writeing this on an old dell inspiron 1300 booted up to a 16gig mem stick loaded
with ubuntu 12.04..wireless cards is a boradcom 4318. I am booted up in the try-me
mode as well...just to see if the wireless would work ok, Getting the wireless to work on
this was not simple...i had do jump through some hoops to get it to fly and its been so
long i;ve forgotten what was involved.
please mark this thread solved if you are satisfied with the results
thanks,

---

### Post by Doug_Ellington on 2014-05-05
> **Hadaka said:**
> Hey Doug
  I dont hve 14.04 loaded so i have no idea if it will work. Anyone with info on this
please feel free to comment.
Yes on a different laptop,although it would be cheper to just change the wifi card.
 I am writeing this on an old dell inspiron 1300 booted up to a 16gig mem stick loaded
with ubuntu 12.04..wireless cards is a boradcom 4318. I am booted up in the try-me
mode as well...just to see if the wireless would work ok, Getting the wireless to work on
this was not simple...i had do jump through some hoops to get it to fly and its been so
long i;ve forgotten what was involved.
please mark this thread solved if you are satisfied with the results
thanks,


Hadaka - you were so responsive and generous with your time for no reward, I was actually going to send you $100 via paypal if you helped me solve the problem (probably against forum rules - sorry!). I told a lot of my friends and family about how selfless and helpful you were. I will most definitely mark the thread solved, even though this didn't solve my problem - I just wish we could have gotten it to work.

If anyone is reading this in the future: I contacted the person who manufactured the usb drive and he gave me a recommendation on an Acer laptop that he knows is compatible with Ubuntu 12.04 wireless.

---

