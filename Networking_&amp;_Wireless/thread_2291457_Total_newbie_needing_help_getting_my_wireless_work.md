---
title: "Total newbie needing help getting my wireless working."
date: 2015-08-20
forum: Networking &amp; Wireless
---

### Post by Trainergames on 2015-08-20
I installed xubuntu on an old laptop,an Acer Aspire 3050 1594,which i upgraded the cpu to a [COLOR=#282828][FONT=Roboto]AMD turion X2 TL-64 and the ram to 3gb. the wireless card in the laptop is a Broadcom [/FONT][/COLOR]bcm94318mpg.

Before now i have never used linux before so this is all new to me,i have no clue what i am doing lol.

When i first installed xubuntu i was not connected to the internet, i have connected using a wired connection.

I then tried some things in terminal that i got from google,but none worked,and i have no idea what to do.

Here is that i have tried already.

"sudo apt-get install b43-fwcutter firmware-b43-installer"
"sudo apt-get install firmware-b43legacy-installer"

But they said something like package not found.

What do i do?

Thank you guys for helping me.

---

### Post by kerry_s on 2015-08-20
if your connected to the internet, just run "additional drivers" it's slow just wait.

---

### Post by Trainergames on 2015-08-20
> **kerry_s said:**
> if your connected to the internet, just run "additional drivers" it's slow just wait.

I did and it says "no additional drivers available",i know the card works because when i had tried to run windows 7 before this it worked fine after i installed the vista driver.

After a few minutes of googling that message i decided to use "sudo lspci" to see if mabye it's broken, but it shows up.

---

### Post by howefield on 2015-08-20
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by kerry_s on 2015-08-20
did you run "sudo apt-get update" before you ran the commands ?

it should be:
sudo apt-get update
sudo apt-get install firmware-b43-installer


then reboot

---

### Post by Bucky Ball on 2015-08-20
And if it still doesn't work:

```
sudo lshw -C network
```

... or the output of the wireless info script in my signature, thanks. :)

---

### Post by Trainergames on 2015-08-20
> **Bucky Ball said:**
> And if it still doesn't work:

```
sudo lshw -C network
```

... or the output of the wireless info script in my signature, thanks. :)

Sorry for the late reply i ended up having to go run some errands.

Here is the Wireless-info.txt.
```
########## wireless info START ##########

Report from: 20 Aug 2015 20:42 CDT -0500


Booted last: 20 Aug 2015 20:36 CDT -0500


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.19.0-26-generic #28~14.04.1-Ubuntu SMP Wed Aug 12 14:12:35 UTC 2015 i686 athlon i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Xubuntu


##### lspci #############################


08:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:010f]
	Kernel driver in use: 8139too


08:04.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: AMBIT Microsystem Corp. TravelMate 2410 [1468:0312]
	Kernel driver in use: wl


##### lsusb #############################


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


0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


wl                   6148096  1 
acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
video                  20480  1 acer_wmi
cfg80211              450560  1 wl
wmi                    20480  1 acer_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.86  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:306:370c:a680:a9f7:ccca:8d12:155c/64 Scope:Global
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          inet6 addr: 2602:306:370c:a680:<IP6 'eth0' [IF]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3570442 (3.5 MB)  TX bytes:366160 (366.1 KB)


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1
search attlocal.net


##### network managers ##################


Installed:


	NetworkManager


Running:


root       909     1  0 20:36 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.86
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254


  IPv6 Settings:
    Address:         2602:306:370c:a680:a9f7:ccca:8d12:155c
    Prefix:          64
    Gateway:         fe80::224:56ff:fed8:c391


    Address:         2602:306:370c:a680:<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         fe80::224:56ff:fed8:c391


    Address:         fe80::<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         fe80::224:56ff:fed8:c391


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


Error executing command as another user: Request dismissed


Acquisition of admin privileges failed.


##### iw reg get ########################


Region: America/Chicago (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


##### iwlist scan #######################


Error executError executing command as another user: Request dismissed


Acquisition of admin privileges failed.


##### module infos ######################


[wl]
filename:       /lib/modules/3.19.0-26-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     9A49255BA90267D99664757
depends:        cfg80211
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[cfg80211]
filename:       /lib/modules/3.19.0-26-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A9:0C:A5:C5:24:E2:3A:FE:22:C9:47:A3:15:A8:52:38:50:22:46:62
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp


##### modprobe options ##################


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


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[   23.082403] wl driver 6.30.223.248 (r487574) failed with code 21
[   23.084003] EIP is at wdev_priv.part.9+0x3/0x5 [wl]
[   23.084011]  [<f9bccaa3>] wl_free_if.isra.15+0x23/0xa0 [wl]
[   23.084011]  [<f9bcd2d8>] wl_free+0x78/0x220 [wl]
[   23.084011]  [<f9bcd7f1>] wl_pci_probe+0x371/0x730 [wl]
[   23.084011]  [<f8b30073>] wl_module_init+0x73/0x1000 [wl]
[   23.084011] EIP: [<f9bd52a1>] wdev_priv.part.9+0x3/0x5 [wl] SS:ESP 0068:f1a29bac


########## wireless info END ############



```

Thank you guys for the help.

---

### Post by Hadaka on 2015-08-20
Hi, from a connected working wired connection
open a terminal ctrl/alt/t then COPY and paste
each command,one line at a time.
```
sudo apt-get update
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
then do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
dissconnect your wired connection and boot
test wireless

---

### Post by kerry_s on 2015-08-20
run:
sudo apt-get reinstall bcmwl-kernel-source

---

### Post by Hadaka on 2015-08-20
@ kerry_s please note*
Wireless Sticky
[http://ubuntuforums.org/showthread.php?t=2214110&](http://ubuntuforums.org/showthread.php?t=2214110&)

pci-id from wireless info text
Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318]

correct wireless driver
14e4:4318                  firmware-b43-installer                firmware-b43-installer

---

### Post by Trainergames on 2015-08-20
> **Hadaka said:**
> Hi, from a connected working wired connection
open a terminal ctrl/alt/t then COPY and paste
each command,one line at a time.
```
sudo apt-get update
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
then do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
dissconnect your wired connection and boot
test wireless
Thank you so very much, it worked, now i can use the laptop for what i planned too.

---

### Post by Bucky Ball on 2015-08-20
Excellent news. Please see the link in my signature to mark the thread as solved. 

Good luck and enjoy. :)

---

### Post by Hadaka on 2015-08-21
Just as Bucky Ball says "Excellent news !"

---

