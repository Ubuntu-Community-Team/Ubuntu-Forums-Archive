---
title: "Bought a new tower, having trouble with wireless."
date: 2014-10-09
forum: Networking &amp; Wireless
---

### Post by jackechanprime on 2014-10-09
Hey all, my old laptop is on it's last half-dozen breaths or so, so I got a new comp -- a desktop model for the first time in ages. Installed ubuntu 14.04 (whatever the latest distro was last night). Works great except for the wireless card -- an ASUS PCE-N15 (my Ethernet port is on the other side of my house, and I didn't want to buy/deal with a 50-foot cord.). The card is TECHNICALLY working... but I'm getting all of 1 Mb/s out of it. After a quick look around the forums, all I can tell is that this card is giving people grief and, I at least, didn't see a definitive solution listed anywhere.

I have the install disk, and have looked at the readme file but... frankly, what it's telling me to do is waaaaaay over my head. I need some help. To use a mathematical frame of reference, if this were an integral calculus problem, whoever wrote that readme completely skipped the "show your work" step on doing the integrals -- and I'm still working on learning derivatives.

"just go do this" ... yeah, um... ok... :confused::confused::confused::confused:

-- second note; the disk I have doesn't have the files listed in this readme EXACTLY per-say.
What I've got on the disk are the following:

rtl8192cfw.bin, rtl8192cfwU.bin, rtl8192cfwU_B.bin, rtl8192defw/bin, rtl8192defw_12.bin, rtl8192sefw.bin, and rtl8192sefw.old.bin.

I'm going to go out on a limb and guess that we wont be using the *.old.bin, but what do I know for sure anyway. Regardless, the readme only calls for 3 files of the above naming structures and I count... 6. :confused:

-- third note; I found the makefile script file... but dont know what to do with the thing. I've never coded before so... well... yeah, if I try anything the result is not going to be pretty. I'll include it here as well. Please let me know what to do.

~Q


Readme
[HR][/HR]
[PHP]Release Date: 2011-12-30, ver 0005
Realtek Linux mac80211 based driver:
   --This driver supports follwing RealTek PCIE Wireless LAN NICs:
	RTL8188CE/RTL8192CE
	RTL8191SE/RTL8192SE
	RTL8192DE

   --This driver supports follwing Linux OS:
 	Fedora Core
	Debian
	Mandriva
	Open SUSE
	Gentoo
	MeeGo
	android 2.2 (froyo-x86), etc.

   --This driver supports follwing kernel versions:
	1) kernel version >=2.6.35
	   you can build & install drvier use II. 


	2) kernel version [2.6.24, 2.6.34]
	   you can build & install drvier use III. 


========================================================================================
		I. Component 
