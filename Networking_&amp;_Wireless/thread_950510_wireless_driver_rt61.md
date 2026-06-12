---
title: "wireless driver rt61"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by propagation_of_sound on 2008-10-17
so, I've just installed Ubuntu Studio 8.04. (64 bit)
Everything's great and easy to use. 
However, I've tried to install the driver for my wireless g card (Linksys Wireless G PCI adapter), which I've found out is the rt61 driver from RaLink. I've downloaded the driver file and followed the instructions in the enclosed README file, but I have encountered errors. HERE is the README file:
[INDENT][I]* README

*

* Ralink Tech Inc.

* 

* [http://www.ralinktech.com](http://www.ralinktech.com)

*



=======================================================================

ModelName:

===========

RT61 Wireless Lan Linux Driver





=======================================================================

Driver lName:

===========

rt61.o/rt61.ko





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

Makefile.4	        : Makefile for kernel 2.4 series

Makefile.6	        : Makefile for kernel 2.6 series

Makefile.RTL865x	: Makefile for big endian platform

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



1> $tar -xvzf RT61_Linux_STA_Drv_x.x.x.x.tar.gz

    go to "./RT61_Linux_STA_Drv_x.x.x.x/Module" directory.

    

2> $cp Makefile.4  ./Makefile       # [kernel 2.4]

    or

   $cp Makefile.6  ./Makefile       # [kernel 2.6]

    or

   $cp Makefile.RTL865x ./Makefile  #  big endian platform

   

3> [kernel 2.4]

    $chmod 755 Configure

    $make config         # config build linux os version



4> $make all            # compile driver source code

4.1> $make install



5> $cp rt2561.bin /etc/Wireless/RT61STA/	# copy firmware

   $cp rt2561s.bin /etc/Wireless/RT61STA/

   $cp rt2661.bin /etc/Wireless/RT61STA/



6>  $dos2unix rt61sta.dat

    $cp rt61sta.dat  /etc/Wireless/RT61STA/rt61sta.dat       

    # !!!check if it is a binary file before loading !!!  

    

7> $load                

    #[kernel 2.4]

    #    $/sbin/insmod rt61.o

    #    $/sbin/ifconfig ra0 inet YOUR_IP up

        

    #[kernel 2.6]

    #    $/sbin/insmod rt61.ko

    #    $/sbin/ifconfig ra0 inet YOUR_IP up



        

Note: Script functionality:

load            load module to kernel

unload          unload module from kernel

Configure       retrieve linux version 





=======================================================================

CONFIGURATION:  

====================

RT61 driver can be configured via following interfaces, 

i.e. (i)"iwconfig" command, (ii)"iwpriv" command, (iii) configuration file,

     (iv)RaConfig61



i)  iwconfig comes with kernel.  

ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for details.

iii)copy configuration file "rt61sta.dat" to /etc/Wireless/RT61STA/rt61sta.dat.

iv) RaConfig61 is utility for rt61.

           

Configuration File : rt61sta.dat

---------------------------------------

# Copy this file to /etc/Wireless/RT61STA/rt61sta.dat

# This file is a binary file and will be read on loading rt.o module.

#

# Use "vi -b rt61sta.dat" to modify settings according to your need.

# 

# 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infrastructure

# 2.) set Channel to "0" for auto-select on Infrastructure mode

# 3.) set SSID for connecting to your Accss-point.

# 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE"

# 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES"

# for more information refer to the Readme file.

# 

# The word of "[Default]" must not be removed

[Default]

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

WPAPSK=abcdefghijklmnopqrstuvwxyz

TxBurst=0

PktAggregate=0

WmmCapable=0

APSDCapable=0

APSDAC=0;0;0;0

BGProtection=0

ShortSlot=0

IEEE80211H=0

TxRate=0

RTSThreshold=2347

FragThreshold=2346

PSMode=CAM

TxPreamble=0

FastRoaming=0

NativeWpa=1



-----------------------------------------------

*NOTE:

WMM parameters:

1.) WmmCapable			

    Set it as 1 to turn on WMM Qos support

	

2.) APSDCapable

	Set it as 1 to use automatic power-save delivery(APSD) on an Non-AP QSTA



3.) APSDAC

	Set ACs corresponding BE, BK, VI and VO as delivery-enabled or delivery-disabled



	

All WMM parameters do not support iwpriv command but WmmCapable, 

	please store all parameter to rt61sta.dat, and restart driver. 	







NetworkManager and WPS:

If Native WPA Supplicant (NetworkManager) is enabled, WPS CAN NOT be triggered.

For this case, we have to set NativeWpa=1 in rt61sta.dat.

