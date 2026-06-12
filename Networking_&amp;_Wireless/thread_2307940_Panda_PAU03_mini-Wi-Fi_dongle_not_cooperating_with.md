---
title: "Panda PAU03 mini-Wi-Fi dongle not cooperating with Xubuntu 14.04.3 or Mint 17.2."
date: 2015-12-29
forum: Networking &amp; Wireless
---

### Post by Jerry_Gorland on 2015-12-29
I recently purchased a Panda PAU03 mini-Wi-Fi USB dongle.  I tried it on my Gigabyte box to see if it works.  The Panda "sees" all the wireless nodes around me, but refuses to connect to mine (little circle continually goes in circles, then fails).  (FYI: Wireless info is avail. at: [http://ubuntuforums.org/showthread.php?t=2304607&p=13413074#post13413074](http://ubuntuforums.org/showthread.php?t=2304607&p=13413074#post13413074).)

I tried disabling the existing NIC with
sudo modprobe -r rtl8723ae * (i.e., the existing internal NIC)*
sudo service network-manager restart

However, no difference.  Has anyone seen this behaviour before with the Panda dongle?

---

### Post by Hadaka on 2015-12-29
Hi, I sought a consult with Dr Chili on this and here is what we came up with.
Your wireless report shows you are missing the Vendor I.D. for your usb device.
# USB device [COLOR=#ff0000]0x:0x[/COLOR] (rt2800usb)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", #KERNEL=="wlan*", NAME="wlan1"

# Panda PAU03 mini-Wi-Fi USB dongle
#Bus 001 Device 002: ID [COLOR=#ff0000]148f:5370[/COLOR] Ralink Technology, Corp. RT5370 Wireless Adapter

# We are going to build 2 FILES:
# /etc/udev/rules.d/network_drivers.rules
# /etc/modprobe.d/network_drivers.conf

Open a terminal and then do.
```
gksudo gedit /etc/udev/rules.d/network_drivers.rules
```
Add one long line please COPY and paste as Caps, brackets, punctuation, etc. are crucial.
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="148f", ATTR{idProduct}=="5370", RUN+="/sbin/modprobe -qba rt2800usb"
```
Close and save gedit. 

Back to terminal and do..
```
gksudo gedit /etc/modprobe.d/network_drivers.conf
```
Add the line for this file,again please copy and paste.
```
install rt2800usb /sbin/modprobe --ignore-install rt2800usb $CMDLINE_OPTS; /bin/echo "148f 5370" > /sys/bus/usb/drivers/rt2800usb/new_id
```
Proofread twice, save and close gedit. Insert the device. If it doesn't start immediately, you might have to do:
```
sudo modprobe rt2800usb
```

---

### Post by Jerry_Gorland on 2015-12-31
Thanks, Hadaka and Chilli555.  Yes, that did the trick!  How does one gain such great knowledge?  The good thing about this fix is that it would allow Wi-Fi to work with a default Linux Live.  Is this workaround a failure of Linux to properly enumerate the device, or something else?

---

### Post by Hadaka on 2015-12-31
Hi, Glad that worked for you.
as you can see a Panda PAU03 is using a Ralink chip, RT5370 Wireless Adapter  rt2800usb
so that vendor may also use different chips in that same device.
the missing vendor id of 148f 5370 is due to that reason, there
no way to know what chip a reseller might use.

---

### Post by Jerry_Gorland on 2016-01-02
Thanks!!  That's helpful and could assist someone in fixing a similar problem.

---

