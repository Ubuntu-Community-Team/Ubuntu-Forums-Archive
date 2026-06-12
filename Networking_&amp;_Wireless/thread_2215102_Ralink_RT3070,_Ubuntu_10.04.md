---
title: "Ralink RT3070, Ubuntu 10.04"
date: 2014-04-04
forum: Networking &amp; Wireless
---

### Post by dave110 on 2014-04-04
Hi,
I'm a new user to Linux/Ubuntu and have no idea what I'm doing.  I installed 10.04 since it was small enough to fit onto a cd and plan on upgrading to the current LTS as soon as I can get a working internet connection.  I have a USB wireless receiver Ralink RT3070 I think, but when I look at the connections icon in desktop, my home wifi is not showing up.  The computer is in my basement and I have no way to get it online in a wired sense.  I do have a working computer upstairs that I can download drivers and such onto a usb drive and transfer to the basement.  The computer used to run windows xp and the wireless worked on that, and I do have the drivers that came with the receiver on a usb drive.  Where do I start?  Thanks for any input!

---

### Post by Ubi_one_2014 on 2014-04-04
[COLOR=#333333][FONT=UbuntuRegular][Tutorial] Howto install ralink RT5370 wifi adapter - aceofclubs - 04-18-2013 02:00 AM[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]This is how I got my RT5370 usb wifi adapter installed and working on CB2.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I eventually came across THIS thread which is where most of the correct information came from. All credits to thoses switched on people I just condensed things a little for CB2.[/FONT][/COLOR]

[LIST=1]
[*]download driver archive 2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2 .5.0.3_DPO.bz2 (RT8070/RT3070/RT3370/RT5370/RT5372 USB 03/28/2012 2.5.0.3 from THIS SITE.

[*]unpack the archive and navigate into the top level directory just extracted: Code:
tar jxvf  2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO.bz2
Code:
cd 2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO

[*]modify the following code in "os/linux/config.mk" as below: Code:
HAS_WPA_SUPPLICANT=y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
WFLAGS += -DCONFIG_STA_SUPPORT

[*]to quieten down the debugging modify "sta/sta-cfg.c": Code:
remove "#ifdef DBG" on line 4095
remove "endif /* DBG */" on line 4693

[*]to change the name from ra0 to wlan0 modify "include/rtmp_def.h" and change "ra" to "wlan" in the following lines: Code:
#define INF_MAIN_DEV_NAME        "ra"
#define INF_MBSSID_DEV_NAME        "ra"

[*]make and install the modified driver Code:
sudo make
sudo make install
modprobe rt5370sta

[*]reboot and check with lsusb lsmod and ifconfig to make sure all is working as required in the operating system.

[*]the CB2 setup program didnt work for me but the xbmc network manager addon worked perfectly so I downloaded and use that rather than doing it all via the operating system.
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]I hope this helps someone else trying to get an RT5370 wifi adapter up and running.[/FONT][/COLOR]

---

### Post by mörgæs on 2014-04-04
Hi, welcome to the fora.
First of all you should begin with a clean install of 13.10 using wired internet connection. If your computer is fairly new you can do it from USB.

---

### Post by dave110 on 2014-04-06
Thanks for input. What ended up working for me was performing option #2 in the following post 
([http://ubuntuforums.org/showthread.php?t=1826584](http://ubuntuforums.org/showthread.php?t=1826584)).

---

### Post by dave110 on 2014-04-06
Next task is to upgrade from 10.04 to 12.04. Don't know if that will screw up the drivers but if so I'll try the same process again

---

