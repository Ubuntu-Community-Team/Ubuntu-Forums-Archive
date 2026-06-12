---
title: "Atheros Network Card Gives Slow WiFi Speed, Ubuntu 16.10"
date: 2016-10-23
forum: Networking &amp; Wireless
---

### Post by tlaporta on 2016-10-23
I noticed today that my Ubuntu 16.10 laptop is showing internet speeds only about 50% of what my android phone is getting. I'm with Verizon, and their internet speed test shows me getting just about 45 Mb/S download speeds with my android phone, but only about 27 from the laptop. The only difference I can find is the wireless adaptor for the laptop. I've attached the output of the Ubuntu wireless script, and the output of iwconfig is below. I notic the the Invalid misc value of 657, which seems concerning. How do I research what those are? Any suggestions on how I should proceed in investigating/fixing this issue?

```
wlp2s0    IEEE 802.11  ESSID:"2LittlePuppyDoodles"            Mode:Managed  Frequency:2.412 GHz  Access Point: 18:1B:EB:1A:A7:CF   
          Bit Rate=65 Mb/s   Tx-Power=17 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:657   Missed beacon:0


lo        no wireless extensions.
```

---

### Post by chili555 on 2016-10-24
First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. In my own case, changing from Auto to 20 MHz only, actually increased my speeds by about 15%!

I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. I notice that your router is set to channel 1, the most congested. In your case, I suggest, then, 6 or 11. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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

If these changes are ineffective, we will have other suggestions.

---

### Post by tlaporta on 2016-10-24
Unfortunately, none of these suggestions worked. The regulatory domain was already set to US, the change in channel only slowed things down (albeit only slightly), and the encryption was already set to WPA2-AES. I also set IPv6 to Ignore, to no avail. You alluded to some other suggestions?

---

### Post by chili555 on 2016-10-24
Please try:```
sudo -i
echo "options  cfg80211  cfg80211_disable_40mhz_24ghz=Y  >  /etc/modprobe.d/cfg80211.conf
exit
```You already have the sometimes useful, "options ath9k nohwcrypt=1".

Reboot and let us hear your report.

---

### Post by tlaporta on 2016-10-25
No dice. Still holding at the same general speed in three different speed tests.

---

