---
title: "Installing drivers (Wireless USB LAN adapter: Edimax EW-7718Un)"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by Rhythmdvl on 2009-01-22
I have an Edimax EW-7718UN wireless LAN USB adapter that I’d like to use with an eight-year-old Dell Inspiron 8100 laptop running Ubuntu 8.04 (desktop). 

The adapter came with a Linux CD, but alas, no self-running installation files (that I can find). 

On the CD there are two Linux-related folders:
[List][*]2008_0718_RT2870_STA_v1.3.1.0
[*]2008_0718_RT2870_STA_WebUI_v1.3.1.0[/list]

I assume the first has the actual drivers, the second has a Web user interface. 

And, well, that’s about as far as I got. I *am* an absolute beginner (still), so I can’t make heads nor tails of the ReadMe file in the (assumed) driver folder. 

I’m unfortunately too new to know what to make of it. I’ll paste the whole thing below in a CODE box, but here’s where it seems to almost make sense to me. Almost. 

No, wait, scratch that. None of it makes sense. 

“1> $tar -xvzf DPO_RT2870_Linux_STA_x.x.x.x.tgz
    go to "./DPO_RT2870_Linux_STA_x.x.x.x" directory.”

Well, maybe that bit does. Almost. I can CD to the directory... but what is $tar? I thought tar was a file format? Does $tar unzip?

Then it says “In Makefile
	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 define the linux kernel source include file path LINUX_SRC
	 modify to meet your need.”

What? “Set the “Mode = STA” in Makefile ... damn I’m lost. 

It gets worse from there. There’s also a config file, but I’m not sure what to do with it/where it goes. 


So.... can I get a bit of help here? I have a wireless WAP2 network in the house and I’d like the connection bit to be as painless as possible (I’m putting this laptop in the parlor to stream music through the receiver, so ease for the rest of the family would be great). 

Both specific (getting this to work) and general (pointing me to a good resource to understand drivers and makefiles in Linux) will be very appreciated. 

Oh, and I’ll be going to Ralinktech.com to get the most updated drivers, but if you have a question about what else is in the folder let me know. 

Thanks, 

Rhythm



