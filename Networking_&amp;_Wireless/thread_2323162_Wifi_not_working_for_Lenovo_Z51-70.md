---
title: "Wifi not working for Lenovo Z51-70"
date: 2016-05-03
forum: Networking &amp; Wireless
---

### Post by siva15 on 2016-05-03
I am new to ubuntu, my wifi is not working. Can someone help me to guide how to make my wifi work?

---

### Post by howefield on 2016-05-03
First thing you might do is to read this [sticky]("http://ubuntuforums.org/showthread.php?t=370108") and provide the information that it suggests which will allow others to help you. :)

---

### Post by siva15 on 2016-05-03
Hi , I have provided the wireless script. Is tat enough?




```



########## wireless info START ##########


Report from: 03 May 2016 12:22 CEST +0200


Booted last: 03 May 2016 00:00 CEST +0200


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3826]
	Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter [168c:0041] (rev 20)
	Subsystem: Lenovo QCA6164 802.11ac Wireless Network Adapter [17aa:3545]
	Kernel modules: ath10k_pci


##### lsusb #############################


Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 002 Device 003: ID 174f:14ee Syntek 
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


snd_soc_rt286          36864  0
snd_soc_rl6347a        16384  1 snd_soc_rt286
snd_soc_core          212992  2 snd_soc_ssm4567,snd_soc_rt286
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_rt286,snd_pcm_dmaengine,snd_hda_core
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  2 i915,ideapad_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF]>  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::612:b7cf:7852:a219/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:952 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1012 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:621419 (621.4 KB)  TX bytes:190587 (190.5 KB)


##### iwconfig ##########################


enp2s0    no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       753     1  0 12:20 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       c51923f9-2227-4a0b-9129-d523e41fc05e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c51923f9-2227-4a0b-9129-d523e41fc05e | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.101/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1462278121
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.101
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.0.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::612:b7cf:7852:a219/64
IP6.GATEWAY:                            


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


nl80211 not found.


##### iwlist channels ###################


enp2s0    no frequency information.


lo        no frequency information.


##### iwlist scan #######################


enp2s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=y


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


grep: /etc/udev/rules.d/*net*.rules: No such file or directory


##### dmesg #############################


[    6.177429] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    6.200696] r8169 0000:02:00.0 enp2s0: link down (repeated 2 times)
[    6.200779] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    7.780153] r8169 0000:02:00.0 enp2s0: link up
[    7.780162] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
[   17.568187] r8169 0000:02:00.0 enp2s0: link down
[   47.134702] r8169 0000:02:00.0 enp2s0: link up
[   52.540841] r8169 0000:02:00.0 enp2s0: link down
[   81.130153] r8169 0000:02:00.0 enp2s0: link up


########## wireless info END ############
```

---

### Post by chili555 on 2016-05-03
What does this tell us?```
sudo modprobe ath10k_pci
dmesg | grep ath
```If, perhaps, it tells us that firmware is missing, search for the exact firmware file it wants; i.e. firmware-2.bin, firmware-5.bin, hw1.0, hw2.1, etc., and look for Solved and jeremy31 or me, chili555.

I suspect your exact problem has an answer out there.

If you get stuck, we'll be glad to assist.

---

### Post by siva15 on 2016-05-14
Hi,
I have tried Jeremy31 code.

