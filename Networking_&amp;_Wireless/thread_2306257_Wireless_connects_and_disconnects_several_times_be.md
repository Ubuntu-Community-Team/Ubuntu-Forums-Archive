---
title: "Wireless connects and disconnects several times before connecting."
date: 2015-12-13
forum: Networking &amp; Wireless
---

### Post by rcmosher on 2015-12-13
This is a weird issue that I've been having a while. I haven't had much to go on to solve it, but just noticed a pattern that might help.

When I log in, my wireless will connect, disconnect, and reconnect a few times before I'm successfully on-line. It can take anywhere from a minute to several minutes before I'm actually able to go on-line. Occasionally an error will be reported with wpa_supplicant. Though not every time I have issues.

Though I noticed something that may shed some light on the issue. Over Thanksgiving I never had this problem at either my uncle's or grandma's. However, I always have it at home, despite moving apartments and completely changing my networking hardware. I came up with a couple possible factors in the problem.

1. At home there are always numerous wi-fi networks listed, including my own. Where I haven't seen this problem, there is only the network I'm connecting to.
2. At both my apartments I had Charter. Though I wouldn't think that would be a factor, as I understand it is just the process of connecting to my wi-fi router, and not the Internet connection that is failing.

All the networks are using WPA & WPA2 Personal for security, so that shouldn't be a factor. Also, at home, numerous devices, including Windows laptops connect without issue, so the issue only seems to be with my Ubuntu laptop.

Maybe this is a bunch of red herrings, but if anything sounds familiar, or you have a recommendation on what to try or look for, please let me know.

Thanks,
Rob

---

### Post by Hadaka on 2015-12-13
Hi, please go here..
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
read the instructions then post back your wireless-info.txt
so we can help you find a solution.
thanks.

---

### Post by rcmosher on 2015-12-14
Here's the requested information. I've done a few searches in the forums, but haven't stumbled on the answer yet.

[ATTACH]266160[/ATTACH]

---

### Post by Hadaka on 2015-12-14
Hi,there are a few things we can try to make it as nice as
when you are at grandma's. Please open a terminal and then
COPY and paste,one line at a time.
```
sudo ifconfig wlan0 down
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
echo "options mac80211 probe_wait_ms=1000" | sudo tee -a /etc/modprobe.d/mac80211.conf
sudo modprobe -v iwlwifi
```

*To delete the above code, should the above not make a difference.
so skip this section first time through.
```
sudo sed -i '/^"options iwlwifi 11n_disable=8"/ d' /etc/modprobe.d/iwlwifi.conf
sudo sed -i '/^"options mac80211 probe_wait_ms=1000"/ d' /etc/modprobe.d/mac80211.conf
```

We need to do some housekeeping on this file, so Please COPY and paste.
saving the original and re-writeing 
```
sudo cp /etc/modules /etc/modules.org
echo "lp\nrtc\npsmouse" | sudo tee /etc/modules
```
Finally please go into networkmgr.,,click the wirelss icon and  adjust your
ipv4 and ipv6 settings like the attached,Ignore that it says Wired1
[ATTACH=CONFIG]266161[/ATTACH][ATTACH=CONFIG]266162[/ATTACH]



[/CODE]

---

### Post by Hadaka on 2015-12-14
Hi,there are a few things we can try to make it as nice as
when you are at grandma's. Please open a terminal and do..
```
sudo ifconfig wlan0 down
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
echo "options mac80211 probe_wait_ms=1000" | sudo tee -a /etc/modprobe.d/mac80211.conf
sudo modprobe -v iwlwifi
```

*To delete the above code, should the above not make a difference
```
sudo sed -i '/^"options iwlwifi 11n_disable=8"/ d' /etc/modprobe.d/iwlwifi.conf
sudo sed -i '/^"options mac80211 probe_wait_ms=1000"/ d' /etc/modprobe.d/mac80211.conf
```

We need to do some housekeeping on this file, so Please COPY and paste.
saving the original and re-writeing 
```
sudo cp /etc/modules /etc/modules/org
echo "lp\nrtc\npsmouse" | sudo tee /etc/modules
```
Finally please go into networkmgr.,,click the wirelss icon and  adjust your
ipv4 and ipv6 settings like the attached,ignore the wired1 ..it should say LoveBirds101
[ATTACH=CONFIG]266161[/ATTACH][ATTACH=CONFIG]266162[/ATTACH]



[/CODE]

---

### Post by rcmosher on 2015-12-14
So far it seems to be working. Thank you very much.

---

### Post by rcmosher on 2015-12-15
It seems I spoke too soon. I just logged on this morning and had the same problem with multiple reconnects and disconnects. I guess I just got lucky last night.

---

### Post by Hadaka on 2015-12-15
Hi, that may have been my fault, we put a parameter in then
took it back out,my template was in error, please copy and
paste..
```
sudo modprobe -r iwldvm
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rf iwlwifi
sudo modprobe -v iwlwifi
```
boot

---

### Post by rcmosher on 2015-12-15
I executed those commands and I'm still having the issue. 
I also removed a second "options iwlwifi 11n_disable=8" line from iwlwifi.conf as there were two at the end of this.

One funny thing is it will sometimes connect right away on boot-up, and then disconnect on log-in.

---

### Post by Hadaka on 2015-12-15
Hi, please run the wireless text file again.

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
thanks

---

### Post by rcmosher on 2015-12-15
As requested. Thanks for helping me work through this.

[ATTACH]266181[/ATTACH]

---

### Post by Hadaka on 2015-12-15
How did this happen??
##### network managers ##################

Installed:

    NetworkManager
    Wicd
-______________________
Pick one then re-do the first set commands.
also do..
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
boot and test.

---

### Post by rcmosher on 2015-12-18
That seems to have been it. I removed Wicd and it connects much more quickly. I think I installed that when network-manager wasn't working at all for me, and somehow ended up with both.

---

### Post by Hadaka on 2015-12-18
Great ! Glad you got it working.

---

