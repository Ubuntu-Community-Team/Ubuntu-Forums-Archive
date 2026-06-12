---
title: "slow wifi"
date: 2016-11-19
forum: Networking &amp; Wireless
---

### Post by timschneider95 on 2016-11-19
Hey there,

just installed ubuntu and figured out that something is not right with the wifi. I did like mentioned in the sticky a update and dist-upgrade. It is now a little bit better but still very slow. With windows I'm getting 45 mbit/s but on ubuntu only 3.

Hope you can help me out. Thanks!

---

### Post by jeremy31 on 2016-11-19
Welcome to the forums

Lets disable the power management for the wifi with
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf 
```

Then use a module option to see if we can increase the performance
```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
Reboot

---

### Post by timschneider95 on 2016-11-19
Hey,

thanks for you fast reply. I executed the commands and rebooted my system. Sadly it didn't help.

Also after rebooting the system isn't always auto connecting to my wifi network. Sometimes it does sometimes not.

---

### Post by jeremy31 on 2016-11-19
The changes can be reversed with
```
sudo sed -i 's/wifi.powersave = 2/wifi.powersave = 3/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
```
sudo sed -i 's/options iwlwifi 11n_disable=8/#options iwlwifi 11n_disable=8/' /etc/modprobe.d/iwlwifi.conf
```

Reboot and I will look at the script results again

---

### Post by timschneider95 on 2016-11-19
Hey,

thanks again. Its now on 4-5. So it increased a little bit but compared to windows its 10x slower. 

I uploaded the script results again - idk if it was necessary. 

Thanks for your help so far!

---

### Post by timschneider95 on 2016-11-19
solved. Somehow.

Thanks a lot for your help!

---

### Post by timschneider95 on 2016-11-20
So I though its fixed but its not. I'm now getting up to 15 mbps on ubuntu. And on windows still 45 mbps. 

On windows such problems are all about drivers. So on that experience I'm looked up for intel wireless drivers. When I'm doing 'modinfo iwlwifi | grep 7265' its outputting 'firmware: iwlwifi-7265-13.ucode' and 'firmware: iwlwifi-7265D-13.ucode'. If I'm right and compared with kernel.org wiki [https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi#and_7265_support](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi#and_7265_support) my driver is 4 Versions behind? 
Searching for 'ls /lib/firmware/iwlwifi-7265* -l' there is a iwlwifi-7265-17.ucode and iwlwifi-7265D-17.ucode. But its not used? I'm confused.

---

### Post by jeremy31 on 2016-11-20
You actually have a 7260 wifi using iwlwifi-7260-17.ucode
Is there actually 2 access points on the same channel with the same SSID?

The modinfo results on iwlwifi usually show the oldest firmware version that can be used

---

### Post by timschneider95 on 2016-11-20
I'm not entirely sure how my father exactly managed our wireless network. But there was a 2,4 GHZ and a 5 GHZ in the past with two SSIDs may its now one. Its hidden anyway so its not that easy to check. Also its connected through an repeater. Normally I can't connect on my position directly to the router.

---

### Post by jeremy31 on 2016-11-20
Does the repeater use the same name as the access point?  Can you change the repeaters name and channel?

---

