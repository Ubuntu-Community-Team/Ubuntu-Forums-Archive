---
title: "azio AWD102N Wireless pci adapter and detecting wireless signals not happening"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by thesnappysneezer on 2011-01-06
So the d-link thing I had would not work and I called up local computer stores and the guy said though it did not say so on thebox, this should work with what I've got but I'm still not online. green light is blinking it does not seem to detect any wireless signals. Is it not like Windows in that it can not detect everything? I tried entering the info but still nothing but I am uncertain as to what is the right info and where to find it. and where to put it. Also I am uncertain if the drivers are actualy in there. The disk did not work like the guy said, I saw a linux driver for it online but I do not really see how to install it anywhere though there seems to be some notion in the booklet about some drivers being built in though for 7. I'm so confused. can anyone walk me through on how to do this, how to setup a connection to te wireless internet available to me and how to install the driver?

PS thank you all who helped me before.


currently I am in 32, I put it in since 64 was nto working with dlink, I am also weighing the options of which is better 32 or 64, I read that 32 is more compatible though 64 is cooler.

---

### Post by wep940 on 2011-01-06
We need more information:
 
- open a terminal window
 
- type: (note no spaces between the 2 ">>")
 
lspci > mytest.txt <press enter>
 
lsusb >> mytest.txt <press enter>
 
lshw -C network >> mytest.txt <press enter>
 
ifconfig >> mytest.txt <press enter>
 
iwconfig >> mytest.txt <press enter>
 
Post the mytest.txt file content back here in a reply, surrounded by ```
 and 
```.

---

### Post by thesnappysneezer on 2011-01-06
when I did the -C line it told me I .should be a super user and stopped doing anything and my commands were not responded to

---

### Post by thesnappysneezer on 2011-01-07
logged in as and again at the one that has the -C, a hangup, it loaded right under my name started saying pci then changed to Network interfaces like it is searchin or scanning, it is not in a field that I think typing will allow for a new command, that is the command or somesuch is not finished yet, what to do? Thanks by the way.

---

### Post by wep940 on 2011-01-07
The lshw -C network is not an "instant" response - it scans all the hardware on your PC. So it will show things like PCI, USB, NETWORK, etc., before it dumps the output. However, given that I asked for the redirect of the output to a file (via the ">>"), I'm not sure at this moment what is going on. When I do this on my PC, the "PCI" line shows on the screen, then there is a delay, then my prompt returns. The actual output is in the text file.
 
BTW - I forgot the software would interpret my code /code block in my original post, so I'll try again:
 
post the output file contents back here, prefixed by a [ then the word code then a ], and add a [ then the phrase /code then a ] at the end.

---

### Post by thesnappysneezer on 2011-01-07
hey, I went to bed before your last post. Thank you. I redid it this morning and the -C one went through fast, I did disconnect an external harddrive full of data, I do not know if thathad any effect. when I did the 1wconfig I got this back on  screen

```


lo          no wireless extensions

eth0      no wireless extensions

eth1      no wireless extensions


```

now I would ask where is the my test.txt but I searhed for it and can not find it.

When I try to close the terminal it says a process is running and closign will kill it, is it still compiling something? My name with - # is appearing for a new commmand. Is there something I am suppose to do to here to see or create the txtfile? where is it?

Thank you for your help.

---

### Post by thesnappysneezer on 2011-01-07
I put the 64 bit in again, did this and I got a mytest in my home. So here goes 
```

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:08.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:09.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:09.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:09.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0a.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0c.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0d.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0e.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:10.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GTS] (rev a1)
02:08.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
02:09.0 Network controller: RaLink Device 3062

```

---

### Post by Kenjitamura on 2011-01-07
Your wireless card appears to be detected as > 02:09.0 Network controller: RaLink Device 3062
You'll probably need to go to [http://www.ralinktech.com/support.php?s=2]("http://www.ralinktech.com/support.php?s=2") and download the 3062 driver (6th entry down ver. 2.4.1.1).  From there follow it's read me to install the driver.  Although that sounds simple I remember when I used a wireless card installing drivers was a nightmare that took hours to get working.

