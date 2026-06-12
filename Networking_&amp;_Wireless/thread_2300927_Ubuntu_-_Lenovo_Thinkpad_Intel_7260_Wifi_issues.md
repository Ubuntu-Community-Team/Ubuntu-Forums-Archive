---
title: "Ubuntu - Lenovo Thinkpad Intel 7260 Wifi issues"
date: 2015-10-29
forum: Networking &amp; Wireless
---

### Post by shahzaibmuneeb on 2015-10-29
Hey!

So I have setup Ubuntu 14.04 as a dualboot on my new Thinkpad which happens to have the notorious Intel 7260 wireless card/chip in it. Now I'm facing very similar to issues to the ones found on the forum already with this particular model and still cannot fix this issue. The wireless disconnects frequently and once in a blue moon I get full speed internet access (very rare) and if I restart/reboot my laptop the internet connection is lost again. 

I have ran the wireless script and attached it to this post.

I also have logged the dmesg script and the dmesg | grep iwl, which are also attached!

I am loving running Ubuntu and this major hiccup is is ruining it! :(

I would appreciate any help I can get! 

[ATTACH]265233[/ATTACH]
[ATTACH]265234[/ATTACH]

---

### Post by chili555 on 2015-10-29
The driver and the firmware that it calls has steadily improved since Ubuntu 14.04. Although you are running a 3.19.0-xx kernel, it may, at some later point, be desirable to upgrade the kernel to 4.2.0-xx. We can install the kernel alone or simply upgrade to Ubuntu 15.10.

You may have already checked some of these things, but please re-check them all.

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

If these changes do not help, please try:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and tell us if there is some improvement. If not, please re-run the wireless script and post it. I am also interested in:```
dmesg | grep firmware
```

---

### Post by shahzaibmuneeb on 2015-10-29
Hey thanks for your response.

I am using 14.04 specifically as it is the same as my deployment server so keeping my development machine the same is beneficial.

I did the things you said and there doesn't seem to be any improvement.

Here is the dmesg | grep firmware

```

[    6.580902] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   11.694248] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.1.2d.d.bseq
[   11.739932] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   11.942658] iwlwifi 0000:03:00.0: loaded firmware version 25.17.12.0 op_mode iwlmvm

```


And here is the script info:

[ATTACH]265246[/ATTACH]

Thanks!

---

### Post by shahzaibmuneeb on 2015-10-29
Maybe there has been some improvement.

Before I couldn't always connect to my router, now it connects every time, but still there is no solid internet connection (if any), regardless, a step in the right direction?

Thanks!

[B]EDIT:

[/B]dmesg | grep firmware

now returns nothing.

---

### Post by chili555 on 2015-10-29
The Intel 7260 is an enigma. The more I study it, the *less* I understand it! The driver version you have says:```
filename:       /lib/modules/3.19.0-31-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
f<snip>
firmware:       iwlwifi-7260-[COLOR="#FF0000"]10[/COLOR].ucode
<snip>
```And yet, the -12 firmware actually loads!```
iwlwifi 0000:03:00.0: loaded firmware version 25.17.[COLOR="#FF0000"]12[/COLOR].0 op_mode iwlmvm
```Later versions of the driver probably use the later -13 and -15 firmware: [https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi)

Let's build the 4.2 version of the driver, download the later firmware and see if it helps. First, download these files to your desktop: [https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7260-ucode-25.30.13.0.tgz](https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7260-ucode-25.30.13.0.tgz) Also: [https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7260-ucode-15.227938.0.tgz](https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7260-ucode-15.227938.0.tgz) Right-click each and select 'Extract Here.' Now, in a terminal:```
cd ~/Desktp/iwlwifi-7260-ucode-25.30.13.0
sudo cp iwlwifi*  /lib/firmware
cd ~/Desktop/iwlwifi-7260-ucode-15.227938.0
sudo cp iwlwifi*  /lib/firmware
```Now, let's build the later driver:```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential
cd ~/Desktop
wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.2-rc1/backports-4.2-rc1-1.tar.gz
tar -zxvf backports-4.2-rc1-1.tar.gz
cd backports-4.2-rc1-1
make defconfig-iwlwifi
make
sudo make install
```Reboot.

Please post:```
dmesg | grep -e firmware -e iwl
```

---

### Post by shahzaibmuneeb on 2015-10-29
Enigma is the right word.

I'm not sure if this was meant to improve something straight away or not, if it was then it didn't, same issue, can connect WIFI but no internet.

**dmesg | grep -e firm**[B]ware -e iwl
[/B][ATTACH]265250[/ATTACH][B]

and script data:[/B]
[ATTACH]265251[/ATTACH]

---

### Post by shahzaibmuneeb on 2015-10-29
Also, if it means anything. I connected my mobile phone (Samsung S5)'s mobile hotspot with my laptop wirelessly and the internet worked flawlessly. Is this representative of some sort of incompatibility with my router?

I will also try tomorrow at my office to see if it works with the routers there.

Would still love to be able to use it at home with WIFI rather than having a 10m ethernet cable around the house!
[B]
EDIT:
[/B]
uname -r returns:

3.19.0-31-generic

isn't this meant to say 4.2 (the new kernel we built?)

**EDIT 2:**

Internet works flawlessy at work, why does it not work at home :(

---

### Post by chili555 on 2015-10-30
> uname -r returns:

3.19.0-31-generic

isn't this meant to say 4.2 (the new kernel we built?)We built only the iwlwifi driver suite. It reports correctly:> [iwlwifi]
filename:       /lib/modules/3.19.0-31-generic/updates/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        [COLOR="#FF0000"]backported from Linux (v4.2-rc1[/COLOR]-0-gd770e55) using backports v4.2-rc1-1-0-g83a2518
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>  > Would still love to be able to use it at home with WIFI rather than having a 10m ethernet cable around the house!I noticed that in all your readings, both the wireless and ethernet are connected. Please let's troubleshoot only the wireless. Are the symptoms the same?> Internet works flawlessy at work, why does it not work at homeWhat does this say about the network at work?```
sudo iwlist wlan0 scan
```For comparison, your home network says:> Cell 02 - Address: <MAC 'NTG IQBAL' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"NTG IQBAL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000016ebcd1ab
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/[COLOR="#FF0000"]WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK[/COLOR]I am just a bit suspicious when I see a space in the name of the SSID. Would you please try changing it to: NTG_IQBAL or NTG-IQBAL or some such to see if it makes any difference. My fears could be brought about by the nightmares the Intel 7260 gives me!

---

### Post by shahzaibmuneeb on 2015-10-30
Cool. When I get home I will alter the SSID, perhaps the space does cause an issue. Is this something you've seen before?

Also I disconnect my ethernet cable when I did the troubleshooting tasks.

Here is my work wlan0 scan:

[ATTACH]265269[/ATTACH]

---

### Post by shahzaibmuneeb on 2015-10-30
Hey! The SSID change seems to work? I'm not sure if it worked or something else changed because I refuse to believe that something as silly as that was the root of this? I've also activated another router in my house which works out the box... Thanks for your help! You have made me a very happy linux user. If you want any of my script data for further analysis of a working connection (For your own knowledge as you seem to enjoy this), feel free to ask and I'll provide you with this.

Thanks.

---

