---
title: "Can someone help me install my wireless drivers?"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by Antexter on 2008-01-19
I want to install linux drivers for wireless card, but I am just lost
So I took the tarball of the disk extracted it this is the dir
> computer@kubuntuin:~/RT61STAV1000_K2.6.8-2-386_Debian31$ dir
load* readme* RT2561.bin* RT2561S.bin* RT2661.bin* rt61.ko* RT61STA.dat* STA_iwpriv_ATE_usage.txt* unload

readme
> * README
*
* Ralink Tech Inc.
* 
* [http://www.ralinktech.com](http://www.ralinktech.com)
*

=======================================================================
ModelName:
===========
rt61


=======================================================================
Supporting Kernel:
===================
linux kernel 2.4 and 2.6 series. 
Tested in Redhat 7.3 or later.


=======================================================================
Description:
=============
This is a linux device driver for Ralink RT61 a/b/g WLAN Card.



=======================================================================
Contents:
=============
./2.4x				: Makefile for kernel 2.4 series
./2.6x				: Makefile for kernel 2.6 series
*.c					: c files
*.h					: header files
Makefile.RTL865x	: Makefile for big endian platform



=======================================================================
Features:
==========
* *This driver implements basic IEEE802.11. Infrastructure and adhoc mode with open or shared or 
* *WPA-PSK authentication method. NONE, WEP, TKIP and AES encryption. 



=======================================================================
Build Instructions:* 
====================
For 2.4 series kernel:
a. $tar -xvzf RT61_Linux_STA_Drv_x.x.x.x.tar.gz
* * go to "./RT61_Linux_STA_Drv_x.x.x.x/Module" directory.
* * 
b. Use 'chmod' command to change access right of following script files :
* *'load', 'unload', 'Configure'
 
c. run 'cp ../2.4x/Makefile .'
d. $make config* * * * *# config build linux os version

e. $make all* * * * * * # compile driver source code

f. $cp RT2561.bin /etc/Wireless/RT61STA/	# copy firmware
* *$cp RT2561S.bin /etc/Wireless/RT61STA/
* *$cp RT2661.bin /etc/Wireless/RT61STA/

g. $load* * * * * * * * # load/insmod module(rt61.o)

Note: Script functionality:
load* * * * * * load module to kernel
unload* * * * * unload module from kernel
Configure* * * *retrieve linux version 


For 2.6 series kernel:
a.* run 'cd STA/Module'
* * * * 'cp ../2.6x/Makefile .'

b. $make all

c. $cp RT2561.bin /etc/Wireless/RT61STA/	# copy firmware
* *$cp RT2561S.bin /etc/Wireless/RT61STA/
* *$cp RT2661.bin /etc/Wireless/RT61STA/
* *
d.* run '/sbin/insmod rt61.ko'* (as root)
* * * * '/sbin/ifconfig ra0 inet YOUR_IP up' 


For big endian platform:
a.* replace Makefile with Makefile.RTL865x
* 
 

=======================================================================
CONFIGURATION:* 
====================
RT61 driver can be configured via following interfaces, 
i.e. (i)"iwconfig" command, (ii)"iwpriv" command, (iii) configuration file

i)* iwconfig comes with kernel.* 
ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for details.
iii)copy configuration file "RT61STA.dat" to /etc/Wireless/RT61STA/RT61STA.dat.

* * * * * *
Configuration File : RT61STA.dat
---------------------------------------
# Copy this file to /etc/Wireless/RT61STA/RT61STA.dat
# This file is a binary file and will be read on loading rt.o module.
#
# Use "vi -b RT61STA.dat" to modify settings according to your need.
# 
# 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infrastructure
# 2.) set Channel to "0" for auto-select on Infrastructure mode
# 3.) set SSID for connecting to your Accss-point.
# 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPANONE"
# 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES"
# for more information refer to the Readme file.
# 
# The word of "Default" must not be removed
Default
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=AP350
NetworkType=Infra
Channel=0
AuthMode=OPEN
EncrypType=NONE
DefaultKeyID=1
Key1Type=0
Key1Str=0123456789
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WpaPsk=abcdefghijklmnopqrstuvwxyz
TXBurst=0
PktAggregate=0
TurboRate=0
WmmCapable=0
AckPolicy1=0
AckPolicy2=0
AckPolicy3=0
AckPolicy4=0
BGProtection=0
ShortSlot=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
PSMode=CAM
TxPreamble=0

