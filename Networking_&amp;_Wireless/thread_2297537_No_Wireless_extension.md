---
title: "No Wireless extension"
date: 2015-10-04
forum: Networking &amp; Wireless
---

### Post by zooey85 on 2015-10-04
Hi, 
I'm totally new to Ubuntu. Just have started using it and I have a problem with my wifi. It gets disconnected every few minutes. To get connected I have to restart my laptop. I've searched through all different forums to find a solution but nothing helps. I'm not good at computers so I really don't know where to look for the solution to my wifi problem. I hope someone could help me.
Anyway this is what I get after typing iwconfig in terminal:
eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Rappen"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: FC:F5:28:CB:CA:D5   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:105   Missed beacon:0

lo        no wireless extensions.

---

### Post by jeremy31 on 2015-10-04
That is not an issue, it is normal.  Post the result from terminal for ```
lspci -nnk | grep -iA2 net
```

---

### Post by zooey85 on 2015-10-04
ok. there it it is:
jojo@Lorien:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:108c]
    Kernel driver in use: r8169
04:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6623]
    Kernel driver in use: ath9k

---

### Post by jeremy31 on 2015-10-04
Can you check the encryption settings on the wifi router?  What is the current encryption?

---

### Post by zooey85 on 2015-10-04
I'm mostly travelling and I'm usually staying at hotels but I'm trying to connect to the router's settings but it's not working..... it it zyxell. I don't think that helps:(

It is an open connection but you have a generated user login and password by the hotel.

---

### Post by jim_deadlock on 2015-10-04
Perhaps it's just a weak wifi signal? How many bars are showing on your wifi icon (top right of screen)?

---

### Post by sandyd on 2015-10-04
Hi, when you are in range of the wireless network you want to connect to, can you run the Wireless Info Script?
You can see instructions here -> [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by howefield on 2015-10-05
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by zooey85 on 2015-10-05
Well I get 3 out of 4 bars and after I copied this 
wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
chmod +x wireless-info && \
./wireless-info

I got 
--2015-10-05 21:14:34--  [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info)
Resolving github.com (github.com)... 192.30.252.131
Connecting to github.com (github.com)|192.30.252.131|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info) [following]
--2015-10-05 21:14:35--  [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 23.235.43.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|23.235.43.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15868 (15K) [text/plain]
Saving to: &#8216;wireless-info&#8217;

wireless-info       100%[=====================>]  15,50K  --.-KB/s   in 0s     

Last-modified header missing -- time-stamps turned off.
2015-10-05 21:14:35 (77,9 MB/s) - &#8216;wireless-info&#8217; saved [15868/15868]

---

### Post by praseodym on 2015-10-05
Hi,

first, deactivate the hardware encryption of the driver:
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Second: For different encryption modes differing from pure WPA2-AES (CCMP) the network-manager is not working well. Try Wicd instead:

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
The template offers mixed mode, etc. If it is working uninstall the network-manager via software center.

[http://sourceforge.net/projects/wicd/](http://sourceforge.net/projects/wicd/)

For the Add-on see the (German) page here

[http://www.elektronenblitz63.de/html/wicd.html](http://www.elektronenblitz63.de/html/wicd.html)

---

### Post by zooey85 on 2015-10-05
I did everything what you wrote. After typing iwconfig it still shows no wireless extension but the internet is working so far. Hopefully it stays this way. Thanks very much

---

