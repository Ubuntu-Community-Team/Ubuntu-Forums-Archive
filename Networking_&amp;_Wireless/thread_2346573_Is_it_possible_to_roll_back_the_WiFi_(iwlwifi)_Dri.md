---
title: "Is it possible to roll back the WiFi (iwlwifi) Driver? Very low speed!"
date: 2016-12-16
forum: Networking &amp; Wireless
---

### Post by bijan2 on 2016-12-16
It appears that the latest version of "iwlwifi" driver on Ubuntu 16.04 is causing a significant drop on my WiFi speed. Just wondering if I can go back to what worked before.
Network card is ==>> Intel Centrino Wireless-N + WiMax 6150 (iwlwifi)

I appreciate any help...

---

### Post by TheFu on 2016-12-16
If you download the driver source, compile it, link it, and load it into the kernel in the normal way, then you can, certainly.  Just be aware that every time there is a new kernel, you'll need to go through the same steps.

Don't know about finding the old package - should be possible, just not something I've done. Then you can **pin** that package. [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto) There will probably be dependency issues, which will become more and more important over time.  That is what happens with held packages.

---

### Post by chili555 on 2016-12-16
I would like to see more details of your current driver and, most importantly, firmware. Please run and post:```
dmesg | grep iwl
```

---

### Post by bijan2 on 2016-12-17
Thank you, here is the dmesg... command output.

---

### Post by chili555 on 2016-12-17
I believe that you already have the latest firmware available. There are a few tweaks you can make to help your speed and connectivity.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
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

### Post by bijan2 on 2016-12-17
The problem is solved and my WiFi speed is back to what it was on Ubuntu 14.04. There was no need for rolling back the driver after all. Thanks for all your recommendations, it helped a lot...

---

### Post by chili555 on 2016-12-17
> **bijan2 said:**
> The problem is solved and my WiFi speed is back to what it was on Ubuntu 14.04. There was no need for rolling back the driver after all. Thanks for all your recommendations, it helped a lot...Awesome! Glad it's working.

---