========================================================================================
The driver is composed of several parts:
	1. Firmare to make nic work
           1.1 firmare/rtlwifi

	2. Module source code
	   2.1 ./*
	   2.2 rtl8192ce
	   2.2 rtl8192se
	   2.2 rtl8192de
	
	3. Script to build the modules
	   3.1 Makefile 

	4. compat-wireless
	   4.1 compat-wireless*.tar.bz2
	   4.2 compat

========================================================================================
		II. Compile & Installation & uninstall
========================================================================================
You can enter top-level directory of driver and execute follwing command to
Compile, Installation, or uninstall the driver:

	1. Change to Super User
	   sudo su

	2. Compile driver from the source code 
	   make

	3. Install the driver to the kernel
	   make install
	   reboot

	4. uninstall driver
	   make uninstall

========================================================================================
		III. Compile & Installation & uninstall [2.6.24, 2.6.34]
========================================================================================
We don't support kernel 2.6.24-2.6.34 directly, Because there are
lots of issues in mac80211 from kernel 2.6.24-2.6.34,
So we suggest you to use the latest kernel >= 2.6.35.

but if you want to use our driver in an old kernel,
you can use compat-wireless. this methord can support all kernel
versions higher than 2.6.24, and you can use all functions
of our driver like you use it in the latest kernel version.

You can get more informations of compat-wireless from:
[http://wireless.kernel.org/en/users/Download/stable](http://wireless.kernel.org/en/users/Download/stable)

you should use the following commands to Compile, Installation, or uninstall the driver:

	1. Change to Super User
	   sudo su

	2. install compat-wireless driver
	   ./compat/script/compat-install.sh
		 
	3. reboot
	   reboot

	4. uninstall driver
	   ./compat/script/compat-uninstall.sh

	5. you can get more information form follwing webset for how to use compat-wireless:
	   [http://wireless.kernel.org/en/users/Download/stable](http://wireless.kernel.org/en/users/Download/stable)
	   
NOTICE:
	1. Maybe you can not use other vendors wireless after you install compat wireless,
	   in this situation, you can uninstall compat-wireless use step 4 to recover it.

	2. This install methord can support all versions of kernel, not just 2.6.24-2.6.34,
	   you can also use it in the kernel higher than 2.6.35.
========================================================================================
				IV. Start Up Wireless
========================================================================================
You can use two methord to start up wireless:

	1. Install driver like II. and reboot OS, Wireless will be brought 
	   up by GUI, such as NetworkManager

	2. If Wireless is not brought up by GUI, you can use: 
	   ifconfig wlan0 up 

	   Note: some times when you have two wireless NICs on your computer,
		 interface "wlan0" may be changed to "wlan1" or "wlan2", etc. 
		 So before "ifconfig wlan0 up", you can use "iwconfig" to check
		 which interface our NIC is.

	   Note: Don't try to down driver by "ifconfig wlan0 down" when 
		 NetworkManager id opened, because NetworkManager will up
		 driver automatically. 

========================================================================================
				V. Wireless UI & NetworkManager 
========================================================================================
	1. All latest distributions have UI & NetworkManager to like with AP.
	   And it's more easy to link with AP than commandline,
	   So we suggest you use UI to link with AP.

	2. Don't try to like with AP use commandline with UI or NetworkManager opened.

	3. If you still used commandline to link with AP, Please check if
	   NetworkManager & wpa_supplicant is killed by follwing command:

		ps -x | grep NetworkManager
		ps -x | grep wpa_supplicant

	4. Follwing commandlines(V-VII) are all used under Linux without UI. 

========================================================================================
				VI. Set wireless lan MIBs  
========================================================================================
This driver uses Wireless Extension as an interface allowing you to set
Wireless LAN specific parameters.

	1. Current driver supports "iwlist" to show the device status of nic

	   iwlist wlan0 [parameters]

	   you can use follwing parameters:

        	parameter explaination      	[parameters]    
       		-----------------------     	-------------   
        	Show available chan and freq	freq / channel  
        	Show and Scan BSS and IBSS 	scan[ning]          
        	Show supported bit-rate         rate / bit[rate]        

	   For example:
		iwlist wlan0 channel
		iwlist wlan0 scan
		iwlist wlan0 rate

	2. Driver also supports "iwconfig", manipulate driver private ioctls, 
	   to set MIBs.

	   iwconfig wlan0 [parameters] [val]

	   you can use follwing parameters:

	   parameter explaination      [parameters]        [val] constraints
        	-----------------------     -------------        ------------------
        	Connect to AP by address    ap              	[mac_addr]
        	Set the essid, join (I)BSS  essid             	[essid]
        	Set operation mode          mode                {Managed|Ad-hoc}
        	Set keys and security mode  key/enc[ryption]    {N|open|restricted|off}

	   For example:
		iwconfig wlan0 ap XX:XX:XX:XX:XX:XX
		iwconfig wlan0 essid "ap_name"
		iwconfig wlan0 mode Ad-hoc
		iwconfig wlan0 essid "name" mode Ad-hoc
		iwconfig wlan0 key 0123456789 [2] open
		iwconfig wlan0 key off
		iwconfig wlan0 key restricted [3] 0123456789
        	iwconfig wlan0 key s:12345

	   Note: There are two types of key, "hex" code or "ascii" code. "hex" code
	        only contains hexadecimal characters, "ascii" code is consist of 
                "ascii" characters. Assume the "hex" code key is "0123456789", you 
                are suggested to use command like this "iwconfig wlan0 key 0123456789". 
                Assume the "ascii" code key is "12345", you should enter command 
                like this "iwconfig wlan0 key s:12345".

           Note: Better to set these MIBS without GUI such as NetworkManager and be 
	        sure that our nic has been brought up before these settings. WEP key
	        index 2-4 is not supportted by NetworkManager.

========================================================================================
				VII. Getting IP address (For OS without UI) 
========================================================================================
Before transmit/receive data, you should obtain an IP address use one of
the follwing method: 

	1. static IP address:

		ifconfig wlan0 IP_ADDRESS

	2. dynamic IP address using DHCP:
	   	
		dhclient wlan0
		

========================================================================================
				VIII. WPAPSK/WPA2PSK (For OS without UI) 
========================================================================================
Wpa_supplicant helps you to link with WPA/WPA2(include WPA Enterprise) AP, 
in Linux with NetworkManger & UI, UI will help you to link with AP, 
But if there is no UI & Networkmanger in your Linux, you can use 
follwing method to link with WPA/WPA2 AP. 
	
	1. we suppose that your Linux have installed wpa_supplicant & 
	   kernel build with WIRELESS_EXT, In fact, lots of distributions
	   have done like this.

	   But if some distribution not install wpa_supplicant,
	   please download wpa_supplicant from webset and install it.

	2. Edit wpa1.conf to set up SSID and its passphrase.
	   For example, the following setting in "wpa1.conf" 
	   means SSID to join is "BufAG54_Ch6" and its 
	   passphrase is "87654321".

	   network={
			ssid="BufAG54_Ch6"
			#scan_ssid=1 //see note 3
			proto=WPA
			key_mgmt=WPA-PSK
			pairwise=CCMP TKIP
			group=CCMP TKIP WEP104 WEP40
			psk="87654321"
			priority=2
		  }

	   You can download wpa_supplicant and read wpa_supplicant.conf 
	   for more examples.

	3. Execute WPA supplicant:

	   wpa_supplicant -D wext -c wpa1.conf -i wlan0 

	4. To see detailed description for driver interface and wpa_supplicant, 
	   please type: 

	   man wpa_supplicant[/PHP]

Makefile script
[HR][/HR]
[PHP]CC = gcc
KVER  := $(shell uname -r)
KSRC := /lib/modules/$(KVER)/build
MODDESTDIR := /lib/modules/$(KVER)/kernel/drivers/net/wireless/rtlwifi
FIRMWAREDIR := /lib/firmware/
PWD := $(shell pwd)
CLR_MODULE_FILES := *.mod.c *.mod *.o .*.cmd *.ko *~ .tmp_versions* modules.order Module.symvers
SYMBOL_FILE := Module.symvers

EXTRA_CFLAGS += -O2
obj-m := rtlwifi.o
PCI_MAIN_OBJS	:= base.o	\
		rc.o	\
		debug.o	\
		regd.o	\
		efuse.o	\
		cam.o	\
		ps.o	\
		core.o	\
		stats.o	\
		pci.o	\

rtlwifi-objs += $(PCI_MAIN_OBJS)

all: 
	$(MAKE) -C $(KSRC) M=$(PWD) modules
	@cp $(SYMBOL_FILE) rtl8192ce/
	@make -C rtl8192ce/
	@cp $(SYMBOL_FILE) rtl8192se/
	@make -C rtl8192se/
	@cp $(SYMBOL_FILE) rtl8192de/
	@make -C rtl8192de/
install: all
	find /lib/modules/$(shell uname -r) -name "r8192se_*.ko" -exec rm {} \;
	find /lib/modules/$(shell uname -r) -name "r8192ce_*.ko" -exec rm {} \;
	@rm -fr $(FIRMWAREDIR)/`uname -r`/rtlwifi

	$(shell rm -fr $(MODDESTDIR))
	$(shell mkdir $(MODDESTDIR))
	$(shell mkdir $(MODDESTDIR)/rtl8192se)
	$(shell mkdir $(MODDESTDIR)/rtl8192ce)
	$(shell mkdir $(MODDESTDIR)/rtl8192de)
	@install -p -m 644 rtlwifi.ko $(MODDESTDIR)	
	@install -p -m 644 ./rtl8192se/rtl8192se.ko $(MODDESTDIR)/rtl8192se
	@install -p -m 644 ./rtl8192ce/rtl8192ce.ko $(MODDESTDIR)/rtl8192ce
	@install -p -m 644 ./rtl8192de/rtl8192de.ko $(MODDESTDIR)/rtl8192de

	@depmod -a

	@#copy firmware img to target fold
	@#$(shell [ -d "$(FIRMWAREDIR)/`uname -r`" ] && cp -fr firmware/rtlwifi/ $(FIRMWAREDIR)/`uname -r`/.)
	@#$(shell [ ! -d "$(FIRMWAREDIR)/`uname -r`" ] && cp -fr firmware/rtlwifi/ $(FIRMWAREDIR)/.)
	@cp -fr firmware/rtlwifi/ $(FIRMWAREDIR)/

uninstall:
	$(shell [ -d "$(MODDESTDIR)" ] && rm -fr $(MODDESTDIR))
	
	@depmod -a
	
	@#delete the firmware img
	@rm -fr /lib/firmware/rtlwifi/
	@rm -fr /lib/firmware/`uname -r`/rtlwifi/

clean:
	rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
	rm -fr .tmp_versions
	rm -fr Modules.symvers
	rm -fr Module.symvers
	rm -fr Module.markers
	rm -fr modules.order
	rm -fr tags
	@find -name "tags" -exec rm {} \;
	@rm -fr $(CLR_MODULE_FILES)
	@make -C rtl8192ce/ clean
	@make -C rtl8192se/ clean
	@make -C rtl8192de/ clean[/PHP]

---

### Post by jackechanprime on 2014-10-09
Apologies, I made this post before I'd had my morning coffee. Can an admin please change the tag from ubuntu 10.04 to 14.04. Totally my screw up there.

---

### Post by weatherman2 on 2014-10-09
It appears the driver that came with the card is three years old.    The kernel driver probably used automatically is probably newer than the one on the disc, anyway.  I'd download the latest driver from Realtek and try to build that before I'd start playing with an old driver.

If you want additional help, you should find the sticky at the top of this forum and run the wireless script and post the results here - will provide lots more detail about your wireless card.

---

### Post by jackechanprime on 2014-10-09
Thanks for the direction to the sticky. Apparently I posted in the wrong forum too -- I wasn't awake this morning, let's leave it at that.](*,)

Anyway, here's the output from the disgnostic script in the sticky. Please. by all means, additional help! It appears that the script identified additional Mb/s modes available -- so how the blazes to I turn them ON?
[HR][/HR]
```


########## wireless info START ##########

Report from: 09 Oct 2014 17:22 PDT -0700

Booted last: 09 Oct 2014 10:07 PDT -0700

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
	Subsystem: ASUSTeK Computer Inc. Device [1043:859e]
	Kernel driver in use: r8169

06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178] (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device [1043:85e3]
	Kernel driver in use: rtl8192ce

##### lsusb #############################

Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 046d:c31d Logitech, Inc. Media Keyboard K200
Bus 003 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 003 Device 002: ID 04f9:025d Brother Industries, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              630653  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              484040  2 mac80211,rtlwifi
mxm_wmi                13021  1 nouveau
video                  19476  2 nouveau,asus_wmi
wmi                    19177  3 mxm_wmi,nouveau,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:******  Bcast:******  Mask:******
          inet6 addr: ****** Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:540407 errors:0 dropped:0 overruns:0 frame:0
          TX packets:376862 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:699663627 (699.6 MB)  TX bytes:33755776 (33.7 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:******  Bcast:******  Mask:******
          inet6 addr: ****** Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14670 errors:0 dropped:0 overruns:0 frame:0
          TX packets:326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:622639 (622.6 KB)  TX bytes:69755 (69.7 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"******"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC '******' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:24   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
*****               *****                *****                 UG    0      0        0 eth0
*****               *****                *****                  U     1      0        0 eth0
*****               *****                *****                  U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search gateway.2wire.net

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [******] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    NETGEAR45:       Infra, <MAC 'NETGEAR45' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 94 WPA2
    ATT368:          Infra, <MAC 'ATT368' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    ATT272:          Infra, <MAC 'ATT272' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    Router2:         Infra, <MAC 'Router2' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    suddenlink.net-2600: Infra, <MAC 'suddenlink.net-2600' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA2
    *******:       Infra, <MAC '******' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 86 WEP
    ATT800:          Infra, <MAC 'ATT800' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Zoey:            Infra, <MAC 'Zoey' [AC10]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    NETGEAR02:       Infra, <MAC 'NETGEAR02' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA2
    Scruffy Nerf-Herders: Infra, <MAC 'Scruffy Nerf-Herders' [AC9]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 34 WPA2
    ATT264:          Infra, <MAC 'ATT264' [AN12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    suddenlink.net-35E0: Infra, <MAC 'suddenlink.net-35E0' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 94 WPA WPA2

  IPv4 Settings:
    Address:         ******
    Prefix:          ******
    Gateway:         ******

    DNS:             ******

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         ******
    Prefix:          ******
    Gateway:         ******

    DNS:             ******

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

[[/etc/NetworkManager/system-connections/******]] (600 root)
[connection] id=****** | type=802-11-wireless
[802-11-wireless] ssid=****** | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     11 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

Channel occupancy:

      6   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      2   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC '*******' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"*********"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000eecdba
                    Extra: Last beacon: 92ms ago
          Cell 02 - Address: <MAC 'suddenlink.net-2600' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-2600"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001937c347af
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'ATT272' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"ATT272"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000016990e3d69
                    Extra: Last beacon: 148ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'RSS-351540' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"RSS-351540"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001937c36a4e
                    Extra: Last beacon: 908ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Router2' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Router2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000025a123e27d
                    Extra: Last beacon: 128ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'suddenlink.net-35E0' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-35E0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002dcc24f393
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'ATT368' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"ATT368"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001710af0504
                    Extra: Last beacon: 980ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'NETGEAR45' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR45"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000152d7a6b14b
                    Extra: Last beacon: 976ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'Scruffy Nerf-Herders' [AC9]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=22 dBm  
                    Encryption key:on
                    ESSID:"Scruffy Nerf-Herders"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000016863aa6246
                    Extra: Last beacon: 632ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'Zoey' [AC10]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"Zoey"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000193c70c287
                    Extra: Last beacon: 284ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'NETGEAR02' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR02"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001b7696dc71d
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'ATT800' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"ATT800"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000325013254
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192ce]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     EF063698748457BBEDB4633
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192ce]
debug: 0
fwlps: Y
ips: Y
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8178 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   12.199519] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   13.118671] wlan0: authenticate with <MAC '******' [AC1]>
[   13.123080] wlan0: send auth to <MAC '******' [AC1]> (try 1/3)
[   13.124943] wlan0: authenticated
[   13.124990] rtl8192ce 0000:06:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   13.124992] rtl8192ce 0000:06:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   13.124993] rtl8192ce 0000:06:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   13.128914] wlan0: associate with <MAC '******' [AC1]> (try 1/3)
[   13.133007] wlan0: RX AssocResp from <MAC '******' [AC1]> (capab=0x431 status=0 aid=1)
[   13.133105] wlan0: associated
[   13.133110] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   13.141016]  [<ffffffffa02dd3ad>] ? rtl_is_special_data+0x2d/0x110 [rtlwifi]

########## wireless info END ############


```

---

### Post by Hadaka on 2014-10-09
perhaps this may help.
[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

---

### Post by weatherman2 on 2014-10-09
You have a Realtek card that is using the rtl8192ce driver.

Fixes were suggested by people who have the same card:

[http://askubuntu.com/questions/414974/realtek-rtl8192ce-wireless-slow-intermittent-access?rq=1](http://askubuntu.com/questions/414974/realtek-rtl8192ce-wireless-slow-intermittent-access?rq=1)

---

### Post by jeremy31 on 2014-10-10
Change the router security to WPA2-AES and see if the speed improves

---

### Post by jackechanprime on 2014-10-10
Here's the terminal output for haduka's suggestion. cp'd before restart. lets see if this works... *restarts*
[HR][/HR]
```

qprime@Jcomp:~$ sudo apt-get install linux-headers-generic build-essential dkms
[sudo] password for qprime: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-generic is already the newest version.
linux-headers-generic set to manually installed.
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
Suggested packages:
  debhelper
The following NEW packages will be installed:
  dkms
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 64.4 kB of archives.
After this operation, 349 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/main dkms all 2.2.0.3-1.1ubuntu5 [64.4 kB]
Fetched 64.4 kB in 0s (105 kB/s)
Selecting previously unselected package dkms.
(Reading database ... 224673 files and directories currently installed.)
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up dkms (2.2.0.3-1.1ubuntu5) ...
qprime@Jcomp:~$ git clone https://github.com/pvaret/rtl8192cu-fixes.git
The program 'git' is currently not installed. You can install it by typing:
sudo apt-get install git
qprime@Jcomp:~$ sudo apt-get instal git
E: Invalid operation instal
qprime@Jcomp:~$ sudo apt-get install git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  git-man liberror-perl
Suggested packages:
  git-daemon-run git-daemon-sysvinit git-doc git-el git-email git-gui gitk
  gitweb git-arch git-bzr git-cvs git-mediawiki git-svn
The following NEW packages will be installed:
  git git-man liberror-perl
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,274 kB of archives.
After this operation, 21.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/main liberror-perl all 0.17-1.1 [21.1 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty/main git-man all 1:1.9.1-1 [698 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty/main git amd64 1:1.9.1-1 [2,555 kB]
Fetched 3,274 kB in 6s (513 kB/s)                                              
Selecting previously unselected package liberror-perl.
(Reading database ... 224720 files and directories currently installed.)
Preparing to unpack .../liberror-perl_0.17-1.1_all.deb ...
Unpacking liberror-perl (0.17-1.1) ...
Selecting previously unselected package git-man.
Preparing to unpack .../git-man_1%3a1.9.1-1_all.deb ...
Unpacking git-man (1:1.9.1-1) ...
Selecting previously unselected package git.
Preparing to unpack .../git_1%3a1.9.1-1_amd64.deb ...
Unpacking git (1:1.9.1-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up liberror-perl (0.17-1.1) ...
Setting up git-man (1:1.9.1-1) ...
Setting up git (1:1.9.1-1) ...
qprime@Jcomp:~$ git clone https://github.com/pvaret/rtl8192cu-fixes.git
Cloning into 'rtl8192cu-fixes'...
remote: Counting objects: 390, done.
remote: Total 390 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (390/390), 1.76 MiB | 546.00 KiB/s, done.
Resolving deltas: 100% (199/199), done.
Checking connectivity... done.
qprime@Jcomp:~$ sudo dkms add ./rtl8192cu-fixes

Creating symlink /var/lib/dkms/8192cu/1.9/source ->
                 /usr/src/8192cu-1.9

DKMS: add completed.
qprime@Jcomp:~$ sudo dkms install 8192cu/1.9

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.13.0-37-generic -C /lib/modules/3.13.0-37-generic/build M=/var/lib/dkms/8192cu/1.9/build........
cleaning build area....

DKMS: build completed.

8192cu.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-37-generic/updates/dkms/

depmod......

Backing up initrd.img-3.13.0-37-generic to /boot/initrd.img-3.13.0-37-generic.old-dkms
Making new initrd.img-3.13.0-37-generic
(If next boot fails, revert to initrd.img-3.13.0-37-generic.old-dkms image)
update-initramfs.......

DKMS: install completed.
qprime@Jcomp:~$ sudo depmod -a
qprime@Jcomp:~$ sudo cp ./rtl8192cu-fixes/blacklist-native-rtl8192.conf /etc/modprobe.d/
qprime@Jcomp:~$ sudo cp ./rtl8192cu-fixes/8192cu-disable-power-management.conf /etc/modprobe.d/
qprime@Jcomp:~$ 

```

---

### Post by jackechanprime on 2014-10-10
Nope, still at 1Mb/s

---

### Post by jackechanprime on 2014-10-10
Now trying the solution from Weatherman2's posted thread link:
[HR][/HR]
create /etc/modprobe.d/rtl8192ce.conf and add options rtl8192ce ips=0 fwlps=0 then reboot.

Rational behind this command; internal powersaving measures and firmware powersaving measures are enabled by default. This should turn them off. (hopefully).

---

### Post by jackechanprime on 2014-10-10
no gold. still at 1 mb/s

---

### Post by jackechanprime on 2014-10-10
Only available wep2 mode the router had was WPA2-PSK. Switching to that.

---

### Post by jackechanprime on 2014-10-10
okay.... and now I dont have any wireless at all. switching back to WPA did squat. Now the system tries to connect to wireless, and immediatly disconnects. I ran the sticky script again, and got this:

I somehow get the feeling that i've only made it worse.


```


########## wireless info START ##########

Report from: 10 Oct 2014 09:53 PDT -0700

Booted last: 10 Oct 2014 09:19 PDT -0700

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
	Subsystem: ASUSTeK Computer Inc. Device [1043:859e]
	Kernel driver in use: r8169

06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178] (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device [1043:85e3]
	Kernel driver in use: rtl8192ce

##### lsusb #############################

Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 046d:c31d Logitech, Inc. Media Keyboard K200
Bus 003 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 003 Device 002: ID 04f9:025d Brother Industries, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              630653  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              484040  2 mac80211,rtlwifi
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
mxm_wmi                13021  1 nouveau
video                  19476  2 nouveau,asus_wmi
wmi                    19177  3 mxm_wmi,nouveau,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::56a0:50ff:fe52:2723/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3522135 (3.5 MB)  TX bytes:528460 (528.4 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
********

##### resolv.conf #######################

nameserver 127.0.1.1
search gateway.2wire.net

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [********] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    NETGEAR45:       Infra, <MAC 'NETGEAR45' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 97 WPA2
    Zoey:            Infra, <MAC 'Zoey' [AC4]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    ATT800:          Infra, <MAC 'ATT800' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    Router2:         Infra, <MAC 'Router2' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA2
    ATT368:          Infra, <MAC 'ATT368' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    ATT272:          Infra, <MAC 'ATT272' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    NETGEAR02:       Infra, <MAC 'NETGEAR02' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AC11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA2
    suddenlink.net-2600: Infra, <MAC 'suddenlink.net-2600' [AC9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    ATT264:          Infra, <MAC 'ATT264' [AC13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    ATT152:          Infra, <MAC 'ATT152' [AC10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    ATT877:          Infra, <MAC 'ATT877' [AC12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    suddenlink.net-35E0: Infra, <MAC 'suddenlink.net-35E0' [AC14]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AC18]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 74 WPA2
    suddenlink.net-6A70: Infra, <MAC 'suddenlink.net-6A70' [AN15]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 34 WPA2
    ATT344:          Infra, <MAC 'ATT344' [AC15]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2
    suddenlink.net-18D0: Infra, <MAC 'suddenlink.net-18D0' [AN17]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 94 WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AN18]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 34 WPA2
    suddenlink.net-6CA0: Infra, <MAC 'suddenlink.net-6CA0' [AN19]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 84 WPA2
    suddenlink.net-C430: Infra, <MAC 'suddenlink.net-C430' [AN20]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 100 WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AN21]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2
    SUDDENLINK.NET-FDED: Infra, <MAC 'SUDDENLINK.NET-FDED' [AN22]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WEP
    Cisco31671:      Infra, <MAC 'Cisco31671' [AN23]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    ATT560:          Infra, <MAC 'ATT560' [AN24]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 94 WPA WPA2
    2WIRE305:        Infra, <MAC '2WIRE305' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WEP

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         ********
    Prefix:          ********
    Gateway:         ********

    DNS:             ********

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

[[/etc/NetworkManager/system-connections/2WIRE305]] (600 root)
[connection] id=2WIRE305 | type=802-11-wireless
[802-11-wireless] ssid=2WIRE305 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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

##### iwlist scan #######################

Channel occupancy:

      7   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.417 GHz (Channel 2)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      4   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Router2' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"Router2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000337d915914
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ATT272' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"ATT272"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000247550f730
                    Extra: Last beacon: 664ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'ATT368' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=16 dBm  
                    Encryption key:on
                    ESSID:"ATT368"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000024ed179fb3
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Zoey' [AC4]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"Zoey"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002718d5e152
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'NETGEAR45' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR45"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000160b4172a64
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'NETGEAR02' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR02"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001c54a326209
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'ATT800' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"ATT800"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000099167021
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC '********' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"********"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000dbe284b
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'suddenlink.net-2600' [AC9]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-2600"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002714369213
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'ATT152' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"ATT152"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001bafda22c5
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'RSS-351540' [AC11]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"RSS-351540"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000271436b311
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'ATT877' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"ATT877"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002bb02bd19
                    Extra: Last beacon: 29732ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'ATT264' [AC13]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"ATT264"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000014aeb650241
                    Extra: Last beacon: 14224ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'suddenlink.net-35E0' [AC14]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-35E0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ba87974a9
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'ATT344' [AC15]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"ATT344"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009129d1734
                    Extra: Last beacon: 4068ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'RSS-351540' [AC16]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"RSS-351540"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002712d50980
                    Extra: Last beacon: 3976ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'ATT152' [AC17]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"ATT152"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000206a5a2183
                    Extra: Last beacon: 3716ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'RSS-351540' [AC18]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"RSS-351540"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000271149b981
                    Extra: Last beacon: 736ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192ce]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     EF063698748457BBEDB4633
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192ce]
debug: 0
fwlps: N
ips: N
swenc: Y
swlps: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/8192cu-disable-power-management.conf]
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0

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

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

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

[/etc/modprobe.d/rtl8192.ce.conf]
options rtl8192ce ips=0 fwlps=0

[/etc/modprobe.d/rtl8192ce.conf]
options rtl8192ce swenc=1 ips=0

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8178 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  386.955382] rtl8192ce: rtl8192ce: Power Save off (module option)
[  386.955384] rtl8192ce: rtl8192ce: FW Power Save off (module option)
[  386.955389] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[  386.955747] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  386.956058] rtlwifi: wireless switch is on
[  387.301437] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  407.365756] wlan0: authenticate with <MAC '2WIRE305' [AC8]>
[  407.365884] wlan0: send auth to <MAC '2WIRE305' [AC8]> (try 1/3)
[  407.368108] wlan0: authenticated
[  412.388334] wlan0: deauthenticating from <MAC '2WIRE305' [AC8]> by local choice (reason=3)
[  412.388489] wlan0: authenticate with <MAC '2WIRE305' [AC8]>
[  412.388561] wlan0: send auth to <MAC '2WIRE305' [AC8]> (try 1/3)
[  412.391536] wlan0: authenticated
[  417.395860] wlan0: deauthenticating from <MAC '2WIRE305' [AC8]> by local choice (reason=3)
[  427.913223] wlan0: authenticate with <MAC '2WIRE305' [AC8]>
[  427.913336] wlan0: send auth to <MAC '2WIRE305' [AC8]> (try 1/3)
[  427.921002] wlan0: authenticated
[  432.925621] wlan0: deauthenticating from <MAC '2WIRE305' [AC8]> by local choice (reason=3)
[  443.949607] wlan0: authenticate with <MAC '2WIRE305' [AC8]>
[  443.949690] wlan0: send auth to <MAC '2WIRE305' [AC8]> (try 1/3)
[  443.958073] wlan0: authenticated
[  448.958514] wlan0: deauthenticating from <MAC '2WIRE305' [AC8]> by local choice (reason=3)
[  460.652712] wlan0: authenticate with <MAC '2WIRE305' [AC8]>
[  460.652808] wlan0: send auth to <MAC '2WIRE305' [AC8]> (try 1/3)
[  460.664319] wlan0: authenticated
[  465.665121] wlan0: deauthenticating from <MAC '2WIRE305' [AC8]> by local choice (reason=3)
[  485.703347] wlan0: authenticate with <MAC '2WIRE305' [AC8]>
[  485.703424] wlan0: send auth to <MAC '2WIRE305' [AC8]> (try 1/3)
[  485.707294] wlan0: authenticated
[  490.713953] wlan0: deauthenticating from <MAC '2WIRE305' [AC8]> by local choice (reason=3)
[  510.747009] wlan0: authenticate with <MAC '2WIRE305' [AC8]>
[  510.747096] wlan0: send auth to <MAC '2WIRE305' [AC8]> (try 1/3)
[  510.749075] wlan0: authenticated
[  515.763568] wlan0: deauthenticating from <MAC '2WIRE305' [AC8]> by local choice (reason=3)
[  529.464553] wlan0: authenticate with <MAC '2WIRE305' [AC8]>
[  529.464635] wlan0: send auth to <MAC '2WIRE305' [AC8]> (try 1/3)
[  529.467734] wlan0: authenticated
[  534.474276] wlan0: deauthenticating from <MAC '2WIRE305' [AC8]> by local choice (reason=3)
[  554.511718] wlan0: authenticate with <MAC '2WIRE305' [AC8]>
[  554.511815] wlan0: send auth to <MAC '2WIRE305' [AC8]> (try 1/3)
[  554.520696] wlan0: authenticated
[  559.521013] wlan0: deauthenticating from <MAC '2WIRE305' [AC8]> by local choice (reason=3)
[  579.553626] wlan0: authenticate with <MAC '2WIRE305' [AC8]>
[  579.553735] wlan0: send auth to <MAC '2WIRE305' [AC8]> (try 1/3)
[  579.557411] wlan0: authenticated
[  584.566061] wlan0: deauthenticating from <MAC '2WIRE305' [AC8]> by local choice (reason=3)
[  911.260926] wlan0: authenticate with <MAC '2WIRE305' [AC8]>
[  911.261018] wlan0: send auth to <MAC '2WIRE305' [AC8]> (try 1/3)
[  911.263085] wlan0: authenticated
[  916.276641] wlan0: deauthenticating from <MAC '2WIRE305' [AC8]> by local choice (reason=3)
[  936.270605] wlan0: authenticate with <MAC '2WIRE305' [AC8]>
[  936.270685] wlan0: send auth to <MAC '2WIRE305' [AC8]> (try 1/3)
[  936.278856] wlan0: authenticated
[  941.278522] wlan0: deauthenticating from <MAC '2WIRE305' [AC8]> by local choice (reason=3)
[  961.300442] wlan0: authenticate with <MAC '2WIRE305' [AC8]>
[  961.300522] wlan0: send auth to <MAC '2WIRE305' [AC8]> (try 1/3)
[  961.303236] wlan0: authenticated
[  966.310318] wlan0: deauthenticating from <MAC '2WIRE305' [AC8]> by local choice (reason=3)
[  986.338156] wlan0: authenticate with <MAC '2WIRE305' [AC8]>
[  986.338233] wlan0: send auth to <MAC '2WIRE305' [AC8]> (try 1/3)
[  986.342720] wlan0: authenticated
[  991.346087] wlan0: deauthenticating from <MAC '2WIRE305' [AC8]> by local choice (reason=3)
[ 1320.635603] wlan0: authenticate with <MAC '2WIRE305' [AC8]>
[ 1320.635701] wlan0: send auth to <MAC '2WIRE305' [AC8]> (try 1/3)
[ 1320.641885] wlan0: authenticated
[ 1325.645503] wlan0: deauthenticating from <MAC '2WIRE305' [AC8]> by local choice (reason=3)
[ 1345.658278] wlan0: authenticate with <MAC '2WIRE305' [AC8]>
[ 1345.658379] wlan0: send auth to <MAC '2WIRE305' [AC8]> (try 1/3)
[ 1345.661448] wlan0: authenticated
[ 1350.665083] wlan0: deauthenticating from <MAC '2WIRE305' [AC8]> by local choice (reason=3)
[ 1370.687510] wlan0: authenticate with <MAC '2WIRE305' [AC8]>
[ 1370.687593] wlan0: send auth to <MAC '2WIRE305' [AC8]> (try 1/3)
[ 1370.690158] wlan0: authenticated
[ 1375.697405] wlan0: deauthenticating from <MAC '2WIRE305' [AC8]> by local choice (reason=3)
[ 1395.723868] wlan0: authenticate with <MAC '2WIRE305' [AC8]>
[ 1395.723955] wlan0: send auth to <MAC '2WIRE305' [AC8]> (try 1/3)
[ 1395.728459] wlan0: authenticated
[ 1400.730668] wlan0: deauthenticating from <MAC '2WIRE305' [AC8]> by local choice (reason=3)
[ 1703.028963] wlan0: authenticate with <MAC '2WIRE305' [AC8]>
[ 1703.039068] wlan0: send auth to <MAC '2WIRE305' [AC8]> (try 1/3)
[ 1703.042384] wlan0: authenticated
[ 1708.048855] wlan0: deauthenticating from <MAC '2WIRE305' [AC8]> by local choice (reason=3)

########## wireless info END ############


```

---

### Post by jeremy31 on 2014-10-10
> **jackechanprime said:**
> okay.... and now I dont have any wireless at all. switching back to WPA did squat. Now the system tries to connect to wireless, and immediatly disconnects. I ran the sticky script again, and got this:

I somehow get the feeling that i've only made it worse.


Check what channel it is on now as this is from the script


Channel occupancy:

      7   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.417 GHz (Channel 2)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      4   APs on   Frequency:2.462 GHz (Channel 11)
And it might not hurt to delete the connection from Network Manager and add it back in

---

### Post by jackechanprime on 2014-10-12
Sorry for the down time there. Anyway, when I was in the router changing the encriptions/passwords I switched to channel 11, as there's 7 other people in my apartment using channel 1.

Either way, my computer seems to have now completely lost it's bead on the wireless network. It's showing last connection was 2 days ago at the moment. I tried deleting it, but I cant seem to add it back correctly. I have no idea what I screwed up.

heeeeeeeeeelp?

---

### Post by jeremy31 on 2014-10-12
If you can connect to the router with ethernet cable you should be able to make changes, even a reset of the router might help and put it back to factory settings

But is there anything here```
sudo cat [COLOR=#000000][FONT=Ubuntu Mono]/etc/NetworkManager/system-connections/2WIRE305
``` 
Do not post the contents as it should contain your password[/FONT][/COLOR]

---

### Post by weatherman2 on 2014-10-12
At worst, you can erase the file "/etc/modprobe.d/rtl8192ce.conf" you created and reboot to get the driver parameters back to the way it was originally:

```
sudo rm /etc/modprobe.d/rtl8192ce.conf
```

---

### Post by jackechanprime on 2014-10-12
On a side note, I'm dead sure that my wireless IS in fact working, this is the script outut for my laptop -- which is having no problem at all connecting even after I tinkered in the router. O.o My wifes computer however, is having a hairball over the whole thing... and if I dont get that fixed I might not live to make many more posts... *mumbles* "god... ****it... windows..."

Anyway, I hope there's some useful info in there.

```

########## wireless info START ##########

Report from: 12 Oct 2014 10:20 PDT -0700

Booted last: 11 Oct 2014 07:03 PDT -0700

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:30:01 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:0504]
	Kernel driver in use: tg3

03:00.0 Network controller [0280]: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e034]
	Kernel driver in use: ath9k

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:c218 Suyin Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

ath9k                 144602  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
mac80211              546051  1 ath9k
cfg80211              409394  3 ath,ath9k,mac80211
acer_wmi               31735  0 
mxm_wmi                12893  0 
sparse_keymap          13708  1 acer_wmi
wmi                    18673  2 acer_wmi,mxm_wmi
video                  18903  2 i915,acer_wmi

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
          inet addr:*****  Bcast:*****  Mask:*****
          inet6 addr: ***** Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:396639 errors:0 dropped:0 overruns:0 frame:0
          TX packets:270798 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:405335263 (405.3 MB)  TX bytes:36780399 (36.7 MB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"*****"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC '*****' [AC1]>   
          Bit Rate=12 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-24 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:111   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
*****

##### resolv.conf #######################

nameserver 127.0.1.1
search gateway.2wire.net

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [2WIRE305] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    NETGEAR45:       Infra, <MAC 'NETGEAR45' [AC16]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WPA2
    ATT800:          Infra, <MAC 'ATT800' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    ATT368:          Infra, <MAC 'ATT368' [AC14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    SUDDENLINK.NET-FDED: Infra, <MAC 'SUDDENLINK.NET-FDED' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WEP
    Router2:         Infra, <MAC 'Router2' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA2
    NETGEAR02:       Infra, <MAC 'NETGEAR02' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA2
    ATT264:          Infra, <MAC 'ATT264' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    ATT272:          Infra, <MAC 'ATT272' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    ATT448:          Infra, <MAC 'ATT448' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Scruffy Nerf-Herders: Infra, <MAC 'Scruffy Nerf-Herders' [AC18]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 32 WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AN11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    suddenlink.net-2FE0: Infra, <MAC 'suddenlink.net-2FE0' [AN12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    ATT264:          Infra, <MAC 'ATT264' [AN13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    ATT344:          Infra, <MAC 'ATT344' [AN14]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    ATT877:          Infra, <MAC 'ATT877' [AN15]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    ATT440:          Infra, <MAC 'ATT440' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AC20]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    ATT560:          Infra, <MAC 'ATT560' [AN18]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    suddenlink.net-6A70: Infra, <MAC 'suddenlink.net-6A70' [AC19]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2
    suddenlink.net-2600: Infra, <MAC 'suddenlink.net-2600' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2
    suddenlink.net-C430: Infra, <MAC 'suddenlink.net-C430' [AN22]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 32 WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AN23]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 27 WPA2
    suddenlink.net-35E0: Infra, <MAC 'suddenlink.net-35E0' [AN24]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    suddenlink.net-06F0: Infra, <MAC 'suddenlink.net-06F0' [AN25]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AN26]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AN27]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 25 WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AN28]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 27 WPA2
    ******:       Infra, <MAC '*****' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA
    suddenlink.net-2820: Infra, <MAC 'suddenlink.net-2820' [AN30]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 27 WPA2
    suddenlink.net-18D0: Infra, <MAC 'suddenlink.net-18D0' [AN31]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AN32]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    ATT440:          Infra, <MAC 'ATT440' [AN33]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    suddenlink.net-C410: Infra, <MAC 'suddenlink.net-C410' [AN34]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 29 WPA2
    Router, I hardly know her: Infra, <MAC 'Router, I hardly know her' [AN35]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    NoWorldOrder:    Infra, <MAC 'NoWorldOrder' [AN36]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2
    ATT952:          Infra, <MAC 'ATT952' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    ATT024:          Infra, <MAC 'ATT024' [AN38]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2

  IPv4 Settings:
    Address:         *****
    Prefix:          *****
    Gateway:         *****

    DNS:             *****

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/safewaywifi]] (600 root)
[connection] id=safewaywifi | type=802-11-wireless
[802-11-wireless] ssid=safewaywifi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto MOTOROLA-F4CD8]] (600 root)
[connection] id=Auto MOTOROLA-F4CD8 | type=802-11-wireless | permissions=user:qprime:;
[802-11-wireless] ssid=MOTOROLA-F4CD8
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Arcata Airport]] (600 root)
[connection] id=Arcata Airport | type=802-11-wireless
[802-11-wireless] ssid=Arcata Airport | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/5177 6347]] (600 root)
[connection] id=5177 6347 | type=802-11-wireless
[802-11-wireless] ssid=5177 6347 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Thug Life-guest]] (600 root)
[connection] id=Thug Life-guest | type=802-11-wireless
[802-11-wireless] ssid=Thug Life-guest | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/CableWiFi]] (600 root)
[connection] id=CableWiFi | type=802-11-wireless
[802-11-wireless] ssid=CableWiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/2WIRE240]] (600 root)
[connection] id=2WIRE240 | type=802-11-wireless
[802-11-wireless] ssid=2WIRE240 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/suddenlink.net-5CC0]] (600 root)
[connection] id=suddenlink.net-5CC0 | type=802-11-wireless
[802-11-wireless] ssid=suddenlink.net-5CC0 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/belkin54g]] (600 root)
[connection] id=belkin54g | type=802-11-wireless
[802-11-wireless] ssid=belkin54g | bssid=<MAC address> | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/SEATAC-FREE-WIFI]] (600 root)
[connection] id=SEATAC-FREE-WIFI | type=802-11-wireless
[802-11-wireless] ssid=SEATAC-FREE-WIFI | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Best_Western]] (600 root)
[connection] id=Best_Western | type=802-11-wireless
[802-11-wireless] ssid=Best_Western | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/2WIRE305]] (600 root)
[connection] id=2WIRE305 | type=802-11-wireless
[802-11-wireless] ssid=2WIRE305 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Als Test2]] (600 root)
[connection] id=Als Test2 | type=802-11-wireless
[802-11-wireless] ssid=Als Test2 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Vagabond Inn]] (600 root)
[connection] id=Vagabond Inn | type=802-11-wireless
[802-11-wireless] ssid=Vagabond Inn | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/2WIRE496]] (600 root)
[connection] id=2WIRE496 | type=802-11-wireless
[802-11-wireless] ssid=2WIRE496 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HSUWireless]] (600 root)
[connection] id=HSUWireless | type=802-11-wireless
[802-11-wireless] ssid=HSUWireless | mac-address=c0:f8:da:35:6:1c
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ZyXEL]] (600 root)
[connection] id=ZyXEL | type=802-11-wireless
[802-11-wireless] ssid=ZyXEL | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/SFO-WiFi]] (600 root)
[connection] id=SFO-WiFi | type=802-11-wireless
[802-11-wireless] ssid=SFO-WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Motel 6]] (600 root)
[connection] id=Motel 6 | type=802-11-wireless
[802-11-wireless] ssid=Motel 6 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/2WIRE844]] (600 root)
[connection] id=2WIRE844 | type=802-11-wireless
[802-11-wireless] ssid=2WIRE844 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/2WIRE013]] (600 root)
[connection] id=2WIRE013 | type=802-11-wireless
[802-11-wireless] ssid=2WIRE013 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Plazanet]] (600 root)
[connection] id=Plazanet | type=802-11-wireless
[802-11-wireless] ssid=Plazanet | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto 2WIRE305]] (600 root)
[connection] id=Auto 2WIRE305 | type=802-11-wireless | permissions=user:qprime:;
[802-11-wireless] ssid=2WIRE305
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     11 channels in total; available frequencies :
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
          Current Frequency=2.462 GHz (Channel 11)

##### iwlist scan #######################

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      10   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC '*****' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-17 dBm  
                    Encryption key:on
                    ESSID:"2WIRE305"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000004803095
                    Extra: Last beacon: 84ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ATT272' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"ATT272"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004d0de5d457
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'suddenlink.net-2600' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-2600"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004fac9e1f2a
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'RSS-351540' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"RSS-351540"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004fac9e4d7d
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Router2' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"Router2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f215ba821
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'SUDDENLINK.NET-FDED' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"SUDDENLINK.NET-FDED"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000014a84922b0
                    Extra: Last beacon: 84ms ago
          Cell 07 - Address: <MAC 'ATT800' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"ATT800"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000029317cb45e
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'NETGEAR02' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR02"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001edef754db1
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'ATT440' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"ATT440"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001f2c735183
                    Extra: Last beacon: 568ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'ATT264' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"ATT264"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000211cbb2a818
                    Extra: Last beacon: 204ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'ATT952' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"ATT952"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000785a0f183
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'ATT448' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"ATT448"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002139fe6183
                    Extra: Last beacon: 1468ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'Zoey' [AC13]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"Zoey"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004fb1455a60
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'ATT368' [AC14]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"ATT368"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000008ab2ee224
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'ATT056' [AC15]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"ATT056"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003322cd5183
                    Extra: Last beacon: 1048ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'NETGEAR45' [AC16]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR45"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001894c743e58
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'RSS-351540' [AC17]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"RSS-351540"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000048fc713978
                    Extra: Last beacon: 708ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'Scruffy Nerf-Herders' [AC18]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Scruffy Nerf-Herders"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000019ed88d4f28
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'suddenlink.net-6A70' [AC19]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-6A70"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c5a5344ba
                    Extra: Last beacon: 612ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'RSS-351540' [AC20]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"RSS-351540"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c5a598a92
                    Extra: Last beacon: 200ms ago
                    lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DF02272C2FA4678C49046E5
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        7A:CF:8E:D9:48:D7:7B:6A:80:F2:4F:59:D5:D8:ED:03:87:AA:B4:26
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        7A:CF:8E:D9:48:D7:7B:6A:80:F2:4F:59:D5:D8:ED:03:87:AA:B4:26
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        7A:CF:8E:D9:48:D7:7B:6A:80:F2:4F:59:D5:D8:ED:03:87:AA:B4:26
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        7A:CF:8E:D9:48:D7:7B:6A:80:F2:4F:59:D5:D8:ED:03:87:AA:B4:26
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        7A:CF:8E:D9:48:D7:7B:6A:80:F2:4F:59:D5:D8:ED:03:87:AA:B4:26
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        7A:CF:8E:D9:48:D7:7B:6A:80:F2:4F:59:D5:D8:ED:03:87:AA:B4:26
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp

##### modprobe options ##################

[/etc/modprobe.d/bbswitch.conf]
options bbswitch load_state=0 unload_state=1

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
blacklist vga16fb
blacklist rivafb
blacklist rivatv
blacklist nvidiafb
blacklist nvidia-173
blacklist nvidia-96

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
options iwlwifi 11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x16b5 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002e (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[43249.035397] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[43249.035400] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[43249.037465] wlan0: associate with <MAC '2WIRE305' [AC1]> (try 1/3)
[43249.040473] wlan0: RX AssocResp from <MAC '2WIRE305' [AC1]> (capab=0x431 status=0 aid=1)
[43249.040761] wlan0: associated
[43249.043383] ath: EEPROM regdomain: 0x8348
[43249.043387] ath: EEPROM indicates we should expect a country code
[43249.043388] ath: doing EEPROM country->regdmn map search
[43249.043390] ath: country maps to regdmn code: 0x3a
[43249.043392] ath: Country alpha2 being used: US
[43249.043393] ath: Regpair used: 0x3a
[43249.043395] ath: regdomain 0x8348 dynamically updated by country IE
[97942.156399] wlan0: deauthenticated from <MAC '2WIRE305' [AC1]> (Reason: 3)
[97943.113268] wlan0: authenticate with <MAC '2WIRE305' [AC1]>
[97943.130011] wlan0: send auth to <MAC '2WIRE305' [AC1]> (try 1/3)
[97943.134342] wlan0: authenticated
[97943.134510] ath9k 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[97943.134514] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[97943.134517] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[97943.137839] wlan0: associate with <MAC '2WIRE305' [AC1]> (try 1/3)
[97943.140863] wlan0: RX AssocResp from <MAC '2WIRE305' [AC1]> (capab=0x431 status=0 aid=1)
[97943.141189] wlan0: associated
[97943.144315] ath: EEPROM regdomain: 0x8348
[97943.144319] ath: EEPROM indicates we should expect a country code
[97943.144320] ath: doing EEPROM country->regdmn map search
[97943.144322] ath: country maps to regdmn code: 0x3a
[97943.144324] ath: Country alpha2 being used: US
[97943.144325] ath: Regpair used: 0x3a
[97943.144327] ath: regdomain 0x8348 dynamically updated by country IE
[97946.178265] wlan0: deauthenticated from <MAC '2WIRE305' [AC1]> (Reason: 2)
[97954.502248] wlan0: authenticate with <MAC '2WIRE305' [AC1]>
[97954.520482] wlan0: send auth to <MAC '2WIRE305' [AC1]> (try 1/3)
[97954.523221] wlan0: authenticated
[97954.523394] ath9k 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[97954.523399] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[97954.523403] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[97954.524219] wlan0: associate with <MAC '2WIRE305' [AC1]> (try 1/3)
[97954.527273] wlan0: RX AssocResp from <MAC '2WIRE305' [AC1]> (capab=0x431 status=0 aid=1)
[97954.527617] wlan0: associated
[97954.531924] ath: EEPROM regdomain: 0x8348
[97954.531929] ath: EEPROM indicates we should expect a country code
[97954.531932] ath: doing EEPROM country->regdmn map search
[97954.531934] ath: country maps to regdmn code: 0x3a
[97954.531937] ath: Country alpha2 being used: US
[97954.531939] ath: Regpair used: 0x3a
[97954.531941] ath: regdomain 0x8348 dynamically updated by country IE

########## wireless info END ############

```

---

### Post by jackechanprime on 2014-10-12
In response to weatherman2's post, I ran that code and... well, nothing happened. Card is still not connecting.

Here's the current wireless script output for my tower. Again, hope there's something useful.

```


########## wireless info START ##########

Report from: 12 Oct 2014 10:37 PDT -0700

Booted last: 10 Oct 2014 09:19 PDT -0700

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
	Subsystem: ASUSTeK Computer Inc. Device [1043:859e]
	Kernel driver in use: r8169

06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178] (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device [1043:85e3]
	Kernel driver in use: rtl8192ce

##### lsusb #############################

Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 046d:c31d Logitech, Inc. Media Keyboard K200
Bus 003 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 003 Device 002: ID 04f9:025d Brother Industries, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              630653  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              484040  2 mac80211,rtlwifi
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
mxm_wmi                13021  1 nouveau
video                  19476  2 nouveau,asus_wmi
wmi                    19177  3 mxm_wmi,nouveau,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:*****  Bcast:*****  Mask:*****
          inet6 addr: ***** Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1069813 errors:0 dropped:0 overruns:0 frame:0
          TX packets:792403 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:978876091 (978.8 MB)  TX bytes:60532791 (60.5 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
*****

##### resolv.conf #######################

nameserver 127.0.1.1
search gateway.2wire.net

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    NETGEAR45:       Infra, <MAC 'NETGEAR45' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 97 WPA2
    Zoey:            Infra, <MAC 'Zoey' [AC3]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    ATT800:          Infra, <MAC 'ATT800' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    Router2:         Infra, <MAC 'Router2' [AC12]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA2
    ATT368:          Infra, <MAC 'ATT368' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    ATT272:          Infra, <MAC 'ATT272' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    NETGEAR02:       Infra, <MAC 'NETGEAR02' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AC9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2
    suddenlink.net-2600: Infra, <MAC 'suddenlink.net-2600' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA2
    ATT264:          Infra, <MAC 'ATT264' [AC10]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    ATT877:          Infra, <MAC 'ATT877' [AC17]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    OXKINKXO:        Infra, <MAC 'OXKINKXO' [AC14]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 37 WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AN13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2
    ATT560:          Infra, <MAC 'ATT560' [AN14]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 26 WPA WPA2
    ATT264:          Infra, <MAC 'ATT264' [AN15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    ATT152:          Infra, <MAC 'ATT152' [AC11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    suddenlink.net-0EA0: Infra, <MAC 'suddenlink.net-0EA0' [AN17]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 18 WPA2
    suddenlink.net-18D0: Infra, <MAC 'suddenlink.net-18D0' [AN18]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA2
    suddenlink.net-C430: Infra, <MAC 'suddenlink.net-C430' [AN19]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 40 WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AN20]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2
    suddenlink.net-BBE0: Infra, <MAC 'suddenlink.net-BBE0' [AN21]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 18 WPA2
    suddenlink.net-31B4: Infra, <MAC 'suddenlink.net-31B4' [AN22]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    ATT848:          Infra, <MAC 'ATT848' [AN23]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    *****:        Infra, <MAC '*****' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WEP
    RSS-351540:      Infra, <MAC 'RSS-351540' [AN25]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AC16]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 44 WPA2
    suddenlink.net-7580: Infra, <MAC 'suddenlink.net-7580' [AN27]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2
    ATT024:          Infra, <MAC 'ATT024' [AC13]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    SUDDENLINK.NET-FDED: Infra, <MAC 'SUDDENLINK.NET-FDED' [AC15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WEP

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         *****
    Prefix:          *****
    Gateway:         *****

    DNS:             *****

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

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=802-11-wireless
[802-11-wireless] ssid=2WIRE305
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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

##### iwlist scan #######################

Channel occupancy:

      6   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      4   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC '*****' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"*****"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000003f5c12
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'NETGEAR45' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR45"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001898a82a1b3
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Zoey' [AC3]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=70/70  Signal level=16 dBm  
                    Encryption key:on
                    ESSID:"Zoey"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004fef4956ab
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'NETGEAR02' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR02"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001ee2d8d0051
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'ATT800' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=18 dBm  
                    Encryption key:on
                    ESSID:"ATT800"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000296f80c118
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'ATT272' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"ATT272"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004d4bf8f9e3
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'ATT368' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"ATT368"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000008e796dcc0
                    Extra: Last beacon: 476ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'suddenlink.net-2600' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=26 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-2600"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004feab15044
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'RSS-351540' [AC9]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"RSS-351540"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004fe9103399
                    Extra: Last beacon: 27344ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'ATT264' [AC10]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=16 dBm  
                    Encryption key:on
                    ESSID:"ATT264"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000173c113b8f7
                    Extra: Last beacon: 27344ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'ATT152' [AC11]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=18 dBm  
                    Encryption key:on
                    ESSID:"ATT152"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000019f82633c7
                    Extra: Last beacon: 832ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'Router2' [AC12]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"Router2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f5f6eb4a3
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'ATT024' [AC13]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"ATT024"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000406bcf2183
                    Extra: Last beacon: 496ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'OXKINKXO' [AC14]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"OXKINKXO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000080e68d80
                    Extra: Last beacon: 28028ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'SUDDENLINK.NET-FDED' [AC15]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"SUDDENLINK.NET-FDED"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000014e4ac49e8
                    Extra: Last beacon: 27344ms ago
          Cell 16 - Address: <MAC 'RSS-351540' [AC16]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"RSS-351540"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000493a78ea4c
                    Extra: Last beacon: 532ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'ATT877' [AC17]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=16 dBm  
                    Encryption key:on
                    ESSID:"ATT877"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001f2e6f2215
                    Extra: Last beacon: 516ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192ce]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     EF063698748457BBEDB4633
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192ce]
debug: 0
fwlps: N
ips: N
swenc: Y
swlps: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/8192cu-disable-power-management.conf]
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0

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

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

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

[/etc/modprobe.d/rtl8192.ce.conf]
options rtl8192ce ips=0 fwlps=0

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8178 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  911.260926] wlan0: authenticate with <MAC '2WIRE305' [AC1]>
[  911.261018] wlan0: send auth to <MAC '2WIRE305' [AC1]> (try 1/3)
[  911.263085] wlan0: authenticated
[  916.276641] wlan0: deauthenticating from <MAC '2WIRE305' [AC1]> by local choice (reason=3)
[  936.270605] wlan0: authenticate with <MAC '2WIRE305' [AC1]>
[  936.270685] wlan0: send auth to <MAC '2WIRE305' [AC1]> (try 1/3)
[  936.278856] wlan0: authenticated
[  941.278522] wlan0: deauthenticating from <MAC '2WIRE305' [AC1]> by local choice (reason=3)
[  961.300442] wlan0: authenticate with <MAC '2WIRE305' [AC1]>
[  961.300522] wlan0: send auth to <MAC '2WIRE305' [AC1]> (try 1/3)
[  961.303236] wlan0: authenticated
[  966.310318] wlan0: deauthenticating from <MAC '2WIRE305' [AC1]> by local choice (reason=3)
[  986.338156] wlan0: authenticate with <MAC '2WIRE305' [AC1]>
[  986.338233] wlan0: send auth to <MAC '2WIRE305' [AC1]> (try 1/3)
[  986.342720] wlan0: authenticated
[  991.346087] wlan0: deauthenticating from <MAC '2WIRE305' [AC1]> by local choice (reason=3)
[ 1320.635603] wlan0: authenticate with <MAC '2WIRE305' [AC1]>
[ 1320.635701] wlan0: send auth to <MAC '2WIRE305' [AC1]> (try 1/3)
[ 1320.641885] wlan0: authenticated
[ 1325.645503] wlan0: deauthenticating from <MAC '2WIRE305' [AC1]> by local choice (reason=3)
[ 1345.658278] wlan0: authenticate with <MAC '2WIRE305' [AC1]>
[ 1345.658379] wlan0: send auth to <MAC '2WIRE305' [AC1]> (try 1/3)
[ 1345.661448] wlan0: authenticated
[ 1350.665083] wlan0: deauthenticating from <MAC '2WIRE305' [AC1]> by local choice (reason=3)
[ 1370.687510] wlan0: authenticate with <MAC '2WIRE305' [AC1]>
[ 1370.687593] wlan0: send auth to <MAC '2WIRE305' [AC1]> (try 1/3)
[ 1370.690158] wlan0: authenticated
[ 1375.697405] wlan0: deauthenticating from <MAC '2WIRE305' [AC1]> by local choice (reason=3)
[ 1395.723868] wlan0: authenticate with <MAC '2WIRE305' [AC1]>
[ 1395.723955] wlan0: send auth to <MAC '2WIRE305' [AC1]> (try 1/3)
[ 1395.728459] wlan0: authenticated
[ 1400.730668] wlan0: deauthenticating from <MAC '2WIRE305' [AC1]> by local choice (reason=3)
[ 1703.028963] wlan0: authenticate with <MAC '2WIRE305' [AC1]>
[ 1703.039068] wlan0: send auth to <MAC '2WIRE305' [AC1]> (try 1/3)
[ 1703.042384] wlan0: authenticated
[ 1708.048855] wlan0: deauthenticating from <MAC '2WIRE305' [AC1]> by local choice (reason=3)

########## wireless info END ############

```

---

### Post by jackechanprime on 2014-10-13
I'm sorry, I forgot to reboot afterwards. Connection established, remains throttled at 1Mb/s.

Any more ideas?

---

### Post by jeremy31 on 2014-10-13
I would find a wifi card with an Intel chipset, should be quite a few cheap on ebay but don't buy one of the antique 3945 or 4965 models

---

### Post by wildmanne39 on 2014-10-13
Why did you have an atheros card showing in one script posting? You do  not need to remove data from the file before posting it, all the sensitive information that matter has already been removed you are just removing information needed to help fix your issue.
Thanks

---

### Post by wildmanne39 on 2014-10-13
I know you have tried some of the things that are in the link that I am going to post, please do exactly as the post says and remove any files that are not what I have listed in the link.
[http://askubuntu.com/questions/504777/unstable-wireless-connection-in-ubuntu-14-04/505246#505246](http://askubuntu.com/questions/504777/unstable-wireless-connection-in-ubuntu-14-04/505246#505246)
If this does not help then you can install a new driver if the kernel bug has been fixed which I think it has.
[http://askubuntu.com/questions/486350/rtl8192ce-connection-drops-and-fluctuation-on-desktop-with-14-04-64bit-with-enco/486931#486931](http://askubuntu.com/questions/486350/rtl8192ce-connection-drops-and-fluctuation-on-desktop-with-14-04-64bit-with-enco/486931#486931)
Thanks

---

### Post by jackechanprime on 2014-10-18
Again apologies for popping in and out. Student life, gotta pick your battles. You know how it is.

Anyway...

> Why did you have an atheros card showing in one script posting? You do not need to remove data from the file before posting it, all the sensitive information that matter has already been removed you are just removing information needed to help fix your issue.
Thanks 

^^ The atheros was from from my laptop -- just demonstrating that another machine was actually succeeding at using my wifi.

All I removed from the script outputs was IP addresses, DNS, etc. And my router's name itself. I figured that wouldn't be "required" one way or the other, so I chose to pull it. If you really need it, let me know and I'll put an untouched one up.

As for this card being an antique... it was actually free. Consolation prize for horrible incompetence at the business where I bought this computer. I'm not even going to BEGIN to rant about how badly they f**d the order up -- but lets say that I should have asked for more either way. :roll: Figures they'd give me something cheep though.

I'll try your links now, and hope for the best.

---

### Post by jackechanprime on 2014-10-18
Ok, link 1)

> First in your router change 802.11bgn to 802.11bg.

Second change the wpa/wpa2 encryption to just wpa2 (CCMP)(AES) not (TKIP) if you have that option it will work best.

Third set your wireless channel in the router to 1 or 11 then save the router configuration and reboot it.

Fourth go into network manager at top right corner of the screen and click on edit connections>wireless tab and set IPV6 to ignore.

Fifth open the terminal CTRL+ALT+_T then copy and paste the following code one line at a time for accuracy:

echo "options rtl8192ce swenc=1 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce


Step 1) Router already on this setting
Step 2) Changing to WPA2-PSK (only available only-WPA2 option)
Step 3) Channel set to 11
Step 4) IPV6 disabled/ignored.
Step 5)

Command 1 outputs:
[PHP]
options rtl8192ce swenc=1 ips=0
[/PHP]

Command 2 outputs:
[PHP]
rmmod rtl8192ce
rmmod rtl8192c_common
rmmod rtl_pci
rmmod rtlwifi
rmmod mac80211
rmmod cfg80211
[/PHP]

Command 3 outputs:
[PHP]
insmod /lib/modules/3.13.0-37-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.13.0-37-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko 
insmod /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko 
insmod /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko 
insmod /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko ips=0 fwlps=0 swenc=1 ips=0
[/PHP]

I await further instructions oh wise ones... because I have no idea what most of that means.

---

### Post by jackechanprime on 2014-10-18
Something in that pack of tricks has caused the wireless link to fail. Why, I don't know. I'll try the new driver install now, since link 1 made things worse. (again).

Heres the terminal input/output for the pre-reboot part if that's at all helpful:

```

qprime@Jcomp:~$ sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 4 reinstalled, 0 to remove and 0 not upgraded.
Need to get 69.3 kB/793 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main build-essential amd64 11.6ubuntu6 [4,838 B]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main dkms all 2.2.0.3-1.1ubuntu5 [64.4 kB]
Fetched 69.3 kB in 0s (107 kB/s)
(Reading database ... 225468 files and directories currently installed.)
Preparing to unpack .../build-essential_11.6ubuntu6_amd64.deb ...
Unpacking build-essential (11.6ubuntu6) over (11.6ubuntu6) ...
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5) over (2.2.0.3-1.1ubuntu5) ...
Preparing to unpack .../linux-headers-3.13.0-37-generic_3.13.0-37.64_amd64.deb ...
Unpacking linux-headers-3.13.0-37-generic (3.13.0-37.64) over (3.13.0-37.64) ...
Preparing to unpack .../linux-headers-generic_3.13.0.37.44_amd64.deb ...
Unpacking linux-headers-generic (3.13.0.37.44) over (3.13.0.37.44) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up build-essential (11.6ubuntu6) ...
Setting up dkms (2.2.0.3-1.1ubuntu5) ...
Setting up linux-headers-3.13.0-37-generic (3.13.0-37.64) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
Setting up linux-headers-generic (3.13.0.37.44) ...
qprime@Jcomp:~$ cd ~/Downloads/backports-3.16-rc1-1
qprime@Jcomp:~/Downloads/backports-3.16-rc1-1$ make defconfig-rtlwifi
Generating local configuration database from kernel ... done.
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o zconf.tab.o zconf.tab.c
cc   conf.o zconf.tab.o   -o conf
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
qprime@Jcomp:~/Downloads/backports-3.16-rc1-1$ make
make[5]: `conf' is up to date.
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
Building backport-include/backport/autoconf.h ... done.
  CC [M]  /home/qprime/Downloads/backports-3.16-rc1-1/compat/main.o
  CC [M]  /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.14.o
  CC [M]  /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.o
In file included from include/net/snmp.h:52:0,
                 from include/net/netns/mib.h:4,
                 from include/net/net_namespace.h:13,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/u64_stats_sync.h:117:28: error: redefinition of ‘u64_stats_fetch_begin_irq’
 static inline unsigned int u64_stats_fetch_begin_irq(const struct u64_stats_sync *syncp)
                            ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/u64_stats_sync.h:6:0,
                 from include/net/snmp.h:52,
                 from include/net/netns/mib.h:4,
                 from include/net/net_namespace.h:13,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/u64_stats_sync.h:122:28: note: previous definition of ‘u64_stats_fetch_begin_irq’ was here
 static inline unsigned int u64_stats_fetch_begin_irq(const struct u64_stats_sync *syncp)
                            ^
In file included from include/net/snmp.h:52:0,
                 from include/net/netns/mib.h:4,
                 from include/net/net_namespace.h:13,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/u64_stats_sync.h:129:20: error: redefinition of ‘u64_stats_fetch_retry_irq’
 static inline bool u64_stats_fetch_retry_irq(const struct u64_stats_sync *syncp,
                    ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/u64_stats_sync.h:6:0,
                 from include/net/snmp.h:52,
                 from include/net/netns/mib.h:4,
                 from include/net/net_namespace.h:13,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/u64_stats_sync.h:134:20: note: previous definition of ‘u64_stats_fetch_retry_irq’ was here
 static inline bool u64_stats_fetch_retry_irq(const struct u64_stats_sync *syncp,
                    ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:357:6: error: nested redefinition of ‘enum pkt_hash_types’
 enum pkt_hash_types {
      ^
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:357:6: error: redeclaration of ‘enum pkt_hash_types’
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:732:6: note: originally defined here
 enum pkt_hash_types {
      ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:358:2: error: redeclaration of enumerator ‘PKT_HASH_TYPE_NONE’
  PKT_HASH_TYPE_NONE, /* Undefined type */
  ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:733:2: note: previous definition of ‘PKT_HASH_TYPE_NONE’ was here
  PKT_HASH_TYPE_NONE, /* Undefined type */
  ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:359:2: error: redeclaration of enumerator ‘PKT_HASH_TYPE_L2’
  PKT_HASH_TYPE_L2, /* Input: src_MAC, dest_MAC */
  ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:734:2: note: previous definition of ‘PKT_HASH_TYPE_L2’ was here
  PKT_HASH_TYPE_L2, /* Input: src_MAC, dest_MAC */
  ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:360:2: error: redeclaration of enumerator ‘PKT_HASH_TYPE_L3’
  PKT_HASH_TYPE_L3, /* Input: src_IP, dst_IP */
  ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:735:2: note: previous definition of ‘PKT_HASH_TYPE_L3’ was here
  PKT_HASH_TYPE_L3, /* Input: src_IP, dst_IP */
  ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:361:2: error: redeclaration of enumerator ‘PKT_HASH_TYPE_L4’
  PKT_HASH_TYPE_L4, /* Input: src_IP, dst_IP, src_port, dst_port */
  ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:736:2: note: previous definition of ‘PKT_HASH_TYPE_L4’ was here
  PKT_HASH_TYPE_L4, /* Input: src_IP, dst_IP, src_port, dst_port */
  ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:365:1: error: redefinition of ‘skb_set_hash’
 skb_set_hash(struct sk_buff *skb, __u32 hash, enum pkt_hash_types type)
 ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:740:1: note: previous definition of ‘skb_set_hash’ was here
 skb_set_hash(struct sk_buff *skb, __u32 hash, enum pkt_hash_types type)
 ^
