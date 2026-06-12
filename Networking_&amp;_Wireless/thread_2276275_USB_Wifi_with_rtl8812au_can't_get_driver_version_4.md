---
title: "USB Wifi with rtl8812au: can't get driver version 4.3.8 to work (but 4.2.2 works)"
date: 2015-05-01
forum: Networking &amp; Wireless
---

### Post by simon94 on 2015-05-01
I'm using driver version 4.2.2 since a few weeks from here: [https://github.com/gnab/rtl8812au](https://github.com/gnab/rtl8812au)
Installed it as described here: [http://ubuntuforums.org/showthread.php?t=2259890](http://ubuntuforums.org/showthread.php?t=2259890)

Although 4.2.2 works fine, it's just speed wise the performance is rather poor, much slower than on Windows with the windows drivers. Now I have discovered that there is a version 4.3.8 of this driver available, which supposedly gives much better speed. One of the forks can be found here: [https://github.com/vsurrel/rtl8812au](https://github.com/vsurrel/rtl8812au)

When I compile and load the module, it doesn't seem to detect my Edimax USB Wifi. I tried to add the USB descriptors of my adapter to the source and re-compile, as described by chili555 in the thread I linked. I did that but it still won't detect my driver.

lsusb:
```

[COLOR=#000000][FONT=monospace]Bus 004 Device 004: ID 7392:a812 Edimax Technology Co., Ltd
[/FONT][/COLOR]
```[COLOR=#000000][FONT=monospace]

modinfo of the 4.2.2 working driver:
[/FONT][/COLOR]```

[FONT=monospace][COLOR=#000000]version:        v4.2.2_7502.20130517[/COLOR]
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     3424792CB6F8055CE7AE336
alias:          usb:v2019pAB32d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9052d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3314d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0821d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p805Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3316d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3315d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB30d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p003Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1058p0632d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3313d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3426d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0022d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17D2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0409p0408d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p016Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0952d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0074d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p330Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1106d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8812d*dc*dsc*dp*ic*isc*ip*in*[/FONT]

```[COLOR=#000000][FONT=monospace]

modinfo of the 4.3.8 driver:
[/FONT][/COLOR]```

[FONT=monospace][COLOR=#000000]version:        v4.3.8_12175.20140902[/COLOR]
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     F7DE2E5E9365393D121066E
alias:          usb:v2001p3316d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3315d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB30d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1058p0632d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3313d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3426d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0022d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17D2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0409p0408d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p016Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0952d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0074d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p330Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1106d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8812d*dc*dsc*dp*ic*isc*ip*in*[/FONT]

```[COLOR=#000000][FONT=monospace]

Obviously my device is not listed. I have added this line:

[/FONT][/COLOR]```

{USB_DEVICE(0x7392, 0xA812),.driver_info = RTL8821}, /* Edimax - EW-7811UTC */

```

to usb_intf.c. I copied this line from the gnab github fork.

Just for reference, here is the whole ifdef block (in case I messed up somehwere):

```

#ifdef CONFIG_RTL8821A
        /*=== Realtek demoboard ===*/
    {USB_DEVICE(USB_VENDER_ID_REALTEK, 0x0811),.driver_info = RTL8821},/* Default ID */
    {USB_DEVICE(USB_VENDER_ID_REALTEK, 0x0821),.driver_info = RTL8821},/* Default ID */
    {USB_DEVICE(USB_VENDER_ID_REALTEK, 0x8822),.driver_info = RTL8821},/* Default ID */
    {USB_DEVICE_AND_INTERFACE_INFO(USB_VENDER_ID_REALTEK, 0x0820,0xff,0xff,0xff),.driver_info = RTL8821}, /* 8821AU */
    /*=== Customer ID ===*/
    {USB_DEVICE(0x7392, 0xA811),.driver_info = RTL8821}, /* Edimax - Edimax */
    {USB_DEVICE(0x04BB, 0x0953),.driver_info = RTL8821}, /* I-O DATA - Edimax */
    {USB_DEVICE(0x7392, 0xA812),.driver_info = RTL8821}, /* Edimax - EW-7811UTC */
    {USB_DEVICE(0x2001, 0x3314),.driver_info = RTL8821}, /* D-Link - Cameo */
    {USB_DEVICE(0x2001, 0x3318),.driver_info = RTL8821}, /* D-Link - Cameo */
    {USB_DEVICE(0x0E66, 0x0023),.driver_info = RTL8821}, /* HAWKING - Edimax */
#endif

```

then I did "make clean & make", loaded the compiled module with "insmod 8812au.ko". Module loads fine, but it won't detect my adapter.

I realize this is not a trivial problem, and not many know about driver stuff (like me), but I hope that chili555 or someone else will see this thread and come to the rescue :D

---

### Post by chili555 on 2015-05-01
It's not often that I get called out publicly on the forums! I was interested to see my name this morning!

I must congratulate you for getting this far. Among the gurus on this forum, both real and imagined, there are maybe two or three that can navigate this stuff. Since you seem more adept than most, I'll just give you the highlights and I think you'll see the solution. If not, post back and I'll be very glad to help.

You said:> Just for reference, here is the whole ifdef block (in case I messed up somehwere):



```
#ifdef CONFIG_[COLOR="#FF0000"]RTL8821A[/COLOR]
        /*=== Realtek demoboard ===*/
    {USB_DEVICE(USB_VENDER_ID_REALTEK, 0x0811),.driver_info = RTL8821},/* Default ID */
    {USB_DEVICE(USB_VENDER_ID_REALTEK, 0x0821),.driver_info = RTL8821},/* Default ID */
    {USB_DEVICE(USB_VENDER_ID_REALTEK, 0x8822),.driver_info = RTL8821},/* Default ID */
    {USB_DEVICE_AND_INTERFACE_INFO(USB_VENDER_ID_REALTEK, 0x0820,0xff,0xff,0xff),.driver_info = RTL8821}, /* 8821AU */
    /*=== Customer ID ===*/
    {USB_DEVICE(0x7392, 0xA811),.driver_info = RTL8821}, /* Edimax - Edimax */
    {USB_DEVICE(0x04BB, 0x0953),.driver_info = RTL8821}, /* I-O DATA - Edimax */
    {USB_DEVICE(0x7392, 0xA812),.driver_info = RTL8821}, /* Edimax - EW-7811UTC */
    {USB_DEVICE(0x2001, 0x3314),.driver_info = RTL8821}, /* D-Link - Cameo */
    {USB_DEVICE(0x2001, 0x3318),.driver_info = RTL8821}, /* D-Link - Cameo */
    {USB_DEVICE(0x0E66, 0x0023),.driver_info = RTL8821}, /* HAWKING - Edimax */
#endif

```
I put some highlighting in there to help.

I think I might instead try the change here:```
#ifdef CONFIG_[COLOR="#FF0000"]RTL8812A[/COLOR]
	/*=== Realtek demoboard ===*/
	{USB_DEVICE(USB_VENDER_ID_REALTEK, 0x8812),.driver_info = RTL8812},/* Default ID */
	{USB_DEVICE(USB_VENDER_ID_REALTEK, 0x881A),.driver_info = RTL8812},/* Default ID */
	{USB_DEVICE(USB_VENDER_ID_REALTEK, 0x881B),.driver_info = RTL8812},/* Default ID */
	{USB_DEVICE(USB_VENDER_ID_REALTEK, 0x881C),.driver_info = RTL8812},/* Default ID */
	/*=== Customer ID ===*/
	{USB_DEVICE(0x050D, 0x1106),.driver_info = RTL8812}, /* Belkin - sercomm */
	{USB_DEVICE(0x2001, 0x330E),.driver_info = RTL8812}, /* D-Link - ALPHA */
	{USB_DEVICE(0x7392, 0xA822),.driver_info = RTL8812}, /* Edimax - Edimax */
	{USB_DEVICE(0x0DF6, 0x0074),.driver_info = RTL8812}, /* Sitecom - Edimax */
        [COLOR="#FF0000"]{USB_DEVICE(0x7392, 0xA812),.driver_info = RTL**8812**}, /* Edimax - EW-7811UTC */[/COLOR]
	{USB_DEVICE(0x04BB, 0x0952),.driver_info = RTL8812}, /* I-O DATA - Edimax */
	{USB_DEVICE(0x0789, 0x016E),.driver_info = RTL8812}, /* Logitec - Edimax */
	{USB_DEVICE(0x0409, 0x0408),.driver_info = RTL8812}, /* NEC - */
	{USB_DEVICE(0x0B05, 0x17D2),.driver_info = RTL8812}, /* ASUS - Edimax */
	{USB_DEVICE(0x0E66, 0x0022),.driver_info = RTL8812}, /* HAWKING - Edimax */
	{USB_DEVICE(0x0586, 0x3426),.driver_info = RTL8812}, /* ZyXEL - */
	{USB_DEVICE(0x2001, 0x3313),.driver_info = RTL8812}, /* D-Link - ALPHA */
	{USB_DEVICE(0x1058, 0x0632),.driver_info = RTL8812}, /* WD - Cybertan*/
	{USB_DEVICE(0x1740, 0x0100),.driver_info = RTL8812}, /* EnGenius - EnGenius */
	{USB_DEVICE(0x2019, 0xAB30),.driver_info = RTL8812}, /* Planex - Abocom */
	{USB_DEVICE(0x07B8, 0x8812),.driver_info = RTL8812}, /* Abocom - Abocom */
	{USB_DEVICE(0x2001, 0x3315),.driver_info = RTL8812}, /* D-Link - Cameo */
	{USB_DEVICE(0x2001, 0x3316),.driver_info = RTL8812}, /* D-Link - Cameo */
#endif

```In other words, you put in 8821 and I suspect it belongs in 8812. Please try it and let me and the searchers know the result.

---

### Post by simon94 on 2015-05-01
When I bought this adapter I expected it to be plug and play, just like my old 2.4 GHz adapter and because it said "Compatible with Linux" on the box. Had I known that this thing would be such a pain I wouldn't have bought it. Now the consumer has to rely on github repos. But at least I learned something about modprobe & Co :)

Anyway, once I figured out that I need the 8812au driver/module, a google search turned your thread on 2nd place, and with that info it was simple to get this thing running. It was easy and concise to follow, so thanks a bunch for that :) And now I'm here trying to get the newer driver running to fix the performance issues the current one has.

Anyway, thanks a lot for your suggestion! I copied the line from gnabs repo: [https://github.com/gnab/rtl8812au/blob/master/os_dep/linux/usb_intf.c#L288](https://github.com/gnab/rtl8812au/blob/master/os_dep/linux/usb_intf.c#L288)

There it is indeed 8821, instead of 8812, and gnabs driver works for me when I compile and load it.

But I have tried your suggestion anyway, and interestingly it will show up in modinfo! When I unload the current module with "sudo modprobe -r 8812au" and then load the new one with insmod, Now I get a lot of "RTL871X" dmesg messages, it looks like an endless loop because the messages keep repeating itself.

I have the feeling that version 4.3.8 simply does not support my adapter, because a quick diff between 4.2.2 and 4.3.8 shows many big code changes and I think it could be likely that my adapter wasn't supposed to be supported right from the start. Realteks naming is also really strange, the drivers name is "rtl8812au", but it seems to support many different rtlXXXX devices. dmesg log messages show up as "RTL871X", what the heck? So my feeling tells me this is going to be hopeless, I'll probably just trash this one and buy a new adapter with better Linux support. But of course let me know if you have any other ideas what I might try, I'm not afraid to do crazy things haha, it's at the very least a nice learning experience :)

I just discovered these flags in the makefile:

```

########################## WIFI IC ############################
CONFIG_MULTIDRV = n
CONFIG_RTL8192C = n
CONFIG_RTL8192D = n
CONFIG_RTL8723A = n
CONFIG_RTL8188E = n
CONFIG_RTL8812A = y
CONFIG_RTL8821A = n
CONFIG_RTL8192E = n
CONFIG_RTL8723B = n

```

I didn't know there are such flags! No wonder that modinfo didn't show my device, because 8821 was disabled!

I've changed it to "y" but unfortunately it won't compile :(

```

[FONT=monospace][COLOR=#000000]In file included from /mnt/shared/data/Downloads/rtl8812au/vsurrel/rtl8812au/include/hal_data.h:25:0,[/COLOR]
                 from /mnt/shared/data/Downloads/rtl8812au/vsurrel/rtl8812au/core/rtw_pwrctrl.c:23:
/mnt/shared/data/Downloads/rtl8812au/vsurrel/rtl8812au/include/../hal/OUTSRC/phydm_precomp.h:199:67: fatal error: rtl8821a/HalPhyRf_8821A.h: No such file or directory
   #include "rtl8821a/HalPhyRf_8821A.h"//for IQK,LCK,Power-tracking
                                                                   ^
compilation terminated.
scripts/Makefile.build:257: recipe for target '/mnt/shared/data/Downloads/rtl8812au/vsurrel/rtl8812au/core/rtw_pwrctrl.o' failed
make[2]: *** [/mnt/shared/data/Downloads/rtl8812au/vsurrel/rtl8812au/core/rtw_pwrctrl.o] Error 1
Makefile:1386: recipe for target '_module_/mnt/shared/data/Downloads/rtl8812au/vsurrel/rtl8812au' failed
make[1]: *** [_module_/mnt/shared/data/Downloads/rtl8812au/vsurrel/rtl8812au] Error 2
make[1]: Leaving directory '/usr/lib/modules/3.19.5-1-ck/build'
Makefile:1456: recipe for target 'modules' failed
make: *** [modules] Error 2
[/FONT]
```[FONT=monospace]

But at least this is a hint: "[/FONT][COLOR=#000000][FONT=monospace]rtl8821a/HalPhyRf_8821A.h: No such file or directory"

I have no clue about C++ but i'll see if I can find this file somewhere and get it to compile...[/FONT][/COLOR]

---

### Post by chili555 on 2015-05-01
> I think it could be likely that my adapter wasn't supposed to be supported right from the start. Realteks naming is also really strange, the drivers name is "rtl8812au", but it seems to support many different rtlXXXX devices. dmesg log messages show up as "RTL871X", what the heck? So my feeling tells me this is going to be hopelessI agree as to the 4.3.8 version. That suggests an explanation for the usb.id being dropped altogether.

Before you trash the device and start over, may we troubleshoot your speed issue on the 4.2.2 version? There are things we might try at the router and I see that there a great many driver parameters in the existing driver.```
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_regulatory_id:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_bw_mode:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_vht_enable:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)

```The exact usage of these parameters is remarkably undocumented. However, if you intend to trash the device anyway, we might just throw a few guesses at it.

---

### Post by chili555 on 2015-05-01
> But at least this is a hint: "rtl8821a/HalPhyRf_8821A.h: No such file or directory"I wonder if vsurrel stripped away all the parts he didn't need. It exists in other versions of the driver:> $ locate HalPhyRf_8821A.h
/home/chili/Downloads/rtl8812au-master/hal/OUTSRC/rtl8821a/HalPhyRf_8821A.h
/home/chili/rtl8812AU_8821AU_linux/hal/OUTSRC/rtl8821a/HalPhyRf_8821A.h

---

### Post by simon94 on 2015-05-01
I did a bit more research and this is what I found out: It seems that at one point the 8812au driver supported both devices/chips, the rtl8812 and rtl8821.

I don't think vsurrel has explicitly stripped away the rtl8821 code files. Every 4.3.8 version I have found so far on the internet doesn't have the code files. All device specific code files are located in the "hal/OUTSRC" directory. The 4.2.2 diver has both in there, "rtl8812a" and "rtl8821a", while 4.3.8 has only "rtl8812a"

But there seems to be hope, I discovered this github repo: [https://github.com/ulli-kroll/rtl8821au](https://github.com/ulli-kroll/rtl8821au)

He's basically reintegrating the rtl8821a code files into the 4.3.8 driver. I'm cloning his repo now and will give it a try. I just don't understand this line in his readme:

"STATUS: Currently driver works with old wireless extension only No support for iw"

What does that mean? I know there is this "iw" command for wifi related stuff. Is this required to make the network manager applet work? (I'm using Kubuntu 15.04 and Arch Linux, also with KDE 5, by the way). Anyway, will try to compile it and report back.

If nothing works I'd be willing to try the driver parameters and router config. But I must admit that the current performance isn't *that* bad: I have a 100 Mbit/s internet connection (cable provider), and on Windows I get with this adapter around ~85 Mbit/s, while on Linux I get "only" ~50 Mbit/s. That's not thaaat bad, but since I'm paying for 100 Mbit I'd like to get the max out of my connection.

So I just tried Ulli Krolls fork, and it looks like it detects my adapter. dmesg is spewing a lot of messages, but I'm not able to connect to my wifi. The network applet is trying to connect in an endless loop, and I guess this will have something to do with the disclaimer he put there. I think KDEs network applet is depending on NetworkManager, and I think that in turn is depending on iw, and I will have to use the "old wireless extension" to make it work I suppose, whatever that is :D I guess I'm off to another couple of hours of google searching, but I think I'll just go and buy a new wifi adapter in the end, to save my weekend and sanity :)

And let me know what kind of optimizations would be possible on router side, I'd be really curious because I run it pretty much on default settings, except that I of course have changed passwords and picked a less-crowded channel. But other than that I didn't configure anything. If there is anything to generally improve wifi speed then I'm all ears! I have a D-Link DIR-825, not the newest model but it just works since 4 years or so. I'm using 5 GHz, there are only 2 other wifis in my neighborhood on that frequency, while 2.4 GHz is crowded with 20 other wifis. I get only ~15 Mbit/s on that frequency.

---

### Post by chili555 on 2015-05-01
This is my recipe honed over the years.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better connectivity (but not necessarily N speeds) with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

### Post by simon94 on 2015-05-08
Hi chilli!

thanks a lot for your suggestions and sorry for not getting back to you earlier. Unfortunately I didn't have had the time to spend on my linux PC at home until now.

I have now applied your suggestions, and today I've also bought a new USB Wifi adapter, the TP-Link T4U. Ironically this one is also a rtl8812au based adapter. But at least this one is supported by the newer 4.3.8 driver, and I'm very happy with it so far! Speed is great, I get almost the whole 100 Mbit downstream of my cable ISP. See:

[img]http://www.speedtest.net/result/4346592565.png[/img]

I even get the same results when I connect with 2.4 GHz instead of 5 Ghz! I'm amazed!

Thanks a lot for your help! It was a great learning experience :)

---

### Post by andrea-cimatoribus on 2015-05-18
Did anyone have any success with this driver? I am struggling to get Alfa AWUS036AC device working properly.
The linux driver they provide on [http://www.alfa.com.tw](http://www.alfa.com.tw) does not compile on Ubuntu 14.04 (even it works fine on Linux Mint 17).
I found this driver [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux) which compiles and works on Ubuntu, but then connection quality is very bad, worse than with the laptop card.

---

### Post by chili555 on 2015-05-18
> **andrea-cimatoribus said:**
> Did anyone have any success with this driver? I am struggling to get Alfa AWUS036AC device working properly.
The linux driver they provide on [http://www.alfa.com.tw](http://www.alfa.com.tw) does not compile on Ubuntu 14.04 (even it works fine on Linux Mint 17).
I found this driver [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux) which compiles and works on Ubuntu, but then connection quality is very bad, worse than with the laptop card.May we have a look at some diagnostics?```
modinfo 8812au | grep -i version
dmesg | grep -e wlan -e 8812au
```Thanks.

---

### Post by andrea-cimatoribus on 2015-05-18
I see I made a mistake, I am using 8821au module, not 8812au, so I'll start a new thread as soon as I am home and have the wi-fi card at hand.

---

### Post by simon94 on 2015-05-18
I didn't even know there is an explicit 8821au module, I've always compiled and used the 8812au module, which until version 4.2.2 supports both, rtl8812 and rtl8821 chipsets. The 4.3.8 version that floats around on github supports the rtl8812 chipset only. I'm now using vsurrels fork: [https://github.com/vsurrel/rtl8812au](https://github.com/vsurrel/rtl8812au)
This one compiles on all kernels, including the latest 4.x kernel. I couldn't get my rtl8812 based USB wifi (Archer T4U) to work on 5 GHz with the 4.2.2 drivers, but 4.3.8 works flawlessly with a very good speed so far, so you might want to give that one a try. I had to add the USB descriptor IDs of the T4U to the source file though, but the driver seems to work just fine.

---

### Post by andrea-cimatoribus on 2015-05-18
I started another dedicated thread. However, after a quick check, it compiles and installs, the card is recognised but doesn't even see any network at all.

Ok, this is even more confusing. Just for the sake of it, I tried to recompile the alfa driver (version 4.3.14). All of a sudden, I get a very good connection. There must be a reason, something that I changed without noticing, but I have no clue what.

---

### Post by ElektromAn on 2015-06-21
> **simon94 said:**
> 
But there seems to be hope, I discovered this github repo: [https://github.com/ulli-kroll/rtl8821au](https://github.com/ulli-kroll/rtl8821au)

He's basically reintegrating the rtl8821a code files into the 4.3.8 driver. I'm cloning his repo now and will give it a try. I just don't understand this line in his readme:

"STATUS: Currently driver works with old wireless extension only No support for iw"

What does that mean? I know there is this "iw" command for wifi related stuff. Is this required to make the network manager applet work? (I'm using Kubuntu 15.04 and Arch Linux, also with KDE 5, by the way). Anyway, will try to compile it and report back.

What's the matter.

Network manager will work, but you can't use the extented stuff from the iw utility.

---

