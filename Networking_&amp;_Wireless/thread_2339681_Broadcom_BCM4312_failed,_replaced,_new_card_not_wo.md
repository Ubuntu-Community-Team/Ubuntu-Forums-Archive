---
title: "Broadcom BCM4312: failed, replaced, new card not working"
date: 2016-10-11
forum: Networking &amp; Wireless
---

### Post by mringer on 2016-10-11
Dell Inspiron 1525, L-Ub 14.04, wicd 1.7.2.4-4.1 (latest)
Broadcom BCM4312. firmware-b43-installer & b43-fwcutter
1.018-2 (latest).

After working for a few years, this failed. I was advised 
that this was probably a hardware fail as I had not then 
changed any software. Symptom: the wicd panel says 
"no wireless networks found". Also it sometimes worked 
for short periods. 

So then I tried a Ralink USB dongle and I couldnt make it 
work. (another story, off-topic).
So then I opened up my PC & removed the wireless card
& put in a new one of the same type. Still doesnt work. 

I have done

sudo apt-get update          and
sudo apt-get dist-upgrade    and

I attach (I hope) the output of wireless-info. Some puzzles:


1: Rfkill says the card is hard blocked, which I believe 
means switched off. So I pushed the switch on, & Rfkill
still says it is blocked.


2: wireless-info says wicd is not running but ps says it is:

ps ax | grep wicd
 1243 ?        S      0:01 /usr/bin/python -O /usr/share/wicd/daemon/wicd-daemon.py
 1302 ?        S      0:00 /usr/bin/python -O /usr/share/wicd/daemon/monitor.py
 1761 ?        Sl     0:00 /usr/bin/python -O /usr/share/wicd/gtk/wicd-client.py --tray
 4132 pts/4    S+     0:00 grep --color=auto wicd


3: If the card is switched off, how does iwlist know what 
channels there are?

Please any advice?
thank you.

---

### Post by jeremy31 on 2016-10-11
You may have the wrong module installed for your wireless.  I would ```
sudo apt-get remove bcmwl-kernel-source  && sudo apt-get install firmware-b43-installer
```

Then reboot

I think the rfkill results are faulty because of the bcmwl kernel module

The iwlist results are based on regulatory settings of the OS and not dependent of whether the wifi device can be used

---

### Post by Hadaka on 2016-10-11
Hi, your card performs best with the b43 dirver
you currently have the "wl" broadcom-kernel-source driver loaded.
BCM4312 802.11b/g LP-PHY [14e4:4315] Kernel driver in use: wl

From a working wired connection please open a terminal then copy and paste one line at a time.
* Ignore any errors do every line.
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```

##### network managers ##################
Installed: Wicd     Running: None found.
 *Not running most likely because the /etc/network/interfaces below is incorrect.
you cannot have both a network manager and a managed network....

##### interfaces ########################
auto lo
iface lo inet loopback
iface wlan0 inet dhcp
wpa-psk <WPA key removed>
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid aaisp-rd4
* Please do to hopefully clear the wicd problem and correct your interface file
```
sudo sed -i '/^wpa/ d' /etc/network/interfaces
```

##### iw reg get ########################
Region: Europe/London (based on set time zone)
country 00:
```
sudo iw reg set GB
sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda
```

This is confused because of the diver attempts, let's delete it and let the system rebuild it on boot
##### udev rules ########################
[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x11ab:0x4354 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4315 (b43)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
Remove the wired connection,boot and test wireless

If after you do all the above and it still shows blocked
Dell computer keyboard toggle on and off for wifi is FN/F2 keys
##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN

---

### Post by mringer on 2016-10-12
Thank you who replied, now working. (I will try to mark thread solved). Mark

---

### Post by Hadaka on 2016-10-13
Great ! jeremy31 and I are glad you got it working.
Thank You for marking your thread solved.

---

