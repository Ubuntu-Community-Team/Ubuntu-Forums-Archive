---
title: "Wifi Signal is very weak with Realtek RTL8723BE"
date: 2017-03-23
forum: Networking &amp; Wireless
---

### Post by jorgeosorio on 2017-03-23
Hello everyone,
Please help, I finished installing Ubuntu 16.04 in my HP laptop that has Realtek RTL8723BE, but the wifi signal is very weak, I have to sit next to the modem to have decent sign, what shoul I do to solve this.
Please help me
Thanks

---

### Post by jeremy31 on 2017-03-24
*Thread moved to **Networking & Wireless**.*
Let's see if changing the ant_sel parameter makes an improvement
```
iwlist scan | egrep -i 'ssid|quality'
```

That will show the Access Points and the reception, then we will unload the module and try the first parameter option
```
sudo modprobe -r rtl8723be
```
```
sudo modprobe rtl8723be ant_sel=1
```
```
iwlist scan | egrep -i 'ssid|quality'
```

The results from the scan may be the same as original or better but we will check the last option for ant_sel

```
sudo modprobe -r rtl8723be
```
```
sudo modprobe rtl8723be ant_sel=2
```
```
iwlist scan | egrep -i 'ssid|quality'
```

If ant_sel=1 was the best then do
```
echo "options rtl8723be ant_sel=1" | sudo tee /etc/modprobe.d/rtl8723-ant-sel.conf
```

If ant_sel=2 was the better option
```
echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723-ant-sel.conf
```

---

### Post by jescott418 on 2017-04-06
The solution is spot on needed ant 1 and it must have been on ant 0 or ant 2 because signal was so weak. Have a HP Pavilion 15 with the RTL8723be. Thanks

---

### Post by hansaj007 on 2017-04-21
1- install new module for realtek wifi cards where they solved the constant disconnects
-install required packages
sudo apt-get install build-essential git


-git clone new realtek wifi modules
git clone [https://github.com/lwfinger/rtlwifi_new/](https://github.com/lwfinger/rtlwifi_new/)


-enter the directory
cd rtlwifi_new


-build it
make


-install
sudo make install


Now you can reboot or unload/load modules
-unload modules
sudo modprobe -r rtl8723be


-load new module
sudo modprobe rtl8723be


2- firmware update.


Download [rtl8723befw.bin]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1454843/+attachment/4438588/+files/rtl8723befw.bin"), copy it to /lib/firmware/rtlwifi/ and then reboot your laptop.
-Disable the sleep feature of the driver:
$ echo "options rtl8723be fwlps=0" | sudo tee /etc/modprobe.d/rtl8723be.conf


3- Antena Test
iwlist scan | egrep -i 'ssid|quality'


sudo modprobe -r rtl8723be


Check antena 1
sudo modprobe rtl8723be ant_sel=1


iwlist scan | egrep -i 'ssid|quality'


sudo modprobe -r rtl8723be


check antena 2
sudo modprobe rtl8723be ant_sel=2


iwlist scan | egrep -i 'ssid|quality'


If ant_sel=1 was the best then do
echo "options rtl8723be ant_sel=1" | sudo tee /etc/modprobe.d/rtl8723-ant-sel.conf


4- Also, I recommend that your regulatory domain be set explicitly. Check yours:


sudo iw reg get


-Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)
Mine is IN 


sudo iw reg set IN


-To set it permanant
gksudo gedit /etc/default/crda
REGDOMAIN=IN

---

### Post by mayur.patil1211 on 2017-06-12
[ 						 					]("https://ubuntuforums.org/member.php?u=1924242") 				 				 					 						 	[**[COLOR=#C61919][B]@jeremy31 : Thanks man it works, i don't how many sites i gone through and how many solution i tried bt finally u solved my problem.   Thanks **[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1924242")

---

