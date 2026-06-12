---
title: "My wi-fi card is not working"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by Usta_AsH on 2007-07-11
Hello I am using
Card is : Alfa Network USB Wireless Card
Model is : AWUS036H
Wireless chipset is : RTL8187

Hello
my problem is
I can't use that card.
I tried every way
I openned ubuntu after that plugged in:
I can see Network part. But When I pushed prefences my card isn't see any wireless access points.
I am sure there is one access point which I am using windows XP. Actually I entered network tools and selected my card but there is in only ipv6 protocol there is no ipv4 protocol

I plugged after that I openned ubuntu:
When I tried to open Network part, Network part is freezing.


How can slove that problem?

---

### Post by linuxwizard on 2007-07-11
According to this link it is supported card. Their are 2 links to get drivers & info. Which driver are you using ? Compared to these 2 links of drivers ?

[http://linux-wless.passys.nl/query_part.php?brandname=Alfa](http://linux-wless.passys.nl/query_part.php?brandname=Alfa)

---

### Post by Usta_AsH on 2007-07-11
actually I didnt install anything because I am using D-Link DWL-650 too When I plugged into my laptop i can use my dlink but i can't use that card.

Also I am beggineer. How can I install driver?(of course i know download but i don't know install)

---

### Post by linuxwizard on 2007-07-11
That link I gave to the drivers it should give info on installing them.

---

### Post by Usta_AsH on 2007-07-11
Hi again
ReadMe.txt is
```
Release Date: 2006-02-09, ver 1.2
RTL8187 Linux driver version 1.2

   --This driver supports RealTek RTL8187 Wireless LAN driver for 
     Fedora Core 2/3/4/5, Debian 3.1, Mandrake 10.2/Mandriva 2006, 
     SUSE 9.3/10.1/10.2, Gentoo 3.1, etc.
   - Support Client mode for either infrastructure or adhoc mode
   - Support WEP and WPAPSK connection

< Component >
The driver is composed of several parts:
	1. Module source code
	  stack.tar.gz
	  drv.tar.gz
	
	2. Script ot build the modules
	  makedrv

	3. Script to load/unload modules
	  wlan0up
	  wlan0down 

	4. Script and configuration for DHCP
 	  wlan0dhcp
	  ifcfg-wlan0
	4. Supplicant source code:
	  wpa_supplicant-0.4.9.tar.gz

	5. Example of supplicant configuration file:
	  wpa1.conf

< Installation >
Runing the scripts can finish all operations of building up modules 
from the source code and start the nic.
	1. Build up the drivers from the source code
	  ./makedrv

	2. load the driver module to kernel and start up nic
	  ./wlan0up

< Set wireless lan MIBs >
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
        Show Power Management mode      power             

For example:
	iwlist wlan0 channel
	iwlist wlan0 scan
	iwlist wlan0 rate
	iwlist wlan0 power

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

< Getting IP address >
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
		
< WPAPSK >
WPA_SUPPLICANT help the network to communicate under the protection of WPAPSK
mechanism
	
	(1)Unpack source code of WPA supplicant:
	  tar -zxvf wpa_supplicant-0.4.9.tar.gz
	  cd wpa_supplicant-0.4.9
	
	(2)Create .config file:
	  cp defconfig .config
	
	(3)Edit .config file, uncomment the following line:
	  #CONFIG_DRIVER_IPW=y.
		
	(4)Build WPA supplicant:
	  make
	If make error for lack of <include/md5.h>, install the openssl lib(two ways):
	 1. Install the openssl lib from corresponding installation disc:
	    Fedora Core 2/3/4/5(openssl-0.9.71x-xx), Mandrake10.2/Mandriva10.2(openssl-0.9.7x-xmdk),
	    Debian 3.1(libssl-dev), Suse 9.3/10.0/10.1(openssl_devl), Gentoo(dev-libs/openssl), etc.
	 2. Download the openssl open source package from www.openssl.org, build and install it.
	 
	(5)Edit wpa_supplicant.conf to set up SSID and its passphrase.
	  For example, the following setting in "wpa1.conf" means SSID 
          to join is "BufAG54_Ch6" and its passphrase is "87654321".
	  network={
			ssid="BufAG54_Ch6"
			proto=WPA
			key_mgmt=WPA-PSK
			pairwise=CCMP TKIP
			group=CCMP TKIP WEP104 WEP40
			psk="87654321"
			priority=2
		  }

	(6)Execute WPA supplicant (Assume 8187 and related modules had been
           loaded):
	  ./wpa_supplicant -D ipw -c wpa1.conf -i wlan0 &


```

First
is it suitable for ubuntu 7.04(I am using xface)
if you say yes it is how can i install?

---

### Post by kevdog on 2007-07-11
Maybe this post can help you, it talks about rtl8187 chipset (a problem yes indeed), but at least in this thread the author proposed and documented a solution:
[http://ubuntuforums.org/showthread.php?t=493958&highlight=rtl8187](http://ubuntuforums.org/showthread.php?t=493958&highlight=rtl8187)

---

