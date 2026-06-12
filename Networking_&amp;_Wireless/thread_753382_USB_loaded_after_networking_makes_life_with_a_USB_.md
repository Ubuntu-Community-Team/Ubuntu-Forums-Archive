---
title: "USB loaded after networking makes life with a USB card hard"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by Luc1fer on 2008-04-12
Hi

I've got a wireless usb card connected to a pc and it almost works.

It seems the usb parts are being loaded after the network parts which makes the usb card to not connect until i restart the networking (/etc/init.d/networking restart) but after that everything works fine.

Anyone got any easy solution. It's my grandmas computer so it has to be easy or she'll just throw it out...

I guess the best solution is to reorder the loading order but that seems a bit hard and therefore I've been thinking about some shell script which just restarts the networking. Although I'm not too good with the shell scripting either so I might need a bit of help with that too...

---

### Post by nixscripter on 2008-04-12
One trick I would suggest is this: if the card is controlled by a kernel module, have it loaded at boot time by appending its name to the bottom of **/etc/modules**. This will cause some of the USB stuff to be loaded (so that it can load the module), and that might be enough to bring up the card's networking interface (which is what the network subsystem wants).

However, I don't know what other side effects it might cause in terms of other dependencies being loaded. If it doesn't work, just take the line out and reboot.

Hope this helps.

---

### Post by Luc1fer on 2008-04-13
The card is a Belkin f5d7050. Found this documentation on how to install it:
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver))

The documentation is a bit old but I did lsmod and found the module "zd1211rw" loaded so is that the module you want me to load?

lsmod | grep zd* returned this:
> zd1211rw               53508  0 
ieee80211softmac       31360  1 zd1211rw
ieee80211              35656  2 zd1211rw,ieee80211softmac
usbcore               138632  4 zd1211rw,ehci_hcd,uhci_hcd

Tried adding zd1211rw to the bottom of /etc/modules and rebooted but still the same problem.

---

### Post by Luc1fer on 2008-04-13
I did something easy i just added "/etc/init.d/networking restart" to /etc/rc.local which work.

Thanks for the help.

---

