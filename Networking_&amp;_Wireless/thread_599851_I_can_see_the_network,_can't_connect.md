---
title: "I can see the network, can't connect"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by spacetoast on 2007-11-01
Hello!

I'm a linux noob and decided to install Ubuntu 7.10 on a machine yesterday and everything went really smoothly.

However, I can't seem to connect to the internet on my wireless network.

I'm using a Netgear 311v3 and was able to install ndiswrapper and get the driver installed using these instructions:

[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

Everything seemed to work just fine and I can see the wireless adapter in the Network Settings and even see the network. However, I can't access the web and ping doesn't work either.

One thing that struck me as odd, though is that in the Network Tools Device list I see the following devices:
lo
eth1
wireless interface (wlan0)
wireless interface (wlan0:avahi)

The wireless interface (wlan0:avahi), when clicked on, shows some IP information, but the (wlan0) shows no information.

If I try to configure the (wlan0:avahi), it tells me the The Interface does not exist. I can configure the (wlan0) one though.

I've been working on this issue for about 6 hours now using the forums and Google to try to learn what I can do, but nothing has worked so far. 

So, in a nutshell, I got the device to work and I can see my wireless network, I just can't connect to it. 

Thanks in advance!

Curtis

---

### Post by spacetoast on 2007-11-01
Well, I tried a number of different things as I mentioned in my first post, but what I didn't do was to do a hard re-boot. After I shut the machine off and then turned it back on again, I had access to my network, no problem.

I'm not sure what of the multitude of things I tried worked, but it worked. I just wish I knew exactly where in the process I should have done the hard re-boot.

---

