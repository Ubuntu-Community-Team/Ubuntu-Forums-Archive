---
title: "Wifi connected but no internet , lenovo y50-70"
date: 2015-07-15
forum: Networking &amp; Wireless
---

### Post by Ebram_Shehata on 2015-07-15
My problem is my wifi always connects successfully to my home network but after a while the internet stops 
and I'm also unable to access 192.168.1.1 although I'm still connected to the network
when I try disable networking & re-enabling it , it works fine for a little bit and re-stops again ..
------------------------------------
Lenovo Y50-70 
Ubuntu 15.04
------------------------------------
I tried to follow instructions in the pinned post : 
"Before posting in Networking & Wireless" -------------> [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
and attached the output files for :

```
wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
chmod +x wireless-info && \
./wireless-info 
```

and I found these in the output txt file :
```

##### lspci #############################


08:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lenovo Device [17aa:4026]
    Kernel driver in use: ath9k



```


so it's : [0280] in here , so I tried to follow this topic :
"How to install a driver for the Broadcom series of PCI wireless cards" ----> [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
but when i try to do :
```
lspci -nn -d 14e4:
```
it gives me no output O.o

---

### Post by praseodym on 2015-07-15
Change the encryption mode to pure WPA2-AES (CCMP), not WPA, deactivate IPv6 in the network-manager profile and the hardware encryption of the Atheros-driver:

```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by Ebram_Shehata on 2015-07-15
Thank u for your reply bro ... please check this picture : 
this is my router settings , any thing needs to be modified after changing the WPA(AES) to : WPA2(AES) ???
[http://www.promisr.net/uploads/1436951183812.png](http://www.promisr.net/uploads/1436951183812.png)

---

### Post by praseodym on 2015-07-15
Choose WPA**2**(AES) and CCMP, Pre-Shared Key. Password at least 8 characters.

---

### Post by Ebram_Shehata on 2015-07-15
where is CCMP ?

---

### Post by praseodym on 2015-07-15
Maybe "Set WEP key"?

---

### Post by PaulW2U on 2015-07-15
> **Ebram_Shehata said:**
> Thank u for your reply bro ... please check this picture : 
this is my router settings , any thing needs to be modified after changing the WPA(AES) to : WPA2(AES) ???
[http://www.promisr.net/uploads/1436951183812.png](http://www.promisr.net/uploads/1436951183812.png)

Please use thumbnails or just link to large images.

We don't all have fast connections and many of us read the forums on mobile devices.

---

### Post by Ebram_Shehata on 2015-07-15
OK about pictures , I'll keep this in mind for next times :)
..
When I press "Set WEP Key" nothing happens ? !

---

### Post by Ebram_Shehata on 2015-07-18
The problem is not solved :(

---

### Post by praseodym on 2015-07-18
Try Wicd instead of the network-manager

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
There you can choose WPA/WPA2 mixed mode from one of the templates.

---

