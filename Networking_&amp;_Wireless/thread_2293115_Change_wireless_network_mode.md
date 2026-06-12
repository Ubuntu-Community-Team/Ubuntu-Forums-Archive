---
title: "Change wireless network mode"
date: 2015-09-02
forum: Networking &amp; Wireless
---

### Post by Giperboloid on 2015-09-02
Hello, guys.
I need to change the wireless mode of my network interface from 802.11bgn to 802.11b. The only thing I've found is the result of executing command "lshw".
[[IMG]http://i11.pixs.ru/thumbs/2/4/0/Screenshot_7804031_18650240.jpg[/IMG]]("http://pixs.ru/showimage/Screenshot_7804031_18650240.png")

---

### Post by chili555 on 2015-09-02
Generally, the declaration you highlighted is coded into the chip itself. It merely means that the hardware was manufactured to be capable of 802.11b, g or n speeds depending, of course, on the driver and the router. You can change many things but probably not what's hard-coded in the silicon. The 802.11bgn notation is not an indication of what the chip is doing at any one moment; it is merely a notation of what it might do under the right circumstances.

The typical wireless card in a laptop or desktop operates in 'managed' mode. Here is a sample from my machine:```
chili@T410:~$ iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          [COLOR="#FF0000"]Mode:Managed[/COLOR]  Frequency:2.462 GHz  Access Point: xx:D7:19:41:54:xx   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:95   Missed beacon:0

lo        no wireless extensions.

```Managed means that the router to which you are connecting will negotiate the correct channel, bit-rate, IP address, DNS nameservers, etc. 

May I ask what you are trying to accomplish? Do you have a bigger underlying problem?

---

### Post by Giperboloid on 2015-09-02
I'm trying to make that changes cause I can connect to wi-fi but I don't have an access to the Internet. That manipulations helped me on Windows and I supposed that they'd do that for me on Ubuntu.

---

### Post by chili555 on 2015-09-02
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

Finally, you might try restricting the 802.11N activity. From a terminal:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and tell us if it has improved.

---

### Post by Giperboloid on 2015-09-03
Thanks for your help. I found the solution:
```
[FONT=dejavu sans mono]sudo sysctl -w  net.ipv4.ip_default_ttl=129[/FONT]
[FONT=dejavu sans mono]sudo sysctl -w  net.ipv6.ip_default_ttl=129[/FONT]
```

The problem wasn't in the network interface, it was hidden in the uncompleted ttl configuration.

---

