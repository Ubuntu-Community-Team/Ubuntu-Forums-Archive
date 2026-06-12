---
title: "Wireless on HP Pavilion dv6 not working after installing UbuntuGnome 14.04 LTS"
date: 2015-09-10
forum: Networking &amp; Wireless
---

### Post by dee10 on 2015-09-10
HI guys. I'm totally new with Ubuntu and need some help. I wanted to try something other than windows and Mac is out of the question. So I went UbuntuGnome. Well, I installed it and while connected to hard wire the internet works well. As soon as I unplug and try to go wireless the internet doesn't work. My router is about 3 feet away also. I've tried to turn my wireless off and on and reboot yet nothing. If I could get some help I'd greatly appreciate it. As I don't know much of the Ubuntu lingo, I did learn Ctrl+Alt+T for terminals. I hope that's right.

---

### Post by chili555 on 2015-09-10
Welcome to Ubuntu!

First, let's identify your wireless device. Open a terminal and run:```
lspci -nnk | grep 0280 -A2 
```That funny pipe symbol | is on the right side of my US keyboard on the same key with \.

Thanks.

---

### Post by dee10 on 2015-09-10
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N + WiMAX 6250 [Kilmer Peak] [8086:0089] (rev 57)
    Subsystem: Intel Corporation Centrino Advanced-N + WiMAX 6250 2x2 AGN [8086:1311]
    Kernel driver in use: iwlwifi

That's what came up. Hope that's correct.

---

### Post by chili555 on 2015-09-10
Looks correct so far. Is the hardware switch on or off?```
rfkill list all
```Does it try and fail to connect or what, exactly?

The driver iwlwifi is particularly sensitive to the access point or router.

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
echo "options iwlwifi 11n_disable=8"   >>   /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and let us have your report.

Finally, Network Manager will default to ethernet if it's available. Please make your tests with the ethernet detached.

---

### Post by dee10 on 2015-09-10
```
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wwan: Wireless WAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: i2400m-usb:1-1.3:1.0: WiMAX
    Soft blocked: yes
    Hard blocked: no
 
```

thank's for the response. i'll sure try everything you've posted and i'll update my findings. Sorry if my answer is a little delayed since I'm new to Linux in general. The wireless network just keeps trying to connect when I try to surf the net.

---

### Post by chili555 on 2015-09-10
>  i'll sure try everything you've posted and i'll update my findings.I look forward to your report.

---

