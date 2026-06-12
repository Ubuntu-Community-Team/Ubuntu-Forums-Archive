---
title: "Broadcom 4328 wifi not working (Mac Mini 3,1/Early 2009)"
date: 2015-01-09
forum: Networking &amp; Wireless
---

### Post by ojdon on 2015-01-09
Hi there

I'm trying to get Ubuntu (Gnome Ubuntu spin) installed on my Mac Mini (Early 2009 model). Unfortunately, it comes with some proprietary hardware that doesn't quite work out of the box. The piece of hardware I'm trying to get working at the moment is the Broadcom 4328 wireless card. Using the "Additional Drivers" application it suggests that I should download and activate the Broadcom STA proprietary driver (Which I used a usb wifi dongle to download it). 

On a reboot it seems to detect the card however it says that "No Networks Found" on the network manager. I have also tried removing that driver and installing the one from the "firmware-b43-installer" package but get the same results.

Any possible solutions? 

Thanks

---

### Post by wildmanne39 on 2015-01-09
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by ojdon on 2015-01-25
Hi there,

Sorry for the lack of a reply. Here is the results from my wireless script. I uploaded it from the Mac Mini itself as I have an old USB wireless adapter plugged in. 

[http://pastebin.com/PR7c87Yw]("http://pastebin.com/PR7c87Yw")

---

### Post by Hadaka on 2015-01-25
Hi please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
remove the usb wifi dongle and boot

---

### Post by ojdon on 2015-01-25
The card is detected but it is not searching for networks, as "No Networks" message is displayed:
[http://i.imgur.com/bmJ0SxX.jpg]("http://i.imgur.com/bmJ0SxX.jpg")
So I had to plug the USB adapter back in once it rebooted.

---

### Post by Hadaka on 2015-01-25
Hi, please leave the driver as b43, please
post the output of..
```
cat /etc/network/interfaces
rfkill list all
```
thanks.

---

### Post by ojdon on 2015-01-25
> **Hadaka said:**
> Hi, please leave the driver as b43, please
post the output of..
```
cat /etc/network/interfaces
rfkill list all
```
thanks.

Ok, so I get this for the first command:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

...And this for the latter:
```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by Hadaka on 2015-01-25
Hi, while connected to the internet please do..
```
sudo apt-get update
sudo apt-get upgrade
```
remove the usb..boot

---

### Post by ojdon on 2015-01-25
Done. There were a few packages that needed updating, I rebooted but the issue is still the same.

---

### Post by Hadaka on 2015-01-25
ok ..lets try this, remove the usb dongle wifi

then copy and paste these commands one at a time
```
sudo iw reg set GB
sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
i know you need to read thses commands, but the usb wireless cannont be attached for this
to acept the commands.
boot
any improvement?

---

### Post by ojdon on 2015-01-26
No change, unfortunately. :/

---

### Post by Hadaka on 2015-01-26
you seem to have several things that need adjusting..
lets start with.creating a file to turn off power mgmt
for wlan0
please do..
bring up the editor
```
gksu gedit /etc/pm/power.d/wireless
```
then in the  EDITOR put 

```
#!/bin/sh
/sbin/iwconfig wlan0 power off
```
save and close gedit

back to terminal  ctrl/alt/t and do..

```
sudo chmod +x /etc/pm/power.d/wireless
```

boot

---

