---
title: "Can't get a Wifi connection, even after Ubuntu reinstall."
date: 2016-04-08
forum: Networking &amp; Wireless
---

### Post by james214 on 2016-04-08
I couldn't get my Ubuntu PC to recognize my library's Wifi connection yesterday. (My smartphone Wifi worked just fine there).
Then I came home, and I couldn't get my PC to recognize my home Wifi either.

I didn't know how to fix this, so I just reinstalled Ubuntu... but it still won't pickup my Wifi connection. (My ethernet connection is working just fine. So is my smartphone's Wifi connection).
(I performed the reinstall using a USB boot stick).

Any idea how to fix this? My PC is about six months old -- certainly doesn't seem like something would have broken.
(My PC is an HP Stream 13.3" laptop).

Edit:  I don't think Ubuntu is recognizing my PC's wireless capabilities at all.  When I typed "ls /sys/class/net" into the terminal, the only result that displayed was "eth0 lo". Please tell me there's a solution for this...

---

### Post by Bucky Ball on 2016-04-08
*Thread moved to **Networking & Wireless**.*

Welcome. You don't mention whether this is an internal or internal wireless card. If internal, run the wireless script linked in my signature at the bottom of this post. If USB wireless dongle, plug it in and run that script. 

Post back the output between code tags, the green link in my signature for how. ;)

(PS: Did you boot the computer at the library and that was it, no wireless card recognised? Had you done and update previously or installed something?)

---

### Post by james214 on 2016-04-08
Internal modem.
Not sure if I'm doing this right, but...

```



########## wireless info START ##########


Report from: 08 Apr 2016 15:04 EDT -0400


Booted last: 08 Apr 2016 14:18 EDT -0400


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.19.0-58-generic #64~14.04.1-Ubuntu SMP Fri Mar 18 19:05:43 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:2230]
	Kernel driver in use: bcma-pci-bridge


##### lsusb #############################


Bus 002 Device 003: ID 0b95:1790 ASIX Electronics Corp. AX88179 Gigabit Ethernet
Bus 002 Device 002: ID 2109:0812 VIA Labs, Inc. VL812 Hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 0a5c:216c Broadcom Corp. BCM43142A0 Bluetooth Device
Bus 001 Device 009: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 006: ID 1058:1003 Western Digital Technologies, Inc. WD Elements Desktop (WDE1UBK)
Bus 001 Device 005: ID 077d:07af Griffin Technology iMic
Bus 001 Device 003: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 001 Device 002: ID 05c8:036e Cheng Uei Precision Industry Co., Ltd (Foxlink) Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
bcma                   53248  0 
snd_soc_rt5640         94208  0 
wmi                    20480  1 hp_wmi
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  2 snd_soc_rt5640,snd_soc_sst_mfld_platform
snd_pcm               106496  9 snd_soc_rt5640,snd_usb_audio,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_sst_mfld_platform,snd_hda_controller,snd_pcm_dmaengine


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.180  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          inet6 addr: 2602:304:ce29:fdc9:4592:5af7:27e1:2934/64 Scope:Global
          inet6 addr: 2602:304:ce29:fdc9:<IP6 'eth0' [IF]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26259 errors:1 dropped:0 overruns:0 frame:0
          TX packets:19961 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26944943 (26.9 MB)  TX bytes:3265953 (3.2 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       674     1  0 14:18 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            ax88179_178a
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.180
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254


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


Region: America/Toronto (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (6, 20)
	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
	(5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
	(5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[bcma]
filename:       /lib/modules/3.19.0-58-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F17244FFF75F9BDF92327ED
depends:        
intree:         Y
vermagic:       3.19.0-58-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        DE:B3:43:0A:26:E6:7D:3D:3B:54:B9:DD:13:25:B3:3A:46:B2:F2:DD
sig_hashalgo:   sha512


##### module parameters #################


##### /etc/modules ######################


lp
rtc


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
# USB device 0x:0x (ax88179_178a)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    9.781562] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-0a5c-216c.hcd failed with error -2
[    9.781571] Bluetooth: hci0: BCM: patch brcm/BCM43142A0-0a5c-216c.hcd not found
[   11.158693] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.210780] ax88179_178a 2-1.1:1.0 eth0: ax88179 - Link status is: 1
[   13.216904] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1263.480349] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1265.317757] ax88179_178a 2-1.1:1.0 eth0: ax88179 - Link status is: 1
[ 1265.325641] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready


########## wireless info END ############


```

---

### Post by james214 on 2016-04-09
Another tool I installed said, "the wireless interface cannot be detected."

For what it's worth, I read somewhere that this might be a BIOS problem... or maybe a problem that can be fixed with one of the other startup menus?

---

### Post by Hadaka on 2016-04-09
Hi james214, with your usb ethernet adapter and active internet connection..
please open a terminal ctrl/alt/t then copy and paste..
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
echo "bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rf bcma
sudo apt-get install bcmwl-kernel-source
sudo modprobe -v wl
```
then do..
```
sudo iw reg set CA
sudo sed -i 's/^REG.*=$/&CA/' /etc/default/crda
```
Remove your usb/ethernet connection, boot and test wireless
thanks.

---

### Post by james214 on 2016-04-11
The good news: My Wifi works now. (Thank you!)
The potentially bad news:  I received a lot of error messages after entering the commands. Here is a sampling:

```

james@HPstream:~$ echo "bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
bcma
james@HPstream:~$ sudo modprobe -rf bcma
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/blacklist.conf line 56: ignoring bad line starting with 'bcma'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/blacklist.conf line 57: ignoring bad line starting with 'bcma'
james@HPstream:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
james@HPstream:~$ sudo modprobe -v wl
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/blacklist.conf line 56: ignoring bad line starting with 'bcma'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/blacklist.conf line 57: ignoring bad line starting with 'bcma'

```

---

### Post by QLee on 2016-04-11
> **james214 said:**
> The potentially bad news:  I received a lot of error messages after entering the commands. Here is a sampling:


Well, the command you used from Hadaka "echo "bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf" was intended to add the mod "bcma" to the mod blacklist. 

And it seems you ran it twice.

However, since the format for that blacklist is "blacklist <module name>" just adding the module name isn't enough and thus those two bad line errors.

Hadaka probably meant for the command to be 
```
 echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Run that code to add the line. Remove those two offending lines from the blacklist.conf file to make the errors go away. Or just edit the file.

---

### Post by Hadaka on 2016-04-11
Hi, QLee is correct, I apologize for my error, If you have entered
the code QLee suggested then you will not need to do it again, If not
then please do to add the correct code..
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
this code will correct the error and eliminate those  messages.
```
sudo sed -i '/bcma/ d' /etc/modprobe.d/blacklist.conf
```
thanks.

@QLee, Thank you.

---

### Post by QLee on 2016-04-11
> **Hadaka said:**
> @QLee, Thank you.

It is a community, I saw you were ofline and stepped in so james214 could have a quick answer. You would have sorted it out as you have when you did arrive. You even coded a simple removal of the offending lines for james214.  Personally, I think it's always best to explain what code will do when it is run but I know many users just want to know which buttons to push and time to document is short when you help as many posters as you do.. If james214 had known what the code was trying to do, might have figured out what the error message meant and figured out what to do to correct it. As we know, error messages in Linux are often useful for understanding the problem. No need to thank me for doing what we are both here for but I do appreciate the acknowledgement from a poster I respect.

---

### Post by james214 on 2016-04-12
Thanks. I just tried entering the proper codes into the Terminal. Not much seemed to happen when I entered them, but at least I didn't get any errors.

Earlier today (before entering the updated code), I was getting intermittent internet service at the library and then again at Panera Bread. Is there any way for me to test my connection? (Maybe packet loss... jitter... or whatever else we might need to test?) Thanks.

---

### Post by Hadaka on 2016-04-12
Hi, having drops and interruptions at public places like the  library and Panera Bread
is quite common as they are heavily used and anyone can access them, You can check
your logs like../var/log/syslog or error messages you may get when the connection has
a problem. Your original thread has been solved for the problem you were having.
Please go to your first post of this thread, click Thread Tools and choose Solved.
If you continue to have other issues, please start a new thread,.
Thanks

---

### Post by QLee on 2016-04-13
> **james214 said:**
> Thanks. I just tried entering the proper codes into the Terminal. Not much seemed to happen when I entered them, but at least I didn't get any errors.

What happened was:
The command "echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf", wrote (echoed) to the file "blacklist.conf" the name of the module that you wanted to blacklist in the correct format this time, "blacklist bcma", thus that module will not be loaded at system boot. However, if you had not run the correct command, at your next boot the module would not have been blacklisted and you would be back with a problem.

The two lines that you wrote to the file previously with the incorrect command and which consisted of just, "bcma" were what were causing the error you saw, ```
"libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/blacklist.conf line 56: ignoring bad line starting with 'bcma'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/blacklist.conf line 57: ignoring bad line starting with 'bcma'
``` It was a minor error, as you can see the system knew enough to ignore those bad lines (here "bad" just means incorrect format) The next command, ```
sudo sed -i '/bcma/ d' /etc/modprobe.d/blacklist.conf
``` deleted the two bad lines so you would not have to see the error they caused while they were there.

Hadaka made it easy for you to correct the error.

If you want to get into things more deeply you can read the manual for the command "sed" by opening a terminal and entering "man sed" (without the quotes).

---

### Post by james214 on 2016-04-13
> **QLee said:**
> If you want to get into things more deeply you can read the manual for the command "sed" by opening a terminal and entering "man sed" (without the quotes).

Thanks. I'm a n00b who only uses Linux because I'm tired of dealing with computer viruses. Sadly, I'm a little disappointed that the "stable" version of Ubuntu isn't more stable. Kind of a bummer that my wireless device would fall of the Earth. At least they have a forum where I can get some help. (I can't see myself spending months & months to master the Terminal -- I'm sure there are plenty of others like me).

---

### Post by QLee on 2016-04-14
> **james214 said:**
> Thanks. I'm a n00b who only uses Linux because I'm tired of dealing with computer viruses. Sadly, I'm a little disappointed that the "stable" version of Ubuntu isn't more stable. Kind of a bummer that my wireless device would fall of the Earth. At least they have a forum where I can get some help. (I can't see myself spending months & months to master the Terminal -- I'm sure there are plenty of others like me).

Of course there are many like you, and more everyday, I expect that's one of the main reasons why these forums exist.
 
Everyone can choose how much or how little they want to learn.

When one buys a computer with an operating system already installed someone has already made sure the hardware has the correct drivers installed, one can do that with Linux systems too but many of us like to install our systems ourselves. I certainly understand why you want to avoid virus or malware. I hope your continued experience with Ubuntu is satisfying.

---

