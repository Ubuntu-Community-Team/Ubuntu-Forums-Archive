---
title: "help wit wifi configeration"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by deafchickadee on 2007-03-23
I have an Intel Prowireless 2200BG wireless thingy in a Dell Insprion 710m laptop. I have already downloaded the updates, and have also installed the network manager using

```
sudo apt-get install network-manager-gnome
```

I have no problems connecting wirelessly on an unsecured wireless network. Right now I'm on someone else's unsecured wireless network, but would like to use my secure wireless network using WPA. But I cannot access to my WPA secured wireless network. 

I have two questions:

1)How do I connect to a WPA secured wireless network. (Step-By-Step)
2)How do I scan for avalible networks. (I can use wifi-radar, but that doesn't actually allow me to connect to any networks, just view them (unless I'm doing something wrong there too)


Thanks heaps!

Please dumb it down, im not a ubuntu expert! :)

---

### Post by gradedcheese on 2007-03-24
You need something called wpa_supplicant, it's a package you install (search the forum for more information).  As for scanning, just click the Network Manager applet and it will show you a list of networks.  Is that not working?

---

