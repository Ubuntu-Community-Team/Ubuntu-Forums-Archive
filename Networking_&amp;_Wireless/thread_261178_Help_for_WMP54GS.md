---
title: "Help for WMP54GS"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by Endrin on 2006-09-19
I couldn't find a relatively new thread to post this on to help with wireless issues regarding the WMP54GS Linksys Wireless-G card.

I'm relatively new to linux, so trouble shooting this problem has turned out to be a huge learning experience into linux.

When I discovered I had to use NDisWrapper to get my card to work, I immediately went for that solution.  When I went to configure my wireless script, it kept on giving me an error saying the Network Was Down.  It turns out that the broadcom had a process(?) called bcm43xx that was cancelling my connection to the network.  I don't know if this is computer specific, or if this is a general problem with the process of getting this card working in general.

After I sudo modprobe -r bcm43xx , I could sudo modprobe ndiswrapper and get the card to connect to the network flawlessly.  Granted, if you don't make a script for the -r bcm43xx, it will be on next time you reboot into linux.

Hopefully this helps some of the problems associated with this card and getting Broadcom cards to work in general.

---

### Post by sjieke on 2006-09-20
Instead of writing a script you can also add the bcm43xx module to the blacklist using following command:

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

This will prevent it from loading on next boot.
You can also let ndiswrapper load on boot using the following command:

```
sudo ndiswrapper -m
```

This will add the correct line to /etc/modules, or you can edit /etc/modules yourself and add the word ndiswrapper to the end of the file

---

