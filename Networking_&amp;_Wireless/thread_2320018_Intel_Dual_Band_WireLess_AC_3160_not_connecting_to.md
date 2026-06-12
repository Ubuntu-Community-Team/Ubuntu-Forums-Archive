---
title: "Intel Dual Band WireLess AC 3160 not connecting to wifi : Ubuntu 14.04"
date: 2016-04-09
forum: Networking &amp; Wireless
---

### Post by Siyanat on 2016-04-09
Hi Guys ,

My dual boot hp pavillion laptop is not connecting to my wifi router when running ubuntu 14.04. The same is working in windows 10.
I am currently submitting my details using a wifi adapter.
Kindly help.



[ATTACH]268266[/ATTACH]

---

### Post by chili555 on 2016-04-10
> Cell 03 - Address: <MAC 'atom' [AC2]>
                    ESSID:"atom"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSKMany Linux wireless drivers do not work well with TKIP or other arrangements where the router is in some Auto mode and switches back and forth between two or more different settings. Mrs. Chili doesn't like it when I switch back and forth between speaking English and python!

I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get

```
If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

   ```
 gksudo gedit /etc/default/crda
```

Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:

    ```
REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

If these changes do not help, please try:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Please detach the USB wireless, reboot and let us hear your report.

---

### Post by Siyanat on 2016-04-16
Thank you for your reply. In router I have lucked out as there is no WPA2-AES only mixed WPA /WPA 2 (it used to work with this  router until suddenly it stopped)
I have added my country code and also checked my wireless settings it is 20 Mhz b/g/n mixed. I also did the echo command at the end and rebooted. I have attached the report after reboot and removing the usb wireless . My wireless info and wifi settings attached. [ATTACH]268413[/ATTACH] [ATTACH=CONFIG]268415[/ATTACH]

---

### Post by chili555 on 2016-04-16
May I also see:```
dmesg | grep iwl
ls /lib/firmware | grep 3160
```I am interested in what firmware is loading and what you have available.

For reference, I have:```
$ ls /lib/firmware | grep 3160
iwlwifi-3160-10.ucode
iwlwifi-3160-12.ucode
iwlwifi-3160-13.ucode
iwlwifi-3160-16.ucode
iwlwifi-3160-7.ucode
iwlwifi-3160-8.ucode
iwlwifi-3160-9.ucode

```If your driver is loading, for example, the -10 firmware, we might try installing -12, -13 and -16 to see if it helps. The driver usually starts looking for the newest and steps down until it finds a suitable file. 

It's sort of like a friend of mine and wives!

---