-----------------------------------------------
*NOTE:
	WMM parameters
			WmmCapable			Set it as 1 to turn on WMM Qos support				
			AckPolicy1~4		Ack policy which support normal Ack or no Ack
								(AC_BK, AC_BE, AC_VI, AC_VO)		
	
	All WMM parameters do not support iwpriv command but &#65533;&#65533;WmmCapable&#65533;&#65533;&#65533;&#65533;, 
	please store all parameter to RT61STA.dat, and restart driver. 	

-----------------------------------------------
syntax is 'Param'='Value' and describes below. 

1. CountryRegion=value* * * * * * * * * * * * * * * * *
	value
		0: use 1 ~ 11 Channel
		1: use 1 ~ 13 Channel
		2: use 10, 11 Channel
		3: use 10 ~ 13 Channel
		4: use 14 Channel
		5: use 1 ~ 14 Channel
		6: use 3 ~ 9 Channel
* *	 	* * * * * * * * * * * * * * * * * * * 
2. CountryRegionForABand=value* * * 							
	value	
		0: use 36, 40, 44, 48, 52, 56, 60, 64, 149, 153, 157, 161, 165 Channel
		1: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140 Channel
		2: use 36, 40, 44, 48, 52, 56, 60, 64 Channel
		3: use 52, 56, 60, 64, 149, 153, 157, 161 Channel
		4: use 149, 153, 157, 161, 165 Channel
		5: use 149, 153, 157, 161 Channel
		6: use 36, 40, 44, 48 Channel
		7: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140, 149, 153, 157, 161, 165 Channel
* * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
3. SSID=value* * * * * * * * 	
	value
		0~z, 1~32 ascii characters.
* * * * * * * * * * 	
4. WirelessMode=value
	value	
		0: 11b/g mixed, 
		1: 11B only, 
		2: 11A only
		3: 11a/b/g mixed
		4: 11G only	
* * * * * * * * * * 	
5. TxRate=value
	value
		 0: Auto* * 	//WirelessMode=0~4	
		 1: 1 Mbps	 	//WirelessMode=0 or 1 or 3
* * * * *2: 2 Mbps	 	//WirelessMode=0 or 1 or 3
* * * * *3: 5.5 Mbps 	//WirelessMode=0 or 1 or 3
* * * * *4: 11 Mbps 	//WirelessMode=0 or 1 or 3
* * * * *5: 6* Mbps* 	//WirelessMode=0 or 2 or 3 or 4
* * * * *6: 9* Mbps* 	//WirelessMode=0 or 2 or 3 or 4
* * * * *7: 12 Mbps* 	//WirelessMode=0 or 2 or 3 or 4
* * * * *8: 18 Mbps* 	//WirelessMode=0 or 2 or 3 or 4
* * * * *9: 24 Mbps* 	//WirelessMode=0 or 2 or 3 or 4
* * * * 10: 36 Mbps* 	//WirelessMode=0 or 2 or 3 or 4
* * * * 11: 48 Mbps* 	//WirelessMode=0 or 2 or 3 or 4
* * * * 12: 54 Mbps* 	//WirelessMode=0 or 2 or 3 or 4
 	* * * * * * * * * * * * * * * * * * * *
6. Channel=value
	value
		1~14 depends on CountryRegion
* * * * * * * * * * 	
7. BGProtection=value
	value
		0: Auto 
		1: Always on 
		2: Always off
* * * * * * * * * * 	
8. TxPreamble=value
* 	value
		0:Preamble Long
		1:Preamble Short 
		2:Auto
* * * * * * * * * * 	
9. RTSThreshold=value
	value
		1~2347* * * * * * * * * * * * * * * * * * * * * * * * * * * *
