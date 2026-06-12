---
title: "Realtek RTL8187 Drivers"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by andrew.pope on 2007-10-27
Before I begin i will let you know that I am running an old version of ubuntu - Hoary Hedgehog 5.4. I got the cd ages ago and used to use it, the only problem was my network card drivers would not work so I uninstalled it and only re-installed it a few days ago. I now have a new network card which uses the RTL8187 chipset. I need help to install the drivers because I am using a linux driver file that confuses me. I am totally new to Linux I hardly know any console commands apart from some easy to remember ones eg. ls and cd and make etc..

I have tried numerous times over the past 2 days to get it to work but i keep getting an error message. I read somewhere that the kernel source files have to be installed. I have no idea what that means or how to do it. I can't remeber the error message I get as I am not booted into Windows. something about setup cannot find a "bulid" command/directory in lib/modules/2.6.10-5-386. The readme file is listed below.

```

Release Date: 2006-01-13, ver 1.1
RTL8187 Linux driver version 1.1

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
	  ./makedrv  <--- HERE IS WHERE MY ERROR OCCURS!

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

any help would be greatly appreciated.

but I am planning on upgrading to Ubuntu 7.10 Desktop very soon. so if the driver is already included in this dist could someone inform me because i heard that they wer included in the 6.10 Edgy Eft so i would presume it would be carried over into 7.10?

thanks in advance for any assistance!

cheers,

andy

---

### Post by kevdog on 2007-10-27
There are many ways to skin the cat -- but your cat is wild -- meaning you are unfortunate to end up with the chipset since its a pain in the butt.  All things considered, I probably recommend ndiswrapper with win98 drivers.

---

