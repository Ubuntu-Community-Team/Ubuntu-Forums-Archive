---
title: "Ethernet controller name increments on reboot"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by limaxray on 2007-11-08
So I picked up an HP Pavilion DV6646 last weekend, and after taking it home and giving Vista a chance for about an hour, I installed Gusty.  This was probably my most problematic install of Ubuntu in terms of hardware issues; but I was able to resolve the majority of the problems with a little effort.  There is still one issue I can't figure out.  

Every time I reboot, the ethernet controller number increments by 2; ie eth0, eth2, eth4, etc. Last I checked, I'm somewhere over 30.  I've looked around the forums and other sites, and while I have found others with a similar issue, I haven't found anyone with a solution. 

I suppose it's really not that important as I rarely ever even use wired ethernet on any of my laptops, but I admit it does annoy the heck out of me and I would like to resolve it.  Does anyone have any suggestions?

---

### Post by noob12 on 2007-11-09
Can you post the output of these:
```

lspci -nn

sudo lshw -C network

ifconfig -a

cat /etc/udev/rules.d/70-persistent-net.rules 

```

---

### Post by Er1ck on 2007-11-11
Suggestion: Drop Ubuntu 7.10 and do a clean installation of Ubuntu 7.04 Feisty Fawn instead.

---

### Post by noob12 on 2007-11-12
That seems a bit excessive.

You likely just need to add a rule for the card in **/etc/udev/rules.d/70-persistent-net.rules** or modify the existing rule to use something that is more stable.

Might be able to provide more directed guidance if you post the output of the commands requested earlier.

---

### Post by Er1ck on 2007-11-18
I have the exact same laptop and I initially tried installing ubuntu 7.10 but I got as far as having it installed on my hard drive without any wireless and I wasn't able to make use of the desktopCD; I had to download the alternate CD. I did the same with 7.04 fiesty, I installed it over my 7.10 and the wireless card didn't work as well, but after looking at another thread, I was able to get it 100% working. The webcam worked on its own, as well as the touchpad and essentially everything else. The video card I got working through envy (manual install of the latest nvidia drivers). So as of now, everything is 100% working.

---