```

* README
*
* Ralink Tech Inc.
* 
* http://www.ralinktech.com
*

=======================================================================
ModelName:
===========
RT2870 Wireless Lan Linux Driver


=======================================================================
Driver lName:
===========
rt2870.o/rt2870.ko


=======================================================================
Supporting Kernel:
===================
linux kernel 2.4 and 2.6 series. 
Tested in Redhat 7.3 or later.


=======================================================================
Ralink Hardware:
===================
Ralink 802.11n Wireless LAN Card.


=======================================================================
Description:
=============
This is a linux device driver for Ralink RT2870 USB ABGN WLAN Card.


=======================================================================
Contents:
=============
Makefile	        : Makefile
*.c					: c files
*.h					: header files


=======================================================================
Features:
==========
   This driver implements basic IEEE802.11. Infrastructure and adhoc mode with 
   open or shared or WPA-PSK or WPA2-PSK authentication method. 
   NONE, WEP, TKIP and AES encryption. 


=======================================================================
Build Instructions:  
====================

1> $tar -xvzf DPO_RT2870_Linux_STA_x.x.x.x.tgz
    go to "./DPO_RT2870_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 define the linux kernel source include file path LINUX_SRC
	 modify to meet your need.

3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.
	** Build for being controlled by NetworkManager
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	** Build for being controlled by WpaSupplicant with Ralink Custom Event
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   command: #./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make									# compile driver source code

5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
    
6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
	$/sbin/rmmod rt2870sta
	
=======================================================================
CONFIGURATION:  
====================
RT2870 driver can be configured via following interfaces, 
i.e. (i)"iwconfig" command, (ii)"iwpriv" command, (iii) configuration file

i)  iwconfig comes with kernel.  
ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for details.
iii)modify configuration file "RT2870STA.dat" in /etc/Wireless/RT2870STA/RT2870STA.dat.
           
Configuration File : RT2870STA.dat
---------------------------------------
# Copy this file to /etc/Wireless/RT2870STA/RT2870STA.dat
# This file is a binary file and will be read on loading rt.o module.
#
# Use "vi RT2870STA.dat" to modify settings according to your need.
# 
# 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infrastructure
# 2.) set Channel to "0" for auto-select on Infrastructure mode
# 3.) set SSID for connecting to your Accss-point.
# 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE"
# 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES"
# for more information refer to the Readme file.
# 
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
SSID=Dennis2860AP
NetworkType=Infra
WirelessMode=9
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
WmmCapable=0
AckPolicy=0;0;0;0
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
FastRoaming=0
RoamThreshold=70
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=1
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0

-----------------------------------------------
*NOTE:
	WMM parameters
			WmmCapable			Set it as 1 to turn on WMM Qos support				
			AckPolicy1~4		Ack policy which support normal Ack or no Ack
								(AC_BK, AC_BE, AC_VI, AC_VO)		
	
	All WMM parameters do not support iwpriv command but ¡¥WmmCapable¡¦¡¦, 
	please store all parameter to RT2870STA.dat, and restart driver. 	

-----------------------------------------------
syntax is 'Param'='Value' and describes below. 

@> CountryRegion=value                                 
	value
		0: use 1 ~ 11 Channel
		1: use 1 ~ 13 Channel
		2: use 10 ~ 11 Channel
		3: use 10 ~ 13 Channel
		4: use 14 Channel
		5: use 1 ~ 14 Channel
		6: use 3 ~ 9 Channel
		7: use 5 ~ 13 Channel
   	 	                                      
@> CountryRegionABand=value      							
	value	
		0: use 36, 40, 44, 48, 52, 56, 60, 64, 149, 153, 157, 161, 165 Channel
		1: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140 Channel
		2: use 36, 40, 44, 48, 52, 56, 60, 64 Channel
		3: use 52, 56, 60, 64, 149, 153, 157, 161 Channel
		4: use 149, 153, 157, 161, 165 Channel
		5: use 149, 153, 157, 161 Channel
		6: use 36, 40, 44, 48 Channel
		7: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140, 149, 153, 157, 161, 165 Channel
		8: use 52, 56, 60, 64 Channel
		9: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 132, 136, 140, 149, 153, 157, 161, 165 Channel
	   10: use 36, 40, 44, 48, 149, 153, 157, 161, 165 Channel
	   11: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 149, 153, 157, 161 Channel

@> CountryCode=value
	value
		AG, AR, AW, AU, AT, BS, BB, BM, BR, BE, BG, CA, KY, CL, CN, CO, CR, CY, CZ, DK, DO, EC, SV, FI, FR, DE, 
		GR, GU, GT, HT, HN, HK, HU, IS, IN, ID, IE, IL, IT, JP, JO, LV, LI, LT, LU, MY, MT, MA, MX, NL, NZ, NO,
		PE, PT, PL, RO, RU, SA, CS, SG, SK, SI, ZA, KR, ES, SE, CH, TW, TR, GB, UA, AE, US, VE
		"" => using default setting: 2.4 G - ch 1~11; 5G - ch 52~64, 100~140, 149~165
                                                           
@> SSID=value                	
	value
		0~z, 1~32 ascii characters.
                    	
@> WirelessMode=value
	value	
		0: legacy 11b/g mixed 
		1: legacy 11B only 
		2: legacy 11A only         //Not support in RfIcType=1(id=RFIC_5225) and RfIcType=2(id=RFIC_5325)
		3: legacy 11a/b/g mixed     //Not support in RfIcType=1(id=RFIC_5225) and RfIcType=2(id=RFIC_5325)
		4: legacy 11G only
		5: 11ABGN mixed
		6: 11N only
		7: 11GN mixed
		8: 11AN mixed
		9: 11BGN mixed
	   10: 11AGN mixed	
                     
@> Channel=value
	value
		depends on CountryRegion or CountryRegionABand
                    	
@> BGProtection=value
	value
		0: Auto 
		1: Always on 
		2: Always off
                    	
@> TxPreamble=value
  	value
		0:Preamble Long
		1:Preamble Short 
		2:Auto
                    	
@> RTSThreshold=value
	value
		1~2347                                                       
                    	                                       
@> FragThreshold=value
	value       	
		256~2346
                    	
@> TxBurst=value
	value
		0: Disable
		1: Enable

@> NetworkType=value	    		
	value 
		Infra: infrastructure mode
       	Adhoc: adhoc mode
                                                                                                                                                        	                                                          
@> AuthMode=value
	value
		OPEN	 	For open system	
		SHARED	  	For shared key system	
		WEPAUTO     Auto switch between OPEN and SHARED
		WPAPSK      For WPA pre-shared key  (Infra)
		WPA2PSK     For WPA2 pre-shared key (Infra)
		WPANONE		For WPA pre-shared key  (Adhoc)
		WPA         Use WPA-Supplicant
		WPA2        Use WPA-Supplicant

@> EncrypType=value
	value
		NONE		For AuthMode=OPEN                    
		WEP			For AuthMode=OPEN or AuthMode=SHARED 
		TKIP		For AuthMode=WPAPSK or WPA2PSK                    
		AES			For AuthMode=WPAPSK or WPA2PSK                     
		
@> DefaultKeyID=value
	value
		1~4

@> Key1=value
    Key2=value
    Key3=value
    Key4=value
	value
		10 or 26 hexadecimal characters eg: 012345678
        5 or 13 ascii characters eg: passd
    (usage : "iwpriv" only)     

@> Key1Type=vaule
    Key2Type=value
    Key3Type=vaule
    Key4Type=vaule
    value
		0   hexadecimal type
		1   assic type
    (usage : reading profile only)

@> Key1Str=value
    Key2Str=value
    Key3Str=vaule
    Key4Str=vaule
    value
		10 or 26 characters (key type=0)
		5 or 13 characters  (key type=1)
    (usage : reading profile only)	

@> WPAPSK=value              	
	value
		8~63 ASCII  		or 
		64 HEX characters
																                    																		
@> WmmCapable=value
	value
		0: Disable WMM
		1: Enable WMM
        
@> PSMode=value
    value
    	CAM			    Constantly Awake Mode
		Max_PSP		    Max Power Savings
		Fast_PSP		Power Save Mode

@> FastRoaming=value
	value
		0				Disabled
		1				Enabled

@> RoamThreshold=value
	value
		Positive Interger(dBm)

@> HT_RDG=value
	value
		0				Disabled
		1				Enabled

@> HT_EXTCHA=value (Extended Channel Switch Announcement)
	value
		0				Below
		1 				Above

@> HT_OpMode=value
	value
		0				HT mixed format
		1				HT greenfield format

@> HT_MpduDensity=value
	value (based on 802.11n D2.0)
		0: no restriction
		1: 1/4 £gs
		2: 1/2 £gs
		3: 1 £gs
		4: 2 £gs
		5: 4 £gs
		6: 8 £gs
		7: 16 £gs

@> HT_BW=value
	value
		0				20MHz
		1				40MHz

@> HT_AutoBA=value
	value
		0				Disabled
		1				Enabled

@> HT_BADecline
	value
		0				Disabled
		1			    Enabled <Reject BA request from AP>

@> HT_AMSDU=value
	value
		0				Disabled
		1				Enabled

@> HT_BAWinSize=value
	value
		1 ~ 64

@> HT_GI=value
	value
		0				long GI
		1				short GI

@> HT_MCS=value
	value
		0 ~ 15
		33: auto

@> HT_MIMOPSMode=value
	value (based on 802.11n D2.0)
		0				Static SM Power Save Mode
		1				Dynamic SM Power Save Mode
		2				Reserved
		3				SM enabled
	(not fully support yet)

@> IEEE80211H=value
	value
		0				Disabled
		1				Enabled

@> TGnWifiTest=value
	value
		0				Disabled
		1				Enabled

@> WirelessEvent=value
	value
		0				Disabled
		1				Enabled <send custom wireless event>
	    
MORE INFORMATION
=================================================================================
If you want for rt2870 driver to auto-load at boot time:
A) choose ra0 for first RT2870 WLAN card, ra1 for second RT2870 WLAN card, etc.
   
B) create(edit) 'ifcfg-ra0' file in /etc/sysconfig/network-scripts/,      
   edit( or add the line) in /etc/modules.conf:
       alias ra0 rt2870sta
   
C) edit(create) the file /etc/sysconfig/network-scripts/ifcfg-ra0  
   DEVICE='ra0'
   ONBOOT='yes'     


NOTE:
   if you use dhcp, add this line too .
    BOOTPROTO='dhcp'

*D) To ease the Default Gateway setting, 
    add the line
    GATEWAY=x.x.x.x   
    in /etc/sysconfig/network
=======================================================================

 
```

