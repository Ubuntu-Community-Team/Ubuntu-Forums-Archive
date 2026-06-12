---
title: "Utterly confused - installing drivers"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by Johnny English on 2010-08-29
So, I got myself a D-Link DWA-130 USB wireless adapter which has Linux drivers available (I even made sure to get revision C, which is the Linux-compatible version). I downloaded the drivers from the D-Link website, but I'm damned if I can work out how to install them.

There's a readme.txt file with the drivers which contains what to me is a list of complete gibberish - can anyone explain this in easy steps please, or is there an easier way of doing it? The machine isn't connected to the web and can't be until I get this thing working.

```
Release Date: 2008-10-31, ver 0.06
RTL8192U Linux driver version 0.06
   --This driver supports RealTek rtl8192U USB Wireless LAN NIC
     for
     2.6 kernel:
     Fedora Core 2/3/4/5, Debian 3.1, Mandrake 10.2/Mandriva 2006, 
     SUSE 9.3/10.1/10.2, Gentoo 3.1, Ubuntu 7.10/8.04, etc.
     2.4 kernel:
     Redhat 9.0/9.1

===============================================================================
				Component 
===============================================================================
The driver is composed of several parts:
	1. Firmare to make nic work
           1.1 firmare/RTL8192U

	2. Module source code
	   2.1 ieee80211 
	   2.2 HAL/rtl8192u
	   2.3 wpa_supplicant-0.5.10 (User can download the latest version from 
	       internet also, but it is suggested to use default package contained
	       in the distribution because there should be less compilation issue.)
	
	3. Script to build the modules
	   3.1 Makefile 

	4. Script to load/unload modules
	   4.1 wlan0up 
	   4.2 wlan0down 

	5. Script and configuration for DHCP
 	   5.1 wlan0dhcp
	   5.2 ifcfg-wlan0

	6. Example of supplicant configuration file:
	   6.1 wpa1.conf

===============================================================================
				Installation 
===============================================================================
<<Method 1>>
Runing the scripts accomplish all operations including building up modules 
from the source code, installing driver to the kernel and starting up the nic.
	1. Build up the drivers from the source code
	  make

	2. Install the driver to the kernel
          make install
          reboot

	3. bring up wlan if nic is not brought up by GUI, such as NetworkManager
	  ifconfig wlan0 up 
	  Note: use ifconfig to check whether wlan0 is brought up and use iwconfig to check your wlan interface name, 
                since it may change wlan0 to wlan1,etc.

<<Method 2>>
Or only load the driver module to kernel and start up nic.
	 1. Build up the drivers from the source code
	  make
         2. Copy firmware to /lib/firmware/ or /lib/firmware/(KERNEL_VERSION)/
            cp -rf firmware/RTL8192U /lib/firmware
          or
            cp -rf firmware/RTL8192U /lib/firmware/(KERNEL_VERSION)
          Note: This depends on whether (KERNEL_VERSION) subdirectory exists under /lib/firmware

	 3. Load driver module to kernel and start up nic.
	  ./wlan0up
          Note: when "insmod: error inserting 'xxxx.ko': -1 File exists" comes out
                after run ./wlan0up, please run ./wlan0down first, then it should 
                be ok..
	  Note: If you see the message of "unkown symbol" during ./wlan0up, it
		is suggested to build driver by <<Method 1>>.

===============================================================================
				Set wireless lan MIBs 
===============================================================================
This driver uses Wireless Extension as an interface allowing you to set
Wireless LAN specific parameters.

Current driver supports "iwlist" to show the device status of nic
        iwlist wlan0 [parameters]
where
        parameter explaination      	[parameters]    
        -----------------------     	-------------   
        Show available chan and freq	freq / channel  
        Show and Scan BSS and IBSS 	scan[ning]          
        Show supported bit-rate         rate / bit[rate]        

For example:
	iwlist wlan0 channel
	iwlist wlan0 scan
	iwlist wlan0 rate

Driver also supports "iwconfig", manipulate driver private ioctls, to set
MIBs.

	iwconfig wlan0 [parameters] [val]
where
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
	iwconfig wlan0 mode essid "name" mode Ad-hoc
	iwconfig wlan0 key 0123456789 [2] open
	iwconfig wlan0 key off
	iwconfig wlan0 key restricted [3] 0123456789
        Note: Better to set these MIBS without GUI such as NetworkManager and be sure that our
              nic has been brought up before these settings. WEP key index 2-4 is not supportted by
              NetworkManager.

===============================================================================
				Getting IP address
===============================================================================
After start up the nic, the network needs to obtain an IP address before
transmit/receive data.
This can be done by setting the static IP via "ifconfig wlan0 IP_ADDRESS"
command, or using DHCP.

If using DHCP, setting steps is as below:
	(1)connect to an AP via "iwconfig" settings
		iwconfig wlan0 essid [name]	or
		iwconfig wlan0 ap XX:XX:XX:XX:XX:XX

	(2)run the script which run the dhclient
		./wlan0dhcp
           or 
		dhcpcd wlan0
              	(Some network admins require that you use the
              	hostname and domainname provided by the DHCP server.
              	In that case, use 
		dhcpcd -HD wlan0)
		
	
===============================================================================
			WPAPSK/WPA2PSK 
===============================================================================
	Wpa_supplicant helps to secure wireless connection with the protection of 
WPAPSK/WPA2PSK mechanism. 

	If the version of Wireless Extension in your system is equal or larger than 18, 
WEXT driver interface is recommended. Otherwise, IPW driver interface is advised.  
	Note: Wireless Extension is defined us "#define WIRELESS_EXT" in Kernel
	Note: To check the version of wireless extension, please type "iwconfig -v"


 	If IPW driver interface is used, it is suggested to follow the steps from 1 to 6. 
If wpa_supplicant has been installed in your system, only steps 5 and 6 are required 
to be executed for WEXT driver interface.

	To see detailed description for driver interface and wpa_supplicant, please type
"man wpa_supplicant".  
	
	(1)Download latetest source code for wpa supplicant or use wpa_supplicant-0.5.10 
	   attached in this package. (It is suggested to use default package contained
           in the distribution because there should less compilation issue.)

	   Unpack source code of WPA supplicant:

	  tar -zxvf wpa_supplicant-0.5.10.tar.gz (e.g.) 
	  cd wpa_supplicant-0.5.10
	
	(2)Create .config file:
	  cp defconfig .config
	
	(3)Edit .config file, uncomment the following line if ipw driver interface 
	   will be applied:
	  #CONFIG_DRIVER_IPW=y.
		
	(4)Build and install WPA supplicant:
	  make
	  cp wpa_cli wpa_supplicant /usr/local/bin	
	
	If make error for lack of <include/md5.h>, install the openssl lib(two ways):
	 1. Install the openssl lib from corresponding installation disc:
	      Fedora Core 2/3/4/5(openssl-0.9.71x-xx), 
	      Mandrake10.2/Mandriva10.2(openssl-0.9.7x-xmdk),
	      Debian 3.1(libssl-dev), Suse 9.3/10.0/10.1(openssl_devl), 
	      Gentoo(dev-libs/openssl), etc.
	   2. Download the openssl open source package from [www.openssl.org](www.openssl.org), build and 
	      install it.
	 
	(5)Edit wpa_supplicant.conf to set up SSID and its passphrase.
	  For example, the following setting in "wpa1.conf" means SSID 
          to join is "BufAG54_Ch6" and its passphrase is "87654321".

	   Example 1: Configuration for WPA-PWK
	  network={
			ssid="BufAG54_Ch6"
			proto=WPA
			key_mgmt=WPA-PSK
			pairwise=CCMP TKIP
			group=CCMP TKIP WEP104 WEP40
			psk="87654321"
			priority=2
		  }
	
	    Example 2: Configuration for LEAP
	    network={
			ssid="BufAG54_Ch6"
			key_mgmt=IEEE8021X
			group=WEP40 WEP104
			eap=LEAP
			identity="user1"
			password="1111"
		  }
		
            Example 3: Linking to hidden ssid given AP's security policy exactly.(see note 3 below)
            ap_scan=2
	    network={
		ssid="Hidden_ssid"
		proto=WPA
		key_mgmt=WPA-PSK
		pairwise=CCMP
		group=CCMP
		psk="12345678"
	  	}

	    Example 4: Linking to ad-hoc (see note 4 below)
	    ap_scan=2
	    network={
		ssid="Ad-hoc"
                mode=1
		proto=WPA
		key_mgmt=WPA-NONE
		pairwise=NONE
		group=TKIP
		psk="12345678"
		}
	Note: 1. proto=WPA for WPA, proto=RSN for WPA2. 
	      2. If user needs to connect an AP with WPA or WPA2 mixed mode, it is suggested 
		 to set the cipher of pairwise and group to both CCMP and TKIP unless you 
		 know exactly which cipher type AP is configured.
	      3. When connecting to hidden ssid, explicit security policy should be given with 
		 ap_scan=2 being setted.
	      4. It is suggested setting ap_scan to 2 and mode to 1 when linking to or creating an ad-hoc. Group and pairwise
		 cipher type should also be explicit, always with group setted to TKIP or CCMP and pairwise setted
		 to NONE. Lower version wpa_supplicant may not allow setting group to CCMP with pairwise setting to NONE.
		 So if any problem, you may try to set both group and pairwise to CCMP, leaving other setting unchanged, when
	         connecting to an CCMP-encrypted ad-hoc.
	      5. More config setting option, please refer to wpa_supplicant.conf in wpa_supplicant.tar.gz that we provide.

	(6)Execute WPA supplicant (Assume rtl8192U and related modules had been
           loaded):
	  wpa_supplicant -D wext -c wpa1.conf -i wlan0  (recommended)
	  wpa_supplicant -D ipw -c wpa1.conf -i wlan0 

	   Note: At first, user sholud check Wireless Extension by typing "iwconfig -v"  
	         on the comment line. If the version of Wireless Extension is equal or 
		 larger than 18, the option of "-D wext" is suggested. If the version 
		 of Wireless extension is less than 18, the option of "-D ipw" is 
		 suggested.
```

