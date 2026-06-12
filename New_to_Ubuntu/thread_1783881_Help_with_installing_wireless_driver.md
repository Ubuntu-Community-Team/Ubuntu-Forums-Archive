---
title: "Help with installing wireless driver"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by rluebke on 2011-06-16
Ok, sorry if I sound like a n00b but I clearly am. Have used windows (ugh) pretty much all my life. I can follow instructions very well but clearly Xubuntu is a new beast I have yet to explore. I have a RALink wireless adapter that has the Linux driver available, however, this is obviously not as easy to set up on windows where I just open the .exe and the work is basically done. I have 2 sets of files in the folder as well as a readme file which might as well be written in Spanish as it makes basically no sense to me. 

Hopefully someone can help with some steps as to what to do next as my PC is not near my router and it would be a big pain to have to move it just to be able to download the ndiswrapper to be able to use the windows driver (I did notice that there is a decent video on YouTube describing the steps in preforming this.)

Any and all help is GREATLY appreciated as this is basically the next step for me into saying bye bye to the awful os we know as windows!

Thanks in advance,
Rick

---

### Post by computerandu on 2011-06-16
> **rluebke said:**
> Ok, sorry if I sound like a n00b but I clearly am. Have used windows (ugh) pretty much all my life. I can follow instructions very well but clearly Xubuntu is a new beast I have yet to explore. I have a RALink wireless adapter that has the Linux driver available, however, this is obviously not as easy to set up on windows where I just open the .exe and the work is basically done. I have 2 sets of files in the folder as well as a readme file which might as well be written in Spanish as it makes basically no sense to me. 

Hopefully someone can help with some steps as to what to do next as my PC is not near my router and it would be a big pain to have to move it just to be able to download the ndiswrapper to be able to use the windows driver (I did notice that there is a decent video on YouTube describing the steps in preforming this.)

Any and all help is GREATLY appreciated as this is basically the next step for me into saying bye bye to the awful os we know as windows!

Thanks in advance,
Rick

Usually the installation instructions are given in the README or INSTALL file...
could you please post the content of readme...or provide me th link from where you want to download the drivers....


P.S. You don't need to be a Windows hater to love Ubuntu...:)

---

### Post by rluebke on 2011-06-16
[FONT=arial][SIZE=2][COLOR=black][SIZE=2][FONT=Arial, Helvetica, sans-serif]Sorry this is incredibly long but did not want to leave anything important off.

* README
*
* Ralink Tech Inc.
* 
* [http://www.ralinktech.com]("http://www.ralinktech.com/")
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
===================
    common/
    include/
    os/
    os/linux/
    sta/
    tools/
    Makefile
    RT2870STA.dat
    README.txt


=======================================================================
Features:
==========
   This driver implements basic IEEE802.11. Infrastructure and adhoc mode with 
   open or shared or WPA-PSK or WPA2-PSK authentication method. 
   NONE, WEP, TKIP and AES encryption. 


=======================================================================
Build Instructions:  
===================
1> $tar -xvzf RT2870_Linux_STA_Drv_x.x.x.x.tar.gz
    go to "./RT2870_Linux_STA_Drv_x.x.x.x/" directory.

2> prepare the firmware (bin file) and the profile (dat file).
    $cp common/rt2870.bin /etc/Wireless/RT2870STA/
    $cp RT2870STA.dat  /etc/Wireless/RT2870STA/ 

3> compile the source code.
    $make all

4.> go to "os/linux/" directory.
    $load

    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

5.> If you wnat to clean the tree, just "make clean".
    It will clean the target and mode you set.


=======================================================================
CONFIGURATION:  
===================
Driver rt2870sta can be configured via following interfaces, 
i.e. (i) configuration file, (ii)"iwpriv" command, (iii)"iwconfig" command, 

i)    configure with the profile "RT2870STA.dat" when the driver starts
ii)    "iwpriv" - configure private parameters of a wireless network interfac
iii)"iwconfig"- configure a wireless network interface