---

### Post by diablo75 on 2009-01-23
If I were you I'd leave messing around with all that Greek on the back burner and try a couple of different things.

Before anything, I'd hook the laptop up to a hardline connection to the Internet and download all available updates.  Then I'd just plug it in, turn on the laptop and shoot for the moon by checking with the network manager at the top panel to see if it works.  If it didn't, I'd then check with System>Administration>Hardware Drivers and see if there is a driver that needs to be enabled/activated to get it to work.  It's usually as simple as clicking on an activate button, waiting a bit for the drivers to download and install, and perhaps restarting the computer.

If that doesn't work, I would install ndiswrapper (you can find it in Applications>Add/Remove...) and use it to install Windows drivers instead of Linux drivers.

---

### Post by cariboo on 2009-01-23
Before trying to compile drivers that are already in the kernel, in an Applications-->Accessories-->Terminal type:

```
sudo lshw -C network
```

This command will list your network cards settings as well as listing the driver.

If the driver is listed in the output, in the same terminal type:

```
sudo iwconfig wlan0
```

next in the same terminal type:

```
sudo dhclient wlan0
```

to see if you get an ip address.

Jim

---

### Post by Rhythmdvl on 2009-01-27
Wow, so close. Thanks. 

The Edimax drivers are wrapped inside an exe/installshield file (i.e., not just a zip), so I can't get to them yet. The great folks at Edimax said they were working on new Linux documentation and offered to send me the files directly, I'm still waiting on them. 

