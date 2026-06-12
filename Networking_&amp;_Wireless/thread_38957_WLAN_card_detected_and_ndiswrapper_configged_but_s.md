---
title: "WLAN card detected and ndiswrapper configged but still no internet"
date: 2005-06-02
forum: Networking &amp; Wireless
---

### Post by Cerberus on 2005-06-02
Hey, i installed Hoary on my laptop today and i use a "D-LINK DWL G650+" wireless PCMCIA card to connect with my access point. After i installed Hoary using only my ETH0 interface i putted in my WLAN card. When i look at "Network" the card shows up but whatever i try it is not working.

I read some tutorials about ndiswrapper-utils so i apt-getted it and downloaded the right *.inf driver. Followed all the steps but still it is not working. When i boot my Ubuntu one of the leds flashes for a second but then goes off again. When i put the card in there is none of the LEDs on, is this normal?

If you need extra info i will give it just say what you need.

Thanks in advance
Cerberus

---

### Post by Cerberus on 2005-06-03
Is there really no-one who can help me? I'm a beginner to linux so i probably did something stupid that can be fixed.

---

### Post by spd106 on 2005-06-04
Hi, your card is listed on the ndiswrapper website 
[http://ndiswrapper.sourceforge.net/phpwiki/index.php/List?PHPSESSID=945bcecf080b67c5c1c9bd4d1fbf37cd](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List?PHPSESSID=945bcecf080b67c5c1c9bd4d1fbf37cd)

It looks like you will have to compile ndiswrapper1.1 from source, as the utils package is not enough.

There is a wiki howto to help you out though.
[http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto)

You will need the kernel sources, gcc complier plus a few other bits and bobs, it's all in the guide.

Any probs search the forum first, then report back here.

Good luck Cerberus

---

### Post by Cerberus on 2005-06-05
Hey, i solved the problem already. The problem was that i forgot to delete the module dat Ubuntu loaded acx100 once i got rid of it it worked like a charm.

---

