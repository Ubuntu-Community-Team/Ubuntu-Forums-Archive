---
title: "No Internet. Please Help"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by FNGtyler on 2007-03-22
I am sure you all have heard this a thousand times. I am new to linux and don't no sh*t.
I however learn quick

I have a acer aspire 5000
I am attempting to connect through a actiontec dsl gateway modem
I have been connecting with no difficulty, simply plug in ethernet connection or connect wirelessly.

I download and installed ubuntu 6.10, It says wireless connection not configured.(not too worried about this yet, if I can get it to connect with ethernet. I think i could figure the wireless part out)

However in the box directly under it, it says network connection dhcp.
However when I use firefox it cannont find anysites.
I checked the connection properties in firefox and they are set to always connected?
How come internet does not work, Do I need to configure my internal lan card to linux?
need drivers?

Any help would be great.

---

### Post by Mr. C. on 2007-03-22
Disable your wireless or wired if both are enabled.  System->Administration->Network.

MrC

---

### Post by chili555 on 2007-03-22
Please sudo gedit /etc/modprobe.d/blacklist to add:```
blacklist ipv6
```Reboot and let us know.

If that doesn't fix it, please post:```
ifconfig -a
ping -c3 www.google.com
ping -c3 64.233.161.147
```We'll get it.

---

### Post by FNGtyler on 2007-03-22
ok, i am very new

I guessing sudo is the text editor i load from the terminal

i opened terminal typed in:
sudo gedit /etc/modprobe.d/blacklist

it opened the editor
then what do i change?

This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

---

### Post by FNGtyler on 2007-03-22
you guys rock, i am up and running writing this from firefox.

anyone wouldn`t know how to make it work with my broadcom wireless card would they?
:)

---

### Post by chili555 on 2007-03-22
I'm sure someone does. Post the output from a terminal where you type:```
lspci -v
```You can skip all the stuff that doesn't have anything to do with Broadcom and copy and paste it here.

I would start a whole new thread referencing Broadcom BCM whatever so the bcm geek zombies will home in on it.

You can also get tips here, once you identify the card: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)
And here: [https://wiki.ubuntu.com/?action=fullsearch&context=180&value=broadcom&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=broadcom&titlesearch=Titles)

By the way, do you have any idea how to pronounce the word 'ndiswrapper'?

---

### Post by Mr. C. on 2007-03-22
Excellent.  Post in a new, more specific wireless thread - you're likely to get more hits and help.

MrC

---

