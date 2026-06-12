---
title: "Killer WiFi adapter is not working - iwlwifi appears to crash"
date: 2021-05-10
forum: Networking &amp; Wireless
---

### Post by apatters on 2021-05-10
Hi,

My wifi adapter is not working after a recent fresh install of Xubuntu Hirsute on an Acer Swift 3. Prior to this fresh install I was running an LTS on which the adapter was working, but broke after a kernel upgrade from 5.4.x to something more recent.

The adapter type is "Killer Wi-Fi 6 AX1650i 160MHz Wireless Network Adapter (201NGW)" according to lshw. This is an Intel-based adapter for which the driver is iwlwifi.

Here's wireless-info.txt: [https://paste.ubuntu.com/p/B3CQh9g9bX/](https://paste.ubuntu.com/p/B3CQh9g9bX/)

You may observe that iwlwifi.conf has only one line in it... I accidentally nuked this file while testing possible fixes so if anyone can help me restore it that would be appreciated. However the adapter had stopped working *before* I changed this file.

You may also observe that the r8188eu driver is running on the system, this is because I have a TP-Link Wireless USB Adapter TL-WN723N plugged into the system. This adapter seems to have its own problems (intermittent dropouts, won't respect the regulatory domain which is set to TH in /etc/default/crda) but I guess we need to take this one problem at a time.

Also, here is an excerpt from dmesg of iwlwifi events. It looks like iwlwifi crashes on boot and dumps some info about the crash into dmesg: [https://paste.ubuntu.com/p/qWgcZj6RJK/](https://paste.ubuntu.com/p/qWgcZj6RJK/)

Any assistance with this would be greatly appreciated. Interpreting iwlwifi crash logs is over my head. I have a third wifi adapter on hand and if that one doesn't work either I don't know how I can continue using Ubuntu as my daily driver.

Thank you!

---

### Post by chili555 on 2021-05-10
Here are some thoughts that may or may not solve the issue, but which may lead us closer to the solution.

First, here is my iwlwifi.conf:

```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

```I suggest that you add this in place of the wording that you added which, I suspect, will be ineffective. 

Next, we see:

```
Cell 01 - Address: <MAC 'unimatrixw' [AC1]>
                    ESSID:"unimatrixw"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
```I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

I also suggest that you disable power saving. From the terminal:

```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```Next, both the USB wireless driver r8188eu and the internal iwlwifi us the helper modules cfg80211 and mac80211 and so having them both loaded probably interfer. Please remove the USB, reboot and run:

```
sudo dmesg | grep iwl
```Do you still get this message?

> iwlwifi 0000:00:14.3: Failed to run INIT ucode: -110There is no need to capture the whole output; just tell us if the dreaded message appears.

Once we see your report, we'll proceed.

---

### Post by apatters on 2021-05-22
Hi, the issue spontaneously resolved itself a few days after I posted,  so I stopped investigating it for a few days, went back to using only  the internal Killer WiFi device, and kept the other device unplugged.

Then this morning the issue spontaneously un-resolved. The Killer WiFI device has stopped working again.

I  followed all of your steps except for changing the default channels on  the router and we are still getting `[   12.032274] iwlwifi  0000:00:14.3: Failed to run INIT ucode: -110` in dmesg. I restarted both  the router and the computer after making the settings changes.

1. Replaced iwlwifi.conf with yours
2. Changed router "Security Setting" to WPA2-PSK and "Encryption Mode" to AES
3. Channel width was already set to 20MHz in the 2.4 GHz band 
4. The router is already set to use 802.11b/g/n in the 2.4 GHz band and 802.11a/n/ac in the 5 GHz band
5. Channel was set to auto for both bands and I did not change that
6.  I noticed the SSID was set to unimatrixw for both bands which struck me  as odd because I'm pretty sure it was set to unimatrixw_5G by the tech  when he first set things up a year back

We still get the message of death and no connectivity.

Your help is greatly appreciated.

---

### Post by chili555 on 2021-05-22
> 5. Channel was set to auto for both bands and I did not change thatWhy not? I think it's very important. [https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection](https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection)

I notice that there is a newer firmware version available. Let's try it.
```
wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/snapshot/linux-firmware-20210511.tar.gz
tar xvzf linux-firmware*
cd linux-firmware-20210511
sudo cp iwlwifi-Qu-c0-hr-b0-62.ucode /usr/lib/firmware
```

Reboot and paste:

```
sudo dmesg | grep iwl
```

We want to see if the driver claims the newer firmware version and if the dreaded message of death is quashed.

---

