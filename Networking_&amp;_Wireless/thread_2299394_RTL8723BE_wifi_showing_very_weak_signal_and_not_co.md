---
title: "RTL8723BE wifi showing very weak signal and not connecting  Ubuntu 15.04"
date: 2015-10-18
forum: Networking &amp; Wireless
---

### Post by pankaj_sharma2 on 2015-10-18
Hi, I am new to ubuntu, after installing ubuntu , it showing wifi signal very week, connect rarely to wifi and if connect disconnect after few seconds automatically.
 Already tried many solution find through google but nothing worked.
[COLOR=#000000]I download and ran wireless-script and these are the results:
[http://paste.ubuntu.com/12840137/](http://paste.ubuntu.com/12840137/)[/COLOR]

---

### Post by Hadaka on 2015-10-18
hi,from a working wired connection do..
[http://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04/](http://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04/)
then do..
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get autoremove && sudo apt-get autoclean
```
then..
```
sudo iw reg set IN
sudo sed -i 's/^REG.*=$/&IN/' /etc/default/crda
```
reboot, disconnect wired connection,test wireless
thanks

---

### Post by pankaj_sharma2 on 2015-10-20
Its still not working

---

### Post by Hadaka on 2015-10-20
please run the wireless script again and post it..thanks,

---

### Post by pankaj_sharma2 on 2015-10-21
I [COLOR=#000000] ran wireless-script and these are the results:
[http://paste.ubuntu.com/12896068/](http://paste.ubuntu.com/12896068/)
[/COLOR]

---

### Post by Hadaka on 2015-10-22
you posted the script program not the wireless-info.txt file
please run and try again,
thanks

---

### Post by pankaj_sharma2 on 2015-10-22
Sorry,
[COLOR=#000000]The wireless-info.txt file is 
[http://paste.ubuntu.com/12896068/](http://paste.ubuntu.com/12896068/)
Thanks[/COLOR]

---

### Post by Hadaka on 2015-10-22
please COPY and paste..
```
echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
sudo modprobe -rv rtl8723be
sudo modprobe -v rtl8723be
```
and did you go here and follow the directions to load the driver?
[http://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04/](http://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04/)
thanks

---

### Post by pankaj_sharma2 on 2015-10-23
I have run these commands, and i also have followed the direction on the page
[http://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04/](http://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04/)
but its still not working.

---

### Post by chili555 on 2015-10-24
There are several Linux drivers that are sensitive to the access point conditions. 

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Does your device scan?```
sudo iwlist wlan0 scan
```

---

