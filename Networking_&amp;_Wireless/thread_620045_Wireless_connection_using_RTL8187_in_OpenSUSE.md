---
title: "Wireless connection using RTL8187 in OpenSUSE"
date: 2007-11-22
forum: Networking &amp; Wireless
---

### Post by zeldaze on 2007-11-22
Hey there,

I am triple booting with Ubuntu + Windows and OpenSUSE (Testing out OpenSUSE)
I am trying to setup my wireles network card (Rraltek RTL8187)
I followed a few guides for installing it with Ubuntu but they don't seem to work in OpenSUSE. 
I understand that there is some sort of conflict etc. I have tried installing the WindowsXP drivers, the Windows 98 drivers through ndiswrapper and I eventually was able to detect the network connection but any attempts to connect to it dont work.
My disc also came with Linux drivers however I am too n00b to install them. They are in a .tar.gz format.
I don't know how to install them?
Maybe if someone could tell me the steps to install them then I can uninstall ndiswrapper to get it working :)
My disc has two versions One for debian and one for 2.x.x
I don't know which to use ?

Some please help me?
Thanks

---

### Post by elspiko on 2007-11-22
First off, I'd suggest (if you haven't already, installing GCC, build essentials and the linux-headers for your kernel), in SuSE this can be done via YAST.

As for the tar.gz files, as SuSe is NOT debian based (unlike Ubuntu) I would suggest using the 2.x.x version.

copy the file into the /tmp directory

```
cp /media/cdrom0/2.x.x.tar.gz /tmp
``` or what ever the path to the file is.

```
cd /tmp
tar zxvf file.tar.gz

```
It will then create a dirctory, usually the same as the file name.

```
cd dirctory
./configure
make
make install

```

"make install" will probably need to be run as root (if your not already, in which case)...

```

su     (then enter the root password)
make install
```

If you get a load of warnings, then don't worry. Its the errors you'll need to worry about.

Have you searched for SuSE drivers for your wireless card?

---

### Post by zeldaze on 2007-11-22
Thanks
- No in my disc is just says linux drivers and has drivers for "debian31-8187(110)" and for "linux26x-8187(110)"

---

### Post by zeldaze on 2007-11-22
Ok after carefully following the intsructions that came with my drivers:

> Release Date: 2006-01-13, ver 1.1

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

	 2. Download the openssl open source package from [www.openssl.org](www.openssl.org), build and install it.

	 

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




I did all that - and now I am answering from openSUSE. But is there anyway to be able to manage the connection with NetworkManager and/or have the instructions I followed execute automatically on startup? Thanks

---

