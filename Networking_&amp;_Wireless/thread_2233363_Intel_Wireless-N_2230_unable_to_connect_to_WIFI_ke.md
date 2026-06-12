---
title: "Intel Wireless-N 2230 unable to connect to WIFI keeps trying,Ubuntu 14.04"
date: 2014-07-08
forum: Networking &amp; Wireless
---

### Post by lotus2 on 2014-07-08
[ATTACH]254568[/ATTACH]

ive attached the wireless.txt , i have this problem since a few days ago, and all of a sudden im unable to connect to my home WIFI, the wifi icon keeps surging and ends up unable to connect.

---

### Post by chili555 on 2014-07-08
I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

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

If these changes do not help, please try:```
sudo modprobe -r iwldvm
sudo modprobe iwlwifi 11n_disable=1
```If it helps, make it permanent:```
sudo -i
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```

---

### Post by lotus2 on 2014-07-08
thanks, i have done the settings above and now im connecting successfully, will get back if it decides to not connect again

---

### Post by lotus2 on 2014-07-09
I am facing the problem again, the connection is so unstable on ubuntu .now it keeps asking me for pw authentication to the WiFi i kept entering the correct pw but it keeps asking abd retrying to connect, why is there no way to troubleshoot like Windows lol... doesn't show why can't it connect. My other devices are connected to the router fine

---

### Post by chili555 on 2014-07-09
> **lotus2 said:**
> I am facing the problem again, the connection is so unstable on ubuntu .now it keeps asking me for pw authentication to the WiFi i kept entering the correct pw but it keeps asking abd retrying to connect, why is there no way to troubleshoot like Windows lol... doesn't show why can't it connect. My other devices are connected to the router fineI don't know much about Windows; I have none in my four computers.

We can certainly check the logs:```
cat /var/log/syslog | grep -e wlan -e iwl | tail -n20
```...ideally run as it's trying and failing to authenticate.

---

### Post by jeremy31 on 2014-07-09
> **lotus2 said:**
> I am facing the problem again, the connection is so unstable on ubuntu .now it keeps asking me for pw authentication to the WiFi i kept entering the correct pw but it keeps asking abd retrying to connect, why is there no way to troubleshoot like Windows lol... doesn't show why can't it connect. My other devices are connected to the router fine
What are the other devices and how old is the router

---

