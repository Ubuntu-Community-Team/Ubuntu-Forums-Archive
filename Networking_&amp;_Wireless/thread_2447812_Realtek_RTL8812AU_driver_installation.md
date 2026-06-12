---
title: "Realtek RTL8812AU driver installation"
date: 2020-07-26
forum: Networking &amp; Wireless
---

### Post by robski2012 on 2020-07-26
Hi please could somebody help me fully purge my system of the old realtek drivers and then help me to install a new one. I have just bought the Alfa AWUS036ACH i sucessfully download the RTL8812AU driver and it worked for about 2 days then suddenly stopped the lights have stopped blinking on the card all together now.

dkms staus = root@venom:~# dkms statusrealtek-rtl88xxau, 5.6.4.2~20200715: added
rtl8812AU, 5: added
rtl8812au, 5.6.4.2: added

 lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 0bda:8812 Realtek Semiconductor Corp. RTL8812AU 802.11a/b/g/n/ac WLAN Adapter




Ive been trying to solve this problem for days now and its driving me insane as i am a noob to ubuntu linux. Any help would be greatly appreciated. Thanks Robski

---

### Post by SeijiSensei on 2020-07-26
If you run the Driver Manager application in Settings, it will download, compile, and install the driver automatically.

As for removing what you have now, I'm afraid I can't help with that. I rarely install software from outside the Ubuntu repository structure.

---

### Post by jeremy31 on 2020-07-27
Have you rebooted since installing those drivers?  The dkms status just says added when it should list a kernel version and "installed"
My results for dkms status show
```
dkms status
rtl8812au, 5.6.4.2, 5.4.0-26-generic, x86_64: installed
rtl8812au, 5.6.4.2, 5.4.0-37-generic, x86_64: installed
rtl8812au, 5.6.4.2, 5.4.0-39-generic, x86_64: installed
rtl8812au, 5.6.4.2, 5.4.0-40-generic, x86_64: installed
```

---

### Post by durexlw on 2020-07-29
Can you confirm the card works on another machine?
If it ran for two days and suddenly breaks down, I'd strongly consider checking the hardware.

In my experience: software bugs have structure: something must have changed for a software bug to suddenly appear: an update, some change in configuration, something. Whereas hardware mistakes can just seemingly pop out of nowhere without much reproducability (if that's even a word).

---