=======================================================================
i) Configuration File
===================
# Copy this file to /etc/Wireless/RT2870STA/RT2870STA.dat
# This file is a binary file and will be read on loading rt.o module.
#
# Use "vi -b RT2870STA.dat" to modify settings according to your need.
# 
# 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infrastructure
# 2.) set Channel to "0" for auto-select on Infrastructure mode
# 3.) set SSID for connecting to your Accss-point.
# 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE"
# 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES"
# for more information refer to the Readme file.

#The word of "Default" must not be removed
Default
CountryRegion=0
CountryRegionABand=7
SSID=11n-AP
NetworkType=Infra
WirelessMode=5
Channel=0
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
WPAPSK=abcdefghijklmnopqrstuvwxyz
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
HT_HTC=0
HT_RDG=1
HT_OpMode=0
HT_BW=1
HT_BADecline=0
HT_AutoBA=1
HT_GI=1
HT_MCS=33
HT_MpduDensity=0

-----------------------------------------------
*NOTE:
    WMM parameters
            WmmCapable            Set it as 1 to turn on WMM Qos support                
            AckPolicy1~4        Ack policy which support normal Ack or no Ack
                                (AC_BK, AC_BE, AC_VI, AC_VO)        
    
    All WMM parameters do not support iwpriv command but ¡¥WmmCapable¡¦¡¦, 
    please store all parameter to RT2860STA.dat, and restart driver.     

-----------------------------------------------
syntax is 'Param'='Value' and describes below. 

@    CountryRegion=value                         
    value
        0: use 1 ~ 11 Channel
        1: use 1 ~ 13 Channel
        2: use 10 ~ 11 Channel
        3: use 10 ~ 13 Channel
        4: use 14 Channel
        5: use 1 ~ 14 Channel
        6: use 3 ~ 9 Channel
        7: use 5 ~ 13 Channel

@    CountryRegionForABand=value
    value
        0: use 36, 40, 44, 48, 52, 56, 60, 64, 149, 153, 157, 161, 165 Channel
        1: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140 Channel
        2: use 36, 40, 44, 48, 52, 56, 60, 64 Channel
        3: use 52, 56, 60, 64, 149, 153, 157, 161 Channel
        4: use 149, 153, 157, 161, 165 Channel
        5: use 149, 153, 157, 161 Channel
        6: use 36, 40, 44, 48 Channel
        7: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116,  120, 124, 128, 132, 136, 140, 149, 153, 157, 161, 165 Channel
        8: use 52, 56, 60, 64 Channel
        9: use 34, 38, 42, 46 Channel
        10 use 34, 36, 38, 40, 42, 44, 46, 48, 52, 56, 60, 64 Channel

@    SSID=value
    value
        0~z, 1~32 ascii characters.

@    WirelessMode=value
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

@    Channel=value
    value
        depends on CountryRegion or CountryRegionForABand

@    BGProtection=value
    value
        0: Auto
        1: Always on
        2: Always off

@    TxPreamble=value
      value
        0:Preamble Long
        1:Preamble Short
        2:Auto

@    RTSThreshold=value
    value
        1~2347

@    FragThreshold=value
    value
        256~2346

@    TxBurst=value
    value
        0: Disable
        1: Enable

@    NetworkType=value
    value
        Infra: infrastructure mode
           Adhoc: adhoc mode

@    AuthMode=value
    value
        OPEN         For open system
        SHARED          For shared key system
        WEPAUTO     Auto switch between OPEN and SHARED
        WPAPSK      For WPA pre-shared key  (Infra)
        WPA2PSK     For WPA2 pre-shared key (Infra)
        WPANONE        For WPA pre-shared key  (Adhoc)
        WPA            Use WPA-Supplicant
        WPA2        Use WPA-Supplicant

@    EncrypType=value
    value
        NONE        For AuthMode=OPEN
        WEP            For AuthMode=OPEN or SHARED 
        TKIP        For AuthMode=WPAPSK or WPA2PSK or WPANONE
        AES            For AuthMode=WPAPSK or WPA2PSK or WPANONE

@    DefaultKeyID=value
    value
        1~4