Any assistance gratefully accepted.

---

### Post by howefield on 2010-08-29
According to...

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB)

> Download Windows XP driver from D-Link, install ndiswrapper and ndisgtk, add windows driver, should work after reboot 

---

### Post by blazemore on 2010-08-29
While you can use the native Linux driver, in this case it's almost certainly easier to use the Windows one, through a special piece of software called "ndiswrapper".

I won't bore you with the details, but it's a project to implement all the functionality of the "ndis" Windows XP wireless driver standard in Linux.

The good news is, it's super-easy to install.

Just fire up the software centre and search for "Windows Wireless Drivers" (I can't remember exactly), or if you can't find it there, search for "ndisgtk" (which is the actual name of the package).

Once you've installed it (click [here]("http://johnson-yip.com/ubuntu910softwarecentretutorial") if you're unsure about installing software), go to System -> Administration and then "Windows Wireless Drivers". After entering your password you should see the following window:

[IMG]http://www.chazco.co.uk/images/upload/1270464153.png[/IMG]

Click "Install new driver" and browse to the location of the Windows XP driver you downloaded from D-Link (If it's in a zip archive you'll have to extract it first).

Find a file with the extensions ".inf" and double-click it.
Press "Install"

Click Close, then restart your computer. If all goes well, your wireless device will be up and running!

