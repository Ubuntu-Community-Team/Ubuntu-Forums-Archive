---
title: "Acer One 14 z1402-50fz Ubuntu 14.04 wireless problem"
date: 2016-03-22
forum: Networking &amp; Wireless
---

### Post by adi-satya001 on 2016-03-22
Hi all,
Just want to share, I have a laptop acer one 14 z1402-50fz, and installed Ubuntu 14.04. And one that not working are Wireless (Wifi) and Bluetooth.
After looking around I found the solution for the wireless / wifi in here
[https://forums.linuxmint.com/viewtopic.php?t=208434](https://forums.linuxmint.com/viewtopic.php?t=208434)
With solution from Pjotr as below, (with connection to internet via other device):

sudo apt-get install git build-essential
git clone [https://github.com/lwfinger/rtl8723bu](https://github.com/lwfinger/rtl8723bu)
cd rtl8723bu
make
sudo make install
sudo modprobe -v 8723bu

It works, but after I do update kernel, the wifi is not recognized again. And I must re do above to have wifi working again.

I hope in next kernel update, the driver for the wifi have included in newer kernel.

======
For bluetooth still not working.

---

### Post by chili555 on 2016-03-22
> And I must re do above to have wifi working again.So you don't really have a wireless problem because you have solved it. 

Most users are not nearly as resourceful as you. Great job!> I hope in next kernel update, the driver for the wifi have included in newer kernel.I doubt that it will be included in Ubuntu prior to 16.04, using the 4.4-xx kernel and I am not even certain about that. As well, I don't think the developers spend much or even any time perusing the forums so your request will not get to them. Instead, I suggest you file a bug report: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

I suggest you start a new thread about the bluetooth and include as many details as you can. If it is a USB attached device, then:```
lsusb
```Otherwise:```
lspci -nn
dmesg | grep -i blue
```

---

### Post by jeremy31 on 2016-03-22
It seems support for this device has been added in the past couple weeks to the linux-next branch [http://git.kernel.org/cgit/linux/kernel/git/next/linux-next.git/log/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.c](http://git.kernel.org/cgit/linux/kernel/git/next/linux-next.git/log/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.c)

---