Edit: I downloaded the drivers read through the read me and looked at the makefile, looks like its already preconfigured properly so it should be an easy install.  However, there are a lot of documented problems with this driver I've noticed after searching through the forums so if it's not working after you've setup the drivers you might find some insight in [This Thread]("http://www.uluga.ubuntuforums.org/showthread.php?t=1612271") (Warning they went through a lot of trial and error, read through it entirely and don't make the same mistakes as the poster)

---

### Post by thesnappysneezer on 2011-01-07
that read me file to install is not understandable by any means to me, I am a newbie and I do not comprehend it. Yeah, it sounds simple but what I see from linux is one mans simple is another man's heart attack.

---

### Post by thesnappysneezer on 2011-01-08
Please walk me through this somebody?

I dropped it in my home folder, double clicked it. Is that ok? I tried tar on what it said but terminal just said 

```
-xvzf: command not found. 
```I just went ahead and did the next step. I found the makefile in the folder I unziped, the one in the first folder, there is another in a subfolder tools. 


mode already = STA, Target = Linux

I went into os/linux/config.mk

I located my gccgcc with gcc- v and got 
```
 Using built-in specs.
Target: x86_64-linux-gnu
Configured with: .../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.4.4-14ubuntu5' --with-bugurl=[file://usr/share/doc/gcc-4.4/README.Bugs](file://usr/share/doc/gcc-4.4/README.Bugs) --enable-languages=c,c++,fortan,obj-c++ --prefix=/usr --program-suffix=-4.4 --enable-shared --enable-multiarch --enable linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=X86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu 5)

```So I put 4.4.5 in config.mk where the line reads ```
CC:=$(4.4.5)gcc
```this is to say, I put it between the () that had I think the word cross files, but not certain. LD was similar, I did ld -v and got

```
GNU ld (GNU Binutils for Ubuntu) 2.20.51-system.20100908
```to where it says ```
LD:= $(2.20.51-system.20100908)ld
```Next it tells me to define CFLAGS which I do not know how to do. Please tell me. 