@    Key1=value
    Key2=value
    Key3=value
    Key4=value
    value
        10 or 26 hexadecimal characters eg: 012345678
        5 or 13 ascii characters eg: passd
    (usage : "iwpriv" only)

@    Key1Type=vaule
    Key2Type=value
    Key3Type=vaule
    Key4Type=vaule
    value
        0    hexadecimal type
        1     assic type

@    Key1Str=value
    Key2Str=value
    Key3Str=vaule
    Key4Str=vaule
    value
        10 or 26 characters (key type=0)
        5 or 13 characters  (key type=1)

@    WPAPSK=value
    value
        8~63 ASCII            or 
        64 HEX characters

@    WmmCapable=value
    value
        0: Disable WMM
        1: Enable WMM

@    FastRoaming=value
    value
        0: Disable
        1: Enable Fast Roaming

@    RoamThreshold=value
    value
        61 ~ 89
    (This value is a absolute threshold in dBm.
    The condition to roam when receiving Rssi less than (-1*value).)

/* *** 802.11n high throughput configuration*** */
@    HT_RDG=value
    value
        0: Disable 
        1: Enable RDG

@    HT_OpMode=value
    value
        0: Mixed Mode
        1: Green Field

@    HT_MpduDensity=value
    value
        0 ~ 7 integer

@    HT_BW=value
    value
        0: 20 MHz
        1: 20/40 MHz

@    HT_BADecline=value
    value
        0: Accept BA req from AP
        1: Reject BA req from AP

@    HT_AutoBA=value
    value    
        0: Disable 
        1: Enable Auto BA

@    HT_GI=value
    value
        0: Long (800) 
        1: Short (400)
                
@    HT_MCS=value
    value
        0 ~ 15, 32, 33 integer
        33 for Auto
                
-----------------------------------------------------------------------

        
=======================================================================
ii) iwpriv
===================
This is detailed explanation of each parameters for iwpriv.

-----------------------------------------------------------------------
USAGE:
    iwpriv ra0 set [parameters]=[value]
    
NOTE:
    Execute one iwpriv/set command simultaneously.
    

DESCRIPTION
[parameters]            Description / {range} / value
-----------------        -----------------------------------------------
CountryRegion            Set the country region.    
                        { 0 ~ 7 }
                        0: 1 ~ 11
                        1: 1 ~ 13
                        2: 10, 11
                        3: 10 ~ 13
                        4: 14
                        5: 1 ~ 14
                        6: 3 ~ 9
                        7: 5 ~ 13

CountryRegionABand        Set the country region for A band.
                        { 0 ~ 8 }
                        0: 36, 40, 44, 48, 52, 56, 60, 64, 149, 153, 157, 161, 165
                        1: 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140
                        2: 36, 40, 44, 48, 52, 56, 60, 64
                        3: 52, 56, 60, 64, 149, 153, 157, 161
                        4: 149, 153, 157, 161, 165
                        5: 149, 153, 157, 161
                        6: 36, 40, 44, 48
                        7: 36, 40, 44, 48, 52, 56, 60, 64, 100, 104,  108, 112, 116, 120, 124, 128, 132, 136, 140, 149, 153, 157, 161, 165
                        8: 52, 56, 60, 64

SSID                    Set the desired SSID.             
                        { 0 ~ z, 1 ~ 32 ascii characters }
                        
NetworkType                Set the network type.
                        { Infra, Adhoc }

WirelessMode            Set the wireless mode.
                        { 0 ~ 5 }
                        0: 802.11 b/g mixed, 
                        1: 802.11 b only, 
                        2: 802.11 a only,  
                        3: 802.11 a/b/g mixed,
                        4: 802.11 a/b/g/n mixed,
                        5: 802.11 b/g/n mixed
    
Channel                    Set the channel.
                        { Within the range of CountryRegion or CountryRegionABand }
                        0: for auto-select on Infrastructure mode

BGProtection            Set 11B/11G protection.
                        { 0 ~ 2 }
                        0: Auto, 
                        1: Always on, 
                        2: Always off
                        
