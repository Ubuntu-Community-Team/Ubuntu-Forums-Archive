---
title: "how to assign the mac address on ubuntu16?"
date: 2016-09-23
forum: Networking &amp; Wireless
---

### Post by roshanlama252 on 2016-09-23
We are moving from ubuntu14 to ubuntu16. we have eth0, eth1 upto eth5 as a interface.
But somehow eth0 and eth1 is not picking up the right mac address. eth0 is getting the mac address of eth1 and eth1 is getting the mac address of eth2. Can anyone please help us how to get the right mac address corresponding to the interface?

---

### Post by roshanlama252 on 2016-09-23
I tried below:
$ sudo nano /etc/default/grubFor &#8220;GRUB_CMDLINE_LINUX&#8221;  and add the following&#8221;**net.ifnames=0 biosdevname=0**&#8220;.

From:
GRUB_CMDLINE_LINUX=""To:
GRUB_CMDLINE_LINUX="**net.ifnames=0 biosdevname=0**"

then update-grub
and reboot

---

### Post by roshanlama252 on 2016-09-23
i am able to get the eth0 and eth1 when i tried "ifconfig". But they are having the wrong mac address.

---

### Post by him610 on 2016-09-23
The network adapter MAC address, when you run > ifconfig will show up as HWaddr 00:00:00:00:00:00 (00 := hex characters). This will not change, ever! It is burned into the firmware of the network card.

Maybe with the upgrade from LTS 14 to LTS 16 the order of your network adapters got changed.

You could power down, remove the network adapters one at the time then reboot to verify which one is truly eth0 or eth1.

---

### Post by roshanlama252 on 2016-09-26
Hi him610,
we did the fresh iso install. 
we used to have the same eth0 and eth1 for ubuntu12 and 14 but in these new servers we are not being able to get the proper mac address for eth0 and eth1.

---