* * * * * * * * * * 	* * * * * * * * * * * * * * * * * * * *
10. FragThreshold=value
	value* * * *	
		256~2346
* * * * * * * * * * 	
11. TxBurst=value
	value
		0: Disable
		1: Enable

12. NetworkType=value	* * 		
	value 
		Infra: infrastructure mode
* * * *	Adhoc: adhoc mode

13. AdhocOfdm=value
	value
		0: Adhere WIFI spec, the Tx MAX rate will be 11Mbps in Adhoc mode
		1: Violate WIFI spec, the Tx MAX rate will be 54Mbps in Adhoc mode(b/g mixed)
		2: Violate WIFI spec, the Tx MAX rate will be 54Mbps in Adhoc mode(11g only)
* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * 	* * * * * * * * * * * * * * * * * * * * * * * * * * * * * 
14. AuthMode=value
	value
		OPEN	 	For Open System	
		SHARED	* 	For Shared key System	
		WEPAUTO
		WPAPSK
		WPANONE		For Adhoc Security System

15. EncrypType=value
	value
		NONE		For AuthMode=OPEN* * * * * * * * * * 
		WEP			For AuthMode=OPEN or AuthMode=SHARED 
		TKIP		For AuthMode=WPAPSK* * * * * * * * * 
		AES			For AuthMode=WPAPSK* * * * * * * * * 
		
16. DefaultKeyID=value
	value
		1~4

17. Key1=value* * * * * * * * *	
	value
		10 or 26 hexadecimal characters eg: 012345678
* * * * 5 or 13 ascii characters eg: passd* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *

18. Key2=value
	value
		10 or 26 hexadecimal characters eg: 012345678
* * * * 5 or 13 ascii characters eg: passd* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *

19. Key3=value
	value
		10 or 26 hexadecimal characters eg: 012345678
* * * * 5 or 13 ascii characters eg: passd* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *

20. Key4=value
	value
		10 or 26 hexadecimal characters eg: 012345678
* * * * 5 or 13 ascii characters eg: passd* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
* * * * * * * * * * * * * * * * * * * * * * * * * * * * 
21. WPAPSK=value* * * * * * * 	
	value
		8~63 ASCII* 		or 
		64 HEX characters

22. PktAggregate=value
	value
		0: Disable
		1: Enable when the peer supports it
																
23. TurboRate=value
	value
		0: Disable
		1: Enable 72/100 Mbps whenever applicable
		(Not support yet!)
* * * * * * * * * * 																		
24. WmmCapable=value				
	value
		0: Disable WMM
		1: Enable WMM

25. PSMode=value
* * value
* * 	0: CAM			Constantly Awake Mode
		1: Max_PSP		Max Power Savings
		2: Fast_PSP		Power Save Mode
		
26. IEEE80211H=value
	value
		0:	Disable
		1:	Enable	Spectrum management
		(This field can be enable only in A band)


MORE INFORMATION
=================================================================================
If you want for rt61 driver to auto-load at boot time:
A) choose ra0 for first RT61 WLAN card, ra1 for second RT61 WLAN card, etc.
* *
B) create(edit) 'ifcfg-ra0' file in /etc/sysconfig/network-scripts/,* * * 
* *edit( or add the line) in /etc/modules.conf:
* * * *alias ra0 rt61* * * * 
* *
C) edit(create) the file /etc/sysconfig/network-scripts/ifcfg-ra0* 
* *DEVICE='ra0'
* *ONBOOT='yes'* * *


NOTE:
* *if you use dhcp, add this line too .
* * BOOTPROTO='dhcp'

*D) To ease the Default Gateway setting, 
* * add the line
* * GATEWAY=x.x.x.x* *
* * in /etc/sysconfig/network
* *

Okay build instructions, I've extracted the tarball in my home folder changed chmod on load and unload but their is no config file.
on "c. run 'cp ../2.4x/Makefile .'" huh?
I don't even have a 2.4x folder.
and if I just copy and paste that its obvious make config doesn't work.

what am I supposed to do?

---