TxPreamble                Set TX preamble mode.
                        { 0 ~ 2 }
                        0:Preamble Long, 
                        1:Preamble Short, 
                        2:Auto

RTSThreshold            Set RTS threshold.
                        { 1 ~ 2347 }
                        2347: Off

FragThreshold            Set Fragment threshold.
                        { 256 ~ 2346 }
                        2346: Off

TxBurst                    Set TX Burst mode.
                        { 0, 1 }
                        0: Disable, 
                        1: Enable

AuthMode                Set authentication mode.
                        { OPEN, SHARED, WEPAUTO, WPAPSK, WPA2PSK, WPANONE }

EncrypType                Set the encryption type.
                        { NONE, WEP, TKIP, AES }

DefaultKeyID            Set TX default Key ID.
                        { 1 ~ 4 }
                        
Key1                    Set key1 string.
                        { 5 ascii characters or 10 hex number or 
                          13 ascii characters or 26 hex numbers }

Key2                    Set key2 string.
                        { 5 ascii characters or 10 hex number or 
                          13 ascii characters or 26 hex numbers }

Key3                    Set key3 string.
                        { 5 ascii characters or 10 hex number or 
                         13 ascii characters or 26 hex numbers }

Key4                    Set key4 string.
                        { 5 ascii characters or 10 hex number or 
                          13 ascii characters or 26 hex numbers }

WPAPSK                    Set WPA pre-shared key.
                        { 8 ~ 63 ascii or 64 hex characters }

HtOpMode                Set high-throughput operation mode.
                        { 0, 1 }
                        0: Mixed Mode,
                        1: Auto (Mixed Mode or Green Field)

HtBw                    Set high-throughput bandwidth.
                        { 0, 1 }
                        0: 20 MHz,
                        1: Auto (20 or 20/40 MHz)

HtGi                    Set high-throughput Guard Interval.
                        { 0, 1 }
                        0: Long GI, 
                        1: Auto (Long or Short)

HtMcs                    Set high-throughput Modulation Coding Scheme.
                        { 0 ~ 15, 32, 33 }
                        33:    Auto

HtRdg                    Set high-throughput Reverse Direction Grant.(Ralink proprietary)
                        { 0, 1 }
                        0: Disable, 
                        1: Enable

HtMpduDensity            Set high-throughput MPDU Density.
                        { 0 ~ 7 }
                        0: no restriction
                        1: 1/8 £gsec
                        2: 1/4 £gsec
                        3: 1/2 £gsec
                        4: 1 £gsec
                        5: 2 £gsec
                        6: 4 £gsec
                        7: 8 £gsec

HtAutoBa                Set high-throughput Auto Block Ack.
                        { 0, 1 }
                        0: Manual BA, 
                        1: Auto BA
-----------------------------------------------------------------------


=======================================================================
iii) iwlist/iwconfig
===================

iwlist ra0 scanning        ; list the results after scanning(manual rescan)

The following are our support in standard configuration - iwconfig
-----------------------------------------------------------------------
iwconfig ra0 essid {NN|on|off}                ; set ssid
iwconfig ra0 mode {managed|ad-hoc|...}        ; set wireless mode
iwconfig ra0 freq N.NNNN[k|M|G]]                ; set frequency
iwconfig ra0 channel N                        ; set channel
iwconfig ra0 ap {N|off|auto}                    ; set ap address
iwconfig ra0 rate {N|auto|fixed}                ; set rate
iwconfig ra0 rts {N|auto|fixed|off}            ; set rts threshold
iwconfig ra0 frag {N|auto|fixed|off}            ; set fragment threshold
iwconfig ra0 enc {NNNN-NNNN|off}                ; set encryption type
iwconfig ra0 key {[id]|s:pswd|pswd}            ; set wep key

*** Please refer to man page of 'iwconfig', 'iwlist' ***


=======================================================================
Examples
===================

a> Configure STA to link with AP which is OPEN auth and NONE enc.
    1. iwpriv ra0 set NetworkType=Infra
    2. iwpriv ra0 set AuthMode=OPEN
    3. iwpriv ra0 set EncrypType=NONE
    4. iwpriv ra0 set SSID="AP's SSID"

