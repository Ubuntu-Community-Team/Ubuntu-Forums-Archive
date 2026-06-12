---
title: "rtl8187b and intrepid"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by mike22 on 2009-02-19
Hello, my gateway laptop with realtek rtl8187b built in is  running dual boot with vista and ubuntu 8.10. I've been having difficulties trying to get internet with my built in adapter. My adapter works perfectly with vista, however I want to be able to surf the internet with ubuntu. My problem with rtl8187b is not a major problem for me, since I have another adapter (rt73) that works fine with ubuntu and vista. Help would be greatly appreciated and I can provide more information if needed. Thanks.

---

### Post by dabomb1022 on 2009-02-19
Try checking for updates user system > Administration and download the updates. That fixed my problems with wifi not working

---

### Post by Crafty Kisses on 2009-02-19
Hey there! Let's see if we can't get that wireless card up and running by using ndiswrapper, so make sure you have the ndiswrapper package installed by running the following:
```
sudo apt-get install ndiswrapper-common
```
Once you have that package installed, you need to grab the driver for the RTL8187b, which you can get right [here.]("http://download2us.softpedia.com/dl/0af152eb73d7b1661469866b2290628d/499d05cb/300025580/drivers/network/win_8187B_6.1063_RtlWlan_402.zip") Once you have the driver installed, find the .inf file in the WinXP folder, once you have done that, run the following:
```
sudo ndiswrapper -i rtl8187b.inf
```
Then to make sure it installed correctly, run the following command:
```
sudo ndiswrapper -l
```
If you get something similar to these results, then it's installed correctly:
```
RTL8187b driver installed, hardware present
```
You're not quite done yet though, you need to make sure the ndiswrapper module loads at every start, so run the following:
```
sudo ndiswrapper –m 
gksu gedit /etc/modules
```
A text file should pop-up, what you want to add at the bottom of the text file is the following:
```
ndiswrapper
```
Once you have done that, save the text file, and reboot with the following command:
```
sudo shutdown -r now
```
Then once you're back into Ubuntu the wireless should work.

---

### Post by mike22 on 2009-02-19
I got it working by following the steps in this thread. [http://ubuntuforums.org/showthread.php?t=792092]("http://ubuntuforums.org/showthread.php?t=792092")

---

