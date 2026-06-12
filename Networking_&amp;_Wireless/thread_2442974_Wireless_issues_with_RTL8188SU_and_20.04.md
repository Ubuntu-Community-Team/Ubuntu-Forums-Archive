---
title: "Wireless issues with RTL8188SU and 20.04"
date: 2020-05-09
forum: Networking &amp; Wireless
---

### Post by tdn19 on 2020-05-09
Hi, absolute Linux noob here.
I've been having big issues with wireless networking in Ubuntu 20.04, where i can't connect to the closest SSID, and the connection with the other SSID is extremely unstable and painfully slow when compared against Windows.

This is what i get when running the networking script: [https://pastebin.com/WReTQv6A](https://pastebin.com/WReTQv6A)
Thank you in advance.

---

### Post by chili555 on 2020-05-09
We see a few things in your paste that we recommend that you tweak.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

Any improvement?

---

### Post by tdn19 on 2020-05-10
Hi! First of all, thanks for the help.
After making the changes you suggested, i can now connect to the closest SSID, but internet connection is still super slow and super unstable.

---

### Post by chili555 on 2020-05-10
Are there any clues in the message log?

```
dmesg | grep -e r87 -e wlx
```

---

### Post by tdn19 on 2020-05-10
This is what i got after running that command:

[    4.568707] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[    4.584086] r8712u: register rtl8712_netdev_ops to netdev_ops
[    4.584088] usb 3-2: r8712u: USB_SPEED_HIGH with 4 endpoints
[    4.585604] usb 3-2: r8712u: Boot from EFUSE: Autoload OK
[    4.918200] usb 3-2: r8712u: CustomerID = 0x0000
[    4.918202] usb 3-2: r8712u: MAC Address from efuse = 00:26:ce:03:d3:eb
[    4.918203] usb 3-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[    4.918268] usbcore: registered new interface driver r8712u
[    4.976734] r8712u 3-2:1.0 wlx0026ce03d3eb: renamed from wlan0
[    6.813194] r8712u 3-2:1.0 wlx0026ce03d3eb: 1 RCR=0x153f00e
[    6.813658] r8712u 3-2:1.0 wlx0026ce03d3eb: 2 RCR=0x553f00e
[   18.829610] IPv6: ADDRCONF(NETDEV_CHANGE): wlx0026ce03d3eb: link becomes ready

---

### Post by praseodym on 2020-05-11
Lets try

```
echo "options r8712u low_power=1 power_mgnt=0 ht_enable=0" | sudo tee /etc/modprobe.d/r8712u.conf
sudo modprobe -rfv r8712u
sudo modprobe -v r8712u
```

---

### Post by chili555 on 2020-05-11
Although this is an older thread, it suggests that newer firmware may be helpful. [https://www.linuxquestions.org/questions/slackware-14/slackware14-and-wifi-r8712u-module-4175430170/page2.html](https://www.linuxquestions.org/questions/slackware-14/slackware14-and-wifi-r8712u-module-4175430170/page2.html)

This is the firmware from my fully updated 20.04 install:

```

-rw-r--r--  1 root root [COLOR="#FF0000"]122328[/COLOR] Mar 19 12:37 rtl8712u.bin

```And this is the latest that I downloaded here: [https://git.kernel.org/pub/scm/linux/kernel/git/afaerber/linux-firmware.git/tree/rtlwifi](https://git.kernel.org/pub/scm/linux/kernel/git/afaerber/linux-firmware.git/tree/rtlwifi)

```

-rw-rw-r--  1 chili chili [COLOR="#FF0000"]820799[/COLOR] May 11 11:17 rtl8712u.bin

```In other words, different and possibly helpful. Let's try it and see if it is helpful. This process is easy to revert if needed:

```
cd /usr/lib/firmware/rtlwifi/
sudo mv rtl8712u.bin  rtl8712u.bak
sudo wget  [https://git.kernel.org/pub/scm/linux/kernel/git/afaerber/linux-firmware.git/tree/rtlwifi/rtl8712u.bin](https://git.kernel.org/pub/scm/linux/kernel/git/afaerber/linux-firmware.git/tree/rtlwifi/rtl8712u.bin)
sudo modprobe -r r8712u
```

You will temporarily lose internet connectivity.

```
sudo modprobe r8712u
```

Any improvement? It may take a reboot.

---

### Post by tdn19 on 2020-05-12
> **praseodym said:**
> Lets try

```
echo "options r8712u low_power=1 power_mgnt=0 ht_enable=0" | sudo tee /etc/modprobe.d/r8712u.conf
sudo modprobe -rfv r8712u
sudo modprobe -v r8712u
```

This fixed it. Thanks a lot!

---

### Post by praseodym on 2020-05-14
Glad it worked. Please use thread tools to mark it as solved.

---

