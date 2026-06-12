---
title: "Intel centrino 6205 doesn't work in ubuntu 14.04 (newer post)"
date: 2016-07-19
forum: Networking &amp; Wireless
---

### Post by maors123 on 2016-07-19
I bought a refurbished ThinPad x220 and installed ubuntu 16.04. The problem is that the **wireless connection drops periodically while shown as connected**. I have an Intel centrino advances-N 6205 wireless card. I have **installed Windows 10 and it works fine**. Can it be that the drivers that exist for the 6205 don't work with the 4.4 kernel?

Here I found the driver for the 6205:
[URL="http://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html"]**[http://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html](http://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html)**
[/URL]
But the newest kernel supported is 3.2. 

I ran the[COLOR=#000000] **wireless info script, **the result is attached.[/COLOR]

---

### Post by chili555 on 2016-07-19
The driver for your device, iwlwifi, works perfectly well in later kernel versions. I am writing this reply using it right now.

There are a few things that can be done to assist the hardware/driver/router system to work better.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and *certainly not* TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=8
```If it helps, make it permanent:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and let us have your report.

---

### Post by maors123 on 2016-07-20
I ran all the steps expect the definitions of the router, and the wifi worked for a while and than dropped. I got the message : "network service discovery disabled  your current network has a .local domain, which is not recommended and incompatible with the avahi network service discovery . the service has been disabled." 

Can I change the avahi configuration to fix this?

---

