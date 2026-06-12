---
title: "Problem with realtek 8723be on ubuntu 14.4"
date: 2016-01-06
forum: Networking &amp; Wireless
---

### Post by paul247 on 2016-01-06
Hello,
Like a lot of people, I have problems of connexion with the Realtek 8723be wifi card and ubuntu...
But I haven't found a thread with the exact same problem.
So here it is. I've bought a HP notebook and installed Ubuntu 14.4 on it. There is problem of connexion to the internet (weak and some interruptions) while there is no problem using windows 10 on the same computer or with a macbook or smartphone and no problem with wired connection... At my present house it cannot even find a single wifi emitter (while I am in a flat where I can see up to 10 wifi emitters on windows 10...). I've checked that problem on the internet, and it seems well known and easy to solve: add a line in the rlt8723be.conf file in modprob.d. 
```
echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```


Problem this file doesn't exist on my computer.


Here's what I've already tried:
```
sudo rmmod rtl8723be && modprobe rtl8723be 
modprobe: ERROR: could not insert 'rtl8723be': Operation not permitted
```

and the list of the files in modprobe.d

```

alsa-base.conf
blacklist-ath_pci.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-rare-network.conf
blacklist-watchdog.conf
fbdev-blacklist.conf
iwlwifi.conf
mlx4.conf
qemu-system-x86.conf
vmwgfx-fbdev.conf
```

Do you have any ideas how to fix this problem or where to look at?

Cheers,

Paul

---

### Post by Jerry_Gorland on 2016-01-08
If you put your laptop within 12 inches of your Wi-Fi router antenna, to you see it?

---

