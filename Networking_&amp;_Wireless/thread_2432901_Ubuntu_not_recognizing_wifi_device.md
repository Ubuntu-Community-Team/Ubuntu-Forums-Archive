---
title: "Ubuntu not recognizing wifi device"
date: 2019-12-10
forum: Networking &amp; Wireless
---

### Post by wontonkrakker on 2019-12-10
Hello,

Ive been working on this issue for a few days now, and I cant seem to figure it out.  Basically, I just got a brand new laptop and my fresh install of Ubuntu 18.04 is not recognizing my wifi hardware.  I can successfully connect using an external USB device, but when I unplug it, it goes back to not detecting the original hardware.  

Here's some info.  Hopefully this is helpful.  If not, just let me know what you need.

laptop: Lenovo Yoga C740-15IML
wireless: Intel Wireless AC 9560

After some research, I saw some common requests for command output, so here it is:

lspci -nnk | grep 0280 -A3
```

00:14.3 Network controller [0280]: Intel Corporation Device [8086:02f0]
    Subsystem: Intel Corporation Device [8086:0034]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi, wl

```

dmesg | grep -e wl -e iwl

```

[    3.635263] iwlwifi 0000:00:14.3: loaded firmware version 43.95eb4e97.0 op_mode iwlmvm
[    3.663763] iwlwifi 0000:00:14.3: Detected Intel(R) Dual Band Wireless AC 9560, REV=0x354
[    4.063100] rt2800usb 1-1:1.0 wlx00259cf01f05: renamed from wlan0
[    8.877441] iwlwifi 0000:00:14.3: Failed to load firmware chunk!
[    8.877447] iwlwifi 0000:00:14.3: iwlwifi transaction failed, dumping registers
[    8.877451] iwlwifi 0000:00:14.3: iwlwifi device config registers:
[    8.877489] iwlwifi 0000:00:14.3: 00000000: 02f08086 00100406 02800000 00800010 b1318004 00000000 00000000 00000000
[    8.877494] iwlwifi 0000:00:14.3: 00000020: 00000000 00000000 00000000 00348086 00000000 000000c8 00000000 000001ff
[    8.877497] iwlwifi 0000:00:14.3: iwlwifi device memory mapped registers:
[    8.877528] iwlwifi 0000:00:14.3: 00000000: 18489004 00000040 00000000 00000000 00000000 00000000 00000000 00000000
[    8.877532] iwlwifi 0000:00:14.3: 00000020: 00000011 0c040005 00000351 d55555d5 d55555d5 d55555d5 80008040 001f0040
[    8.877551] iwlwifi 0000:00:14.3: Could not load the [0] uCode section
[    8.877574] iwlwifi 0000:00:14.3: Failed to start INIT ucode: -110
[    8.877578] iwlwifi 0000:00:14.3: Collecting data: trigger 15 fired.
[    9.102645] iwlwifi 0000:00:14.3: Failing on timeout while stopping DMA channel 8 [0x0bad1122]
[    9.114896] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -110
[   11.640900] wlx00259cf01f05: authenticate with 58:97:1e:56:b5:d7
[   11.655449] wlx00259cf01f05: send auth to 58:97:1e:56:b5:d7 (try 1/3)
[   11.655971] wlx00259cf01f05: authenticated
[   11.657538] wlx00259cf01f05: associate with 58:97:1e:56:b5:d7 (try 1/3)
[   11.660374] wlx00259cf01f05: RX AssocResp from 58:97:1e:56:b5:d7 (capab=0x101 status=0 aid=55)
[   11.664671] wlx00259cf01f05: associated
[   11.664900] IPv6: ADDRCONF(NETDEV_CHANGE): wlx00259cf01f05: link becomes ready
[   11.769494] wlx00259cf01f05: Limiting TX power to 14 dBm as advertised by 58:97:1e:56:b5:d7
[   49.064443] wlx00259cf01f05: deauthenticating from 58:97:1e:56:b5:d7 by local choice (Reason: 3=DEAUTH_LEAVING)

```

uname -r
```

5.0.0-37-generic

```


Please help!

Thanks

---

### Post by wontonkrakker on 2019-12-10
Also, I should mention that I have done the following:

Reinstalled Ubuntu to ensure the checkbox is checked to install 3rd party drivers for wifi
reinstalled and restarted the network manager 
Downloaded the driver for the 9560 and manually copied it into /lib/firmware - [iwlwifi-9000-pu-b0-jf-b0-34.618819.0.tgz]("https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-9000-pu-b0-jf-b0-34.618819.0.tgz") for kernel 4.14+

---

### Post by jeremy31 on 2019-12-10
Try ```
sudo add-apt-repository ppa:canonical-hwe-team/backport-iwlwifi
sudo apt-get update
sudo apt-get install backport-iwlwifi-dkms
```
Reboot, if it doesn't work do ```
sudo apt-get remove backport-iwlwifi-dkms
```
Might want to make a screenshot of this post as if the backport-iwlwifi-dkms doesn't work, you will not be able to use your USB device either

---

### Post by praseodym on 2019-12-11
Do also uninstall
```

sudo apt-get remove --purge bcmwl-kernel-source broadcom-sta-dkms
```

---

### Post by wontonkrakker on 2019-12-11
@jeremy31

Thanks so much!  This worked.

If you dont mind me asking, what does the command:

sudo add-apt-repository ppa:canonical-hwe-team/backport-iwlwifi

do?

Im still relatively newish to Linux, so Im still trying to learn.

---

### Post by jeremy31 on 2019-12-11
I adds another repository to your software sources so you can download/update programs not in the regular Ubuntu repositories
Just like github sources, PPA's are not always trustworthy, but after seeing familiar names in [https://launchpad.net/~canonical-hwe-team](https://launchpad.net/~canonical-hwe-team) I think it can be trusted

---

### Post by ninjds on 2020-04-01
Hi @jeremy31,
First, thank you for helping us.
I have the exact same problem as the OP. I tried your solution but got no result at all.

I am on a Dell Vostro, i5-10 with Ubuntu 19.10. My wifi is Intel. Funny thing: **it's pefectly working as long as I don't update Ubuntu**. To be more specific, it works when these to conditions are met :
1. During installation, no internet connection is set up (so, obviously, no update is downladed)
2. After installation, I must not install any update, else, after the reboot my Wifi adapter is dead.

Same thing on Ubuntu 18.04.4, by the way.

Any idea? I struggle with this, I already installed Ubuntu 11 times to try every possible setting combination (internet: none/USB/Wifi ; install third party drivers: yes/no ; install update during setup: yes/no ; secure boot: yes/no ; LVM : yes/no; disk encryption: yes/no)

Thank you :)

---