Otherwise, if we want to use WPS, we have to disable NetworkManager by setting

NativeWpa=0 in rt61sta.dat.



-----------------------------------------------

syntax is 'Param'='Value' and describes below. 



1. CountryRegion=value                                 

	value

		0: use 1 ~ 11 Channel

		1: use 1 ~ 13 Channel

		2: use 10, 11 Channel

		3: use 10 ~ 13 Channel

		4: use 14 Channel

		5: use 1 ~ 14 Channel

		6: use 3 ~ 9 Channel

		7: use 5 ~ 13 Channel

   	 	                                      

2. CountryRegionABand=value      							

	value	

		0: use 36, 40, 44, 48, 52, 56, 60, 64, 149, 153, 157, 161, 165 Channel

		1: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140 Channel

		2: use 36, 40, 44, 48, 52, 56, 60, 64 Channel

		3: use 52, 56, 60, 64, 149, 153, 157, 161 Channel

		4: use 149, 153, 157, 161, 165 Channel

		5: use 149, 153, 157, 161 Channel

		6: use 36, 40, 44, 48 Channel

		7: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140, 149, 153, 157, 161, 165 Channel

		8: 52, 56, 60, 64 Channel

		9: 34, 38, 42, 46 Channel

		10: 34, 36, 38, 40, 42, 44, 46, 48, 52, 56, 60, 64 Channel

                                                   

3. SSID=value                	

	value

		0~z, 1~32 ascii characters.

                    	

4. WirelessMode=value

	value	

		0: 11b/g mixed 

		1: 11B only 

		2: 11A only          //Support in RfIcType=1(id=RFIC_5225) or RfIcType=2(id=RFIC_5325)

		3: 11a/b/g mixed     //Support in RfIcType=1(id=RFIC_5225) or RfIcType=2(id=RFIC_5325)

		4: 11G only

		

5. TxRate=value

	value

		 0: Auto    	//WirelessMode=0~4	

		 1: 1 Mbps	 	//WirelessMode=0 or 1 or 3

         2: 2 Mbps	 	//WirelessMode=0 or 1 or 3

         3: 5.5 Mbps 	//WirelessMode=0 or 1 or 3

         4: 11 Mbps 	//WirelessMode=0 or 1 or 3

         5: 6  Mbps  	//WirelessMode=0 or 2 or 3 or 4

         6: 9  Mbps  	//WirelessMode=0 or 2 or 3 or 4

         7: 12 Mbps  	//WirelessMode=0 or 2 or 3 or 4

         8: 18 Mbps  	//WirelessMode=0 or 2 or 3 or 4

         9: 24 Mbps  	//WirelessMode=0 or 2 or 3 or 4

        10: 36 Mbps  	//WirelessMode=0 or 2 or 3 or 4

        11: 48 Mbps  	//WirelessMode=0 or 2 or 3 or 4

        12: 54 Mbps  	//WirelessMode=0 or 2 or 3 or 4

 	                                       

6. Channel=value

	value

		depends on CountryRegion or CountryRegionABand

                    	

7. BGProtection=value

	value

		0: Auto 

		1: Always on 

		2: Always off

                    	

8. TxPreamble=value

  	value

		0:Preamble Long

		1:Preamble Short 

		2:Auto

                    	

9. RTSThreshold=value

	value

		1~2347                                                       

                    	                                       

10. FragThreshold=value

	value       	

		256~2346

                    	

11. TxBurst=value

	value

		0: Disable

		1: Enable



12. NetworkType=value	    		

	value 

		Infra: infrastructure mode

       	Adhoc: adhoc mode

                                                                                                                                                        	                                                          

13. AuthMode=value

	value

		OPEN	 	For open system	

		SHARED	  	For shared key system	

		WEPAUTO     Auto switch between OPEN and SHARED

		WPAPSK      For WPA pre-shared key  (Infra)

		WPA2PSK     For WPA2 pre-shared key (Infra)

		WPANONE		For WPA pre-shared key  (Adhoc)

		WPA         Use WPA_Supplicant

		WPA2        Use WPA_Supplicant



14. EncrypType=value

	value

		NONE		For AuthMode=OPEN                    

		WEP			For AuthMode=OPEN or AuthMode=SHARED 

		TKIP		For AuthMode=WPAPSK or WPA2PSK                    

		AES			For AuthMode=WPAPSK or WPA2PSK                     

		

15. DefaultKeyID=value

	value

		1~4



16. Key1=value

    Key2=value

    Key3=value

    Key4=value

	value

		10 or 26 hexadecimal characters eg: 012345678

        5 or 13 ascii characters eg: passd

    (usage : "iwpriv" only)     



