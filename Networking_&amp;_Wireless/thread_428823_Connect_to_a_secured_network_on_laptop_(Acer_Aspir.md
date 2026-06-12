---
title: "Connect to a secured network on laptop (Acer Aspire 3000)"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by Sup3rkirby on 2007-04-30
Hey.  I am hopefully going to install Ubuntu 7.04 on my laptop(Acer Aspire 3000).

The only thing I am trying to make sure of is that I can get my wireless network card to work.
I am trying to connect to a secured wireless network, but I can't seem to actually connect.  I have tried setting it up manually, entering the essid and network key, but it will not connect.  It doesn't even show the network existing...

The network card is supported as far as I know(and have read).  I'm just not sure why it won't connect to the secured network.

---

### Post by Floppyjoe on 2007-04-30
I'm posting this message from an acer aspire 3003wlci using the broadcom 4318 card in feisty with network manager,ndiswrapper,wpa supplicant.

---

### Post by Sup3rkirby on 2007-04-30
I am sitting here with my laptop on my lap, 20 ft from the base station, using a WEP 64 bit hex key, an not connected.

Do I have to install the driver using ndiswrapper?  I thought it was already supported and should work with no installation....
If I must install it, is the driver download from the link in your sig the one i need to use?

---

### Post by Floppyjoe on 2007-04-30
> **Sup3rkirby said:**
> I am sitting here with my laptop on my lap, 20 ft from the base station, using a WEP 64 bit hex key, an not connected.

Do I have to install the driver using ndiswrapper?  I thought it was already supported and should work with no installation....
If I must install it, is the driver download from the link in your sig the one i need to use?

If you have the broadcom 4318 card installed there are two ways to get it to work.
1)Ndiswrapper with the windows drivers using the link in my sig.
2)The bcm43xx driver with firmware either loaded using fwcutter or  firmware pre-cut from another location on the web.

---

### Post by Sup3rkirby on 2007-04-30
yes, i have the broadcom 4318 card installed.  but there is a problem.  you see, i have no internet on my laptop.  I need ndiswrapper to install the driver.  to install ndiswrapper, i have to be connected to the internet.  it is trying to download the needed files, which can't be done with no internet connection.

---

### Post by Floppyjoe on 2007-04-30
> **Sup3rkirby said:**
> yes, i have the broadcom 4318 card installed.  but there is a problem.  you see, i have no internet on my laptop.  I need ndiswrapper to install the driver.  to install ndiswrapper, i have to be connected to the internet.  it is trying to download the needed files, which can't be done with no internet connection.

There is a nice script method out here in Ubuntu land that uses the ubuntu install disk with the script. Hang on and let me see if I can find it . Ill post it here so just reload this page.
Here it is:
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

