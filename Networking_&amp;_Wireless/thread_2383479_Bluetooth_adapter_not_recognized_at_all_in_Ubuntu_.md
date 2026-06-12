---
title: "Bluetooth adapter not recognized at all in Ubuntu 17.10"
date: 2018-01-25
forum: Networking &amp; Wireless
---

### Post by adhdluke on 2018-01-25
Just installed Ubtunu 17.10 a while ago. I have only a few issues, but I'll talk about those in other topics as they're unrelated to this.
I cannot get my computer to recognize my bluetooth adapter at all. Gnome doesn't see it, no command line utility I run seems to see it, it's very annoying.
I know next to nothing about troubleshooting wireless issues, please help.

---

### Post by praseodym on 2018-01-27
Please show the outputs of
```

lspci -nnk
lsusb
usb-devices
lsmod
```

---

### Post by adhdluke on 2018-01-30
output of lspci -nnk = [https://pastebin.com/CcvkNxMT](https://pastebin.com/CcvkNxMT)
output of lsusb = [https://pastebin.com/4dC1eVGk](https://pastebin.com/4dC1eVGk)
output of usb-devices = [https://pastebin.com/qRZYTnsA](https://pastebin.com/qRZYTnsA)
output of lsmod = [https://pastebin.com/1FpxNZTc](https://pastebin.com/1FpxNZTc)

---

### Post by praseodym on 2018-01-30
```
02:00.1 Bluetooth [0d11]: Ralink corp. RT3290 Bluetooth [1814:3298]
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
```
There it is. Driver installation via
```

sudo add-apt-repository ppa:blaze/rtbth-dkms
sudo apt-get update
sudo apt install --reinstall dkms rtbth-dkms blueman linux-headers-$(uname -r) linux-headers-generic build-essential
sudo modprobe -v rtbth 
```

---

### Post by adhdluke on 2018-01-30
Okay, had to quick disable secure boot but other than that no hiccups installing the driver. Now, it recognizes the adapter but doesn't turn bluetooth on when i tell it to

---

### Post by praseodym on 2018-01-30
Lets check
```

hciconfig --all
lsmod
rfkill list
dmesg | grep blue
```
Any hotkey for BT?

---

### Post by adhdluke on 2018-01-31
lsmod output if you need it [https://pastebin.com/9dAZBtT9](https://pastebin.com/9dAZBtT9)
rfkill list output:
"
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
"
No hotkey for bluetooth, and now after rebooting it doesn't recognize the adapter again.

---

### Post by adhdluke on 2018-02-20
Quick update, turns out the reason it won't work is because a bug in my BIOS doesn't let me disable secure boot or enable legacy boot, the changes don't save even when it says I saved them. After a reboot it just shows that secure boot is on and legacy boot is off. The updater for the BIOS is a windows executable from HP, and I don't really want to install windows just to update my BIOS, so I'm wondering how to do that now.

---