17. Key1Type=vaule

    Key2Type=value

    Key3Type=vaule

    Key4Type=vaule

    value

		0   hexadecimal type

		1   assic type

    (usage : reading profile only)



18. Key1Str=value

    Key2Str=value

    Key3Str=vaule

    Key4Str=vaule

    value

		10 or 26 characters (key type=0)

		5 or 13 characters  (key type=1)

    (usage : reading profile only)	



19. WPAPSK=value              	

	value

		8~63 ASCII  		or 

		64 HEX characters



20. PktAggregate=value

	value

		0: Disable

		1: Enable when the peer supports it

																

21. WmmCapable=value

	value

		0: Disable WMM

		1: Enable WMM

        

22. PSMode=value

    value

    	CAM			    Constantly Awake Mode

		Fast_PSP		Power Save Mode

		MAX_PSP			Max power save mode

		

23. IEEE80211H=value

	value

		0:	Disable

		1:	Enable	Spectrum management

		(This field can be enable only in A band)

		

24. FastRoaming=value				

	value

		0: Disable Fast Roaming

		1: Enable Fast Roaming



25. RoamThreshold=value

	value [Valid on FastRoaming=1]      	

		60~90



26. APSDCapable=value

	value [Valid on WmmCapable=1]

		0: Disable APSD

		1: Enable APSD



27. APSDAC=value

	value [Valid on APSDCapable=1]

		0: Delivery-disabled AC 

		1: Delivery-enabled AC

	

		//========================//

		AC_BE  AC_BK  AC_VI  AC_VO

		{0, 1};{0, 1};{0, 1};{0, 1}

        //========================//







MORE INFORMATION

=================================================================================

If you want for rt61 driver to auto-load at boot time:

A) choose ra0 for first RT61 WLAN card, ra1 for second RT61 WLAN card, etc.

 

B) go to "./RT61_Linux_STA_Drv_x.x.x.x/Module" directory.

   $make install



NOTE:

	if you use dhcp, 

	add this line

	BOOTPROTO='dhcp'

	in the file ifcfg-ra0 .





*C) To ease the Default Gateway setting, 

    add the line

    GATEWAY=x.x.x.x   

    in /etc/sysconfig/network



D) When build for SUSE, please unmark the part for SUSE in Makefile.

   When build for Mandriva 2007.1, please unmark the part for Mandriva in Makefile.[/INDENT][/I]

The first error I encounter is:

[INDENT]joshua@ubuntu:~/2008_0723_RT61_Linux_STA_v1.1.2.2/Module$ cp Makefile.6 ./Makefile
joshua@ubuntu:~/2008_0723_RT61_Linux_STA_v1.1.2.2/Module$ make all
make -C /lib/modules/2.6.24-21-rt/build SUBDIRS=/home/joshua/2008_0723_RT61_Linux_STA_v1.1.2.2/Module modules
make: *** /lib/modules/2.6.24-21-rt/build: No such file or directory. Stop.
make: *** [all] Error 2
joshua@ubuntu:~/2008_0723_RT61_Linux_STA_v1.1.2.2/Module$ 

[/INDENT]

Please could you help me to understand what this is actually saying?

Thanks in advance

[I]I am running:
Linux ubuntu 2.6.24-21-rt #1 SMP PREEMPT RT Mon Aug 25 18:23:02 UTC 2008 x86_64 GNU/Linux
AMD 2.1GHz dual core
2GB RAM
500GB HDD - Windows XP
40GB HDD - Ubuntu

750GB USB HDD

[/I]

---

### Post by Ayuthia on 2008-10-17
> **propagation_of_sound said:**
> 
The first error I encounter is:

[INDENT]joshua@ubuntu:~/2008_0723_RT61_Linux_STA_v1.1.2.2/Module$ cp Makefile.6 ./Makefile
joshua@ubuntu:~/2008_0723_RT61_Linux_STA_v1.1.2.2/Module$ make all
make -C /lib/modules/2.6.24-21-rt/build SUBDIRS=/home/joshua/2008_0723_RT61_Linux_STA_v1.1.2.2/Module modules
make: *** /lib/modules/2.6.24-21-rt/build: No such file or directory. Stop.
make: *** [all] Error 2
joshua@ubuntu:~/2008_0723_RT61_Linux_STA_v1.1.2.2/Module$ 

[/INDENT]

Please could you help me to understand what this is actually saying?



There is a link that is created in /lib/modules/2.6.24-21-rt/build that points to /usr/src/linux-headers-2.6.24-21-rt.  It looks like the linux-headers-2.6.24-21-rt package was not installed.  You should go into Synaptic (or whichever package manager that you use) and see if you have it installed.

