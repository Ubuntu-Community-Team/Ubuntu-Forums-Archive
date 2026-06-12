---
title: "Wifi disconnects frequently!"
date: 2015-07-21
forum: Networking &amp; Wireless
---

### Post by ashwary2 on 2015-07-21
Hello. I'm a new user. I connected to WiFi when i installed Ubuntu 14.04. But after some time, the internet stopped working and i could not get it to work by disabling and re-enabling wifi. I had to restart my  laptop to get it working. So googled the issue and found out that this is a common bug in linux with my Wifi card. My WiFi card is Realtek Semiconductor Co., Ltd. RTL8723BE PCIe. 

I tried a solution which was given on one forum and installed this module - [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new)

After install, my wifi still gets disconnected frequently but now i don't have to restart the computer to get it working again. Now i can reconnect just by disabling and re-enabling the wifi from wifi swith or the top bar. 

So i googled again to resolve this issue. People had suggest to turn power management off. I checked and my wifi power management was already set to off. 

This problem arises even while the laptop is on AC power. 

I tried another solution which included adding something in a certain config file. I ran this command - 
sudo sh -c 'echo "options iwlwifi 11n_disable=1" >> /etc/modprobe.d/iwlwifi.conf'

But it didn't help either. 

Any ideas? let me know if you need any other information.

---

### Post by chili555 on 2015-07-21
> I tried another solution which included adding something in a certain config file. I ran this command - 
sudo sh -c 'echo "options iwlwifi 11n_disable=1" >> /etc/modprobe.d/iwlwifi.conf'As your driver is rtl8723be and not iwlwifi, we are not surprised that the command did nothing.

NOTE TO SEARCHERS: Please don't randomly add parameters, blacklists, etc., for any and everything you read on the forums unless you are *sure* it applies to your device and your driver. Best case, they are a waste of your time and, worst case, they actually hurt the problem rather than fix it. Then we have to go on a safari to track down and repair all the damage before we can fix it. Unless you are *sure*, stop and ask.

</rant>

Please try this instead:```
sudo -i
echo "options rtl8723be  fwlps=0"  >  /etc/modprobe.d/rtl8723be.conf
exit
```Did you install rtlwifi_new with dkms? If you don't know or are unsure, then probably not. If you didn't, you'll need to recompile whenever a newer kernel version, also known as linux-image is installed. Did you do that?```
cd ~/path/to/rtlwifi_new
make clean
make
sudo make install

```Reboot.

Any improvement?

---

### Post by ashwary2 on 2015-07-22
Thanks a lot for the reply. It's been only 3 days since started using Ubuntu. Thanks for your tip. 

I've tried the solution you have suggested. I'll report if the problem still persists. 

I've not installed rtlwifi_new with dkms. Should i do that? if yes, how?

---

### Post by chili555 on 2015-07-22
Installing with dkms means that you needn't recompile every time a newer kernel version is installed by Update Manager. Here is the procedure. Although the device is different, the driver suite, rtlwifi_new, is the same: [http://askubuntu.com/questions/629679/rtl8723ae-unstable-on-ubuntu-14-04](http://askubuntu.com/questions/629679/rtl8723ae-unstable-on-ubuntu-14-04)

---

### Post by ashwary2 on 2016-01-04
>  			 				[INDENT] 					Installing with dkms means that you needn't recompile every time a  newer kernel version is installed by Update Manager. Here is the  procedure. Although the device is different, the driver suite,  rtlwifi_new, is the same: [http://askubuntu.com/questions/62967...n-ubuntu-14-04]("http://askubuntu.com/questions/629679/rtl8723ae-unstable-on-ubuntu-14-04") 				[/INDENT] 			
  			   		

This seems to have worked. Thanks a lot for the reply. :)

---

