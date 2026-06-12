---
title: "Intel Corporation Wireless 3160 keeps dropping connection ubuntu 14.04"
date: 2016-02-06
forum: Networking &amp; Wireless
---

### Post by angelo17 on 2016-02-06
My wireless connection keeps dropping connection whenever I use it. I'll have to uncheck enable wifi then recheck to get my internet working again. Also whenever my computer falls asleep I'll have to do the same thing to get my wifi working. Is there a solution to this problem? Here's the tar file from my wireless info script. I'm also using a Toshiba Satellite s55t if that helps at all. Thanks guys!

---

### Post by chili555 on 2016-02-06
I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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

Reboot and tell us if connectivity has improved. I actually suspect that TKIP and CRDA are 90% of the problem.

---

### Post by Vladlenin5000 on 2016-02-06
Hi and welcome.

The first thing you should do is to set your router to WPA2 with AES only.
Mixed mode WPA/WPA2 is known to cause issues with some adapters in Linux and TKIP likewise. On top of that TKIP is bad and was intended as a temporary solution. According to [this]("https://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol"), > TKIP is no longer considered secure and was deprecated in the 2012 revision of the 802.11 standard.


EDIT: Ninja'd by The Master.

---

### Post by angelo17 on 2016-02-06
Ok I disabled TKIP and enabled WPA2-AES and set my country code accordingly. If that doesn't work I'll try the other changes that were recommended by [chili555]("http://ubuntuforums.org/member.php?u=35909")[COLOR=#000000] . I'll post back in a few days and report on performance.[/COLOR]

---

### Post by chili555 on 2016-02-06
> **angelo17 said:**
> Ok I disabled TKIP and enabled WPA2-AES and set my country code accordingly. If that doesn't work I'll try the other changes that were recommended by [chili555]("http://ubuntuforums.org/member.php?u=35909")[COLOR=#000000] . I'll post back in a few days and report on performance.[/COLOR]We await your good report!

---

### Post by angelo17 on 2016-02-10
My performance has improved, but I still lose my signal and have to disable and enable wifi. The only thing I haven't tried is setting my channel width to 20 MHz. I'm not sure how to do that.

---

### Post by Vladlenin5000 on 2016-02-10
If available, that's also a setting at your router.

---

### Post by Hadaka on 2016-02-10
Hi, please post the output of..
```
iwconfig wlan0 | egrep -i 'mode|signal'
grep '' /sys/module/iwlwifi*/parameters/*
iw reg get
cat /etc/default/crda | grep "REGDOMAIN="
```
thanks

---

### Post by angelo17 on 2016-02-11
Here's the output

```
angelo@angelo:~$ iwconfig wlan0 | egrep -i 'mode|signal'
          Mode:Managed  Frequency:2.412 GHz  Access Point: CC:03:FA:DE:76:E2   
          Link Quality=51/70  Signal level=-59 dBm  
angelo@angelo:~$ grep '' /sys/module/b43*/parameters/*
grep: /sys/module/b43*/parameters/*: No such file or directory
angelo@angelo:~$ iw reg get
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)
angelo@angelo:~$ cat /etc/default/crda | grep "REGDOMAIN="
REGDOMAIN=US

```

---

### Post by Hadaka on 2016-02-12
Hi, from a wired connection please open a terminal then copy and paste.
```
sudo modprobe -rf iwlwifi
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
sudo modprobe -v iwlwifi
```
then please post the output of..
```
grep '' /sys/module/iwlwifi*/parameters/*
```
thanks.

---

### Post by angelo17 on 2016-02-12
Here it is

```
/sys/module/iwlwifi/parameters/11n_disable:8
/sys/module/iwlwifi/parameters/amsdu_size_8K:0
/sys/module/iwlwifi/parameters/antenna_coupling:0
/sys/module/iwlwifi/parameters/bt_coex_active:Y
/sys/module/iwlwifi/parameters/fw_monitor:N
/sys/module/iwlwifi/parameters/fw_restart:Y
/sys/module/iwlwifi/parameters/led_mode:0
/sys/module/iwlwifi/parameters/nvm_file:(null)
/sys/module/iwlwifi/parameters/power_level:0
/sys/module/iwlwifi/parameters/power_save:N
/sys/module/iwlwifi/parameters/swcrypto:0
/sys/module/iwlwifi/parameters/uapsd_disable:Y
/sys/module/iwlwifi/parameters/wd_disable:1

```

---

### Post by Hadaka on 2016-02-12
Thanks, the last command that might have helped was..
```
#echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
which you did and it is set, are you seeing an improvement in the disconnects ?
thanks.

---

### Post by angelo17 on 2016-02-12
So far it seems  better, but it's too early to tell. What did exactly did you do?

---

### Post by Hadaka on 2016-02-12
Hi setting this value:
echo "options iwlwifi 11n_disable=8"

helps with the N speed to allow a better
connection. Hopefully you will see fewer disconnects
keep us posted.
thanks.

---

### Post by Hadaka on 2016-02-14
Hi, If your connection is still stable please mark this thread solved
by logging back in, going to your first post of the thread and clicking
TOOLS then choose SOLVED
Thanks.

---

### Post by angelo17 on 2016-02-14
I'm going to have to say this is unsolved. There to appear to be fewer disconnects, but I still am getting disconnected often.

---

### Post by Hadaka on 2016-02-14
ok, please post another wireless info report so
we can see what the possible cause is.
thanks.

---

### Post by angelo17 on 2016-02-14
Here it is.

---

### Post by chili555 on 2016-02-15
I suggest we install a later driver and firmware for your device. Please download this file to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.3/backports-4.3-1.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.3/backports-4.3-1.tar.gz) Right-click it and select 'Extract Here.' Now, in the terminal:

```
cd ~/Desktop/backports-4.3.1
make defconfig-iwlwifi
make
sudo make install
```

You will have built the driver for your current kernel version only. When Update Manager installs a later kernel version, also known as linux-image, after the requested reboot, re-compile:

```
cd ~/Desktop/backports-4.3.1
make clean
make defconfig-iwlwifi
make
sudo make install
```

Please retain the files and these instructions for that time.

This device also requires firmware. Please download this package to your desktop: [https://github.com/OpenELEC/iwlwifi-firmware/archive/master.zip](https://github.com/OpenELEC/iwlwifi-firmware/archive/master.zip) Right-click it and select 'Extract Here.' Now, back to the terminal:

```
cd ~/Desktop/iwlwifi-firmware-master/firmware
sudo cp iwlwifi-3160*  /lib/firmware

```
Reboot and your wireless should be working much better.

---

### Post by angelo17 on 2016-02-15
Ok I just did what you said chili555. I'll let you know how things go!

---

### Post by angelo17 on 2016-02-18
My internet connection has been stable ever since I updated drivers and firmware. I'm going to go ahead and say this is solved. I appreciate the help!

---

