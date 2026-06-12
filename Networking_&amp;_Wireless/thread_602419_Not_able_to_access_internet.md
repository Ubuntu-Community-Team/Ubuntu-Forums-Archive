---
title: "Not able to access internet"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by Haama on 2007-11-04
Hi!

I just did a fresh install of Ubuntu 7.10 and now I can't access the internet. It worked just fine from the live-cd but once I booted to the system it didn't work.
I have router which is connected to the other computer and to internet. I can't even ping the router.

Note: I have to boot with the irqpoll option, otherwise ubuntu won't boot. I believe this has nothing to do with the network issue but decided to mention it anyway.

Thanks in advance!

---

### Post by JayvJay on 2007-11-04
If the other computer is a windows box and you are sharing the network connection you need to go to the window machine connection and allow sharing of the connection. It is the advanced tab on the connection.

Luck!

---

### Post by Haama on 2007-11-04
I tried what you said and I don't think that is the problem. I have a dual boot machine and I'm able to access the internet with windows just fine. Both computers are connected straight to the router which is connected to internet (guess I didn't explain this too clearly in the first post).
Thanks anyway.

---

### Post by Haama on 2007-11-05
Came to post some more information.
I reinstalled gutsy but it didn't help.
My system specs are:
Intel E4300
1GB 800Mhz RAM
Samsung 320BG HDD
GeForce 8500 GT
Abit IB9 motherboard (intel p965 chipset)
"Realtek Gigabit ethernet" network card (is this even a valid word? xP)
Ubuntu 7.10 32-bit

I was also thinking if it would be possible to somehow copy the settings from the live-cd session? Since it works with the live-cd. The strange thing is that I can't ping the router while using the live-cd...

---

### Post by sipickles on 2007-11-05
I bust a gut trying to get mine to work (it made a wireless setup on a laptop look easy!), until I put 

noapic


in the boot command line. That enabled the net card and off I go. 

My problem is it works in firefox but not package manage :(

---

### Post by Haama on 2007-11-06
Thanks for the hint but that didn't help either.. :neutral: I've usually been able solve my problems with ubuntu but this is a tough one... The strange thing is it works straigth off the live-cd..

---

### Post by noob12 on 2007-11-06
First of all, is the device showing up in your **lspci -nn** output?  and is it shown as claimed by a driver when you run **sudo lshw -C network**.   If you had experienced PCI routing issues before adding irqpoll, I would try the **pci=noacpi** flag rather than irqpoll and see if that helps.  I've put some help text at the end of the message on setting and verifying boot flags for a one-time boot.

If that is all ok, check that you have link detected using **sudo ethtool eth0**.   Make sure it shows "Link Detected: Yes."

If DHCP failed, try assigning an address manually and pinging your router.

Look at the tail of your kernel log (/var/log/kern.log) for any errors.


**Instructions for one-time boot flag entry**

When booting you'll normally see grub flash a menu of boot options up for a little while.  While it is up  with the default selection highlighted, press **e**, then use arrow keys to navigate to the line that starts with **kernel** and hit **e** again to edit it.  Put the flags at the end of the line, separated from each other and from prior material on that line by space or spaces.  Hit Enter to accept, then b to boot.

To confirm you got the flags entered properly, you should see them if you type
```

dmesg | grep 'Kernel command line'

```
after you boot.

The flags will only apply to that one boot.

---

