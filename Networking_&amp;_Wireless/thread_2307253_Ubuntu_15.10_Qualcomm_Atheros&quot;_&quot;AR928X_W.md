---
title: "Ubuntu 15.10 Qualcomm Atheros&quot; &quot;AR928X Wireless&quot; very slow &lt;56kbit"
date: 2015-12-23
forum: Networking &amp; Wireless
---

### Post by LuckyLuzz on 2015-12-23
Hey guys,
to introduce myself to this nice community, i would like to say that I am pretty happy with Ubuntu since I installed it on my Dell E7440 two months ago! It's just better for surfing the web than Win10, also it has a way better battery life!
A couple days ago I installed Ubuntu on my Living Room "Walking Dead" Notebook, an older Model (6 Years) from Packard Bell (Easynote-TJ65) with:
Pentium Duo Core T4400 @2,2 GHz
4GB RAM
160GB Hard Drive
GeForce GT 240
Wifi Qualcomm Atheros" "AR928X Wireless Network Adapter (PCI-Express)"

Its running pretty good on Win10 with no issues. I got a 25 Mbit Internet connection too.

So now whats my problem. Something is wrong with the Wifi Card on Ubuntu, the max. Speed I can get is 56 kbit. It's like surfing in the 90s...just without the modem sound ^^
Google is my friend and so I found a couple troubleshooting's.  [URL="http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/"]http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/
[/URL]I tried 1,4 and 5. of them but nothing helped my poor Notebook to come back to the 2010s

Also I did the " Thread: Before posting in Network & Wireless". The txt file and a foto from my System while doing a speed test are attached. Just again my Dell works perfect and with full download speed, but the Wireless Connection on the Packard Bell is slow as .. on Ubuntu.


I am looking forward to hear from you guys. Thanks and merry Christmas.

---

### Post by praseodym on 2015-12-23
Hi,

deactivate the hardware encryption of the driver

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
and choose Wicd instead of the Network-Mnager (here Wicd, too):

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
More info here (German):

[http://www.elektronenblitz63.de/html/wicd.html](http://www.elektronenblitz63.de/html/wicd.html)

---

### Post by LuckyLuzz on 2015-12-26
Hi,
thanks for your reply! Unfortunately it has not helped me to reach full speed, just to 400kbit from the possible 25Mbit. I just tested it again with cable network on Ubuntu and Wifi on Win10 to be sure.

So any other possible solutions?

---

### Post by weatherman2 on 2015-12-26
Although there may be a software solution, there is also a hardware solution:  upgrade the wireless card, perhaps to one that also has better performance (dual band 802.11n).  I have installed the Intel 5100 and Intel 6235 dual band wireless cards in a couple of different laptops with Ubuntu and it has worked well without any tweaks.  The 6235 has bluetooth; the 5100 does not.

Looks like the internal wireless card is easy to get to in this particular laptop (if this is the one you have):

[ftp://ftp.packardbell.com/pub/itemnr/CS070A00/en_tj_disassembly.pdf](ftp://ftp.packardbell.com/pub/itemnr/CS070A00/en_tj_disassembly.pdf)

Here in the US, it is fairly easy to find cheap used wireless cards on eBay.  (Sometimes $5 USD or less shipped.)  if you are not in the US, not sure how easy/cheap it is.

The trick is finding the right wireless card.  A quick look at the disassembly guide above shows that your wireless card is probably a "full height" card.  The 5100 comes in both full height and half height sizes.  The 6235 is only half height but can still replace a full height card with an adapter - extra cost you may not want to worry about on an old laptop.

Assuming you'd get an Intel 5100 (I think the correct name is "Intel 512AN_MMW WiFi Link 5100"), you can get the full height version but also make sure you get one that is *NOT* for IBM/Lenovo or HP - while this version may in fact work in Ubuntu, it may not work at all in Windows if you ever need to go back.  There are different flavors of these wireless cards; some are interchangeable, others are not.  A version of the card for Dell, Acer, Toshiba, or Sony ought to work fine.  I'd get a used card and not a "new" card from Asia that may be an engineering sample - I've had bad luck with those but great luck with used cards. 

Your existing card may have two antenna wires or three.  It doesn't necessarily matter if you replace your current card that has three wires with a card that uses only two.  (The 5100 and 6235 have only two wires.)

---

### Post by Hadaka on 2015-12-26
Hi, please open a terminal then do.
```
sudo iw reg set DE
sudo sed -i 's/^REG.*=$/&DE/' /etc/default/crda
```
then do.
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove
sudo apt-get clean
```
then,,
Access your router settings and remove the TKIP setting
set WPA2/AES
boot and test...if no change please re run the wireless-info script.
thanks

---

### Post by LuckyLuzz on 2015-12-27
Hi,

nothing new. I attached the updated script. At the moment I got Win and Ubuntu on this Laptop, so if this is not working I will go back to win.

 Somewhere in my old computer parts I found a Wifi Card from a Dell D530 ( 4965AGA MM2). I will try that one later this day if nobody has another guess. 

Thanks

---

### Post by praseodym on 2015-12-27
Uninstall the network-manager:
```

sudo service network-manager stop
sudo apt-get remove --purge network-manager*
sudo killall wpa_supplicant
sudo service wicd restart
```
Choose the template WPA1/2 (passphrase). You may want to try
```

sudo apt-get remove --purge resolvconf
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service wicd restart
```

---

### Post by LuckyLuzz on 2015-12-27
Hi,
still just 400KiB/s... :(

Updated Script is attached.

---

### Post by praseodym on 2015-12-27
Change the encryption in your router to WPA2-AES (CCMP), not mixed mode WPA/WPA2. Adjust Wicd accordingly. Also check if your router firmware is up-to-date. Fixed channel 13 and bandwidth to 20MHz instead of 20/40MHz can also be tried

---

### Post by LuckyLuzz on 2015-12-31
I have solved it over replacing the wifi card.

Thanks a lot for your help!

---

