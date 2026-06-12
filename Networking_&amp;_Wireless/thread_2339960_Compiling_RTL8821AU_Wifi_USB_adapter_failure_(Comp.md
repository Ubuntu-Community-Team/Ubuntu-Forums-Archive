---
title: "Compiling RTL8821AU Wifi USB adapter failure (Compile make driver error: 2)"
date: 2016-10-14
forum: Networking &amp; Wireless
---

### Post by hunterni on 2016-10-14
I just bought a Realtek usb wifi adapter for an old computer I got running linux. I'm completely fresh to linux so all of this is very new to me. When I run the installation bash script (install.sh), I'm getting this error:

[FONT=arial]scripts/Makefile.build:258: recipe for target '/home/nick/Documents/linux/[/FONT][FONT=arial]driver/rtl8821AU_linux_v4.3.[/FONT][FONT=arial]14_13455.20150212_[/FONT][FONT=arial]BTCOEX20150128-51/core/rtw_[/FONT][FONT=arial]cmd.o' failed[/FONT]
[FONT=arial]make[2]: *** [/home/nick/Documents/linux/[/FONT][FONT=arial]driver/rtl8821AU_linux_v4.3.[/FONT][FONT=arial]14_13455.20150212_[/FONT][FONT=arial]BTCOEX20150128-51/core/rtw_[/FONT][FONT=arial]cmd.o] Error 1[/FONT]
[FONT=arial]Makefile:1403: recipe for target '_module_/home/nick/Documents/[/FONT][FONT=arial]linux/driver/rtl8821AU_linux_[/FONT][FONT=arial]v4.3.14_13455.20150212_[/FONT][FONT=arial]BTCOEX20150128-51' failed[/FONT]
[FONT=arial]make[1]: *** [_module_/home/nick/Documents/[/FONT][FONT=arial]linux/driver/rtl8821AU_linux_[/FONT][FONT=arial]v4.3.14_13455.20150212_[/FONT][FONT=arial]BTCOEX20150128-51] Error 2[/FONT]
[FONT=arial]make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-[/FONT][FONT=arial]31-generic'[/FONT]
[FONT=arial]Makefile:1551: recipe for target 'modules' failed[/FONT]
[FONT=arial]make: *** [modules] Error 2[/FONT]
[FONT=arial]##############################[/FONT][FONT=arial]####################[/FONT]
[FONT=arial]Compile make driver error: 2[/FONT]
[FONT=arial]Please check error Mesg

Realtek makes it seem like this particular adapter might not work for the kernel version I'm using (4.3.14), but I've read things that make it sound like it's possible to get it running. Anyone know how to troubleshoot this? Thanks!

Oh and I've done already done [sudo apt-get update] and [sudo apt-get dist-upgrade].[/FONT]

---

### Post by chili555 on 2016-10-14
Just because we love to be precise (read: insecure), we'd love to verify the device first. Please run and post:```
lsusb
```

---

### Post by hunterni on 2016-10-14
Ok. I'm at work now but when I get home I will.

---

### Post by hunterni on 2016-10-14
After running lsusb it returned this:

Bus 001 Device 002: ID 0bda:0811 Realtek Semiconductor Corp.

---

### Post by chili555 on 2016-10-14
Please try: 

```
sudo apt-get update
sudo apt-get install rtl8812au-dkms
```
You should be all set.

---

### Post by hunterni on 2016-10-14
It looked really promising as it ran for a bit! But then it gave the same exact error message. 

The part that says "please check error Mesg", any idea how to do that and if that would diagnose the problem?

---

### Post by chili555 on 2016-10-14
Doesn't it say: > Consult /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/make.log for more information.
...Or some such. You look exactly there!```
cat  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/make.log 
```I suspect we have a train-wreck and need to report a bug. If so, we'll do so and then look elsewhere for a driver.

---

### Post by hunterni on 2016-10-14
I checked that path (how did you find that by the way?) and there isn't a make.log file. There exist the directories: core, hal, include, os_dep, and platform. And also the files: dkms.conf, Kconfig, and Makefile.

What are the first steps in reporting a bug? I feel so lost in all of this! But I really am bowled over by the support from this forum/community! Thank you, chili555.

---

### Post by jeremy31 on 2016-10-14
Show the result for ```
ls /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/
```

---

### Post by hunterni on 2016-10-14
```
nick@ubuntu:/var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build$ ls -a
.  ..  core  dkms.conf  hal  include  Kconfig  Makefile  os_dep  platform
```

---

### Post by chili555 on 2016-10-14
It's a known bug. [https://bugs.launchpad.net/ubuntu/+source/rtl8812au/+bug/1625097](https://bugs.launchpad.net/ubuntu/+source/rtl8812au/+bug/1625097)

Please try:```
sudo apt update
sudo apt install git
git clone https://github.com/diederikdehaas/rtl8812AU.git
cd rtl8812AU
make
sudo make install
sudo modprobe 8812au
```You may encounter a few warnings but it should install and work.

Let us know as we will have another step.

---

### Post by hunterni on 2016-10-15
It's giving the same error message after navigating to:

```
nick@ubuntu:~/Documents/linux$ ls
android_ref_codes_JB_4.2  driver      readme.txt                  wireless_tools
android_ref_codes_KK_4.4  install.sh  ReleaseNotes.pdf            wpa_supplicant_hostapd
document                  mp_tools    WiFi_Direct_User_Interface
```

and running install.sh.


So now I have a directory with the new driver information, correct? But the old one still exists as the tar.gz file alongside that new directory:

```
nick@ubuntu:~/Documents/linux/driver$ ls
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51.tar.gz
```

Could that be a problem?

---

### Post by chili555 on 2016-10-15
> rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51.tar.gzThis is unrelated to my post just above. Did you try it?

I suspect that the file you downloaded is too old for your 4.4.0-xx kernel and, also, it appears to be written for Android. Please abandon it.

---

### Post by hunterni on 2016-10-15
I did try and I got the same error message as before. However, when I ran the install script from the new RTL8812AU directory that was downloaded from your previous instructions:

```
nick@ubuntu:~/rtl8812AU$ sudo bash /home/nick/Documents/linux/install.sh
```

I got something that indicated things were going well...maybe?? Here it is: 

```
Compile make driver ok!!
##################################################
Authentication requested [root] for remove driver:
Authentication requested [root] for insert driver:
insmod: ERROR: could not insert module 8812au.ko: Unknown symbol in module
Authentication requested [root] for install driver:
install -p -m 644 8812au.ko  /lib/modules/4.4.0-43-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 4.4.0-43-generic
##################################################
The Setup Script is completed !
```

It had run things before it but this seemed like the most relevant output. Is there any hope??

---

### Post by chili555 on 2016-10-15
> Is there any hope??What do you think?> insmod: ERROR: could not insert module 8812au.ko: Unknown symbol in moduleThat doesn't sound hopeful to me. What is the result of:```
sudo modprobe 8812au
```> I did try and I got the same error message as before.It would have been nice to know that, see the error and attempt to troubleshoot. Perhaps you know best.

For what it's worth, the git version 'makes' on my 4.8.0-xx system with a couple of warnings only; no errors.

---

### Post by hunterni on 2016-10-15
There is no output after running

```
sudo modprobe 8812au
```

Well I appreciate all your help. I have no idea what I'm doing so if you say we're at a wall I'll stop while I'm ahead. I've at least learned somethings in the process.

---

### Post by chili555 on 2016-10-15
> There is no output after running

Code:
sudo modprobe 8812auThat's a good sign, actually. Is the module present here?```
lsmod | grep 8812
```Does it cover your device?```
modinfo 8812au | grep 0811 
```Does the wireless work? 

Any clues in the log?```
dmesg | grep 8812
```

---

### Post by hunterni on 2016-10-15
I apologize, but I'm really new to all of this so I'm going to post this and see if you can make sense of it: 

```
nick@ubuntu:~/rtl8812AU$ lsmod | grep 8812
8812au                790528  0
nick@ubuntu:~/rtl8812AU$ modinfo 8812au | grep 0811
nick@ubuntu:~/rtl8812AU$ 
nick@ubuntu:~/rtl8812AU$ dmesg | grep 8812
[    1.881207] scsi 2:0:0:0: Direct-Access     ATA      WDC WD7500AAVS-0 1A01 PQ: 0 ANSI: 5
[  768.311363] 8812au: module verification failed: signature and/or required key missing - tainting kernel
[  768.322373] RTL871X: rtl8812au v4.3.8_12175.20140902
[  768.322470] usbcore: registered new interface driver rtl8812au
[ 2249.434234] usbcore: deregistering interface driver rtl8812au
[ 2249.472521] 8812au: Unknown symbol __cfg80211_alloc_event_skb (err 0)
[ 2249.472553] 8812au: Unknown symbol wiphy_register (err 0)
[ 2249.472574] 8812au: Unknown symbol cfg80211_remain_on_channel_expired (err 0)
[ 2249.472618] 8812au: Unknown symbol cfg80211_vendor_cmd_reply (err 0)
[ 2249.472637] 8812au: Unknown symbol cfg80211_del_sta_sinfo (err 0)
[ 2249.472656] 8812au: Unknown symbol wiphy_unregister (err 0)
[ 2249.472762] 8812au: Unknown symbol cfg80211_ready_on_channel (err 0)
[ 2249.472785] 8812au: Unknown symbol __ieee80211_get_channel (err 0)
[ 2249.472828] 8812au: Unknown symbol wiphy_free (err 0)
[ 2249.472842] 8812au: Unknown symbol wiphy_new_nm (err 0)
[ 2249.472856] 8812au: Unknown symbol cfg80211_get_bss (err 0)
[ 2249.472884] 8812au: Unknown symbol __cfg80211_send_event_skb (err 0)
[ 2249.472910] 8812au: Unknown symbol cfg80211_disconnected (err 0)
[ 2249.472929] 8812au: Unknown symbol cfg80211_michael_mic_failure (err 0)
[ 2249.472954] 8812au: Unknown symbol cfg80211_ibss_joined (err 0)
[ 2249.473009] 8812au: Unknown symbol cfg80211_scan_done (err 0)
[ 2249.473026] 8812au: Unknown symbol cfg80211_roamed (err 0)
[ 2249.473039] 8812au: Unknown symbol cfg80211_put_bss (err 0)
[ 2249.473084] 8812au: Unknown symbol cfg80211_unlink_bss (err 0)
[ 2249.473108] 8812au: Unknown symbol cfg80211_connect_result (err 0)
[ 2249.473122] 8812au: Unknown symbol cfg80211_inform_bss_frame_data (err 0)
[ 2249.473145] 8812au: Unknown symbol cfg80211_new_sta (err 0)
[ 2249.473178] 8812au: Unknown symbol __cfg80211_alloc_reply_skb (err 0)
[ 2249.473197] 8812au: Unknown symbol cfg80211_rx_mgmt (err 0)
[ 2249.473213] 8812au: Unknown symbol ieee80211_frequency_to_channel (err 0)
[ 2249.473229] 8812au: Unknown symbol wiphy_apply_custom_regulatory (err 0)
[ 2249.473246] 8812au: Unknown symbol cfg80211_mgmt_tx_status (err 0)
[ 4406.914025] RTL871X: rtl8812au v4.3.8_12175.20140902
[ 4406.914120] usbcore: registered new interface driver rtl8812au
```

---

### Post by chili555 on 2016-10-15
> nick@ubuntu:~/rtl8812AU$ modinfo 8812au | grep 0811
nick@ubuntu:~/rtl8812AU$ There you have it. The driver you compiled doesn't support your device. Even if we can overcome its many issues, it won't work.

Would you mind trying the git version and post the error?

It *DOES *support your device:```
chili@chili:~$ modinfo Desktop/Forum/rtl8812AU/8812au.ko | grep 0811
alias:          usb:v[COLOR="#FF0000"]0BDA[/COLOR]p[COLOR="#FF0000"]0811[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*

```

---

### Post by hunterni on 2016-10-15
Sorry, you mean run the install with the git version? Here's the error:

```
scripts/Makefile.build:258: recipe for target '/home/nick/Documents/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o' failed
make[2]: *** [/home/nick/Documents/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o] Error 1
Makefile:1403: recipe for target '_module_/home/nick/Documents/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51' failed
make[1]: *** [_module_/home/nick/Documents/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-43-generic'
Makefile:1551: recipe for target 'modules' failed
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################
```

Again, thanks for all your help. I'll have to find another way to get an internet connection I guess.

---

### Post by chili555 on 2016-10-15
> rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51That is not the git version.

---

### Post by hunterni on 2016-10-15
How do I install with the git version?

---

### Post by chili555 on 2016-10-15
Exactly as I outlined in post #11. I thought you said you tried it and got an error. No?

---

### Post by hunterni on 2016-10-15
When I run ```
sudo modprobe 8812au
``` nothing happens. There is not result.

---

### Post by chili555 on 2016-10-15
> **hunterni said:**
> When I run ```
sudo modprobe 8812au
``` nothing happens. There is not result.Was the device inserted?

Any clues in the log?```
dmesg | grep 8812
iwconfig
```

---

### Post by hunterni on 2016-10-15
Yeah, the device was inserted. This is what I got:
```
nick@ubuntu:~$ dmesg | grep 8812
[ 1432.486060] 8812au: module verification failed: signature and/or required key missing - tainting kernel
[ 1432.490622] RTL871X: rtl8812au v4.3.8_12175.20140902
[ 1432.490710] usbcore: registered new interface driver rtl8812au
[ 1693.905745] usbcore: deregistering interface driver rtl8812au
[ 1693.948793] 8812au: Unknown symbol __cfg80211_alloc_event_skb (err 0)
[ 1693.948823] 8812au: Unknown symbol wiphy_register (err 0)
[ 1693.948843] 8812au: Unknown symbol cfg80211_remain_on_channel_expired (err 0)
[ 1693.948887] 8812au: Unknown symbol cfg80211_vendor_cmd_reply (err 0)
[ 1693.948905] 8812au: Unknown symbol cfg80211_del_sta_sinfo (err 0)
[ 1693.948924] 8812au: Unknown symbol wiphy_unregister (err 0)
[ 1693.949030] 8812au: Unknown symbol cfg80211_ready_on_channel (err 0)
[ 1693.949053] 8812au: Unknown symbol __ieee80211_get_channel (err 0)
[ 1693.949096] 8812au: Unknown symbol wiphy_free (err 0)
[ 1693.949109] 8812au: Unknown symbol wiphy_new_nm (err 0)
[ 1693.949123] 8812au: Unknown symbol cfg80211_get_bss (err 0)
[ 1693.949151] 8812au: Unknown symbol __cfg80211_send_event_skb (err 0)
[ 1693.949177] 8812au: Unknown symbol cfg80211_disconnected (err 0)
[ 1693.949196] 8812au: Unknown symbol cfg80211_michael_mic_failure (err 0)
[ 1693.949221] 8812au: Unknown symbol cfg80211_ibss_joined (err 0)
[ 1693.949277] 8812au: Unknown symbol cfg80211_scan_done (err 0)
[ 1693.949293] 8812au: Unknown symbol cfg80211_roamed (err 0)
[ 1693.949307] 8812au: Unknown symbol cfg80211_put_bss (err 0)
[ 1693.949353] 8812au: Unknown symbol cfg80211_unlink_bss (err 0)
[ 1693.949378] 8812au: Unknown symbol cfg80211_connect_result (err 0)
[ 1693.949392] 8812au: Unknown symbol cfg80211_inform_bss_frame_data (err 0)
[ 1693.949415] 8812au: Unknown symbol cfg80211_new_sta (err 0)
[ 1693.949451] 8812au: Unknown symbol __cfg80211_alloc_reply_skb (err 0)
[ 1693.949469] 8812au: Unknown symbol cfg80211_rx_mgmt (err 0)
[ 1693.949486] 8812au: Unknown symbol ieee80211_frequency_to_channel (err 0)
[ 1693.949501] 8812au: Unknown symbol wiphy_apply_custom_regulatory (err 0)
[ 1693.949518] 8812au: Unknown symbol cfg80211_mgmt_tx_status (err 0)
[ 3436.387810] RTL871X: rtl8812au v4.3.8_12175.20140902
[ 3436.387911] usbcore: registered new interface driver rtl8812au
nick@ubuntu:~$ iwconfig
enp3s8    no wireless extensions.

lo        no wireless extensions.

enp0s29f7u6  no wireless extensions.
```

---

### Post by chili555 on 2016-10-15
> [ 3436.387810] RTL871X: rtl8812au v4.3.8_12175.20140902Looks like the incorrect driver is loaded. Let's blacklist it:```

sudo -i
echo "blacklist rtl8812au"  >>  /etc/modprobe.d/blacklist.conf
exit

```Reboot and show us:```
dmesg | grep 8812
iwconfig
```

---

### Post by hunterni on 2016-10-15
Here it is:

```
nick@ubuntu:~/Documents/wifi_adapter/rtl8812AU$ dmesg | grep 8812au
[  294.110639] 8812au: module verification failed: signature and/or required key missing - tainting kernel
[  294.123130] RTL871X: rtl8812au v4.3.8_12175.20140902
[  294.123239] usbcore: registered new interface driver rtl8812au
nick@ubuntu:~/Documents/wifi_adapter/rtl8812AU$ iwconfig
enp3s8    no wireless extensions.

lo        no wireless extensions.

enp0s29f7u6  no wireless extensions.

nick@ubuntu:~/Documents/wifi_adapter/rtl8812AU$ 
```

---

### Post by chili555 on 2016-10-15
> 8812au: module verification failed: signature and/or required key missing [http://askubuntu.com/questions/483283/module-verification-failed-signature-and-or-required-key-missing](http://askubuntu.com/questions/483283/module-verification-failed-signature-and-or-required-key-missing)

I'm still worried about what module is loaded. Please let us see:```
lsmod | grep 8812
```

---

### Post by hunterni on 2016-10-15
```
nick@ubuntu:~$ lsmod | grep 8812
8812au                790528  0
```

---

### Post by chili555 on 2016-10-15
Let's dig deeper:```
modinfo 8812au | grep 0811
```

---

### Post by hunterni on 2016-10-15
There was no result with that code

---

### Post by chili555 on 2016-10-15
You *STILL* have the wrong driver installed. We'll have to struggle a bit to remove it.```
cd  ~/Documents/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51
sudo make uninstall
```Reboot and check:```
dmesg | grep 8812
```If it shows nothing, then do:```
cd ~/Documents/wifi_adapter/rtl8812AU
make clean
make
sudo make install
sudo modprobe 8812au
dmesg | grep 8812 
```We hope you see:> [27600.727609] 8812au: loading out-of-tree module taints kernel.
[27600.728463] 8812au: module verification failed: signature and/or required key missing - tainting kernel
[27600.731628] RTL871X: module init start
[27600.731630] RTL871X: rtl8821au [COLOR="#FF0000"]v4.3.14[/COLOR]
[27600.731630] RTL871X: rtl8821au BT-Coex version = BTCOEX20150128-51
[27600.731678] usbcore: registered new interface driver rtl8821au
And we hope the wireless is working.

---

### Post by hunterni on 2016-10-15
So I wanted to show you everything in case I'm doing something wrong. Running 'make clean' and 'make' gave errors: 

```
nick@ubuntu:~/Documents/wifi_adapter/rtl8812AU$ make clean
cd hal/OUTSRC/ ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal/OUTSRC/ ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal/led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
cd hal ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd platform ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm: cannot remove '.tmp_versions/8812au.mod': Permission denied
Makefile:1597: recipe for target 'clean' failed
make: *** [clean] Error 1
nick@ubuntu:~/Documents/wifi_adapter/rtl8812AU$ make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/4.4.0-43-generic/build M=/home/nick/Documents/wifi_adapter/rtl8812AU  modules
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-43-generic'
rm: cannot remove '/home/nick/Documents/wifi_adapter/rtl8812AU/.tmp_versions/8812au.mod': Permission denied
Makefile:1390: recipe for target 'crmodverdir' failed
make[1]: *** [crmodverdir] Error 1
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-43-generic'
Makefile:1576: recipe for target 'modules' failed
make: *** [modules] Error 2
nick@ubuntu:~/Documents/wifi_adapter/rtl8812AU$ sudo make install
install -p -m 644 8812au.ko  /lib/modules/4.4.0-43-generic/kernel/drivers/net/wireless/
install: cannot stat '8812au.ko': No such file or directory
Makefile:1582: recipe for target 'install' failed
make: *** [install] Error 1
nick@ubuntu:~/Documents/wifi_adapter/rtl8812AU$ sudo modprobe 8812au
nick@ubuntu:~/Documents/wifi_adapter/rtl8812AU$ dmesg | grep 8812
[  266.779406] 8812au: module verification failed: signature and/or required key missing - tainting kernel
[  266.786530] RTL871X: rtl8812au v4.3.8_12175.20140902
[  266.786629] usbcore: registered new interface driver rtl8812au
nick@ubuntu:~/Documents/wifi_adapter/rtl8812AU$ 
```

---

### Post by chili555 on 2016-10-15
Please remove the incorrect driver first as per my instructions. It is still loaded and we need for it to be removed. Then reboot. 

Next, we see permission problems, so let's try to solve those with:```
cd ~/Documents/wifi_adapter/rtl8812AU
sudo make clean
sudo make
sudo make install
sudo modprobe 8812au
dmesg | grep 8812
```

---

### Post by hunterni on 2016-10-15
I removed the incorrect driver as you specified and your most recent code...

```
nick@ubuntu:~/Documents/wifi_adapter/rtl8812AU$ sudo modprobe 8812au
nick@ubuntu:~/Documents/wifi_adapter/rtl8812AU$ dmesg | grep 8812
[  356.011300] 8812au: module verification failed: signature and/or required key missing - tainting kernel
[  356.024190] RTL871X: rtl8812au v4.3.8_12175.20140902
[  356.024287] usbcore: registered new interface driver rtl8812au
nick@ubuntu:~/Documents/wifi_adapter/rtl8812AU$ 
```

---

### Post by chili555 on 2016-10-16
> RTL871X: rtl8812au [COLOR="#FF0000"]v4.3.8_12175.20140902[/COLOR]I am still suspicious that you have the incorrect driver. Let's compare to what I get when I compile the git version:> [  177.415028] 8812au: loading out-of-tree module taints kernel.
[  177.415637] 8812au: module verification failed: signature and/or required key missing - tainting kernel
[  177.418229] RTL871X: module init start
[  177.418230] RTL871X: rtl8821au [COLOR="#FF0000"]v4.3.14[/COLOR]
[  177.418231] RTL871X: rtl8821au BT-Coex version = BTCOEX20150128-51
[  177.418272] usbcore: registered new interface driver rtl8821au
Check to see if your version claims your device:```
modinfo 8812au | grep 0811
```The git version reports:```
alias:          usb:v[COLOR="#FF0000"]0BDA[/COLOR]p[COLOR="#FF0000"]0811[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
```So we know that your device is covered in the git version. Finally, check the version:```
modinfo 8812au | grep -i version
```The git version I compiled reports:```
version:       [COLOR="#FF0000"] v4.3.14[/COLOR]
srcversion:     AAD75FABBBEC53147DA66EB

```How about yours?

---

### Post by hunterni on 2016-10-16
This is what I got:

```
nick@ubuntu:~$ modinfo 8812au | grep 0811
nick@ubuntu:~$ 
nick@ubuntu:~$ 
nick@ubuntu:~$ modinfo 8812au | grep -i version
version:        v4.3.8_12175.20140902
srcversion:     5E9D12706FAF7E2BB4F284E
vermagic:       4.4.0-43-generic SMP mod_unload modversions 686 
parm:           rtw_chip_version:int
nick@ubuntu:~$ ^C
nick@ubuntu:~$ 
```

Should I try to reinstall the git version?

---

### Post by chili555 on 2016-10-16
> **hunterni said:**
> This is what I got:

```
nick@ubuntu:~$ modinfo 8812au | grep 0811
nick@ubuntu:~$ 
nick@ubuntu:~$ 
nick@ubuntu:~$ modinfo 8812au | grep -i version
version:        v4.3.8_12175.20140902
srcversion:     5E9D12706FAF7E2BB4F284E
vermagic:       4.4.0-43-generic SMP mod_unload modversions 686 
parm:           rtw_chip_version:int
nick@ubuntu:~$ ^C
nick@ubuntu:~$ 
```

Should I try to reinstall the git version?Uninstall the downloaded version; reboot; reinstall the git version and then post these again:```
dmesg | grep 8812
modinfo 8812au | grep -e 0811 -e version
```

---

### Post by hunterni on 2016-10-16
I uninstalled the old version as instructed in post #33 but I still got the same output when reinstalling with the git version:

```
nick@ubuntu:~/Documents/wifi_adapter/rtl8812AU$ dmesg | grep 8812
[  310.898302] 8812au: module verification failed: signature and/or required key missing - tainting kernel
[  310.904755] RTL871X: rtl8812au v4.3.8_12175.20140902
[  310.904854] usbcore: registered new interface driver rtl8812au
nick@ubuntu:~/Documents/wifi_adapter/rtl8812AU$ modinfo 8812au | grep -e 0811 -e version
version:        v4.3.8_12175.20140902
srcversion:     5E9D12706FAF7E2BB4F284E
vermagic:       4.4.0-43-generic SMP mod_unload modversions 686 
parm:           rtw_chip_version:int
nick@ubuntu:~/Documents/wifi_adapter/rtl8812AU$ 
```

I know you posted a link about this problem:
```
[  310.898302] 8812au: module verification failed: signature and/or required key missing - tainting kernel
```

Could that be the problem?

---

### Post by chili555 on 2016-10-16
Alright! Time to get out the sledgehammer and the plasma cutter. We are going to go step-by-step and I'd like you to show your work for each step. First:```
modinfo 8812au | grep filename
```

---

### Post by hunterni on 2016-10-16
You got it! Thank you so much... you probably can't tell how new I am to linux, huh? But seriously, even if this doesn't get resolved, I'm very grateful for all your help.
```
nick@ubuntu:~/Documents/wifi_adapter/rtl8812AU$ modinfo 8812au | grep filename
filename:       /lib/modules/4.4.0-43-generic/updates/dkms/8812au.ko
nick@ubuntu:~/Documents/wifi_adapter/rtl8812AU$ 
```

---

### Post by chili555 on 2016-10-16
Alrighty! Next:```
dkms status
history | grep dkms
```Thanks.

---

### Post by hunterni on 2016-10-16
```
nick@ubuntu:~/Documents/wifi_adapter/rtl8812AU$ dkms status
rtl8812au, 4.3.8.12175.20140902+dfsg, 4.4.0-43-generic, i686: installed
```

---

### Post by chili555 on 2016-10-16
```
sudo apt-get purge rtl8812au-dkms
```Even though the installation, way back a few pages, errored out, all kinds of changes were made in dkms making the uninstall process very tricky.

Reboot and show us:```
lsmod | grep 8812
dmesg | grep 8812
```

---

### Post by hunterni on 2016-10-16
```
nick@ubuntu:~$ lsmod | grep 8812
8812au               1470464  0
cfg80211              499712  1 8812au
nick@ubuntu:~$ dmesg | grep 8812
[   21.811439] 8812au: module verification failed: signature and/or required key missing - tainting kernel
```

---

### Post by chili555 on 2016-10-16
Looking a bit better. Now, how about:```
modinfo 8812au | head -6
iwconfig
```We hope we see:```
version:        v[COLOR="#FF0000"]4.3.14[/COLOR]
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     AAD75FABBBEC53147DA66EB

```

---

### Post by hunterni on 2016-10-16
Well look at that!
```
nick@ubuntu:~$ modinfo 8812au | head -6
filename:       /lib/modules/4.4.0-43-generic/kernel/drivers/net/wireless/8812au.ko
version:        v4.3.14
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     AAD75FABBBEC53147DA66EB


```

---

### Post by chili555 on 2016-10-16
Now, let's see:```
modinfo 8812au | grep 0811
iwconfig
```

---

### Post by hunterni on 2016-10-16
```
nick@ubuntu:~$ modinfo | grep 0811
modinfo: ERROR: missing module or filename.
nick@ubuntu:~$ iwconfig
wlxe84e063c144e  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

enp3s8    no wireless extensions.

lo        no wireless extensions.

enp0s29f7u6  no wireless extensions.

nick@ubuntu:~$ 


```

---

### Post by chili555 on 2016-10-16
> nick@ubuntu:~$ modinfo | grep 0811It is actually:```
 modinfo 8812au | grep 0811
```However, your iwconfig looks like you have a wireless interface that's ready to connect. Does it scan?```
sudo iwlist scan
```If it scans, you can probably click the Network Manager icon, see your network and connect. Please try.

What does this tell us?```
dmesg | grep wlxe
```

---

### Post by hunterni on 2016-10-16
Oh, sorry here it is. And it says it doesn't support scanning but in my network manager it's able to show available wifi networks -- including the one that is from my router.

```
nick@ubuntu:~$ modinfo 8812au | grep 0811
alias:          usb:v0BDAp0811d*dc*dsc*dp*ic*isc*ip*in*
nick@ubuntu:~$ sudo iwlist scan
[sudo] password for nick: 
wlxe84e063c144e  Scan completed :
          Cell 01 - Address: FA:8F:CA:68:17:E8
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:72 Mb/s
                    Quality=100/100  Signal level=84/100  
                    Extra:fm=0001
          Cell 02 - Address: EC:AA:A0:A7:42:8A
                    ESSID:"xfinitywifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:144 Mb/s
                    Quality=100/100  Signal level=89/100  
                    Extra:fm=0003
          Cell 03 - Address: EC:AA:A0:A7:42:88
                    ESSID:"HOME-7D1C-2.4"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD8D0050F204104A0001101044000102103B00010310470010D1BD042EA33E5177A420FAAB624F497E10210013436973636F2053797374656D732C20496E632E10230007445043333934311024000744504333393431104200093030303030303030311054000800060050F20400011011000744504333393431100800020000103C0001011049000600372A000120
                    Quality=100/100  Signal level=90/100  
                    Extra:fm=0003
          Cell 04 - Address: 40:5D:82:E3:AF:9B
                    ESSID:"Lothlorien"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD800050F204104A0001101044000102103B000103104700109C3B40F8827AD8D5C7FB1885DE0C0C16102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F2040001101100094E6574676561724150100800022008103C0001031049000600372A000120
                    Quality=36/100  Signal level=70/100  
                    Extra:fm=0003
          Cell 05 - Address: 6E:8F:E0:94:35:DA
                    ESSID:"xfinitywifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:144 Mb/s
                    Quality=0/100  Signal level=48/100  
                    Extra:fm=0001
          Cell 06 - Address: 7E:8F:E0:94:35:DA
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=20/100  Signal level=47/100  
                    Extra:fm=0001
          Cell 07 - Address: 5E:8F:E0:94:35:DA
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=20/100  Signal level=47/100  
                    Extra:fm=0001
          Cell 08 - Address: 5C:8F:E0:94:35:DA
                    ESSID:"celinespimentel24"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD1D0050F204104A0001101044000102103C0001021049000600372A000120
                    Quality=20/100  Signal level=46/100  
                    Extra:fm=0001
          Cell 09 - Address: 74:85:2A:DF:C3:8A
                    ESSID:"xfinitywifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:144 Mb/s
                    Quality=20/100  Signal level=50/100  
                    Extra:fm=0003
          Cell 10 - Address: A0:63:91:1B:D9:14
                    ESSID:"NETGEAR53"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:150 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DDAC0050F204104A0001101044000102103B000103104700103883309230921883957EA063911BD9141021000D4E4554474541522C20496E632E1023001D4E45544745415220576972656C6573732041636365737320506F696E74102400074E4554474541521042000831323334353637381054000800060050F204000110110017574E523130303076342028576972656C6573732041502910080002210C103C0001011049000600372A000120
                    Quality=72/100  Signal level=63/100  
                    Extra:fm=0003
          Cell 11 - Address: 74:85:2A:DF:C3:88
                    ESSID:"HOME-F576-2.4"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD8D0050F204104A0001101044000102103B00010310470010E6423B70F0995F5998E716457B6E0FDC10210013436973636F2053797374656D732C20496E632E10230007445043333934311024000744504333393431104200093030303030303030311054000800060050F20400011011000744504333393431100800020000103C0001011049000600372A000120
                    Quality=100/100  Signal level=48/100  
                    Extra:fm=0003
          Cell 12 - Address: 74:85:2A:DF:C3:89
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=56/100  
                    Extra:fm=0001
          Cell 13 - Address: 62:45:B0:F1:DE:23
                    ESSID:""
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Frequency:5.22 GHz (Channel 44)
                    Encryption key:on
                    Bit Rates:0 kb/s
                    Quality=95/100  Signal level=72/100  
                    Extra:fm=0001
          Cell 14 - Address: A0:63:91:EC:39:00
                    ESSID:"NETGEAR87-5G"
                    Protocol:IEEE 802.11an
                    Mode:Master
                    Frequency:5.765 GHz
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD800050F204104A0001101044000102103B000103104700109C3B40F8827AD8D5C7FB1885DE0C0C16102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F2040001101100094E6574676561724150100800022008103C0001031049000600372A000120
                    Quality=46/100  Signal level=57/100  
                    Extra:fm=0003
          Cell 15 - Address: EC:AA:A0:A7:42:90
                    ESSID:"HOME-7D1C-5"
                    Protocol:IEEE 802.11AC
                    Mode:Master
                    Frequency:5.785 GHz
                    Encryption key:on
                    Bit Rates:867 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD8D0050F204104A0001101044000102103B00010310470010D1BD042EA33E5177A420FAAB624F497E10210013436973636F2053797374656D732C20496E632E10230007445043333934311024000744504333393431104200093030303030303030311054000800060050F20400011011000744504333393431100800020000103C0001011049000600372A000120
                    Quality=74/100  Signal level=84/100  
                    Extra:fm=0003
          Cell 16 - Address: EC:AA:A0:A7:42:91
                    ESSID:"xfinitywifi"
                    Protocol:IEEE 802.11AC
                    Mode:Master
                    Frequency:5.785 GHz
                    Encryption key:off
                    Bit Rates:867 Mb/s
                    Quality=82/100  Signal level=84/100  
                    Extra:fm=0003

enp3s8    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

enp0s29f7u6  Interface doesn't support scanning.

nick@ubuntu:~$ dmesg | grep wlxe
[   21.980631] rtl8821au 1-5:1.0 wlxe84e063c144e: renamed from wlan0
[   33.426641] IPv6: ADDRCONF(NETDEV_UP): wlxe84e063c144e: link is not ready
[   33.834143] IPv6: ADDRCONF(NETDEV_UP): wlxe84e063c144e: link is not ready
[   37.677357] IPv6: ADDRCONF(NETDEV_UP): wlxe84e063c144e: link is not ready
```

---

### Post by hunterni on 2016-10-16
Hey! It's working! I'm currently connected to my wifi! You are amazing, chili555. Thank you so much!!

---

### Post by chili555 on 2016-10-16
> **hunterni said:**
> Hey! It's working! I'm currently connected to my wifi! You are amazing, chili555. Thank you so much!!Awesome! Glad it's working.

You have compiled the driver for your current running kernel only. When Update Manager installs a later one, also known as linux-image, re-compile:

```
cd  ~/Documents/wifi_adapter/rtl8812AU
make clean
make
sudo make install
sudo modprobe 8812au

```Please retain the file and these instructions for that time.

Please use thread tools to mark Solved.

---

