---
title: "Netgear N600 USB Wireless adapter WNDA 3100 for Ubuntu 12.04"
date: 2014-06-11
forum: Networking &amp; Wireless
---

### Post by donnab on 2014-06-11
Hi. Im recently put Ubuntu 12.04 on  My Compaq Presario Desktop Computer and Im wanting to go wireless on it. I have a Netgear N600 Wireless Dual Band USB Adapter- WNDA3100. Im a newbie with Ubuntu so not sure how to install it. I do have Wine in my computer and ran the disk from the Netgear but not sure how to go furter to get it working. 

Any help would be appreciated. 

Thanks

---

### Post by chili555 on 2014-06-14
I understand that you have successfully installed it and it now tries to connect but doesn't. 

Before we start, I have to warn you. As you have seen from the many threads about this device, some running over 100 replies, it is a tricky device to get going. In many cases, it *never* works correctly. If it were mine, I'd sell it or give it away and get a fully supported device. There are many threads here about which are recommended.

If, however, you are determined to try to troubleshoot, there are a few things we can try. First, are there any clues in the message logs?```
dmesg | grep -e ndis -e wlan
```Next, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or vim if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

