---
title: "Acer C720 Chromebook - Just added Ubuntu, but no wireless option"
date: 2015-03-01
forum: Networking &amp; Wireless
---

### Post by tash2 on 2015-03-01
Hi,
I just installed Ubuntu on my chromebook, but I can't get the wifi turned on. It's not even an option from the network drop down (enable/VPN are the only ones available). I followed the help guide, and it does see my card, but there is no info listed about wireless/wifi. I tried to see if I could update the drivers, but the help guide really was no help (you go in circles trying to get to the device drivers area, even from the direct links in the guide.)
Since it's a chromebook, there is no ethernet port. I know the wireless card works (I'm on it right now with the ChromeOS.)

I've tried the other tips in the c720 posts in this forum, but I'm getting no love.

This is the first time I've used Ubuntu, so any help you can offer would be greatly appreciated! But please be patient with me.  Thank you!
:)

---

### Post by Bucky Ball on 2015-03-01
Please open a terminal and give us the output of this command:

```
sudo lshw -C network
```

---

### Post by tash2 on 2015-03-01
Hi, ty for getting back. Is there a way to copy the text and get it back to chrome? I'm trying to enter this on my phone so if there's an obvious typo pls ignore.

*network UNCLAIMED
description: network controller
Product: atheros communications inc
Vendor: atheros communications inc
Physical id: 0
Bus info: PCI@0000:01:00.01
Version : 01
Width 64 bits
Clock: 33mhz
Capabilities: pm MSI PC express cap_list
Configuration: latency=0
Resources:memory:e0400000-e047ffff memory:e0480000-e048ffff

---

### Post by jeremy31 on 2015-03-03
Try ```
sudo modprobe ath9k
```  If it works, follow the instructions in the sticky post "before posting in networking and wireless" to see the instructions for running the wireless script and posting the output

---

### Post by tash2 on 2015-03-03
Hi,
So they it gives a bunch of fatal errors, and I can't install the wireless script (tried that, it wouldn't recognize my flash drive.) If I just reinstall it, is there a way to download the script using chrome? Or moving it over from chromeos? I'm kind of screwed here.
And if I didn't want to just play some fricken skyrim I think I would have given up by now.
Help!

---

### Post by jeremy31 on 2015-03-04
> **tash2 said:**
> Hi,
So they it gives a bunch of fatal errors, and I can't install the wireless script (tried that, it wouldn't recognize my flash drive.) If I just reinstall it, is there a way to download the script using chrome? Or moving it over from chromeos? I'm kind of screwed here.
And if I didn't want to just play some fricken skyrim I think I would have given up by now.
Help!

I think the instructions are in the sticky post for how to use it without an internet connection, here it is, Method 2 [http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385)
We know the wifi can work in Ubuntu in the C720 as there was another post [http://ubuntuforums.org/showthread.php?t=2267460](http://ubuntuforums.org/showthread.php?t=2267460)

Can you copy the error messages and paste it into a text file to put on a USB to post with your chrome os?

---

