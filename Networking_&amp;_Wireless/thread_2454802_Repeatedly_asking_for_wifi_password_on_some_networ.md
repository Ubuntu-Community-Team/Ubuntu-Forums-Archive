---
title: "Repeatedly asking for wifi password on some networks"
date: 2020-12-06
forum: Networking &amp; Wireless
---

### Post by default-man on 2020-12-06
Hi! 

I'm using ubuntu 20.10, but the problem exists since 19.10. I can not connect to some networks with my wifi-card Intel Corporation Centrino Advanced-N 6205 (802.11a/b/g/n) (I'm using a Lenovo X230). It "connects", asks me for a wifi-password and then repeats to do so, there's nothing changing. I can connect to these wifis with other notebooks (windows) and phones (android and iOS) just fine.

Is there an easy way to find out if a network is 5Ghz or 2.4Ghz? Because that is somehow my only suspicion of wireless networks I can and can not connect to. But regardless, I believe both should work.

I uploaded my wireless-info here: [https://pastebin.com/kDcEF1yz](https://pastebin.com/kDcEF1yz) (btw, great procedure from you guys!)

Thank you in advance!

---

### Post by praseodym on 2020-12-07
Obviously, you are located in Austria?! Run

```
sudo sed -i "s/REGDOMAIN=/REGDOMAIN=AT/g" /etc/default/crda 
```
and reboot

---

### Post by default-man on 2020-12-07
Yes I am located in Austria. Thank you for your hint. Unfortunately it didn't change anything (rebooted twice and also checked the content of the /etc/default/crda file). 

Still the same behaviour. 
I uploaded another file on pastebin [https://pastebin.com/6dqeua1F](https://pastebin.com/6dqeua1F) and this time I ran the script while trying to connect to one network which doesn't work (GASSL) - if that changes anything.

---

### Post by praseodym on 2020-12-07
Ok, now try
```

sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```
Try to connect again. Please also show
```

sudo dmesg | egrep 'firm|iwl|reason'
```

---

### Post by alecjw on 2020-12-10
I wonder if you're having the same problem I solved [here]("https://ubuntuforums.org/showthread.php?t=2455001")?

---

### Post by default-man on 2020-12-11
Unfortunately (or luckily...) I don't have access to this wifi everyday. 

@praseodom: I'm having problems executing the commands, first commands does nothing I believe, the /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf just shows "[connection] wifi.powersave = 2". That should include more, right? Also I get "Failed to restart network-manager.service: Unit network-manager.service not found." on the second line.

my sudo dmesg | egrep 'firm|iwl|reason': [https://pastebin.com/TmwjCxjj](https://pastebin.com/TmwjCxjj)

@alecjw: Thank you for your input! just dmesg shows this:  [https://pastebin.com/j1behbnk](https://pastebin.com/j1behbnk) 
 So i guess it's not the same problem unfortunately.
It looks like it's just reconnecting again and again. Unfortunately I don't have access to the router itself.
Also sudo iwlist scan | grep "ESSID" just shows only one entry for the respective wifi, so i guess that means it's only using one band?

---

### Post by praseodym on 2020-12-11
Rebooted?

---

### Post by default-man on 2020-12-18
> **praseodym said:**
> Rebooted?

I rebooted and it still doesn't work. etc/NetworkManager/conf.d/default-wifi-powersave-on.conf just shows 
"[connection]
 wifi.powersave = 2"

the network-manager.service can't be found. Only service I have with "network" is network-online.target and networkd-dispatcher.service

---

### Post by default-man on 2020-12-18
I finally found a solution, I don't know what the caveats of this are, but still the Wifi finally works.

See:
[https://ubuntuforums.org/showthread.php?t=2235768](https://ubuntuforums.org/showthread.php?t=2235768) 
or [https://superuser.com/questions/911635/wifi-authentication-times-out](https://superuser.com/questions/911635/wifi-authentication-times-out)

Basically all i did was 
> echo "options iwlwifi 11n_disable=1 wd_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf

and rebooted. 


I checked the iwlwifi.conf file before and it hat some cryptic stuff in it, unfortunately I didn't back it up. Now it only has those 2 disable statements and it works. Maybe if you run into the same error you can just append these statements instead of replacing the whole file.

---

