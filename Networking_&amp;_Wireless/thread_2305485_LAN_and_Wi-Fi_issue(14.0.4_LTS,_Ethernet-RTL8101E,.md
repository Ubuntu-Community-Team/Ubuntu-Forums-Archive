---
title: "LAN and Wi-Fi issue(14.0.4 LTS, Ethernet-RTL8101E, WLAN-RTL8723BE)"
date: 2015-12-06
forum: Networking &amp; Wireless
---

### Post by shri_thecool on 2015-12-06
HI All,

This is my very first interaction with Ubuntu....infact with Linux environment and as expected there seems to be no smooth path here and that is testing my patience; making things more interesting to me.
I would love to dig in more but my laptop being the only system, Ubuntu as base OS and 1 week of continuous failures prompted to post here. I would appreciate a kind help.

Config-
HP 15-ac184tu
OS- Ubuntu 14.0.4 LTS
Ethernet- RTL8101E/RTL8102E (rev 07)
Wireless adapter- RTL8723BE
Router- Asus RT-N-13u


Issue-
Wired PPOE connection and Wi-Fi both keep getting disconnected; so far since installation I could only connect to Wi-Fi for 5 minutes.
Except my router's Wi-Fi other available wireless connections are not getting scanned, I added SSID to 'Connect to hidden Wi-Fi network' but still connection could not be established.
No Internet means stuck with plenty to do list :(

Things tried so far-
1) [http://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04](http://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04)

Output- Couldn't make it work as neither other available Wi-Fi connections in surrounding are scanned nor adding SSID to hidden network help also wired PPOE connection not working.....in short there's absolutely no way to connect to internet.
I wanted to know whether manually copy-past of rtl8723BE directory from github and installing would help in any way.


2) [http://ubuntuforums.org/showthread.php?t=2304709](http://ubuntuforums.org/showthread.php?t=2304709)

Output- I followed instructions as is except echo "blacklist ideapad-laptop" but issue still remained!!


3) With Ndiswrapper...no luck


Please find attached [COLOR=#000000]wireless-info.txt
[/COLOR]Positively hope a new learning experience, knowledge and resolution!!

Thanks for reading :)

---

### Post by praseodym on 2015-12-06
Hi,

there is another wifi driver loaded (iwlwifi for Intel cards):
```

echo "blacklist iwlwifi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
For the Realtek card try these ([COLOR="#FF0000"]additional[/COLOR]) parameter(s)

```
echo "options rtl8723be swenc=1 fwlps=0 [COLOR="#FF0000"]ips=0[/COLOR]" | sudo tee /etc/modprobe.d/rtl8723be.conf
echo 'KERNEL=="wlan0", RUN+="/sbin/iwconfig wlan0 txpower 18"' | sudo tee -a /etc/udev/rules.d/75-wlan.rules 
```
Remove the current wifi profile and reboot. Try again to connect with IPv6 disabled

---

### Post by shri_thecool on 2015-12-06
HI praseodym,
thanks for responding!!

I have run these commands, disabled iv6 but after reboot the Wi-Fi is not getting connected.

Please refer to a screenshot from friend's WIN machine where several Wi-Fi connections are scanned but in my case only home router is getting scanned, what could be possible reason.

Attached is error screenshot too.

---

### Post by Jerry_Gorland on 2015-12-07
Can you position your PC to be right next to your Wi-Fi router's antenna?  I ask because I found that to be the case (RTL8723BE was "functional" but only at close range).

---

