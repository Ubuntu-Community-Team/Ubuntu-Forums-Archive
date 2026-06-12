---
title: "Low Internet Connection Speed via Wireless"
date: 2015-11-23
forum: Networking &amp; Wireless
---

### Post by asteris2 on 2015-11-23
Hello !
 I am using Ubuntu Mate, and Linux in general, for the past few months and I am still kinda new to the Unix environment.
After  testing Linux Mint, Ubuntu and Ubuntu MATE, I am now extremely  satisfied with Ubuntu MATE considering its clean interface and its speed  in general! My problem is with my wireless connection. I noticed the  problem after installing Linux Mint, but after a while I realised that I  shouldn't have installed it without an ethernet cable. Afterwards, I  installed Ubuntu with wired connection but the same problem occured. I  didn't like Ubuntu as they were quite slow compared to Linux Mint, so  after a quick search, I found that Ubuntu MATE is a great OS for laptop  computers. After installing Ubuntu MATE with a  wired connection as  well, the same problem occured once more. 
I am using a Dell XPS 15 L502x laptop and I have a 25Mbps internet connection speed and while I am connected  through a wired connection on this laptop I get its full potential.  However, while being wirelessly connected to the internet the speed  drops down to 5-6Mbps and its terribly slow !
Here's what i get after using sudo lshw -C network :  [http://pastebin.com/XghFPYka](http://pastebin.com/XghFPYka)  

I tried disabling the 'n' feature from my wireless adapter but  nothing changed. In general, I tried a lot of things that I found while I  googled my problem, but I thought of posting my own device and try find  some help about my problem specifically.


I have some other issues too with my Linux installation on this device  but my internet connection is the one I give more priority to.


I don't know what else I can do to provide you with more information on this issue so I would appreciate any help at all!
  Thanks a lot !

---

### Post by chili555 on 2015-11-23
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

If these changes do not help, please try:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and tell us if performance has improved.

---

### Post by asteris2 on 2015-11-23
Thanks for such quick reply on my problem !!

I tried everything that you suggested and I think I didn't do something wrong, but there was no improvement to the issue. Is there anything else in mind that i could try ? 

Thanks once again for your help!

---

### Post by chili555 on 2015-11-24
After a fresh reboot, may we see:```
dmesg | grep -e iwl -e 80211
```Thanks.

---

### Post by asteris2 on 2015-11-24
Here's the result :  [http://paste.ubuntu.com/13493564/](http://paste.ubuntu.com/13493564/)

---

