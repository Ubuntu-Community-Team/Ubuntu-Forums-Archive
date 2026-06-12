---
title: "RTL8150 usb lan postinstall dhcp"
date: 2006-08-09
forum: Networking &amp; Wireless
---

### Post by commanda on 2006-08-09
I recently acquired a HP e-vectra.

After installing Ubuntu 5.10 I discovered the onboard ethernet doesn't actually work, even though it is detected during bootup and assigned eth0.

So I picked up a usb ethernet device, based on an RTL 8150 chip.
After much mucking around I found a precompiled driver for it already installed in /lib/modules/2.6..../kernel/drivers/usb/net/rtl8150.ko

I can make it work by doing;
insmod (path as above) rtl8150.ko
followed by /sbin/ifconfig eth1 192.168.0.21 netmask 255.255.255.0 broadcast 192.168.0.255
followed by /sbin/route add default gw 192.168.0.1 dev eth1

BUT this doesn't survive a reboot.

Q1: How do I do this correctly so it survives a reboot.

Q2: I have a dhcp server on my network. How do I make it get an ip number via dhcp rather than manually assigning one.

Thanks in advance
Amanda

---

### Post by commanda on 2006-08-10
No help huh?

OK. So modprobe rtl8150 survives a reboot.

BUT, it insists on activating the faulty onboard ethernet. After booting, I can go into System > Administration > Networking and deactivate eth0. Then the usb lan device on eth1 will work.

Short of getting out the soldering iron and removing the chip from the board, who amongst the self-proclaimed experts on here is going to tell me how to make this work.

Maybe a brute-force ifdown eth0 in a bash script in the correct /etc/rc.d

Amanda

ps: I don't post here often. I'm rapidly coming to the conclusion it's a complete & utter waste of time.

pps: Blind leading the blind.

ppps: Have I goaded anybody into piping up & giving me an answer yet?

---

