---
title: "Unable to connect to wi-fi"
date: 2014-06-26
forum: Networking &amp; Wireless
---

### Post by ImBunting on 2014-06-26
I'm brand new to ubuntu and linux in general, so I apologize in advance if this is the incorrect location to post this or if this question is trivial. I was given a wiped computer and installed a clean version of ubuntu 14.04. When I try to connect to the wi-fi using network connections, the only option I am given is ethernet. When I run ifconfig the only devices are 'lo' and 'etho0'. Running iwconfig confirms that neither of these have wireless capabilities. Connecting via an ethernet cable allows me to get on the itnernet, but this is difficult for me because ethernet ports I have access to are hard to come by. I suspect this is because the ubuntu download doesn't include the driver software for my specific wireless card, but unfortunately I'm not allowed to open the laptop to see what the wireless card is, and furthermore I don't actually know whether there is a wireless card in it at all. Any and all help would be greatly appreciated, even simply pointing me to the correct location to post this. Thanks.

---

### Post by varunendra on 2014-06-26
First off, Welcome to the forums sbunting! :)

To see whether you have a wireless card or not in the laptop, you can check its BIOS. Is there any option related to "Wireless"?

You can also check it with a few commands in Ubuntu -
```
lspci -nnk | grep -iA2 net
lsusb
sudo lshw -C network
```

If the card is on a PCI bus, the first command should show it, if it is on a USB bus, the second will show it. You can also use 'lspci' without filters to see all the devices on PCI bus. The third command is an alternative way to list devices that are detected as 'Network' devices.

---

