---
title: "not able to connect via wireless with all correct settings"
date: 2017-01-01
forum: Networking &amp; Wireless
---

### Post by Vitor_Matias on 2017-01-01
Hi,
I'm using Ubuntu 16.04 on an old machine (started with Ubuntu 10) and untill now I had no problem connecting to my wireless net at home. A few days ago my daughter started to complain that she was unable to connect and that the authentication window was always poping up, even tough the password was/is correct and remains unchanged for years!
I've used the wireless-info script to collect the information that I hope someone will use to provide me some light on the issue.
I've tried to remove the connection and add again but the problem insists on not going away.
Any help will be appreciated!

---

### Post by wildmanne39 on 2017-01-01
Your router is on channel 0, I recommend setting it to 1, 6, or 11 not auto then save the settings.

We need to set the country code for your router if you are in the Lisbon area please do:
```
sudo iw reg set PT
```
```
sudo sed -i 's/^REG.*=$/&PT/' /etc/default/crda
```
Does the wifi come on if not reboot.
Thanks

---

### Post by jeremy31 on 2017-01-01
I think the script had a problem and it really isn't on channel 0
In addition to wildmanne39's advise, I would
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
Reboot
The 70-persistent-net.rules may be causing problems in systemd especially with it naming your wifi eth1

---

### Post by Vitor_Matias on 2017-01-01
Hello again,
thank you both for the replies, but the problem remains.
I've confirmed the channel, it is on 12.
I've collected a new file after running the suggested commands.

---

### Post by wildmanne39 on 2017-01-01
I made one typo in my second command in the previous post, I have corrected it please run both of those commands again.
I apologize for the error.
Thanks

---

### Post by Vitor_Matias on 2017-01-02
thanks once again, the problem is that it seems unable to authenticate, because the behaviour is the same as if I use a wrong password, which is not the case.

---

### Post by wildmanne39 on 2017-01-04
Any time you can not connect to your wifi it will always pop the password box back up even if it is not a password issue, I do not see a password issue in the dmesg but there are somethings that we can do that will help.
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

```
Check the settings in the router. WPA2-AES is best, not WPA and WPA2 mixed mode or TKIP.

Go into network manager and remove all wifi connections then reboot and let network manager find your connections then set your wifi settings to match the screenshots, then do
```
sudo  systemctl restart NetworkManager.service
``` without the ethernet plugged in.
[ATTACH=CONFIG]273049[/ATTACH][ATTACH=CONFIG]273050[/ATTACH]
does it connect if not install wicd.

---

