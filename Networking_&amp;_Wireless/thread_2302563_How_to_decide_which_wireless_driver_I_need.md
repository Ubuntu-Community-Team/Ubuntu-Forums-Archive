---
title: "How to decide which wireless driver I need"
date: 2015-11-11
forum: Networking &amp; Wireless
---

### Post by amarumayo on 2015-11-11
Hi all, On Lenovo Thinkpad L440. Internet keeps dropping out. Wireless card is below. Ubuntu certification for this model laptop says "Installation of proprietary NVidia video driver is required for full functionality" however, additional drivers in ubuntu displays "no additional drivers available". How can I install the correct driver to fix this issue?Thanks!02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192EE PCIe Wireless Network Adapter [10ec:818b]bird@bird:~$

---

### Post by chili555 on 2015-11-11
I expect that you already have the correct driver. There may be, however, a few things we can tweak to get the driver and hardware to work and play well together.

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
echo "options rtl8192ee ips=0"  >  /etc/modprobe.d/rtl8192ee.conf
exit 
```Reboot and tell us if there is any improvement.

---

### Post by amarumayo on 2015-11-12
Thanks for your assistance. I have applied the changes that you suggest to my router and system. I am still having problem with intermittent outages. Sometimes it works fine, and others I can't load any pages. It seems to work in cycles of a few minutes. Any other ideas?

Thanks again!

---

### Post by chili555 on 2015-11-12
Please try:

```
sudo -i
echo "options rtl8192ee swenc=1 ips=0"  >  /etc/modprobe.d/rtl8192ee.conf
exit
```

Reboot and tell us if there is any improvement.

---

### Post by amarumayo on 2015-11-12
Still having the same problem. Pinging google.com gives me widely fluctuating times ranging between 300 ms and 10,000 ms if that is any help.

Thanks.

---

### Post by chili555 on 2015-11-12
Please try:```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms linux-firmware
```Reboot and let us know if it's improved.

---

### Post by amarumayo on 2015-11-12
Installing Ubuntu Wily (15.10) fixed this issue for me. Thank for your help.

---

