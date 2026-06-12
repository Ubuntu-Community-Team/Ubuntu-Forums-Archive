---
title: "Ubuntu 16.04 LTS - TP-LINK N150"
date: 2017-03-01
forum: Networking &amp; Wireless
---

### Post by ubu112 on 2017-03-01
Please,I bought Tp-Link N150 to pass from wireless g to n.I have Acer Aspire One AOA/ZG5 and I hoped that I don't need to install driver because I don't have a Cd reader.Now I don't know how to connect it.Can someone help me?Thank you

---

### Post by chili555 on 2017-03-01
Please open a terminal Ctrl+Alt+t and run and post:```
lsusb
```Thanks.

---

### Post by ubu112 on 2017-03-01
Thank you,"chili555".The terminal say:```
ID 0cf3:9271 Atheros Communications AR 9271 802.11n
```

---

### Post by chili555 on 2017-03-01
I have that exact same device and I plug it in and it connects! I am surprised it doesn't do the same for you.

May we see:```
lsmod | grep ath
```If the module ath9k_htc isn't loaded, please load it and see what happens:```
sudo modprobe ath9k_htc
```If the wireless doesn't start, check the log for messages:```
dmesg | grep ath
```

---

### Post by ubu112 on 2017-03-01
You are the expert - [www.imgur.com/ae0tK8c]("http://www.imgur.com/ae0tK8c")
I didn't make sudo because maybe ath9k_htc is loaded

---

### Post by chili555 on 2017-03-01
It looks pretty well perfect. If you wish to use the USB and not the internal device, I'd blacklist the internal and reboot:```
sudo -i
echo "blacklist ath5k"  >>  /etc/modprobe.d/blacklist.conf
exit
```After the reboot, does the USB work?```
iwconfig
```

---

### Post by ubu112 on 2017-03-01
I don't understand nothing,but maybe the country is wrong
HaveI to disconnect before blacklisting ?can I come back if I want?all depends from speed if it's faster or not.
Stupid question: How can I understand if it's working?because I always had a solid green light

---

### Post by chili555 on 2017-03-01
The country is wrong. However, every way that I know of to change it fails. I assume the country CN is encoded at the factory in the chip itself. If we can't change it, all we can do is ignore it and move forward.> HaveI to disconnect before blacklisting ?No. If it were required, I would have requested it. Please blacklist, reboot and report.> can I come back if I want?Are you asking if you can undo the blacklist and go back to the internal device if needed? Certainly you can.

---

### Post by ubu112 on 2017-03-01
I don't know how to say THANK YOU.It works - [www.imgur.com/A7rW0p3](www.imgur.com/A7rW0p3) - I tried with speedtest.net: Chromium 20+(before)40+(after)-Firefox_ the same that before_,but I tried with the speedtest of my provider (Vodafone)and it gives 40+.What do you think about it?with Firefox I have the same problem I had,if you remember,with wired connection.Can I change channels if I want?and if yes,how can I do?

---

### Post by chili555 on 2017-03-01
I think 40+ is very good. The actual speed you achieve is very much dependent on the distance from the router, interference, and, of course, the speed that your internet service provider delivers to your doorstep.

You can change the channel only in the router.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

### Post by ubu112 on 2017-03-01
Do you think I made the right choice with this N adapter?or can be better with an AC adapter?because I have a AC router.What do you think about speed difference between Chromium and Firefox?which browser can you suggest to me,I mean one faster but with this small pc at 32bit I can't use Chrome because isn't supported.Working in AC,sometimes,I have problems with 5 Ghz (it disconnect with more distance from router,changing weather,walls)which is more stable:5 Ghz or 2,4 Ghz?Finally,curiosity,are you an engineer or are you working in IT sector?your commands are in "bash"?how easy is to learn "bash"from 1 to 10?Can you,please,suggest to me some good and easy books to learn something more?THANK YOU VERY MUCH "chili555"

---

