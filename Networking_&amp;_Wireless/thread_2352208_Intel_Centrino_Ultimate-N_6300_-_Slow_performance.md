---
title: "Intel Centrino Ultimate-N 6300 - Slow performance"
date: 2017-02-10
forum: Networking &amp; Wireless
---

### Post by evanshaw2 on 2017-02-10
This is my first post here. I've been using linux in my professional life for years but I am by no means an expert.

The machine in question is a ThinkPad W530 with an Intel Corporation Centrino Ultimate-N 6300 [8086:4238] (rev 3e)

When  booting to Windows 10, the wireless performance is excellent. However,  when booting to Ubuntu the speeds seem to be "capped" at 2MB/sec.  SpeedTest.net confirms I am getting about half the download speed under linux.

Link to wireless info script output: [http://pastebin.com/NcfznVBg](http://pastebin.com/NcfznVBg)

There are many old posts related to this card. Some of the solutions seem to be outdated, others simply don't seem to work.

Any wizards here with ideas on how to fix this is appreciated. The machine is usable, just not practical with the "speed cap".

---

### Post by chili555 on 2017-02-10
Wow! Why is your network unencrypted? That is very dangerous. You may as well put your money in a shoebox on the front porch.

As well, I actually believe the hardware and driver will work better with WPA2-AES encryption, for which it was built.

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

If these changes do not help, please try:

```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=8

```
If it helps, make it permanent:

```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```

---

### Post by evanshaw2 on 2017-02-10
Thanks! Good news! The solution was found here: [https://www.linuxquestions.org/questions/linux-networking-3/slow-wifi-on-intel-centrino-ultimate-n-6300-a-4175599455/](https://www.linuxquestions.org/questions/linux-networking-3/slow-wifi-on-intel-centrino-ultimate-n-6300-a-4175599455/)

Similar to what you suggested here, except I didn't modify the regulatory domain info.

The network is not encrypted. I don't own it so there is nothing I can do about it. Nothing a good VPN can't solve. Thanks again for your detailed response!

May I ask what is regulatory domain and why did you want me to modify it? How would that affect my WiFi speeds?

---

### Post by jeremy31 on 2017-02-10
Please post a new wireless script result as you might have some conflicting settings.  And you can answer your own question at askubuntu

---

### Post by chili555 on 2017-02-10
Please see: [https://wireless.wiki.kernel.org/en/developers/regulatory/crda](https://wireless.wiki.kernel.org/en/developers/regulatory/crda)

It tells your system what channels, transmit power and channel width to operate on so that is in regulatory compliance, but more importantly, is aligned with the router or other wireless access point. In many cases I've worked on, but not every case, it has been helpful. In the case of a little USB wireless that I bought that was manufactured in China and with which the CRDA was coded to CN, it was impossible to connect to my US-sold router without setting the regulatory domain to US.

It is easy enough to try temporarily with:```
sudo iw reg set IS
```...or whatever your region is if not Iceland. It will reset on reboot or else:```
sudo iw reg set 00
```

---