Code:
sudo apt-get install build-essential linux-headers-generic git
echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf
wget [https://www.kernel.org/pub/linux/kernel/projects/backports/2015/09/03/backports-20150903.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/2015/09/03/backports-20150903.tar.gz)
tar -zxvf backports-20150903.tar.gz
cd backports-20150903
make defconfig-ath10k
make
sudo make install
git clone [https://github.com/atondwal/ath10k-firmware.git](https://github.com/atondwal/ath10k-firmware.git)
sudo cp -r /ath10k-firmware/ath10k/ /lib/firmware/
sudo cp -r /lib/firmware/ath10k/QCA6164/hw2.1 /lib/firmware/ath10k/QCA6174/


But when I execute   
sudo cp -r /ath10k-firmware/ath10k/ /lib/firmware/
it says No such file or directory

---

### Post by jeremy31 on 2016-05-14
Try this instead
```
sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/
sudo cp -r /lib/firmware/ath10k/QCA6164/hw2.1 /lib/firmware/ath10k/QCA6174/
```

And removal of the old backports is a good idea as the 4.4 kernel has support for the wifi, it lacks the firmware
```
cd backports-20150903
sudo make uninstall
```

Reboot.

See the code tags link in my signature to see how they work

---

### Post by siva15 on 2016-05-15
Hi Jeremy31,

Thanks a lot. Now Wifi is working!!. Small clarification how to avoid wifi driver issue after kernel updates ?

---

### Post by jeremy31 on 2016-05-15
You don't have to worry about kernel updates in Ubuntu 16.04 as the wifi is supported by the kernel

---

### Post by siva15 on 2016-05-15
Cool!! Thanks a lot :)

---

### Post by svo-n on 2016-09-24
[QUOTE=siva15;13488827]Hi,
I have tried Jeremy31 code.
...
wget [https://www.kernel.org/pub/linux/kernel/projects/backports/2015/09/03/backports-20150903.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/2015/09/03/backports-20150903.tar.gz)
...


Hi, I have find: "404 Not Found"...

---

### Post by jeremy31 on 2016-09-24
Please see the wireless script link in my signature and post the contents of the wireless-info.**txt** file or attach the wireless-info.tar.gz

---

### Post by svo-n on 2016-09-24
Yes, I think I have gone it. But still I cant see any wifi.

---

### Post by jeremy31 on 2016-09-24
The script gathers info about your system so that we do not need to ask as many questions.  Please post the file

---

### Post by svo-n on 2017-02-03
Please, I have the same problem. My txt file about wifi is little bit defferent.

---

### Post by chili555 on 2017-02-03
> **svo-n said:**
> Please, I have the same problem. My txt file about wifi is little bit defferent.Your wireless device is:> Network controller [0280]: Broadcom Corporation Device [14e4:43ae] (rev 02)
	Subsystem: Lenovo Device [17aa:0622]
I'm not at all sure we've encountered that exact device before. Let's install the most likely driver and see if it works:```
sudo apt-get install bcmwl-kernel-source
```
Detach the ethernet, reboot and let us have your report.

---

### Post by svo-n on 2017-02-03
Thank You. I did it. But I can't see any wi-fi... I attach txt file about wifi again.

---

### Post by chili555 on 2017-02-03
That didn't work at all:>  wl driver 6.30.223.248 (r487574) failed with code 1001An extensive Google search finds several posts about your exact device and trying the Broadcom STA driver (bcmwl-kernel-source) or brcmsmac or bcma or b43 and firmware or even ndiswrapper yield no success. The only suggestion is to get a different device.

RANT: Please do not be fooled by this interesting page: [https://github.com/nekhbet/linux-14e4-43ae](https://github.com/nekhbet/linux-14e4-43ae) Although he says, "make Broadcom Wi-Fi (14e4:43ae) work on Debian-based Linux distros", his install script has nothing, NOTHING WHATEVER to do with a Broadcom device. Here is a snip:```
git clone https://github.com/kvalo/ath10k-firmware.git
cd ath10k-firmware/QCA9377/hw1.0
sudo mkdir -p /lib/firmware/ath10k/QCA9377/hw1.0
sudo cp board.bin /lib/firmware/ath10k/QCA9377/hw1.0
```This is for an Atheros ath10k_pci device and has nothing to do with Broadcom.

I raised an issue with the originator and he had no explanation and simply deleted my question. Why do people do things like this???

End rant. Whew, I feel better now.

I suggest that you get a different device.

---

### Post by svo-n on 2017-02-03
I thank you very much for your work and time. Can you maybe get an tip (proposal) for some different device? It's all Greek to me...Or shall I claim this notebook? Oh, it's sad.                             [TABLE="class: EMI_table EMI_table_bordered EMI_table_full_width EMI_table_with_repro EMI_table_scrollable"]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]

---

### Post by chili555 on 2017-02-03
Lenovo is well known to whitelist its wireless devices. That means that you can only install an approved-by-Lenovo PCI wireless device. Here is a recent discussion on the subject: [https://forum.thinkpads.com/viewtopic.php?f=68&t=122095](https://forum.thinkpads.com/viewtopic.php?f=68&t=122095) Because yours is, I assume, an older model, I have been unable to locate the System Service Parts list for your exact model. I can therefor offer no suggestions as to replacing the internal card.

You can easily get a USB wireless, however. I have and use this: [https://www.amazon.com/TP-Link-N150-Wireless-Adapter-TL-WN722N/dp/B002SZEOLG/](https://www.amazon.com/TP-Link-N150-Wireless-Adapter-TL-WN722N/dp/B002SZEOLG/)

---

