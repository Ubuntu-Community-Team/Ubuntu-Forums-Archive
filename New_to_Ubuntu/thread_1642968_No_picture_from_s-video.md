---
title: "No picture from s-video"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by supererki on 2010-12-11
Im having some serious trouble trying to get my TV work with ubuntu 10.10. I connected the cables, and switched TV to s-video mode, but there is no picture. If i press something like "detect monitors" or when i log in the screen just blinks, but thats it. 

I have standard intel integrated 945GM graphics adapter.

erki@hacktrack:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

When i run lshw, it says *-display:1 UNCLAIMED, but i am not sure if the display:1 stands for s-video output or the VGA output (nothing connected there, but i have tested that VGA works). What does in mean - unclaimed? do i have to install some separate drivers to get it work ?

erki@hacktrack:~$ sudo lshw -C display
  *-display:0             
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:ee100000-ee17ffff ioport:1800(size=8) memory:d0000000-dfffffff memory:ee200000-ee23ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:ee180000-ee1fffff


erki@hacktrack:~$ uname -a
Linux hacktrack 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686 GNU/Linux

There is nothing interesting in dmesg output, i also didnt find anything about s-video in BIOS.

The computer itself is Lenova z61t

    description: Notebook
    product: 94482FG
    vendor: LENOVO
    version: ThinkPad Z61t
    serial: L3A0120
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=normal chassis=notebook cpus=2 frontpanel_password=unknown keyboard_password=disabled power-on_password=disabled uuid=6F9EBE81-4802-11CB-B7C0-FFBDC8E4EE77

Do you thing that it may be TVs issue ? It is a rather old Samsung CRT TV.

---

### Post by cariboo on 2010-12-11
Do you see anything on the TV screen when you restart you computer?

---

### Post by sandyd on 2010-12-11
> **supererki said:**
> Im having some serious trouble trying to get my TV work with ubuntu 10.10. I connected the cables, and switched TV to s-video mode, but there is no picture. If i press something like "detect monitors" or when i log in the screen just blinks, but thats it. 

I have standard intel integrated 945GM graphics adapter.

erki@hacktrack:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

When i run lshw, it says *-display:1 UNCLAIMED, but i am not sure if the display:1 stands for s-video output or the VGA output (nothing connected there, but i have tested that VGA works). What does in mean - unclaimed? do i have to install some separate drivers to get it work ?

erki@hacktrack:~$ sudo lshw -C display
  *-display:0             
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:ee100000-ee17ffff ioport:1800(size=8) memory:d0000000-dfffffff memory:ee200000-ee23ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:ee180000-ee1fffff


erki@hacktrack:~$ uname -a
Linux hacktrack 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686 GNU/Linux

There is nothing interesting in dmesg output, i also didnt find anything about s-video in BIOS.

The computer itself is Lenova z61t

    description: Notebook
    product: 94482FG
    vendor: LENOVO
    version: ThinkPad Z61t
    serial: L3A0120
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=normal chassis=notebook cpus=2 frontpanel_password=unknown keyboard_password=disabled power-on_password=disabled uuid=6F9EBE81-4802-11CB-B7C0-FFBDC8E4EE77

Do you thing that it may be TVs issue ? It is a rather old Samsung CRT TV.
post output of
```

xrandr
```
while tv is connected.

---

### Post by supererki on 2010-12-11
erki@hacktrack:~$ xrandr 
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
   1440x900       60.0*+   59.9  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
TV1 disconnected (normal left inverted right x axis y axis)

---

### Post by supererki on 2010-12-11
erki@hacktrack:~$ xrandr --verbose
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x41
	Timestamp:  53773236
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
LVDS1 connected 1440x900+0+0 (0x44) normal (normal left inverted right x axis y axis) 303mm x 190mm
	Identifier: 0x42
	Timestamp:  53773236
	Subpixel:   horizontal rgb
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       1
	CRTCs:      1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	EDID:
		00ffffffffffff0030ae334000000000
		000f0103801e1378eaae109658538c28
		24505421080001010101010101010101
		0101010101013226a04051841a303020
		36002fbe10000019d51fa04051841a30
		302036002fbe100000190000000f0090
		0a32900a28140100320c4811000000fe
		004c503134315750312d544c423200c7
	BACKLIGHT: 7 (0x00000007)	range:  (0,7)
	Backlight: 7 (0x00000007)	range:  (0,7)
	scaling mode:	Full aspect
		supported: None         Full         Center       Full aspect 
  1440x900 (0x44)   97.8MHz -HSync -VSync *current +preferred
        h: width  1440 start 1488 end 1520 total 1760 skew    0 clock   55.6KHz
        v: height  900 start  903 end  909 total  926           clock   60.0Hz
  1440x900 (0x45)  106.5MHz -HSync +VSync
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock   55.9KHz
        v: height  900 start  903 end  909 total  934           clock   59.9Hz
  1360x768 (0x46)   84.8MHz -HSync +VSync
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz
  1360x768 (0x47)   72.0MHz +HSync -VSync
        h: width  1360 start 1408 end 1440 total 1520 skew    0 clock   47.4KHz
        v: height  768 start  771 end  781 total  790           clock   60.0Hz
  1152x864 (0x48)   81.6MHz -HSync +VSync
        h: width  1152 start 1216 end 1336 total 1520 skew    0 clock   53.7KHz
        v: height  864 start  865 end  868 total  895           clock   60.0Hz
  1024x768 (0x49)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x4a)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x4b)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x4c)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
TV1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x43
	Timestamp:  53773236
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	bottom margin: 37 (0x00000025)	range:  (0,100)
	right margin: 46 (0x0000002e)	range:  (0,100)
	top margin: 36 (0x00000024)	range:  (0,100)
	left margin: 54 (0x00000036)	range:  (0,100)
	mode:	NTSC-M
		supported: NTSC-M       NTSC-443     NTSC-J       PAL-M       
		           PAL-N        PAL          480p@59.94Hz 480p@60Hz   
		           576p         720p@60Hz    720p@59.94Hz 720p@50Hz   
		           1080i@50Hz   1080i@60Hz   1080i@59.94H

---

### Post by supererki on 2010-12-11
cariboo907 - the screen just blinks. By default it is all black, but when i restart it blinks few times.

---

### Post by supererki on 2010-12-11
xrandr says : TV1 disconnected, but the cable is definetely connected.

---

### Post by sandyd on 2010-12-12
> **supererki said:**
> xrandr says : TV1 disconnected, but the cable is definetely connected.
bad cable?

---

