---
title: "Realtek 8812AU"
date: 2018-02-17
forum: Networking &amp; Wireless
---

### Post by mc4man on 2018-02-17
Due to continuing nonsense of my ISP I need to use the 5g band to get good wifi thru-put 
Unfortunately this laptop's built-in (Intel Corporation Wireless 7260) is 2.4g only so picked up a  usb device which uses Realtek 8812AU
The repo's rtl8812au-dkms package, while it works, is useless as after about 10 min it disconnects with no way to re-connect other than a reboot which is again only good for 10 min.

However the git driver works absolutely fine, stays connected & I get the thru-put expected for service (200mbps plan
The only downside is that on a log out/in or if manually disconnecting there also is no way to connect other than reboot.
Currently using this driver installed via dkms
[https://github.com/gordboy/rtl8812au](https://github.com/gordboy/rtl8812au)

Any insights as to why it can only connect via a boot up?

---

### Post by jeremy31 on 2018-02-17
You might want to see what module parameters are available ```
modinfo -p 8812au
```
I know the old rtl8192cu github used rtw_power_mgnt=0 rtw_enusbss=0 options to disable power management, so you might be able to ```
echo "options 8812au rtw_power_mgnt=0 rtw_enusbss=0" | sudo tee /etc/modprobe.d/8812au.conf
```
Reboot and see if it made an improvement

Network Manager can also enable wifi power management and that can be disabled with ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

---

### Post by Hadaka on 2018-02-17
Hi, have you blacklisted the intel driver ?
have you unchecked the "Connect Automatically" box for the 2.4 connection ?
have you checked the "Connect Automatically" box for the 5 GHz connection ?
is the ssid different as it should be from the 2.4 GHz...as in my_wifi2.4  my_wifi5.0 ???
Please post a wireless script...click jeremy31's link for how to.
Thanks

---

### Post by mc4man on 2018-02-17
> **jeremy31 said:**
> You might want to see what module parameters are available ```
modinfo -p 8812au
```
I know the old rtl8192cu github used rtw_power_mgnt=0 rtw_enusbss=0 options to disable power management, so you might be able to ```
echo "options 8812au rtw_power_mgnt=0 rtw_enusbss=0" | sudo tee /etc/modprobe.d/8812au.conf
```
Reboot and see if it made an improvement

Network Manager can also enable wifi power management and that can be disabled with ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

> **Hadaka said:**
> Hi, have you blacklisted the intel driver ?
have you unchecked the "Connect Automatically" box for the 2.4 connection ?
have you checked the "Connect Automatically" box for the 5 GHz connection ?
is the ssid different as it should be from the 2.4 GHz...as in my_wifi2.4  my_wifi5.0 ???
Please post a wireless script...click jeremy31's link for how to.
Thanks

Thanks guys, what I've found

The repo driver seems unsuitable as it doesn't respond well to kernel upgrades & in my target (18.04) in a fresh install it works but requires I unplug the device & plug back in after a reboot > log in.
On my current 16.04 & 18.04 installs basically the same deal plus can't re-connect if disconnected or can't connect after log out/in. (both use lightdm..

The git driver works fine with kernel upgrades (got one for 16.04 & tried with the 4.15 upgrade in 18.04 -proposed).  So that's likely the driver I'd use long term..

The issue with loss of connection & no way to reconnect after a log out/in seems to be lightdm related. On the fresh install of 18.04 removed the repo driver, installed the git one with dkms, rebooted and it was fine. Doing a log out/in also was fine.
Installed and switched from gdm3 to lightdm > reboot, everything fine. A log out/in caused the disconnect & failure to reconnect.

Why lightdm has a role in this when logging out/in remains a mystery..

Not sure of use but..
[http://paste.ubuntu.com/p/ZpVDNCj3fn/](http://paste.ubuntu.com/p/ZpVDNCj3fn/)

---

### Post by mc4man on 2018-02-17
Wasn't lightdm but could see the issue in lightdm > greeter as there was no wifi & couldn't be enabled (no permission
Seems somehow allow all was unset or possibly never set though swear I did set initially.
Any way working fine now with the git driver.

---

### Post by Hadaka on 2018-02-17
Hi, glad you found a solution !
Thank you for posting what you found and how
you were able to resolve.It will help searchers.
Also thank you for marking your thread Soved.

---

