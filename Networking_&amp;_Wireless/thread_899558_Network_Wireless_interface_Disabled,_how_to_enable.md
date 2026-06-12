---
title: "Network Wireless interface Disabled, how to enable it?"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by Barad on 2008-08-24
Hello all,
I've just installed Linux and i have a problem with my wireless connection.It just doesn't want to connect to my router(Netgear).
I have a "Broadcom corporation BCM4306 802.11b/g Wireless Lan controller" card.

I go to the network settings and set "wireless connection" to "roaming mode enabled" then go to the network manager at the taskbar, but there are no networks.I choose connect to other wireless network and type everything it wants but still i don't have internet on my Laptop.
I really need your help!Thank you

---

### Post by Sam Lars on 2008-08-24
Broadcom cards like that are tough.  What did you do to get it working?

---

### Post by Barad on 2008-08-25
I tried a lot of things to get it working but it still doesn't want to work.
I am posting you link with the things i've tried:

1).[http://www.linuxquestions.org/questions/linux-hardware-18/apple-powerbook-g4-broadcom-bcm4306-wireless-failure-connecting-ap-663405/](http://www.linuxquestions.org/questions/linux-hardware-18/apple-powerbook-g4-broadcom-bcm4306-wireless-failure-connecting-ap-663405/)

2).[http://www.linuxforums.org/forum/debian-linux-help/85006-installing-broadcom-bcm4306.html](http://www.linuxforums.org/forum/debian-linux-help/85006-installing-broadcom-bcm4306.html)

and more but i cannot find the links now.

P.S. I have found anything about this card here in ubuntuforums...Am i lucky to have this card?!?

---

### Post by Sam Lars on 2008-08-26
Well I have a couple 4306 rev 03, and this is what I've found in Hardy:
There are 3 drivers you could possibly use:
1. b43
2. Ndiswrapper
3. bcm43xx

I think in Intrepid bcm43xx will be gone and replaced with b43.  It's good because bcm43xx is not that great.  I've found it to be anywhere from okay to not stable at all.
Ndiswrapper may work for you, but I could not get it to work with WPA, and I did have it in a pattern of freezing the system before.  That may or may not affect you.
The b43 driver is probably the best in theory, but right now it probably won't work for you.  You can try it, I think it's what Ubuntu wants to install by default.  You can get to it either through the Restricted Drivers program or by installing
```
sudo apt-get install b43-fwcutter
```
If you hook up to Ethernet it will automatically download and install what you need.  I can also attach later the files that I use if Ethernet won't work for you.

I'm not sure what you've done, if anything, to your
/etc/modules
/etc/modprobe.d/blacklist
but you want to make sure that you only have the name of the driver you want to use in /etc/modules and it's a good idea to blacklist the rest in the other file.
Also, unless everything works great for you, please post the output of
```
lspci | grep Network
```

---

### Post by Barad on 2008-08-27
Hey buddy i've solved the problem. I used one of these drivers that you mentioned(b43). It works now and i am very very happy. :)) 

Thank you for your help.I really appreciate it:) :lolflag:

---

