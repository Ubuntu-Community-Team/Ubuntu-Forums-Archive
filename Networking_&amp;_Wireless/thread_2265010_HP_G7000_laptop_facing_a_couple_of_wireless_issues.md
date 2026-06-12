---
title: "HP G7000 laptop facing a couple of wireless issues"
date: 2015-02-11
forum: Networking &amp; Wireless
---

### Post by desesperado on 2015-02-11
Good evening wireless gurus.

Let me start saying that **_I'm using the "Try Xubuntu" option of today's image on a HP G7000 laptop. This is not a installed system._**

My first issue related to the fact that everytime I boot the laptop the  wireless button is orange, meaning that my wireless is hard-blocked, and  no matter pressing the button will turn it on. The only way I have to  turn it on is by rebooting into windows, and once at the windows login,  I'm then able to press the button and it will turn on.
I've google this to exhaustion to no avail.

The other issue I'm facing relates to the fact that I'm not getting any  wireless networks signals. In fact the network indicator/applet only  shows the wired one (and yes the led on the wireless button is blue,  meaning it is turned on)/

Here's what I have done so far```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get update
sudo apt-get install firmware-b43-installer
sudo modprobe -r b43
sudo modprobe b43
```But still nothing.


Here's some output I think you might need```
xubuntu@xubuntu:~$ grep 'blacklist b43' /etc/modprobe.d/*
xubuntu@xubuntu:~$

xubuntu@xubuntu:~$ lsmod | grep -e b43 -e wl
b43                   398950  0 
bcma                   46583  1 b43
mac80211              580709  1 b43
wl                   6148792  0 
cfg80211              433826  3 wl,b43,mac80211
ssb                    55983  2 b43,ssb_hcd

xubuntu@xubuntu:~$ dmesg | grep b43
[   29.376722] b43-phy0: Broadcom 4311 WLAN found (core revision 13)
[   29.447340] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 9
[   29.447358] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 2, Version 0
[   29.466652] b43 ssb0:0: Direct firmware load for b43/ucode13.fw failed with error -2
[   29.466691] b43 ssb0:0: Direct firmware load for b43/ucode13.fw failed with error -2
[   29.466742] b43 ssb0:0: Direct firmware load for b43-open/ucode13.fw failed with error -2
[   29.466761] b43 ssb0:0: Direct firmware load for b43-open/ucode13.fw failed with error -2
[   29.466766] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found
[   29.466771] b43-phy0 ERROR: Firmware file "b43-open/ucode13.fw" not found
[    29.466775] b43-phy0 ERROR: You must go to   http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and   download the correct firmware for this driver version. Please carefully   read all instructions on this website.
[  813.962368] b43-wlan ERROR: Dual-core devices are not supported
[  813.962382] b43: probe of ssb0:0 failed with error -524
[ 1242.900505] b43-wlan ERROR: Dual-core devices are not supported
[ 1242.900521] b43: probe of ssb0:0 failed with error -524
[ 1498.989014] b43-wlan ERROR: Dual-core devices are not supported
[ 1498.989028] b43: probe of ssb0:0 failed with error -524

xubuntu@xubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

Thanks in advance for all the help.

**_EDIT:_** Here's the output obtained by the wireless script -> [http://paste.ubuntu.com/10179683/](http://paste.ubuntu.com/10179683/)

---

### Post by Hadaka on 2015-02-11
Hi, from a working wired connection please do 
it's close....try this

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo modprobe -rf wl
sudo modprobe -r b43
sudo apt-get update
sudo apt-get ubgrade
sudo modprobe b43
```
got wireless now??

---

### Post by desesperado on 2015-02-11
Thanks for answering Hadaka. Here you go:```
xubuntu@xubuntu:~$ sudo apt-get remove --purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

xubuntu@xubuntu:~$ sudo apt-get update 
Ign cdrom://Xubuntu 15.04 _Vivid Vervet_ - Alpha i386 (20150211) vivid InRelease
Ign cdrom://Xubuntu 15.04 _Vivid Vervet_ - Alpha i386 (20150211) vivid/main Translation-en_US                                    
Ign cdrom://Xubuntu 15.04 _Vivid Vervet_ - Alpha i386 (20150211) vivid/main Translation-en                
Ign cdrom://Xubuntu 15.04 _Vivid Vervet_ - Alpha i386 (20150211) vivid/multiverse Translation-en_US       
Ign cdrom://Xubuntu 15.04 _Vivid Vervet_ - Alpha i386 (20150211) vivid/multiverse Translation-en          
Ign cdrom://Xubuntu 15.04 _Vivid Vervet_ - Alpha i386 (20150211) vivid/restricted Translation-en_US       
Ign cdrom://Xubuntu 15.04 _Vivid Vervet_ - Alpha i386 (20150211) vivid/restricted Translation-en          
Ign cdrom://Xubuntu 15.04 _Vivid Vervet_ - Alpha i386 (20150211) vivid/universe Translation-en_US         
Ign cdrom://Xubuntu 15.04 _Vivid Vervet_ - Alpha i386 (20150211) vivid/universe Translation-en            
Ign http://archive.ubuntu.com vivid InRelease                                                             
Ign http://security.ubuntu.com vivid-security InRelease                                                   
Ign http://archive.ubuntu.com vivid-updates InRelease
Get:1 http://security.ubuntu.com vivid-security Release.gpg [933 B]
Get:2 http://archive.ubuntu.com vivid Release.gpg [933 B]
Get:3 http://security.ubuntu.com vivid-security Release [59.7 kB]
Get:4 http://archive.ubuntu.com vivid-updates Release.gpg [933 B]
Get:5 http://archive.ubuntu.com vivid Release [215 kB]
Get:6 http://security.ubuntu.com vivid-security/main i386 Packages [14 B]
Get:7 http://security.ubuntu.com vivid-security/restricted i386 Packages [14 B]
Get:8 http://security.ubuntu.com vivid-security/universe i386 Packages [14 B]  
Get:9 http://security.ubuntu.com vivid-security/multiverse i386 Packages [14 B]
Get:10 http://security.ubuntu.com vivid-security/main Translation-en [14 B]   
Get:11 http://archive.ubuntu.com vivid-updates Release [59.7 kB]
Get:12 http://security.ubuntu.com vivid-security/multiverse Translation-en [14 B]
Get:13 http://security.ubuntu.com vivid-security/restricted Translation-en [14 B]       
Get:14 http://security.ubuntu.com vivid-security/universe Translation-en [14 B]         
Get:15 http://archive.ubuntu.com vivid/main i386 Packages [1,349 kB]   
Get:16 http://archive.ubuntu.com vivid/restricted i386 Packages [13.2 kB]
Get:17 http://archive.ubuntu.com vivid/universe i386 Packages [6,480 kB]
Get:18 http://archive.ubuntu.com vivid/multiverse i386 Packages [135 kB]                                                                                                           
Get:19 http://archive.ubuntu.com vivid/main Translation-en [779 kB]                                                                                                                
Hit http://archive.ubuntu.com vivid/multiverse Translation-en                                                                                                                      
Hit http://archive.ubuntu.com vivid/restricted Translation-en                                                                                                                      
Get:20 http://archive.ubuntu.com vivid/universe Translation-en [4,457 kB]                                                                                                          
Get:21 http://archive.ubuntu.com vivid-updates/main i386 Packages [14 B]                                                                                                           
Get:22 http://archive.ubuntu.com vivid-updates/restricted i386 Packages [14 B]                                                                                                     
Get:23 http://archive.ubuntu.com vivid-updates/universe i386 Packages [14 B]                                                                                                       
Get:24 http://archive.ubuntu.com vivid-updates/multiverse i386 Packages [14 B]                                                                                                     
Get:25 http://archive.ubuntu.com vivid-updates/main Translation-en [14 B]                                                                                                          
Get:26 http://archive.ubuntu.com vivid-updates/multiverse Translation-en [14 B]                                                                                                    
Get:27 http://archive.ubuntu.com vivid-updates/restricted Translation-en [14 B]                                                                                                    
Get:28 http://archive.ubuntu.com vivid-updates/universe Translation-en [14 B]                                                                                                      
Fetched 13.6 MB in 19s (693 kB/s)                                                                                                                                                  
Reading package lists... Done

xubuntu@xubuntu:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

xubuntu@xubuntu:~$ sudo modprobe -r b43
xubuntu@xubuntu:~$ 
xubuntu@xubuntu:~$ sudo modprobe b43
xubuntu@xubuntu:~$ 

```

Still without wireless.

---

### Post by Hadaka on 2015-02-11
lets see if we got rid of that wl
please post the output of..
```
lsmod |egrep 'wl|b43|ssb'
sudo modprobe -rf b43
sudo modprobe -v b43
dmesg | grep b43
```

---

### Post by desesperado on 2015-02-11
Here it is:```
xubuntu@xubuntu:~$ lsmod | egrep 'wl|b43|ssb'
b43                   398950  0 
bcma                   46583  1 b43
mac80211              580709  1 b43
wl                   6148792  0 
ssb_hcd                12757  0 
cfg80211              433826  3 wl,b43,mac80211
ssb                    55983  2 b43,ssb_hcd

xubuntu@xubuntu:~$ sudo modprobe -rf b43
xubuntu@xubuntu:~$ 

xubuntu@xubuntu:~$ sudo modprobe -v b43
insmod /lib/modules/3.18.0-13-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.18.0-13-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.18.0-13-generic/kernel/drivers/net/wireless/b43/b43.ko 

xubuntu@xubuntu:~$ dmesg | grep b43
[   29.376722] b43-phy0: Broadcom 4311 WLAN found (core revision 13)
[   29.447340] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 9
[   29.447358] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 2, Version 0
[   29.466652] b43 ssb0:0: Direct firmware load for b43/ucode13.fw failed with error -2
[   29.466691] b43 ssb0:0: Direct firmware load for b43/ucode13.fw failed with error -2
[   29.466742] b43 ssb0:0: Direct firmware load for b43-open/ucode13.fw failed with error -2
[   29.466761] b43 ssb0:0: Direct firmware load for b43-open/ucode13.fw failed with error -2
[   29.466766] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found
[   29.466771] b43-phy0 ERROR: Firmware file "b43-open/ucode13.fw" not found
[   29.466775] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  813.962368] b43-wlan ERROR: Dual-core devices are not supported
[  813.962382] b43: probe of ssb0:0 failed with error -524
[ 1242.900505] b43-wlan ERROR: Dual-core devices are not supported
[ 1242.900521] b43: probe of ssb0:0 failed with error -524
[ 1498.989014] b43-wlan ERROR: Dual-core devices are not supported
[ 1498.989028] b43: probe of ssb0:0 failed with error -524
[ 5860.076497] b43-wlan ERROR: Dual-core devices are not supported
[ 5860.076515] b43: probe of ssb0:0 failed with error -524
[ 7128.765295] b43-wlan ERROR: Dual-core devices are not supported
[ 7128.765312] b43: probe of ssb0:0 failed with error -524


```

---

### Post by Hadaka on 2015-02-11
wl is still jammed in there,,,try this.
```
sudo apt-get remove --purge firmware-b43-installer
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -rf wl
sudo modprpbe -rf b43
sudo apt-get install  firmware-b43-installer
sudo modprobe -v b43
dmesg | grep b43
```
if it says it has proprietary drivers ignore

---

### Post by chili555 on 2015-02-12
And, as a precaution, I suggest you reboot.

---

### Post by desesperado on 2015-02-12
> **Hadaka said:**
> wl is still jammed in there,,,try this. ```
sudo apt-get remove --purge firmware-b43-installer sudo apt-get remove --purge bcmwl-kernel-source sudo modprobe -rf wl sudo modprpbe -rf b43 sudo apt-get install  firmware-b43-installer sudo modprobe -v b43 dmesg | grep b43
``` if it says it has proprietary drivers ignore  ```
~$ sudo apt-get remove --purge firmware-b43-installer Reading package lists... Done Building dependency tree        Reading state information... Done The following package was automatically installed and is no longer required:   b43-fwcutter Use 'apt-get autoremove' to remove it. The following packages will be REMOVED:   firmware-b43-installer* 0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded. After this operation, 57.3 kB disk space will be freed. Do you want to continue? [Y/n]  (Reading database ... 160408 files and directories currently installed.) Removing firmware-b43-installer (1:019-1) ... Deleting old extracted firmware... Purging configuration files for firmware-b43-installer (1:019-1) ... Deleting old extracted firmware...
``` ```
~$ sudo apt-get remove --purge bcmwl-kernel-source Reading package lists... Done Building dependency tree        Reading state information... Done Package 'bcmwl-kernel-source' is not installed, so not removed The following package was automatically installed and is no longer required:   b43-fwcutter Use 'apt-get autoremove' to remove it. 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
``` ```
~$ sudo modprobe -rf wl modprobe: FATAL: Module wl not found.
``` ```
~$ sudo modprobe -rf b43 $
``` ```
~$ sudo apt-get install firmware-b43-installer Reading package lists... Done Building dependency tree        Reading state information... Done The following NEW packages will be installed:   firmware-b43-installer 0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded. Need to get 0 B/4,126 B of archives. After this operation, 57.3 kB of additional disk space will be used. Selecting previously unselected package firmware-b43-installer. (Reading database ... 160403 files and directories currently installed.) Preparing to unpack .../firmware-b43-installer_1%3a019-1_all.deb ... Unpacking firmware-b43-installer (1:019-1) ... Setting up firmware-b43-installer (1:019-1) ... No chroot environment found. Starting normal installation --2015-02-12 11:07:25--  http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2 Resolving www.lwfinger.com (www.lwfinger.com)... 173.254.28.119 Connecting to www.lwfinger.com (www.lwfinger.com)|173.254.28.119|:80... connected. HTTP request sent, awaiting response... 200 OK Length: 13514651 (13M) [application/x-bzip2] Saving to: ‘broadcom-wl-5.100.138.tar.bz2’  broadcom-wl-5.100.138.tar.bz2                100%[================================================================================================>]  12.89M   460KB/s   in 5m 44s s  2015-02-12 11:13:11 (38.4 KB/s) - ‘broadcom-wl-5.100.138.tar.bz2’ saved [13514651/13514651]  Deleting old extracted firmware... broadcom-wl-5.100.138/ broadcom-wl-5.100.138/linux/ broadcom-wl-5.100.138/linux/wl_apsta.o broadcom-wl-5.100.138/linux/wl_ap.o broadcom-wl-5.100.138/linux/wl_sta.o broadcom-wl-5.100.138/README broadcom-wl-5.100.138/config/ broadcom-wl-5.100.138/config/wlconfig_lx_shared broadcom-wl-5.100.138/config/wl.mk broadcom-wl-5.100.138/config/wl_default broadcom-wl-5.100.138/config/wl_hnd broadcom-wl-5.100.138/config/wlconfig_nomimo This file is recognised as:   filename   :  wl_apsta.o   version    :  666.2   MD5        :  e1b05e268bcdbfef3560c28fc161f30e Extracting b43/lp0initvals14.fw Extracting b43/lcn0bsinitvals25.fw Extracting b43/n0bsinitvals25.fw Extracting b43/n0bsinitvals17.fw Extracting b43/ucode17_mimo.fw Extracting b43/ucode16_lp.fw Extracting b43/sslpn1initvals27.fw Extracting b43/lp2bsinitvals19.fw Extracting b43/sslpn3bsinitvals21.fw Extracting b43/ucode16_sslpn.fw   ucode time:     01:15:07 Extracting b43/ucode25_lcn.fw Extracting b43/ucode21_sslpn.fw Extracting b43/lp0bsinitvals14.fw Extracting b43/b0g0initvals9.fw Extracting b43/ucode20_sslpn.fw Extracting b43/a0g1bsinitvals9.fw Extracting b43/lp1initvals20.fw Extracting b43/b0g0bsinitvals13.fw Extracting b43/lp2initvals19.fw Extracting b43/n2bsinitvals19.fw Extracting b43/sslpn4bsinitvals22.fw Extracting b43/ucode16_sslpn_nobt.fw   ucode date:     2011-02-23 Extracting b43/n1bsinitvals20.fw Extracting b43/n1initvals20.fw Extracting b43/b0g0bsinitvals5.fw Extracting b43/ucode22_sslpn.fw Extracting b43/b0g0initvals13.fw Extracting b43/ht0initvals26.fw Extracting b43/ucode33_lcn40.fw Extracting b43/sslpn1bsinitvals20.fw Extracting b43/lcn400bsinitvals33.fw Extracting b43/ucode14.fw Extracting b43/a0g0initvals5.fw Extracting b43/lp1bsinitvals22.fw Extracting b43/n16initvals30.fw Extracting b43/lp0bsinitvals16.fw Extracting b43/lcn1bsinitvals25.fw Extracting b43/lcn400initvals33.fw Extracting b43/n0bsinitvals24.fw Extracting b43/lcn2bsinitvals26.fw Extracting b43/lcn1initvals26.fw Extracting b43/n0bsinitvals22.fw Extracting b43/n18initvals32.fw Extracting b43/lcn2initvals26.fw Extracting b43/a0g1bsinitvals5.fw Extracting b43/n0bsinitvals11.fw Extracting b43/lcn2initvals24.fw Extracting b43/lcn0initvals26.fw Extracting b43/n0absinitvals11.fw Extracting b43/ucode21_sslpn_nobt.fw   ucode time:     01:15:07 Extracting b43/ucode26_mimo.fw Extracting b43/n2initvals19.fw Extracting b43/sslpn3initvals21.fw Extracting b43/a0g1bsinitvals13.fw Extracting b43/sslpn4initvals22.fw Extracting b43/pcm5.fw Extracting b43/ucode22_mimo.fw Extracting b43/ucode9.fw Extracting b43/lcn2initvals25.fw Extracting b43/lp1initvals22.fw Extracting b43/sslpn1bsinitvals27.fw Extracting b43/lcn0initvals24.fw Extracting b43/ucode32_mimo.fw Extracting b43/a0g0bsinitvals9.fw Extracting b43/n18bsinitvals32.fw Extracting b43/n0initvals24.fw Extracting b43/n0initvals25.fw Extracting b43/a0g1initvals5.fw Extracting b43/ucode24_lcn.fw Extracting b43/n0initvals17.fw Extracting b43/n0bsinitvals16.fw Extracting b43/lp0initvals15.fw Extracting b43/b0g0initvals5.fw Extracting b43/ucode20_sslpn_nobt.fw Extracting b43/lcn1initvals24.fw Extracting b43/sslpn0initvals16.fw Extracting b43/a0g1initvals13.fw Extracting b43/lp1bsinitvals20.fw Extracting b43/sslpn2initvals19.fw Extracting b43/a0g1initvals9.fw Extracting b43/lcn1bsinitvals24.fw Extracting b43/ucode5.fw Extracting b43/lcn2bsinitvals24.fw Extracting b43/lp0bsinitvals13.fw Extracting b43/n0initvals16.fw Extracting b43/ucode19_sslpn_nobt.fw Extracting b43/b0g0bsinitvals9.fw Extracting b43/ucode11.fw Extracting b43/lp0initvals16.fw Extracting b43/ucode16_mimo.fw Extracting b43/lcn0bsinitvals26.fw Extracting b43/ht0initvals29.fw Extracting b43/lcn2bsinitvals25.fw Extracting b43/a0g0initvals9.fw Extracting b43/ucode29_mimo.fw Extracting b43/lcn0bsinitvals24.fw Extracting b43/ucode19_sslpn.fw Extracting b43/lcn1initvals25.fw Extracting b43/ucode30_mimo.fw Extracting b43/n16bsinitvals30.fw Extracting b43/ucode25_mimo.fw Extracting b43/ucode24_mimo.fw Extracting b43/ucode27_sslpn.fw Extracting b43/lp0initvals13.fw Extracting b43/a0g0bsinitvals5.fw Extracting b43/ht0bsinitvals26.fw Extracting b43/ucode13.fw Extracting b43/sslpn2bsinitvals19.fw Extracting b43/ucode15.fw Extracting b43/lp0bsinitvals15.fw Extracting b43/n0initvals11.fw Extracting b43/lcn0initvals25.fw Extracting b43/sslpn0bsinitvals16.fw Extracting b43/sslpn1initvals20.fw Extracting b43/lcn1bsinitvals26.fw Extracting b43/n0initvals22.fw Extracting b43/ht0bsinitvals29.fw 
``` ```
~$ sudo modprobe -v b43 insmod /lib/modules/3.18.0-13-generic/kernel/net/wireless/cfg80211.ko  insmod /lib/modules/3.18.0-13-generic/kernel/net/mac80211/mac80211.ko  insmod /lib/modules/3.18.0-13-generic/kernel/drivers/bcma/bcma.ko  insmod /lib/modules/3.18.0-13-generic/kernel/drivers/net/wireless/b43/b43.ko 
``` ```
~$ dmesg | grep b43 [   29.253267] b43-phy0: Broadcom 4311 WLAN found (core revision 13) [   29.285790] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 9 [   29.285806] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 2, Version 0 [   29.296837] b43 ssb0:0: Direct firmware load for b43/ucode13.fw failed with error -2 [   29.296872] b43 ssb0:0: Direct firmware load for b43/ucode13.fw failed with error -2 [   29.296930] b43 ssb0:0: Direct firmware load for b43-open/ucode13.fw failed with error -2 [   29.296949] b43 ssb0:0: Direct firmware load for b43-open/ucode13.fw failed with error -2 [   29.296954] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found [   29.296959] b43-phy0 ERROR: Firmware file "b43-open/ucode13.fw" not found [   29.296963] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website. [ 1297.396699] b43-wlan ERROR: Dual-core devices are not supported [ 1297.396716] b43: probe of ssb0:0 failed with error -524 [ 1932.298691] b43-wlan ERROR: Dual-core devices are not supported [ 1932.298706] b43: probe of ssb0:0 failed with error -524 [ 1969.802083] b43-wlan ERROR: Dual-core devices are not supported [ 1969.802099] b43: probe of ssb0:0 failed with error -524 [ 4211.112275] b43-wlan ERROR: Dual-core devices are not supported [ 4211.112291] b43: probe of ssb0:0 failed with error -524 
```

---

### Post by jeremy31 on 2015-02-13
I saw your post on [https://answers.launchpad.net/ubuntu/+question/261996](https://answers.launchpad.net/ubuntu/+question/261996) and your device will work on Ubuntu 14.04 which is a version that will be supported until 2019(IIRC)
After you install you will need to ```
sudo apt-get install firmware-b43-installer
``` using a wired connection and then reboot and it will normally work.  Just do a google search for your wifi device ID which is [COLOR=#333333][FONT=Ubuntu][14e4:4311]  to see how many posts are marked solved[/FONT][/COLOR]

---

### Post by desesperado on 2015-02-14
@ [COLOR=#000000]Hadaka, [/COLOR][COLOR=#000000]chili555 [/COLOR][COLOR=#000000]and jeremy31[/COLOR]
Thanks for your all the help and knowledge you three have been so kind to provided me. You truly make the Ubuntu motto a reality. 

I guess I have no other choice than take a leap of faith and install Xubuntu on the laptop. The first thing I'll do after installation will be the execution of the command```
sudo apt-get update && sudo apt-get install firmware-b43-installer
```and then reboot (keeping my fingers crossed  the all time).

I'll get back to report how it all end up well - hopefully - or to get further help/assistance from you.

---

### Post by desesperado on 2015-02-18
Everything worked as expected, after a full install in the HDD.```
~$ ifconfig 
eth0      Link encap:Ethernet  Endereço de HW 00:1b:38:8d:b3:bf  
          inet end.: 10.40.111.20  Bcast:10.40.111.255  Masc:255.255.255.0
          endereço inet6: fe80::21b:38ff:fe8d:b3bf/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:34435 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:27961 erros:0 descartados:0 excesso:3 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:37332982 (37.3 MB) TX bytes:2775087 (2.7 MB)

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:65536  Métrica:1
          pacotes RX:4843 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:4843 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:471808 (471.8 KB) TX bytes:471808 (471.8 KB)

wlan0     Link encap:Ethernet  Endereço de HW 00:1a:73:b9:37:ec  
          endereço inet6: fe80::21a:73ff:feb9:37ec/64 Escopo:Link
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
          IRQ:16 
```
Again, thanks for all your help, Hadaka, chili555 and jeremy31.

---

### Post by malic2 on 2015-04-30
I have the same laptop... but with Lubuntu. What's your experience with Xubuntu?

My internal speakers and DVD drive are spoilt... ever had any replacements?

---

