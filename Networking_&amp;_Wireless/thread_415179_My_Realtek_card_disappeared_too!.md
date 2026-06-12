---
title: "My Realtek card disappeared too!"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by jstone00 on 2007-04-20
Grrrr! Here I thought I'd finally found a version of Linux that played well with my Encore PCI WiFi card Realtek 8185. Ubuntu 6.1 detected it and ran it flawlessly. Last night I upgraded to Feisty Fawn (Feisty Goat?) 7.04 and the wireless card disappeared, and no longer appears in the Network Manager applet. It seems like this is a common problem and a known bug, and I haven't been able to find a solution. Ndiswrapper reports "invalid driver" when I attempt to load any of the Windows drivers supplied with the card. I've even tried editing the /etc/network/interfaces file and managed to make Ubuntu unbootable. Luckily, another live-CD version of Linux (Puppy Linux) allowed me to view the Ubuntu partition and re-edit the damaged file so Ubuntu would boot again.

I know this has affected other users and that various suggestions for fixes have been posted elsewhere, but none have worked for me.  The person who posts a clear solution to this problem will earn my undying gratitude, and maybe a Snickers bar.  :popcorn: 

Regards.....

---

### Post by luke411 on 2007-04-20
There are some other posts on here about this but I'll add in my two cents worth since I had the same problem and managed to get mine working again.

1) You have to comment out the drivers in the black-listed file. 

/etc/modprobe.d/blacklist

#blacklist r818x
#blacklist r8187

2. You have to add a 'dummy' character to your ESSID after you reboot and the modules load. I used a " for mine at the end. I guess some bug makes the last character of your ESSID leave the building and you have to do that in order to connect. 

Good luck,

---

