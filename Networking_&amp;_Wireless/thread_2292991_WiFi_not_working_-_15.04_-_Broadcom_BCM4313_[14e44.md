---
title: "WiFi not working - 15.04 - Broadcom BCM4313 [14e4:4727] (rev 01)"
date: 2015-09-01
forum: Networking &amp; Wireless
---

### Post by daksh_shah2 on 2015-09-01
I will first start by describing my problem: I have a 2 WiFis that I want to use on Ubuntu, they first worked and then after a few days they stopped stopped working. I tried reinstalling the machine, with no luck. I swapped the modem with another one of the same model and after that it again worked but only for a few days until now, when it has again stopped working. 
I tried searching for my answer and found there could be a driver problem.
My WiFi Card is: Broadcom BCM4314 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
I have gone through the thread [http://ubuntuforums.org/showthread.php?t=2232939](http://ubuntuforums.org/showthread.php?t=2232939) 
But the problem there was, like the #7 said, it does not work with the 'b43' driver. But I could not find the "[COLOR=#000000]brcmsmac[/COLOR]" driver either. I tried installing 'wl', 'wl/brcm80211' and 'bcmwl-kernel-source' (reinstall) none of them helped me see my WiFi's SSID in the list of available networks. Though, I am not sure that the method I followed, i.e. The command I typed were 100% correct. So I could try again, the commands you want me to, to install the same drivers again.
Also looked at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx), but could not find any driver as such for "4727"
And I started with, and was basically trying to follow the steps given at [http://askubuntu.com/a/60395/326313](http://askubuntu.com/a/60395/326313) , it originally asks me to install the same driver that WAS there by default. And even if I redo it, it does not work. So I tried variations of the method given there, with the foresaid drivers to try and replace them.
I can let you know the outputs of any command you tell me, and I would like to mention that I am new to Ubuntu.

Update: (next day) It was funny that this time when I booted up my laptop, I could see the WiFi network again. I have no idea how. But I am perplexed.

---

