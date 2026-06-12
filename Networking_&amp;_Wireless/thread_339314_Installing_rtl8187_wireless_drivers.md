---
title: "Installing rtl8187 wireless drivers"
date: 2007-01-15
forum: Networking &amp; Wireless
---

### Post by AgentSmith15 on 2007-01-15
I am trying to install a driver for my wireless card, but I am new and have no idea what to do.  I see the wireless driver I need but I have no idea how to compile and install it. The driver below is the link to the driver. 
[ftp://210.51.181.211/cn/wlan/rtl8187_linux_26.1010.zip](ftp://210.51.181.211/cn/wlan/rtl8187_linux_26.1010.zip)

Any help would be greatly appreciated:)

---

### Post by teaker1s on 2007-01-15
download it double click unzip it read the readme files

terminal [COLOR="Red"]apt-get install build-essential

[/COLOR]

Install the correct headers for your version of Ubuntu: (don't worry if it tells you that yours are up to date.)

user@ubuntu:~$[COLOR="Red"] sudo apt-get install linux-headers-`uname -r`[/COLOR] 
user@ubuntu:~$ [COLOR="Red"]sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build[/COLOR]


you will need to compile the source code first "cd" into folder location eg.

[COLOR="Red"]cd /home/daniel/junk[/COLOR]

someone will help you more on source, if when you make you get errors you have dependency issues that need installing first

[COLOR="Red"]make distclean
./configure
 make
 sudo make install[/COLOR]

---

### Post by teaker1s on 2007-01-15
this tread may help
[http://ubuntuforums.org/showthread.php?t=338445]("http://ubuntuforums.org/showthread.php?t=338445")

---

### Post by AgentSmith15 on 2007-01-15
Thank you for the help. I installed the build-essential and also typed the commands you listed, but in terminal when when I type make distclean I get.

[COLOR="Red"]make: *** No rule to make target `distclean'.  Stop.[/COLOR]

Also ./configure doesn't work?

---

### Post by teaker1s on 2007-01-15
okay leave dist clean out, have you read the readme's they may guide you?

---

### Post by AgentSmith15 on 2007-01-15
Yes I have read the readme, but it is very hard to understand because it isn't clear.

---

### Post by tdwester on 2007-01-16
Lets step back a second. Is this a usb, pcmcia or pci card?

---

### Post by AgentSmith15 on 2007-01-16
It is a built in internal card and judging from what XP says it is I think it is USB.:-k 

[IMG]http://img411.imageshack.us/img411/5974/wirelesshc9.png[/IMG]

---

### Post by AgentSmith15 on 2007-01-16
This the readme
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

As you can see I am having problems running the scripts.   ./makedrv doesn't work when I run i either.

---

### Post by teaker1s on 2007-01-16
having a route round I've found this
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111]("https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111")
biggest problem is linux documentation is fragmented and finding what you want is a mission
> Note: Ubuntu 6.10 Edgy Eft supports the WG111v2 (rtl8187 chipset) with a native driver straight out of the box

if your using edgy with a wired ethernet connection then terminal
[COLOR="Red"]gksudo synaptic[/COLOR]

search and install

[COLOR="Red"]network-manager-gnome[/COLOR]


on panel click 
system
administration
networking

remove ticks so the interfaces are unconfigured and remove ethernet cable

reboot 

next to volume icon there is gnome-network-manager applet which left click should now show wireless networks avaliable.

---