b> Configure STA to link with AP and OPEN auth and WEP enc.
    Default Key ID = 3
    1. iwconfig ra0 key [3]
    2. iwconfig ra0 key s:abcde
    3. iwconfig ra0 essid "AP's SSID"

c> Configure STA to link with AP which is SHARED auth and WEP enc.
    1. iwpriv ra0 set NetworkType=Infra
    2. iwpriv ra0 set AuthMode=SHARED
    3. iwpriv ra0 set EncrypType=WEP
    4. iwpriv ra0 set DefaultKeyID=1
    5. iwpriv ra0 set Key1="AP's wep key"
    6. iwpriv ra0 set SSID="AP's SSID"

d> Configure STA to link with AP which is WPAPSK auth and TKIP enc.
    1. iwpriv ra0 set NetworkType=Infra
    2. iwpriv ra0 set AuthMode=WPAPSK
    3. iwpriv ra0 set EncrypType=TKIP
    4. iwpriv ra0 set SSID="AP's SSID"
    5. iwpriv ra0 set WPAPSK="12345678"
    6. iwpriv ra0 set SSID="AP's SSID"
    
 Note.    Step 4 is part of generating wpapsk password and is necessary.

e> Configure STA to link with AP which is WPA2PSK auth and TKIP enc.
    1. iwpriv ra0 set NetworkType=Infra
    2. iwpriv ra0 set AuthMode=WPA2PSK
    3. iwpriv ra0 set EncrypType=TKIP
    4. iwpriv ra0 set SSID="AP's SSID"
    5. iwpriv ra0 set WPAPSK="12345678"
    6. iwpriv ra0 set SSID="AP's SSID"

f> Configure STA to create an adhoc network, which is OPEN auth and NONE enc.
    1. iwpriv ra0 set NetworkType=Adhoc
    2. iwpriv ra0 set Channel=6
    3. iwpriv ra0 set AuthMode=OPEN
    4. iwpriv ra0 set EncrypType=NONE
    5. iwpriv ra0 set SSID="Adhoc's SSID"

g>  Configure STA to link with an existed adhoc network, which is WPANONE auth and TKIP enc.
    1. iwpriv ra0 set NetworkType=Adhoc
    2. iwpriv ra0 set AuthMode=WPANONE
    3. iwpriv ra0 set EncrypType=TKIP
    4. iwpriv ra0 set SSID="AP's SSID"
    5. iwpriv ra0 set WPAPSK=12345678
    6. iwpriv ra0 set SSID="AP's SSID"

h> Get site survey. 
    iwpriv ra0 get_site_survey
        
i> Get Statistics. 
    iwpriv ra0 stat                        ; read statistic counter
    iwpriv ra0 set ResetCounter=0        ; reset statistic counter

j> Link with any AP without security.        ; set ANY SSID
    iwpriv ra0 set SSID=""
    iwpriv ra0 set AuthMode=OPEN
    iwpriv ra0 set EncrypType=NONE

k> Get high-throughput information.
    iwpriv ra0 get_ht

l> Configure STA to new HT, which is Mixed Mode/20MHz/Long GI/no STBC/auto MCS.
    1. iwpriv ra0 set HtOpMode=0
    2. iwpriv ra0 set HtBw=0
    3. iwpriv ra0 set HtGi=0
    4. iwpriv ra0 set HtMcs=33
    5. iwpriv ra0 set WirelessMode=5
    6. iwpriv ra0 set SSID="AP's SSID"

Note.    Step 5 is check if STA is in the correct wireless mode. 
        All HT configuration are valid only in 802.11n wireless mode.
        Step 6 is the way to HT reconstruction and is necessary.
    
=======================================================================        
MORE INFORMATION
===================
If you want for rt2870sta driver to auto-load at boot time:
A) choose ra0 for first RT2870 WLAN card, rausb1 for second RT2870 WLAN card, etc.

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
=======================================================================[/FONT][/SIZE][/COLOR][/SIZE][/FONT]

