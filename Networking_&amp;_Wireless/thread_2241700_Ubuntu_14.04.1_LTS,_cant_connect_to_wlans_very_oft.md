---
title: "Ubuntu 14.04.1 LTS, cant connect to wlans very often"
date: 2014-08-27
forum: Networking &amp; Wireless
---

### Post by jan29 on 2014-08-27
Hello,

I sometimes cant connect to wlans of my university and to the wlan of the flat were i currently stay. The Wlan-Hotspot of my phone as a temporary solution seems to work every time but is slow and cost intensiv : / . The same wlans seems to work after some time but it seems to be not connected to disable the wlan or restart of the computer.

Hope u can help me, internet is really important at my university ( upload of files during class etc.) 

Thx Jan

---

### Post by varunendra on 2014-08-29
Hello jan29, Welcome to the forums! :)

Your current access-point is using TKIP algorithm with WPA2 encryption. That is a non-standard combination that may cause problems. If you have admin access to the router, or if you can convince the owner of the router, please have it changed to WPA2 with AES (CCMP). I hope that alone should solve the problem with the connection in your flat.

For troubleshooting of the problem with University network, please post a report when you are in the University. I recommend this script which is slightly different than the one you used above : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)
It provides a little more info that may be useful sometimes. If it fails to generate a report (happens sometimes due to a reported bug which I haven't found time to fix yet), please use the regular one.

---

### Post by jan29 on 2014-08-29
Hi varunendra, 

The new script you provided worked :> i added the output.
I am currently at my University but i cant connect to the wlans again ( we have 3 different ones) tec-alumos , itesm , tec_secure. Since my last post i also reinstalled my drivers -> sudo apt-get install --reinstall linux-firmware.
I also disabled some options in hope it would improve the situation -> 
options iwlwifi 11n_disable=1
options iwlwifi bt_coex_active=N

in etc/modprobe.d/iwlwifi.conf

Any ideas what else i should try?

---

### Post by varunendra on 2014-08-29
Why are you using ndiswrapper? Do you really need it? If not, I suggest to completely remove it (ndiswrapper, as well as its configuration files/entries).

And why is the mac address of wlan0 set as "unmanaged device" in NetworkManager.conf? That is something I can't even guess, and the /etc/interfaces file is at default anyway.

For now, I have 3 suggestions (apart from removing ndiswrapper if it is not necessary) -

[indent]**1)** Delete the [keyfile] section from NetworkManager.conf. Manually, or with this command -
```
sudo sed -i '/\[keyfile\]/,+1 d' /etc/NetworkManager.conf
```
This will delete the line [keyfile] and the line immediately following it.

**2)** Explicitly set your country code for regdomain settings -
```
sudo sed -i 's/^REG.*=$/&DE/' /etc/default/crda
sudo iw reg set DE
```
..assuming you are in Germany. If not, please refer to this table to find your country code, and change 'DE' with it : [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table)

**3)** Try changing value of parameter 11n_disable from 1 to 8, and remove the backup file (I'm not sure, but it might get used) -
```
sudo rm /etc/modprobe.d/**iwlwifi.conf~**
sudo sed -i '/11n_disable/ s/1/8/' /etc/modprobe.d/iwlwifi.conf
```[/indent]

If the problem still remains the same, please post a fresh report with the above changes applied. Please mind that you may have to reboot for some of the above changes to take effect properly.

---

