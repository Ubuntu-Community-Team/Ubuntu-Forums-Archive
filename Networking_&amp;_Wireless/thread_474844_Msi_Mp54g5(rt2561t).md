---
title: "Msi Mp54g5(rt2561t??)"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by PeterDenStore on 2007-06-15
Hello,

Is there such a Ralink Wireless chip known as RT2561T?? I have a  MSI MP54G5 MiniPCI in my laptop. I thought it was a Ralink RT61 chip but after trying and trying to get it to run in Linux with no success. I thought I would check the chip on on the card and it has RT2561T on it. So is this a chip for Ralink and is there any linux drivers for it?

Thanks,
Pate

---

### Post by MeeMaw on 2007-06-15
From what I have read rt2561 and rt61 are the same - it should be recognized as ra0 rather than eth0 or wlan0....

Try this;
[http://ubuntuforums.org/showthread.php?t=419709&highlight=rt2561](http://ubuntuforums.org/showthread.php?t=419709&highlight=rt2561)

holler if you have problems and we'll be along to help.    ;)

---

### Post by PeterDenStore on 2007-06-15
Hello,

Thanks for the reply MeeMaw. I am hoping to give it another go this weekend if I have the time. 

With the RT61 chip do you think an older version of Ubuntu would be better?


Thanks,
Pete

---

### Post by MeeMaw on 2007-06-15
I used it on Edgy when I dual-booted Ubuntu with PCLinuxOS on my desktop and it worked fine. I have Feisty on my laptop (with a different wireless card) and PCLOS only on my desktop (I got tired of the dual-boot... dual-boot also means dual-configure and I don't always have that much time.....)

I'm sure it will work in Edgy or Feisty.... the thing I had to watch with my old arthritic hands was typing in the settings EXACTLY -- Linux is case-sensitive so (example) dog is different from DOG (which is also different from Dog!!!)

Don't give up!!!!    ;)   I'm sure you can get it going!

---

### Post by Girindor on 2008-04-29
I installed Ubuntu 8.04 Server edition on an old Desktop to help me learn CLI and networking, and my wireless PCI card, which worked perfectly under 7.10 Desktop edition, is just not working. During the install it couldn't see it.

It is the Ralink RT2561T chip set. When I do "lspci" it tells me, "Network controller: RaLink RT2651/RT61 802.11g PCI", so it can see it.

I tried the following:
sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid "NAMEOFMYNETWORK"

so far so good.... but then, when I did:
sudo iwpriv wlan0 set AuthMode=WPAPSK

...it threw up the following error:
wlan0: no private ioctls

...I don't know how to proceed and would appreciate any help with this.
Thank you!

---