However, the rt61_pci module should be built-in the Hardy.  Have you tried and see if you can connect to it?

Also, I think that serialmonkey is the site for the rt61 drivers.  At least that is where I downloaded and installed mine in Arch when I had problems with the rt61_pci module (which worked fine in Ubuntu).  Here is the link:
[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

---

### Post by propagation_of_sound on 2008-10-17
Thanks. 

However, I remember the headers being installed yesterday when I updated for the first time. The only thing is that there is no /build directory, and I can't create one. 

As regards to the connection with the pci card, ubuntu recognises the card. Does this mean that the driver is already working? I suddenly realise I might have spent a long time messing around with no need. 
In Windows, the card's activity light turns on whilst booting, but this does not happen in Linux. That's what led me to think that there was no driver.

---

### Post by Ayuthia on 2008-10-17
> **propagation_of_sound said:**
> Thanks. 

However, I remember the headers being installed yesterday when I updated for the first time. The only thing is that there is no /build directory, and I can't create one. 

As regards to the connection with the pci card, ubuntu recognises the card. Does this mean that the driver is already working? I suddenly realise I might have spent a long time messing around with no need. 
In Windows, the card's activity light turns on whilst booting, but this does not happen in Linux. That's what led me to think that there was no driver.

It might be possible that it already works.  Can you post the following:
```
lshw -C network
sudo iwlist scan
```

---

### Post by propagation_of_sound on 2008-10-18
as requested...

[INDENT][I]joshua@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:60:77:a3:ad
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 5
       bus info: pci@0000:03:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64
joshua@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

joshua@ubuntu:~$ 
{I}
[/INDENT]

Is what's going wrong to do with the NETWORK UNCLAIMED?
:confused: I am linux noob

---

### Post by Ayuthia on 2008-10-18
> **propagation_of_sound said:**
> as requested...

[INDENT][I]joshua@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:60:77:a3:ad
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 5
       bus info: pci@0000:03:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64
joshua@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

joshua@ubuntu:~$ 
{I}
[/INDENT]

Is what's going wrong to do with the NETWORK UNCLAIMED?
:confused: I am linux noob

You can try the following (from the Terminal):
```
sudo modprobe rt61_pci
sudo iwlist scan
```

---

### Post by propagation_of_sound on 2008-10-20
I typed in the commands and the terminal says:

joshua@ubuntu:~$ sudo modprobe rt61_pci
FATAL: Module rt61_pci not found.
joshua@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

joshua@ubuntu:~$ 

:???:

---

### Post by propagation_of_sound on 2008-10-20
maybe the command is:

sudo modprobe rt61pci

i'll see whether that command works

:)

---

### Post by propagation_of_sound on 2008-10-20
tried sudo modprobe rt61pci instead:

joshua@ubuntu:~$ sudo modprobe rt61pci
joshua@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:E2:D5:03:9D
                    ESSID:"BTHomeHub2-SRGZ"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/100  Signal level=-68 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000000a9b0ac03
          Cell 02 - Address: 00:18:4D:FC:E0:3A
                    ESSID:"SKY53954"
                    Mode:Master
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=52/100  Signal level=-46 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000016595bb16

joshua@ubuntu:~$ 




The green LED on the card has illuminated now!
I want to connect to SKY53954 - how will I do that?

Methinks we're getting somewhere!:)

---

### Post by Ayuthia on 2008-10-20
I think that you should be able to get connected through network manager now.  I don't have very much experience with WPA so I can't really help you connect to your router.

---

### Post by propagation_of_sound on 2008-10-21
Thank you very much. 

I've noticed that the card only works if I open up terminal and type

sudo modprobe rt61pci

once booted. 

How would I do this automatically on boot?

Thank you again.

---

### Post by Ayuthia on 2008-10-21
> **propagation_of_sound said:**
> Thank you very much. 

I've noticed that the card only works if I open up terminal and type

sudo modprobe rt61pci

once booted. 

How would I do this automatically on boot?

Thank you again.

Just add the following in the Terminal:
```
echo rt61pci | sudo tee -a /etc/modules
```
This will add the module to /etc/modules.  That file is used to load any additional modules that the kernel did not load.

---

### Post by propagation_of_sound on 2008-10-23
Think I'd just let you guys know I've got my internet working (I'm pleased to note I'm writing this within Linux!). Once I'd downloaded and installed Kwifi Manager and Network Manager and configured the rt61pci module to start up automatically, it worked. 

I'd like to thank Ayuthia very much because I wouldn't have been able to browse the documentation and have the know-how myself. 

=D>:-D

---