Next it tells me this:

 ```


3> In os/linux/config.mk 
    define the GCC and LD of the target machine
    define the compiler flags CFLAGS
    modify to meet your need.
    ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
       => #>cd wpa_supplicant-x.x
       => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
    ** Build for being controlled by WpaSupplicant with Ralink Driver
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
       => #>cd wpa_supplicant-0.5.7
       => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d
```I did not wuite understand, I went with the 2nd option of y and n and I pasted thr => lines right So far have I done right? I hope so because I exited and saved. I do not undersatnd from here if I did understand correctly in the first place. What and where is $make, how do I compile driver source code, what is this too fix error bit about, what is that thing with the yen symbol and how do I type that or do I need to, where do I put that patch? those things with the =>do I just add them at the end, do I hit ent4er and tab tomake them line up as indented as they look in these instructions? what and where is that .dat at?how do I load driver?Wny must I unload it after? Then there is all of this stuff about configuration. Please explain. Here is the readme file. Gonna nap now, so I f I do not respond to quickly that is why. Thank you all for your help and again, here is the readme instructions.
```
* README
*
* Ralink Tech Inc.
* 
* [http://www.ralinktech.com](http://www.ralinktech.com)
*

=======================================================================
ModelName:
===========
RT2860 Wireless Lan Linux Driver


=======================================================================
Driver lName:
=============
rt2860.o/rt2860.ko


=======================================================================
Supporting Kernel:
===================
linux kernel 2.4 and 2.6 series. 
Tested in Redhat 7.3 or later.


=======================================================================
Description:
=============
This is a linux device driver for Ralink RT2860 ABGN WLAN Card.


=======================================================================
Contents:
=============
Makefile            : Makefile
*.c                    : c files
*.h                    : header files


=======================================================================
Features:
==========
   This driver implements basic IEEE802.11. Infrastructure and adhoc mode with 
   open or shared or WPA-PSK or WPA2-PSK authentication method. 
   NONE, WEP, TKIP and AES encryption. 


=======================================================================
Build Instructions:  
====================

1> $tar -xvzf DPB_RT2860_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2860_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
     define the linux kernel source include file path LINUX_SRC
     modify to meet your need.

3> In os/linux/config.mk 
    define the GCC and LD of the target machine
    define the compiler flags CFLAGS
    modify to meet your need.
    ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
       => #>cd wpa_supplicant-x.x
       => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
    ** Build for being controlled by WpaSupplicant with Ralink Driver
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
       => #>cd wpa_supplicant-0.5.7
       => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make            
    # compile driver source code
    # To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
      => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

5> $cp RT2860STA.dat  /etc/Wireless/RT2860STA/RT2860STA.dat       
    
6> load driver
    #[kernel 2.4]
    #    $/sbin/insmod rt2860sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2860sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
    $/sbin/rmmod rt2860sta
    
=======================================================================
CONFIGURATION:  
====================
RT2860 driver can be configured via following interfaces, 
i.e. (i)"iwconfig" command, (ii)"iwpriv" command, (iii) configuration file

i)  iwconfig comes with kernel.  
ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for details.
iii)modify configuration file "RT2860STA.dat" in /etc/Wireless/RT2860STA/RT2860STA.dat.
           
Configuration File : RT2860STA.dat
---------------------------------------
# Copy this file to /etc/Wireless/RT2860STA/RT2860STA.dat
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
EthConvertMode=
EthCloneMac=
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
MeshId=MESH
MeshAutoLink=1
MeshAuthMode=OPEN
MeshEncrypType=NONE
MeshWPAKEY=
MeshDefaultkey=1
MeshWEPKEY=
CarrierDetect=0

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
       31: use 1 ~ 14 Channel (ch1-11:active scan, ch12-14 passive scan)
                                                  
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
        OPEN         For open system    
        SHARED          For shared key system    
        WEPAUTO     Auto switch between OPEN and SHARED
        WPAPSK      For WPA pre-shared key  (Infra)
        WPA2PSK     For WPA2 pre-shared key (Infra)
        WPANONE        For WPA pre-shared key  (Adhoc)
        WPA         Use WPA-Supplicant
        WPA2        Use WPA-Supplicant

@> EncrypType=value
    value
        NONE        For AuthMode=OPEN                    
        WEP            For AuthMode=OPEN or AuthMode=SHARED 
        TKIP        For AuthMode=WPAPSK or WPA2PSK                    
        AES            For AuthMode=WPAPSK or WPA2PSK                     
        
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
        8~63 ASCII          or 
        64 HEX characters
                                                                                                                                                            
@> WmmCapable=value
    value
        0: Disable WMM
        1: Enable WMM
        
@> PSMode=value
    value
        CAM                Constantly Awake Mode
        Max_PSP            Max Power Savings
        Fast_PSP        Power Save Mode

@> FastRoaming=value
    value
        0                Disabled
        1                Enabled

@> RoamThreshold=value
    value
        Positive Interger(dBm)

@> HT_RDG=value
    value
        0                Disabled
        1                Enabled

@> HT_EXTCHA=value (Extended Channel Switch Announcement)
    value
        0                Below
        1                 Above

@> HT_OpMode=value
    value
        0                HT mixed format
        1                HT greenfield format

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
        0                20MHz
        1                40MHz

@> HT_AutoBA=value
    value
        0                Disabled
        1                Enabled

@> HT_BADecline
    value
        0                Disabled
        1                Enabled <Reject BA request from AP>

@> HT_AMSDU=value
    value
        0                Disabled
        1                Enabled

@> HT_BAWinSize=value
    value
        1 ~ 64

@> HT_GI=value
    value
        0                long GI
        1                short GI

@> HT_MCS=value
    value
        0 ~ 15
        33: auto

@> HT_MIMOPSMode=value
    value (based on 802.11n D2.0)
        0                Static SM Power Save Mode
        1                Dynamic SM Power Save Mode
        2                Reserved
        3                SM enabled
    (not fully support yet)

@> EthConvertMode=value
    value
        dongle
        clone
        hybrid

@> EthCloneMac=value
    value
        xx:xx:xx:xx:xx:xx
        
@> IEEE80211H=value
    value
        0                Disabled
        1                Enabled

@> TGnWifiTest=value
    value
        0                Disabled
        1                Enabled

@> WirelessEvent=value
    value
        0                Disabled
        1                Enabled <send custom wireless event>
        
@> MeshId=value
    value
        Length 1~32 ascii characters

@> MeshAutoLink=value
    value
        0                Disabled
        1                Enabled

@> MeshAuthMode=value
    value
        OPEN         For open system    
        WPANONE        For WPA pre-shared key  (Adhoc)

@> MeshEncrypType=value
    value
        NONE        For MeshAuthMode=OPEN                    
        WEP            For MeshAuthMode=OPEN
        TKIP        For MeshAuthMode=WPANONE
        AES            For MeshAuthMode=WPANONE

@> MeshWPAKEY=value
    value
        8~63 ASCII          or 
        64 HEX characters

@> MeshDefaultkey=value
    value
        1~4

@> MeshWEPKEY=value
    value
        10 or 26 characters
        5 or 13 characters

@> CarrierDetect=value
    value
        0                Disabled
        1                Enabled

MORE INFORMATION
=================================================================================
If you want for rt2860 driver to auto-load at boot time:
A) choose ra0 for first RT2860 WLAN card, ra1 for second RT2860 WLAN card, etc.
   
B) create(edit) 'ifcfg-ra0' file in /etc/sysconfig/network-scripts/,      
   edit( or add the line) in /etc/modules.conf:
       alias ra0 rt2860sta
   
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
Dongle/Clone Features:
======================
A) Dongle mode: 
       Provides a 1-to-N MAC address mapping mechanism such that more than one PC behind the STA 
       can transparently connect to the AP.

B) Clone mode:
    Provides a 1-to-1 MAC address mapping mechanism. 
    STA can use own MAC as SA MAC or 
            use user desired MAC as SA MAC or
            use source MAC of first packet coming from wired device as SA MAC.
    NOTE: In this mode, only the PC who own the specified MAC can connect to the AP.

 
C) Hybrid mode(Dongle+Clone):
    Provides a 1-to-N MAC address mapping mechanism such that more than one PC behind the STA 
       can transparently connect to the AP.
    STA can use own MAC as SA MAC or 
            use user desired MAC as SA MAC or
            use source MAC of first packet coming from wired device as SA MAC.

D) Please refer to "Config STA to link as dongle mode..." in iwpriv_usage.txt for releated commands.


```