Any problems, post back here.

---

### Post by themusicalduck on 2010-08-29
Before doing any of the ndiswrapper stuff, have you checked under System > Administration > Hardware Drivers?

---

### Post by Johnny English on 2010-08-29
howefield / blazemore - thanks for that. I had seen through various searches that this was potentially a recommended route, but I couldn't work out how to get this ndiswrapper thing without first having my machine connected to the internet. Is it something I can easily download to my Windows machine from which I am typing currently and then transfer using a flash drive?

themusicalduck - I looked in there but the only thing showing was a proprietary driver for my Nvidia graphics card (I'm running an Asrock Ion 330 mini PC with Ubuntu 10.04 as my media server). I'm presuming that lack of internet connection means that it can't pull it up automatically?

---

### Post by Perfect Storm on 2010-08-29
> **Johnny English said:**
> howefield / blazemore - thanks for that. I had seen through various searches that this was potentially a recommended route, but I couldn't work out how to get this ndiswrapper thing without first having my machine connected to the internet. Is it something I can easily download to my Windows machine from which I am typing currently and then transfer using a flash drive?

themusicalduck - I looked in there but the only thing showing was a proprietary driver for my Nvidia graphics card (I'm running an Asrock Ion 330 mini PC with Ubuntu 10.04 as my media server). I'm presuming that lack of internet connection means that it can't pull it up automatically?

You might want to read this: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Or if you have a wire you can use until your wireless is set up.

---

### Post by Johnny English on 2010-08-29
Thanks for that. Unfortunately, it's still absolute gobbledegook. Section 2.2 is fine, I've managed that (although I'm not sure whether I need the AMD64 or the i386 versions of the files?), but when we get to statements like 

> Firstly, all releases since Ubuntu 6.06 have the open source bcm43xx driver, which was replaced in 8.04 by b43 and b43legacy, see WifiDocs/Driver/bcm43xx. If this driver doesn't work for you, then you should disable it, because it will conflict with ndiswrapper. To disable it, add blacklist bcm43xx lines for each driver to the modprobe blacklist.

echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist

then I might as well be reading Swahili. Is this really more simple than installing the Linux drivers that I already downloaded?

I'm going to go and buy a really long patch lead and try to use Blazemore's approach which looks more simple!

---

### Post by Perfect Storm on 2010-08-29
AMD64 = 64-bit
i386 = 32-bit

First did you rebooted afterwards? (checking if it was enough getting it working?)
Secondly, did you ran the command you posted?

---

### Post by Johnny English on 2010-08-30
OK, I found a long enough patch lead and followed blazemore's instructions - thank you for that, as everything appeared as you said it would. Except that having rebooted, there's still no wireless connection visible.

When I go into the Wireless Network Drivers tool it shows me that the driver for the device is installed and it says Hardware present, but I've no idea how to actually view wireless networks?

---

### Post by jtarin on 2010-08-30
Enter the command ```
lsmod
``` in a terminal and post the output. The reason I ask is the module/driver is already included in 10.04 and we need to see if its loading.

---

### Post by blazemore on 2010-08-30
(left-)click the icon in the indicator area at the top-right of the screen. A list of networks should appear.

---