make[6]: *** [/home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.o] Error 1
make[5]: *** [/home/qprime/Downloads/backports-3.16-rc1-1/compat] Error 2
make[4]: *** [_module_/home/qprime/Downloads/backports-3.16-rc1-1] Error 2
make[3]: *** [modules] Error 2
make[2]: *** [modules] Error 2
make[1]: *** [modules] Error 2
make: *** [default] Error 2
qprime@Jcomp:~/Downloads/backports-3.16-rc1-1$ sudo make install
  CC [M]  /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.o
In file included from include/net/snmp.h:52:0,
                 from include/net/netns/mib.h:4,
                 from include/net/net_namespace.h:13,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/u64_stats_sync.h:117:28: error: redefinition of ‘u64_stats_fetch_begin_irq’
 static inline unsigned int u64_stats_fetch_begin_irq(const struct u64_stats_sync *syncp)
                            ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/u64_stats_sync.h:6:0,
                 from include/net/snmp.h:52,
                 from include/net/netns/mib.h:4,
                 from include/net/net_namespace.h:13,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/u64_stats_sync.h:122:28: note: previous definition of ‘u64_stats_fetch_begin_irq’ was here
 static inline unsigned int u64_stats_fetch_begin_irq(const struct u64_stats_sync *syncp)
                            ^
