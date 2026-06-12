---
title: "WiFi problem"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by elfuego on 2007-05-21
I have a officially unsuported WiFi card "Vivanco" WLAN PCC54, 802.11g PCMCIA. Feisty does recognize it though as Texas Instruments ACX 111 54Mbps Wireless Interface with device type/capabilities unknown. 
It's interesting that I can detect the wireless networks, but I cannot connect to them - with or without WEP key. Is this the driver issue, or is there something else behind? Can someone help me, it's really a bother to restart the system in windows mode just because of wifi... :)

10x!

---

### Post by Kobalt on 2007-05-21
Check [it]("https://help.ubuntu.com/community/WifiDocs/Driver/acx111") out. 
Note that the open source drivers for this acx111 modules don't provide WPA encryption support. To have this you will have to use ndiswrapper.

---

### Post by Darkmoon_UK on 2007-05-22
Hi, I am having the same problem with an ACX111 based PCMCIA card from ZCom. Worked with no problems at all in Edgy Eft but is now broken in Feisty Fawn. iwconfig actually shows a good connection but somehow this doesn't translate to any kind of connectivity in the GUI.

Various posts (including the reply above) lead me to believe that the Feisty drivers are b0rked and it'll work by installing with an older driver?  This leads me to another question; the link mentions installing an alternative firmware... as I understand the term, this means I need to reflash my card? I also saw the ndiswrapper solution, might this actually be better than using an older driver e.g. does it integrate with Feisty GUI?
If I need to flash the card, fine, but will it still work under Windows? Perhaps 'firmware' means something different here that just resides on the PC, but I really don't want to flash and end up with a card that works in neither. Thanks for any guidance you can offer...

---

### Post by chili555 on 2007-05-22
I think the problem is, indeed, the firmware. After you do *updatedb* if you do *locate acx | grep firmware* you will see dozens of choices! acx111 cards load the firmware from 'default' unless you tell it otherwise. Here is an excerpt from /lib/firmware/2.6.20-15-generic/acx/readme.txt:> The acx loads the firmware marked "default", unless you pass it another
version using the firmware_ver=XXXX module parameter.
........
acx111 PCI 0.1.0.11
acx111 PCI 0.4.11.4
acx111 PCI 0.4.11.9
acx111 PCI 1.2.0.30
acx111 PCI 2.3.1.31 (default)So, I suggest *sudo gedit /etc/modprobe.d/options* to add a new line:```
options acx firmware_ver=2.3.1.31
```Reboot and see if your card springs to life.

---

### Post by elfuego on 2007-05-22
Thanks guys; I'll give it a try when I get near to access point. :)

---

### Post by Darkmoon_UK on 2007-05-23
**Update on my situation:**

I have my **ACX111** based card working now, using **ndiswrapper** and the windows drivers.

I *tried *to use the native drivers but gave up as this method is less well documented - I was faced with the issue that I knew I had an older driver called acx as well as the newer one... how would I remove the older one to prevent conflict? Blacklisting would surely blacklist the new one too. Do the newer ones overwrite the old one or do they still reside in the install directory? All these things I don't know, being a Linux n00b.

However I was able to set up **ndiswrapper **relatively easily; and it works (yay) but still isn't playing ball with the Network Manager in Feisty KDE (boo!). Basically any time I try to edit the settings there it stops working and breaks the ESSID setting, so that I have to re-set it using iwconfig.

After reboot **at the moment I have to do the following to get connectivity **from Firefox:

```
sudo iwconfig wlan0 essid studio
sudo iwconfig wlan0 key <<<MyKey>>>
sudo dhclient
```

So, what am I missing? Or should I simply put these three commands in an auto run script. Not terribly convenient though as I do change locations with my laptop.

Any further help greatly appreciated.

- Chris.

---

