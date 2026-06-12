---
title: "BCM4311 Ubuntu 14.04.2 firmware-b43-installer not working"
date: 2015-07-30
forum: Networking &amp; Wireless
---

### Post by Daniel_Berman on 2015-07-30
Wireless-info.txt -->. [ATTACH]263501[/ATTACH]

At this point I have no wireless available on my Vostro 1000 despite having installed the firmware-b43-installer as listed in the [Broadcom Guide]("http://ubuntuforums.org/showthread.php?t=2214110"). I have never installed the STA driver and have even attempted to purge it just in case it was installed without my awareness. What am I missing?

---

### Post by kerry_s on 2015-07-30
well you need internet to use the installer it downloads the firmware from the internet.

i'm not sure if they did it back in 14, but i no in 15 the drivers are on the installer. try plugging in your usb or cd & run additional drivers, be patient it's slow.

---

### Post by Daniel_Berman on 2015-07-30
Ethernet is and has been alive and well throughout this entire process.

---

### Post by Hadaka on 2015-07-30
Hi ,with a working wired connection,please do..
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```

```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
```
sudo apt-get remove --purge  b43-fwcutter firmware-b43-installer
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
boot
then do..
```
sudo apt-get update
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```cat

---

### Post by Daniel_Berman on 2015-07-30
Thank you Hadaka,
I followed your instructions and the only thing that came back with an error message or any error message actually was that I was unable to remove /etc/modprobe.d/blacklist-bcm43.conf because it did not exist. Still no obvious signs of wifi though,

Here's a new wifi-info.txt if this helps,
[ATTACH]263503[/ATTACH]

---

### Post by tgalati4 on 2015-07-30
The *b43* module is loaded with its dependencies.  

> depends:        bcma,ssb,mac80211,cfg80211

Perhaps reboot and then try:

```
ifconfig
```

Post the entire *lsmod*:

```
lsmod
```

And finally:

```
rfkill list
```

I didn't see any output for it in your debug script.  It should look like:

> tgalati4@Mint17 ~ $ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no


---

### Post by Hadaka on 2015-07-30
Please check that the wireless card is not turned off in bios.
the b43 module is not loading to the card,your country code
did not set as well...so please do..
copy and paste to avoid error please
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda

``` and run again..
```
sudo apt-get update
```
and post the output of...
```
sudo modprobe b43
dmesg | grep b43
```
and another info txt file
thanks

---

### Post by Daniel_Berman on 2015-07-31
Hadaka you had it. I checked the BIOS and sure enough the wireless was turned off as well as the wifi control button. Once those were turned on and saved the unit booted up and the wireless came up in the network manager just fine

I have attached a new wifi-info file in case there is something I missed, and/or if a presumably healthy configuration for this card and machine combination is helpful to anyone.

[ATTACH]263504[/ATTACH]

---

### Post by Hadaka on 2015-07-31
Awesome..glad you found the problem. Everything looks great!
Please take the time to mark this thread solved by clicking thread tools
thanks.

---