I also had a Linksys USB-G wireless USB device and tried Cariboo's suggestion. It had drivers, but the iwconfig resulted in 
```
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1d:7e:03:ba:49
Sending on   LPF/wlan0/00:1d:7e:03:ba:49
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I'm off to see what I can find regarding WAP2 utilities/configuration, both from the Linux side and from the Web interface side of the router. Anyh suggestions, of course, will be much appreciated. 

But thanks so far...

---

### Post by robbiemac on 2009-09-05
This from a review of the product at Amazon:

> Here is a short description of the steps I followed to install the 
Linux kernel module. My system is Debian lenny x86_64 with Linux 
kernel 2.6.26-2-amd64. 

Step 1. It is necessary to compile the new Linux kernel module.  You 
need these: gcc, make, and the kernel header files.  These you should 
get with your distribution of Linux.  I chose to use the 
wpa_supplicant program provided by Debian. If you are using Debian, 
modify the kernel version and issue this command: 'apt-get install 
wpasupplicant make gcc linux-headers-2.6.26-2-amd64'. 

Step 2. Sources for the modules are included on a cd-rom from Edimax. 
However, rather than use the supplied sources, I chose to get the 
latest version which is available from Ralink.  Go to this URL: 
'http://www.ralinktech.com/ralink/Home/Support/Linux.html' and 
download the latest version of the drivers for 
RT2870USB(RT2870/RT2770). The file that I downloaded was created on 
May 21, 2009, is version 2.1.2.0, hence is named 
'2009_0521_RT2870_Linux_STA_V2.1.2.0.tgz'.  Save the file in a 
convenient location. I put mine in /pub/RalinkWireless/. 

Step 3. Extract the files: 

> cd /pub/RalinkWireless/ 
> tar xvfz 2009_0521_RT2870_Linux_STA_V2.1.2.0.tgz 

Step 4. Configure: 

> cd 2009_0521_RT2870_Linux_STA_V2.1.2.0/ 

Using emacs (or your favorite text editor), open the file 
os/linux/config.mk and change the values of the following variables: 

HAS_WPA_SUPPLICANT=y 
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y 

Save and exit. 

Step 5. Login as root. You probably already know how to do this. 

Step 6. Compile the drivers: 

> make 
> cp RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat 

Step 7. Load the kernel module and use dhcp to establish a connection: 

> insmod /pub/RalinkWireless/2009_0521_RT2870_Linux_STA_V2.1.2.0/os/linux/rt2870sta.ko 
> ifconfig ra0 inet up 
> dhclient ra0 

Have fun![]("http://www.amazon.com/review/R2JEDQVRFID33O/ref=cm_cr_dp_cmt?ie=UTF8&ASIN=B00146ILHI&nodeID=172282#wasThisHelpful")

---