---

### Post by thesnappysneezer on 2011-01-09
Still can't configure cflags as I do not know what they are.

Also, I noticed I was to save it to a folder in wireless under etc well, there is no wireless folder there and I cannot create one or put anything in the etc folder, it says I do not have permission. I still so not know what $make is either or what I am to do next. Please help

---

### Post by thesnappysneezer on 2011-01-10
Rising Tackle

That might have made more sense in a snk forum

---

### Post by thesnappysneezer on 2011-04-06
please help, I am still not online

---

### Post by wipmonkey on 2011-04-09
I got the same card
Part 1:
I got from here [http://ubuntuforums.org/showthread.php?t=1609086](http://ubuntuforums.org/showthread.php?t=1609086)

```
gksu gedit /etc/modprobe.d/blacklist-rt2860sta.conf
```

Put this in that file:
```
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2800lib
```

```
gksu gedit /etc/modules
```

Add to the end of that file
```
rt3562sta.ko
```

Part 2:
I think this will make it recompile on new kernels(someone correct me if I'm wrong)

Install DKMS if is not already there. 
```
sudo apt-get install dkms
```

copy to /usr/src
```
sudo mv DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217 /usr/src/rt2860sta-2.4.1.1/
```

```
cd /usr/src/rt2860sta-2.4.1.1/
```

```
gksu gedit dkms.conf
```

make it look like:

```
MAKE="make"
CLEAN="make clean"
BUILT_MODULE_NAME=rt3562sta
BUILT_MODULE_LOCATION=os/linux
PACKAGE_NAME=rt3562sta
PACKAGE_VERSION=2.4.1.1
REMAKE_INITRD=yes
DEST_MODULE_LOCATION=/kernel/drivers/staging/rt2860/
```

add it to dkms
```
sudo dkms add -m rt2860sta -v 2.4.1.1
```

build it:
```
sudo dkms build  -m rt2860sta -v 2.4.1.1
```

install it:
```
sudo dkms install -m rt2860sta -v 2.4.1.1
```

Then reboot and should work

if its not magically working when a new kernel is installed just do: 

build it:
```
sudo dkms build  -m rt2860sta -v 2.4.1.1
```

install it:
```
sudo dkms install -m rt2860sta -v 2.4.1.1
```

Then reboot

---