In file included from include/net/snmp.h:52:0,
                 from include/net/netns/mib.h:4,
                 from include/net/net_namespace.h:13,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/u64_stats_sync.h:129:20: error: redefinition of ‘u64_stats_fetch_retry_irq’
 static inline bool u64_stats_fetch_retry_irq(const struct u64_stats_sync *syncp,
                    ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/u64_stats_sync.h:6:0,
                 from include/net/snmp.h:52,
                 from include/net/netns/mib.h:4,
                 from include/net/net_namespace.h:13,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/u64_stats_sync.h:134:20: note: previous definition of ‘u64_stats_fetch_retry_irq’ was here
 static inline bool u64_stats_fetch_retry_irq(const struct u64_stats_sync *syncp,
                    ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:357:6: error: nested redefinition of ‘enum pkt_hash_types’
 enum pkt_hash_types {
      ^
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:357:6: error: redeclaration of ‘enum pkt_hash_types’
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:732:6: note: originally defined here
 enum pkt_hash_types {
      ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:358:2: error: redeclaration of enumerator ‘PKT_HASH_TYPE_NONE’
  PKT_HASH_TYPE_NONE, /* Undefined type */
  ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:733:2: note: previous definition of ‘PKT_HASH_TYPE_NONE’ was here
  PKT_HASH_TYPE_NONE, /* Undefined type */
  ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:359:2: error: redeclaration of enumerator ‘PKT_HASH_TYPE_L2’
  PKT_HASH_TYPE_L2, /* Input: src_MAC, dest_MAC */
  ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:734:2: note: previous definition of ‘PKT_HASH_TYPE_L2’ was here
  PKT_HASH_TYPE_L2, /* Input: src_MAC, dest_MAC */
  ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:360:2: error: redeclaration of enumerator ‘PKT_HASH_TYPE_L3’
  PKT_HASH_TYPE_L3, /* Input: src_IP, dst_IP */
  ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:735:2: note: previous definition of ‘PKT_HASH_TYPE_L3’ was here
  PKT_HASH_TYPE_L3, /* Input: src_IP, dst_IP */
  ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:361:2: error: redeclaration of enumerator ‘PKT_HASH_TYPE_L4’
  PKT_HASH_TYPE_L4, /* Input: src_IP, dst_IP, src_port, dst_port */
  ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:736:2: note: previous definition of ‘PKT_HASH_TYPE_L4’ was here
  PKT_HASH_TYPE_L4, /* Input: src_IP, dst_IP, src_port, dst_port */
  ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:365:1: error: redefinition of ‘skb_set_hash’
 skb_set_hash(struct sk_buff *skb, __u32 hash, enum pkt_hash_types type)
 ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:740:1: note: previous definition of ‘skb_set_hash’ was here
 skb_set_hash(struct sk_buff *skb, __u32 hash, enum pkt_hash_types type)
 ^
make[5]: *** [/home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.o] Error 1
make[4]: *** [/home/qprime/Downloads/backports-3.16-rc1-1/compat] Error 2
make[3]: *** [_module_/home/qprime/Downloads/backports-3.16-rc1-1] Error 2
make[2]: *** [modules] Error 2
make[1]: *** [modules] Error 2
make: *** [install] Error 2
qprime@Jcomp:~/Downloads/backports-3.16-rc1-1$ 

```

---

### Post by jackechanprime on 2014-10-18
and heres the second half of the terminal input/output for after the reboot. Doing second reboot, then i'll run the sticky's script again and post it, and we'll see if anything is working better.

```

qprime@Jcomp:~$ cd ~/Downloads/backports-3.16-rc1-1
qprime@Jcomp:~/Downloads/backports-3.16-rc1-1$ make clean
  CLEAN   /home/qprime/Downloads/backports-3.16-rc1-1/.tmp_versions
qprime@Jcomp:~/Downloads/backports-3.16-rc1-1$ make defconfig-rtlwifi
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o zconf.tab.o zconf.tab.c
cc   conf.o zconf.tab.o   -o conf
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
qprime@Jcomp:~/Downloads/backports-3.16-rc1-1$ make
make[5]: `conf' is up to date.
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
Building backport-include/backport/autoconf.h ... done.
  CC [M]  /home/qprime/Downloads/backports-3.16-rc1-1/compat/main.o
  CC [M]  /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.14.o
  CC [M]  /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.o
In file included from include/net/snmp.h:52:0,
                 from include/net/netns/mib.h:4,
                 from include/net/net_namespace.h:13,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/u64_stats_sync.h:117:28: error: redefinition of ‘u64_stats_fetch_begin_irq’
 static inline unsigned int u64_stats_fetch_begin_irq(const struct u64_stats_sync *syncp)
                            ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/u64_stats_sync.h:6:0,
                 from include/net/snmp.h:52,
                 from include/net/netns/mib.h:4,
                 from include/net/net_namespace.h:13,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/u64_stats_sync.h:122:28: note: previous definition of ‘u64_stats_fetch_begin_irq’ was here
 static inline unsigned int u64_stats_fetch_begin_irq(const struct u64_stats_sync *syncp)
                            ^
In file included from include/net/snmp.h:52:0,
                 from include/net/netns/mib.h:4,
                 from include/net/net_namespace.h:13,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/u64_stats_sync.h:129:20: error: redefinition of ‘u64_stats_fetch_retry_irq’
 static inline bool u64_stats_fetch_retry_irq(const struct u64_stats_sync *syncp,
                    ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/u64_stats_sync.h:6:0,
                 from include/net/snmp.h:52,
                 from include/net/netns/mib.h:4,
                 from include/net/net_namespace.h:13,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/u64_stats_sync.h:134:20: note: previous definition of ‘u64_stats_fetch_retry_irq’ was here
 static inline bool u64_stats_fetch_retry_irq(const struct u64_stats_sync *syncp,
                    ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:357:6: error: nested redefinition of ‘enum pkt_hash_types’
 enum pkt_hash_types {
      ^
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:357:6: error: redeclaration of ‘enum pkt_hash_types’
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:732:6: note: originally defined here
 enum pkt_hash_types {
      ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:358:2: error: redeclaration of enumerator ‘PKT_HASH_TYPE_NONE’
  PKT_HASH_TYPE_NONE, /* Undefined type */
  ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:733:2: note: previous definition of ‘PKT_HASH_TYPE_NONE’ was here
  PKT_HASH_TYPE_NONE, /* Undefined type */
  ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:359:2: error: redeclaration of enumerator ‘PKT_HASH_TYPE_L2’
  PKT_HASH_TYPE_L2, /* Input: src_MAC, dest_MAC */
  ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:734:2: note: previous definition of ‘PKT_HASH_TYPE_L2’ was here
  PKT_HASH_TYPE_L2, /* Input: src_MAC, dest_MAC */
  ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:360:2: error: redeclaration of enumerator ‘PKT_HASH_TYPE_L3’
  PKT_HASH_TYPE_L3, /* Input: src_IP, dst_IP */
  ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:735:2: note: previous definition of ‘PKT_HASH_TYPE_L3’ was here
  PKT_HASH_TYPE_L3, /* Input: src_IP, dst_IP */
  ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:361:2: error: redeclaration of enumerator ‘PKT_HASH_TYPE_L4’
  PKT_HASH_TYPE_L4, /* Input: src_IP, dst_IP, src_port, dst_port */
  ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:736:2: note: previous definition of ‘PKT_HASH_TYPE_L4’ was here
  PKT_HASH_TYPE_L4, /* Input: src_IP, dst_IP, src_port, dst_port */
  ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:365:1: error: redefinition of ‘skb_set_hash’
 skb_set_hash(struct sk_buff *skb, __u32 hash, enum pkt_hash_types type)
 ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:740:1: note: previous definition of ‘skb_set_hash’ was here
 skb_set_hash(struct sk_buff *skb, __u32 hash, enum pkt_hash_types type)
 ^
make[6]: *** [/home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.o] Error 1
make[5]: *** [/home/qprime/Downloads/backports-3.16-rc1-1/compat] Error 2
make[4]: *** [_module_/home/qprime/Downloads/backports-3.16-rc1-1] Error 2
make[3]: *** [modules] Error 2
make[2]: *** [modules] Error 2
make[1]: *** [modules] Error 2
make: *** [default] Error 2
qprime@Jcomp:~/Downloads/backports-3.16-rc1-1$ sudo make install
[sudo] password for qprime: 
  CC [M]  /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.o
In file included from include/net/snmp.h:52:0,
                 from include/net/netns/mib.h:4,
                 from include/net/net_namespace.h:13,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/u64_stats_sync.h:117:28: error: redefinition of ‘u64_stats_fetch_begin_irq’
 static inline unsigned int u64_stats_fetch_begin_irq(const struct u64_stats_sync *syncp)
                            ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/u64_stats_sync.h:6:0,
                 from include/net/snmp.h:52,
                 from include/net/netns/mib.h:4,
                 from include/net/net_namespace.h:13,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/u64_stats_sync.h:122:28: note: previous definition of ‘u64_stats_fetch_begin_irq’ was here
 static inline unsigned int u64_stats_fetch_begin_irq(const struct u64_stats_sync *syncp)
                            ^
In file included from include/net/snmp.h:52:0,
                 from include/net/netns/mib.h:4,
                 from include/net/net_namespace.h:13,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/u64_stats_sync.h:129:20: error: redefinition of ‘u64_stats_fetch_retry_irq’
 static inline bool u64_stats_fetch_retry_irq(const struct u64_stats_sync *syncp,
                    ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/u64_stats_sync.h:6:0,
                 from include/net/snmp.h:52,
                 from include/net/netns/mib.h:4,
                 from include/net/net_namespace.h:13,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/u64_stats_sync.h:134:20: note: previous definition of ‘u64_stats_fetch_retry_irq’ was here
 static inline bool u64_stats_fetch_retry_irq(const struct u64_stats_sync *syncp,
                    ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:357:6: error: nested redefinition of ‘enum pkt_hash_types’
 enum pkt_hash_types {
      ^
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:357:6: error: redeclaration of ‘enum pkt_hash_types’
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:732:6: note: originally defined here
 enum pkt_hash_types {
      ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:358:2: error: redeclaration of enumerator ‘PKT_HASH_TYPE_NONE’
  PKT_HASH_TYPE_NONE, /* Undefined type */
  ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:733:2: note: previous definition of ‘PKT_HASH_TYPE_NONE’ was here
  PKT_HASH_TYPE_NONE, /* Undefined type */
  ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:359:2: error: redeclaration of enumerator ‘PKT_HASH_TYPE_L2’
  PKT_HASH_TYPE_L2, /* Input: src_MAC, dest_MAC */
  ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:734:2: note: previous definition of ‘PKT_HASH_TYPE_L2’ was here
  PKT_HASH_TYPE_L2, /* Input: src_MAC, dest_MAC */
  ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:360:2: error: redeclaration of enumerator ‘PKT_HASH_TYPE_L3’
  PKT_HASH_TYPE_L3, /* Input: src_IP, dst_IP */
  ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:735:2: note: previous definition of ‘PKT_HASH_TYPE_L3’ was here
  PKT_HASH_TYPE_L3, /* Input: src_IP, dst_IP */
  ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:361:2: error: redeclaration of enumerator ‘PKT_HASH_TYPE_L4’
  PKT_HASH_TYPE_L4, /* Input: src_IP, dst_IP, src_port, dst_port */
  ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:736:2: note: previous definition of ‘PKT_HASH_TYPE_L4’ was here
  PKT_HASH_TYPE_L4, /* Input: src_IP, dst_IP, src_port, dst_port */
  ^
In file included from include/linux/netfilter.h:5:0,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
/home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:365:1: error: redefinition of ‘skb_set_hash’
 skb_set_hash(struct sk_buff *skb, __u32 hash, enum pkt_hash_types type)
 ^
In file included from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/linux/skbuff.h:3:0,
                 from include/linux/netfilter.h:5,
                 from include/net/netns/netfilter.h:5,
                 from include/net/net_namespace.h:20,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/backport-include/net/net_namespace.h:4,
                 from /home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.c:16:
include/linux/skbuff.h:740:1: note: previous definition of ‘skb_set_hash’ was here
 skb_set_hash(struct sk_buff *skb, __u32 hash, enum pkt_hash_types type)
 ^
make[5]: *** [/home/qprime/Downloads/backports-3.16-rc1-1/compat/backport-3.15.o] Error 1
make[4]: *** [/home/qprime/Downloads/backports-3.16-rc1-1/compat] Error 2
make[3]: *** [_module_/home/qprime/Downloads/backports-3.16-rc1-1] Error 2
make[2]: *** [modules] Error 2
make[1]: *** [modules] Error 2
make: *** [install] Error 2
qprime@Jcomp:~/Downloads/backports-3.16-rc1-1$ 

```

---

### Post by jackechanprime on 2014-10-18
Connection remains trottled at 1mb/s. I don't know why this thing just wont cooperate. Here's the script output -- untouched this time, as requested.

```

########## wireless info START ##########

Report from: 17 Oct 2014 21:47 PDT -0700

Booted last: 17 Oct 2014 21:44 PDT -0700

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
	Subsystem: ASUSTeK Computer Inc. Device [1043:859e]
	Kernel driver in use: r8169

06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178] (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device [1043:85e3]
	Kernel driver in use: rtl8192ce

##### lsusb #############################

Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 046d:c31d Logitech, Inc. Media Keyboard K200
Bus 003 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 003 Device 002: ID 04f9:025d Brother Industries, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              630653  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              484040  2 mac80211,rtlwifi
mxm_wmi                13021  1 nouveau
video                  19476  2 nouveau,asus_wmi
wmi                    19177  3 mxm_wmi,nouveau,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::56a0:50ff:fe52:2723/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1932 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1901 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1217974 (1.2 MB)  TX bytes:266832 (266.8 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e23f:49ff:fe8f:f425/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12174 (12.1 KB)  TX bytes:24555 (24.5 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"2WIRE305"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC '2WIRE305' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=30/70  Signal level=-80 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search gateway.2wire.net

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [2WIRE305] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    suddenlink.net-2820: Infra, <MAC 'suddenlink.net-2820' [AN1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 26 WPA2
    ATT264:          Infra, <MAC 'ATT264' [AN2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 26 WPA WPA2
    suddenlink.net-2600: Infra, <MAC 'suddenlink.net-2600' [AN3]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 26 WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AN4]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 26 WPA2
    suddenlink.net-18D0: Infra, <MAC 'suddenlink.net-18D0' [AN5]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 26 WPA2
    ATT368:          Infra, <MAC 'ATT368' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 26 WPA WPA2
    NETGEAR02:       Infra, <MAC 'NETGEAR02' [AN7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 26 WPA2
    ATT272:          Infra, <MAC 'ATT272' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 26 WPA WPA2
    Router2:         Infra, <MAC 'Router2' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 26 WPA2
    NETGEAR45:       Infra, <MAC 'NETGEAR45' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 26 WPA2
    ATT264:          Infra, <MAC 'ATT264' [AN11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 26 WPA WPA2
    ATT800:          Infra, <MAC 'ATT800' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    ATT152:          Infra, <MAC 'ATT152' [AN13]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2
    Zoey:            Infra, <MAC 'Zoey' [AC3]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2
    SUDDENLINK.NET-FDED: Infra, <MAC 'SUDDENLINK.NET-FDED' [AN15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 26 WEP
    *2WIRE305:       Infra, <MAC '2WIRE305' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 90 WPA2
    ATT448:          Infra, <MAC 'ATT448' [AN17]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.70
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.68
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

[[/etc/NetworkManager/system-connections/2WIRE305]] (600 root)
[connection] id=2WIRE305 | type=802-11-wireless
[802-11-wireless] ssid=2WIRE305 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=802-11-wireless
[802-11-wireless] ssid=2WIRE305
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     11 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

Channel occupancy:

      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      3   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC '2WIRE305' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"2WIRE305"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000003403264
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'NETGEAR45' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR45"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001f77ac72230
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Zoey' [AC3]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"Zoey"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000bddf9301db
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'ATT800' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"ATT800"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000031765f015
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'ATT272' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"ATT272"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000003c8c01b3
                    Extra: Last beacon: 1056ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Router2' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-26 dBm  
                    Encryption key:on
                    ESSID:"Router2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004ba8e3153d
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'ATT368' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=14/70  Signal level=-96 dBm  
                    Encryption key:on
                    ESSID:"ATT368"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000026e3cc62f1
                    Extra: Last beacon: 980ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192ce]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     EF063698748457BBEDB4633
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192ce]
debug: 0
fwlps: N
ips: N
swenc: Y
swlps: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/8192cu-disable-power-management.conf]
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0

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

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

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

[/etc/modprobe.d/rtl8192.ce.conf]
options rtl8192ce ips=0 fwlps=0

[/etc/modprobe.d/rtl8192ce.conf]
options rtl8192ce swenc=1 ips=0

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8178 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   13.070629] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   14.029471] wlan0: authenticate with <MAC '2WIRE305' [AC1]>
[   14.040217] wlan0: send auth to <MAC '2WIRE305' [AC1]> (try 1/3)
[   14.041877] wlan0: authenticated
[   14.041946] rtl8192ce 0000:06:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   14.041949] rtl8192ce 0000:06:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   14.044079] wlan0: associate with <MAC '2WIRE305' [AC1]> (try 1/3)
[   14.048166] wlan0: RX AssocResp from <MAC '2WIRE305' [AC1]> (capab=0x431 status=0 aid=1)
[   14.048214] wlan0: associated
[   14.048220] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   14.156267]  [<ffffffffa02e23ad>] ? rtl_is_special_data+0x2d/0x110 [rtlwifi]

########## wireless info END ############

```

---

### Post by jackechanprime on 2014-10-27
so...um... any ideas? Should I try the card's manufacturer guys?

---

