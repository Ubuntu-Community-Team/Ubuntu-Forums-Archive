---
title: "WMP300N + Hardy Heron help needed"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by AtheriShadow on 2008-05-04
I recently installed Ubuntu Hardy Heron 8.04 on my PC, and I'm trying to get my Linksys WMP300N wireless card working.  I followed various guides around the internet and was able to get ndiswrapper set up with a bcmwl5.inf driver that was provided.  ndiswrapper -l reports that the bcmwl5 driver is installed and the hardware is reported as present, but no wireless networks appear in the network manager window.

The guides I followed instructed me to blacklist the default bcm43xx driver, but this was already done in the blacklist file, which mentioned a newer default.

Do I need to blacklist something different, or am I going about this installation all wrong for 8.04?

I dual-boot with Windows so I can access any files necessary to download, and I have an older wireless card I can try if this is a hopeless endeavor for now.

Any help getting this card working is greatly appreciated.

---

### Post by SMB6009 on 2008-06-14
I am running the Kubuntu 8.04 Live CD and I got my WMP300N to work by following the how-to at this link:

[http://ubuntuforums.org/showthread.php?p=3284373]("http://ubuntuforums.org/showthread.php?p=3284373")

By following this how-to, I did get my card to work with public networks, but cannot connect to my WPA protected network :(.
You might be able to get your card working with a WPA protected network, as some people have been successful at this, but unfortunately I was not one of those people.

---

### Post by appzattak on 2008-09-02
i got this to work, well sort of, the card is seen adn i can see wireless networks, but when I connect to mine and enter my wpa key, it freezes my system (8.04) and I have to hard reboot.

Anyone else have this problem???

---

