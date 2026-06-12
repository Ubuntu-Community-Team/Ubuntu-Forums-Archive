---
title: "gutsy and belkin rt61pci not conecting  to wpa network."
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by casagan on 2007-10-19
Hello, this is my first post here.
A few months ago I installed feisty fawn on my machine. No problems except that I couldnt get my wifi pci card to work. Its a belkin based on the rt61 chipset. I tried everything, I searched all the ubuntu forums post about this kind of issues, and still doesnt work, even now, using gutsy gibon. At last, now I can see my network, but the network manager cannot connect to it, it freezes after a few minutes. Right now I am at office and I dont have acces to my machine, but please, can some one tell if there is still some serious bug with this chipset? If there is, I am considering buying a new wifi card, one that is fully supported in gutsy. If there is not, and it is suposed to work out of the box, I dont know what elese to try. At home I have another windows machine and an xbox 360 and thay connect without any issue to the wifi wpa secured network. 

Thanks in advance.

Casagan.

---

### Post by Haim on 2007-10-19
Have a look here...

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)

---

### Post by casagan on 2007-10-19
Thanks, but I tried that back in Feisty and I couldnt get it to work. Where  can I find if Gusty supports "out of the box" this chipset?

Regards,
Casagan.

---

### Post by Amt0571 on 2007-10-19
I'm having the same issue with a RT61 conceptronic card. No way to conenct to a WPA network. I'm frankly quite tired with the disaster of Ralink chipsets on Ubuntu.

Would Ndiswrapper solve this issues or the only solution is change the wireless card or change to another distro?

Thanks

---

### Post by kashms on 2007-10-19
I also have a card based on RT61 (DWL-G630), and the Gutsy module rt61pci works for me even with WPA2. It was however unstable under high load (TV streaming, playing ET) and would disconnect. 

I am now using ndiswrapper and the connection is very stable also under high load.

If you have the option to do so, try turning off security on the router just to make sure that it really is a WPA issue and not a connection issue.

---

### Post by Haim on 2007-10-23
I've seen someone suggest  following these instructions, but substitute rt61 for the rt73.

[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

---

