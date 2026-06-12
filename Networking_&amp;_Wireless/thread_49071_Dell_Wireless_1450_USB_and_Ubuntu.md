---
title: "Dell Wireless 1450 USB and Ubuntu"
date: 2005-07-14
forum: Networking &amp; Wireless
---

### Post by csalinas on 2005-07-14
I have installed Ubuntu 5.04 on a Dell Dimension 8400 with a Dell Wireless 1450 that uses USB.  

The card is not recognized as evidenced by it not showing up when I issue the lsusb command from a terminal window.  

I've read through a number of forum messages and am still unclear what the next steps would be to recognize the card, eg. should I find an NDIS 1.1 wrapper and put it on a cd-rom?  

If anyone has this hardware environment working or any ideas, I would really appreciate it.

Chad Salinas

---

### Post by jimmyp on 2005-08-09
You ever get this figured out?

---

### Post by Neomor on 2006-02-19
Yes.  Did you ever figure this out--I have the exact same problem!

---

### Post by pcastrog on 2006-06-10
Any solution? I have the same problem, Any Idea, I try all in this forum and nothing. Please

---

### Post by SouthMan on 2006-06-21
I was able to get the Dell 1450 USB WLAN adapter working.  It wasn't too bad.

1 - rmmod e100 and all islsm modules
2 - using the dell driver cd use ndiswrapper to install the driver
3 - modprobe -a ndiswrapper
4 - go to the network configuration tool and load your wlan info

That's all I had to do.

---

### Post by sparhawk on 2006-07-07
> **SouthMan said:**
> I was able to get the Dell 1450 USB WLAN adapter working.  It wasn't too bad.

1 - rmmod e100 and all islsm modules
2 - using the dell driver cd use ndiswrapper to install the driver
3 - modprobe -a ndiswrapper
4 - go to the network configuration tool and load your wlan info

That's all I had to do.


How did you manage to remove the islsm modules? When I try it tells me that they are in use and cannot be removed.

---

### Post by cleverselfreferentialname on 2006-07-18
Maybe if you removed them from /etc/modules and rebooted?

---

### Post by hansi001 on 2006-08-12
I MADE IT! :D I just had to remove the islsmu modules by blacklisting them :D

---

### Post by geomantic8 on 2006-09-21
> I was able to get the Dell 1450 USB WLAN adapter working. It wasn't too bad.

1 - rmmod e100 and all islsm modules
2 - using the dell driver cd use ndiswrapper to install the driver
3 - modprobe -a ndiswrapper
4 - go to the network configuration tool and load your wlan info

That's all I had to do.

Okay, I'm a relative newbie to the command line. I've tried to follow these instructions and while they seem relatively straightforward, I'm making rookie mistakes somewhere. I've posted my results below. Thanks in advance for any helpful replies.  

root@halesia:~# ndiswrapper -i /dev/cdrom0/driver/prism02.sys
Installing prism02.sys
couldn't copy /dev/cdrom0/driver/prism02.sys at /usr/sbin/ndiswrapper line 135.
root@halesia:~# ndiswrapper -i /dev/cdrom/driver/prism02.sys
prism02.sys is already installed. Use -e to remove it

root@halesia:~# modprobe -a ndiswrapper
WARNING: Error inserting ndiswrapper (/lib/modules/2.6.15-27-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

---

### Post by geomantic8 on 2006-09-21
Oh, one more question...

The Dell disk has an RPM in the Linux directory, as well as the prisma02.sys in the Drivers directory. The driver would be the prisma02.sys file, no?

Thanks again!

---

