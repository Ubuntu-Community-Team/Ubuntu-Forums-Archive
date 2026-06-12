---
title: "No listed bluetooth device using Intel AC7260 iwlwifi in Ubuntu 16.04"
date: 2017-04-07
forum: Networking &amp; Wireless
---

### Post by somelinuxuser on 2017-04-07
Hi,

I have a Dell XPS 15 which has an Intel AC7260 wireless chipset running ubuntu 16.04. My wireless lan is working although not at AC speeds. My main problem though is that the bluetooth device is not being picked up at all.

hcitool dev
Devices:

0: nfc0: NFC
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Running this command [ uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth ] shows a couple of firmware bug entries, [https://pastebin.com/rMHBtadD](https://pastebin.com/rMHBtadD)


I have ran the wireless-info script as well and the log can be found here: [https://pastebin.com/raw/8jcc89hB](https://pastebin.com/raw/8jcc89hB)

I believe this has to do with the iwlwifi firmware/drivers. I have done an [apt-get dist-upgrade] without having any luck. The bios does not have any options to enable/disable bluetooth and the keyboard shortcut to enable WiFi does not seem to do anything. Has anyone else experienced this or know of a possible solution? Ideally I would want to get the bluetooth working and it would be a bonus to have the network card recognise AC wireless speeds.

Any help would be appreciated.

Regards

---

### Post by praseodym on 2017-04-09
Please show the outputs of
```
modprobe -c | grep -i "8087.*8000"
modprobe -c | grep -i "8087.*8008"
usb-devices
```

---

### Post by somelinuxuser on 2017-04-09
Thanks for the reply,

modprobe -c | grep -i "8087.*8000"

Returns no output.

modprobe -c | grep -i "8087.*8008"

Returns no output.

usb-devices

Returns: [https://pastebin.com/yjn8zquv](https://pastebin.com/yjn8zquv)

---

### Post by praseodym on 2017-04-09
If there is no output the IDs are not referring to a driver, please show all of them!

---

### Post by somelinuxuser on 2017-04-09
I am not entirely sure which ID to use other than the ones provided for filtering out the modprobe command. Here is the entire output of my modprobe -c command: [https://gist.github.com/somejavadev/6c8541d3e7e753663ddf8095d9c67825](https://gist.github.com/somejavadev/6c8541d3e7e753663ddf8095d9c67825)

---

### Post by praseodym on 2017-04-09
Ok, so what about

```
usb-devices
```

? Have you checked
```

sudo rfkill unblock all
```

---

### Post by somelinuxuser on 2017-04-09
usb-devices brings back this list: [https://pastebin.com/yjn8zquv](https://pastebin.com/yjn8zquv) but I do not see any specific hci devices for bluetooth. rfkill list shows:

1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: nfc0: NFC
	Soft blocked: no
	Hard blocked: no

After running sudo rfkill unblock all the output stays unchanged. I read in the forums about people installing "backports", not sure if this is something I should try and do.

---

### Post by praseodym on 2017-04-09
Are you sure there is a BT device?

---

### Post by somelinuxuser on 2017-04-09
I will see if I can boot Windows again or another linux distro and see if it has got the same problem. I remember the bluetooth working when I was running Windows. It has the following chip: [http://www.intel.com/content/www/us/en/wireless-products/dual-band-wireless-ac-7260-bluetooth.html](http://www.intel.com/content/www/us/en/wireless-products/dual-band-wireless-ac-7260-bluetooth.html) which has bluetooth and WiFi.

---

### Post by jeremy31 on 2017-04-09
If you happen to boot into Windows again check to see if their are any BIOS updates.  I know those cards have bluetooth as an option and the bluetooth usually shows in lsusb results as 8087:07dc

I put one in my Toshiba a couple years ago and it wouldn't find the bluetooth in Linux or Windows but I found an older Atheros card that did work for bluetooth so I put the 7260 in a Dell and it worked fine

---