---

### Post by gandaran on 2011-06-16
instead of trying to install those drivers you could just first find out what chipset the wireless adapter really has, if the adapter is usb type in terminal
```
lsusb
```
that should show which chip then enter the results in the Ubuntu forum search box, I'm sure there are many posts with the same problem as yours or if you don't find any to solve your problem post in the network and wireless section for help, you will get it working without installing those drivers, besides most ralink adapters work out of the box on Ubuntu or just need some configuration file tweaking, have you tried connecting with it?

---

### Post by Toz on 2011-06-16
[http://ubuntuforums.org/showthread.php?t=1509969]("http://ubuntuforums.org/showthread.php?t=1509969") - seems like all you have to do to get this card to work is blacklist rt2800usb and reboot.

---

### Post by manzdagratiano on 2011-06-16
EDIT: The thread Toz posted seems to have all the information necessary. You should follow that before you look at mine.

> **rluebke said:**
> [FONT=arial][SIZE=2][COLOR=black][SIZE=2][FONT=Arial, Helvetica, sans-serif]Sorry this is incredibly long but did not want to leave anything important off.

1> $tar -xvzf RT2870_Linux_STA_Drv_x.x.x.x.tar.gz
    go to "./RT2870_Linux_STA_Drv_x.x.x.x/" directory.

2> prepare the firmware (bin file) and the profile (dat file).
    $cp common/rt2870.bin /etc/Wireless/RT2870STA/
    $cp RT2870STA.dat  /etc/Wireless/RT2870STA/ 

3> compile the source code.
    $make all

4.> go to "os/linux/" directory.
    $load

    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
[/FONT][/SIZE][/COLOR][/SIZE][/FONT]

This is the relevant part. I will try to simplify it for you - all you basically need is to type these commands into a terminal, which I am writing below.
Assuming your driver is in downloads, open a terminal and:
```

$ cd Downloads
$ tar -xvzf <name of the file goes here>.tar.gz
$ cd <whatever the name of the directory is that got created after the previous step>
$ sudo mkdir /etc/Wireless/[FONT=arial][SIZE=2][COLOR=black][SIZE=2][FONT=Arial, Helvetica, sans-serif]RT2870STA[/FONT][/SIZE][/COLOR][/SIZE][/FONT]
$ [FONT=arial][SIZE=2][COLOR=black][SIZE=2][FONT=Arial, Helvetica, sans-serif]cp common/rt2870.bin /etc/Wireless/RT2870STA/[/FONT][/SIZE][/COLOR][/SIZE][/FONT]
$ [FONT=arial][SIZE=2][COLOR=black][SIZE=2][FONT=Arial, Helvetica, sans-serif]cp RT2870STA.dat  /etc/Wireless/RT2870STA/ 
$ make all
$ cd os/linux/
$ sudo [/FONT][/SIZE][/COLOR][/SIZE][/FONT][FONT=arial][SIZE=2][COLOR=black][SIZE=2][FONT=Arial, Helvetica, sans-serif]insmod rt2870sta.ko[/FONT][/SIZE][/COLOR][/SIZE][/FONT]
$ sudo cp [FONT=arial][SIZE=2][COLOR=black][SIZE=2][FONT=Arial, Helvetica, sans-serif]rt2870sta.ko /lib/modules/<kernel name goes here>/kernel/drivers/net/wireless/[/FONT][/SIZE][/COLOR][/SIZE][/FONT]
$ sudo depmod -a
$ sudo echo [FONT=arial][SIZE=2][COLOR=black][SIZE=2][FONT=Arial, Helvetica, sans-serif]rt2870sta.ko >> /etc/modules.conf[/FONT][/SIZE][/COLOR][/SIZE][/FONT]

```You can find your kernel name by doing:

```

$ uname -a

```or best, the name of the directory itself by checking:
```

$ ls /lib/modules/

```This ***should*** work - the last part which is not there in the README file comes from my own experiences with installing my Broadcom driver in Slackware.

---

