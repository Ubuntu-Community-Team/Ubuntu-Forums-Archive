---
title: "Trying to install print server on kubuntu dapper"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by jonboy99 on 2007-05-19
Hi folks, sorry to still be using an old ubuntu release.

I've just bought a netgear wgps606 print server / wireless bridge, as I was so sick of trying to get WPA working with ubuntu (but that's a different issue entirely ;) )
It's working great as a bridge, but i've got trouble installing my printer to work with it in Kubuntu. The printer works fine plugged directly into the computer via USB (samsung ml1510), and works fine in the bridge using winXP, but i'm getting nowhere with kubuntu.

I've tried following the instructions here [http://www.cups.org/articles.php?L317](http://www.cups.org/articles.php?L317) but there are minor differences in the setup with kde compared to gnome which have stumped me.

In the system settings>printer screen, the first choice is to decide on the print system currently used. Options are:

CUPS
Generic unix LPD print system
LPR/LPRng print system
RLPR environment (remote LPD servers)

I'm not getting anywhere with either option - has anyone got any pointers?  The most promising i've got is using the last option in the list, which invites me to enter my host and queue, which i've done.
I'm then asked to enter a name for my printer, but never get the chance to select a manufacturer then printer, and when I try to print to the option created, get the message

'A print error occured.  Error message received from system: The rlpr executabel could not be found in your path. Check your installation.'


However, as I have never had the chance to enter the make and model of my printer anyway (as I do when I install it as a local printer) I suspect i'm going down the wrong path here.

Cheers folks

Jon

---

### Post by jonboy99 on 2007-05-19
Hmm, well - getting somewhere!

I tried installing the printer using a different computer on the same network.

I went to system settings>printers

Print system used was CUPS

Then I selected remote LPD queue

Entered the IP address of the printer as 192.168.1.121 (as standard the bridge would be 192.168.0.102, I altered my bridge's IP for my network).
Queue: L2 (or L1 depending on which socket your printer is plugged into)

Click Next - this takes a minute or two.

Then selected my printer driver.   This step is where I fell down last time - the available list of printer drivers is about 4 or 5 times as long as on the original computer I used - and my samsung is there!  From then on it all went smoothly.  I had assumed as my samsung didn't appear on driver list on the first computer that I had tried to install from a small group of network specific printers, but it simply is a case of the printer driver being missing from the first computer.

Anyone know how to fix this - why would a load of printer drivers be missing?  I have looked at adept package manager, and anything found with the search 'printer' is installed on both computers - so I don't think i'm missing a driver package.


Almost solved - help welcome!  :)

---

### Post by jonboy99 on 2007-05-19
Sorted!  Well, they say self help is the best kind  ;)

After finding this page: [http://www.linuxquestions.org/questions/showthread.php?t=452459](http://www.linuxquestions.org/questions/showthread.php?t=452459)

Used the sudo foomatic-cleanupdrivers command, and all the drivers appeared as they should on the next attempted install.  Hope this helps someone  :)

---

